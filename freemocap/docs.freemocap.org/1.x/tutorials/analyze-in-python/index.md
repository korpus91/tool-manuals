# Analyze your data in Python | FreeMoCap

Skip to main content

This is documentation for FreeMoCap 1.x (legacy), which is no longer actively maintained.

For up-to-date documentation, see the latest version (2.0 (alpha)).

Version: 1.x (legacy)

AI-generated documentationnot yet checked against current software

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-20

not checked against a specific version

More about how these docs are written

# Analyze your data in Python

Your recording's output includes a parquet file (see Find and read your output) in tidy long format: one row per keypoint per frame, with frame, keypoint, x, y, z, model, trajectory, and reprojection_error columns. See the output data model for what each of those means; this page is about actually working with it.

## Loading your data​

```

import pandas as pd

df = pd.read_parquet("path/to/your_recording_data.parquet")

df.head()

```

Because the format is tidy (one row per keypoint per frame) rather than wide, it plays well with pandas' own filtering and grouping instead of requiring custom indexing logic.

## Pulling out a single joint​

```

right_wrist = df[df["keypoint"] == "right_wrist"]

right_wrist = right_wrist.sort_values("frame")

```

That gives you every frame's x, y, z for one keypoint, in order, ready to plot or feed into further calculations.

## Filtering by tracking quality​

reprojection_error travels with every row, not just as a diagnostic afterthought. Before trusting a frame's position, it's worth checking it:

```

# a lower threshold is stricter; there's no single universal cutoff,

# it depends on your camera setup and task

clean = right_wrist[right_wrist["reprojection_error"] < right_wrist["reprojection_error"].quantile(0.95)]

```

## A quick trajectory plot​

```

import matplotlib.pyplot as plt

fig, ax = plt.subplots()

ax.plot(right_wrist["frame"], right_wrist["z"])

ax.set_xlabel("Frame")

ax.set_ylabel("Z position (mm)")

plt.show()

```

Remember the coordinate system: data is in millimetres, with +Z as up, if your ground-plane calibration set a Z-up frame in the first place.

## If you need array-shaped data instead​

The tidy parquet is usually the easier starting point, but the same data is also available as .npy arrays shaped (num_frames, num_markers, 3) per tracker and body region, if that's a better fit for your existing tooling:

```

import numpy as np

body_3d = np.load("path/to/mediapipe_body_3d_xyz.npy")

print(body_3d.shape)  # (num_frames, num_markers, 3)

```

See array shapes and units and skeleton models and keypoints for exactly which index maps to which keypoint, that mapping is tracker-specific.

## Next steps​

- The FreeMoCap output data model

- Array shapes and units

- Accuracy, validity, and limits

- Loading your data

- Pulling out a single joint

- Filtering by tracking quality

- A quick trajectory plot

- If you need array-shaped data instead

- Next steps
