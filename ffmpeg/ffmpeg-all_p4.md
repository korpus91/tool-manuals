Show fields and transforms in the resulting frames. It accepts an integer in the range 0-2. Default value is 0, which disables any visualization.

fileformat

Format for the transforms data file to be written. Acceptable values are

‘ascii’

Human-readable plain text

‘binary’

Binary format, roughly 40% smaller than ascii. (default)

#### 39.275.1 Examples# TOC

- Use default values:

```
vidstabdetect

```

- Analyze strongly shaky movie and put the results in file mytransforms.trf:

```
vidstabdetect=shakiness=10:accuracy=15:result="mytransforms.trf"

```

- Visualize the result of internal transformations in the resulting video:

```
vidstabdetect=show=1

```

- Analyze a video with medium shakiness using ffmpeg:

```
ffmpeg -i input -vf vidstabdetect=shakiness=5:show=1 dummy.avi

```

### 39.276 vidstabtransform# TOC

Video stabilization/deshaking: pass 2 of 2, see vidstabdetect for pass 1.

Read a file with transform information for each frame and apply/compensate them. Together with the vidstabdetect filter this can be used to deshake videos. See also http://public.hronopik.de/vid.stab. It is important to also use the unsharp filter, see below.

To enable compilation of this filter you need to configure FFmpeg with --enable-libvidstab.

#### 39.276.1 Options# TOC

input

Set path to the file used to read the transforms. Default value is transforms.trf.

smoothing

Set the number of frames (value*2 + 1) used for lowpass filtering the camera movements. Default value is 10.

For example a number of 10 means that 21 frames are used (10 in the past and 10 in the future) to smoothen the motion in the video. A larger value leads to a smoother video, but limits the acceleration of the camera (pan/tilt movements). 0 is a special case where a static camera is simulated.

optalgo

Set the camera path optimization algorithm.

Accepted values are:

‘gauss’

gaussian kernel low-pass filter on camera motion (default)

‘avg’

averaging on transformations

maxshift

Set maximal number of pixels to translate frames. Default value is -1, meaning no limit.

maxangle

Set maximal angle in radians (degree*PI/180) to rotate frames. Default value is -1, meaning no limit.

crop

Specify how to deal with borders that may be visible due to movement compensation.

Available values are:

‘keep’

keep image information from previous frame (default)

‘black’

fill the border black

invert

Invert transforms if set to 1. Default value is 0.

relative

Consider transforms as relative to previous frame if set to 1, absolute if set to 0. Default value is 0.

zoom

Set percentage to zoom. A positive value will result in a zoom-in effect, a negative value in a zoom-out effect. Default value is 0 (no zoom).

optzoom

Set optimal zooming to avoid borders.

Accepted values are:

‘0’

disabled

‘1’

optimal static zoom value is determined (only very strong movements will lead to visible borders) (default)

‘2’

optimal adaptive zoom value is determined (no borders will be visible), see zoomspeed

Note that the value given at zoom is added to the one calculated here.

zoomspeed

Set percent to zoom maximally each frame (enabled when optzoom is set to 2). Range is from 0 to 5, default value is 0.25.

interpol

Specify type of interpolation.

Available values are:

‘no’

no interpolation

‘linear’

linear only horizontal

‘bilinear’

linear in both directions (default)

‘bicubic’

cubic in both directions (slow)

tripod

Enable virtual tripod mode if set to 1, which is equivalent to relative=0:smoothing=0. Default value is 0.

Use also tripod option of vidstabdetect.

debug

Increase log verbosity if set to 1. Also the detected global motions are written to the temporary file global_motions.trf. Default value is 0.

#### 39.276.2 Examples# TOC

- Use ffmpeg for a typical stabilization with default values:

```
ffmpeg -i inp.mpeg -vf vidstabtransform,unsharp=5:5:0.8:3:3:0.4 inp_stabilized.mpeg

```

Note the use of the unsharp filter which is always recommended.

- Zoom in a bit more and load transform data from a given file:

```
vidstabtransform=zoom=5:input="mytransforms.trf"

```

- Smoothen the video even more:

```
vidstabtransform=smoothing=30

```

### 39.277 vflip# TOC

Flip the input video vertically.

For example, to vertically flip a video with ffmpeg:

```
ffmpeg -i in.avi -vf "vflip" out.avi

```

### 39.278 vfrdet# TOC

Detect variable frame rate video.

This filter tries to detect if the input is variable or constant frame rate.

At end it will output number of frames detected as having variable delta pts, and ones with constant delta pts. If there was frames with variable delta, than it will also show min, max and average delta encountered.

### 39.279 vibrance# TOC

Boost or alter saturation.

The filter accepts the following options:

intensity

Set strength of boost if positive value or strength of alter if negative value. Default is 0. Allowed range is from -2 to 2.

rbal

Set the red balance. Default is 1. Allowed range is from -10 to 10.

gbal

Set the green balance. Default is 1. Allowed range is from -10 to 10.

bbal

Set the blue balance. Default is 1. Allowed range is from -10 to 10.

rlum

Set the red luma coefficient.

glum

Set the green luma coefficient.

blum

Set the blue luma coefficient.

alternate

If intensity is negative and this is set to 1, colors will change, otherwise colors will be less saturated, more towards gray.

#### 39.279.1 Commands# TOC

This filter supports the all above options as commands.

### 39.280 vif# TOC

Obtain the average VIF (Visual Information Fidelity) between two input videos.

This filter takes two input videos.

Both input videos must have the same resolution and pixel format for this filter to work correctly. Also it assumes that both inputs have the same number of frames, which are compared one by one.

The obtained average VIF score is printed through the logging system.

The filter stores the calculated VIF score of each frame.

This filter also supports the framesync options.

In the below example the input file main.mpg being processed is compared with the reference file ref.mpg.

```
ffmpeg -i main.mpg -i ref.mpg -lavfi vif -f null -

```

### 39.281 vignette# TOC

Make or reverse a natural vignetting effect.

The filter accepts the following options:

angle, a

Set lens angle expression as a number of radians.

The value is clipped in the [0,PI/2] range.

Default value: "PI/5"

x0

y0

Set center coordinates expressions. Respectively "w/2" and "h/2" by default.

mode

Set forward/backward mode.

Available modes are:

‘forward’

The larger the distance from the central point, the darker the image becomes.

‘backward’

The larger the distance from the central point, the brighter the image becomes. This can be used to reverse a vignette effect, though there is no automatic detection to extract the lens angle and other settings (yet). It can also be used to create a burning effect.

Default value is ‘forward’.

eval

Set evaluation mode for the expressions (angle, x0, y0).

It accepts the following values:

‘init’

Evaluate expressions only once during the filter initialization.

‘frame’

Evaluate expressions for each incoming frame. This is way slower than the ‘init’ mode since it requires all the scalers to be re-computed, but it allows advanced dynamic expressions.

Default value is ‘init’.

dither

Set dithering to reduce the circular banding effects. Default is 1 (enabled).

aspect

Set vignette aspect. This setting allows one to adjust the shape of the vignette. Setting this value to the SAR of the input will make a rectangular vignetting following the dimensions of the video.

Default is 1/1.

#### 39.281.1 Expressions# TOC

The alpha, x0 and y0 expressions can contain the following parameters.

w

h

input width and height

n

the number of input frame, starting from 0

pts

the PTS (Presentation TimeStamp) time of the filtered video frame, expressed in TB units, NAN if undefined

r

frame rate of the input video, NAN if the input frame rate is unknown

t

the PTS (Presentation TimeStamp) of the filtered video frame, expressed in seconds, NAN if undefined

tb

time base of the input video

#### 39.281.2 Examples# TOC

- Apply simple strong vignetting effect:

```
vignette=PI/4

```

- Make a flickering vignetting:

```
vignette='PI/4+random(1)*PI/50':eval=frame

```

### 39.282 vmafmotion# TOC

Obtain the average VMAF motion score of a video. It is one of the component metrics of VMAF.

The obtained average motion score is printed through the logging system.

The filter accepts the following options:

stats_file

If specified, the filter will use the named file to save the motion score of each frame with respect to the previous frame. When filename equals "-" the data is sent to standard output.

Example:

```
ffmpeg -i ref.mpg -vf vmafmotion -f null -

```

### 39.283 vpp_amf# TOC

Scale (resize) and convert colorspace, transfer characteristics or color primaries for the input video, using AMD Advanced Media Framework library for hardware acceleration. Setting the output width and height works in the same way as for the scale filter.

The filter accepts the following options:

w

h

Set the output video dimension expression. Default value is the input dimension.

Allows for the same expressions as the scale filter.

scale_type

Sets the algorithm used for scaling:

bilinear

Bilinear

This is the default.

bicubic

Bicubic

format

Controls the output pixel format. By default, or if none is specified, the input pixel format is used.

force_original_aspect_ratio

force_divisible_by

Work the same as the identical scale filter options.

reset_sar

Works the same as the identical scale filter option.

in_color_range

Override input color range.

out_color_range

Specify output color range.

The accepted values for in_trc and out_trc are:

‘studio’

Studio (or restricted, or MPEG) color range.

‘full’

Full (or JPEG) color range.

color_profile

Specify all color properties at once.

The accepted values are:

‘bt601’

BT.601

‘bt709’

BT.709

‘bt2020’

BT.2020

in_trc

Override input transfer characteristics.

out_trc

Specify output transfer characteristics.

The accepted values for in_trc and out_trc are:

‘bt709’

BT.709

‘gamma22’

Constant gamma of 2.2

‘gamma28’

Constant gamma of 2.8

‘smpte170m’

SMPTE-170M

‘smpte240m’

SMPTE-240M

‘linear’

Linear

‘log’

LOG

‘log-sqrt’

LOG_SQRT

‘iec61966-2-4’

iec61966-2-4

‘bt1361-ecg’

BT1361_ECG

‘iec61966-2-1’

iec61966-2-1

‘bt2020-10’

BT.2020 for 10-bits content

‘bt2020-12’

BT.2020 for 12-bits content

‘smpte2084’

SMPTE2084

‘smpte428’

SMPTE428

‘arib-std-b67’

ARIB_STD_B67

in_primaries

Override input color primaries.

out_primaries

Specify output color primaries.

The accepted values for in_primaries and out_primaries are:

‘bt709’

BT.709

‘bt470m’

BT.470M

‘bt470bg’

BT.470BG or BT.601-6 625

‘smpte170m’

SMPTE-170M or BT.601-6 525

‘smpte240m’

SMPTE-240M

‘film’

film

‘bt2020’

BT.2020

‘smpte428’

SMPTE-428

‘smpte431’

SMPTE-431

‘smpte432’

SMPTE-432

‘jedec-p22’

JEDEC P22 phosphors

#### 39.283.1 Examples# TOC

- Scale input to 720p, keeping aspect ratio and ensuring the output is yuv420p. The filter always outputs AMF surfaces, so a hwdownload is needed to feed a software encoder.

```
vpp_amf=-2:720:format=yuv420p,hwdownload,format=yuv420p

```

- Upscale to 4K and change color profile to bt2020.

```
vpp_amf=4096:2160:color_profile=bt2020

```

- Override input primaries and input transfer characteristics, change both to bt709.

```
vpp_amf=color_profile=bt2020:in_trc=smpte2084:in_primaries=bt2020:out_trc=bt709:out_primaries=bt709

```

### 39.284 vstack# TOC

Stack input videos vertically.

All streams must be of same pixel format and of same width.

Note that this filter is faster than using overlay and pad filter to create same output.

The filter accepts the following options:

inputs

Set number of input streams. Default is 2.

shortest

If set to 1, force the output to terminate when the shortest input terminates. Default value is 0.

### 39.285 w3fdif# TOC

Deinterlace the input video ("w3fdif" stands for "Weston 3 Field Deinterlacing Filter").

Based on the process described by Martin Weston for BBC R&D, and implemented based on the de-interlace algorithm written by Jim Easterbrook for BBC R&D, the Weston 3 field deinterlacing filter uses filter coefficients calculated by BBC R&D.

This filter uses field-dominance information in frame to decide which of each pair of fields to place first in the output. If it gets it wrong use setfield filter before w3fdif filter.

There are two sets of filter coefficients, so called "simple" and "complex". Which set of filter coefficients is used can be set by passing an optional parameter:

filter

Set the interlacing filter coefficients. Accepts one of the following values:

‘simple’

Simple filter coefficient set.

‘complex’

More-complex filter coefficient set.

Default value is ‘complex’.

mode

The interlacing mode to adopt. It accepts one of the following values:

frame

Output one frame for each frame.

field

Output one frame for each field.

The default value is field.

parity

The picture field parity assumed for the input interlaced video. It accepts one of the following values:

tff

Assume the top field is first.

bff

Assume the bottom field is first.

auto

Enable automatic detection of field parity.

The default value is auto. If the interlacing is unknown or the decoder does not export this information, top field first will be assumed.

deint

Specify which frames to deinterlace. Accepts one of the following values:

‘all’

Deinterlace all frames,

‘interlaced’

Only deinterlace frames marked as interlaced.

Default value is ‘all’.

#### 39.285.1 Commands# TOC

This filter supports same commands as options.

### 39.286 waveform# TOC

Video waveform monitor.

The waveform monitor plots color component intensity. By default luma only. Each column of the waveform corresponds to a column of pixels in the source video.

It accepts the following options:

mode, m

Can be either row, or column. Default is column. In row mode, the graph on the left side represents color component value 0 and the right side represents value = 255. In column mode, the top side represents color component value = 0 and bottom side represents value = 255.

intensity, i

Set intensity. Smaller values are useful to find out how many values of the same luminance are distributed across input rows/columns. Default value is 0.04. Allowed range is [0, 1].

mirror, r

Set mirroring mode. 0 means unmirrored, 1 means mirrored. In mirrored mode, higher values will be represented on the left side for row mode and at the top for column mode. Default is 1 (mirrored).

display, d

Set display mode. It accepts the following values:

‘overlay’

Presents information identical to that in the parade, except that the graphs representing color components are superimposed directly over one another.

This display mode makes it easier to spot relative differences or similarities in overlapping areas of the color components that are supposed to be identical, such as neutral whites, grays, or blacks.

‘stack’

Display separate graph for the color components side by side in row mode or one below the other in column mode.

‘parade’

Display separate graph for the color components side by side in column mode or one below the other in row mode.

Using this display mode makes it easy to spot color casts in the highlights and shadows of an image, by comparing the contours of the top and the bottom graphs of each waveform. Since whites, grays, and blacks are characterized by exactly equal amounts of red, green, and blue, neutral areas of the picture should display three waveforms of roughly equal width/height. If not, the correction is easy to perform by making level adjustments the three waveforms.

Default is stack.

components, c

Set which color components to display. Default is 1, which means only luma or red color component if input is in RGB colorspace. If is set for example to 7 it will display all 3 (if) available color components.

envelope, e

‘none’

No envelope, this is default.

‘instant’

Instant envelope, minimum and maximum values presented in graph will be easily visible even with small step value.

‘peak’

Hold minimum and maximum values presented in graph across time. This way you can still spot out of range values without constantly looking at waveforms.

‘peak+instant’

Peak and instant envelope combined together.

filter, f

‘lowpass’

No filtering, this is default.

‘flat’

Luma and chroma combined together.

‘aflat’

Similar as above, but shows difference between blue and red chroma.

‘xflat’

Similar as above, but use different colors.

‘yflat’

Similar as above, but again with different colors.

‘chroma’

Displays only chroma.

‘color’

Displays actual color value on waveform.

‘acolor’

Similar as above, but with luma showing frequency of chroma values.

graticule, g

Set which graticule to display.

‘none’

Do not display graticule.

‘green’

Display green graticule showing legal broadcast ranges.

‘orange’

Display orange graticule showing legal broadcast ranges.

‘invert’

Display invert graticule showing legal broadcast ranges.

opacity, o

Set graticule opacity.

flags, fl

Set graticule flags.

‘numbers’

Draw numbers above lines. By default enabled.

‘dots’

Draw dots instead of lines.

scale, s

Set scale used for displaying graticule.

‘digital’

‘millivolts’

‘ire’

Default is digital.

bgopacity, b

Set background opacity.

tint0, t0

tint1, t1

Set tint for output. Only used with lowpass filter and when display is not overlay and input pixel formats are not RGB.

fitmode, fm

Set sample aspect ratio of video output frames. Can be used to configure waveform so it is not stretched too much in one of directions.

‘none’

Set sample aspect ration to 1/1.

‘size’

Set sample aspect ratio to match input size of video

Default is ‘none’.

input

Set input formats for filter to pick from. Can be ‘all’, for selecting from all available formats, or ‘first’, for selecting first available format. Default is ‘first’.

### 39.287 weave, doubleweave# TOC

The weave takes a field-based video input and join each two sequential fields into single frame, producing a new double height clip with half the frame rate and half the frame count.

The doubleweave works same as weave but without halving frame rate and frame count.

It accepts the following option:

first_field

Set first field. Available values are:

‘top, t’

Set the frame as top-field-first.

‘bottom, b’

Set the frame as bottom-field-first.

#### 39.287.1 Examples# TOC

- Interlace video using select and separatefields filter:

```
separatefields,select=eq(mod(n,4),0)+eq(mod(n,4),3),weave

```

### 39.288 xbr# TOC

Apply the xBR high-quality magnification filter which is designed for pixel art. It follows a set of edge-detection rules, see https://forums.libretro.com/t/xbr-algorithm-tutorial/123.

It accepts the following option:

n

Set the scaling dimension: 2 for 2xBR, 3 for 3xBR and 4 for 4xBR. Default is 3.

### 39.289 xcorrelate# TOC

Apply normalized cross-correlation between first and second input video stream.

Second input video stream dimensions must be lower than first input video stream.

The filter accepts the following options:

planes

Set which planes to process.

secondary

Set which secondary video frames will be processed from second input video stream, can be first or all. Default is all.

The xcorrelate filter also supports the framesync options.

### 39.290 xfade# TOC

Apply cross fade from one input video stream to another input video stream. The cross fade is applied for specified duration.

Both inputs must be constant frame-rate and have the same resolution, pixel format, frame rate and timebase.

The filter accepts the following options:

transition

Set one of available transition effects:

‘custom’

‘fade’

‘wipeleft’

‘wiperight’

‘wipeup’

‘wipedown’

‘slideleft’

‘slideright’

‘slideup’

‘slidedown’

‘circlecrop’

‘rectcrop’

‘distance’

‘fadeblack’

‘fadewhite’

‘radial’

‘smoothleft’

‘smoothright’

‘smoothup’

‘smoothdown’

‘circleopen’

‘circleclose’

‘vertopen’

‘vertclose’

‘horzopen’

‘horzclose’

‘dissolve’

‘pixelize’

‘diagtl’

‘diagtr’

‘diagbl’

‘diagbr’

‘hlslice’

‘hrslice’

‘vuslice’

‘vdslice’

‘hblur’

‘fadegrays’

‘wipetl’

‘wipetr’

‘wipebl’

‘wipebr’

‘squeezeh’

‘squeezev’

‘zoomin’

‘fadefast’

‘fadeslow’

‘hlwind’

‘hrwind’

‘vuwind’

‘vdwind’

‘coverleft’

‘coverright’

‘coverup’

‘coverdown’

‘revealleft’

‘revealright’

‘revealup’

‘revealdown’

Default transition effect is fade.

duration

Set cross fade duration in seconds. Range is 0 to 60 seconds. Default duration is 1 second.

offset

Set cross fade start relative to first input stream in seconds. Default offset is 0.

expr

Set expression for custom transition effect.

The expressions can use the following variables and functions:

X

Y

The coordinates of the current sample.

W

H

The width and height of the image.

P

Progress of transition effect.

PLANE

Currently processed plane.

A

Return value of first input at current location and plane.

B

Return value of second input at current location and plane.

a0(x, y)

a1(x, y)

a2(x, y)

a3(x, y)

Return the value of the pixel at location (x,y) of the first/second/third/fourth component of first input.

b0(x, y)

b1(x, y)

b2(x, y)

b3(x, y)

Return the value of the pixel at location (x,y) of the first/second/third/fourth component of second input.

#### 39.290.1 Examples# TOC

- Cross fade from one input video to another input video, with fade transition and duration of transition of 2 seconds starting at offset of 5 seconds:

```
ffmpeg -i first.mp4 -i second.mp4 -filter_complex xfade=transition=fade:duration=2:offset=5 output.mp4

```

### 39.291 xmedian# TOC

Pick median pixels from several input videos.

The filter accepts the following options:

inputs

Set number of inputs. Default is 3. Allowed range is from 3 to 255. If number of inputs is even number, than result will be mean value between two median values.

planes

Set which planes to filter. Default value is 15, by which all planes are processed.

percentile

Set median percentile. Default value is 0.5. Default value of 0.5 will pick always median values, while 0 will pick minimum values, and 1 maximum values.

#### 39.291.1 Commands# TOC

This filter supports all above options as commands, excluding option inputs.

### 39.292 xpsnr# TOC

Obtain the average (across all input frames) and minimum (across all color plane averages) eXtended Perceptually weighted peak Signal-to-Noise Ratio (XPSNR) between two input videos.

The XPSNR is a low-complexity psychovisually motivated distortion measurement algorithm for assessing the difference between two video streams or images. This is especially useful for objectively quantifying the distortions caused by video and image codecs, as an alternative to a formal subjective test. The logarithmic XPSNR output values are in a similar range as those of traditional psnr assessments but better reflect human impressions of visual coding quality. More details on the XPSNR measure, which essentially represents a blockwise weighted variant of the PSNR measure, can be found in the following freely available papers:

- C. R. Helmrich, M. Siekmann, S. Becker, S. Bosse, D. Marpe, and T. Wiegand, "XPSNR: A Low-Complexity Extension of the Perceptually Weighted Peak Signal-to-Noise Ratio for High-Resolution Video Quality Assessment," in Proc. IEEE Int. Conf. Acoustics, Speech, Sig. Process. (ICASSP), virt./online, May 2020. www.ecodis.de/xpsnr.htm

- C. R. Helmrich, S. Bosse, H. Schwarz, D. Marpe, and T. Wiegand, "A Study of the Extended Perceptually Weighted Peak Signal-to-Noise Ratio (XPSNR) for Video Compression with Different Resolutions and Bit Depths," ITU Journal: ICT Discoveries, vol. 3, no. 1, pp. 65 - 72, May 2020. http://handle.itu.int/11.1002/pub/8153d78b-en

When publishing the results of XPSNR assessments obtained using, e.g., this FFmpeg filter, a reference to the above papers as a means of documentation is strongly encouraged. The filter requires two input videos. The first input is considered a (usually not distorted) reference source and is passed unchanged to the output, whereas the second input is a (distorted) test signal. Except for the bit depth, these two video inputs must have the same pixel format. In addition, for best performance, both compared input videos should be in YCbCr color format.

The obtained overall XPSNR values mentioned above are printed through the logging system. In case of input with multiple color planes, we suggest reporting of the minimum XPSNR average.

The following parameter, which behaves like the one for the psnr filter, is accepted:

stats_file, f

If specified, the filter will use the named file to save the XPSNR value of each individual frame and color plane. When the file name equals "-", that data is sent to standard output.

This filter also supports the framesync options.

#### 39.292.1 Examples# TOC

- XPSNR analysis of two 1080p HD videos, ref_source.yuv and test_video.yuv, both at 24 frames per second, with color format 4:2:0, bit depth 8, and output of a logfile named "xpsnr.log":

```
ffmpeg -s 1920x1080 -framerate 24 -pix_fmt yuv420p -i ref_source.yuv -s 1920x1080 -framerate
24 -pix_fmt yuv420p -i test_video.yuv -lavfi xpsnr="stats_file=xpsnr.log" -f null -

```

- XPSNR analysis of two 2160p UHD videos, ref_source.yuv with bit depth 8 and test_video.yuv with bit depth 10, both at 60 frames per second with color format 4:2:0, no logfile output:

```
ffmpeg -s 3840x2160 -framerate 60 -pix_fmt yuv420p -i ref_source.yuv -s 3840x2160 -framerate
60 -pix_fmt yuv420p10le -i test_video.yuv -lavfi xpsnr="stats_file=-" -f null -

```

### 39.293 xstack# TOC

Stack video inputs into custom layout.

All streams must be of same pixel format.

The filter accepts the following options:

inputs

Set number of input streams. Default is 2.

layout

Specify layout of inputs. This option requires the desired layout configuration to be explicitly set by the user. This sets position of each video input in output. Each input is separated by ’|’. The first number represents the column, and the second number represents the row. Numbers start at 0 and are separated by ’_’. Optionally one can use wX and hX, where X is video input from which to take width or height. Multiple values can be used when separated by ’+’. In such case values are summed together.

Note that if inputs are of different sizes gaps may appear, as not all of the output video frame will be filled. Similarly, videos can overlap each other if their position doesn’t leave enough space for the full frame of adjoining videos.

For 2 inputs, a default layout of 0_0|w0_0 (equivalent to grid=2x1) is set. In all other cases, a layout or a grid must be set by the user. Either grid or layout can be specified at a time. Specifying both will result in an error.

grid

Specify a fixed size grid of inputs. This option is used to create a fixed size grid of the input streams. Set the grid size in the form COLUMNSxROWS. There must be ROWS * COLUMNS input streams and they will be arranged as a grid with ROWS rows and COLUMNS columns. When using this option, each input stream within a row must have the same height and all the rows must have the same width.

If grid is set, then inputs option is ignored and is implicitly set to ROWS * COLUMNS.

For 2 inputs, a default grid of 2x1 (equivalent to layout=0_0|w0_0) is set. In all other cases, a layout or a grid must be set by the user. Either grid or layout can be specified at a time. Specifying both will result in an error.

shortest

If set to 1, force the output to terminate when the shortest input terminates. Default value is 0.

fill

If set to valid color, all unused pixels will be filled with that color. By default fill is set to none, so it is disabled.

#### 39.293.1 Examples# TOC

- Display 4 inputs into 2x2 grid.
Layout:

```
input1(0, 0)  | input3(w0, 0)
input2(0, h0) | input4(w0, h0)

```

```
xstack=inputs=4:layout=0_0|0_h0|w0_0|w0_h0

```

Note that if inputs are of different sizes, gaps or overlaps may occur.

- Display 4 inputs into 1x4 grid.
Layout:

```
input1(0, 0)
input2(0, h0)
input3(0, h0+h1)
input4(0, h0+h1+h2)

```

```
xstack=inputs=4:layout=0_0|0_h0|0_h0+h1|0_h0+h1+h2

```

Note that if inputs are of different widths, unused space will appear.

- Display 9 inputs into 3x3 grid.
Layout:

```
input1(0, 0)       | input4(w0, 0)      | input7(w0+w3, 0)
input2(0, h0)      | input5(w0, h0)     | input8(w0+w3, h0)
input3(0, h0+h1)   | input6(w0, h0+h1)  | input9(w0+w3, h0+h1)

```

```
xstack=inputs=9:layout=0_0|0_h0|0_h0+h1|w0_0|w0_h0|w0_h0+h1|w0+w3_0|w0+w3_h0|w0+w3_h0+h1

```

Note that if inputs are of different sizes, gaps or overlaps may occur.

- Display 16 inputs into 4x4 grid.
Layout:

```
input1(0, 0)       | input5(w0, 0)       | input9 (w0+w4, 0)       | input13(w0+w4+w8, 0)
input2(0, h0)      | input6(w0, h0)      | input10(w0+w4, h0)      | input14(w0+w4+w8, h0)
input3(0, h0+h1)   | input7(w0, h0+h1)   | input11(w0+w4, h0+h1)   | input15(w0+w4+w8, h0+h1)
input4(0, h0+h1+h2)| input8(w0, h0+h1+h2)| input12(w0+w4, h0+h1+h2)| input16(w0+w4+w8, h0+h1+h2)

```

```
xstack=inputs=16:layout=0_0|0_h0|0_h0+h1|0_h0+h1+h2|w0_0|w0_h0|w0_h0+h1|w0_h0+h1+h2|w0+w4_0|
w0+w4_h0|w0+w4_h0+h1|w0+w4_h0+h1+h2|w0+w4+w8_0|w0+w4+w8_h0|w0+w4+w8_h0+h1|w0+w4+w8_h0+h1+h2

```

Note that if inputs are of different sizes, gaps or overlaps may occur.

### 39.294 yadif# TOC

Deinterlace the input video ("yadif" means "yet another deinterlacing filter").

It accepts the following parameters:

mode

The interlacing mode to adopt. It accepts one of the following values:

0, send_frame

Output one frame for each frame.

1, send_field

Output one frame for each field.

2, send_frame_nospatial

Like send_frame, but it skips the spatial interlacing check.

3, send_field_nospatial

Like send_field, but it skips the spatial interlacing check.

The default value is send_frame.

parity

The picture field parity assumed for the input interlaced video. It accepts one of the following values:

0, tff

Assume the top field is first.

1, bff

Assume the bottom field is first.

-1, auto

Enable automatic detection of field parity.

The default value is auto. If the interlacing is unknown or the decoder does not export this information, top field first will be assumed.

deint

Specify which frames to deinterlace. Accepts one of the following values:

0, all

Deinterlace all frames.

1, interlaced

Only deinterlace frames marked as interlaced.

The default value is all.

### 39.295 yaepblur# TOC

Apply blur filter while preserving edges ("yaepblur" means "yet another edge preserving blur filter"). The algorithm is described in "J. S. Lee, Digital image enhancement and noise filtering by use of local statistics, IEEE Trans. Pattern Anal. Mach. Intell. PAMI-2, 1980."

It accepts the following parameters:

radius, r

Set the window radius. Default value is 3.

planes, p

Set which planes to filter. Default is only the first plane.

sigma, s

Set blur strength. Default value is 128.

#### 39.295.1 Commands# TOC

This filter supports same commands as options.

### 39.296 zoompan# TOC

Apply Zoom & Pan effect.

This filter accepts the following options:

zoom, z

Set the zoom expression. Range is 1-10. Default is 1.

x

y

Set the x and y expression. Default is 0.

d

Set the duration expression in number of frames. This sets for how many number of frames effect will last for single input image. Default is 90.

s

Set the output image size, default is ’hd720’.

fps

Set the output frame rate, default is ’25’.

Each expression can contain the following constants:

in_w, iw

Input width.

in_h, ih

Input height.

out_w, ow

Output width.

out_h, oh

Output height.

in

Input frame count.

on

Output frame count.

in_time, it

The input timestamp expressed in seconds. It’s NAN if the input timestamp is unknown.

out_time, time, ot

The output timestamp expressed in seconds.

x

y

Last calculated ’x’ and ’y’ position from ’x’ and ’y’ expression for current input frame.

px

py

’x’ and ’y’ of last output frame of previous input frame or 0 when there was not yet such frame (first input frame).

zoom

Last calculated zoom from ’z’ expression for current input frame.

pzoom

Last calculated zoom of last output frame of previous input frame.

duration

Number of output frames for current input frame. Calculated from ’d’ expression for each input frame.

pduration

number of output frames created for previous input frame

a

Rational number: input width / input height

sar

sample aspect ratio

dar

display aspect ratio

#### 39.296.1 Examples# TOC

- Zoom in up to 1.5x and pan at same time to some spot near center of picture:

```
zoompan=z='min(zoom+0.0015,1.5)':d=700:x='if(gte(zoom,1.5),x,x+1/a)':y='if(gte(zoom,1.5),y,y+1)':s=640x360

```

- Zoom in up to 1.5x and pan always at center of picture:

```
zoompan=z='min(zoom+0.0015,1.5)':d=700:x='iw/2-(iw/zoom/2)':y='ih/2-(ih/zoom/2)'

```

- Same as above but without pausing:

```
zoompan=z='min(max(zoom,pzoom)+0.0015,1.5)':d=1:x='iw/2-(iw/zoom/2)':y='ih/2-(ih/zoom/2)'

```

- Zoom in 2x into center of picture only for the first second of the input video:

```
zoompan=z='if(between(in_time,0,1),2,1)':d=1:x='iw/2-(iw/zoom/2)':y='ih/2-(ih/zoom/2)'

```

### 39.297 zscale# TOC

Scale (resize) the input video, using the z.lib library: https://github.com/sekrit-twc/zimg. To enable compilation of this filter, you need to configure FFmpeg with --enable-libzimg.

The zscale filter forces the output display aspect ratio to be the same as the input, by changing the output sample aspect ratio.

If the input image format is different from the format requested by the next filter, the zscale filter will convert the input to the requested format.

#### 39.297.1 Options# TOC

The filter accepts the following options.

width, w

height, h

Set the output video dimension expression. Default value is the input dimension.

If the width or w value is 0, the input width is used for the output. If the height or h value is 0, the input height is used for the output.

If one and only one of the values is -n with n >= 1, the zscale filter will use a value that maintains the aspect ratio of the input image, calculated from the other specified dimension. After that it will, however, make sure that the calculated dimension is divisible by n and adjust the value if necessary.

If both values are -n with n >= 1, the behavior will be identical to both values being set to 0 as previously detailed.

See below for the list of accepted constants for use in the dimension expression.

size, s

Set the video size. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual.

dither, d

Set the dither type.

Possible values are:

none

ordered

random

error_diffusion

Default is none.

filter, f

Set the resize filter type.

Possible values are:

point

bilinear

bicubic

spline16

spline36

spline64

lanczos

Default is bilinear.

range, r

Set the color range.

Possible values are:

input

limited

full

Default is same as input.

primaries, p

Set the color primaries.

Possible values are:

input

709

unspecified

170m

240m

2020

Default is same as input.

transfer, t

Set the transfer characteristics.

Possible values are:

input

709

unspecified

601

linear

2020_10

2020_12

smpte2084

iec61966-2-1

arib-std-b67

Default is same as input.

matrix, m

Set the colorspace matrix.

Possible value are:

input

709

unspecified

470bg

170m

2020_ncl

2020_cl

Default is same as input.

rangein, rin

Set the input color range.

Possible values are:

input

limited

full

Default is same as input.

primariesin, pin

Set the input color primaries.

Possible values are:

input

709

unspecified

170m

240m

2020

Default is same as input.

transferin, tin

Set the input transfer characteristics.

Possible values are:

input

709

unspecified

601

linear

2020_10

2020_12

Default is same as input.

matrixin, min

Set the input colorspace matrix.

Possible value are:

input

709

unspecified

470bg

170m

2020_ncl

2020_cl

chromal, c

Set the output chroma location.

Possible values are:

input

left

center

topleft

top

bottomleft

bottom

chromalin, cin

Set the input chroma location.

Possible values are:

input

left

center

topleft

top

bottomleft

bottom

npl

Set the nominal peak luminance.

param_a

Parameter A for scaling filters. Parameter "b" for bicubic, and the number of filter taps for lanczos.

param_b

Parameter B for scaling filters. Parameter "c" for bicubic.

The values of the w and h options are expressions containing the following constants:

in_w

in_h

The input width and height

iw

ih

These are the same as in_w and in_h.

out_w

out_h

The output (scaled) width and height

ow

oh

These are the same as out_w and out_h

a

The same as iw / ih

sar

input sample aspect ratio

dar

The input display aspect ratio. Calculated from (iw / ih) * sar.

hsub

vsub

horizontal and vertical input chroma subsample values. For example for the pixel format "yuv422p" hsub is 2 and vsub is 1.

ohsub

ovsub

horizontal and vertical output chroma subsample values. For example for the pixel format "yuv422p" hsub is 2 and vsub is 1.

#### 39.297.2 Commands# TOC

This filter supports the following commands:

width, w

height, h

Set the output video dimension expression. The command accepts the same syntax of the corresponding option.

If the specified expression is not valid, it is kept at its current value.

## 40 CUDA Video Filters# TOC

Below is a description of the currently available Nvidia CUDA video filters.

Prerequisites:

- Install Nvidia CUDA Toolkit

Note: If FFmpeg detects the Nvidia CUDA Toolkit during configuration, it will enable CUDA filters automatically without requiring any additional flags. If you want to explicitly enable them, use the following options:

- Configure FFmpeg with --enable-cuda-nvcc --enable-nonfree.

- Configure FFmpeg with --enable-cuda-llvm. Additional requirement: llvm lib must be installed.

Running CUDA filters requires you to initialize a hardware device and to pass that device to all filters in any filter graph.

-init_hw_device cuda[=name][:device[,key=value...]]

Initialise a new hardware device of type cuda called name, using the given device parameters.

-filter_hw_device name

Pass the hardware device called name to all filters in any filter graph.

For more detailed information see https://www.ffmpeg.org/ffmpeg.html#Advanced-Video-options

- Example of initializing second CUDA device on the system and running scale_cuda and bilateral_cuda filters.

```
./ffmpeg -hwaccel cuda -hwaccel_output_format cuda -i input.mp4 -init_hw_device cuda:1 -filter_complex \
"[0:v]scale_cuda=format=yuv444p[scaled_video];[scaled_video]bilateral_cuda=window_size=9:sigmaS=3.0:sigmaR=50.0" \
-an -sn -c:v h264_nvenc -cq 20 out.mp4

```

Since CUDA filters operate exclusively on GPU memory, frame data must sometimes be uploaded (hwupload) to hardware surfaces associated with the appropriate CUDA device before processing, and downloaded (hwdownload) back to normal memory afterward, if required. Whether hwupload or hwdownload is necessary depends on the specific workflow:

- If the input frames are already in GPU memory (e.g., when using -hwaccel cuda or -hwaccel_output_format cuda), explicit use of hwupload is not needed, as the data is already in the appropriate memory space.

- If the input frames are in CPU memory (e.g., software-decoded frames or frames processed by CPU-based filters), it is necessary to use hwupload to transfer the data to GPU memory for CUDA processing.

- If the output of the CUDA filters needs to be further processed by software-based filters or saved in a format not supported by GPU-based encoders, hwdownload is required to transfer the data back to CPU memory.

Note that hwupload uploads data to a surface with the same layout as the software frame, so it may be necessary to add a format filter immediately before hwupload to ensure the input is in the correct format. Similarly, hwdownload may not support all output formats, so an additional format filter may need to be inserted immediately after hwdownload in the filter graph to ensure compatibility.

### 40.1 bilateral_cuda# TOC

CUDA accelerated bilateral filter, an edge preserving filter. This filter is mathematically accurate thanks to the use of GPU acceleration. For best output quality, use one to one chroma subsampling, i.e. yuv444p format.

The filter accepts the following options:

sigmaS

Set sigma of gaussian function to calculate spatial weight, also called sigma space. Allowed range is 0.1 to 512. Default is 0.1.

sigmaR

Set sigma of gaussian function to calculate color range weight, also called sigma color. Allowed range is 0.1 to 512. Default is 0.1.

window_size

Set window size of the bilateral function to determine the number of neighbours to loop on. If the number entered is even, one will be added automatically. Allowed range is 1 to 255. Default is 1.

#### 40.1.1 Examples# TOC

- Apply the bilateral filter on a video.

```
./ffmpeg -v verbose \
-hwaccel cuda -hwaccel_output_format cuda -i input.mp4  \
-init_hw_device cuda \
-filter_complex \
" \
[0:v]scale_cuda=format=yuv444p[scaled_video];
[scaled_video]bilateral_cuda=window_size=9:sigmaS=3.0:sigmaR=50.0" \
-an -sn -c:v h264_nvenc -cq 20 out.mp4

```

### 40.2 bwdif_cuda# TOC

Deinterlace the input video using the bwdif algorithm, but implemented in CUDA so that it can work as part of a GPU accelerated pipeline with nvdec and/or nvenc.

It accepts the following parameters:

mode

The interlacing mode to adopt. It accepts one of the following values:

0, send_frame

Output one frame for each frame.

1, send_field

Output one frame for each field.

The default value is send_field.

parity

The picture field parity assumed for the input interlaced video. It accepts one of the following values:

0, tff

Assume the top field is first.

1, bff

Assume the bottom field is first.

-1, auto

Enable automatic detection of field parity.

The default value is auto. If the interlacing is unknown or the decoder does not export this information, top field first will be assumed.

deint

Specify which frames to deinterlace. Accepts one of the following values:

0, all

Deinterlace all frames.

1, interlaced

Only deinterlace frames marked as interlaced.

The default value is all.

### 40.3 chromakey_cuda# TOC

CUDA accelerated YUV colorspace color/chroma keying.

This filter works like normal chromakey filter but operates on CUDA frames. for more details and parameters see chromakey.

#### 40.3.1 Examples# TOC

- Make all the green pixels in the input video transparent and use it as an overlay for another video:

```
./ffmpeg \
    -hwaccel cuda -hwaccel_output_format cuda -i input_green.mp4  \
    -hwaccel cuda -hwaccel_output_format cuda -i base_video.mp4 \
    -init_hw_device cuda \
    -filter_complex \
    " \
        [0:v]chromakey_cuda=0x25302D:0.1:0.12:1[overlay_video]; \
        [1:v]scale_cuda=format=yuv420p[base]; \
        [base][overlay_video]overlay_cuda" \
    -an -sn -c:v h264_nvenc -cq 20 output.mp4

```

- Process two software sources, explicitly uploading the frames:

```
./ffmpeg -init_hw_device cuda=cuda -filter_hw_device cuda \
    -f lavfi -i color=size=800x600:color=white,format=yuv420p \
    -f lavfi -i yuvtestsrc=size=200x200,format=yuv420p \
    -filter_complex \
    " \
        [0]hwupload[under]; \
        [1]hwupload,chromakey_cuda=green:0.1:0.12[over]; \
        [under][over]overlay_cuda" \
    -c:v hevc_nvenc -cq 18 -preset slow output.mp4

```

### 40.4 colorspace_cuda# TOC

CUDA accelerated implementation of the colorspace filter.

It is by no means feature complete compared to the software colorspace filter, and at the current time only supports color range conversion between jpeg/full and mpeg/limited range.

The filter accepts the following options:

range

Specify output color range.

The accepted values are:

‘tv’

TV (restricted) range

‘mpeg’

MPEG (restricted) range

‘pc’

PC (full) range

‘jpeg’

JPEG (full) range

### 40.5 overlay_cuda# TOC

Overlay one video on top of another.

This is the CUDA variant of the overlay filter. It only accepts CUDA frames. The underlying input pixel formats have to match.

It takes two inputs and has one output. The first input is the "main" video on which the second input is overlaid.

It accepts the following parameters:

x

y

Set expressions for the x and y coordinates of the overlaid video on the main video.

They can contain the following parameters:

main_w, W

main_h, H

The main input width and height.

overlay_w, w

overlay_h, h

The overlay input width and height.

x

y

The computed values for x and y. They are evaluated for each new frame.

n

The ordinal index of the main input frame, starting from 0.

pos

The byte offset position in the file of the main input frame, NAN if unknown. Deprecated, do not use.

t

The timestamp of the main input frame, expressed in seconds, NAN if unknown.

Default value is "0" for both expressions.

eval

Set when the expressions for x and y are evaluated.

It accepts the following values:

init

Evaluate expressions once during filter initialization or when a command is processed.

frame

Evaluate expressions for each incoming frame

Default value is frame.

eof_action

See framesync.

shortest

See framesync.

repeatlast

See framesync.

This filter also supports the framesync options.

### 40.6 pad_cuda# TOC

Add paddings to an input video stream using CUDA.

This filter is the CUDA-accelerated version of the pad filter. It accepts the same options and expressions and provides the same core functionality. For a detailed description of available options, please see the documentation for the pad filter.

#### 40.6.1 Examples# TOC

- Add a 200-pixel black border to all sides of a video frame:

```
ffmpeg -hwaccel cuda -hwaccel_output_format cuda -i input.mp4 -vf "pad_cuda=w=iw+400:h=ih+400:x=200:y=200" -c:v h264_nvenc out.mp4

```

- Pad the input video to a 16:9 aspect ratio, filling with the color "blue":

```
ffmpeg -hwaccel cuda -hwaccel_output_format cuda -i input.mp4 -vf "pad_cuda=w=ih*16/9/sar:h=ih:x=(ow-iw)/2:y=(oh-ih)/2:color=blue" -c:v h264_nvenc out.mp4

```

### 40.7 scale_cuda# TOC

Scale (resize) and convert (pixel format) the input video, using accelerated CUDA kernels. Setting the output width and height works in the same way as for the scale filter.

The filter accepts the following options:

w

h

Set the output video dimension expression. Default value is the input dimension.

Allows for the same expressions as the scale filter.

interp_algo

Sets the algorithm used for scaling:

nearest

Nearest neighbour

Used by default if input parameters match the desired output.

bilinear

Bilinear

bicubic

Bicubic

This is the default.

lanczos

High-quality separable Lanczos (windowed sinc). The filter radius can be set with param; the default is 3.

format

Controls the output pixel format. By default, or if none is specified, the input pixel format is used.

Converting between yuv420p, yuv422p, yuv444p, yuv420p10, yuv422p10, yuv444p10, nv12, nv16, p010 or p210 and bgra, rgba, bgr0 or rgb0 is supported, also together with resizing. Resizing is then done on the RGB side, after converting from YUV or before converting to YUV, and always uses the generic filters selected with interp_algo. Resizing the YUV side in a separate instance instead needs less intermediate memory and may be faster, but filters chroma differently. YUV to RGB conversion uses the YCbCr matrix and range of the input, RGB to YUV conversion those selected for the output (see out_color_matrix and out_range). An unspecified matrix is treated as BT.601 and an unspecified range as limited. The conversion samples chroma independently of interp_algo: YUV to RGB conversion uses the nearest chroma sample, RGB to YUV conversion averages, which centers the chroma samples.

passthrough

If set to 0, every frame is processed, even if no conversion is necessary. This mode can be useful to use the filter as a buffer for a downstream frame-consumer that exhausts the limited decoder frame pool.

If set to 1, frames are passed through as-is if they match the desired output parameters. This is the default behaviour.

use_filters

If set to 1, filter with a generic weight LUT instead of using fixed-function shader kernels. May be faster or slower depending on the hardware. A value of auto (the default) enables this automatically when required for correct anti-aliasing when downscaling, and for high-quality Lanczos scaling. Set this to 0 to use the legacy fixed 4-tap Lanczos kernel. Resizing during YUV to RGB or RGB to YUV conversion always uses the generic filters.

param

Algorithm-specific parameter. For bicubic, this affects the filter curve. For lanczos, this sets the filter radius from 1 to 10 (default 3) when using the generic filter path; it has no effect with use_filters=0.

force_original_aspect_ratio

force_divisible_by

Work the same as the identical scale filter options.

reset_sar

Works the same as the identical scale filter option.

out_range

Set the output YCbCr sample range. One of auto (the default), jpeg/full/pc, or mpeg/limited/tv.

out_color_matrix

Set the output YCbCr matrix. One of auto (the default), bt601, smpte170m, bt470, bt470bg, bt709, fcc, smpte240m, ycgco, bt2020 or bt2020nc.

With auto, out_range and out_color_matrix are left to filter-graph negotiation. They follow a single range and matrix negotiated for the input, as for decoded video, and otherwise prefer BT.601 limited range. For RGB to YUV conversion, auto thus means BT.601 limited range, unless the filter graph requires otherwise; converting full range YUV to RGB and back keeps the full range.

Outside RGB to YUV conversion, these options describe the existing samples without remapping them; an unspecified input description may adopt the negotiated output description, while conflicting specified descriptions are rejected. Both options can only be used with YUV output; RGB output is full range.

#### 40.7.1 Examples# TOC

- Scale input to 720p, keeping aspect ratio and ensuring the output is yuv420p.

```
scale_cuda=-2:720:format=yuv420p

```

- Upscale to 4K using nearest neighbour algorithm.

```
scale_cuda=4096:2160:interp_algo=nearest

```

- Don’t do any conversion or scaling, but copy all input frames into newly allocated ones. This can be useful to deal with a filter and encode chain that otherwise exhausts the decoders frame pool.

```
scale_cuda=passthrough=0

```

- Convert BT.709 input to RGB for a filter that requires it, then back to BT.709 NV12 with limited range.

```
scale_cuda=format=bgra,scale_cuda=format=nv12:out_color_matrix=bt709:out_range=limited

```

- Scale to 720p while converting to RGB.

```
scale_cuda=-2:720:format=bgra

```

### 40.8 thumbnail_cuda# TOC

Select the most representative frame in a given sequence of consecutive frames using CUDA.

The filter accepts the following options:

n

Set the frames batch size to analyze; in a set of n frames, the filter will pick one of them, and then handle the next batch of n frames until the end. Default is 100.

Since the filter keeps track of the whole frames sequence, a bigger n value will result in a higher memory usage, so a high value is not recommended.

#### 40.8.1 Example# TOC

- Thumbnails are extracted from every n=150-frame batch, selecting one per batch. Chosen frames are then scaled with scale_cuda.

```
./ffmpeg  -hwaccel cuda -hwaccel_output_format cuda  -i ./input.mp4 -vf "thumbnail_cuda=150,scale_cuda=1920:1080,hwdownload,format=nv12" ./output/out%03d.png

```

### 40.9 transpose_cuda# TOC

Transpose rows with columns in the input video and optionally flip it. For more in depth examples see the transpose video filter, which shares mostly the same options.

It accepts the following parameters:

dir

Specify the transposition direction.

Can assume the following values:

‘cclock_flip’

Rotate by 90 degrees counterclockwise and vertically flip. (default)

‘clock’

Rotate by 90 degrees clockwise.

‘cclock’

Rotate by 90 degrees counterclockwise.

‘clock_flip’

Rotate by 90 degrees clockwise and vertically flip.

‘reversal’

Rotate by 180 degrees.

‘hflip’

Flip horizontally.

‘vflip’

Flip vertically.

passthrough

Do not apply the transposition if the input geometry matches the one specified by the specified value. It accepts the following values:

‘none’

Always apply transposition. (default)

‘portrait’

Preserve portrait geometry (when height >= width).

‘landscape’

Preserve landscape geometry (when width >= height).

### 40.10 yadif_cuda# TOC

Deinterlace the input video using the yadif algorithm, but implemented in CUDA so that it can work as part of a GPU accelerated pipeline with nvdec and/or nvenc.

It accepts the following parameters:

mode

The interlacing mode to adopt. It accepts one of the following values:

0, send_frame

Output one frame for each frame.

1, send_field

Output one frame for each field.

2, send_frame_nospatial

Like send_frame, but it skips the spatial interlacing check.

3, send_field_nospatial

Like send_field, but it skips the spatial interlacing check.

The default value is send_frame.

parity

The picture field parity assumed for the input interlaced video. It accepts one of the following values:

0, tff

Assume the top field is first.

1, bff

Assume the bottom field is first.

-1, auto

Enable automatic detection of field parity.

The default value is auto. If the interlacing is unknown or the decoder does not export this information, top field first will be assumed.

deint

Specify which frames to deinterlace. Accepts one of the following values:

0, all

Deinterlace all frames.

1, interlaced

Only deinterlace frames marked as interlaced.

The default value is all.

## 41 OpenCL Video Filters# TOC

Below is a description of the currently available OpenCL video filters.

To enable compilation of these filters you need to configure FFmpeg with --enable-opencl.

Running OpenCL filters requires you to initialize a hardware device and to pass that device to all filters in any filter graph.

-init_hw_device opencl[=name][:device[,key=value...]]

Initialise a new hardware device of type opencl called name, using the given device parameters.

-filter_hw_device name

Pass the hardware device called name to all filters in any filter graph.

For more detailed information see https://www.ffmpeg.org/ffmpeg.html#Advanced-Video-options

- Example of choosing the first device on the second platform and running avgblur_opencl filter with default parameters on it.

```
-init_hw_device opencl=gpu:1.0 -filter_hw_device gpu -i INPUT -vf "hwupload, avgblur_opencl, hwdownload" OUTPUT

```

Since OpenCL filters are not able to access frame data in normal memory, all frame data needs to be uploaded(hwupload) to hardware surfaces connected to the appropriate device before being used and then downloaded(hwdownload) back to normal memory. Note that hwupload will upload to a surface with the same layout as the software frame, so it may be necessary to add a format filter immediately before to get the input into the right format and hwdownload does not support all formats on the output - it may be necessary to insert an additional format filter immediately following in the graph to get the output in a supported format.

### 41.1 avgblur_opencl# TOC

Apply average blur filter.

The filter accepts the following options:

sizeX

Set horizontal radius size. Range is [1, 1024] and default value is 1.

planes

Set which planes to filter. Default value is 0xf, by which all planes are processed.

sizeY

Set vertical radius size. Range is [1, 1024] and default value is 0. If zero, sizeX value will be used.

#### 41.1.1 Example# TOC

- Apply average blur filter with horizontal and vertical size of 3, setting each pixel of the output to the average value of the 7x7 region centered on it in the input. For pixels on the edges of the image, the region does not extend beyond the image boundaries, and so out-of-range coordinates are not used in the calculations.

```
-i INPUT -vf "hwupload, avgblur_opencl=3, hwdownload" OUTPUT

```

### 41.2 boxblur_opencl# TOC

Apply a boxblur algorithm to the input video.

It accepts the following parameters:

luma_radius, lr

luma_power, lp

chroma_radius, cr

chroma_power, cp

alpha_radius, ar

alpha_power, ap

A description of the accepted options follows.

luma_radius, lr

chroma_radius, cr

alpha_radius, ar

Set an expression for the box radius in pixels used for blurring the corresponding input plane.

The radius value must be a non-negative number, and must not be greater than the value of the expression min(w,h)/2 for the luma and alpha planes, and of min(cw,ch)/2 for the chroma planes.

Default value for luma_radius is "2". If not specified, chroma_radius and alpha_radius default to the corresponding value set for luma_radius.

The expressions can contain the following constants:

w

h

The input width and height in pixels.

cw

ch

The input chroma image width and height in pixels.

hsub

vsub

The horizontal and vertical chroma subsample values. For example, for the pixel format "yuv422p", hsub is 2 and vsub is 1.

luma_power, lp

chroma_power, cp

alpha_power, ap

Specify how many times the boxblur filter is applied to the corresponding plane.

Default value for luma_power is 2. If not specified, chroma_power and alpha_power default to the corresponding value set for luma_power.

A value of 0 will disable the effect.

#### 41.2.1 Examples# TOC

Apply boxblur filter, setting each pixel of the output to the average value of box-radiuses luma_radius, chroma_radius, alpha_radius for each plane respectively. The filter will apply luma_power, chroma_power, alpha_power times onto the corresponding plane. For pixels on the edges of the image, the radius does not extend beyond the image boundaries, and so out-of-range coordinates are not used in the calculations.

- Apply a boxblur filter with the luma, chroma, and alpha radius set to 2 and luma, chroma, and alpha power set to 3. The filter will run 3 times with box-radius set to 2 for every plane of the image.

```
-i INPUT -vf "hwupload, boxblur_opencl=luma_radius=2:luma_power=3, hwdownload" OUTPUT
-i INPUT -vf "hwupload, boxblur_opencl=2:3, hwdownload" OUTPUT

```

- Apply a boxblur filter with luma radius set to 2, luma_power to 1, chroma_radius to 4, chroma_power to 5, alpha_radius to 3 and alpha_power to 7.
For the luma plane, a 2x2 box radius will be run once.

For the chroma plane, a 4x4 box radius will be run 5 times.

For the alpha plane, a 3x3 box radius will be run 7 times.

```
-i INPUT -vf "hwupload, boxblur_opencl=2:1:4:5:3:7, hwdownload" OUTPUT

```

### 41.3 colorkey_opencl# TOC

RGB colorspace color keying.

The filter accepts the following options:

color

The color which will be replaced with transparency.

similarity

Similarity percentage with the key color.

0.01 matches only the exact key color, while 1.0 matches everything.

blend

Blend percentage.

0.0 makes pixels either fully transparent, or not transparent at all.

Higher values result in semi-transparent pixels, with a higher transparency the more similar the pixels color is to the key color.

#### 41.3.1 Examples# TOC

- Make every semi-green pixel in the input transparent with some slight blending:

```
-i INPUT -vf "hwupload, colorkey_opencl=green:0.3:0.1, hwdownload" OUTPUT

```

### 41.4 convolution_opencl# TOC

Apply convolution of 3x3, 5x5, 7x7 matrix.

The filter accepts the following options:

0m

1m

2m

3m

Set matrix for each plane. Matrix is sequence of 9, 25 or 49 signed numbers. Default value for each plane is 0 0 0 0 1 0 0 0 0.

0rdiv

1rdiv

2rdiv

3rdiv

Set multiplier for calculated value for each plane. If unset or 0, it will be sum of all matrix elements. The option value must be a float number greater or equal to 0.0. Default value is 1.0.

0bias

1bias

2bias

3bias

Set bias for each plane. This value is added to the result of the multiplication. Useful for making the overall image brighter or darker. The option value must be a float number greater or equal to 0.0. Default value is 0.0.

#### 41.4.1 Examples# TOC

- Apply sharpen:

```
-i INPUT -vf "hwupload, convolution_opencl=0 -1 0 -1 5 -1 0 -1 0:0 -1 0 -1 5 -1 0 -1 0:0 -1 0 -1 5 -1 0 -1 0:0 -1 0 -1 5 -1 0 -1 0, hwdownload" OUTPUT

```

- Apply blur:

```
-i INPUT -vf "hwupload, convolution_opencl=1 1 1 1 1 1 1 1 1:1 1 1 1 1 1 1 1 1:1 1 1 1 1 1 1 1 1:1 1 1 1 1 1 1 1 1:1/9:1/9:1/9:1/9, hwdownload" OUTPUT

```

- Apply edge enhance:

```
-i INPUT -vf "hwupload, convolution_opencl=0 0 0 -1 1 0 0 0 0:0 0 0 -1 1 0 0 0 0:0 0 0 -1 1 0 0 0 0:0 0 0 -1 1 0 0 0 0:5:1:1:1:0:128:128:128, hwdownload" OUTPUT

```

- Apply edge detect:

```
-i INPUT -vf "hwupload, convolution_opencl=0 1 0 1 -4 1 0 1 0:0 1 0 1 -4 1 0 1 0:0 1 0 1 -4 1 0 1 0:0 1 0 1 -4 1 0 1 0:5:5:5:1:0:128:128:128, hwdownload" OUTPUT

```

- Apply laplacian edge detector which includes diagonals:

```
-i INPUT -vf "hwupload, convolution_opencl=1 1 1 1 -8 1 1 1 1:1 1 1 1 -8 1 1 1 1:1 1 1 1 -8 1 1 1 1:1 1 1 1 -8 1 1 1 1:5:5:5:1:0:128:128:0, hwdownload" OUTPUT

```

- Apply emboss:

```
-i INPUT -vf "hwupload, convolution_opencl=-2 -1 0 -1 1 1 0 1 2:-2 -1 0 -1 1 1 0 1 2:-2 -1 0 -1 1 1 0 1 2:-2 -1 0 -1 1 1 0 1 2, hwdownload" OUTPUT

```

### 41.5 erosion_opencl# TOC

Apply erosion effect to the video.

This filter replaces the pixel by the local(3x3) minimum.

It accepts the following options:

threshold0

threshold1

threshold2

threshold3

Limit the maximum change for each plane. Range is [0, 65535] and default value is 65535. If 0, plane will remain unchanged.

coordinates

Flag which specifies the pixel to refer to. Range is [0, 255] and default value is 255, i.e. all eight pixels are used.

Flags to local 3x3 coordinates region centered on x:

1 2 3

4 x 5

6 7 8

#### 41.5.1 Example# TOC

- Apply erosion filter with threshold0 set to 30, threshold1 set 40, threshold2 set to 50 and coordinates set to 231, setting each pixel of the output to the local minimum between pixels: 1, 2, 3, 6, 7, 8 of the 3x3 region centered on it in the input. If the difference between input pixel and local minimum is more then threshold of the corresponding plane, output pixel will be set to input pixel - threshold of corresponding plane.

```
-i INPUT -vf "hwupload, erosion_opencl=30:40:50:coordinates=231, hwdownload" OUTPUT

```

### 41.6 deshake_opencl# TOC

Feature-point based video stabilization filter.

The filter accepts the following options:

tripod

Simulates a tripod by preventing any camera movement whatsoever from the original frame. Defaults to 0.

debug

Whether or not additional debug info should be displayed, both in the processed output and in the console.

Note that in order to see console debug output you will also need to pass -v verbose to ffmpeg.

Viewing point matches in the output video is only supported for RGB input.

Defaults to 0.

adaptive_crop

Whether or not to do a tiny bit of cropping at the borders to cut down on the amount of mirrored pixels.

Defaults to 1.

refine_features

Whether or not feature points should be refined at a sub-pixel level.

This can be turned off for a slight performance gain at the cost of precision.

Defaults to 1.

smooth_strength

The strength of the smoothing applied to the camera path from 0.0 to 1.0.

1.0 is the maximum smoothing strength while values less than that result in less smoothing.

0.0 causes the filter to adaptively choose a smoothing strength on a per-frame basis.

Defaults to 0.0.

smooth_window_multiplier

Controls the size of the smoothing window (the number of frames buffered to determine motion information from).

The size of the smoothing window is determined by multiplying the framerate of the video by this number.

Acceptable values range from 0.1 to 10.0.

Larger values increase the amount of motion data available for determining how to smooth the camera path, potentially improving smoothness, but also increase latency and memory usage.

Defaults to 2.0.

#### 41.6.1 Examples# TOC

- Stabilize a video with a fixed, medium smoothing strength:

```
-i INPUT -vf "hwupload, deshake_opencl=smooth_strength=0.5, hwdownload" OUTPUT

```

- Stabilize a video with debugging (both in console and in rendered video):

```
-i INPUT -filter_complex "[0:v]format=rgba, hwupload, deshake_opencl=debug=1, hwdownload, format=rgba, format=yuv420p" -v verbose OUTPUT

```

### 41.7 dilation_opencl# TOC

Apply dilation effect to the video.

This filter replaces the pixel by the local(3x3) maximum.

It accepts the following options:

threshold0

threshold1

threshold2

threshold3

Limit the maximum change for each plane. Range is [0, 65535] and default value is 65535. If 0, plane will remain unchanged.

coordinates

Flag which specifies the pixel to refer to. Range is [0, 255] and default value is 255, i.e. all eight pixels are used.

Flags to local 3x3 coordinates region centered on x:

1 2 3

4 x 5

6 7 8

#### 41.7.1 Example# TOC

- Apply dilation filter with threshold0 set to 30, threshold1 set 40, threshold2 set to 50 and coordinates set to 231, setting each pixel of the output to the local maximum between pixels: 1, 2, 3, 6, 7, 8 of the 3x3 region centered on it in the input. If the difference between input pixel and local maximum is more then threshold of the corresponding plane, output pixel will be set to input pixel + threshold of corresponding plane.

```
-i INPUT -vf "hwupload, dilation_opencl=30:40:50:coordinates=231, hwdownload" OUTPUT

```

### 41.8 nlmeans_opencl# TOC

Non-local Means denoise filter through OpenCL, this filter accepts same options as nlmeans.

### 41.9 overlay_opencl# TOC

Overlay one video on top of another.

It takes two inputs and has one output. The first input is the "main" video on which the second input is overlaid. This filter requires same memory layout for all the inputs. So, format conversion may be needed.

The filter accepts the following options:

x

Set the x coordinate of the overlaid video on the main video. Default value is 0.

y

Set the y coordinate of the overlaid video on the main video. Default value is 0.

#### 41.9.1 Examples# TOC

- Overlay an image LOGO at the top-left corner of the INPUT video. Both inputs are yuv420p format.

```
-i INPUT -i LOGO -filter_complex "[0:v]hwupload[a], [1:v]format=yuv420p, hwupload[b], [a][b]overlay_opencl, hwdownload" OUTPUT

```

- The inputs have same memory layout for color channels , the overlay has additional alpha plane, like INPUT is yuv420p, and the LOGO is yuva420p.

```
-i INPUT -i LOGO -filter_complex "[0:v]hwupload[a], [1:v]format=yuva420p, hwupload[b], [a][b]overlay_opencl, hwdownload" OUTPUT

```

### 41.10 pad_opencl# TOC

Add paddings to the input image, and place the original input at the provided x, y coordinates.

It accepts the following options:

width, w

height, h

Specify an expression for the size of the output image with the paddings added. If the value for width or height is 0, the corresponding input size is used for the output.

The width expression can reference the value set by the height expression, and vice versa.

The default value of width and height is 0.

x

y

Specify the offsets to place the input image at within the padded area, with respect to the top/left border of the output image.

The x expression can reference the value set by the y expression, and vice versa.

The default value of x and y is 0.

If x or y evaluate to a negative number, they’ll be changed so the input image is centered on the padded area.

color

Specify the color of the padded area. For the syntax of this option, check the "Color" section in the ffmpeg-utils manual.

aspect

Pad to an aspect instead to a resolution.

The value for the width, height, x, and y options are expressions containing the following constants:

in_w

in_h

The input video width and height.

iw

ih

These are the same as in_w and in_h.

out_w

out_h

The output width and height (the size of the padded area), as specified by the width and height expressions.

ow

oh

These are the same as out_w and out_h.

x

y

The x and y offsets as specified by the x and y expressions, or NAN if not yet specified.

a

same as iw / ih

sar

input sample aspect ratio

dar

input display aspect ratio, it is the same as (iw / ih) * sar

### 41.11 prewitt_opencl# TOC

Apply the Prewitt operator (https://en.wikipedia.org/wiki/Prewitt_operator) to input video stream.

The filter accepts the following option:

planes

Set which planes to filter. Default value is 0xf, by which all planes are processed.

scale

Set value which will be multiplied with filtered result. Range is [0.0, 65535] and default value is 1.0.

delta

Set value which will be added to filtered result. Range is [-65535, 65535] and default value is 0.0.

#### 41.11.1 Example# TOC

- Apply the Prewitt operator with scale set to 2 and delta set to 10.

```
-i INPUT -vf "hwupload, prewitt_opencl=scale=2:delta=10, hwdownload" OUTPUT

```

### 41.12 program_opencl# TOC

Filter video using an OpenCL program.

source

OpenCL program source file.

kernel

Kernel name in program.

inputs

Number of inputs to the filter. Defaults to 1.

size, s

Size of output frames. Defaults to the same as the first input.

The program_opencl filter also supports the framesync options.

The program source file must contain a kernel function with the given name, which will be run once for each plane of the output. Each run on a plane gets enqueued as a separate 2D global NDRange with one work-item for each pixel to be generated. The global ID offset for each work-item is therefore the coordinates of a pixel in the destination image.

The kernel function needs to take the following arguments:

- Destination image, __write_only image2d_t.
This image will become the output; the kernel should write all of it.

- Frame index, unsigned int.
This is a counter starting from zero and increasing by one for each frame.

- Source images, __read_only image2d_t.
These are the most recent images on each input. The kernel may read from them to generate the output, but they can’t be written to.

Example programs:

- Copy the input to the output (output must be the same size as the input).
```
__kernel void copy(__write_only image2d_t destination,
                   unsigned int index,
                   __read_only  image2d_t source)
{
    const sampler_t sampler = CLK_NORMALIZED_COORDS_FALSE;

    int2 location = (int2)(get_global_id(0), get_global_id(1));

    float4 value = read_imagef(source, sampler, location);

    write_imagef(destination, location, value);
}

```

- Apply a simple transformation, rotating the input by an amount increasing with the index counter. Pixel values are linearly interpolated by the sampler, and the output need not have the same dimensions as the input.
```
__kernel void rotate_image(__write_only image2d_t dst,
                           unsigned int index,
                           __read_only  image2d_t src)
{
    const sampler_t sampler = (CLK_NORMALIZED_COORDS_FALSE |
                               CLK_FILTER_LINEAR);

    float angle = (float)index / 100.0f;

    float2 dst_dim = convert_float2(get_image_dim(dst));
    float2 src_dim = convert_float2(get_image_dim(src));

    float2 dst_cen = dst_dim / 2.0f;
    float2 src_cen = src_dim / 2.0f;

    int2   dst_loc = (int2)(get_global_id(0), get_global_id(1));

    float2 dst_pos = convert_float2(dst_loc) - dst_cen;
    float2 src_pos = {
        cos(angle) * dst_pos.x - sin(angle) * dst_pos.y,
        sin(angle) * dst_pos.x + cos(angle) * dst_pos.y
    };
    src_pos = src_pos * src_dim / dst_dim;

    float2 src_loc = src_pos + src_cen;

    if (src_loc.x < 0.0f      || src_loc.y < 0.0f ||
        src_loc.x > src_dim.x || src_loc.y > src_dim.y)
        write_imagef(dst, dst_loc, 0.5f);
    else
        write_imagef(dst, dst_loc, read_imagef(src, sampler, src_loc));
}

```

- Blend two inputs together, with the amount of each input used varying with the index counter.
```
__kernel void blend_images(__write_only image2d_t dst,
                           unsigned int index,
                           __read_only  image2d_t src1,
                           __read_only  image2d_t src2)
{
    const sampler_t sampler = (CLK_NORMALIZED_COORDS_FALSE |
                               CLK_FILTER_LINEAR);

    float blend = (cos((float)index / 50.0f) + 1.0f) / 2.0f;

    int2  dst_loc = (int2)(get_global_id(0), get_global_id(1));
    int2 src1_loc = dst_loc * get_image_dim(src1) / get_image_dim(dst);
    int2 src2_loc = dst_loc * get_image_dim(src2) / get_image_dim(dst);

    float4 val1 = read_imagef(src1, sampler, src1_loc);
    float4 val2 = read_imagef(src2, sampler, src2_loc);

    write_imagef(dst, dst_loc, val1 * blend + val2 * (1.0f - blend));
}

```

### 41.13 remap_opencl# TOC

Remap pixels using 2nd: Xmap and 3rd: Ymap input video stream.

Destination pixel at position (X, Y) will be picked from source (x, y) position where x = Xmap(X, Y) and y = Ymap(X, Y). If mapping values are out of range, zero value for pixel will be used for destination pixel.

Xmap and Ymap input video streams must be of same dimensions. Output video stream will have Xmap/Ymap video stream dimensions. Xmap and Ymap input video streams are 32bit float pixel format, single channel.

interp

Specify interpolation used for remapping of pixels. Allowed values are near and linear. Default value is linear.

fill

Specify the color of the unmapped pixels. For the syntax of this option, check the "Color" section in the ffmpeg-utils manual. Default color is black.

### 41.14 roberts_opencl# TOC

Apply the Roberts cross operator (https://en.wikipedia.org/wiki/Roberts_cross) to input video stream.

The filter accepts the following option:

planes

Set which planes to filter. Default value is 0xf, by which all planes are processed.

scale

Set value which will be multiplied with filtered result. Range is [0.0, 65535] and default value is 1.0.

delta

Set value which will be added to filtered result. Range is [-65535, 65535] and default value is 0.0.

#### 41.14.1 Example# TOC

- Apply the Roberts cross operator with scale set to 2 and delta set to 10

```
-i INPUT -vf "hwupload, roberts_opencl=scale=2:delta=10, hwdownload" OUTPUT

```

### 41.15 sobel_opencl# TOC

Apply the Sobel operator (https://en.wikipedia.org/wiki/Sobel_operator) to input video stream.

The filter accepts the following option:

planes

Set which planes to filter. Default value is 0xf, by which all planes are processed.

scale

Set value which will be multiplied with filtered result. Range is [0.0, 65535] and default value is 1.0.

delta

Set value which will be added to filtered result. Range is [-65535, 65535] and default value is 0.0.

#### 41.15.1 Example# TOC

- Apply sobel operator with scale set to 2 and delta set to 10

```
-i INPUT -vf "hwupload, sobel_opencl=scale=2:delta=10, hwdownload" OUTPUT

```

### 41.16 tonemap_opencl# TOC

Perform HDR(PQ/HLG) to SDR conversion with tone-mapping.

It accepts the following parameters:

tonemap

Specify the tone-mapping operator to be used. Same as tonemap option in tonemap.

param

Tune the tone mapping algorithm. same as param option in tonemap.

desat

Apply desaturation for highlights that exceed this level of brightness. The higher the parameter, the more color information will be preserved. This setting helps prevent unnaturally blown-out colors for super-highlights, by (smoothly) turning into white instead. This makes images feel more natural, at the cost of reducing information about out-of-range colors.

The default value is 0.5, and the algorithm here is a little different from the cpu version tonemap currently. A setting of 0.0 disables this option.

threshold

The tonemapping algorithm parameters is fine-tuned per each scene. And a threshold is used to detect whether the scene has changed or not. If the distance between the current frame average brightness and the current running average exceeds a threshold value, we would re-calculate scene average and peak brightness. The default value is 0.2.

format

Specify the output pixel format.

Currently supported formats are:

p010

nv12

range, r

Set the output color range.

Possible values are:

tv/mpeg

pc/jpeg

Default is same as input.

primaries, p

Set the output color primaries.

Possible values are:

bt709

bt2020

Default is same as input.

transfer, t

Set the output transfer characteristics.

Possible values are:

bt709

bt2020

Default is bt709.

matrix, m

Set the output colorspace matrix.

Possible value are:

bt709

bt2020

Default is same as input.

#### 41.16.1 Example# TOC

- Convert HDR(PQ/HLG) video to bt2020-transfer-characteristic p010 format using linear operator.

```
-i INPUT -vf "format=p010,hwupload,tonemap_opencl=t=bt2020:tonemap=linear:format=p010,hwdownload,format=p010" OUTPUT

```

### 41.17 unsharp_opencl# TOC

Sharpen or blur the input video.

It accepts the following parameters:

luma_msize_x, lx

Set the luma matrix horizontal size. Range is [1, 23] and default value is 5.

luma_msize_y, ly

Set the luma matrix vertical size. Range is [1, 23] and default value is 5.

luma_amount, la

Set the luma effect strength. Range is [-10, 10] and default value is 1.0.

Negative values will blur the input video, while positive values will sharpen it, a value of zero will disable the effect.

chroma_msize_x, cx

Set the chroma matrix horizontal size. Range is [1, 23] and default value is 5.

chroma_msize_y, cy

Set the chroma matrix vertical size. Range is [1, 23] and default value is 5.

chroma_amount, ca

Set the chroma effect strength. Range is [-10, 10] and default value is 0.0.

Negative values will blur the input video, while positive values will sharpen it, a value of zero will disable the effect.

All parameters are optional and default to the equivalent of the string ’5:5:1.0:5:5:0.0’.

#### 41.17.1 Examples# TOC

- Apply strong luma sharpen effect:

```
-i INPUT -vf "hwupload, unsharp_opencl=luma_msize_x=7:luma_msize_y=7:luma_amount=2.5, hwdownload" OUTPUT

```

- Apply a strong blur of both luma and chroma parameters:

```
-i INPUT -vf "hwupload, unsharp_opencl=7:7:-2:7:7:-2, hwdownload" OUTPUT

```

### 41.18 xfade_opencl# TOC

Cross fade two videos with custom transition effect by using OpenCL.

It accepts the following options:

transition

Set one of possible transition effects.

custom

Select custom transition effect, the actual transition description will be picked from source and kernel options.

fade

wipeleft

wiperight

wipeup

wipedown

slideleft

slideright

slideup

slidedown

Default transition is fade.

source

OpenCL program source file for custom transition.

kernel

Set name of kernel to use for custom transition from program source file.

duration

Set duration of video transition.

offset

Set time of start of transition relative to first video.

The program source file must contain a kernel function with the given name, which will be run once for each plane of the output. Each run on a plane gets enqueued as a separate 2D global NDRange with one work-item for each pixel to be generated. The global ID offset for each work-item is therefore the coordinates of a pixel in the destination image.

The kernel function needs to take the following arguments:

- Destination image, __write_only image2d_t.
This image will become the output; the kernel should write all of it.

- First Source image, __read_only image2d_t. Second Source image, __read_only image2d_t.
These are the most recent images on each input. The kernel may read from them to generate the output, but they can’t be written to.

- Transition progress, float. This value is always between 0 and 1 inclusive.

Example programs:

- Apply dots curtain transition effect:
```
__kernel void blend_images(__write_only image2d_t dst,
                           __read_only  image2d_t src1,
                           __read_only  image2d_t src2,
                           float progress)
{
    const sampler_t sampler = (CLK_NORMALIZED_COORDS_FALSE |
                               CLK_FILTER_LINEAR);
    int2  p = (int2)(get_global_id(0), get_global_id(1));
    float2 rp = (float2)(get_global_id(0), get_global_id(1));
    float2 dim = (float2)(get_image_dim(src1).x, get_image_dim(src1).y);
    rp = rp / dim;

    float2 dots = (float2)(20.0, 20.0);
    float2 center = (float2)(0,0);
    float2 unused;

    float4 val1 = read_imagef(src1, sampler, p);
    float4 val2 = read_imagef(src2, sampler, p);
    bool next = distance(fract(rp * dots, &unused), (float2)(0.5, 0.5)) < (progress / distance(rp, center));

    write_imagef(dst, p, next ? val1 : val2);
}

```

## 42 VAAPI Video Filters# TOC

VAAPI Video filters are usually used with VAAPI decoder and VAAPI encoder. Below is a description of VAAPI video filters.

To enable compilation of these filters you need to configure FFmpeg with --enable-vaapi.

To use vaapi filters, you need to setup the vaapi device correctly. For more information, please read https://trac.ffmpeg.org/wiki/Hardware/VAAPI

### 42.1 overlay_vaapi# TOC

Overlay one video on the top of another.

It takes two inputs and has one output. The first input is the "main" video on which the second input is overlaid.

The filter accepts the following options:

x

y

Set expressions for the x and y coordinates of the overlaid video on the main video.

Default value is "0" for both expressions.

w

h

Set expressions for the width and height the overlaid video on the main video.

Default values are ’overlay_iw’ for ’w’ and ’overlay_ih*w/overlay_iw’ for ’h’.

The expressions can contain the following parameters:

main_w, W

main_h, H

The main input width and height.

overlay_iw

overlay_ih

The overlay input width and height.

overlay_w, w

overlay_h, h

The overlay output width and height.

overlay_x, x

overlay_y, y

Position of the overlay layer inside of main

alpha

Set transparency of overlaid video. Allowed range is 0.0 to 1.0. Higher value means lower transparency. Default value is 1.0.

eof_action

See framesync.

shortest

See framesync.

repeatlast

See framesync.

This filter also supports the framesync options.

#### 42.1.1 Examples# TOC

- Overlay an image LOGO at the top-left corner of the INPUT video. Both inputs for this filter are yuv420p format.

```
-i INPUT -i LOGO -filter_complex "[0:v]hwupload[a], [1:v]format=yuv420p, hwupload[b], [a][b]overlay_vaapi" OUTPUT

```

- Overlay an image LOGO at the offset (200, 100) from the top-left corner of the INPUT video. The inputs have same memory layout for color channels, the overlay has additional alpha plane, like INPUT is yuv420p, and the LOGO is yuva420p.

```
-i INPUT -i LOGO -filter_complex "[0:v]hwupload[a], [1:v]format=yuva420p, hwupload[b], [a][b]overlay_vaapi=x=200:y=100:w=400:h=300:alpha=1.0, hwdownload, format=nv12" OUTPUT

```

### 42.2 tonemap_vaapi# TOC

Perform HDR-to-SDR or HDR-to-HDR tone-mapping. It currently only accepts HDR10 as input.

It accepts the following parameters:

format

Specify the output pixel format.

Default is nv12 for HDR-to-SDR tone-mapping and p010 for HDR-to-HDR tone-mapping.

primaries, p

Set the output color primaries.

Default is bt709 for HDR-to-SDR tone-mapping and same as input for HDR-to-HDR tone-mapping.

transfer, t

Set the output transfer characteristics.

Default is bt709 for HDR-to-SDR tone-mapping and same as input for HDR-to-HDR tone-mapping.

matrix, m

Set the output colorspace matrix.

Default is bt709 for HDR-to-SDR tone-mapping and same as input for HDR-to-HDR tone-mapping.

display

Set the output mastering display colour volume. It is given by a ’|’-separated list of two values, two values are space separated. It set display primaries x & y in G, B, R order, then white point x & y, the nominal minimum & maximum display luminances.

HDR-to-HDR tone-mapping will be performed when this option is set.

light

Set the output content light level information. It accepts 2 space-separated values, the first input is the maximum light level and the second input is the maximum average light level.

It is ignored for HDR-to-SDR tone-mapping, and optional for HDR-to-HDR tone-mapping.

#### 42.2.1 Example# TOC

- Convert HDR(HDR10) video to bt2020-transfer-characteristic p010 format

```
tonemap_vaapi=format=p010:t=bt2020-10

```

- Convert HDR video to HDR video

```
tonemap_vaapi=display=7500\ 3000|34000\ 16000|13250\ 34500|15635\ 16450|500\ 10000000

```

### 42.3 hstack_vaapi# TOC

Stack input videos horizontally.

This is the VA-API variant of the hstack filter, each input stream may have different height, this filter will scale down/up each input stream while keeping the original aspect.

It accepts the following options:

inputs

See hstack.

shortest

See hstack.

height

Set height of output. If set to 0, this filter will set height of output to height of the first input stream. Default value is 0.

### 42.4 vstack_vaapi# TOC

Stack input videos vertically.

This is the VA-API variant of the vstack filter, each input stream may have different width, this filter will scale down/up each input stream while keeping the original aspect.

It accepts the following options:

inputs

See vstack.

shortest

See vstack.

width

Set width of output. If set to 0, this filter will set width of output to width of the first input stream. Default value is 0.

### 42.5 xstack_vaapi# TOC

Stack video inputs into custom layout.

This is the VA-API variant of the xstack filter, each input stream may have different size, this filter will scale down/up each input stream to the given output size, or the size of the first input stream.

It accepts the following options:

inputs

See xstack.

shortest

See xstack.

layout

See xstack. Moreover, this permits the user to supply output size for each input stream.

```
xstack_vaapi=inputs=4:layout=0_0_1920x1080|0_h0_1920x1080|w0_0_1920x1080|w0_h0_1920x1080

```

grid

See xstack.

grid_tile_size

Set output size for each input stream when grid is set. If this option is not set, this filter will set output size by default to the size of the first input stream. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual.

fill

See xstack.

### 42.6 pad_vaapi# TOC

Add paddings to the input image, and place the original input at the provided x, y coordinates.

It accepts the following options:

width, w

height, h

Specify an expression for the size of the output image with the paddings added. If the value for width or height is 0, the corresponding input size is used for the output.

The width expression can reference the value set by the height expression, and vice versa.

The default value of width and height is 0.

x

y

Specify the offsets to place the input image at within the padded area, with respect to the top/left border of the output image.

The x expression can reference the value set by the y expression, and vice versa.

The default value of x and y is 0.

If x or y evaluate to a negative number, they’ll be changed so the input image is centered on the padded area.

color

Specify the color of the padded area. For the syntax of this option, check the "Color" section in the ffmpeg-utils manual.

aspect

Pad to an aspect instead to a resolution.

The value for the width, height, x, and y options are expressions containing the following constants:

in_w

in_h

The input video width and height.

iw

ih

These are the same as in_w and in_h.

out_w

out_h

The output width and height (the size of the padded area), as specified by the width and height expressions.

ow

oh

These are the same as out_w and out_h.

x

y

The x and y offsets as specified by the x and y expressions, or NAN if not yet specified.

a

same as iw / ih

sar

input sample aspect ratio

dar

input display aspect ratio, it is the same as (iw / ih) * sar

### 42.7 drawbox_vaapi# TOC

Draw a colored box on the input image.

It accepts the following parameters:

x

y

The expressions which specify the top left corner coordinates of the box. It defaults to 0.

width, w

height, h

The expressions which specify the width and height of the box; if 0 they are interpreted as the input width and height. It defaults to 0.

color, c

Specify the color of the box to write. For the general syntax of this option, check the "Color" section in the ffmpeg-utils manual.

thickness, t

The expression which sets the thickness of the box edge. A value of fill will create a filled box. Default value is 3.

See below for the list of accepted constants.

replace

With value 1, the pixels of the painted box will overwrite the video’s color and alpha pixels. Default is 0, which composites the box onto the input video.

The parameters for x, y, w and h and t are expressions containing the following constants:

in_h, ih

in_w, iw

The input width and height.

x

y

The x and y offset coordinates where the box is drawn.

w

h

The width and height of the drawn box.

t

The thickness of the drawn box.

#### 42.7.1 Examples# TOC

- Draw a black box around the edge of the input image:

```
drawbox

```

- Draw a box with color red and an opacity of 50%:

```
drawbox=10:20:200:60:red@0.5

```

The previous example can be specified as:

```
drawbox=x=10:y=20:w=200:h=60:color=red@0.5

```

- Fill the box with pink color:

```
drawbox=x=10:y=10:w=100:h=100:color=pink@0.5:t=fill

```

- Draw a 2-pixel red 2.40:1 mask:

```
drawbox=x=-t:y=0.5*(ih-iw/2.4)-t:w=iw+t*2:h=iw/2.4+t*2:t=2:c=red

```

## 43 VideoToolbox Video Filters# TOC

Below is a description of the currently available VideoToolbox video filters.

VideoToolbox filter depends on VideoToolbox framework, and is auto detected when building ffmpeg for an Apple platform such as macOS. Add --enable-videotoolbox to configure if autodetect is disabled.

### 43.1 scale_vt# TOC

Scale and convert the color parameters using VTPixelTransferSession.

The filter accepts the following options:

w

h

Set the output video dimension expression. Default value is the input dimension.

color_matrix

Set the output colorspace matrix.

color_primaries

Set the output color primaries.

color_transfer

Set the output transfer characteristics.

#### 43.1.1 Examples# TOC

- Perform HDR to SDR conversion, and scale to half size of input

```
ffmpeg -hwaccel videotoolbox \
        -hwaccel_output_format videotoolbox_vld \
        -i hdr.mov \
        -c:v hevc_videotoolbox \
        -profile:v main \
        -b:v 3M \
        -vf scale_vt=w=iw/2:h=ih/2:color_matrix=bt709:color_primaries=bt709:color_transfer=bt709 \
        -c:a copy \
        -tag:v hvc1 \
        sdr.mp4

```

### 43.2 transpose_vt# TOC

Transpose rows with columns in the input video and optionally flip it. For more in depth examples see the transpose video filter, which shares mostly the same options.

It accepts the following parameters:

dir

Specify the transposition direction.

Can assume the following values:

‘cclock_flip’

Rotate by 90 degrees counterclockwise and vertically flip. (default)

‘clock’

Rotate by 90 degrees clockwise.

‘cclock’

Rotate by 90 degrees counterclockwise.

‘clock_flip’

Rotate by 90 degrees clockwise and vertically flip.

‘hflip’

Flip the input video horizontally.

‘vflip’

Flip the input video vertically.

passthrough

Do not apply the transposition if the input geometry matches the one specified by the specified value. It accepts the following values:

‘none’

Always apply transposition. (default)

‘portrait’

Preserve portrait geometry (when height >= width).

‘landscape’

Preserve landscape geometry (when width >= height).

## 44 Vulkan Video Filters# TOC

Below is a description of the currently available Vulkan video filters.

To enable compilation of these filters you need to configure FFmpeg with --enable-vulkan, and have a SPIR-V compiler (glslc or glslangValidator) available at build time.

Running Vulkan filters requires you to initialize a hardware device and to pass that device to all filters in any filter graph.

-init_hw_device vulkan[=name][:device[,key=value...]]

Initialise a new hardware device of type vulkan called name, using the given device parameters and options in key=value. The following options are supported:

debug

Switches validation layers on if set to 1.

linear_images

Allocates linear images. Does not apply to decoding.

disable_multiplane

Disables multiplane images. Does not apply to decoding.

avoid_host_import

Avoids the use of dynamic host memory imports, in favor of a regular memcpy() into a previously mapped buffer.

-filter_hw_device name

Pass the hardware device called name to all filters in any filter graph.

For more detailed information see https://www.ffmpeg.org/ffmpeg.html#Advanced-Video-options

- Example of choosing the first device and running nlmeans_vulkan filter with default parameters on it.

```
-init_hw_device vulkan=vk:0 -filter_hw_device vk -i INPUT -vf "hwupload,nlmeans_vulkan,hwdownload" OUTPUT

```

As Vulkan filters are not able to access frame data in normal memory, all frame data needs to be uploaded (hwupload) to hardware surfaces connected to the appropriate device before being used and then downloaded (hwdownload) back to normal memory. Note that hwupload will upload to a frame with the same layout as the software frame, so it may be necessary to add a format filter immediately before to get the input into the right format and hwdownload does not support all formats on the output - it is usually necessary to insert an additional format filter immediately following in the graph to get the output in a supported format.

### 44.1 avgblur_vulkan# TOC

Apply an average blur filter, implemented on the GPU using Vulkan.

The filter accepts the following options:

sizeX

Set horizontal radius size. Range is [1, 32] and default value is 3.

sizeY

Set vertical radius size. Range is [1, 32] and default value is 3.

planes

Set which planes to filter. Default value is 0xf, by which all planes are processed.

### 44.2 blend_vulkan# TOC

Blend two Vulkan frames into each other.

The blend filter takes two input streams and outputs one stream, the first input is the "top" layer and second input is "bottom" layer. By default, the output terminates when the longest input terminates.

A description of the accepted options follows.

c0_mode

c1_mode

c2_mode

c3_mode

all_mode

Set blend mode for specific pixel component or all pixel components in case of all_mode. Default value is normal.

Available values for component modes are:

‘normal’

‘multiply’

### 44.3 bwdif_vulkan# TOC

Deinterlacer using bwdif, the "Bob Weaver Deinterlacing Filter" algorithm, implemented on the GPU using Vulkan.

It accepts the following parameters:

mode

The interlacing mode to adopt. It accepts one of the following values:

0, send_frame

Output one frame for each frame.

1, send_field

Output one frame for each field.

The default value is send_field.

parity

The picture field parity assumed for the input interlaced video. It accepts one of the following values:

0, tff

Assume the top field is first.

1, bff

Assume the bottom field is first.

-1, auto

Enable automatic detection of field parity.

The default value is auto. If the interlacing is unknown or the decoder does not export this information, top field first will be assumed.

deint

Specify which frames to deinterlace. Accepts one of the following values:

0, all

Deinterlace all frames.

1, interlaced

Only deinterlace frames marked as interlaced.

The default value is all.

### 44.4 chromaber_vulkan# TOC

Apply an effect that emulates chromatic aberration. Works best with RGB inputs, but provides a similar effect with YCbCr inputs too.

dist_x

Horizontal displacement multiplier. Each chroma pixel’s position will be multiplied by this amount, starting from the center of the image. Default is 0.

dist_y

Similarly, this sets the vertical displacement multiplier. Default is 0.

### 44.5 color_vulkan# TOC

Video source that creates a Vulkan frame of a solid color. Useful for benchmarking, or overlaying.

It accepts the following parameters:

color

The color to use. Either a name, or a hexadecimal value. The default value is black.

size

The size of the output frame. Default value is 1920x1080.

rate

The framerate to output at. Default value is 60 frames per second.

duration

The video duration. Default value is -0.000001.

sar

The video signal aspect ratio. Default value is 1/1.

format

The pixel format of the output Vulkan frames. Default value is yuv444p.

out_range

Set the output YCbCr sample range.

This allows the autodetected value to be overridden as well as allows forcing a specific value used for the output and encoder. If not specified, the range depends on the pixel format. Possible values:

‘auto/unknown’

Choose automatically.

‘jpeg/full/pc’

Set full range (0-255 in case of 8-bit luma).

‘mpeg/limited/tv’

Set "MPEG" range (16-235 in case of 8-bit luma).

### 44.6 vflip_vulkan# TOC

Flips an image vertically.

### 44.7 hflip_vulkan# TOC

Flips an image horizontally.

### 44.8 flip_vulkan# TOC

Flips an image along both the vertical and horizontal axis.

### 44.9 fruc_vulkan# TOC

Frame rate up-conversion using the NVIDIA Vulkan optical flow extension (VK_NV_optical_flow), implemented on the GPU using Vulkan.

For each pair of consecutive input frames the filter computes a forward and backward optical flow field on the device’s optical flow engine, and uses those fields to synthesise motion-compensated intermediate frames at the requested output frame rate. The frame timing logic mirrors the framerate filter.

The majority of YUV and RGB pixel formats are supported. The exceptions are subsampled packed YUV formats such as yuyv422 and uyvy422, formats with more than 16 bits integer data per component, such as rgb96 and gray32, and Bayer formats.

fps

A string describing the desired output frame rate, evaluated as an expression. The following constants are available: source_fps. The default value is 60.

perf

Optical flow performance level, trading motion-estimation quality for speed. This is the dominant cost at high resolutions. Possible values are:

‘slow’

Highest quality, slowest. This is the default.

‘medium’

Balanced quality and speed.

‘fast’

Lowest quality, fastest.

grid

Optical flow output grid size in pixels. A coarser grid computes fewer flow vectors, making it faster and less memory hungry at the cost of flow detail. Possible values are auto (the default; selects the finest grid the device supports, usually 1x1), 1, 2, 4 and 8. Only grid sizes the device advertises are accepted.

### 44.10 gblur_vulkan# TOC

Apply Gaussian blur filter on Vulkan frames.

The filter accepts the following options:

sigma

Set horizontal sigma, standard deviation of Gaussian blur. Default is 0.5.

sigmaV

Set vertical sigma, if negative it will be same as sigma. Default is -1.

planes

Set which planes to filter. By default all planes are filtered.

size

Set the kernel size along the horizontal axis. Default is 19.

sizeV

Set the kernel size along the vertical axis. Default is 0, which sets to use the same value as size.

### 44.11 nlmeans_vulkan# TOC

Denoise frames using Non-Local Means algorithm, implemented on the GPU using Vulkan. Supports more pixel formats than nlmeans or nlmeans_opencl, including alpha channel support.

The filter accepts the following options.

s

Set denoising strength for all components. Default is 1.0. Must be in range [0.0, 100.0].

p

Set patch size for all planes. Default is 7. Must be odd number in range [0, 99].

r

Set research size. Default is 15. Must be odd number in range [0, 99].

t

Set parallelism. Default is 8. Must be a number in the range [1, 64]. Larger values will use more VRAM but may not result in greater speed. The optimal value is hardware and input dependent.

s0

s1

s2

s3

Set denoising strength for a specific component. Default is 1.0, equal to s. Must be in range [0.0, 100.0]. 0.0 disables denoising in that component.

p0

p1

p2

p3

Set patch size for a specific component. Default is 7, equal to p. Must be odd number in range [0, 99].

### 44.12 overlay_vulkan# TOC

Overlay one video on top of another.

It takes two inputs and has one output. The first input is the "main" video on which the second input is overlaid. This filter requires all inputs to use the same pixel format. So, format conversion may be needed.

The filter accepts the following options:

x

Set the x coordinate of the overlaid video on the main video. Default value is 0.

y

Set the y coordinate of the overlaid video on the main video. Default value is 0.

### 44.13 transpose_vulkan# TOC

Transpose rows with columns in the input video and optionally flip it. For more in depth examples see the transpose video filter, which shares mostly the same options.

It accepts the following parameters:

dir

Specify the transposition direction.

Can assume the following values:

‘cclock_flip’

Rotate by 90 degrees counterclockwise and vertically flip. (default)

‘clock’

Rotate by 90 degrees clockwise.

‘cclock’

Rotate by 90 degrees counterclockwise.

‘clock_flip’

Rotate by 90 degrees clockwise and vertically flip.

passthrough

Do not apply the transposition if the input geometry matches the one specified by the specified value. It accepts the following values:

‘none’

Always apply transposition. (default)

‘portrait’

Preserve portrait geometry (when height >= width).

‘landscape’

Preserve landscape geometry (when width >= height).

### 44.14 v360_vulkan# TOC

Convert 360 videos between various formats. Supported formats (projections) are subset of v360 filter, that are most popular 360-degree video formats.

The filter accepts subset of v360 options:

input

output

Set format of the input/output video.

‘e’

‘equirect’

Equirectangular projection.

‘eac’

Equi-Angular Cubemap. (Output only)

FIXME: current output doesn’t contain padding.

‘flat’

Regular video.

‘dfisheye’

Dual fisheye.

‘sg’

Stereographic format.

‘fisheye’

Fisheye projection.

‘gopromax’

GoPro Max .360 format. (Input only)

A .360 video file contains two video streams (front and rear); with this input projection the filter takes two inputs and combines them into a single stream. See the overlap option.

w

h

Set the output video resolution. See v360 options.

yaw

pitch

roll

rorder

Set rotation for the output video. See v360 options.

h_fov

v_fov

Set output horizontal/vertical field of view. See v360 options.

ih_fov

iv_fov

Set input horizontal/vertical field of view. See v360 options.

overlap

Set number of overlapped pixels on input .360 video. Only used with input=gopromax.

The GoPro Max .360 video contains overlapped area (See https://gopro.com/news/max-tech-specs-stitching-resolution). The filter blends overlapped images in these two areas.

The number of pixels of overlapped areas depends on the video resolution. In most cases, the value is automatically calculated based on input video size, but it may be changed on GoPro Max2 or future models. The option is to adjust for unknown video resolutions.

#### 44.14.1 Examples# TOC

Special notes exist to use with input=gopromax.

The GoPro Max .360 video file contains two video streams, and the stream number must be specified. The stream number (e.g., [0:5]) depends on the model and shooting mode. Please check actual stream number with ffprobe command.

- Convert GoPro Max (8bit color depth) .360 to Equirectangular projection. GoPro Max uses obsolete yuvj420p pixel format, thus convert the format to yuv420p before this filter.

```
ffmpeg -init_hw_device vulkan -i INPUT.360 -filter_complex "[0:0]format=yuv420p,hwupload[vf],[0:5]format=yuv420p,hwupload[vr], [vf][vr]v360_vulkan=input=gopromax:output=e, hwdownload,format=yuv420p" OUTPUT.mkv

```

- Convert GoPro Max2 (10bit color depth) .360 to Dual fisheye projection. GoPro Max2 uses yuv420p10le pixel format.

```
ffmpeg -init_hw_device vulkan -i INPUT.360 -filter_complex "[0:0]hwupload[vf],[0:4]hwupload[vr], [vf][vr]v360_vulkan=input=gopromax:output=dfisheye, hwdownload,format=yuv420p10le" OUTPUT.mkv

```

## 45 QSV Video Filters# TOC

Below is a description of the currently available QSV video filters.

To enable compilation of these filters you need to configure FFmpeg with --enable-libmfx or --enable-libvpl.

To use QSV filters, you need to setup the QSV device correctly. For more information, please read https://trac.ffmpeg.org/wiki/Hardware/QuickSync

### 45.1 hstack_qsv# TOC

Stack input videos horizontally.

This is the QSV variant of the hstack filter, each input stream may have different height, this filter will scale down/up each input stream while keeping the original aspect.

It accepts the following options:

inputs

See hstack.

shortest

See hstack.

height

Set height of output. If set to 0, this filter will set height of output to height of the first input stream. Default value is 0.

### 45.2 vstack_qsv# TOC

Stack input videos vertically.

This is the QSV variant of the vstack filter, each input stream may have different width, this filter will scale down/up each input stream while keeping the original aspect.

It accepts the following options:

inputs

See vstack.

shortest

See vstack.

width

Set width of output. If set to 0, this filter will set width of output to width of the first input stream. Default value is 0.

### 45.3 xstack_qsv# TOC

Stack video inputs into custom layout.

This is the QSV variant of the xstack filter.

It accepts the following options:

inputs

See xstack.

shortest

See xstack.

layout

See xstack. Moreover, this permits the user to supply output size for each input stream.

```
xstack_qsv=inputs=4:layout=0_0_1920x1080|0_h0_1920x1080|w0_0_1920x1080|w0_h0_1920x1080

```

grid

See xstack.

grid_tile_size

Set output size for each input stream when grid is set. If this option is not set, this filter will set output size by default to the size of the first input stream. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual.

fill

See xstack.

## 46 Video Sources# TOC

Below is a description of the currently available video sources.

### 46.1 buffer# TOC

Buffer video frames, and make them available to the filter chain.

This source is mainly intended for a programmatic use, in particular through the interface defined in libavfilter/buffersrc.h.

It accepts the following parameters:

video_size

Specify the size (width and height) of the buffered video frames. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual.

width

The input video width.

height

The input video height.

pix_fmt

A string representing the pixel format of the buffered video frames. It may be a number corresponding to a pixel format, or a pixel format name.

time_base

Specify the timebase assumed by the timestamps of the buffered frames.

frame_rate

Specify the frame rate expected for the video stream.

colorspace

A string representing the color space of the buffered video frames. It may be a number corresponding to a color space, or a color space name.

range

A string representing the color range of the buffered video frames. It may be a number corresponding to a color range, or a color range name.

alpha_mode

A string representing the alpha mode of the buffered video frames. It may be a number corresponding to an alpha mode, or an alpha mode name.

chroma_location

A string representing the chroma sample location of the buffered video frames. It may be a number corresponding to a chroma sample location, or a chroma sample location name. When it is not set, the filtergraph chooses the chroma sample location of the output. Frames without a chroma sample location are tagged with the one negotiated for the output.

pixel_aspect, sar

The sample (pixel) aspect ratio of the input video.

hw_frames_ctx

When using a hardware pixel format, this should be a reference to an AVHWFramesContext describing input frames.

For example:

```
buffer=width=320:height=240:pix_fmt=yuv410p:time_base=1/24:sar=1

```

will instruct the source to accept video frames with size 320x240 and with format "yuv410p", assuming 1/24 as the timestamps timebase and square pixels (1:1 sample aspect ratio). Since the pixel format with name "yuv410p" corresponds to the number 6 (check the enum AVPixelFormat definition in libavutil/pixfmt.h), this example corresponds to:

```
buffer=size=320x240:pixfmt=6:time_base=1/24:pixel_aspect=1/1

```

Alternatively, the options can be specified as a flat string, but this syntax is deprecated:

width:height:pix_fmt:time_base.num:time_base.den:pixel_aspect.num:pixel_aspect.den

### 46.2 cellauto# TOC

Create a pattern generated by an elementary cellular automaton.

The initial state of the cellular automaton can be defined through the filename and pattern options. If such options are not specified an initial state is created randomly.

At each new frame a new row in the video is filled with the result of the cellular automaton next generation. The behavior when the whole frame is filled is defined by the scroll option.

This source accepts the following options:

filename, f

Read the initial cellular automaton state, i.e. the starting row, from the specified file. In the file, each non-whitespace character is considered an alive cell, a newline will terminate the row, and further characters in the file will be ignored.

pattern, p

Read the initial cellular automaton state, i.e. the starting row, from the specified string.

Each non-whitespace character in the string is considered an alive cell, a newline will terminate the row, and further characters in the string will be ignored.

rate, r

Set the video rate, that is the number of frames generated per second. Default is 25.

random_fill_ratio, ratio

Set the random fill ratio for the initial cellular automaton row. It is a floating point number value ranging from 0 to 1, defaults to 1/PHI.

This option is ignored when a file or a pattern is specified.

random_seed, seed

Set the seed for filling randomly the initial row, must be an integer included between 0 and UINT32_MAX. If not specified, or if explicitly set to -1, the filter will try to use a good random seed on a best effort basis.

rule

Set the cellular automaton rule, it is a number ranging from 0 to 255. Default value is 110.

size, s

Set the size of the output video. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual.

If filename or pattern is specified, the size is set by default to the width of the specified initial state row, and the height is set to width * PHI.

If size is set, it must contain the width of the specified pattern string, and the specified pattern will be centered in the larger row.

If a filename or a pattern string is not specified, the size value defaults to "320x518" (used for a randomly generated initial state).

scroll

If set to 1, scroll the output upward when all the rows in the output have been already filled. If set to 0, the new generated row will be written over the top row just after the bottom row is filled. Defaults to 1.

start_full, full

If set to 1, completely fill the output with generated rows before outputting the first frame. This is the default behavior, for disabling set the value to 0.

stitch

If set to 1, stitch the left and right row edges together. This is the default behavior, for disabling set the value to 0.

#### 46.2.1 Examples# TOC

- Read the initial state from pattern, and specify an output of size 200x400.

```
cellauto=f=pattern:s=200x400

```

- Generate a random initial row with a width of 200 cells, with a fill ratio of 2/3:

```
cellauto=ratio=2/3:s=200x200

```

- Create a pattern generated by rule 18 starting by a single alive cell centered on an initial row with width 100:

```
cellauto=p=@:s=100x400:full=0:rule=18

```

- Specify a more elaborated initial pattern:

```
cellauto=p='@@ @ @@':s=100x400:full=0:rule=18

```

### 46.3 coreimagesrc# TOC

Video source generated on GPU using Apple’s CoreImage API on OSX.

This video source is a specialized version of the coreimage video filter. Use a core image generator at the beginning of the applied filterchain to generate the content.

The coreimagesrc video source accepts the following options:

list_generators

List all available generators along with all their respective options as well as possible minimum and maximum values along with the default values.

```
list_generators=true

```

size, s

Specify the size of the sourced video. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual. The default value is 320x240.

rate, r

Specify the frame rate of the sourced video, as the number of frames generated per second. It has to be a string in the format frame_rate_num/frame_rate_den, an integer number, a floating point number or a valid video frame rate abbreviation. The default value is "25".

sar

Set the sample aspect ratio of the sourced video.

duration, d

Set the duration of the sourced video. See the Time duration section in the ffmpeg-utils(1) manual for the accepted syntax.

If not specified, or the expressed duration is negative, the video is supposed to be generated forever.

Additionally, all options of the coreimage video filter are accepted. A complete filterchain can be used for further processing of the generated input without CPU-HOST transfer. See coreimage documentation and examples for details.

#### 46.3.1 Examples# TOC

- Use CIQRCodeGenerator to create a QR code for the FFmpeg homepage, given as complete and escaped command-line for Apple’s standard bash shell:

```
ffmpeg -f lavfi -i coreimagesrc=s=100x100:filter=CIQRCodeGenerator@inputMessage=https\\\\\://FFmpeg.org/@inputCorrectionLevel=H -frames:v 1 QRCode.png

```

This example is equivalent to the QRCode example of coreimage without the need for a nullsrc video source.

### 46.4 ddagrab# TOC

Captures the Windows Desktop via Desktop Duplication API.

The filter exclusively returns D3D11 Hardware Frames, for on-gpu encoding or processing. So an explicit hwdownload is needed for any kind of software processing.

It accepts the following options:

output_idx

DXGI Output Index to capture.

Usually corresponds to the index Windows has given the screen minus one, so it’s starting at 0.

Defaults to output 0.

draw_mouse

Whether to draw the mouse cursor.

Defaults to true.

Only affects hardware cursors. If a game or application renders its own cursor, it’ll always be captured.

framerate

Maximum framerate at which the desktop will be captured - the interval between successive frames will not be smaller than the inverse of the framerate. When dup_frames is true (the default) and the desktop is not being updated often enough, the filter will duplicate a previous frame. Note that there is no background buffering going on, so when the filter is not polled often enough then the actual inter-frame interval may be significantly larger.

Defaults to 30 FPS.

video_size

Specify the size of the captured video.

Defaults to the full size of the screen.

Cropped from the bottom/right if smaller than screen size.

offset_x

Horizontal offset of the captured video.

offset_y

Vertical offset of the captured video.

output_fmt

Desired filter output format. Defaults to 8 Bit BGRA.

It accepts the following values:

‘auto’

Passes all supported output formats to DDA and returns what DDA decides to use.

‘8bit’

‘bgra’

8 Bit formats always work, and DDA will convert to them if necessary.

‘10bit’

‘x2bgr10’

Filter initialization will fail if 10 bit format is requested but unavailable.

dup_frames

When this option is set to true (the default), the filter will duplicate frames when the desktop has not been updated in order to maintain approximately constant target framerate. When this option is set to false, the filter will wait for the desktop to be updated (inter-frame intervals may vary significantly in this case).

#### 46.4.1 Examples# TOC

Capture primary screen and encode using nvenc:

```
ffmpeg -f lavfi -i ddagrab -c:v h264_nvenc -cq 18 output.mp4

```

You can also skip the lavfi device and directly use the filter. Also demonstrates downloading the frame and encoding with libx264. Explicit output format specification is required in this case:

```
ffmpeg -filter_complex ddagrab=output_idx=1:framerate=60,hwdownload,format=bgra -c:v libx264 -crf 18 output.mp4

```

If you want to capture only a subsection of the desktop, this can be achieved by specifying a smaller size and its offsets into the screen:

```
ddagrab=video_size=800x600:offset_x=100:offset_y=100

```

### 46.5 gfxcapture# TOC

Capture windows or monitors using Windows.Graphics.Capture API.

This source provides low overhead capture of application windows or entire monitors. The filter outputs hardware frames in d3d11 format; use hwdownload,format= if system memory frames are required.

The window to be captured can be selected via regular expressions on its title, class name or backing executable name, by explicit native handles, or by monitor index or explicit native handle. A window must match all provided expressions to be selected. The first matching window will be picked, in whatever order Windows returns them.

Explicit handles (hwnd, hmonitor) override pattern or index based selection. If neither handles nor a monitor index are given, the first window matching the provided regular expressions is captured.

This source does NOT hold a stable FPS. It returns frames at whatever rate the compositor provides them, only capped by the max_framerate. If you need a stable rate, you need to add an fps filter to drop/duplicate frames as needed. Note that a static source may not deliver any frames at all, which also stalls the fps filter; see dup_frames.

If the capture source disappears mid-capture (window closed, monitor disconnected), the filter will return EOF.

This source accepts the following options:

window_title

ECMAScript regular expression matched against the window title. Supports a PCRE style (?i) prefix for case-insensitive matching.

window_class

As window_title, but matched against the window class name.

window_exe

As window_title, but matched against the executable file name of the window’s process.

monitor_idx

Zero-based index of the monitor to capture.

Can also be set to window to capture the monitor the selected window is displayed on at filter initialization time.

hwnd

Explicit native window handle (HWND).

hmonitor

Explicit native monitor handle (HMONITOR).

capture_cursor

Capture the mouse cursor. Enabled by default.

capture_border

Capture the full area of the window, including its window decorarions/border. Disabled by default.

display_border

Draw a yellow highlight border around the captured window. Disabled by default.

max_framerate

Maximum capture frame rate. Accepts a video rate (e.g. 30, 60/1, 24000/1001). The default is 60 FPS. The actual rate is the rate at which the compositor renders the window/monitor, capped by this option.

width

Force the output canvas width. If zero (default) the initial captured source width is used. If a negative number is provided, the width will be rounded down to the next multiple of that number.

See resize_mode.

height

Force the output canvas height. If zero (default) the initial captured source height is used. If a negative number is provided, the height will be rounded down to the next multiple of that number.

See resize_mode.

crop_left

Crop this many pixels from the left side of the captured frames.

crop_top

Crop this many pixels from the left side of the captured frames.

crop_right

Crop this many pixels from the left side of the captured frames.

crop_bottom

Crop this many pixels from the left side of the captured frames.

premultiplied

If set to 1, return frames with premultiplied alpha. Default is 0 (straight alpha).

dup_frames

If enabled (the default), the last frame is output again whenever the source delivered no new frame within one max_framerate interval, and black frames are output until the source delivered its first frame. This keeps the output flowing while the captured content is static. The output rate is still not constant, add an fps filter if needed.

resize_mode

Defines how the captured content is fitted into the output canvas size. Possible values:

‘crop’

Crop (or pad with black) to the canvas size. (default)

‘scale’

Scale the source to fill the canvas, potentially altering aspect ratio.

‘scale_aspect’

Scale the source to fit inside the canvas while preserving aspect ratio. Remaining area is filled with black.

scale_mode

Scaling algorithm used when resizing is required.

Possible values:

‘point’

Nearest neighbour (pixelated) scaling.

‘bilinear’

Bilinear filtering. (default)

‘bicubic’

Bicubic filtering. Potentially more blurry, but fewer scaling artifacts depending on contents.

output_fmt

Desired output pixel format inside the D3D11 hardware frames.

Possible values:

‘bgra’

‘8bit’

8 bit BGRA output (default)

‘x2bgr10’

‘10bit’

10 bit BGR output

‘rgbaf16’

‘16bit’

16bit float RGBA output

#### 46.5.1 Examples# TOC

- Capture a window by title (case-insensitive) at a maximum of 60 fps:

```
ffmpeg -filter_complex gfxcapture=window_title='(?i)My Application':max_framerate=60,hwdownload,format=bgra,format=yuv420p -c:v libx264 -crf 15 capture.mp4

```

- Capture monitor 1 at native refresh, 10bit color depth, scale to 1920x1080 preserving aspect:

```
ffmpeg -filter_complex gfxcapture=monitor_idx=1:width=1920:height=1080:resize_mode=scale_aspect:output_fmt=10bit -c:v hevc_nvenc -cq 15 capture.mp4

```

- Capture a window by executable name, draw border, force point scaling, fixed 60 fps:

```
ffmpeg -filter_complex gfxcapture=window_exe='^firefox.exe$':display_border=1:scale_mode=point,fps=60 -rc qvbr -qvbr_quality_level 15 -c:v h264_amf capture.mp4

```

### 46.6 gradients# TOC

Generate several gradients.

size, s

Set frame size. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual. Default value is "640x480".

rate, r

Set frame rate, expressed as number of frames per second. Default value is "25".

c0, c1, c2, c3, c4, c5, c6, c7

Set 8 colors. Default values for colors is to pick random one.

x0, y0, x1, y1

Set gradient line source and destination points. If negative or out of range, random ones are picked.

nb_colors, n

Set number of colors to use at once. Allowed range is from 2 to 8. Default value is 2.

seed

Set seed for picking gradient line points.

duration, d

Set the duration of the sourced video. See the Time duration section in the ffmpeg-utils(1) manual for the accepted syntax.

If not specified, or the expressed duration is negative, the video is supposed to be generated forever.

speed

Set speed of gradients rotation.

type, t

Set type of gradients. Available values are:

‘linear’

‘radial’

‘circular’

‘spiral’

‘square’

Default type is linear.

#### 46.6.1 Commands# TOC

This source supports the some above options as commands.

### 46.7 mandelbrot# TOC

Generate a Mandelbrot set fractal, and progressively zoom towards the point specified with start_x and start_y.

This source accepts the following options:

end_pts

Set the terminal pts value. Default value is 400.

end_scale

Set the terminal scale value. Must be a floating point value. Default value is 0.3.

inner

Set the inner coloring mode, that is the algorithm used to draw the Mandelbrot fractal internal region.

It shall assume one of the following values:

black

Set black mode.

convergence

Show time until convergence.

mincol

Set color based on point closest to the origin of the iterations.

period

Set period mode.

Default value is mincol.

bailout

Set the bailout value. Default value is 10.0.

maxiter

Set the maximum of iterations performed by the rendering algorithm. Default value is 7189.

outer

Set outer coloring mode. It shall assume one of following values:

iteration_count

Set iteration count mode.

normalized_iteration_count

set normalized iteration count mode.

Default value is normalized_iteration_count.

rate, r

Set frame rate, expressed as number of frames per second. Default value is "25".

size, s

Set frame size. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual. Default value is "640x480".

start_scale

Set the initial scale value. Default value is 3.0.

start_x

Set the initial x position. Must be a floating point value between -100 and 100. Default value is -0.743643887037158704752191506114774.

start_y

Set the initial y position. Must be a floating point value between -100 and 100. Default value is -0.131825904205311970493132056385139.

### 46.8 mptestsrc# TOC

Generate various test patterns, as generated by the MPlayer test filter.

The size of the generated video is fixed, and is 512x512. This source is useful in particular for testing encoding features.

This source accepts the following options:

rate, r

Specify the frame rate of the sourced video, as the number of frames generated per second. It has to be a string in the format frame_rate_num/frame_rate_den, an integer number, a floating point number or a valid video frame rate abbreviation. The default value is "25".

duration, d

Set the duration of the sourced video. See the Time duration section in the ffmpeg-utils(1) manual for the accepted syntax.

If not specified, or the expressed duration is negative, the video is supposed to be generated forever.

test, t

Set the number or the name of the test to perform. Supported tests are:

dc_luma

dc_chroma

freq_luma

freq_chroma

amp_luma

amp_chroma

cbp

mv

ring1

ring2

all

max_frames, m

Set the maximum number of frames generated for each test, default value is 30.

Default value is "all", which will cycle through the list of all tests.

Some examples:

```
mptestsrc=t=dc_luma

```

will generate a "dc_luma" test pattern.

### 46.9 frei0r_src# TOC

Provide a frei0r source.

To enable compilation of this filter you need to install the frei0r header and configure FFmpeg with --enable-frei0r.

This source accepts the following parameters:

size

The size of the video to generate. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual.

framerate

The framerate of the generated video. It may be a string of the form num/den or a frame rate abbreviation.

filter_name

The name to the frei0r source to load. For more information regarding frei0r and how to set the parameters, read the frei0r section in the video filters documentation.

filter_params

A ’|’-separated list of parameters to pass to the frei0r source.

For example, to generate a frei0r partik0l source with size 200x200 and frame rate 10 which is overlaid on the overlay filter main input:

```
frei0r_src=size=200x200:framerate=10:filter_name=partik0l:filter_params=1234 [overlay]; [in][overlay] overlay

```

### 46.10 life# TOC

Generate a life pattern.

This source is based on a generalization of John Conway’s life game.

The sourced input represents a life grid, each pixel represents a cell which can be in one of two possible states, alive or dead. Every cell interacts with its eight neighbours, which are the cells that are horizontally, vertically, or diagonally adjacent.

At each interaction the grid evolves according to the adopted rule, which specifies the number of neighbor alive cells which will make a cell stay alive or born. The rule option allows one to specify the rule to adopt.

This source accepts the following options:

filename, f

Set the file from which to read the initial grid state. In the file, each non-whitespace character is considered an alive cell, and newline is used to delimit the end of each row.

If this option is not specified, the initial grid is generated randomly.

rate, r

Set the video rate, that is the number of frames generated per second. Default is 25.

random_fill_ratio, ratio

Set the random fill ratio for the initial random grid. It is a floating point number value ranging from 0 to 1, defaults to 1/PHI. It is ignored when a file is specified.

random_seed, seed

Set the seed for filling the initial random grid, must be an integer included between 0 and UINT32_MAX. If not specified, or if explicitly set to -1, the filter will try to use a good random seed on a best effort basis.

rule

Set the life rule.

A rule can be specified with a code of the kind "SNS/BNB", where NS and NB are sequences of numbers in the range 0-8, NS specifies the number of alive neighbor cells which make a live cell stay alive, and NB the number of alive neighbor cells which make a dead cell to become alive (i.e. to "born"). "s" and "b" can be used in place of "S" and "B", respectively.

Alternatively a rule can be specified by an 18-bits integer. The 9 high order bits are used to encode the next cell state if it is alive for each number of neighbor alive cells, the low order bits specify the rule for "borning" new cells. Higher order bits encode for an higher number of neighbor cells. For example the number 6153 = (12<<9)+9 specifies a stay alive rule of 12 and a born rule of 9, which corresponds to "S23/B03".

Default value is "S23/B3", which is the original Conway’s game of life rule, and will keep a cell alive if it has 2 or 3 neighbor alive cells, and will born a new cell if there are three alive cells around a dead cell.

size, s

Set the size of the output video. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual.

If filename is specified, the size is set by default to the same size of the input file. If size is set, it must contain the size specified in the input file, and the initial grid defined in that file is centered in the larger resulting area.

If a filename is not specified, the size value defaults to "320x240" (used for a randomly generated initial grid).

stitch

If set to 1, stitch the left and right grid edges together, and the top and bottom edges also. Defaults to 1.

mold

Set cell mold speed. If set, a dead cell will go from death_color to mold_color with a step of mold. mold can have a value from 0 to 255.

life_color

Set the color of living (or new born) cells.

death_color

Set the color of dead cells. If mold is set, this is the first color used to represent a dead cell.

mold_color

Set mold color, for definitely dead and moldy cells.

For the syntax of these 3 color options, check the "Color" section in the ffmpeg-utils manual.

#### 46.10.1 Examples# TOC

- Read a grid from pattern, and center it on a grid of size 300x300 pixels:

```
life=f=pattern:s=300x300

```

- Generate a random grid of size 200x200, with a fill ratio of 2/3:

```
life=ratio=2/3:s=200x200

```

- Specify a custom rule for evolving a randomly generated grid:

```
life=rule=S14/B34

```

- Full example with slow death effect (mold) using ffplay:

```
ffplay -f lavfi life=s=300x200:mold=10:r=60:ratio=0.1:death_color=#C83232:life_color=#00ff00,scale=1200:800:flags=16

```

### 46.11 perlin# TOC

Generate Perlin noise.

Perlin noise is a kind of noise with local continuity in space. This can be used to generate patterns with continuity in space and time, e.g. to simulate smoke, fluids, or terrain.

In case more than one octave is specified through the octaves option, Perlin noise is generated as a sum of components, each one with doubled frequency. In this case the persistence option specify the ratio of the amplitude with respect to the previous component. More octave components enable to specify more high frequency details in the generated noise (e.g. small size variations due to boulders in a generated terrain).

#### 46.11.1 Options# TOC

size, s

Specify the size (width and height) of the buffered video frames. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual. Default value is 320x240.

rate, r

Specify the frame rate expected for the video stream, expressed as a number of frames per second. Default value is 25.

octaves

Specify the total number of components making up the noise, each one with doubled frequency. Default value is 1.

persistence

Set the ratio used to compute the amplitude of the next octave component with respect to the previous component amplitude. Default value is 1.

xscale

yscale

Define a scale factor used to multiple the x, y coordinates. This can be useful to define an effect with a pattern stretched along the x or y axis. Default value is 1.

tscale

Define a scale factor used to multiple the time coordinate. This can be useful to change the time variation speed. Default value is 1.

random_mode

Set random mode used to compute initial pattern.

Supported values are:

random

Compute and use random seed.

ken

Use the predefined initial pattern defined by Ken Perlin in the original article, can be useful to compare the output with other sources.

seed

Use the value specified by random_seed option.

Default value is random.

random_seed, seed

When random_mode is set to random_seed, use this value to compute the initial pattern. Default value is 0.

#### 46.11.2 Examples# TOC

- Generate single component:

```
perlin

```

- Use Perlin noise with 7 components, each one with a halved contribution to total amplitude:

```
perlin=octaves=7:persistence=0.5

```

- Chain Perlin noise with the lutyuv to generate a black&white effect:

```
perlin=octaves=3:tscale=0.3,lutyuv=y='if(lt(val\,128)\,255\,0)'

```

- Stretch noise along the y axis, and convert gray level to red-only signal:

```
perlin=octaves=7:tscale=0.4:yscale=0.3,lutrgb=r=val:b=0:g=0

```

### 46.12 qrencodesrc# TOC

Generate a QR code using the libqrencode library (see https://fukuchi.org/works/qrencode/).

To enable the compilation of this source, you need to configure FFmpeg with --enable-libqrencode.

The QR code is generated from the provided text or text pattern. The corresponding QR code is scaled and put in the video output according to the specified output size options.

In case no text is specified, the QR code is not generated, but an empty colored output is returned instead.

This source accepts the following options:

qrcode_width, q

padded_qrcode_width, Q

Specify an expression for the width of the rendered QR code, with and without padding. The qrcode_width expression can reference the value set by the padded_qrcode_width expression, and vice versa. By default padded_qrcode_width is set to qrcode_width, meaning that there is no padding.

These expressions are evaluated only once, when initializing the source. See the qrencode Expressions section for details.

Note that some of the constants are missing for the source (for example the x or t or ¸n), since they only makes sense when evaluating the expression for each frame rather than at initialization time.

rate, r

Specify the frame rate of the sourced video, as the number of frames generated per second. It has to be a string in the format frame_rate_num/frame_rate_den, an integer number, a floating point number or a valid video frame rate abbreviation. The default value is "25".

case_sensitive, cs

Instruct libqrencode to use case sensitive encoding. This is enabled by default. This can be disabled to reduce the QR encoding size.

level, l

Specify the QR encoding error correction level. With an higher correction level, the encoding size will increase but the code will be more robust to corruption. Lower level is L.

It accepts the following values:

‘L’

‘M’

‘Q’

‘H’

expansion

Select how the input text is expanded. Can be either none, or normal (default). See the qrencode Text expansion section for details.

text

textfile

Define the text to be rendered. In case neither is specified, no QR is encoded (just an empty colored frame).

In case expansion is enabled, the text is treated as a text template, using the qrencode expansion mechanism. See the qrencode Text expansion section for details.

background_color, bc

foreground_color, fc

Set the QR code and background color. The default value of foreground_color is "black", the default value of background_color is "white".

For the syntax of the color options, check the "Color" section in the ffmpeg-utils manual.

#### 46.12.1 Examples# TOC

- Generate a QR code encoding the specified text with the default size:

```
qrencodesrc=text=www.ffmpeg.org

```

- Same as below, but select blue on pink colors:

```
qrencodesrc=text=www.ffmpeg.org:bc=pink:fc=blue

```

- Generate a QR code with width of 200 pixels and padding, making the padded width 4/3 of the QR code width:

```
qrencodesrc=text=www.ffmpeg.org:q=200:Q=4/3*q

```

- Generate a QR code with padded width of 200 pixels and padding, making the QR code width 3/4 of the padded width:

```
qrencodesrc=text=www.ffmpeg.org:Q=200:q=3/4*Q

```

- Generate a QR code encoding the frame number:

```
qrencodesrc=text=%{n}

```

- Generate a QR code encoding the GMT timestamp:

```
qrencodesrc=text=%{gmtime}

```

- Generate a QR code encoding the timestamp expressed as a float:

```
qrencodesrc=text=%{pts}

```

### 46.13 allrgb, allyuv, color, colorchart, colorspectrum, haldclutsrc, nullsrc, pal75bars, pal100bars, rgbtestsrc, smptebars, smptehdbars, testsrc, testsrc2, yuvtestsrc# TOC

The allrgb source returns frames of size 4096x4096 of all rgb colors.

The allyuv source returns frames of size 4096x4096 of all yuv colors.

The color source provides an uniformly colored input.

The colorchart source provides a colors checker chart.

The colorspectrum source provides a color spectrum input.

The haldclutsrc source provides an identity Hald CLUT. See also haldclut filter.

The nullsrc source returns unprocessed video frames. It is mainly useful to be employed in analysis / debugging tools, or as the source for filters which ignore the input data.

The pal75bars source generates a color bars pattern, based on EBU PAL recommendations with 75% color levels.

The pal100bars source generates a color bars pattern, based on EBU PAL recommendations with 100% color levels.

The rgbtestsrc source generates an RGB test pattern useful for detecting RGB vs BGR issues. You should see a red, green and blue stripe from top to bottom.

The smptebars source generates a color bars pattern, based on the SMPTE Engineering Guideline EG 1-1990.

The smptehdbars source generates a color bars pattern, based on the SMPTE RP 219-2002.

The testsrc source generates a test video pattern, showing a color pattern, a scrolling gradient and a timestamp. This is mainly intended for testing purposes.

The testsrc2 source is similar to testsrc, but supports more pixel formats instead of just rgb24. This allows using it as an input for other tests without requiring a format conversion.

The yuvtestsrc source generates an YUV test pattern. You should see a y, cb and cr stripe from top to bottom.

The sources accept the following parameters:

level

Specify the level of the Hald CLUT, only available in the haldclutsrc source. A level of N generates a picture of N*N*N by N*N*N pixels to be used as identity matrix for 3D lookup tables. Each component is coded on a 1/(N*N) scale.

color, c

Specify the color of the source, only available in the color source. For the syntax of this option, check the "Color" section in the ffmpeg-utils manual.

size, s

Specify the size of the sourced video. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual. The default value is 320x240.

This option is not available with the allrgb, allyuv, and haldclutsrc filters.

rate, r

Specify the frame rate of the sourced video, as the number of frames generated per second. It has to be a string in the format frame_rate_num/frame_rate_den, an integer number, a floating point number or a valid video frame rate abbreviation. The default value is "25".

duration, d

Set the duration of the sourced video. See the Time duration section in the ffmpeg-utils(1) manual for the accepted syntax.

If not specified, or the expressed duration is negative, the video is supposed to be generated forever.

Since the frame rate is used as time base, all frames including the last one will have their full duration. If the specified duration is not a multiple of the frame duration, it will be rounded up.

sar

Set the sample aspect ratio of the sourced video.

alpha

Specify the alpha (opacity) of the background, only available in the testsrc2 source. The value must be between 0 (fully transparent) and 255 (fully opaque, the default).

decimals, n

Set the number of decimals to show in the timestamp, only available in the testsrc source.

The displayed timestamp value will correspond to the original timestamp value multiplied by the power of 10 of the specified value. Default value is 0.

type

Set the type of the color spectrum, only available in the colorspectrum source. Can be one of the following:

‘black’

‘white’

‘all’

patch_size

Set patch size of single color patch, only available in the colorchart source. Default is 64x64.

preset

Set colorchecker colors preset, only available in the colorchart source.

Available values are:

‘reference’

‘skintones’

Default value is reference.

#### 46.13.1 Examples# TOC

- Generate a video with a duration of 5.3 seconds, with size 176x144 and a frame rate of 10 frames per second:

```
testsrc=duration=5.3:size=qcif:rate=10

```

- The following graph description will generate a red source with an opacity of 0.2, with size "qcif" and a frame rate of 10 frames per second:

```
color=c=red@0.2:s=qcif:r=10

```

- If the input content is to be ignored, nullsrc can be used. The following command generates noise in the luma plane by employing the geq filter:

```
nullsrc=s=256x256, geq=random(1)*255:128:128

```

#### 46.13.2 Commands# TOC

The color source supports the following commands:

c, color

Set the color of the created image. Accepts the same syntax of the corresponding color option.

### 46.14 openclsrc# TOC

Generate video using an OpenCL program.

source

OpenCL program source file.

kernel

Kernel name in program.

size, s

Size of frames to generate. This must be set.

format

Pixel format to use for the generated frames. This must be set.

rate, r

Number of frames generated every second. Default value is ’25’.

For details of how the program loading works, see the program_opencl filter.

Example programs:

- Generate a colour ramp by setting pixel values from the position of the pixel in the output image. (Note that this will work with all pixel formats, but the generated output will not be the same.)
```
__kernel void ramp(__write_only image2d_t dst,
                   unsigned int index)
{
    int2 loc = (int2)(get_global_id(0), get_global_id(1));

    float4 val;
    val.xy = val.zw = convert_float2(loc) / convert_float2(get_image_dim(dst));

    write_imagef(dst, loc, val);
}

```

- Generate a Sierpinski carpet pattern, panning by a single pixel each frame.
```
__kernel void sierpinski_carpet(__write_only image2d_t dst,
                                unsigned int index)
{
    int2 loc = (int2)(get_global_id(0), get_global_id(1));

    float4 value = 0.0f;
    int x = loc.x + index;
    int y = loc.y + index;
    while (x > 0 || y > 0) {
        if (x % 3 == 1 && y % 3 == 1) {
            value = 1.0f;
            break;
        }
        x /= 3;
        y /= 3;
    }

    write_imagef(dst, loc, value);
}

```

### 46.15 sierpinski# TOC

Generate a Sierpinski carpet/triangle fractal, and randomly pan around.

This source accepts the following options:

size, s

Set frame size. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual. Default value is "640x480".

rate, r

Set frame rate, expressed as number of frames per second. Default value is "25".

seed

Set seed which is used for random panning.

jump

Set max jump for single pan destination. Allowed range is from 1 to 10000.

type

Set fractal type, can be default carpet or triangle.

### 46.16 zoneplate# TOC

Generate a zoneplate test video pattern.

This source accepts the following options:

size, s

Set frame size. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual. Default value is "320x240".

rate, r

Set frame rate, expressed as number of frames per second. Default value is "25".

duration, d

Set the duration of the sourced video. See the Time duration section in the ffmpeg-utils(1) manual for the accepted syntax.

If not specified, or the expressed duration is negative, the video is supposed to be generated forever.

sar

Set the sample aspect ratio of the sourced video.

precision

Set precision in bits for look-up table for sine calculations. Default value is 10. Allowed range is from 4 to 16.

xo

Set horizontal axis offset for output signal. Default value is 0.

yo

Set vertical axis offset for output signal. Default value is 0.

to

Set time axis offset for output signal. Default value is 0.

k0

Set 0-order, constant added to signal phase. Default value is 0.

kx

Set 1-order, phase factor multiplier for horizontal axis. Default value is 0.

ky

Set 1-order, phase factor multiplier for vertical axis. Default value is 0.

kt

Set 1-order, phase factor multiplier for time axis. Default value is 0.

kxt, kyt, kxy

Set phase factor multipliers for combination of spatial and temporal axis. Default value is 0.

kx2

Set 2-order, phase factor multiplier for horizontal axis. Default value is 0.

ky2

Set 2-order, phase factor multiplier for vertical axis. Default value is 0.

kt2

Set 2-order, phase factor multiplier for time axis. Default value is 0.

ku

Set the constant added to final phase to produce chroma-blue component of signal. Default value is 0.

kv

Set the constant added to final phase to produce chroma-red component of signal. Default value is 0.

#### 46.16.1 Commands# TOC

This source supports the some above options as commands.

#### 46.16.2 Examples# TOC

- Generate horizontal color sine sweep:

```
zoneplate=ku=512:kv=0:kt2=0:kx2=256:s=wvga:xo=-426:kt=11

```

- Generate vertical color sine sweep:

```
zoneplate=ku=512:kv=0:kt2=0:ky2=156:s=wvga:yo=-240:kt=11

```

- Generate circular zone-plate:

```
zoneplate=ku=512:kv=100:kt2=0:ky2=256:kx2=556:s=wvga:yo=0:kt=11

```

## 47 Video Sinks# TOC

Below is a description of the currently available video sinks.

### 47.1 buffersink# TOC

Buffer video frames, and make them available to the end of the filter graph.

This sink is mainly intended for programmatic use, in particular through the interface defined in libavfilter/buffersink.h or the options system.

It accepts a pointer to an AVBufferSinkContext structure, which defines the incoming buffers’ formats, to be passed as the opaque parameter to avfilter_init_filter for initialization.

### 47.2 nullsink# TOC

Null video sink: do absolutely nothing with the input video. It is mainly useful as a template and for use in analysis / debugging tools.

## 48 Multimedia Filters# TOC

Below is a description of the currently available multimedia filters.

### 48.1 a3dscope# TOC

Convert input audio to 3d scope video output.

The filter accepts the following options:

rate, r

Set frame rate, expressed as number of frames per second. Default value is "25".

size, s

Specify the video size for the output. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual. Default value is hd720.

fov

Set the camera field of view. Default is 90 degrees. Allowed range is from 40 to 150.

roll

Set the camera roll.

pitch

Set the camera pitch.

yaw

Set the camera yaw.

xzoom

Set the camera zoom on X-axis.

yzoom

Set the camera zoom on Y-axis.

zzoom

Set the camera zoom on Z-axis.

xpos

Set the camera position on X-axis.

ypos

Set the camera position on Y-axis.

zpos

Set the camera position on Z-axis.

length

Set the length of displayed audio waves in number of frames.

#### 48.1.1 Commands# TOC

Filter supports the some above options as commands.

### 48.2 abitscope# TOC

Convert input audio to a video output, displaying the audio bit scope.

The filter accepts the following options:

rate, r

Set frame rate, expressed as number of frames per second. Default value is "25".

size, s

Specify the video size for the output. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual. Default value is 1024x256.

colors

Specify list of colors separated by space or by ’|’ which will be used to draw channels. Unrecognized or missing colors will be replaced by white color.

mode, m

Set output mode. Can be bars or trace. Default is bars.

### 48.3 adrawgraph# TOC

Draw a graph using input audio metadata.

See drawgraph

### 48.4 agraphmonitor# TOC

See graphmonitor.

### 48.5 ahistogram# TOC

Convert input audio to a video output, displaying the volume histogram.

The filter accepts the following options:

dmode

Specify how histogram is calculated.

It accepts the following values:

‘single’

Use single histogram for all channels.

‘separate’

Use separate histogram for each channel.

Default is single.

rate, r

Set frame rate, expressed as number of frames per second. Default value is "25".

size, s

Specify the video size for the output. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual. Default value is hd720.

scale

Set display scale.

It accepts the following values:

‘log’

logarithmic

‘sqrt’

square root

‘cbrt’

cubic root

‘lin’

linear

‘rlog’

reverse logarithmic

Default is log.

ascale

Set amplitude scale.

It accepts the following values:

‘log’

logarithmic

‘lin’

linear

Default is log.

acount

Set how much frames to accumulate in histogram. Default is 1. Setting this to -1 accumulates all frames.

rheight

Set histogram ratio of window height.

slide

Set sonogram sliding.

It accepts the following values:

‘replace’

replace old rows with new ones.

‘scroll’

scroll from top to bottom.

Default is replace.

hmode

Set histogram mode.

It accepts the following values:

‘abs’

Use absolute values of samples.

‘sign’

Use untouched values of samples.

Default is abs.

### 48.6 aphasemeter# TOC

Measures phase of input audio, which is exported as metadata lavfi.aphasemeter.phase, representing mean phase of current audio frame. A video output can also be produced and is enabled by default. The audio is passed through as first output.

Audio will be rematrixed to stereo if it has a different channel layout. Phase value is in range [-1, 1] where -1 means left and right channels are completely out of phase and 1 means channels are in phase.

The filter accepts the following options, all related to its video output:

rate, r

Set the output frame rate. Default value is 25.

size, s

Set the video size for the output. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual. Default value is 800x400.

rc

gc

bc

Specify the red, green, blue contrast. Default values are 2, 7 and 1. Allowed range is [0, 255].

mpc

Set color which will be used for drawing median phase. If color is none which is default, no median phase value will be drawn.

video

Enable video output. Default is enabled.

#### 48.6.1 phasing detection# TOC

The filter also detects out of phase and mono sequences in stereo streams. It logs the sequence start, end and duration when it lasts longer or as long as the minimum set.

The filter accepts the following options for this detection:

phasing

Enable mono and out of phase detection. Default is disabled.

tolerance, t

Set phase tolerance for mono detection, in amplitude ratio. Default is 0. Allowed range is [0, 1].

angle, a

Set angle threshold for out of phase detection, in degree. Default is 170. Allowed range is [90, 180].

duration, d

Set mono or out of phase duration until notification, expressed in seconds. Default is 2.

#### 48.6.2 Examples# TOC

- Complete example with ffmpeg to detect 1 second of mono with 0.001 phase tolerance:

```
ffmpeg -i stereo.wav -af aphasemeter=video=0:phasing=1:duration=1:tolerance=0.001 -f null -

```

### 48.7 avectorscope# TOC

Convert input audio to a video output, representing the audio vector scope.

The filter is used to measure the difference between channels of stereo audio stream. A monaural signal, consisting of identical left and right signal, results in straight vertical line. Any stereo separation is visible as a deviation from this line, creating a Lissajous figure. If the straight (or deviation from it) but horizontal line appears this indicates that the left and right channels are out of phase.

The filter accepts the following options:

mode, m

Set the vectorscope mode.

Available values are:

‘lissajous’

Lissajous rotated by 45 degrees.

‘lissajous_xy’

Same as above but not rotated.

‘polar’

Shape resembling half of circle.

Default value is ‘lissajous’.

size, s

Set the video size for the output. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual. Default value is 400x400.

rate, r

Set the output frame rate. Default value is 25.

rc

gc

bc

ac

Specify the red, green, blue and alpha contrast. Default values are 40, 160, 80 and 255. Allowed range is [0, 255].

rf

gf

bf

af

Specify the red, green, blue and alpha fade. Default values are 15, 10, 5 and 5. Allowed range is [0, 255].

zoom

Set the zoom factor. Default value is 1. Allowed range is [0, 10]. Values lower than 1 will auto adjust zoom factor to maximal possible value.

draw

Set the vectorscope drawing mode.

Available values are:

‘dot’

Draw dot for each sample.

‘line’

Draw line between previous and current sample.

‘aaline’

Draw anti-aliased line between previous and current sample.

Default value is ‘dot’.

scale

Specify amplitude scale of audio samples.

Available values are:

‘lin’

Linear.

‘sqrt’

Square root.

‘cbrt’

Cubic root.

‘log’

Logarithmic.

swap

Swap left channel axis with right channel axis.

mirror

Mirror axis.

‘none’

No mirror.

‘x’

Mirror only x axis.

‘y’

Mirror only y axis.

‘xy’

Mirror both axis.

#### 48.7.1 Examples# TOC

- Complete example using ffplay:

```
ffplay -f lavfi 'amovie=input.mp3, asplit [a][out1];
             [a] avectorscope=zoom=1.3:rc=2:gc=200:bc=10:rf=1:gf=8:bf=7 [out0]'

```

#### 48.7.2 Commands# TOC

This filter supports the all above options as commands except options size and rate.

### 48.8 bench, abench# TOC

Benchmark part of a filtergraph.

The filter accepts the following options:

action

Start or stop a timer.

Available values are:

‘start’

Get the current time, set it as frame metadata (using the key lavfi.bench.start_time), and forward the frame to the next filter.

‘stop’

Get the current time and fetch the lavfi.bench.start_time metadata from the input frame metadata to get the time difference. Time difference, average, maximum and minimum time (respectively t, avg, max and min) are then printed. The timestamps are expressed in seconds.

#### 48.8.1 Examples# TOC

- Benchmark selectivecolor filter:

```
bench=start,selectivecolor=reds=-.2 .12 -.49,bench=stop

```

### 48.9 concat# TOC

Concatenate audio and video streams, joining them together one after the other.

The filter works on segments of synchronized video and audio streams. All segments must have the same number of streams of each type, and that will also be the number of streams at output.

The filter accepts the following options:

n

Set the number of segments. Default is 2.

v

Set the number of output video streams, that is also the number of video streams in each segment. Default is 1.

a

Set the number of output audio streams, that is also the number of audio streams in each segment. Default is 0.

unsafe

Activate unsafe mode: do not fail if segments have a different format.

The filter has v+a outputs: first v video outputs, then a audio outputs.

There are nx(v+a) inputs: first the inputs for the first segment, in the same order as the outputs, then the inputs for the second segment, etc.

Related streams do not always have exactly the same duration, for various reasons including codec frame size or sloppy authoring. For that reason, related synchronized streams (e.g. a video and its audio track) should be concatenated at once. The concat filter will use the duration of the longest stream in each segment (except the last one), and if necessary pad shorter audio streams with silence.

For this filter to work correctly, all segments must start at timestamp 0.

All corresponding streams must have the same parameters in all segments; the filtering system will automatically select a common pixel format for video streams, and a common sample format, sample rate and channel layout for audio streams, but other settings, such as resolution, must be converted explicitly by the user.

Different frame rates are acceptable but will result in variable frame rate at output; be sure to configure the output file to handle it.

#### 48.9.1 Examples# TOC

- Concatenate an opening, an episode and an ending, all in bilingual version (video in stream 0, audio in streams 1 and 2):

```
ffmpeg -i opening.mkv -i episode.mkv -i ending.mkv -filter_complex \
  '[0:0] [0:1] [0:2] [1:0] [1:1] [1:2] [2:0] [2:1] [2:2]
   concat=n=3:v=1:a=2 [v] [a1] [a2]' \
  -map '[v]' -map '[a1]' -map '[a2]' output.mkv

```

- Concatenate two parts, handling audio and video separately, using the (a)movie sources, and adjusting the resolution:

```
movie=part1.mp4, scale=512:288 [v1] ; amovie=part1.mp4 [a1] ;
movie=part2.mp4, scale=512:288 [v2] ; amovie=part2.mp4 [a2] ;
[v1] [v2] concat [outv] ; [a1] [a2] concat=v=0:a=1 [outa]

```

Note that a desync will happen at the stitch if the audio and video streams do not have exactly the same duration in the first file.

#### 48.9.2 Commands# TOC

This filter supports the following commands:

next

Close the current segment and step to the next one

### 48.10 ebur128# TOC

EBU R128 scanner filter. This filter takes an audio stream and analyzes its loudness level. By default, it logs a message at a frequency of 10Hz with the Momentary loudness (identified by M), Short-term loudness (S), Integrated loudness (I) and Loudness Range (LRA).

The filter can only analyze streams which have sample format is double-precision floating point. The input stream will be converted to this specification, if needed. Users may need to insert aformat and/or aresample filters after this filter to obtain the original parameters.

The filter also has a video output (see the video option) with a real time graph to observe the loudness evolution. The graphic contains the logged message mentioned above, so it is not printed anymore when this option is set, unless the verbose logging is set. The main graphing area contains the short-term loudness (3 seconds of analysis), and the gauge on the right is for the momentary loudness (400 milliseconds), but can optionally be configured to instead display short-term loudness (see gauge).

The green area marks a +/- 1LU target range around the target loudness (-23LUFS by default, unless modified through target).

More information about the Loudness Recommendation EBU R128 on http://tech.ebu.ch/loudness.

The filter accepts the following options:

video

Activate the video output. The audio stream is passed unchanged whether this option is set or no. The video stream will be the first output stream if activated. Default is 0.

size

Set the video size. This option is for video only. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual. Default and minimum resolution is 640x480.

meter

Set the EBU scale meter. Default is 9. Common values are 9 and 18, respectively for EBU scale meter +9 and EBU scale meter +18. Any other integer value between this range is allowed.

metadata

Set metadata injection. If set to 1, the audio input will be segmented into 100ms output frames, each of them containing various loudness information in metadata. All the metadata keys are prefixed with lavfi.r128..

Default is 0.

framelog

Force the frame logging level.

Available values are:

‘quiet’

logging disabled

‘info’

information logging level

‘verbose’

verbose logging level

By default, the logging level is set to info. If the video or the metadata options are set, it switches to verbose.

peak

Set peak mode(s).

Available modes can be cumulated (the option is a flag type). Possible values are:

‘none’

Disable any peak mode (default).

‘sample’

Enable sample-peak mode.

Simple peak mode looking for the higher sample value. It logs a message for sample-peak (identified by SPK).

‘true’

Enable true-peak mode.

If enabled, the peak lookup is done on an over-sampled version of the input stream for better peak accuracy. It logs a message for true-peak. (identified by TPK) and true-peak per frame (identified by FTPK). This mode requires a build with libswresample.

dualmono

Treat mono input files as "dual mono". If a mono file is intended for playback on a stereo system, its EBU R128 measurement will be perceptually incorrect. If set to true, this option will compensate for this effect. Multi-channel input files are not affected by this option.

panlaw

Set a specific pan law to be used for the measurement of dual mono files. This parameter is optional, and has a default value of -3.01dB.

target

Set a specific target level (in LUFS) used as relative zero in the visualization. This parameter is optional and has a default value of -23LUFS as specified by EBU R128. However, material published online may prefer a level of -16LUFS (e.g. for use with podcasts or video platforms).

gauge

Set the value displayed by the gauge. Valid values are momentary and s shortterm. By default the momentary value will be used, but in certain scenarios it may be more useful to observe the short term value instead (e.g. live mixing).

scale

Sets the display scale for the loudness. Valid parameters are absolute (in LUFS) or relative (LU) relative to the target. This only affects the video output, not the summary or continuous log output.

integrated

Read-only exported value for measured integrated loudness, in LUFS.

range

Read-only exported value for measured loudness range, in LU.

lra_low

Read-only exported value for measured LRA low, in LUFS.

lra_high

Read-only exported value for measured LRA high, in LUFS.

sample_peak

Read-only exported value for measured sample peak, in dBFS.

true_peak

Read-only exported value for measured true peak, in dBFS.

#### 48.10.1 Examples# TOC

- Real-time graph using ffplay, with a EBU scale meter +18:

```
ffplay -f lavfi -i "amovie=input.mp3,ebur128=video=1:meter=18 [out0][out1]"

```

- Run an analysis with ffmpeg:

```
ffmpeg -nostats -i input.mp3 -filter_complex ebur128 -f null -

```

### 48.11 interleave, ainterleave# TOC

Temporally interleave frames from several inputs.

interleave works with video inputs, ainterleave with audio.

These filters read frames from several inputs and send the oldest queued frame to the output.

Input streams must have well defined, monotonically increasing frame timestamp values.

In order to submit one frame to output, these filters need to enqueue at least one frame for each input, so they cannot work in case one input is not yet terminated and will not receive incoming frames.

For example consider the case when one input is a select filter which always drops input frames. The interleave filter will keep reading from that input, but it will never be able to send new frames to output until the input sends an end-of-stream signal.

Also, depending on inputs synchronization, the filters will drop frames in case one input receives more frames than the other ones, and the queue is already filled.

These filters accept the following options:

nb_inputs, n

Set the number of different inputs, it is 2 by default.

duration

How to determine the end-of-stream.

longest

The duration of the longest input. (default)

shortest

The duration of the shortest input.

first

The duration of the first input.

#### 48.11.1 Examples# TOC

- Interleave frames belonging to different streams using ffmpeg:

```
ffmpeg -i bambi.avi -i pr0n.mkv -filter_complex "[0:v][1:v] interleave" out.avi

```

- Add flickering blur effect:

```
select='if(gt(random(0), 0.2), 1, 2)':n=2 [tmp], boxblur=2:2, [tmp] interleave

```

### 48.12 latency, alatency# TOC

Measure filtering latency.

Report previous filter filtering latency, delay in number of audio samples for audio filters or number of video frames for video filters.

On end of input stream, filter will report min and max measured latency for previous running filter in filtergraph.

### 48.13 metadata, ametadata# TOC

Manipulate frame metadata.

This filter accepts the following options:

mode

Set mode of operation of the filter.

Can be one of the following:

‘select’

If both value and key is set, select frames which have such metadata. If only key is set, select every frame that has such key in metadata.

‘add’

Add new metadata key and value. If key is already available do nothing.

‘modify’

Modify value of already present key.

‘delete’

If value is set, delete only keys that have such value. Otherwise, delete key. If key is not set, delete all metadata values in the frame.

‘print’

Print key and its value if metadata was found. If key is not set print all metadata values available in frame.

key

Set key used with all modes. Must be set for all modes except print and delete.

value

Set metadata value which will be used. This option is mandatory for modify and add mode.

function

Which function to use when comparing metadata value and value.

Can be one of following:

‘same_str’

Values are interpreted as strings, returns true if metadata value is same as value.

‘starts_with’

Values are interpreted as strings, returns true if metadata value starts with the value option string.

‘less’

Values are interpreted as floats, returns true if metadata value is less than value.

‘equal’

Values are interpreted as floats, returns true if value is equal with metadata value.

‘greater’

Values are interpreted as floats, returns true if metadata value is greater than value.

‘expr’

Values are interpreted as floats, returns true if expression from option expr evaluates to true.

‘ends_with’

Values are interpreted as strings, returns true if metadata value ends with the value option string.

expr

Set expression which is used when function is set to expr. The expression is evaluated through the eval API and can contain the following constants:

VALUE1, FRAMEVAL

Float representation of value from metadata key.

VALUE2, USERVAL

Float representation of value as supplied by user in value option.

file

If specified in print mode, output is written to the named file. Instead of plain filename any writable url can be specified. Filename “-” is a shorthand for standard output. If file option is not set, output is written to the log with AV_LOG_INFO loglevel.

direct

Reduces buffering in print mode when output is written to a URL set using file.

#### 48.13.1 Examples# TOC

- Print all metadata values for frames with key lavfi.signalstats.YDIF with values between 0 and 1.

```
signalstats,metadata=print:key=lavfi.signalstats.YDIF:value=0:function=expr:expr='between(VALUE1,0,1)'

```

- Print silencedetect output to file metadata.txt.

```
silencedetect,ametadata=mode=print:file=metadata.txt

```

- Direct all metadata to a pipe with file descriptor 4.

```
metadata=mode=print:file='pipe\:4'

```

### 48.14 perms, aperms# TOC

Set read/write permissions for the output frames.

These filters are mainly aimed at developers to test direct path in the following filter in the filtergraph.

The filters accept the following options:

mode

Select the permissions mode.

It accepts the following values:

‘none’

Do nothing. This is the default.

‘ro’

Set all the output frames read-only.

‘rw’

Set all the output frames directly writable.

‘toggle’

Make the frame read-only if writable, and writable if read-only.

‘random’

Set each output frame read-only or writable randomly.

seed

Set the seed for the random mode, must be an integer included between 0 and UINT32_MAX. If not specified, or if explicitly set to -1, the filter will try to use a good random seed on a best effort basis.

Note: in case of auto-inserted filter between the permission filter and the following one, the permission might not be received as expected in that following filter. Inserting a format or aformat filter before the perms/aperms filter can avoid this problem.

### 48.15 realtime, arealtime# TOC

Slow down filtering to match real time approximately.

These filters will pause the filtering for a variable amount of time to match the output rate with the input timestamps. They are similar to the re option to ffmpeg.

They accept the following options:

limit

Time limit for the pauses. Any pause longer than that will be considered a timestamp discontinuity and reset the timer. Default is 2 seconds.

speed

Speed factor for processing. The value must be a float larger than zero. Values larger than 1.0 will result in faster than realtime processing, smaller will slow processing down. The limit is automatically adapted accordingly. Default is 1.0.

A processing speed faster than what is possible without these filters cannot be achieved.

#### 48.15.1 Commands# TOC

Both filters supports the all above options as commands.

### 48.16 segment, asegment# TOC

Split single input stream into multiple streams.

This filter does opposite of concat filters.

segment works on video frames, asegment on audio samples.

This filter accepts the following options:

timestamps

Timestamps of output segments separated by ’|’. The first segment will run from the beginning of the input stream. The last segment will run until the end of the input stream

frames, samples

Exact frame/sample count to split the segments.

In all cases, prefixing an each segment with ’+’ will make it relative to the previous segment.

#### 48.16.1 Examples# TOC

- Split input audio stream into three output audio streams, starting at start of input audio stream and storing that in 1st output audio stream, then following at 60th second and storing than in 2nd output audio stream, and last after 150th second of input audio stream store in 3rd output audio stream:

```
asegment=timestamps="60|150"

```

### 48.17 select, aselect# TOC

Select frames to pass in output.

This filter accepts the following options:

expr, e

Set expression, which is evaluated for each input frame.

If the expression is evaluated to zero, the frame is discarded.

If the evaluation result is negative or NaN, the frame is sent to the first output; otherwise it is sent to the output with index ceil(val)-1, assuming that the input index starts from 0.

For example a value of 1.2 corresponds to the output with index ceil(1.2)-1 = 2-1 = 1, that is the second output.

outputs, n

Set the number of outputs. The output to which to send the selected frame is based on the result of the evaluation. Default value is 1.

The expression can contain the following constants:

n

The (sequential) number of the filtered frame, starting from 0.

selected_n

The (sequential) number of the selected frame, starting from 0.

prev_selected_n

The sequential number of the last selected frame. It’s NAN if undefined.

TB

The timebase of the input timestamps.

pts

The PTS (Presentation TimeStamp) of the filtered frame, expressed in TB units. It’s NAN if undefined.

t

The PTS of the filtered frame, expressed in seconds. It’s NAN if undefined.

prev_pts

The PTS of the previously filtered frame. It’s NAN if undefined.

prev_selected_pts

The PTS of the last previously filtered frame. It’s NAN if undefined.

prev_selected_t

The PTS of the last previously selected frame, expressed in seconds. It’s NAN if undefined.

start_pts

The first PTS in the stream which is not NAN. It remains NAN if not found.

start_t

The first PTS, in seconds, in the stream which is not NAN. It remains NAN if not found.

pict_type (video only)

The type of the filtered frame. It can assume one of the following values:

I

P

B

S

SI

SP

BI

interlace_type (video only)

The frame interlace type. It can assume one of the following values:

PROGRESSIVE

The frame is progressive (not interlaced).

TOPFIRST

The frame is top-field-first.

BOTTOMFIRST

The frame is bottom-field-first.

consumed_sample_n (audio only)

the number of selected samples before the current frame

samples_n (audio only)

the number of samples in the current frame

sample_rate (audio only)

the input sample rate

key

This is 1 if the filtered frame is a key-frame, 0 otherwise.

pos

the position in the file of the filtered frame, -1 if the information is not available (e.g. for synthetic video); deprecated, do not use

scene (video only)

value between 0 and 1 to indicate a new scene; a low value reflects a low probability for the current frame to introduce a new scene, while a higher value means the current frame is more likely to be one (see the example below)

concatdec_select

The concat demuxer can select only part of a concat input file by setting an inpoint and an outpoint, but the output packets may not be entirely contained in the selected interval. By using this variable, it is possible to skip frames generated by the concat demuxer which are not exactly contained in the selected interval.

This works by comparing the frame pts against the lavf.concat.start_time and the lavf.concat.duration packet metadata values which are also present in the decoded frames.

The concatdec_select variable is -1 if the frame pts is at least start_time and either the duration metadata is missing or the frame pts is less than start_time + duration, 0 otherwise, and NaN if the start_time metadata is missing.

That basically means that an input frame is selected if its pts is within the interval set by the concat demuxer.

iw (video only)

Represents the width of the input video frame.

ih (video only)

Represents the height of the input video frame.

view (video only)

View ID for multi-view video.

The default value of the select expression is "1".

#### 48.17.1 Examples# TOC

- Select all frames in input:

```
select

```

The example above is the same as:

```
select=1

```

- Skip all frames:

```
select=0

```

- Select only I-frames:

```
select='eq(pict_type\,I)'

```

- Select one frame every 100:

```
select='not(mod(n\,100))'

```

- Select only frames contained in the 10-20 time interval:

```
select=between(t\,10\,20)

```

- Select only I-frames contained in the 10-20 time interval:

```
select=between(t\,10\,20)*eq(pict_type\,I)

```

- Select frames with a minimum distance of 10 seconds:

```
select='isnan(prev_selected_t)+gte(t-prev_selected_t\,10)'

```

- Use aselect to select only audio frames with samples number > 100:

```
aselect='gt(samples_n\,100)'

```

- Create a mosaic of the first scenes:

```
ffmpeg -i video.avi -vf select='gt(scene\,0.4)',scale=160:120,tile -frames:v 1 preview.png

```

Comparing scene against a value between 0.3 and 0.5 is generally a sane choice.

- Send even and odd frames to separate outputs, and compose them:

```
select=n=2:e='mod(n, 2)+1' [odd][even]; [odd] pad=h=2*ih [tmp]; [tmp][even] overlay=y=h

```

- Select useful frames from an ffconcat file which is using inpoints and outpoints but where the source files are not intra frame only.

```
ffmpeg -copyts -segment_time_metadata 1 -i input.ffconcat -fps_mode passthrough -vf select=concatdec_select -af aselect=concatdec_select output.avi

```

### 48.18 sendcmd, asendcmd# TOC

Send commands to filters in the filtergraph.

These filters read commands to be sent to other filters in the filtergraph.

sendcmd must be inserted between two video filters, asendcmd must be inserted between two audio filters, but apart from that they act the same way.

The specification of commands can be provided in the filter arguments with the commands option, or in a file specified by the filename option.

These filters accept the following options:

commands, c

Set the commands to be read and sent to the other filters.

filename, f

Set the filename of the commands to be read and sent to the other filters.

#### 48.18.1 Commands syntax# TOC

A commands description consists of a sequence of interval specifications, comprising a list of commands to be executed when a particular event related to that interval occurs. The occurring event is typically the current frame time entering or leaving a given time interval.

An interval is specified by the following syntax:

```
START[-END] COMMANDS;

```

The time interval is specified by the START and END times. END is optional and defaults to the maximum time.

The current frame time is considered within the specified interval if it is included in the interval [START, END), that is when the time is greater or equal to START and is lesser than END.

COMMANDS consists of a sequence of one or more command specifications, separated by ",", relating to that interval. The syntax of a command specification is given by:

```
[FLAGS] TARGET COMMAND ARG

```

FLAGS is optional and specifies the type of events relating to the time interval which enable sending the specified command, and must be a non-null sequence of identifier flags separated by "+" or "|" and enclosed between "[" and "]".

The following flags are recognized:

enter

The command is sent when the current frame timestamp enters the specified interval. In other words, the command is sent when the previous frame timestamp was not in the given interval, and the current is.

leave

The command is sent when the current frame timestamp leaves the specified interval. In other words, the command is sent when the previous frame timestamp was in the given interval, and the current is not.

expr

The command ARG is interpreted as expression and result of expression is passed as ARG.

The expression is evaluated through the eval API and can contain the following constants:

POS

Original position in the file of the frame, or undefined if undefined for the current frame. Deprecated, do not use.

PTS

The presentation timestamp in input.

N

The count of the input frame for video or audio, starting from 0.

T

The time in seconds of the current frame.

TS

The start time in seconds of the current command interval.

TE

The end time in seconds of the current command interval.

TI

The interpolated time of the current command interval, TI = (T - TS) / (TE - TS).

W

The video frame width.

H

The video frame height.

If FLAGS is not specified, a default value of [enter] is assumed.

TARGET specifies the target of the command, usually the name of the filter class or a specific filter instance name.

COMMAND specifies the name of the command for the target filter.

ARG is optional and specifies the optional list of argument for the given COMMAND.

Between one interval specification and another, whitespaces, or sequences of characters starting with # until the end of line, are ignored and can be used to annotate comments.

A simplified BNF description of the commands specification syntax follows:

```
COMMAND_FLAG  ::= "enter" | "leave"
COMMAND_FLAGS ::= COMMAND_FLAG [(+|"|")COMMAND_FLAG]
COMMAND       ::= ["[" COMMAND_FLAGS "]"] TARGET COMMAND [ARG]
COMMANDS      ::= COMMAND [,COMMANDS]
INTERVAL      ::= START[-END] COMMANDS
INTERVALS     ::= INTERVAL[;INTERVALS]

```

#### 48.18.2 Examples# TOC

- Specify audio tempo change at second 4:

```
asendcmd=c='4.0 atempo tempo 1.5',atempo

```

- Target a specific filter instance:

```
asendcmd=c='4.0 atempo@my tempo 1.5',atempo@my

```

- Specify a list of drawtext and hue commands in a file.

```
# show text in the interval 5-10
5.0-10.0 [enter] drawtext reinit 'fontfile=FreeSerif.ttf:text=hello world',
         [leave] drawtext reinit 'fontfile=FreeSerif.ttf:text=';

# desaturate the image in the interval 15-20
15.0-20.0 [enter] hue s 0,
          [enter] drawtext reinit 'fontfile=FreeSerif.ttf:text=nocolor',
          [leave] hue s 1,
          [leave] drawtext reinit 'fontfile=FreeSerif.ttf:text=color';

# apply an exponential saturation fade-out effect, starting from time 25
25 [enter] hue s exp(25-t)

```

A filtergraph allowing to read and process the above command list stored in a file test.cmd, can be specified with:

```
sendcmd=f=test.cmd,drawtext=fontfile=FreeSerif.ttf:text='',hue

```

### 48.19 setpts, asetpts# TOC

Change the PTS (presentation timestamp) of the input frames.

setpts works on video frames, asetpts on audio frames.

This filter accepts the following options:

expr

The expression which is evaluated for each frame to construct its timestamp.

strip_fps (video only)

Boolean option which determines if the original framerate and frame duration metadata is unset. If set to true, be advised that a sane frame rate should be explicitly specified if output is sent to a constant frame rate muxer. Default is false.

The expression is evaluated through the eval API and can contain the following constants:

FRAME_RATE, FR

frame rate, only defined for constant frame-rate video

PTS

The presentation timestamp in input

N

The count of the input frame for video or the number of consumed samples, not including the current frame for audio, starting from 0.

NB_CONSUMED_SAMPLES

The number of consumed samples, not including the current frame (only audio)

NB_SAMPLES, S

The number of samples in the current frame (only audio)

SAMPLE_RATE, SR

The audio sample rate.

STARTPTS

The PTS of the first frame.

STARTT

the time in seconds of the first frame

INTERLACED

State whether the current frame is interlaced.

T

the time in seconds of the current frame

POS

original position in the file of the frame, or undefined if undefined for the current frame; deprecated, do not use

PREV_INPTS

The previous input PTS.

PREV_INT

previous input time in seconds

PREV_OUTPTS

The previous output PTS.

PREV_OUTT

previous output time in seconds

RTCTIME

The wallclock (RTC) time in microseconds. This is deprecated, use time(0) instead.

RTCSTART

The wallclock (RTC) time at the start of the movie in microseconds.

TB

The timebase of the input timestamps.

T_CHANGE

Time of the first frame after command was applied or time of the first frame if no commands.

#### 48.19.1 Examples# TOC

- Start counting PTS from zero

```
setpts=PTS-STARTPTS

```

- Apply fast motion effect:

```
setpts=0.5*PTS

```

- Apply slow motion effect:

```
setpts=2.0*PTS

```

- Set fixed rate of 25 frames per second:

```
setpts=N/(25*TB)

```

- Apply a random jitter effect of +/-100 TB units:

```
setpts=PTS+randomi(0, -100\,100)

```

- Set fixed rate 25 fps with some jitter:

```
setpts='1/(25*TB) * (N + 0.05 * sin(N*2*PI/25))'

```

- Apply an offset of 10 seconds to the input PTS:

```
setpts=PTS+10/TB

```

- Generate timestamps from a "live source" and rebase onto the current timebase:

```
setpts='(RTCTIME - RTCSTART) / (TB * 1000000)'

```

- Generate timestamps by counting samples:

```
asetpts=N/SR/TB

```

#### 48.19.2 Commands# TOC

Both filters support all above options as commands.

### 48.20 setrange# TOC

Force color range for the output video frame.

The setrange filter marks the color range property for the output frames. It does not change the input frame, but only sets the corresponding property, which affects how the frame is treated by following filters.

The filter accepts the following options:

range

Available values are:

‘auto’

Keep the same color range property.

‘unspecified, unknown’

Set the color range as unspecified.

‘limited, tv, mpeg’

Set the color range as limited.

‘full, pc, jpeg’

Set the color range as full.

### 48.21 settb, asettb# TOC

Set the timebase to use for the output frames timestamps. It is mainly useful for testing timebase configuration.

It accepts the following parameters:

expr, tb

The expression which is evaluated into the output timebase.

The value for tb is an arithmetic expression representing a rational. The expression can contain the constants "AVTB" (the default timebase), "intb" (the input timebase) and "sr" (the sample rate, audio only). Default value is "intb".

#### 48.21.1 Examples# TOC

- Set the timebase to 1/25:

```
settb=expr=1/25

```

- Set the timebase to 1/10:

```
settb=expr=0.1

```

- Set the timebase to 1001/1000:

```
settb=1+0.001

```

- Set the timebase to 2*intb:

```
settb=2*intb

```

- Set the default timebase value:

```
settb=AVTB

```

### 48.22 showcqt# TOC

Convert input audio to a video output representing frequency spectrum logarithmically using Brown-Puckette constant Q transform algorithm with direct frequency domain coefficient calculation (but the transform itself is not really constant Q, instead the Q factor is actually variable/clamped), with musical tone scale, from E0 to D#10.

The filter accepts the following options:

size, s

Specify the video size for the output. It must be even. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual. Default value is 1920x1080.

fps, rate, r

Set the output frame rate. Default value is 25.

bar_h

Set the bargraph height. It must be even. Default value is -1 which computes the bargraph height automatically.

axis_h

Set the axis height. It must be even. Default value is -1 which computes the axis height automatically.

sono_h

Set the sonogram height. It must be even. Default value is -1 which computes the sonogram height automatically.

fullhd

Set the fullhd resolution. This option is deprecated, use size, s instead. Default value is 1.

sono_v, volume

Specify the sonogram volume expression. It can contain variables:

bar_v

the bar_v evaluated expression

frequency, freq, f

the frequency where it is evaluated

timeclamp, tc

the value of timeclamp option

and functions:

a_weighting(f)

A-weighting of equal loudness

b_weighting(f)

B-weighting of equal loudness

c_weighting(f)

C-weighting of equal loudness.

Default value is 16.

bar_v, volume2

Specify the bargraph volume expression. It can contain variables:

sono_v

the sono_v evaluated expression

frequency, freq, f

the frequency where it is evaluated

timeclamp, tc

the value of timeclamp option

and functions:

a_weighting(f)

A-weighting of equal loudness

b_weighting(f)

B-weighting of equal loudness

c_weighting(f)

C-weighting of equal loudness.

Default value is sono_v.

sono_g, gamma

Specify the sonogram gamma. Lower gamma makes the spectrum more contrast, higher gamma makes the spectrum having more range. Default value is 3. Acceptable range is [1, 7].

bar_g, gamma2

Specify the bargraph gamma. Default value is 1. Acceptable range is [1, 7].

bar_t

Specify the bargraph transparency level. Lower value makes the bargraph sharper. Default value is 1. Acceptable range is [0, 1].

timeclamp, tc

Specify the transform timeclamp. At low frequency, there is trade-off between accuracy in time domain and frequency domain. If timeclamp is lower, event in time domain is represented more accurately (such as fast bass drum), otherwise event in frequency domain is represented more accurately (such as bass guitar). Acceptable range is [0.002, 1]. Default value is 0.17.

attack

Set attack time in seconds. The default is 0 (disabled). Otherwise, it limits future samples by applying asymmetric windowing in time domain, useful when low latency is required. Accepted range is [0, 1].

basefreq

Specify the transform base frequency. Default value is 20.01523126408007475, which is frequency 50 cents below E0. Acceptable range is [10, 100000].

endfreq

Specify the transform end frequency. Default value is 20495.59681441799654, which is frequency 50 cents above D#10. Acceptable range is [10, 100000].

coeffclamp

This option is deprecated and ignored.

tlength

Specify the transform length in time domain. Use this option to control accuracy trade-off between time domain and frequency domain at every frequency sample. It can contain variables:

frequency, freq, f

the frequency where it is evaluated

timeclamp, tc

the value of timeclamp option.

Default value is 384*tc/(384+tc*f).

count

Specify the transform count for every video frame. Default value is 6. Acceptable range is [1, 30].

fcount

Specify the transform count for every single pixel. Default value is 0, which makes it computed automatically. Acceptable range is [0, 10].

fontfile

Specify font file for use with freetype to draw the axis. If not specified, use embedded font. Note that drawing with font file or embedded font is not implemented with custom basefreq and endfreq, use axisfile option instead.

font

Specify fontconfig pattern. This has lower priority than fontfile. The : in the pattern may be replaced by | to avoid unnecessary escaping.

fontcolor

Specify font color expression. This is arithmetic expression that should return integer value 0xRRGGBB. It can contain variables:

frequency, freq, f

the frequency where it is evaluated

timeclamp, tc

the value of timeclamp option

and functions:

midi(f)

midi number of frequency f, some midi numbers: E0(16), C1(24), C2(36), A4(69)

r(x), g(x), b(x)

red, green, and blue value of intensity x.

Default value is st(0, (midi(f)-59.5)/12); st(1, if(between(ld(0),0,1), 0.5-0.5*cos(2*PI*ld(0)), 0)); r(1-ld(1)) + b(ld(1)).

axisfile

Specify image file to draw the axis. This option override fontfile and fontcolor option.

axis, text

Enable/disable drawing text to the axis. If it is set to 0, drawing to the axis is disabled, ignoring fontfile and axisfile option. Default value is 1.

csp

Set colorspace. The accepted values are:

‘unspecified’

Unspecified (default)

‘bt709’

BT.709

‘fcc’

FCC

‘bt470bg’

BT.470BG or BT.601-6 625

‘smpte170m’

SMPTE-170M or BT.601-6 525

‘smpte240m’

SMPTE-240M

‘bt2020ncl’

BT.2020 with non-constant luminance

cscheme

Set spectrogram color scheme. This is list of floating point values with format left_r|left_g|left_b|right_r|right_g|right_b. The default is 1|0.5|0|0|0.5|1.

#### 48.22.1 Examples# TOC

- Playing audio while showing the spectrum:

```
ffplay -f lavfi 'amovie=a.mp3, asplit [a][out1]; [a] showcqt [out0]'

```

- Same as above, but with frame rate 30 fps:

```
ffplay -f lavfi 'amovie=a.mp3, asplit [a][out1]; [a] showcqt=fps=30:count=5 [out0]'

```

- Playing at 1280x720:

```
ffplay -f lavfi 'amovie=a.mp3, asplit [a][out1]; [a] showcqt=s=1280x720:count=4 [out0]'

```

- Disable sonogram display:

```
sono_h=0

```

- A1 and its harmonics: A1, A2, (near)E3, A3:

```
ffplay -f lavfi 'aevalsrc=0.1*sin(2*PI*55*t)+0.1*sin(4*PI*55*t)+0.1*sin(6*PI*55*t)+0.1*sin(8*PI*55*t),
                 asplit[a][out1]; [a] showcqt [out0]'

```

- Same as above, but with more accuracy in frequency domain:

```
ffplay -f lavfi 'aevalsrc=0.1*sin(2*PI*55*t)+0.1*sin(4*PI*55*t)+0.1*sin(6*PI*55*t)+0.1*sin(8*PI*55*t),
                 asplit[a][out1]; [a] showcqt=timeclamp=0.5 [out0]'

```

- Custom volume:

```
bar_v=10:sono_v=bar_v*a_weighting(f)

```

- Custom gamma, now spectrum is linear to the amplitude.

```
bar_g=2:sono_g=2

```

- Custom tlength equation:

```
tc=0.33:tlength='st(0,0.17); 384*tc / (384 / ld(0) + tc*f /(1-ld(0))) + 384*tc / (tc*f / ld(0) + 384 /(1-ld(0)))'

```

- Custom fontcolor and fontfile, C-note is colored green, others are colored blue:

```
fontcolor='if(mod(floor(midi(f)+0.5),12), 0x0000FF, g(1))':fontfile=myfont.ttf

```

- Custom font using fontconfig:

```
font='Courier New,Monospace,mono|bold'

```

- Custom frequency range with custom axis using image file:

```
axisfile=myaxis.png:basefreq=40:endfreq=10000

```

### 48.23 showcwt# TOC

Convert input audio to video output representing frequency spectrum using Continuous Wavelet Transform and Morlet wavelet.

The filter accepts the following options:

size, s

Specify the video size for the output. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual. Default value is 640x512.

rate, r

Set the output frame rate. Default value is 25.

scale

Set the frequency scale used. Allowed values are:

linear

log

bark

mel

erbs

sqrt

cbrt

qdrt

fm

Default value is linear.

iscale

Set the intensity scale used. Allowed values are:

linear

log

sqrt

cbrt

qdrt

Default value is log.

min

Set the minimum frequency that will be used in output. Default is 20 Hz.

max

Set the maximum frequency that will be used in output. Default is 20000 Hz. The real frequency upper limit depends on input audio’s sample rate and such will be enforced on this value when it is set to value greater than Nyquist frequency.

imin

Set the minimum intensity that will be used in output.

imax

Set the maximum intensity that will be used in output.

logb

Set the logarithmic basis for brightness strength when mapping calculated magnitude values to pixel values. Allowed range is from 0 to 1. Default value is 0.0001.

deviation

Set the frequency deviation. Lower values than 1 are more frequency oriented, while higher values than 1 are more time oriented. Allowed range is from 0 to 10. Default value is 1.

pps

Set the number of pixel output per each second in one row. Allowed range is from 1 to 1024. Default value is 64.

mode

Set the output visual mode. Allowed values are:

magnitude

Show magnitude.

phase

Show only phase.

magphase

Show combination of magnitude and phase. Magnitude is mapped to brightness and phase to color.

channel

Show unique color per channel magnitude.

stereo

Show unique color per stereo difference.

Default value is magnitude.

slide

Set the output slide method. Allowed values are:

replace

scroll

frame

direction

Set the direction method for output slide method. Allowed values are:

lr

Direction from left to right.

rl

Direction from right to left.

ud

Direction from up to down.

du

Direction from down to up.

bar

Set the ratio of bargraph display to display size. Default is 0.

rotation

Set color rotation, must be in [-1.0, 1.0] range. Default value is 0.

### 48.24 showfreqs# TOC

Convert input audio to video output representing the audio power spectrum. Audio amplitude is on Y-axis while frequency is on X-axis.

The filter accepts the following options:

size, s

Specify size of video. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual. Default is 1024x512.

rate, r

Set video rate. Default is 25.

mode

Set display mode. This set how each frequency bin will be represented.

It accepts the following values:

‘line’

‘bar’

‘dot’

Default is bar.

ascale

Set amplitude scale.

It accepts the following values:

‘lin’

Linear scale.

‘sqrt’

Square root scale.

‘cbrt’

Cubic root scale.

‘log’

Logarithmic scale.

Default is log.

fscale

Set frequency scale.

It accepts the following values:

‘lin’

Linear scale.

‘log’

Logarithmic scale.

‘rlog’

Reverse logarithmic scale.

Default is lin.

win_size

Set window size. Allowed range is from 16 to 65536.

Default is 2048

win_func

Set windowing function.

It accepts the following values:

‘rect’

‘bartlett’

‘hanning’

‘hamming’

‘blackman’

‘welch’

‘flattop’

‘bharris’

‘bnuttall’

‘bhann’

‘sine’

‘nuttall’

‘lanczos’

‘gauss’

‘tukey’

‘dolph’

‘cauchy’

‘parzen’

‘poisson’

‘bohman’

‘kaiser’

Default is hanning.

overlap

Set window overlap. In range [0, 1]. Default is 1, which means optimal overlap for selected window function will be picked.

averaging

Set time averaging. Setting this to 0 will display current maximal peaks. Default is 1, which means time averaging is disabled.

colors

Specify list of colors separated by space or by ’|’ which will be used to draw channel frequencies. Unrecognized or missing colors will be replaced by white color.

cmode

Set channel display mode.

It accepts the following values:

‘combined’

‘separate’

Default is combined.

minamp

Set minimum amplitude used in log amplitude scaler.

data

Set data display mode.

It accepts the following values:

‘magnitude’

‘phase’

‘delay’

Default is magnitude.

channels

Set channels to use when processing audio. By default all are processed.

### 48.25 showspatial# TOC

Convert stereo input audio to a video output, representing the spatial relationship between two channels.

The filter accepts the following options:

size, s

Specify the video size for the output. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual. Default value is 512x512.

win_size

Set window size. Allowed range is from 1024 to 65536. Default size is 4096.

win_func

Set window function.

It accepts the following values:

‘rect’

‘bartlett’

‘hann’

‘hanning’

‘hamming’

‘blackman’

‘welch’

‘flattop’

‘bharris’

‘bnuttall’

‘bhann’

‘sine’

‘nuttall’

‘lanczos’

‘gauss’

‘tukey’

‘dolph’

‘cauchy’

‘parzen’

‘poisson’

‘bohman’

‘kaiser’

Default value is hann.

rate, r

Set output framerate.

### 48.26 showspectrum# TOC

Convert input audio to a video output, representing the audio frequency spectrum.

The filter accepts the following options:

size, s

Specify the video size for the output. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual. Default value is 640x512.

slide

Specify how the spectrum should slide along the window.

It accepts the following values:

‘replace’

the samples start again on the left when they reach the right

‘scroll’

the samples scroll from right to left

‘fullframe’

frames are only produced when the samples reach the right

‘rscroll’

the samples scroll from left to right

‘lreplace’

the samples start again on the right when they reach the left

Default value is replace.

mode

Specify display mode.

It accepts the following values:

‘combined’

all channels are displayed in the same row

‘separate’

all channels are displayed in separate rows

Default value is ‘combined’.

color

Specify display color mode.

It accepts the following values:

‘channel’

each channel is displayed in a separate color

‘intensity’

each channel is displayed using the same color scheme

‘rainbow’

each channel is displayed using the rainbow color scheme

‘moreland’

each channel is displayed using the moreland color scheme

‘nebulae’

each channel is displayed using the nebulae color scheme

‘fire’

each channel is displayed using the fire color scheme

‘fiery’

each channel is displayed using the fiery color scheme

‘fruit’

each channel is displayed using the fruit color scheme

‘cool’

each channel is displayed using the cool color scheme

‘magma’

each channel is displayed using the magma color scheme

‘green’

each channel is displayed using the green color scheme

‘viridis’

each channel is displayed using the viridis color scheme

‘plasma’

each channel is displayed using the plasma color scheme

‘cividis’

each channel is displayed using the cividis color scheme

‘terrain’

each channel is displayed using the terrain color scheme

Default value is ‘channel’.

scale

Specify scale used for calculating intensity color values.

It accepts the following values:

‘lin’

linear

‘sqrt’

square root, default

‘cbrt’

cubic root

‘log’

logarithmic

‘4thrt’

4th root

‘5thrt’

5th root

Default value is ‘sqrt’.

fscale

Specify frequency scale.

It accepts the following values:

‘lin’

linear

‘log’

logarithmic

Default value is ‘lin’.

saturation

Set saturation modifier for displayed colors. Negative values provide alternative color scheme. 0 is no saturation at all. Saturation must be in [-10.0, 10.0] range. Default value is 1.

win_func

Set window function.

It accepts the following values:

‘rect’

‘bartlett’

‘hann’

‘hanning’

‘hamming’

‘blackman’

‘welch’

‘flattop’

‘bharris’

‘bnuttall’

‘bhann’

‘sine’

‘nuttall’

‘lanczos’

‘gauss’

‘tukey’

‘dolph’

‘cauchy’

‘parzen’

‘poisson’

‘bohman’

‘kaiser’

Default value is hann.

orientation

Set orientation of time vs frequency axis. Can be vertical or horizontal. Default is vertical.

overlap

Set ratio of overlap window. Default value is 0. When value is 1 overlap is set to recommended size for specific window function currently used.

gain

Set scale gain for calculating intensity color values. Default value is 1.

data

Set which data to display. Can be magnitude, default or phase, or unwrapped phase: uphase.

rotation

Set color rotation, must be in [-1.0, 1.0] range. Default value is 0.

start

Set start frequency from which to display spectrogram. Default is 0.

stop

Set stop frequency to which to display spectrogram. Default is 0.

fps

Set upper frame rate limit. Default is auto, unlimited.

legend

Draw time and frequency axes and legends. Default is disabled.

drange

Set dynamic range used to calculate intensity color values. Default is 120 dBFS. Allowed range is from 10 to 200.

limit

Set upper limit of input audio samples volume in dBFS. Default is 0 dBFS. Allowed range is from -100 to 100.

opacity

Set opacity strength when using pixel format output with alpha component.

The usage is very similar to the showwaves filter; see the examples in that section.

#### 48.26.1 Examples# TOC

- Large window with logarithmic color scaling:

```
showspectrum=s=1280x480:scale=log

```

- Complete example for a colored and sliding spectrum per channel using ffplay:

```
ffplay -f lavfi 'amovie=input.mp3, asplit [a][out1];
             [a] showspectrum=mode=separate:color=intensity:slide=1:scale=cbrt [out0]'

```

### 48.27 showspectrumpic# TOC

Convert input audio to a single video frame, representing the audio frequency spectrum.

The filter accepts the following options:

size, s

Specify the video size for the output. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual. Default value is 4096x2048.

mode

Specify display mode.

It accepts the following values:

‘combined’

all channels are displayed in the same row

‘separate’

all channels are displayed in separate rows

Default value is ‘combined’.

color

Specify display color mode.

It accepts the following values:

‘channel’

each channel is displayed in a separate color

‘intensity’

each channel is displayed using the same color scheme

‘rainbow’

each channel is displayed using the rainbow color scheme

‘moreland’

each channel is displayed using the moreland color scheme

‘nebulae’

each channel is displayed using the nebulae color scheme

‘fire’

each channel is displayed using the fire color scheme

‘fiery’

each channel is displayed using the fiery color scheme

‘fruit’

each channel is displayed using the fruit color scheme

‘cool’

each channel is displayed using the cool color scheme

‘magma’

each channel is displayed using the magma color scheme

‘green’

each channel is displayed using the green color scheme

‘viridis’

each channel is displayed using the viridis color scheme

‘plasma’

each channel is displayed using the plasma color scheme

‘cividis’

each channel is displayed using the cividis color scheme

‘terrain’

each channel is displayed using the terrain color scheme

Default value is ‘intensity’.

scale

Specify scale used for calculating intensity color values.

It accepts the following values:

‘lin’

linear

‘sqrt’

square root, default

‘cbrt’

cubic root

‘log’

logarithmic

‘4thrt’

4th root

‘5thrt’

5th root

Default value is ‘log’.

fscale

Specify frequency scale.

It accepts the following values:

‘lin’

linear

‘log’

logarithmic

Default value is ‘lin’.

saturation

Set saturation modifier for displayed colors. Negative values provide alternative color scheme. 0 is no saturation at all. Saturation must be in [-10.0, 10.0] range. Default value is 1.

win_func

Set window function.

It accepts the following values:

‘rect’

‘bartlett’

‘hann’

‘hanning’

‘hamming’

‘blackman’

‘welch’

‘flattop’

‘bharris’

‘bnuttall’

‘bhann’

‘sine’

‘nuttall’

‘lanczos’

‘gauss’

‘tukey’

‘dolph’

‘cauchy’

‘parzen’

‘poisson’

‘bohman’

‘kaiser’

Default value is hann.

orientation

Set orientation of time vs frequency axis. Can be vertical or horizontal. Default is vertical.

gain

Set scale gain for calculating intensity color values. Default value is 1.

legend

Draw time and frequency axes and legends. Default is enabled.

rotation

Set color rotation, must be in [-1.0, 1.0] range. Default value is 0.

start

Set start frequency from which to display spectrogram. Default is 0.

stop

Set stop frequency to which to display spectrogram. Default is 0.

drange

Set dynamic range used to calculate intensity color values. Default is 120 dBFS. Allowed range is from 10 to 200.

limit

Set upper limit of input audio samples volume in dBFS. Default is 0 dBFS. Allowed range is from -100 to 100.

opacity

Set opacity strength when using pixel format output with alpha component.

#### 48.27.1 Examples# TOC

- Extract an audio spectrogram of a whole audio track in a 1024x1024 picture using ffmpeg:

```
ffmpeg -i audio.flac -lavfi showspectrumpic=s=1024x1024 spectrogram.png

```

### 48.28 showvolume# TOC

Convert input audio volume to a video output.

The filter accepts the following options:

rate, r

Set video rate.

b

Set border width, allowed range is [0, 5]. Default is 1.

w

Set channel width, allowed range is [80, 8192]. Default is 400.

h

Set channel height, allowed range is [1, 900]. Default is 20.

f

Set fade, allowed range is [0, 1]. Default is 0.95.

c

Set volume color expression.

The expression can use the following variables:

VOLUME

Current max volume of channel in dB.

PEAK

Current peak.

CHANNEL

Current channel number, starting from 0.

t

If set, displays channel names. Default is enabled.

v

If set, displays volume values. Default is enabled.

o

Set orientation, can be horizontal: h or vertical: v, default is h.

s

Set step size, allowed range is [0, 5]. Default is 0, which means step is disabled.

p

Set background opacity, allowed range is [0, 1]. Default is 0.

m

Set metering mode, can be peak: p or rms: r, default is p.

ds

Set display scale, can be linear: lin or log: log, default is lin.

dm

In second. If set to > 0., display a line for the max level in the previous seconds. default is disabled: 0.

dmc

The color of the max line. Use when dm option is set to > 0. default is: orange

### 48.29 showwaves# TOC

Convert input audio to a video output, representing the samples waves.

The filter accepts the following options:

size, s

Specify the video size for the output. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual. Default value is 600x240.

mode

Set display mode.

Available values are:

‘point’

Draw a point for each sample.

‘line’

Draw a vertical line for each sample.

‘p2p’

Draw a point for each sample and a line between them.

‘cline’

Draw a centered vertical line for each sample.

Default value is point.

n

Set the number of samples which are printed on the same column. A larger value will decrease the frame rate. Must be a positive integer. This option can be set only if the value for rate is not explicitly specified.

rate, r

Set the (approximate) output frame rate. This is done by setting the option n. Default value is "25".

split_channels

Set if channels should be drawn separately or overlap. Default value is 0.

colors

Set colors separated by ’|’ which are going to be used for drawing of each channel.

scale

Set amplitude scale.

Available values are:

‘lin’

Linear.

‘log’

Logarithmic.

‘sqrt’

Square root.

‘cbrt’

Cubic root.

Default is linear.

draw

Set the draw mode. This is mostly useful to set for high n.

Available values are:

‘scale’

Scale pixel values for each drawn sample.

‘full’

Draw every sample directly.

Default value is scale.

#### 48.29.1 Examples# TOC

- Output the input file audio and the corresponding video representation at the same time:

```
amovie=a.mp3,asplit[out0],showwaves[out1]

```

- Create a synthetic signal and show it with showwaves, forcing a frame rate of 30 frames per second:

```
aevalsrc=sin(1*2*PI*t)*sin(880*2*PI*t):cos(2*PI*200*t),asplit[out0],showwaves=r=30[out1]

```

### 48.30 showwavespic# TOC

Convert input audio to a single video frame, representing the samples waves.

The filter accepts the following options:

size, s

Specify the video size for the output. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual. Default value is 600x240.

split_channels

Set if channels should be drawn separately or overlap. Default value is 0.

colors

Set colors separated by ’|’ which are going to be used for drawing of each channel.

scale

Set amplitude scale.

Available values are:

‘lin’

Linear.

‘log’

Logarithmic.

‘sqrt’

Square root.

‘cbrt’

Cubic root.

Default is linear.

draw

Set the draw mode.

Available values are:

‘scale’

Scale pixel values for each drawn sample.

‘full’

Draw every sample directly.

Default value is scale.

filter

Set the filter mode.

Available values are:

‘average’

Use average samples values for each drawn sample.

‘peak’

Use peak samples values for each drawn sample.

Default value is average.

#### 48.30.1 Examples# TOC

- Extract a channel split representation of the wave form of a whole audio track in a 1024x800 picture using ffmpeg:

```
ffmpeg -i audio.flac -lavfi showwavespic=split_channels=1:s=1024x800 waveform.png

```

### 48.31 sidedata, asidedata# TOC

Delete frame side data, or select frames based on it.

This filter accepts the following options:

mode

Set mode of operation of the filter.

Can be one of the following:

‘select’

Select every frame with side data of type.

‘delete’

Delete side data of type. If type is not set, delete all side data in the frame.

type

Set side data type used with all modes. Must be set for select mode.

Possible values are:

‘PANSCAN’

‘A53_CC’

‘STEREO3D’

‘MATRIXENCODING’

‘DOWNMIX_INFO’

‘REPLAYGAIN’

‘DISPLAYMATRIX’

‘AFD’

‘MOTION_VECTORS’

‘SKIP_SAMPLES’

‘AUDIO_SERVICE_TYPE’

‘MASTERING_DISPLAY_METADATA’

‘GOP_TIMECODE’

‘SPHERICAL’

‘CONTENT_LIGHT_LEVEL’

‘ICC_PROFILE’

‘S12M_TIMECODE’

‘DYNAMIC_HDR_PLUS’

‘REGIONS_OF_INTEREST’

‘VIDEO_ENC_PARAMS’

‘SEI_UNREGISTERED’

‘FILM_GRAIN_PARAMS’

‘DETECTION_BOUNDING_BOXES’

‘DETECTION_BBOXES’

‘DOVI_RPU_BUFFER’

‘DOVI_METADATA’

‘DYNAMIC_HDR_VIVID’

‘AMBIENT_VIEWING_ENVIRONMENT’

‘VIDEO_HINT’

‘GAIN_MAP_PARAMS’

### 48.32 spectrumsynth# TOC

Synthesize audio from 2 input video spectrums, first input stream represents magnitude across time and second represents phase across time. The filter will transform from frequency domain as displayed in videos back to time domain as presented in audio output.

This filter is primarily created for reversing processed showspectrum filter outputs, but can synthesize sound from other spectrograms too. But in such case results are going to be poor if the phase data is not available, because in such cases phase data need to be recreated, usually it’s just recreated from random noise. For best results use gray only output (channel color mode in showspectrum filter) and log scale for magnitude video and lin scale for phase video. To produce phase, for 2nd video, use data option. Inputs videos should generally use fullframe slide mode as that saves resources needed for decoding video.

The filter accepts the following options:

sample_rate

Specify sample rate of output audio, the sample rate of audio from which spectrum was generated may differ.

channels

Set number of channels represented in input video spectrums.

scale

Set scale which was used when generating magnitude input spectrum. Can be lin or log. Default is log.

slide

Set slide which was used when generating inputs spectrums. Can be replace, scroll, fullframe or rscroll. Default is fullframe.

win_func

Set window function used for resynthesis.

overlap

Set window overlap. In range [0, 1]. Default is 1, which means optimal overlap for selected window function will be picked.

orientation

Set orientation of input videos. Can be vertical or horizontal. Default is vertical.

#### 48.32.1 Examples# TOC

- First create magnitude and phase videos from audio, assuming audio is stereo with 44100 sample rate, then resynthesize videos back to audio with spectrumsynth:

```
ffmpeg -i input.flac -lavfi showspectrum=mode=separate:scale=log:overlap=0.875:color=channel:slide=fullframe:data=magnitude -an -c:v rawvideo magnitude.nut
ffmpeg -i input.flac -lavfi showspectrum=mode=separate:scale=lin:overlap=0.875:color=channel:slide=fullframe:data=phase -an -c:v rawvideo phase.nut
ffmpeg -i magnitude.nut -i phase.nut -lavfi spectrumsynth=channels=2:sample_rate=44100:win_func=hann:overlap=0.875:slide=fullframe output.flac

```

### 48.33 split, asplit# TOC

Split input into several identical outputs.

asplit works with audio input, split with video.

The filter accepts a single parameter which specifies the number of outputs. If unspecified, it defaults to 2.

#### 48.33.1 Examples# TOC

- Create two separate outputs from the same input:

```
[in] split [out0][out1]

```

- To create 3 or more outputs, you need to specify the number of outputs, like in:

```
[in] asplit=3 [out0][out1][out2]

```

- Create two separate outputs from the same input, one cropped and one padded:

```
[in] split [splitout1][splitout2];
[splitout1] crop=100:100:0:0    [cropout];
[splitout2] pad=200:200:100:100 [padout];

```

- Create 5 copies of the input audio with ffmpeg:

```
ffmpeg -i INPUT -filter_complex asplit=5 OUTPUT

```

### 48.34 zmq, azmq# TOC

Receive commands sent through a libzmq client, and forward them to filters in the filtergraph.

zmq and azmq work as a pass-through filters. zmq must be inserted between two video filters, azmq between two audio filters. Both are capable to send messages to any filter type.

To enable these filters you need to install the libzmq library and headers and configure FFmpeg with --enable-libzmq.

For more information about libzmq see: http://www.zeromq.org/

The zmq and azmq filters work as a libzmq server, which receives messages sent through a network interface defined by the bind_address (or the abbreviation "b") option. Default value of this option is tcp://localhost:5555. You may want to alter this value to your needs, but do not forget to escape any ’:’ signs (see filtergraph escaping).

The received message must be in the form:

```
TARGET COMMAND [ARG]

```

TARGET specifies the target of the command, usually the name of the filter class or a specific filter instance name. The default filter instance name uses the pattern ‘Parsed_<filter_name>_<index>’, but you can override this by using the ‘filter_name@id’ syntax (see Filtergraph syntax).

COMMAND specifies the name of the command for the target filter.

ARG is optional and specifies the optional argument list for the given COMMAND.

Upon reception, the message is processed and the corresponding command is injected into the filtergraph. Depending on the result, the filter will send a reply to the client, adopting the format:

```
ERROR_CODE ERROR_REASON
MESSAGE

```

MESSAGE is optional.

#### 48.34.1 Examples# TOC

Look at tools/zmqsend for an example of a zmq client which can be used to send commands processed by these filters.

Consider the following filtergraph generated by ffplay. In this example the last overlay filter has an instance name. All other filters will have default instance names.

```
ffplay -dumpgraph 1 -f lavfi "
color=s=100x100:c=red  [l];
color=s=100x100:c=blue [r];
nullsrc=s=200x100, zmq [bg];
[bg][l]   overlay     [bg+l];
[bg+l][r] overlay@my=x=100 "

```

To change the color of the left side of the video, the following command can be used:

```
echo Parsed_color_0 c yellow | tools/zmqsend

```

To change the right side:

```
echo Parsed_color_1 c pink | tools/zmqsend

```

To change the position of the right side:

```
echo overlay@my x 150 | tools/zmqsend

```

## 49 Multimedia Sources# TOC

Below is a description of the currently available multimedia sources.

### 49.1 amovie# TOC

This is the same as movie source, except it selects an audio stream by default.

### 49.2 avsynctest# TOC

Generate an Audio/Video Sync Test.

Generated stream periodically shows flash video frame and emits beep in audio. Useful to inspect A/V sync issues.

It accepts the following options:

size, s

Set output video size. Default value is hd720.

framerate, fr

Set output video frame rate. Default value is 30.

samplerate, sr

Set output audio sample rate. Default value is 44100.

amplitude, a

Set output audio beep amplitude. Default value is 0.7.

period, p

Set output audio beep period in seconds. Default value is 3.

delay, dl

Set output video flash delay in number of frames. Default value is 0.

cycle, c

Enable cycling of video delays, by default is disabled.

duration, d

Set stream output duration. By default duration is unlimited.

fg, bg, ag

Set foreground/background/additional color.

#### 49.2.1 Commands# TOC

This source supports the some above options as commands.

### 49.3 movie# TOC

Read audio and/or video stream(s) from a movie container.

It accepts the following parameters:

filename

The name of the resource to read (not necessarily a file; it can also be a device or a stream accessed through some protocol).

format_name, f

Specifies the format assumed for the movie to read, and can be either the name of a container or an input device. If not specified, the format is guessed from movie_name or by probing.

seek_point, sp

Specifies the seek point in seconds. The frames will be output starting from this seek point. The parameter is evaluated with av_strtod, so the numerical value may be suffixed by an IS postfix. The default value is "0".

streams, s

Specifies the streams to read. Several streams can be specified, separated by "+". The source will then have as many outputs, in the same order. The syntax is explained in the "Stream specifiers" section in the ffmpeg manual. Two special names, "dv" and "da" specify respectively the default (best suited) video and audio stream. Default is "dv", or "da" if the filter is called as "amovie".

stream_index, si

Specifies the index of the video stream to read. If the value is -1, the most suitable video stream will be automatically selected. The default value is "-1". Deprecated. If the filter is called "amovie", it will select audio instead of video.

loop

Specifies how many times to read the stream in sequence. If the value is 0, the stream will be looped infinitely. Default value is "1".

Note that when the movie is looped the source timestamps are not changed, so it will generate non monotonically increasing timestamps.

discontinuity

Specifies the time difference between frames above which the point is considered a timestamp discontinuity which is removed by adjusting the later timestamps.

dec_threads

Specifies the number of threads for decoding

format_opts

Specify format options for the opened file. Format options can be specified as a list of key=value pairs separated by ’:’. The following example shows how to add protocol_whitelist and protocol_blacklist options:

```
ffplay -f lavfi
"movie=filename='1.sdp':format_opts='protocol_whitelist=file,rtp,udp\:protocol_blacklist=http'"

```

It allows overlaying a second video on top of the main input of a filtergraph, as shown in this graph:

```
input -----------> deltapts0 --> overlay --> output
                                    ^
                                    |
movie --> scale--> deltapts1 -------+

```

#### 49.3.1 Examples# TOC

- Skip 3.2 seconds from the start of the AVI file in.avi, and overlay it on top of the input labelled "in":

```
movie=in.avi:seek_point=3.2, scale=180:-1, setpts=PTS-STARTPTS [over];
[in] setpts=PTS-STARTPTS [main];
[main][over] overlay=16:16 [out]

```

- Read from a video4linux2 device, and overlay it on top of the input labelled "in":

```
movie=/dev/video0:f=video4linux2, scale=180:-1, setpts=PTS-STARTPTS [over];
[in] setpts=PTS-STARTPTS [main];
[main][over] overlay=16:16 [out]

```

- Read the first video stream and the audio stream with id 0x81 from dvd.vob; the video is connected to the pad named "video" and the audio is connected to the pad named "audio":

```
movie=dvd.vob:s=v:0+#0x81 [video] [audio]

```

#### 49.3.2 Commands# TOC

Both movie and amovie support the following commands:

seek

Perform seek using "av_seek_frame". The syntax is: seek stream_index|timestamp|flags

- stream_index: If stream_index is -1, a default stream is selected, and timestamp is automatically converted from AV_TIME_BASE units to the stream specific time_base.

- timestamp: Timestamp in AVStream.time_base units or, if no stream is specified, in AV_TIME_BASE units.

- flags: Flags which select direction and seeking mode.

get_duration

Get movie duration in AV_TIME_BASE units.

## 50 External libraries# TOC

FFmpeg can be hooked up with a number of external libraries to add support for more formats. None of them are used by default, their use has to be explicitly requested by passing the appropriate flags to ./configure.

### 50.1 Alliance for Open Media (AOM)# TOC

FFmpeg can make use of the AOM library for AV1 decoding and encoding.

Go to http://aomedia.org/ and follow the instructions for installing the library. Then pass --enable-libaom to configure to enable it.

### 50.2 ARM ASTC Encoder# TOC

FFmpeg can make use of the Arm ASTC Encoder library for ASTC image compression and decompression in the libastcenc encoder and decoder.

Go to https://github.com/ARM-software/astc-encoder to obtain the sources. Version 5.4 or newer is required, because the wrappers use the four-argument astcenc_context_alloc() interface introduced in that release.

The upstream build does not install the public header, and the library file name depends on the configured SIMD and linkage variants, so install the pieces manually in a layout that configure can detect: the header as astcenc/astcenc.h and a library that can be linked with -lastcenc. Keep the library’s own file name, which is the SONAME recorded in the binary, and provide the plain name as an alias:

```
cmake -S . -B build -DCMAKE_BUILD_TYPE=Release -DASTCENC_SHAREDLIB=ON
cmake --build build
install -Dm644 Source/astcenc.h /usr/local/include/astcenc/astcenc.h
install -Dm755 build/Source/libastcenc-native-shared.so \
              /usr/local/lib/libastcenc-native-shared.so
ln -sf libastcenc-native-shared.so /usr/local/lib/libastcenc.so

```

Use the platform’s shared library suffix, and adjust the built library name for other variants (for example libastcenc-neon-shared.so or a static libastcenc.a), or pass --extra-cflags and --extra-ldflags to configure if the files are installed elsewhere. Installing only under the plain name breaks linking at run time, and the installation directory has to be in the runtime loader’s search path.

On big-endian systems, also pass -DASTCENC_ISA_NONE=ON and -DASTCENC_BIG_ENDIAN=ON to CMake. For this variant, install libastcenc-none-shared.so under its own name and provide libastcenc.so as an alias, as in the example above.

The library is licensed under Apache-2.0, which requires version 3 of the (L)GPL, so pass --enable-version3 and --enable-libastcenc to configure to enable it.

### 50.3 AMD AMF/VCE# TOC

FFmpeg can use the AMD Advanced Media Framework library for accelerated H.264 and HEVC(only windows) encoding on hardware with Video Coding Engine (VCE).

To enable support you must obtain the AMF framework header files(version 1.4.9+) from https://github.com/GPUOpen-LibrariesAndSDKs/AMF.git.

Create an AMF/ directory in the system include path. Copy the contents of AMF/amf/public/include/ into that directory. Then configure FFmpeg with --enable-amf.

Initialization of amf encoder occurs in this order: 1) trying to initialize through dx11(only windows) 2) trying to initialize through dx9(only windows) 3) trying to initialize through vulkan

To use h.264(AMD VCE) encoder on linux amdgru-pro version 19.20+ and amf-amdgpu-pro package(amdgru-pro contains, but does not install automatically) are required.

This driver can be installed using amdgpu-pro-install script in official amd driver archive.

### 50.4 AviSynth# TOC

FFmpeg can read AviSynth scripts as input. To enable support, pass --enable-avisynth to configure after installing the headers provided by AviSynth+. AviSynth+ can be configured to install only the headers by either passing -DHEADERS_ONLY:bool=on to the normal CMake-based build system, or by using the supplied GNUmakefile.

For Windows, supported AviSynth variants are AviSynth 2.6 RC1 or higher for 32-bit builds and AviSynth+ r1718 or higher for 32-bit and 64-bit builds.

For Linux, macOS, and BSD, the only supported AviSynth variant is AviSynth+, starting with version 3.5.

In 2016, AviSynth+ added support for building with GCC. However, due to the eccentricities of Windows’ calling conventions, 32-bit GCC builds of AviSynth+ are not compatible with typical 32-bit builds of FFmpeg.

By default, FFmpeg assumes compatibility with 32-bit MSVC builds of AviSynth+ since that is the most widely-used and entrenched build configuration. Users can override this and enable support for 32-bit GCC builds of AviSynth+ by passing -DAVSC_WIN32_GCC32 to --extra-cflags when configuring FFmpeg.

64-bit builds of FFmpeg are not affected, and can use either MSVC or GCC builds of AviSynth+ without any special flags.

AviSynth(+) is loaded dynamically. Distributors can build FFmpeg with --enable-avisynth, and the binaries will work regardless of the end user having AviSynth installed. If/when an end user would like to use AviSynth scripts, then they can install AviSynth(+) and FFmpeg will be able to find and use it to open scripts.

### 50.5 Chromaprint# TOC

FFmpeg can make use of the Chromaprint library for generating audio fingerprints. Pass --enable-chromaprint to configure to enable it. See https://acoustid.org/chromaprint.

### 50.6 codec2# TOC

FFmpeg can make use of the codec2 library for codec2 decoding and encoding. There is currently no native decoder, so libcodec2 must be used for decoding.

Go to http://freedv.org/, download "Codec 2 source archive". Build and install using CMake. Debian users can install the libcodec2-dev package instead. Once libcodec2 is installed you can pass --enable-libcodec2 to configure to enable it.

The easiest way to use codec2 is with .c2 files, since they contain the mode information required for decoding. To encode such a file, use a .c2 file extension and give the libcodec2 encoder the -mode option: ffmpeg -i input.wav -mode 700C output.c2. Playback is as simple as ffplay output.c2. For a list of supported modes, run ffmpeg -h encoder=libcodec2. Raw codec2 files are also supported. To make sense of them the mode in use needs to be specified as a format option: ffmpeg -f codec2raw -mode 1300 -i input.raw output.wav.

### 50.7 dav1d# TOC

FFmpeg can make use of the dav1d library for AV1 video decoding.

Go to https://code.videolan.org/videolan/dav1d and follow the instructions for installing the library. Then pass --enable-libdav1d to configure to enable it.

### 50.8 davs2# TOC

FFmpeg can make use of the davs2 library for AVS2-P2/IEEE1857.4 video decoding.

Go to https://github.com/pkuvcl/davs2 and follow the instructions for installing the library. Then pass --enable-libdavs2 to configure to enable it.

libdavs2 is under the GNU Public License Version 2 or later (see http://www.gnu.org/licenses/old-licenses/gpl-2.0.html for details), you must upgrade FFmpeg’s license to GPL in order to use it.

### 50.9 uavs3d# TOC

FFmpeg can make use of the uavs3d library for AVS3-P2/IEEE1857.10 video decoding.

Go to https://github.com/uavs3/uavs3d and follow the instructions for installing the library. Then pass --enable-libuavs3d to configure to enable it.

### 50.10 Game Music Emu# TOC

FFmpeg can make use of the Game Music Emu library to read audio from supported video game music file formats. Pass --enable-libgme to configure to enable it. See https://bitbucket.org/mpyne/game-music-emu/overview.

### 50.11 Intel QuickSync Video# TOC

FFmpeg can use Intel QuickSync Video (QSV) for accelerated decoding and encoding of multiple codecs. To use QSV, FFmpeg must be linked against the libmfx dispatcher, which loads the actual decoding libraries.

The dispatcher is open source and can be downloaded from https://github.com/lu-zero/mfx_dispatch.git. FFmpeg needs to be configured with the --enable-libmfx option and pkg-config needs to be able to locate the dispatcher’s .pc files.

### 50.12 Kvazaar# TOC

FFmpeg can make use of the Kvazaar library for HEVC encoding.

Go to https://github.com/ultravideo/kvazaar and follow the instructions for installing the library. Then pass --enable-libkvazaar to configure to enable it.

### 50.13 LAME# TOC

FFmpeg can make use of the LAME library for MP3 encoding.

Go to http://lame.sourceforge.net/ and follow the instructions for installing the library. Then pass --enable-libmp3lame to configure to enable it.

### 50.14 LCEVCdec# TOC

FFmpeg can make use of the liblcevc_dec library for LCEVC enhancement layer decoding on supported bitstreams.

Go to https://github.com/v-novaltd/LCEVCdec and follow the instructions for installing the library. Then pass --enable-liblcevc-dec to configure to enable it.

LCEVCdec is under the BSD-3-Clause-Clear License.

### 50.15 libilbc# TOC

iLBC is a narrowband speech codec that has been made freely available by Google as part of the WebRTC project. libilbc is a packaging friendly copy of the iLBC codec. FFmpeg can make use of the libilbc library for iLBC decoding and encoding.

Go to https://github.com/TimothyGu/libilbc and follow the instructions for installing the library. Then pass --enable-libilbc to configure to enable it.

### 50.16 libjxl# TOC

JPEG XL is an image format intended to fully replace legacy JPEG for an extended period of life. See https://jpegxl.info/ for more information, and see https://github.com/libjxl/libjxl for the library source. You can pass --enable-libjxl to configure in order enable the libjxl wrapper.

### 50.17 libvpx# TOC

FFmpeg can make use of the libvpx library for VP8/VP9 decoding and encoding.

Go to http://www.webmproject.org/ and follow the instructions for installing the library. Then pass --enable-libvpx to configure to enable it.

### 50.18 ModPlug# TOC

FFmpeg can make use of this library, originating in Modplug-XMMS, to read from MOD-like music files. See https://github.com/Konstanty/libmodplug. Pass --enable-libmodplug to configure to enable it.

### 50.19 ONNX Runtime# TOC

FFmpeg can make use of the ONNX Runtime library as a backend for DNN based filters.

Go to https://onnxruntime.ai/ and follow the instructions for installing the library. Pre-built packages are available for various platforms.

Configure FFmpeg with ONNX Runtime support:

```
./configure \
    --enable-libonnxruntime \
    --extra-cflags="-I/path/to/onnxruntime/include" \
    --extra-ldflags="-L/path/to/onnxruntime/lib"

```

On ELF-based systems (Linux, BSD) you may also want to embed the library search path so that the installed ffmpeg binary finds the shared library at run time without setting LD_LIBRARY_PATH:

```
./configure \
    --enable-libonnxruntime \
    --extra-cflags="-I/path/to/onnxruntime/include" \
    --extra-ldflags="-L/path/to/onnxruntime/lib -Wl,-rpath,/path/to/onnxruntime/lib"

```

The -Wl,-rpath flag is ELF-specific and should be omitted on other platforms (Windows, macOS).

For MinGW GCC builds, add the -D_stdcall=__stdcall flag for compatibility with ONNX Runtime headers.

### 50.20 OpenCORE, VisualOn, and Fraunhofer libraries# TOC

Spun off Google Android sources, OpenCore, VisualOn and Fraunhofer libraries provide encoders for a number of audio codecs.

OpenCORE and VisualOn libraries are under the Apache License 2.0 (see http://www.apache.org/licenses/LICENSE-2.0 for details), which is incompatible to the LGPL version 2.1 and GPL version 2. You have to upgrade FFmpeg’s license to LGPL version 3 (or if you have enabled GPL components, GPL version 3) by passing --enable-version3 to configure in order to use it.

The license of the Fraunhofer AAC library is incompatible with the GPL. Therefore, for GPL builds, you have to pass --enable-nonfree to configure in order to use it. To the best of our knowledge, it is compatible with the LGPL.

#### 50.20.1 OpenCORE AMR# TOC

FFmpeg can make use of the OpenCORE libraries for AMR-NB decoding/encoding and AMR-WB decoding.

Go to http://sourceforge.net/projects/opencore-amr/ and follow the instructions for installing the libraries. Then pass --enable-libopencore-amrnb and/or --enable-libopencore-amrwb to configure to enable them.

#### 50.20.2 VisualOn AMR-WB encoder library# TOC

FFmpeg can make use of the VisualOn AMR-WBenc library for AMR-WB encoding.

Go to http://sourceforge.net/projects/opencore-amr/ and follow the instructions for installing the library. Then pass --enable-libvo-amrwbenc to configure to enable it.

#### 50.20.3 Fraunhofer AAC library# TOC

FFmpeg can make use of the Fraunhofer AAC library for AAC decoding & encoding.

Go to http://sourceforge.net/projects/opencore-amr/ and follow the instructions for installing the library. Then pass --enable-libfdk-aac to configure to enable it.

#### 50.20.4 Fraunhofer xHE-AAC library# TOC

FFmpeg can make use of the Fraunhofer xHE-AAC library for xHE-AAC encoding.

Go to http://sourceforge.net/projects/opencore-amr/ and follow the instructions for installing the library. Then pass --enable-libfdk-xhe-aac to configure to enable it.

#### 50.20.5 Fraunhofer MPEG-H 3D Audio decoder library# TOC

FFmpeg can make use of the Fraunhofer MPEG-H decoder library for MPEG-H 3DA decoding.

Go to https://github.com/Fraunhofer-IIS/mpeghdec and follow the instructions for installing the library. Then pass --enable-libmpeghdec --enable-nonfree to configure to enable it.

#### 50.20.6 LC3 library# TOC

FFmpeg can make use of the Google LC3 library for LC3 decoding & encoding.

Go to https://github.com/google/liblc3/ and follow the instructions for installing the library. Then pass --enable-liblc3 to configure to enable it.

### 50.21 OpenH264# TOC

FFmpeg can make use of the OpenH264 library for H.264 decoding and encoding.

Go to http://www.openh264.org/ and follow the instructions for installing the library. Then pass --enable-libopenh264 to configure to enable it.

For decoding, this library is much more limited than the built-in decoder in libavcodec; currently, this library lacks support for decoding B-frames and some other main/high profile features. (It currently only supports constrained baseline profile and CABAC.) Using it is mostly useful for testing and for taking advantage of Cisco’s patent portfolio license (http://www.openh264.org/BINARY_LICENSE.txt).

### 50.22 OpenJPEG# TOC

FFmpeg can use the OpenJPEG libraries for decoding/encoding J2K videos. Go to http://www.openjpeg.org/ to get the libraries and follow the installation instructions. To enable using OpenJPEG in FFmpeg, pass --enable-libopenjpeg to ./configure.

### 50.23 rav1e# TOC

FFmpeg can make use of rav1e (Rust AV1 Encoder) via its C bindings to encode videos. Go to https://github.com/xiph/rav1e/ and follow the instructions to build the C library. To enable using rav1e in FFmpeg, pass --enable-librav1e to ./configure.

### 50.24 SVT-AV1# TOC

FFmpeg can make use of the Scalable Video Technology for AV1 library for AV1 encoding.

Go to https://gitlab.com/AOMediaCodec/SVT-AV1/ and follow the instructions for installing the library. Then pass --enable-libsvtav1 to configure to enable it.

### 50.25 SVT-JPEG-XS# TOC

FFmpeg can make use of the Scalable Video Technology for JPEG-XS library for JPEG-XS decoding and encoding.

Go to https://github.com/OpenVisualCloud/SVT-JPEG-XS and follow the instructions for installing the library. Then pass --enable-libsvtjpegxs to configure to enable it.

### 50.26 TwoLAME# TOC

FFmpeg can make use of the TwoLAME library for MP2 encoding.

Go to http://www.twolame.org/ and follow the instructions for installing the library. Then pass --enable-libtwolame to configure to enable it.

### 50.27 VapourSynth# TOC

FFmpeg can read VapourSynth scripts as input. To enable support, pass --enable-vapoursynth to configure. Vapoursynth is detected via pkg-config. Versions 42 or greater supported. See http://www.vapoursynth.com/.

Due to security concerns, Vapoursynth scripts will not be autodetected so the input format has to be forced. For ff* CLI tools, add -f vapoursynth before the input -i yourscript.vpy.

### 50.28 x264# TOC

FFmpeg can make use of the x264 library for H.264 encoding.

Go to http://www.videolan.org/developers/x264.html and follow the instructions for installing the library. Then pass --enable-libx264 to configure to enable it.

x264 is under the GNU Public License Version 2 or later (see http://www.gnu.org/licenses/old-licenses/gpl-2.0.html for details), you must upgrade FFmpeg’s license to GPL in order to use it.

### 50.29 x265# TOC

FFmpeg can make use of the x265 library for HEVC encoding.

Go to http://x265.org/developers.html and follow the instructions for installing the library. Then pass --enable-libx265 to configure to enable it.

x265 is under the GNU Public License Version 2 or later (see http://www.gnu.org/licenses/old-licenses/gpl-2.0.html for details), you must upgrade FFmpeg’s license to GPL in order to use it.

### 50.30 xavs# TOC

FFmpeg can make use of the xavs library for AVS encoding.

Go to http://xavs.sf.net/ and follow the instructions for installing the library. Then pass --enable-libxavs to configure to enable it.

### 50.31 xavs2# TOC

FFmpeg can make use of the xavs2 library for AVS2-P2/IEEE1857.4 video encoding.

Go to https://github.com/pkuvcl/xavs2 and follow the instructions for installing the library. Then pass --enable-libxavs2 to configure to enable it.

libxavs2 is under the GNU Public License Version 2 or later (see http://www.gnu.org/licenses/old-licenses/gpl-2.0.html for details), you must upgrade FFmpeg’s license to GPL in order to use it.

### 50.32 eXtra-fast Essential Video Encoder (XEVE)# TOC

FFmpeg can make use of the XEVE library for EVC video encoding.

Go to https://github.com/mpeg5/xeve and follow the instructions for installing the XEVE library. Then pass --enable-libxeve to configure to enable it.

### 50.33 eXtra-fast Essential Video Decoder (XEVD)# TOC

FFmpeg can make use of the XEVD library for EVC video decoding.

Go to https://github.com/mpeg5/xevd and follow the instructions for installing the XEVD library. Then pass --enable-libxevd to configure to enable it.

### 50.34 ZVBI# TOC

ZVBI is a VBI decoding library which can be used by FFmpeg to decode DVB teletext pages and DVB teletext subtitles.

Go to http://sourceforge.net/projects/zapping/ and follow the instructions for installing the library. Then pass --enable-libzvbi to configure to enable it.

## 51 Supported File Formats, Codecs or Features# TOC

You can use the -formats and -codecs options to have an exhaustive list.

### 51.1 File Formats# TOC

FFmpeg supports the following file formats through the libavformat library:

NameEncodingDecodingComments

3dostrX

4xmX4X Technologies format, used in some games.

8088flex TMVX

AAXXAudible Enhanced Audio format, used in audiobooks.

AAXAudible Format 2, 3, and 4, used in audiobooks.

ACT VoiceXcontains G.729 audio

Adobe FilmstripXX

Audio IFF (AIFF)XX

American Laser Games MMXMultimedia format used in games like Mad Dog McCree.

3GPP AMRXX

Amazing Studio Packed Animation FileXMultimedia format used in game Heart Of Darkness.

Apple HTTP Live StreamingX

Artworx Data FormatX

Interplay ACMXAudio only format used in some Interplay games.

ADPXAudio format used on the Nintendo Gamecube.

AFCXAudio format used on the Nintendo Gamecube.

ADS/SS2XAudio format used on the PS2.

APNGXX

.astcXXRaw ASTC texture container.

ASFXXAdvanced / Active Streaming Format.

ASTXXAudio format used on the Nintendo Wii.

AVIXX

AviSynthX

AVRXAudio format used on Mac.

AVSXMultimedia format used by the Creature Shock game.

Beam Software SIFFXAudio and video format used in some games by Beam Software.

Bethesda Softworks VIDXUsed in some games from Bethesda Softworks.

Binary textX

BinkXMultimedia format used by many games.

Bink AudioXAudio only multimedia format used by some games.

Bitmap Brothers JVXUsed in Z and Z95 games.

BRPXArgonaut Games format.

Brute Force & IgnoranceXUsed in the game Flash Traffic: City of Angels.

BFSTMXAudio format used on the Nintendo WiiU (based on BRSTM).

BRSTMXAudio format used on the Nintendo Wii.

BW64XBroadcast Wave 64bit.

BWFXX

codec2 (raw)XXMust be given -mode format option to decode correctly.

codec2 (.c2 files)XXContains header with version and mode info, simplifying playback.

CRI ADXXXAudio-only format used in console video games.

CRI AIXX

CRI HCAXAudio-only format used in console video games.

Discworld II BMVX

Interplay C93XUsed in the game Cyberia from Interplay.

Delphine Software International CINXMultimedia format used by Delphine Software games.

Digital Speech Standard (DSS)X

CD+GXVideo format used by CD+G karaoke disks

Phantom CineX

Commodore CDXLXAmiga CD video format

Core Audio FormatXXApple Core Audio Format

CRC testing formatX

Creative VoiceXXCreated for the Sound Blaster Pro.

CRYO APCXAudio format used in some games by CRYO Interactive Entertainment.

D-Cinema audioXX

Deluxe Paint AnimationX

DCSTRX

DFAXThis format is used in Chronomaster game

DirectDraw SurfaceX

DSD Stream File (DSF)X

DV videoXX

DXAXThis format is used in the non-Windows version of the Feeble Files game and different game cutscenes repacked for use with ScummVM.

Electronic Arts cdataX

Electronic Arts MultimediaXUsed in various EA games; files have extensions like WVE and UV2.

Ensoniq Paris Audio FileX

FFM (FFserver live feed)XX

Flash (SWF)XX

Flash 9 (AVM2)XXOnly embedded audio is decoded.

FLI/FLC/FLX animationX.fli/.flc files

Flash Video (FLV)XXMacromedia Flash video files

framecrc testing formatX

FunCom ISSXAudio format used in various games from FunCom like The Longest Journey.

G.723.1XX

G.726XBoth left- and right-justified.

G.729 BITXX

G.729 rawX

GENHXAudio format for various games.

GIF AnimationXX

GXFXXGeneral eXchange Format SMPTE 360M, used by Thomson Grass Valley playout servers.

HNMXOnly version 4 supported, used in some games from Cryo Interactive

iCEDraw FileX

ICOXXMicrosoft Windows ICO

id Quake II CIN videoX

id RoQXXUsed in Quake III, Jedi Knight 2 and other computer games.

IEC61937 encapsulationXX

IFFXInterchange File Format

IFVXA format used by some old CCTV DVRs.

iLBCXX

Interplay MVEXFormat used in various Interplay computer games.

Iterated Systems ClearVideoXI-frames only

IV8XA format generated by IndigoVision 8000 video server.

IVF (On2)XXA format used by libvpx

Internet Video RecordingX

IRCAMXX

JPEG Multi-Picture FormatXXIncludes JPEG Ultra HDR (ISO 21496-1 gain map) images.

LAFXLimitless Audio Format

LATMXX

LMLM4XUsed by Linux Media Labs MPEG-4 PCI boards

LOASXcontains LATM multiplexed AAC audio

LRCXX

LVFX

LXFXVR native stream format, used by Leitch/Harris’ video servers.

Magic Lantern Video (MLV)X

MatroskaXX

Matroska audioX

FFmpeg metadataXXMetadata in text format.

MAXIS XAXUsed in Sim City 3000; file extension .xa.

MCAXUsed in some games from Capcom; file extension .mca.

MD StudioX

Metal Gear Solid: The Twin SnakesX

Megalux FrameXUsed by Megalux Ultimate Paint

MobiClip MODSX

MobiClip MOFLEXX

Mobotix .mxgX

Monkey’s AudioX

Motion Pixels MVIX

MOV/QuickTime/MP4XX3GP, 3GP2, PSP, iPod variants supported

MP2XX

MP3XX

MPEG-1 SystemXXmuxed audio and video, VCD format supported

MPEG-PS (program stream)XXalso known as VOB file, SVCD and DVD format supported

MPEG-TS (transport stream)XXalso known as DVB Transport Stream

MPEG-4XXMPEG-4 is a variant of QuickTime.

MSFXAudio format used on the PS3.

Mirillis FIC videoXNo cursor rendering.

MIDI Sample Dump StandardX

MIME multipart JPEGX

MSN TCP webcamXUsed by MSN Messenger webcam streams.

MTVX

MusepackX

Musepack SV8X

Material eXchange Format (MXF)XXSMPTE 377M, used by D-Cinema, broadcast industry.

Material eXchange Format (MXF), D-10 MappingXXSMPTE 386M, D-10/IMX Mapping.

NC camera feedXNC (AVIP NC4600) camera streams

NIST SPeech HEader REsourcesX

Computerized Speech Lab NSPX

NTT TwinVQ (VQF)XNippon Telegraph and Telephone Corporation TwinVQ.

Nullsoft Streaming VideoX

NuppelVideoX

NUTXXNUT Open Container Format

OggXX

Playstation Portable PMPX

Portable Voice FormatX

RK Audio (RKA)X

TechnoTrend PVAXUsed by TechnoTrend DVB PCI boards.

QCPX

raw ADTS (AAC)XX

raw AC-3XX

raw AMR-NBX

raw AMR-WBX

raw APACX

raw APVXX

raw aptXXX

raw aptX HDXX

raw BonkX

raw Chinese AVS videoXX

raw DFPWMXX

raw DiracXX

raw DNxHDXX

raw DTSXX

raw DTS-HDX

raw E-AC-3XX

raw EVCXX

raw FLACXX

raw G.728X

raw GSMX

raw H.261XX

raw H.263XX

raw H.264XX

raw HEVCXX

raw Ingenient MJPEGX

raw MJPEGXX

raw MLPX

raw MPEGX

raw MPEG-1X

raw MPEG-2X

raw MPEG-4XX

raw NULLX

raw videoXX

raw id RoQX

raw OBUXX

raw OSQX

raw SBCXX

raw ShortenX

raw TAKX

raw TrueHDXX

raw VC-1XX

raw PCM A-lawXX

raw PCM mu-lawXX

raw PCM Archimedes VIDCXX

raw PCM signed 8 bitXX

raw PCM signed 16 bit big-endianXX

raw PCM signed 16 bit little-endianXX

raw PCM signed 24 bit big-endianXX

raw PCM signed 24 bit little-endianXX

raw PCM signed 32 bit big-endianXX

raw PCM signed 32 bit little-endianXX

raw PCM signed 64 bit big-endianXX

raw PCM signed 64 bit little-endianXX

raw PCM unsigned 8 bitXX

raw PCM unsigned 16 bit big-endianXX

raw PCM unsigned 16 bit little-endianXX

raw PCM unsigned 24 bit big-endianXX

raw PCM unsigned 24 bit little-endianXX

raw PCM unsigned 32 bit big-endianXX

raw PCM unsigned 32 bit little-endianXX

raw PCM 16.8 floating point little-endianX

raw PCM 24.0 floating point little-endianX

raw PCM floating-point 32 bit big-endianXX

raw PCM floating-point 32 bit little-endianXX

raw PCM floating-point 64 bit big-endianXX

raw PCM floating-point 64 bit little-endianXX

RDTX

REDCODE R3DXFile format used by RED Digital cameras, contains JPEG 2000 frames and PCM audio.

RealMediaXX

RedirectorX

RedSparkX

Renderware TeXture DictionaryX

Resolume DXVXXEncoding is only supported for the DXT1 (Normal Quality, No Alpha) texture format.

RF64X

RL2XAudio and video format used in some games by Entertainment Software Partners.

RPL/ARMovieX

Lego Mindstorms RSOXX

RSDX

RTMPXXOutput is performed by publishing stream to RTMP server

RTPXX

RTSPXX

Sample Dump eXchangeX

SAPXX

SBGX

SDNSX

SDPX

SERX

Digital Pictures SGAX

Sega FILM/CPKXXUsed in many Sega Saturn console games.

Silicon Graphics MovieX

Sierra SOLX.sol files used in Sierra Online games.

Sierra VMDXUsed in Sierra CD-ROM games.

SmackerXMultimedia format used by many games.

SMJPEGXXUsed in certain Loki game ports.

SMPTE 337M encapsulationX

SmushXMultimedia format used in some LucasArts games.

Sony OpenMG (OMA)XXAudio format used in Sony Sonic Stage and Sony Vegas.

Sony PlayStation STRX

Sony Wave64 (W64)XX

SoX native formatXX

SUN AU formatXX

SUP raw PGS subtitlesXX

SVAGXAudio format used in Konami PS2 games.

TDSCX

Text filesX

THPXUsed on the Nintendo GameCube.

Tiertex Limited SEQXTiertex .seq files used in the DOS CD-ROM version of the game Flashback.

True AudioXX

VAGXAudio format used in many Sony PS2 games.

VC-1 test bitstreamXX

Vidvox HapXX

VivoX

VPKXAudio format used in Sony PS games.

Marble WADYX

WAVXX

Waveform ArchiverX

WavPackXX

WebMXX

Windows Televison (WTV)XX

Wing Commander III movieXMultimedia format used in Origin’s Wing Commander III computer game.

Westwood Studios audioXXMultimedia format used in Westwood Studios games.

Westwood Studios VQAXMultimedia format used in Westwood Studios games.

Wideband Single-bit Data (WSD)X

WVEX

KTXXXKhronos Texture 1.0 container for ASTC.

Konami XMDX

XMVXMicrosoft video container used in Xbox games.

XVAGXAudio format used on the PS3.

xWMAXMicrosoft audio container used by XAudio 2.

eXtended BINary text (XBIN)X

YUV4MPEG pipeXX

Psygnosis YOPX

X means that the feature in that column (encoding / decoding) is supported.

### 51.2 Image Formats# TOC

FFmpeg can read and write images for each frame of a video sequence. The following image formats are supported:

NameEncodingDecodingComments

.Y.U.VXXone raw file per component

Alias PIXXXAlias/Wavefront PIX image format

animated GIFXX

APNGXXAnimated Portable Network Graphics

ASTCEEAdaptive Scalable Texture Compression, through external library libastcenc

BMPXXMicrosoft BMP image

BRender PIXXArgonaut BRender 3D engine image format.

CRIXCintel RAW

DPXXXDigital Picture Exchange

EXRXOpenEXR

FITSXXFlexible Image Transport System

HDRXXRadiance HDR RGBE Image format

IMGXGEM Raster image

JPEGXXProgressive JPEG is not supported.

JPEG 2000XX

JPEG-LSXX

JPEG-XSEESupported through external library libsvtjpegxs

LJPEGXLossless JPEG

Media 100X

MSPXMicrosoft Paint image

PAMXXPAM is a PNM extension with alpha support.

PBMXXPortable BitMap image

PCDXPhotoCD

PCXXXPC Paintbrush

PFMXXPortable FloatMap image

PGMXXPortable GrayMap image

PGMYUVXXPGM with U and V components in YUV 4:2:0

PGXXPGX file decoder

PHMXXPortable HalfFloatMap image

PICXPictor/PC Paint

PNGXXPortable Network Graphics image

PPMXXPortable PixelMap image

PSDXPhotoshop

PTXXV.Flash PTX format

QOIXXQuite OK Image format

RW2XPanasonic raw image, RawFormat 8 only

SGIXXSGI RGB image format

Sun RasterfileXXSun RAS image format

TIFFXXYUV, JPEG and some extension is not supported yet.

Truevision TargaXXTarga (.TGA) image format

VBNXXVizrt Binary Image format

WBMPXXWireless Application Protocol Bitmap image format

WebPEXWebP image format, encoding supported through external library libwebp

XBMXXX BitMap image format

XFaceXXX-Face image format

XPMXX PixMap image format

XWDXXX Window Dump image format

X means that the feature in that column (encoding / decoding) is supported.

E means that support is provided through an external library.

### 51.3 Video Codecs# TOC

NameEncodingDecodingComments

4X MovieXUsed in certain computer games.

8088flex TMVX

A64 multicolorXCreates video suitable to be played on a commodore 64 (multicolor mode).

Amazing Studio PAF VideoX

American Laser Games MMXUsed in games like Mad Dog McCree.

Amuse Graphics MovieX

AMV VideoXXUsed in Chinese MP3 players.

ANSI/ASCII artX

Apple Intermediate CodecX

Apple MJPEG-BX

Apple PixletX

Apple ProResXXfourcc: apch,apcn,apcs,apco,ap4h,ap4x

Apple QuickDrawXfourcc: qdrw

APVX

Argonaut VideoXUsed in some Argonaut games.

Asus v1XXfourcc: ASV1

Asus v2XXfourcc: ASV2

ATI VCR1Xfourcc: VCR1

ATI VCR2Xfourcc: VCR2

Auravision AuraX

Auravision Aura 2X

Autodesk Animator Flic videoX

Autodesk RLEXfourcc: AASC

AV1EESupported through external libraries libaom, libdav1d, librav1e and libsvtav1

Avid 1:1 10-bit RGB PackerXXfourcc: AVrp

AVS (Audio Video Standard) videoXVideo encoding used by the Creature Shock game.

AVS2-P2/IEEE1857.4EESupported through external libraries libxavs2 and libdavs2

AVS3-P2/IEEE1857.10ESupported through external library libuavs3d

AYUVXXMicrosoft uncompressed packed 4:4:4:4

Beam Software VBX

Bethesda VID videoXUsed in some games from Bethesda Softworks.

Bink VideoX

BitJazz SheerVideoX

Bitmap Brothers JV videoX

y41p Brooktree uncompressed 4:1:1 12-bitXX

Brooktree ProSumer VideoXfourcc: BT20

Brute Force & IgnoranceXUsed in the game Flash Traffic: City of Angels.

C93 videoXCodec used in Cyberia game.

CamStudioXfourcc: CSCD

CD+GXVideo codec for CD+G karaoke disks

CDXLXAmiga CD video codec

Chinese AVS videoEXAVS1-P2, JiZhun profile, encoding through external library libxavs

Delphine Software International CIN videoXCodec used in Delphine Software International games.

Discworld II BMV VideoX

CineForm HDXX

Canopus HQX

Canopus HQAX

Canopus HQXX

Canopus Lossless CodecX

CDToonsXCodec used in various Broderbund games.

CinepakX

Cirrus Logic AccuPakXXfourcc: CLJR

CPiA Video FormatX

Creative YUV (CYUV)X

DFAXCodec used in Chronomaster game.

DiracEXsupported though the native vc2 (Dirac Pro) encoder

Deluxe Paint AnimationX

DNxHDXXaka SMPTE VC3

Duck TrueMotion 1.0Xfourcc: DUCK

Duck TrueMotion 2.0Xfourcc: TM20

Duck TrueMotion 2.0 RTXfourcc: TR20

DV (Digital Video)XX

Dxtory capture formatX

Feeble Files/ScummVM DXAXCodec originally used in Feeble Files game.

Electronic Arts CMV videoXUsed in NHL 95 game.

Electronic Arts Madcow videoX

Electronic Arts TGV videoX

Electronic Arts TGQ videoX

Electronic Arts TQI videoX

Escape 124X

Escape 130X

EVC / MPEG-5 Part 1EEencoding and decoding supported through external libraries libxeve and libxevd

FFmpeg video codec #1XXlossless codec (fourcc: FFV1)

Flash Screen Video v1XXfourcc: FSV1

Flash Screen Video v2XX

Flash Video (FLV)XXSorenson H.263 used in Flash

FM Screen Capture CodecX

Forward UncompressedX

FrapsX

Go2MeetingXfourcc: G2M2, G2M3

Go2WebinarXfourcc: G2M4

Gremlin Digital VideoX

H.261XX

H.263 / H.263-1996XX

H.263+ / H.263-1998 / H.263 version 2XX

H.264 / AVC / MPEG-4 AVC / MPEG-4 part 10EXencoding supported through external library libx264 and OpenH264, decoding supports data partitioning

HEVCXXencoding supported through external library libx265 and libkvazaar

HNM version 4X

HuffYUVXX

HuffYUV FFmpeg variantXX

IBM UltimotionXfourcc: ULTI

id Cinematic videoXUsed in Quake II.

id RoQ videoXXUsed in Quake III, Jedi Knight 2, other computer games.

IFF ILBMXIFF interleaved bitmap

IFF ByteRun1XIFF run length encoded bitmap

Infinity IMM4X

Infinity IMM5X

Infinity IMM6X

Intel H.263X

Intel Indeo 2X

Intel Indeo 3X

Intel Indeo 4X

Intel Indeo 5X

Interplay C93XUsed in the game Cyberia from Interplay.

Interplay MVE videoXUsed in Interplay .MVE files.

J2KXX

Karl Morton’s video codecXCodec used in Worms games.

Kega Game Video (KGV1)XKega emulator screen capture codec.

LagarithX

LCEVC / MPEG-5 LCEVC / MPEG-5 Part 2Edecoding supported through external library liblcevc-dec

LCL (LossLess Codec Library) MSZHX

LCL (LossLess Codec Library) ZLIBEE

LEAD MCMPX

LOCOX

LucasArts SANM/SmushXUsed in LucasArts games / SMUSH animations.

lossless MJPEGXX

MagicYUV VideoXX

Mandsoft Screen Capture CodecX

Microsoft ATC ScreenXAlso known as Microsoft Screen 3.

Microsoft Expression Encoder ScreenXAlso known as Microsoft Titanium Screen 2.

Microsoft RLEXX

Microsoft Screen 1XAlso known as Windows Media Video V7 Screen.

Microsoft Screen 2XAlso known as Windows Media Video V9 Screen.

Microsoft Video 1X

MimicXUsed in MSN Messenger Webcam streams.

Miro VideoXLXfourcc: VIXL

MJPEG (Motion JPEG)XX

Mobotix MxPEG videoX

Motion Pixels videoX

MPEG-1 videoXX

MPEG-2 videoXX

MPEG-4 part 2XXlibxvidcore can be used alternatively for encoding.

MPEG-4 part 2 Microsoft variant version 1X

MPEG-4 part 2 Microsoft variant version 2XX

MPEG-4 part 2 Microsoft variant version 3XX

Newtek SpeedHQXX

Nintendo Gamecube THP videoX

NotchLCX

NuppelVideo/RTjpegXVideo encoding used in NuppelVideo files.

On2 VP3Xstill experimental

On2 VP4Xfourcc: VP40

On2 VP5Xfourcc: VP50

On2 VP6Xfourcc: VP60,VP61,VP62

On2 VP7Xfourcc: VP70,VP71

VP8EXfourcc: VP80, encoding supported through external library libvpx

VP9EXencoding supported through external library libvpx

Pinnacle TARGA CineWave YUV16Xfourcc: Y216

Q-team QPEGXfourccs: QPEG, Q1.0, Q1.1

QuickTime 8BPS videoX

QuickTime Animation (RLE) videoXXfourcc: ’rle ’

QuickTime Graphics (SMC)XXfourcc: ’smc ’

QuickTime video (RPZA)XXfourcc: rpza

R10K AJA Kona 10-bit RGB CodecXX

R210 Quicktime Uncompressed RGB 10-bitXX

Raw VideoXX

RealVideo 1.0XX

RealVideo 2.0XX

RealVideo 3.0Xstill far from ideal

RealVideo 4.0X

RealVideo 6.0X

Renderware TXD (TeXture Dictionary)XTexture dictionaries used by the Renderware Engine.

RivaTuner VideoXfourcc: ’RTV1’

RL2 videoXused in some games by Entertainment Software Partners

ScreenPressorX

ScreenpressoX

Screen Recorder Gold CodecX

Sierra VMD videoXUsed in Sierra VMD files.

Silicon Graphics Motion Video Compressor 1 (MVC1)X

Silicon Graphics Motion Video Compressor 2 (MVC2)X

Silicon Graphics RLE 8-bit videoX

Smacker videoXVideo encoding used in Smacker.

SMPTE VC-1X

SnowXXexperimental wavelet codec (fourcc: SNOW)

Sony PlayStation MDEC (Motion DECoder)X

Sorenson Vector Quantizer 1XXfourcc: SVQ1

Sorenson Vector Quantizer 3Xfourcc: SVQ3

Sunplus JPEG (SP5X)Xfourcc: SP5X

TechSmith Screen Capture CodecXfourcc: TSCC

TechSmith Screen Capture Codec 2Xfourcc: TSC2

TheoraEXencoding supported through external library libtheora

Tiertex Limited SEQ videoXCodec used in DOS CD-ROM FlashBack game.

Ut VideoXX

v210 QuickTime uncompressed 4:2:2 10-bitXX

v308 QuickTime uncompressed 4:4:4XX

v408 QuickTime uncompressed 4:4:4:4XX

v410 QuickTime uncompressed 4:4:4 10-bitXX

VBLE Lossless CodecX

vMix VideoXfourcc: ’VMX1’

VMware Screen Codec / VMware VideoXCodec used in videos captured by VMware.

Westwood Studios VQA (Vector Quantized Animation) videoX

Windows Media ImageX

Windows Media Video 7XX

Windows Media Video 8XX

Windows Media Video 9Xnot completely working

Wing Commander III / XanXUsed in Wing Commander III .MVE files.

Wing Commander IV / XanXUsed in Wing Commander IV.

Winnov WNV1X

WMV7XX

YAMAHA SMAFXX

Psygnosis YOP VideoX

yuv4XXlibquicktime uncompressed packed 4:2:0

ZeroCodec Lossless VideoX

ZLIBXXpart of LCL, encoder experimental

Zip Motion Blocks VideoXXEncoder works only in PAL8.

X means that the feature in that column (encoding / decoding) is supported.

E means that support is provided through an external library.

### 51.4 Audio Codecs# TOC

NameEncodingDecodingComments

8SVX exponentialX

8SVX fibonacciX

AACEXXencoding supported through internal encoder and external library libfdk-aac

AAC+EIXencoding supported through external library libfdk-aac

AC-3IXIX

ACELP.KELVINX

ADPCM 4X MovieX

ADPCM Yamaha AICAX

ADPCM AmuseGraphics MovieX

ADPCM Argonaut GamesXX

ADPCM CDROM XAX

ADPCM Creative TechnologyX16 -> 4, 8 -> 4, 8 -> 3, 8 -> 2

ADPCM Electronic ArtsXUsed in various EA titles.

ADPCM Electronic Arts Maxis CDROM XSXUsed in Sim City 3000.

ADPCM Electronic Arts R1X

ADPCM Electronic Arts R2X

ADPCM Electronic Arts R3X

ADPCM Electronic Arts XASX

ADPCM G.722XX

ADPCM G.726XX

ADPCM IMA Acorn ReplayX

ADPCM IMA AMVXXUsed in AMV files

ADPCM IMA CitrixX

ADPCM IMA Cunning DevelopmentsX

ADPCM IMA Electronic Arts EACSX

ADPCM IMA Electronic Arts SEADX

ADPCM IMA FuncomX

ADPCM IMA High Voltage Software ALPXX

ADPCM IMA Mobiclip MOFLEXX

ADPCM IMA QuickTimeXX

ADPCM IMA Simon & Schuster InteractiveXX

ADPCM IMA Ubisoft APMXX

ADPCM IMA Loki SDL MJPEGX

ADPCM IMA WAVXX

ADPCM IMA WestwoodX

ADPCM ISS IMAXUsed in FunCom games.

ADPCM IMA DialogicX

ADPCM IMA Duck DK3XUsed in some Sega Saturn console games.

ADPCM IMA Duck DK4XUsed in some Sega Saturn console games.

ADPCM IMA RadicalX

ADPCM IMA XboxX

ADPCM MicrosoftXX

ADPCM MS IMAXX

ADPCM Nintendo Gamecube AFCX

ADPCM Nintendo Gamecube DTKX

ADPCM Nintendo THPX

ADPCM PlaystationX

ADPCM QT IMAXX

ADPCM RhetorexX

ADPCM SanyoX

ADPCM SEGA CRI ADXXXUsed in Sega Dreamcast games.

ADPCM Shockwave FlashXX

ADPCM Sound Blaster Pro 2-bitX

ADPCM Sound Blaster Pro 2.6-bitX

ADPCM Sound Blaster Pro 4-bitX

ADPCM VIMAXUsed in LucasArts SMUSH animations.

ADPCM Konami XMDX

ADPCM Westwood Studios IMAXXUsed in Westwood Studios games like Command and Conquer.

ADPCM YamahaXX

ADPCM ZorkX

AMR-NBEXencoding supported through external library libopencore-amrnb

AMR-WBEXencoding supported through external library libvo-amrwbenc

Amazing Studio PAF AudioX

Apple lossless audioXXQuickTime fourcc ’alac’

aptXXXUsed in Bluetooth A2DP

aptX HDXXUsed in Bluetooth A2DP

ATRAC1X

ATRAC3X

ATRAC3+X

ATRAC9X

Bink AudioXUsed in Bink and Smacker files in many games.

Bonk audioX

codec2EEen/decoding supported through external library libcodec2

CRI HCAX

Delphine Software International CIN audioXCodec used in Delphine Software International games.

DFPWMXX

Digital Speech Standard - Standard Play mode (DSS SP)X

Discworld II BMV AudioX

COOKXAll versions except 5.1 are supported.

DCA (DTS Coherent Acoustics)XXsupported extensions: XCh, XXCH, X96, XBR, XLL, LBR (partially)

Dolby EX

DPCM Cuberoot-Delta-ExactXUsed in few games.

DPCM GremlinX

DPCM id RoQXXUsed in Quake III, Jedi Knight 2 and other computer games.

DPCM Marble WADYX

DPCM InterplayXUsed in various Interplay computer games.

DPCM Squareroot-Delta-ExactXUsed in various games.

DPCM Sierra OnlineXUsed in Sierra Online game audio files.

DPCM SolX

DPCM XanXUsed in Origin’s Wing Commander IV AVI files.

DPCM Xilam DERFX

DSD (Direct Stream Digital), least significant bit firstX

DSD (Direct Stream Digital), most significant bit firstXX

DSD (Direct Stream Digital), least significant bit first, planarX

DSD (Direct Stream Digital), most significant bit first, planarX

DSP Group TrueSpeechX

DST (Direct Stream Transfer)X

DV audioX

Enhanced AC-3XX

EVRC (Enhanced Variable Rate Codec)X

FLAC (Free Lossless Audio Codec)XIX

FTR VoiceX

G.723.1XX

G.728X

G.729X

GSMEXencoding supported through external library libgsm

GSM Microsoft variantEXencoding supported through external library libgsm

IAC (Indeo Audio Coder)X

iLBC (Internet Low Bitrate Codec)EEXencoding and decoding supported through external library libilbc

IMC (Intel Music Coder)X

Interplay ACMX

LC3EEsupported through external library liblc3

MACE (Macintosh Audio Compression/Expansion) 6:1X

Marian’s A-pac audioX

MI-SC4 (Micronas SC-4 Audio)X

MLP (Meridian Lossless Packing)XXUsed in DVD-Audio discs.

Monkey’s AudioX

MP1 (MPEG audio layer 1)IX

MP2 (MPEG audio layer 2)IXIXencoding supported also through external library TwoLAME

MP3 (MPEG audio layer 3)EIXencoding supported through external library LAME, ADU MP3 and MP3onMP4 also supported

MPEG-4 Audio Lossless Coding (ALS)X

MPEG-H 3D AudioEdecoding supported through external library libmpeghdec

MobiClip FastAudioX

Musepack SV7X

Musepack SV8X

Nellymoser AsaoXX

On2 AVC (Audio for Video Codec)X

OpusEXencoding supported through external library libopus

OSQ (Original Sound Quality)X

PCM A-lawXX

PCM mu-lawXX

PCM Archimedes VIDCXX

PCM signed 8-bit planarXX

PCM signed 16-bit big-endian planarXX

PCM signed 16-bit little-endian planarXX

PCM signed 24-bit little-endian planarXX

PCM signed 32-bit little-endian planarXX

PCM 32-bit floating point big-endianXX

PCM 32-bit floating point little-endianXX

PCM 64-bit floating point big-endianXX

PCM 64-bit floating point little-endianXX

PCM D-Cinema audio signed 24-bitXX

PCM signed 8-bitXX

PCM signed 16-bit big-endianXX

PCM signed 16-bit little-endianXX

PCM signed 24-bit big-endianXX

PCM signed 24-bit little-endianXX

PCM signed 32-bit big-endianXX

PCM signed 32-bit little-endianXX

PCM signed 16/20/24-bit big-endian for DVD-AudioX

PCM signed 16/20/24-bit big-endian in MPEG-TSX

PCM unsigned 8-bitXX

PCM unsigned 16-bit big-endianXX

PCM unsigned 16-bit little-endianXX

PCM unsigned 24-bit big-endianXX

PCM unsigned 24-bit little-endianXX

PCM unsigned 32-bit big-endianXX

PCM unsigned 32-bit little-endianXX

PCM SGAX

QCELP / PureVoiceX

QDesign Music Codec 1X

QDesign Music Codec 2XThere are still some distortions.

RealAudio 1.0 (14.4K)XXReal 14400 bit/s codec

RealAudio 2.0 (28.8K)XReal 28800 bit/s codec

RealAudio 3.0 (dnet)IXXReal low bitrate AC-3 codec

RealAudio LosslessX

RealAudio SIPR / ACELP.NETX

RK Audio (RKA)X

SBC (low-complexity subband codec)XXUsed in Bluetooth A2DP

ShortenX

Sierra VMD audioXUsed in Sierra VMD files.

Smacker audioX

SMPTE 302M AES3 audioXX

SonicXXexperimental codec

Sonic losslessXXexperimental codec

SpeexEEXsupported through external library libspeex

TAK (Tom’s lossless Audio Kompressor)X

True Audio (TTA)XX

TrueHDXXUsed in HD-DVD and Blu-Ray discs.

TwinVQ (VQF flavor)X

VIMAXUsed in LucasArts SMUSH animations.

ViewQuest VQCX

VorbisEXA native but very primitive encoder exists.

Voxware MetaSoundX

Waveform ArchiverX

WavPackXX

Westwood Audio (SND1)X

Windows Media Audio 1XX

Windows Media Audio 2XX

Windows Media Audio LosslessX

Windows Media Audio ProX

Windows Media Audio VoiceX

Xbox Media Audio 1X

Xbox Media Audio 2X

X means that the feature in that column (encoding / decoding) is supported.

E means that support is provided through an external library.

I means that an integer-only version is available, too (ensures high performance on systems without hardware floating point support).

### 51.5 Subtitle Formats# TOC

NameMuxingDemuxingEncodingDecoding

3GPP Timed TextXX

AQTitleXX

DVBXXXX

DVB teletextXE

DVDXXXX

JACOsubXXX

MicroDVDXXX

MPL2XX

MPsub (MPlayer)XX

PGSX

PJS (Phoenix)XX

RealTextXX

SAMIXX

Spruce format (STL)XX

SSA/ASSXXXX

SubRip (SRT)XXXX

SubViewer v1XX

SubViewerXX

TED Talks captionsXX

TTMLXX

VobSub (IDX+SUB)XX

VPlayerXX

WebVTTXXXX

XSUBXX

X means that the feature is supported.

E means that support is provided through an external library.

### 51.6 Network Protocols# TOC

NameSupport

AMQPE

fileX

FTPX

GopherX

GophersX

HLSX

HTTPX

HTTPSX

IcecastX

MMSHX

MMSTX

pipeX

Pro-MPEG FECX

RTMPX

RTMPEX

RTMPSX

RTMPTX

RTMPTEX

RTMPTSX

RTPX

SAMBAE

SCTPX

SFTPE

TCPX

TLSX

UDPX

ZMQE

X means that the protocol is supported.

E means that support is provided through an external library.

### 51.7 Input/Output Devices# TOC

NameInputOutput

ALSAXX

BKTRX

cacaX

DV1394X

Lavfi virtual deviceX

Linux framebufferXX

JACKX

LIBCDIOX

LIBDC1394X

OpenALX

OSSXX

PulseAudioXX

SDLX

Video4Linux2XX

VfW captureX

X11 grabbingX

Win32 grabbingX

X means that input/output is supported.

### 51.8 Timecode# TOC

Codec/formatReadWrite

AVIXX

DVXX

GXFXX

MOVXX

MPEG1/2XX

MXFXX

## 52 See Also# TOC

ffmpeg ffplay, ffprobe, ffmpeg-utils, ffmpeg-scaler, ffmpeg-resampler, ffmpeg-codecs, ffmpeg-bitstream-filters, ffmpeg-formats, ffmpeg-devices, ffmpeg-protocols, ffmpeg-filters

## 53 Authors# TOC

The FFmpeg developers.

For details about the authorship, see the Git history of the project (https://git.ffmpeg.org/ffmpeg), e.g. by typing the command git log in the FFmpeg source directory, or browsing the online repository at https://git.ffmpeg.org/ffmpeg.

Maintainers for the specific components are listed in the file MAINTAINERS in the source code tree.

 This document was generated using makeinfo.

Hosting provided by telepoint.bg

