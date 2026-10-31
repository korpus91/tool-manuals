# FreeMoCap documentation | FreeMoCap

Skip to main content

# FreeMoCap

User documentation for the FreeMoCap project.

Get StartedWhat is FreeMoCap?Developer Docs

## Get Started

Install FreeMoCap and make your first recording.

## Beginner

Set up your cameras and record with one, then several.

## Intermediate

Dial in your calibration, choose a tracker, and process your data.

## Advanced

Specialization tracks.
DevTechnologyScienceArt

## Get Started

1?SetupTwo ways to install: pip for developers, or a packaged app for everyone else.2?RecordingStart with one camera before multi-camera. Simpler, faster, confirms your pipeline works.3?VisualizationCheck whether it worked: a skeleton moving in Blender, matching what you actually did.

## Beginner

1?Choose and set up your camerasOne camera minimum, three recommended, plus a ChArUco board for calibration.2?Record with one cameraStart with one camera before multi-camera. Simpler, faster, confirms your pipeline works.3?Calibrate your camerasPrint a ChArUco board and record it so FreeMoCap can place your cameras in space.

4?Record with multiple camerasCalibrate a camera array and capture real 3D motion instead of a single flat view.5?Find and read your outputEvery recording lands in its own folder. This is a map of what's actually in there.6?Open your recording in BlenderGet a rigged, animated skeleton into a 3D scene, automatically or by hand.

## Intermediate

?Get a calibration you can trustHabits that make a bad calibration less likely in the first place.?Set the ground planeSets the 3D world so "up" means up and the ground is where it should be.?Choose a tracking modelFreeMoCap runs on several pose estimation backends without changing your pipeline.?Filter and fill your dataWhat happens to a recording before it reaches you as output.?Optimize your capture spaceLighting, background, and camera placement tips that meaningfully improve tracking.?Analyze your data in PythonLoad a recording into a notebook and compute the numbers yourself.?Build a custom pipelineFreeMoCap's backend runs on two different pipelines; know the difference before you customize.?Process many recordings at onceFreeMoCap V2 has no built-in batch mode yet, here is what to do in the meantime.

## Advanced

### FMC Dev

Developer pages on this site

?Architecture overviewA React desktop app talks to a Python backend, with the sub-skelly libraries underneath.?The Skelly componentsFour standalone libraries, each owning one stage of the pipeline.?Follow one recording e2eTrace one recording from the first camera frame to the final Blender scene.?Data contractsWhat each Skelly component expects, and what it hands to the next one.?All repositoriesEvery repository in the FreeMoCap org, what it owns, and how they depend on each other.?ContributeSet up a dev environment, follow GitHub Flow, open your first pull request.?Array shapes and unitsExact array shapes, dtypes, and units, generated straight from the code.?REST APIEndpoints for controlling recordings, calibration, and processing from outside the GUI.?WebSocket APIReal-time updates for live camera previews and processing status.

### Technology

Upcoming Skelly University course (GitHub stub)

?SkellyCamThe camera backend: synchronized multi-camera video capture and detection.?SkellyTrackerThe pose estimation backend: one unified API across multiple tracking models.?SkellyForgePost-processing: filtering, interpolation, and 3D reconstruction of tracked points.?SkellyBlenderThe Blender integration: visualizing and working with motion capture data.?FreeMoCap CoreThe main application: orchestrates the entire motion capture pipeline.

### Science

Upcoming Skelly University course (GitHub stub)

?MeasurementFundamental measurement concepts for motion capture research.?Data AnalysisSignal processing and analysis workflows for motion capture data.?BiomechanicsThe mechanical laws relating to movement and the structure of living organisms.?NeuroscienceThe neural control of movement and perceptuo-motor processes.

### Art

Upcoming Skelly University course (GitHub stub)

?AnimationUsing motion capture for character animation in Blender and other 3D software.?Game DevUsing motion capture for game character animation and interactive applications.

## Coming Soon

### Skelly University

A course-based path through markerless motion capture from first recording to specialized tracks in technology, science, and art. Will offer microcertification.
Read more

## Papers, talks, and community

### Cite and read

- Cite FreeMoCap

- Zenodo record

- Accuracy and limits

### Community

- Discord

- YouTube

- freemocap.org

### Project

- About FreeMoCap

- Code of conduct

- How these docs are written

- Roadmap
