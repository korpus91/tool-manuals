# Calibrate your cameras | FreeMoCap

Skip to main content

This is documentation for FreeMoCap 1.x (legacy), which is no longer actively maintained.

For up-to-date documentation, see the latest version (2.0 (alpha)).

Version: 1.x (legacy)

Human-checked documentationchecked against source

This page is adapted from real, human-written FreeMoCap documentation. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-19

v1 (ported, not yet re-checked against v2)

More about how these docs are written

# Calibrate your cameras

This calibration process describes the use of an anipose-based calibration method. We will soon be updating our method to use a more flexible and interactive interface.

 Video Guidance

Check out this video for more information and directed guidance in the calibration process

## Preparing the Charuco Board​

To perform a multi-camera calibration, you'll need to print out a Charuco board image.

For smaller spaces, a simple printout from a standard printer should work just fine. Make sure to mount the printout on something rigid like cardboard - the calibration process requires a flat charuco board.

For larger spaces, you might need to print this on a larger poster board so that it can be seen well by the cameras.

If you do not have access to a poster printer, you can assemble a larger board using these PDF template (just be sure to be accurate when cutting and assembling the pieces!)

### Charuco Board Types​

We support two configurations of Charuco board, based on the number of rows and columns of squares on the board.

We generally recommend using the 5x3 board for most applications. It has fewer squares so it will print larger for a given paper size, so it will be trackable from farther distances, which allows calibration of larger spaces.

5x3 Charuco Board (5 columns, 3 rows)7x5 Charuco Board (7 columns, 5 rows)

Download:
 PNG | SVG | Annotated

Download:
 PNG | SVG

## Setting up Cameras​

To get a multiple camera recording, you'll need multiple cameras set up and connected to your computer. There's detailed instructions on multiple camera setups in the Mocap Tips and Tricks, but for now it will suffice to have two or more (three or more is best) cameras connected directly to your camera. We don't recommend using a USB hub to connect cameras. The cameras should be set up so they all see the subject at the same time, and have a 40-60 degree angle between each camera from the subject's viewpoint.

## Using the Charuco board to set the recording origin​

By checking the Use initial board position checkbox, you can use the Charuco board to define the axes of the 3D world, so that the reconstructed data comes in with the person oriented 'up' and standing on the ground. See the ground plane calibration page for more information.

## Recording Calibration Videos​

In the camera view section of the GUI, select the calibration videos option:

Begin the recording, and then move until your Charuco board can be seen in the overlapping fields of view of at least two cameras at a time. Move the Charuco board up and down so that you are "painting" each camera's view with images of the board. Make sure that every camera has shared views of the board with at least one other camera. We will be using the corresponding views of the board with the other cameras to help localize the camera positions relative to each other, which is necessary for the 3D triangulation step later.

For more information about how to use the board to get a high quality calibration, see this video (it uses a different version of this software, but the same principles apply).

## Processing the Calibration​

Once you have given each camera a good view of the board shared with another camera, click "Stop Recording," and it will begin the calibration process automatically.

Be sure to keep an eye on the terminal that launched the GUI for helpful output, as the log at the bottom of the GUI screen does not capture all of the outputs yet. Note: The terminal only launches in this way on Windows.

## Recording Motion Capture Videos​

Once you have completed the calibration process, you are are ready to record motion capture videos!

Select "Record Motion Capture Videos" from the camera view section of the GUI, and then click "Record." Perform your movement, and then click "Stop." The software will automatically process the videos and generate a Blender scene with the output data!

To manually process/re-process the videos, use the Process Motion Capture Videos button in the Processing tab of the GUI.

- Preparing the Charuco Board

- Charuco Board Types

- Setting up Cameras

- Using the Charuco board to set the recording origin

- Recording Calibration Videos

- Processing the Calibration

- Recording Motion Capture Videos
