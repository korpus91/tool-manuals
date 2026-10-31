# Precise Timestamps | FreeMoCap

Skip to main content

# Precise Timestamps
🤖AI-generated documentation✓ curatedAI Generated
This page was drafted by an AI assistant and may contain inaccuracies. This content has been reviewed by a human curator.About content generation types

🤖
AI Generated — Page drafted entirely by AI from codebase or prompt instructions.
(e.g., docs generated from codebase analysis)
← this page

✋→🤖
AI Transformatted — Human provided raw material; AI restructured it into a different format.
(e.g., livestream → blog post, meeting notes → docs)

✋
Human Generated — Page written entirely by a human author.
(e.g., hand-written tutorial)

More info about content generation types ↗

⏱️
Most USB cameras do not record real timestamps. SkellyCam captures precise timestamps for every camera at every stage of the capture pipeline, plus the multi-camera stream — all in human-readable format with pre-calculated inter-camera synchronization statistics.

## Why timestamps matter​

Most USB cameras do not provide real timestamps. The cv2.VideoCapture timestamp property (CAP_PROP_POS_MSEC) is unreliable across platforms and drivers — sometimes it returns zero, sometimes wall-clock time, sometimes time since the camera was opened.

Many systems that do claim to provide timestamps actually "fake" them by computing frame_number × (1 / fps). This assumes the frame rate is constant and accurate — but in practice, USB camera frame rates fluctuate due to USB bandwidth contention, driver scheduling, exposure time variations, and system load. The resulting timestamps can be off by tens of milliseconds or more. These values are good-enough for most use cases, but they are not ideal for precise scientific measurement.

If you're doing motion capture, biomechanics, or any time-sensitive analysis, you need to know when each frame was actually captured — not a guess based on the nominal frame rate.

### Precision matters for 3D reconstruction​

For FreeMoCap and similar multi-camera motion capture systems, timestamp precision is not just nice-to-have, it is a limiting factor on the precision of 3D triangulation. When triangulating a 3D point from 2D observations across multiple cameras, any temporal misalignment between the cameras translates directly into spatial error in the reconstructed point. More precise timestamps enable more precise 3D reconstruction.
 Does it really matter though?

We put a LOT of effort into synchronizing frame grabs from multiple cameras, but does it really matter? Does the de-sync that would occur in a much simpler multi-camera strategy actually affect the quality downstream applications, such as skeleton reconstruction in FreeMoCap? Ultimately, its an empirical question that depends on your application. For casual video recording, it probably doesn't. But for multi-camera 3D triangulation (particarly for scientific analysis of fast movements), synchronization precision directly limits reconstruction accuracy. In SkellyCam, we treat synchronization precision as an aspirational goal — the target is perfect synchronization, and we get as close as we can. Even if your application doesn't need super high temporal precision today, having the data available means you can quantify your temporal error budget rather than guessing.

Also, its more fun this way :)

## The timebase concept​

For timestamps from multiple cameras to be comparable, they must share the same time base — that is, they must agree on what "zero" means.

Each camera in SkellyCam runs in its own process, but all processes share the same system clock. SkellyCam uses Python's time.perf_counter_ns() as the primary timestamp source. This provides:

- Nanosecond resolution — the finest granularity available in Python. While we should not trust nanosecond-scale values in Python (OS scheduling introduces microsecond/milisecond-level jitter), the integer nanosecond format avoids floating-point precision loss that would occur with perf_counter().

- Monotonic — the clock never goes backward, even during NTP adjustments (NTP is the protocol that keeps your system clock synchronized with internet time servers).

- Shared across processes — all processes on the same machine reference the same monotonic clock

The TimebaseMapping class is the primary tool SkellyCam uses to ensure a consistent timebase across all camera processes.

The perf_counter_ns clock has an arbitrary epoch (it starts at some point when the system booted), so the raw values are not directly meaningful. SkellyCam converts them into useful time representations using a TimebaseMapping:

RepresentationHow it's computedUse case

perf_counter_nsRaw monotonic nanosecond timestampHighest precision, inter-camera comparisons

timestamp.utc.secondsReference time.time_ns() + delta from reference perf_counter_nsCorrelation with external systems (IMU, force plates)

timestamp.from_recording_start.secperf_counter_ns minus first frame's perf_counter_nsHuman-readable elapsed time

timestamp.local.iso8601UTC + local timezone offsetHuman-readable wall-clock time

The TimebaseMapping is created once at recording start by sampling both time.time_ns() (wall-clock) and time.perf_counter_ns() (monotonic) simultaneously. This single reference point is then used to convert all subsequent perf_counter_ns values into wall-clock time.

## What SkellyCam records​

SkellyCam captures high-resolution perf_counter_ns timestamps at multiple stages of each frame's lifecycle (defined in the frame metadata structures in the source code):

- Pre-grab — Just before calling cv2.VideoCapture.grab()

- Post-grab — Immediately after grab() returns

- Pre-retrieve — Just before calling retrieve()

- Post-retrieve — Immediately after retrieve() returns the decoded frame

- Pre/post shared memory copy — When the frame is written to the shared memory ring buffer

- Pre/post record — When the frame is written to the video file (during recording)

These timestamps are recorded for every camera on every frame, plus timestamps for the assembled multi-camera payload.

## Output format​

When a recording completes, the RecordingFinalizer processes all accumulated timestamps and writes them as CSV files in human-readable format.

### Per-camera CSV columns​

Each camera gets its own CSV with one row per frame. Key columns include:

ColumnDescription

recording_frame_numberSequential frame index from recording start

timestamp.from_recording_start.secSeconds elapsed since recording began

timestamp.perf_counter_ns.nsRaw monotonic nanosecond timestamp

timestamp.utc.secondsUnix UTC timestamp in seconds

timestamp.local.iso8601Local time as ISO 8601 string

from_previous.frame_duration.msTime since previous frame

from_previous.framerate.hzInstantaneous FPS from frame interval

frame.pre_frame_grab.ns ... frame.post_frame_record.nsLifecycle stage timestamps

duration.during_frame_grab.ns ... duration.during_frame_record.nsDuration of each stage

### Multi-frame CSV​

An additional CSV aggregates statistics across all cameras for each frame event, including mean, median, standard deviation, and range of each lifecycle stage — plus the critical inter_camera.frame_grab_range.ms metric, which measures the temporal spread between cameras within each frame grab.

The timestamps use Python's time.perf_counter_ns(), which provides nanosecond resolution monotonic timing. While the absolute accuracy depends on the OS scheduler, the relative timing between events within a frame cycle is highly precise — typically sub-millisecond.

## Using timestamps in your analysis​

The timestamp data lets you:

- Measure the actual temporal spread between cameras within each frame event

- Verify that synchronization is working as expected

- Correlate frames with external data sources (IMU, force plates, etc.) by aligning UTC timestamps

- Quantify system performance (grab latency, retrieve latency, I/O latency)

- Why timestamps matter

- Precision matters for 3D reconstruction

- The timebase concept

- What SkellyCam records

- Output format

- Per-camera CSV columns

- Multi-frame CSV

- Using timestamps in your analysis
