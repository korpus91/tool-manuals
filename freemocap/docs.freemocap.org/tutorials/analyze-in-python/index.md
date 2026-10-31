# Analyze your data in Python | FreeMoCap

Skip to main content

Version: 2.0 (alpha)

This page is in flux. The V2 output column names and array shapes described here are a work in progress for version alpha. They're expected to stabilize by beta.
AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-10-14

freemocap main at v2.0.0-alpha.25 (75c8acc2): skeleton_from_mediapipe_observations.py builds the Human without reprojection error, so skellymodels actor.py writes the parquet reprojection_error column as NaN. Replaced the quantile-filter example, which returned no rows.

2026-10-14

freemocap main at v2.0.0-alpha.25 (75c8acc2): skellyforge skellymodels actor.py (freemocap_data_by_frame.parquet; tidy columns frame, keypoint, x, y, z, model, trajectory, reprojection_error; npy names {tracker}_{aspect}_{trajectory}.npy), posthoc_mocap_task.py (output_data/). File paths corrected; code examples unchanged.

2026-08-26

skellyforge/skellymodels/models/trajectory.py (as_array, as_dataframe docstrings) and managers/actor.py (create_summary_dataframe, save_out_numpy_data), confirming parquet columns, .npy shape, and the mediapipe_body_3d_xyz example filename all match current source verbatim

2026-08-20

not checked against a specific version

More about how these docs are written

# Analyze your data in Python

Each recording's output_data/freemocap_data_by_frame.parquet file (see find and read your output) holds all the data in one table: one row per keypoint per frame, with frame, keypoint, x, y, z, model, trajectory, and reprojection_error columns. See the output data model for what each of those means; this page is about actually working with it.

## Loading your data​

```

import pandas as pd

df = pd.read_parquet("path/to/recording/output_data/freemocap_data_by_frame.parquet")

df.head()

```

## Pulling out a single joint​

```

right_wrist = df[df["keypoint"] == "right_wrist"]

right_wrist = right_wrist.sort_values("frame")

```

That gives you the x, y, and z position of one keypoint in every frame, in order.

## Checking tracking quality​

The reprojection_error column is there for a per-point quality score, but it's empty (all NaN) in current recordings. For now, check tracking quality by eye in the annotated videos. See the output data model.

## A quick trajectory plot​

```

import matplotlib.pyplot as plt

fig, ax = plt.subplots()

ax.plot(right_wrist["frame"], right_wrist["z"])

ax.set_xlabel("Frame")

ax.set_ylabel("Z position (mm)")

plt.show()

```

Remember the coordinate system. Data is in millimetres, with +Z as up, if your ground-plane calibration set a Z-up frame in the first place.

## If you need array-shaped data instead​

The tidy parquet is usually the easier starting point, but the same data is also available as .npy arrays shaped (num_frames, num_markers, 3) per tracker and body region, if that's a better fit for your existing tooling:

```

import numpy as np

# file names start with the tracker used, for example rtmpose_ or mediapipe_

body_3d = np.load("path/to/recording/output_data/mediapipe_body_3d_xyz.npy")

print(body_3d.shape)  # (num_frames, num_markers, 3)

```

See array shapes and units and skeleton models and keypoints for exactly which index maps to which keypoint, that mapping is tracker-specific.

## Next steps​

- The FreeMoCap output data model

- Array shapes and units

- Accuracy, validity, and limits

- Loading your data

- Pulling out a single joint

- Checking tracking quality

- A quick trajectory plot

- If you need array-shaped data instead

- Next steps
