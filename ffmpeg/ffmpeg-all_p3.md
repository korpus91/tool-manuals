Cross feed of left into right with inverted phase. This helps in suppressing the mono. If the value is 1 it will cancel all the signal common to both channels. Default is 0.3.

drymix

Set level of input signal of original channel. Default is 0.8.

#### 36.112.1 Commands# TOC

This filter supports the all above options except delay as commands.

### 36.113 superequalizer# TOC

Apply 18 band equalizer.

The filter accepts the following options:

1b

Set 65Hz band gain.

2b

Set 92Hz band gain.

3b

Set 131Hz band gain.

4b

Set 185Hz band gain.

5b

Set 262Hz band gain.

6b

Set 370Hz band gain.

7b

Set 523Hz band gain.

8b

Set 740Hz band gain.

9b

Set 1047Hz band gain.

10b

Set 1480Hz band gain.

11b

Set 2093Hz band gain.

12b

Set 2960Hz band gain.

13b

Set 4186Hz band gain.

14b

Set 5920Hz band gain.

15b

Set 8372Hz band gain.

16b

Set 11840Hz band gain.

17b

Set 16744Hz band gain.

18b

Set 20000Hz band gain.

### 36.114 surround# TOC

Apply audio surround upmix filter.

This filter allows to produce multichannel output from audio stream.

The filter accepts the following options:

chl_out

Set output channel layout. By default, this is 5.1.

See the Channel Layout section in the ffmpeg-utils(1) manual for the required syntax.

chl_in

Set input channel layout. By default, this is stereo.

See the Channel Layout section in the ffmpeg-utils(1) manual for the required syntax.

level_in

Set input volume level. By default, this is 1.

level_out

Set output volume level. By default, this is 1.

lfe

Enable LFE channel output if output channel layout has it. By default, this is enabled.

lfe_low

Set LFE low cut off frequency. By default, this is 128 Hz.

lfe_high

Set LFE high cut off frequency. By default, this is 256 Hz.

lfe_mode

Set LFE mode, can be add or sub. Default is add. In add mode, LFE channel is created from input audio and added to output. In sub mode, LFE channel is created from input audio and added to output but also all non-LFE output channels are subtracted with output LFE channel.

smooth

Set temporal smoothness strength, used to gradually change factors when transforming stereo sound in time. Allowed range is from 0.0 to 1.0. Useful to improve output quality with focus option values greater than 0.0. Default is 0.0. Only values inside this range and without edges are effective.

angle

Set angle of stereo surround transform, Allowed range is from 0 to 360. Default is 90.

focus

Set focus of stereo surround transform, Allowed range is from -1 to 1. Default is 0.

fc_in

Set front center input volume. By default, this is 1.

fc_out

Set front center output volume. By default, this is 1.

fl_in

Set front left input volume. By default, this is 1.

fl_out

Set front left output volume. By default, this is 1.

fr_in

Set front right input volume. By default, this is 1.

fr_out

Set front right output volume. By default, this is 1.

sl_in

Set side left input volume. By default, this is 1.

sl_out

Set side left output volume. By default, this is 1.

sr_in

Set side right input volume. By default, this is 1.

sr_out

Set side right output volume. By default, this is 1.

bl_in

Set back left input volume. By default, this is 1.

bl_out

Set back left output volume. By default, this is 1.

br_in

Set back right input volume. By default, this is 1.

br_out

Set back right output volume. By default, this is 1.

bc_in

Set back center input volume. By default, this is 1.

bc_out

Set back center output volume. By default, this is 1.

lfe_in

Set LFE input volume. By default, this is 1.

lfe_out

Set LFE output volume. By default, this is 1.

allx

Set spread usage of stereo image across X axis for all channels. Allowed range is from -1 to 15. By default this value is negative -1, and thus unused.

ally

Set spread usage of stereo image across Y axis for all channels. Allowed range is from -1 to 15. By default this value is negative -1, and thus unused.

fcx, flx, frx, blx, brx, slx, srx, bcx

Set spread usage of stereo image across X axis for each channel. Allowed range is from 0.06 to 15. By default this value is 0.5.

fcy, fly, fry, bly, bry, sly, sry, bcy

Set spread usage of stereo image across Y axis for each channel. Allowed range is from 0.06 to 15. By default this value is 0.5.

win_size

Set window size. Allowed range is from 1024 to 65536. Default size is 4096.

win_func

Set window function.

It accepts the following values:

‘rect’

‘bartlett’

‘hann, hanning’

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

Default is hann.

overlap

Set window overlap. If set to 1, the recommended overlap for selected window function will be picked. Default is 0.5.

### 36.115 tiltshelf# TOC

Boost or cut the lower frequencies and cut or boost higher frequencies of the audio using a two-pole shelving filter with a response similar to that of a standard hi-fi’s tone-controls. This is also known as shelving equalisation (EQ).

The filter accepts the following options:

gain, g

Give the gain at 0 Hz. Its useful range is about -20 (for a large cut) to +20 (for a large boost). Beware of clipping when using a positive gain.

frequency, f

Set the filter’s central frequency and so can be used to extend or reduce the frequency range to be boosted or cut. The default value is 3000 Hz.

width_type, t

Set method to specify band-width of filter.

h

Hz

q

Q-Factor

o

octave

s

slope

k

kHz

width, w

Determine how steep is the filter’s shelf transition.

poles, p

Set number of poles. Default is 2.

mix, m

How much to use filtered signal in output. Default is 1. Range is between 0 and 1.

channels, c

Specify which channels to filter, by default all available are filtered.

normalize, n

Normalize biquad coefficients, by default is disabled. Enabling it will normalize magnitude response at DC to 0dB.

transform, a

Set transform type of IIR filter.

di

dii

tdi

tdii

latt

svf

zdf

precision, r

Set precision of filtering.

auto

Pick automatic sample format depending on surround filters.

s16

Always use signed 16-bit.

s32

Always use signed 32-bit.

f32

Always use float 32-bit.

f64

Always use float 64-bit.

block_size, b

Set block size used for reverse IIR processing. If this value is set to high enough value (higher than impulse response length truncated when reaches near zero values) filtering will become linear phase otherwise if not big enough it will just produce nasty artifacts.

Note that filter delay will be exactly this many samples when set to non-zero value.

#### 36.115.1 Commands# TOC

This filter supports some options as commands.

### 36.116 treble, highshelf# TOC

Boost or cut treble (upper) frequencies of the audio using a two-pole shelving filter with a response similar to that of a standard hi-fi’s tone-controls. This is also known as shelving equalisation (EQ).

The filter accepts the following options:

gain, g

Give the gain at whichever is the lower of ~22 kHz and the Nyquist frequency. Its useful range is about -20 (for a large cut) to +20 (for a large boost). Beware of clipping when using a positive gain.

frequency, f

Set the filter’s central frequency and so can be used to extend or reduce the frequency range to be boosted or cut. The default value is 3000 Hz.

width_type, t

Set method to specify band-width of filter.

h

Hz

q

Q-Factor

o

octave

s

slope

k

kHz

width, w

Determine how steep is the filter’s shelf transition.

poles, p

Set number of poles. Default is 2.

mix, m

How much to use filtered signal in output. Default is 1. Range is between 0 and 1.

channels, c

Specify which channels to filter, by default all available are filtered.

normalize, n

Normalize biquad coefficients, by default is disabled. Enabling it will normalize magnitude response at DC to 0dB.

transform, a

Set transform type of IIR filter.

di

dii

tdi

tdii

latt

svf

zdf

precision, r

Set precision of filtering.

auto

Pick automatic sample format depending on surround filters.

s16

Always use signed 16-bit.

s32

Always use signed 32-bit.

f32

Always use float 32-bit.

f64

Always use float 64-bit.

block_size, b

Set block size used for reverse IIR processing. If this value is set to high enough value (higher than impulse response length truncated when reaches near zero values) filtering will become linear phase otherwise if not big enough it will just produce nasty artifacts.

Note that filter delay will be exactly this many samples when set to non-zero value.

#### 36.116.1 Commands# TOC

This filter supports the following commands:

frequency, f

Change treble frequency. Syntax for the command is : "frequency"

width_type, t

Change treble width_type. Syntax for the command is : "width_type"

width, w

Change treble width. Syntax for the command is : "width"

gain, g

Change treble gain. Syntax for the command is : "gain"

mix, m

Change treble mix. Syntax for the command is : "mix"

### 36.117 tremolo# TOC

Sinusoidal amplitude modulation.

The filter accepts the following options:

f

Modulation frequency in Hertz. Modulation frequencies in the subharmonic range (20 Hz or lower) will result in a tremolo effect. This filter may also be used as a ring modulator by specifying a modulation frequency higher than 20 Hz. Range is 0.1 - 20000.0. Default value is 5.0 Hz.

d

Depth of modulation as a percentage. Range is 0.0 - 1.0. Default value is 0.5.

### 36.118 vibrato# TOC

Sinusoidal phase modulation.

The filter accepts the following options:

f

Modulation frequency in Hertz. Range is 0.1 - 20000.0. Default value is 5.0 Hz.

d

Depth of modulation as a percentage. Range is 0.0 - 1.0. Default value is 0.5.

### 36.119 virtualbass# TOC

Apply audio Virtual Bass filter.

This filter accepts stereo input and produce stereo with LFE (2.1) channels output. The newly produced LFE channel have enhanced virtual bass originally obtained from both stereo channels. This filter outputs front left and front right channels unchanged as available in stereo input.

The filter accepts the following options:

cutoff

Set the virtual bass cutoff frequency. Default value is 250 Hz. Allowed range is from 100 to 500 Hz.

strength

Set the virtual bass strength. Allowed range is from 0.5 to 3. Default value is 3.

### 36.120 volume# TOC

Adjust the input audio volume.

It accepts the following parameters:

volume

Set audio volume expression.

Output values are clipped to the maximum value.

The output audio volume is given by the relation:

```
output_volume = volume * input_volume

```

The default value for volume is "1.0".

precision

This parameter represents the mathematical precision.

It determines which input sample formats will be allowed, which affects the precision of the volume scaling.

fixed

8-bit fixed-point; this limits input sample format to U8, S16, and S32.

float

32-bit floating-point; this limits input sample format to FLT. (default)

double

64-bit floating-point; this limits input sample format to DBL.

replaygain

Choose the behaviour on encountering ReplayGain side data in input frames.

drop

Remove ReplayGain side data, ignoring its contents (the default).

ignore

Ignore ReplayGain side data, but leave it in the frame.

track

Prefer the track gain, if present.

album

Prefer the album gain, if present.

replaygain_preamp

Pre-amplification gain in dB to apply to the selected replaygain gain.

Default value for replaygain_preamp is 0.0.

replaygain_noclip

Prevent clipping by limiting the gain applied.

Default value for replaygain_noclip is 1.

eval

Set when the volume expression is evaluated.

It accepts the following values:

‘once’

only evaluate expression once during the filter initialization, or when the ‘volume’ command is sent

‘frame’

evaluate expression for each incoming frame

Default value is ‘once’.

The volume expression can contain the following parameters.

n

frame number (starting at zero)

nb_channels

number of channels

nb_consumed_samples

number of samples consumed by the filter

nb_samples

number of samples in the current frame

pos

original frame position in the file; deprecated, do not use

pts

frame PTS

sample_rate

sample rate

startpts

PTS at start of stream

startt

time at start of stream

t

frame time

tb

timestamp timebase

volume

last set volume value

Note that when eval is set to ‘once’ only the sample_rate and tb variables are available, all other variables will evaluate to NAN.

#### 36.120.1 Commands# TOC

This filter supports the following commands:

volume

Modify the volume expression. The command accepts the same syntax of the corresponding option.

If the specified expression is not valid, it is kept at its current value.

#### 36.120.2 Examples# TOC

- Halve the input audio volume:

```
volume=volume=0.5
volume=volume=1/2
volume=volume=-6.0206dB

```

In all the above example the named key for volume can be omitted, for example like in:

```
volume=0.5

```

- Increase input audio power by 6 decibels using fixed-point precision:

```
volume=volume=6dB:precision=fixed

```

- Fade volume after time 10 with an annihilation period of 5 seconds:

```
volume='if(lt(t,10),1,max(1-(t-10)/5,0))':eval=frame

```

### 36.121 volumedetect# TOC

Detect the volume of the input video.

The filter has no parameters. It supports only 16-bit signed integer samples, so the input will be converted when needed. Statistics about the volume will be printed in the log when the input stream end is reached.

In particular it will show the mean volume (root mean square), maximum volume (on a per-sample basis), and the beginning of a histogram of the registered volume values (from the maximum value to a cumulated 1/1000 of the samples).

All volumes are in decibels relative to the maximum PCM value.

#### 36.121.1 Examples# TOC

Here is an excerpt of the output:

```
[Parsed_volumedetect_0  0xa23120] mean_volume: -27 dB
[Parsed_volumedetect_0  0xa23120] max_volume: -4 dB
[Parsed_volumedetect_0  0xa23120] histogram_4db: 6
[Parsed_volumedetect_0  0xa23120] histogram_5db: 62
[Parsed_volumedetect_0  0xa23120] histogram_6db: 286
[Parsed_volumedetect_0  0xa23120] histogram_7db: 1042
[Parsed_volumedetect_0  0xa23120] histogram_8db: 2551
[Parsed_volumedetect_0  0xa23120] histogram_9db: 4609
[Parsed_volumedetect_0  0xa23120] histogram_10db: 8409

```

It means that:

- The mean square energy is approximately -27 dB, or 10^-2.7.

- The largest sample is at -4 dB, or more precisely between -4 dB and -5 dB.

- There are 6 samples at -4 dB, 62 at -5 dB, 286 at -6 dB, etc.

In other words, raising the volume by +4 dB does not cause any clipping, raising it by +5 dB causes clipping for 6 samples, etc.

### 36.122 whisper# TOC

It runs automatic speech recognition using the OpenAI’s Whisper model.

It requires the whisper.cpp library (https://github.com/ggml-org/whisper.cpp) as a prerequisite. After installing the library it can be enabled using: ./configure --enable-whisper.

The filter has following options:

model

The file path of the downloaded whisper.cpp model (mandatory).

language

The language to use for transcription. Besides a language code, the following special values enable auto-detection:

‘eval’

Re-run language detection on every queued chunk. This costs an extra encoder pass per chunk and the detected language may change mid-file.

‘lock’

Detect the language on the first chunk that produces transcribed text, then reuse it for the remaining chunks.

‘auto’

Currently an alias for ‘eval’. This may change in a future version, so use ‘eval’ or ‘lock’ if the behavior matters.

Default value: "auto"

translate

If enabled, translate the transcription from the source language to English. A multilingual model is required to enable this option. Default value: "false"

queue

The maximum size that will be queued into the filter before processing the audio with whisper. Using a small value the audio stream will be processed more often, but the transcription quality will be lower and the required processing power will be higher. Using a large value (e.g. 10-20s) will produce more accurate results using less CPU (as using the whisper-cli tool), but the transcription latency will be higher, thus not useful to process real-time streams. Consider using the vad_model option associated with a large queue value. Default value: "3"

use_gpu

If the GPU support should be enabled. Default value: "true"

gpu_device

The GPU device index to use. Default value: "0"

destination

If set, the transcription output will be sent to the specified file or URL (use one of the FFmpeg AVIO protocols); otherwise, the output will be logged as info messages. The output will also be set in the "lavfi.whisper.text" frame metadata. If the destination is a file and it already exists, it will be overwritten.

format

The destination format string; it could be "text" (only the transcribed text will be sent to the destination), "srt" (subtitle format) or "json". JSON segments include a language field containing the language code reported by whisper.cpp for the transcription chunk, or unknown if none is available. All segments from the same chunk have the same language. Default value: "text"

max_len

Maximum segment length in characters. When set to a value greater than 0, transcription segments will be split by word to not exceed this length. This is useful for generating subtitles with shorter lines. Default value: "0"

vad_model

Path to the VAD model file. If set, the filter will load an additional voice activity detection module (https://github.com/snakers4/silero-vad) that will be used to fragment the audio queue; use this option setting a valid path obtained from the whisper.cpp repository (e.g. "../whisper.cpp/models/ggml-silero-v5.1.2.bin") and increase the queue parameter to a higher value (e.g. 20).

vad_threshold

The VAD threshold to use. Default value: "0.5"

vad_min_speech_duration

The minimum VAD speaking duration. Default value: "0.1"

vad_min_silence_duration

The minimum VAD silence duration. Default value: "0.5"

#### 36.122.1 Examples# TOC

- Run a transcription with srt file generation:

```
ffmpeg -i input.mp4 -vn -af "whisper=model=../whisper.cpp/models/ggml-base.en.bin\
:language=en\
:queue=3\
:destination=output.srt\
:format=srt" -f null -

```

- Run a transcription and send the output in JSON format to an HTTP service:

```
ffmpeg -i input.mp4 -vn -af "whisper=model=../whisper.cpp/models/ggml-base.en.bin\
:language=en\
:queue=3\
:destination=http\\://localhost\\:3000\
:format=json' -f null -

```

- Transcribe the microphone input using the VAD option:

```
ffmpeg -loglevel warning -f pulse -i default \
-af 'highpass=f=200,lowpass=f=3000,whisper=model=../whisper.cpp/models/ggml-medium.bin\
:language=en\
:queue=10\
:destination=-\
:format=json\
:vad_model=../whisper.cpp/models/ggml-silero-v5.1.2.bin' -f null -

```

## 37 Audio Sources# TOC

Below is a description of the currently available audio sources.

### 37.1 abuffer# TOC

Buffer audio frames, and make them available to the filter chain.

This source is mainly intended for a programmatic use, in particular through the interface defined in libavfilter/buffersrc.h.

It accepts the following parameters:

time_base

The timebase which will be used for timestamps of submitted frames. It must be either a floating-point number or in numerator/denominator form.

sample_rate

The sample rate of the incoming audio buffers.

sample_fmt

The sample format of the incoming audio buffers. Either a sample format name or its corresponding integer representation from the enum AVSampleFormat in libavutil/samplefmt.h

channel_layout

The channel layout of the incoming audio buffers. Either a channel layout name from channel_layout_map in libavutil/channel_layout.c or its corresponding integer representation from the AV_CH_LAYOUT_* macros in libavutil/channel_layout.h

channels

The number of channels of the incoming audio buffers. If both channels and channel_layout are specified, then they must be consistent.

#### 37.1.1 Examples# TOC

```
abuffer=sample_rate=44100:sample_fmt=s16p:channel_layout=stereo

```

will instruct the source to accept planar 16bit signed stereo at 44100Hz. Since the sample format with name "s16p" corresponds to the number 6 and the "stereo" channel layout corresponds to the value 0x3, this is equivalent to:

```
abuffer=sample_rate=44100:sample_fmt=6:channel_layout=0x3

```

### 37.2 aevalsrc# TOC

Generate an audio signal specified by an expression.

This source accepts in input one or more expressions (one for each channel), which are evaluated and used to generate a corresponding audio signal.

This source accepts the following options:

exprs

Set the ’|’-separated expressions list for each separate channel. In case the channel_layout option is not specified, the selected channel layout depends on the number of provided expressions. Otherwise the last specified expression is applied to the remaining output channels.

channel_layout, c

Set the channel layout. The number of channels in the specified layout must be equal to the number of specified expressions.

duration, d

Set the minimum duration of the sourced audio. See the Time duration section in the ffmpeg-utils(1) manual for the accepted syntax. Note that the resulting duration may be greater than the specified duration, as the generated audio is always cut at the end of a complete frame.

If not specified, or the expressed duration is negative, the audio is supposed to be generated forever.

nb_samples, n

Set the number of samples per channel per each output frame, default to 1024.

sample_rate, s

Specify the sample rate, default to 44100.

Each expression in exprs can contain the following constants:

n

number of the evaluated sample, starting from 0

t

time of the evaluated sample expressed in seconds, starting from 0

s

sample rate

#### 37.2.1 Examples# TOC

- Generate silence:

```
aevalsrc=0

```

- Generate a sin signal with frequency of 440 Hz, set sample rate to 8000 Hz:

```
aevalsrc="sin(440*2*PI*t):s=8000"

```

- Generate a two channels signal, specify the channel layout (Front Center + Back Center) explicitly:

```
aevalsrc="sin(420*2*PI*t)|cos(430*2*PI*t):c=FC|BC"

```

- Generate white noise:

```
aevalsrc="-2+random(0)"

```

- Generate an amplitude modulated signal:

```
aevalsrc="sin(10*2*PI*t)*sin(880*2*PI*t)"

```

- Generate 2.5 Hz binaural beats on a 360 Hz carrier:

```
aevalsrc="0.1*sin(2*PI*(360-2.5/2)*t) | 0.1*sin(2*PI*(360+2.5/2)*t)"

```

### 37.3 afdelaysrc# TOC

Generate a fractional delay FIR coefficients.

The resulting stream can be used with afir filter for filtering the audio signal.

The filter accepts the following options:

delay, d

Set the fractional delay. Default is 0.

sample_rate, r

Set the sample rate, default is 44100.

nb_samples, n

Set the number of samples per each frame. Default is 1024.

taps, t

Set the number of filter coefficients in output audio stream. Default value is 0.

channel_layout, c

Specifies the channel layout, and can be a string representing a channel layout. The default value of channel_layout is "stereo".

### 37.4 afireqsrc# TOC

Generate a FIR equalizer coefficients.

The resulting stream can be used with afir filter for filtering the audio signal.

The filter accepts the following options:

preset, p

Set equalizer preset. Default preset is flat.

Available presets are:

‘custom’

‘flat’

‘acoustic’

‘bass’

‘beats’

‘classic’

‘clear’

‘deep bass’

‘dubstep’

‘electronic’

‘hard-style’

‘hip-hop’

‘jazz’

‘metal’

‘movie’

‘pop’

‘r&b’

‘rock’

‘vocal booster’

gains, g

Set custom gains for each band. Only used if the preset option is set to custom. Gains are separated by white spaces and each gain is set in dBFS. Default is 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0.

bands, b

Set the custom bands from where custom equalizer gains are set. This must be in strictly increasing order. Only used if the preset option is set to custom. Bands are separated by white spaces and each band represent frequency in Hz. Default is 25 40 63 100 160 250 400 630 1000 1600 2500 4000 6300 10000 16000 24000.

taps, t

Set number of filter coefficients in output audio stream. Default value is 4096.

sample_rate, r

Set sample rate of output audio stream, default is 44100.

nb_samples, n

Set number of samples per each frame in output audio stream. Default is 1024.

interp, i

Set interpolation method for FIR equalizer coefficients. Can be linear or cubic.

phase, h

Set phase type of FIR filter. Can be linear or min: minimum-phase. Default is minimum-phase filter.

### 37.5 afirsrc# TOC

Generate a FIR coefficients using frequency sampling method.

The resulting stream can be used with afir filter for filtering the audio signal.

The filter accepts the following options:

taps, t

Set number of filter coefficients in output audio stream. Default value is 1025.

frequency, f

Set frequency points from where magnitude and phase are set. This must be in non decreasing order, and first element must be 0, while last element must be 1. Elements are separated by white spaces.

magnitude, m

Set magnitude value for every frequency point set by frequency. Number of values must be same as number of frequency points. Values are separated by white spaces.

phase, p

Set phase value for every frequency point set by frequency. Number of values must be same as number of frequency points. Values are separated by white spaces.

sample_rate, r

Set sample rate, default is 44100.

nb_samples, n

Set number of samples per each frame. Default is 1024.

win_func, w

Set window function. Default is blackman.

### 37.6 anullsrc# TOC

The null audio source, return unprocessed audio frames. It is mainly useful as a template and to be employed in analysis / debugging tools, or as the source for filters which ignore the input data (for example the sox synth filter).

This source accepts the following options:

channel_layout, cl

Specifies the channel layout, and can be either an integer or a string representing a channel layout. The default value of channel_layout is "stereo".

Check the channel_layout_map definition in libavutil/channel_layout.c for the mapping between strings and channel layout values.

sample_rate, r

Specifies the sample rate, and defaults to 44100.

nb_samples, n

Set the number of samples per requested frames.

duration, d

Set the duration of the sourced audio. See the Time duration section in the ffmpeg-utils(1) manual for the accepted syntax.

If not specified, or the expressed duration is negative, the audio is supposed to be generated forever.

#### 37.6.1 Examples# TOC

- Set the sample rate to 48000 Hz and the channel layout to AV_CH_LAYOUT_MONO.

```
anullsrc=r=48000:cl=4

```

- Do the same operation with a more obvious syntax:

```
anullsrc=r=48000:cl=mono

```

All the parameters need to be explicitly defined.

### 37.7 flite# TOC

Synthesize a voice utterance using the libflite library.

To enable compilation of this filter you need to configure FFmpeg with --enable-libflite.

Note that versions of the flite library prior to 2.0 are not thread-safe.

The filter accepts the following options:

list_voices

If set to 1, list the names of the available voices and exit immediately. Default value is 0.

nb_samples, n

Set the maximum number of samples per frame. Default value is 512.

textfile

Set the filename containing the text to speak.

text

Set the text to speak.

voice, v

Set the voice to use for the speech synthesis. Default value is kal. See also the list_voices option.

#### 37.7.1 Examples# TOC

- Read from file speech.txt, and synthesize the text using the standard flite voice:

```
flite=textfile=speech.txt

```

- Read the specified text selecting the slt voice:

```
flite=text='So fare thee well, poor devil of a Sub-Sub, whose commentator I am':voice=slt

```

- Input text to ffmpeg:

```
ffmpeg -f lavfi -i flite=text='So fare thee well, poor devil of a Sub-Sub, whose commentator I am':voice=slt

```

- Make ffplay speak the specified text, using flite and the lavfi device:

```
ffplay -f lavfi flite=text='No more be grieved for which that thou hast done.'

```

For more information about libflite, check: http://www.festvox.org/flite/

### 37.8 anoisesrc# TOC

Generate a noise audio signal.

The filter accepts the following options:

sample_rate, r

Specify the sample rate. Default value is 48000 Hz.

amplitude, a

Specify the amplitude (0.0 - 1.0) of the generated audio stream. Default value is 1.0.

duration, d

Specify the duration of the generated audio stream. Not specifying this option results in noise with an infinite length.

color, colour, c

Specify the color of noise. Available noise colors are white, pink, brown, blue, violet and velvet. Default color is white.

seed, s

Specify a value used to seed the PRNG.

nb_samples, n

Set the number of samples per each output frame, default is 1024.

density

Set the density (0.0 - 1.0) for the velvet noise generator, default is 0.05.

#### 37.8.1 Examples# TOC

- Generate 60 seconds of pink noise, with a 44.1 kHz sampling rate and an amplitude of 0.5:

```
anoisesrc=d=60:c=pink:r=44100:a=0.5

```

### 37.9 hilbert# TOC

Generate odd-tap Hilbert transform FIR coefficients.

The resulting stream can be used with afir filter for phase-shifting the signal by 90 degrees.

This is used in many matrix coding schemes and for analytic signal generation. The process is often written as a multiplication by i (or j), the imaginary unit.

The filter accepts the following options:

sample_rate, s

Set sample rate, default is 44100.

taps, t

Set length of FIR filter, default is 22051.

nb_samples, n

Set number of samples per each frame.

win_func, w

Set window function to be used when generating FIR coefficients.

### 37.10 sinc# TOC

Generate a sinc kaiser-windowed low-pass, high-pass, band-pass, or band-reject FIR coefficients.

The resulting stream can be used with afir filter for filtering the audio signal.

The filter accepts the following options:

sample_rate, r

Set sample rate, default is 44100.

nb_samples, n

Set number of samples per each frame. Default is 1024.

hp

Set high-pass frequency. Default is 0.

lp

Set low-pass frequency. Default is 0. If high-pass frequency is lower than low-pass frequency and low-pass frequency is higher than 0 then filter will create band-pass filter coefficients, otherwise band-reject filter coefficients.

phase

Set filter phase response. Default is 50. Allowed range is from 0 to 100.

beta

Set Kaiser window beta.

att

Set stop-band attenuation. Default is 120dB, allowed range is from 40 to 180 dB.

round

Enable rounding, by default is disabled.

hptaps

Set number of taps for high-pass filter.

lptaps

Set number of taps for low-pass filter.

### 37.11 sine# TOC

Generate an audio signal made of a sine wave with amplitude 1/8.

The audio signal is bit-exact.

The filter accepts the following options:

frequency, f

Set the carrier frequency. Default is 440 Hz.

beep_factor, b

Enable a periodic beep every second with frequency beep_factor times the carrier frequency. Default is 0, meaning the beep is disabled.

sample_rate, r

Specify the sample rate, default is 44100.

duration, d

Specify the duration of the generated audio stream.

samples_per_frame

Set the number of samples per output frame.

The expression can contain the following constants:

n

The (sequential) number of the output audio frame, starting from 0.

pts

The PTS (Presentation TimeStamp) of the output audio frame, expressed in TB units.

t

The PTS of the output audio frame, expressed in seconds.

TB

The timebase of the output audio frames.

Default is 1024.

#### 37.11.1 Examples# TOC

- Generate a simple 440 Hz sine wave:

```
sine

```

- Generate a 220 Hz sine wave with a 880 Hz beep each second, for 5 seconds:

```
sine=220:4:d=5
sine=f=220:b=4:d=5
sine=frequency=220:beep_factor=4:duration=5

```

- Generate a 1 kHz sine wave following 1602,1601,1602,1601,1602 NTSC pattern:

```
sine=1000:samples_per_frame='st(0,mod(n,5)); 1602-not(not(eq(ld(0),1)+eq(ld(0),3)))'

```

## 38 Audio Sinks# TOC

Below is a description of the currently available audio sinks.

### 38.1 abuffersink# TOC

Buffer audio frames, and make them available to the end of filter chain.

This sink is mainly intended for programmatic use, in particular through the interface defined in libavfilter/buffersink.h or the options system.

It accepts a pointer to an AVABufferSinkContext structure, which defines the incoming buffers’ formats, to be passed as the opaque parameter to avfilter_init_filter for initialization.

### 38.2 anullsink# TOC

Null audio sink; do absolutely nothing with the input audio. It is mainly useful as a template and for use in analysis / debugging tools.

## 39 Video Filters# TOC

When you configure your FFmpeg build, you can disable any of the existing filters using --disable-filters. The configure output will show the video filters included in your build.

Below is a description of the currently available video filters.

### 39.1 addroi# TOC

Mark a region of interest in a video frame.

The frame data is passed through unchanged, but metadata is attached to the frame indicating regions of interest which can affect the behaviour of later encoding. Multiple regions can be marked by applying the filter multiple times.

x

Region distance in pixels from the left edge of the frame.

y

Region distance in pixels from the top edge of the frame.

w

Region width in pixels.

h

Region height in pixels.

The parameters x, y, w and h are expressions, and may contain the following variables:

iw

Width of the input frame.

ih

Height of the input frame.

qoffset

Quantisation offset to apply within the region.

This must be a real value in the range -1 to +1. A value of zero indicates no quality change. A negative value asks for better quality (less quantisation), while a positive value asks for worse quality (greater quantisation).

The range is calibrated so that the extreme values indicate the largest possible offset - if the rest of the frame is encoded with the worst possible quality, an offset of -1 indicates that this region should be encoded with the best possible quality anyway. Intermediate values are then interpolated in some codec-dependent way.

For example, in 10-bit H.264 the quantisation parameter varies between -12 and 51. A typical qoffset value of -1/10 therefore indicates that this region should be encoded with a QP around one-tenth of the full range better than the rest of the frame. So, if most of the frame were to be encoded with a QP of around 30, this region would get a QP of around 24 (an offset of approximately -1/10 * (51 - -12) = -6.3). An extreme value of -1 would indicate that this region should be encoded with the best possible quality regardless of the treatment of the rest of the frame - that is, should be encoded at a QP of -12.

clear

If set to true, remove any existing regions of interest marked on the frame before adding the new one.

#### 39.1.1 Examples# TOC

- Mark the centre quarter of the frame as interesting.

```
addroi=iw/4:ih/4:iw/2:ih/2:-1/10

```

- Mark the 100-pixel-wide region on the left edge of the frame as very uninteresting (to be encoded at much lower quality than the rest of the frame).

```
addroi=0:0:100:ih:+1/5

```

### 39.2 alphaextract# TOC

Extract the alpha component from the input as a grayscale video. This is especially useful with the alphamerge filter.

### 39.3 alphamerge# TOC

Add or replace the alpha component of the primary input with the grayscale value of a second input. This is intended for use with alphaextract to allow the transmission or storage of frame sequences that have alpha in a format that doesn’t support an alpha channel.

For example, to reconstruct full frames from a normal YUV-encoded video and a separate video created with alphaextract, you might use:

```
movie=in_alpha.mkv [alpha]; [in][alpha] alphamerge [out]

```

### 39.4 amplify# TOC

Amplify differences between current pixel and pixels of adjacent frames in same pixel location.

This filter accepts the following options:

radius

Set frame radius. Default is 2. Allowed range is from 1 to 63. For example radius of 3 will instruct filter to calculate average of 7 frames.

factor

Set factor to amplify difference. Default is 2. Allowed range is from 0 to 65535.

threshold

Set threshold for difference amplification. Any difference greater or equal to this value will not alter source pixel. Default is 10. Allowed range is from 0 to 65535.

tolerance

Set tolerance for difference amplification. Any difference lower to this value will not alter source pixel. Default is 0. Allowed range is from 0 to 65535.

low

Set lower limit for changing source pixel. Default is 65535. Allowed range is from 0 to 65535. This option controls maximum possible value that will decrease source pixel value.

high

Set high limit for changing source pixel. Default is 65535. Allowed range is from 0 to 65535. This option controls maximum possible value that will increase source pixel value.

planes

Set which planes to filter. Default is all. Allowed range is from 0 to 15.

#### 39.4.1 Commands# TOC

This filter supports the following commands that corresponds to option of same name:

factor

threshold

tolerance

low

high

planes

### 39.5 ass# TOC

Same as the subtitles filter, except that it doesn’t require libavcodec and libavformat to work. On the other hand, it is limited to ASS (Advanced Substation Alpha) subtitles files.

This filter accepts filename/f, original_size, fontsdir, and alpha from the subtitles filter, plus the following options:

script

The ASS script to render, given inline. Exactly one of filename and script must be set.

shaping

Set the shaping engine.

Available values are:

‘auto’

The default libass shaping engine, which is the best available.

‘simple’

Fast, font-agnostic shaper that can do only substitutions.

‘complex’

Slower shaper using OpenType for substitutions and positioning. Required for correct rendering of complex scripts such as Arabic, Hebrew, Devanagari and Thai. Requires libass to be built with HarfBuzz.

The default is auto.

#### 39.5.1 Commands# TOC

This filter supports the script option as commands; the new script replaces the one being rendered.

### 39.6 atadenoise# TOC

Apply an Adaptive Temporal Averaging Denoiser to the video input.

The filter accepts the following options:

0a

Set threshold A for 1st plane. Default is 0.02. Valid range is 0 to 0.3.

0b

Set threshold B for 1st plane. Default is 0.04. Valid range is 0 to 5.

1a

Set threshold A for 2nd plane. Default is 0.02. Valid range is 0 to 0.3.

1b

Set threshold B for 2nd plane. Default is 0.04. Valid range is 0 to 5.

2a

Set threshold A for 3rd plane. Default is 0.02. Valid range is 0 to 0.3.

2b

Set threshold B for 3rd plane. Default is 0.04. Valid range is 0 to 5.

3a

Set threshold A for 4th plane. Default is 0.02. Valid range is 0 to 0.3.

3b

Set threshold B for 4th plane. Default is 0.04. Valid range is 0 to 5.

Threshold A is designed to react on abrupt changes in the input signal and threshold B is designed to react on continuous changes in the input signal.

s

Set number of frames filter will use for averaging. Default is 9. Must be odd number in range [5, 129].

p

Set what planes of frame filter will use for averaging. Default is all.

a

Set what variant of algorithm filter will use for averaging. Default is p parallel. Alternatively can be set to s serial.

Parallel can be faster then serial, while other way around is never true. Parallel will abort early on first change being greater then thresholds, while serial will continue processing other side of frames if they are equal or below thresholds.

0s

1s

2s

3s

Set sigma for 1st plane, 2nd plane, 3rd plane or 4th plane. Default is 32767. Valid range is from 0 to 32767. This options controls weight for each pixel in radius defined by size. Default value means every pixel have same weight. Setting this option to 0 effectively disables filtering.

#### 39.6.1 Commands# TOC

This filter supports same commands as options except option s. The command accepts the same syntax of the corresponding option.

### 39.7 avgblur# TOC

Apply average blur filter.

The filter accepts the following options:

sizeX

Set horizontal radius size.

planes

Set which planes to filter. By default all planes are filtered.

sizeY

Set vertical radius size, if zero it will be same as sizeX. Default is 0.

#### 39.7.1 Commands# TOC

This filter supports same commands as options. The command accepts the same syntax of the corresponding option.

If the specified expression is not valid, it is kept at its current value.

### 39.8 backgroundkey# TOC

Turns a static background into transparency.

The filter accepts the following option:

threshold

Threshold for scene change detection.

similarity

Similarity percentage with the background.

blend

Set the blend amount for pixels that are not similar.

#### 39.8.1 Commands# TOC

This filter supports the all above options as commands.

### 39.9 bbox# TOC

Compute the bounding box for the non-black pixels in the input frame luma plane.

This filter computes the bounding box containing all the pixels with a luma value greater than the minimum allowed value. The parameters describing the bounding box are printed on the filter log.

The filter accepts the following option:

min_val

Set the minimal luma value. Default is 16.

#### 39.9.1 Commands# TOC

This filter supports the all above options as commands.

### 39.10 bilateral# TOC

Apply bilateral filter, spatial smoothing while preserving edges.

The filter accepts the following options:

sigmaS

Set sigma of gaussian function to calculate spatial weight. Allowed range is 0 to 512. Default is 0.1.

sigmaR

Set sigma of gaussian function to calculate range weight. Allowed range is 0 to 1. Default is 0.1.

planes

Set planes to filter. Default is first only.

#### 39.10.1 Commands# TOC

This filter supports the all above options as commands.

### 39.11 bitplanenoise# TOC

Show and measure bit plane noise.

The filter accepts the following options:

bitplane

Set which plane to analyze. Default is 1.

filter

Filter out noisy pixels from bitplane set above. Default is disabled.

### 39.12 blackdetect, blackdetect_vulkan# TOC

Detect video intervals that are (almost) completely black. Can be useful to detect chapter transitions, commercials, or invalid recordings.

The filter outputs its detection analysis to both the log as well as frame metadata. If a black segment of at least the specified minimum duration is found, a line with the start and end timestamps as well as duration is printed to the log with level info. In addition, a log line with level debug is printed per frame showing the black amount detected for that frame.

The filter also attaches metadata to the first frame of a black segment with key lavfi.black_start and to the first frame after the black segment ends with key lavfi.black_end. The value is the frame’s timestamp. This metadata is added regardless of the minimum duration specified.

The filter accepts the following options:

black_min_duration, d

Set the minimum detected black duration expressed in seconds. It must be a non-negative floating point number.

Default value is 2.0.

picture_black_ratio_th, pic_th

Set the threshold for considering a picture "black". Express the minimum value for the ratio:

```
nb_black_pixels / nb_pixels

```

for which a picture is considered black. Default value is 0.98.

pixel_black_th, pix_th

Set the threshold for considering a pixel "black".

The threshold expresses the maximum pixel luma value for which a pixel is considered "black". The provided value is scaled according to the following equation:

```
absolute_threshold = luma_minimum_value + pixel_black_th * luma_range_size

```

luma_range_size and luma_minimum_value depend on the input video format, the range is [0-255] for YUV full-range formats and [16-235] for YUV non full-range formats.

Default value is 0.10.

alpha

If true, check the alpha channel instead of the luma channel. Detects frames which are (almost) transparent, instead of frames which are almost black.

Default value is disabled.

The following example sets the maximum pixel threshold to the minimum value, and detects only black intervals of 2 or more seconds:

```
blackdetect=d=2:pix_th=0.00

```

### 39.13 blackframe# TOC

Detect frames that are (almost) completely black. Can be useful to detect chapter transitions or commercials. Output lines consist of the frame number of the detected frame, the percentage of blackness, the position in the file if known or -1 and the timestamp in seconds.

In order to display the output lines, you need to set the loglevel at least to the AV_LOG_INFO value.

This filter exports frame metadata lavfi.blackframe.pblack. The value represents the percentage of pixels in the picture that are below the threshold value.

It accepts the following parameters:

amount

The percentage of the pixels that have to be below the threshold; it defaults to 98.

threshold, thresh

The threshold below which a pixel value is considered black; it defaults to 32.

### 39.14 blend# TOC

Blend two video frames into each other.

The blend filter takes two input streams and outputs one stream, the first input is the "top" layer and second input is "bottom" layer. By default, the output terminates when the longest input terminates.

The tblend (time blend) filter takes two consecutive frames from one single stream, and outputs the result obtained by blending the new frame on top of the old frame.

A description of the accepted options follows.

c0_mode

c1_mode

c2_mode

c3_mode

all_mode

Set blend mode for specific pixel component or all pixel components in case of all_mode. Default value is normal.

Available values for component modes are:

‘addition’

‘and’

‘average’

‘bleach’

‘burn’

‘darken’

‘difference’

‘divide’

‘dodge’

‘exclusion’

‘extremity’

‘freeze’

‘geometric’

‘glow’

‘grainextract’

‘grainmerge’

‘hardlight’

‘hardmix’

‘hardoverlay’

‘harmonic’

‘heat’

‘interpolate’

‘lighten’

‘linearlight’

‘multiply’

‘multiply128’

‘negation’

‘normal’

‘or’

‘overlay’

‘phoenix’

‘pinlight’

‘reflect’

‘screen’

‘softdifference’

‘softlight’

‘stain’

‘subtract’

‘vividlight’

‘xor’

c0_opacity

c1_opacity

c2_opacity

c3_opacity

all_opacity

Set blend opacity for specific pixel component or all pixel components in case of all_opacity. Only used in combination with pixel component blend modes.

c0_expr

c1_expr

c2_expr

c3_expr

all_expr

Set blend expression for specific pixel component or all pixel components in case of all_expr. Note that related mode options will be ignored if those are set.

The expressions can use the following variables:

N

The sequential number of the filtered frame, starting from 0.

X

Y

the coordinates of the current sample

W

H

the width and height of currently filtered plane

SW

SH

Width and height scale for the plane being filtered. It is the ratio between the dimensions of the current plane to the luma plane, e.g. for a yuv420p frame, the values are 1,1 for the luma plane and 0.5,0.5 for the chroma planes.

T

Time of the current frame, expressed in seconds.

TOP, A

Value of pixel component at current location for first video frame (top layer).

BOTTOM, B

Value of pixel component at current location for second video frame (bottom layer).

The blend filter also supports the framesync options.

#### 39.14.1 Examples# TOC

- Apply transition from bottom layer to top layer in first 10 seconds:

```
blend=all_expr='A*(if(gte(T,10),1,T/10))+B*(1-(if(gte(T,10),1,T/10)))'

```

- Apply linear horizontal transition from top layer to bottom layer:

```
blend=all_expr='A*(X/W)+B*(1-X/W)'

```

- Apply 1x1 checkerboard effect:

```
blend=all_expr='if(eq(mod(X,2),mod(Y,2)),A,B)'

```

- Apply uncover left effect:

```
blend=all_expr='if(gte(N*SW+X,W),A,B)'

```

- Apply uncover down effect:

```
blend=all_expr='if(gte(Y-N*SH,0),A,B)'

```

- Apply uncover up-left effect:

```
blend=all_expr='if(gte(T*SH*40+Y,H)*gte((T*40*SW+X)*W/H,W),A,B)'

```

- Split diagonally video and shows top and bottom layer on each side:

```
blend=all_expr='if(gt(X,Y*(W/H)),A,B)'

```

- Display differences between the current and the previous frame:

```
tblend=all_mode=grainextract

```

#### 39.14.2 Commands# TOC

This filter supports same commands as options.

### 39.15 blockdetect# TOC

Determines blockiness of frames without altering the input frames.

Based on Remco Muijs and Ihor Kirenko: "A no-reference blocking artifact measure for adaptive video processing." 2005 13th European signal processing conference.

The filter accepts the following options:

period_min

period_max

Set minimum and maximum values for determining pixel grids (periods). Default values are [3,24].

planes

Set planes to filter. Default is first only.

#### 39.15.1 Examples# TOC

- Determine blockiness for the first plane and search for periods within [8,32]:

```
blockdetect=period_min=8:period_max=32:planes=1

```

### 39.16 blurdetect# TOC

Determines blurriness of frames without altering the input frames.

Based on Marziliano, Pina, et al. "A no-reference perceptual blur metric." Allows for a block-based abbreviation.

The filter accepts the following options:

low

high

Set low and high threshold values used by the Canny thresholding algorithm.

The high threshold selects the "strong" edge pixels, which are then connected through 8-connectivity with the "weak" edge pixels selected by the low threshold.

low and high threshold values must be chosen in the range [0,1], and low should be lesser or equal to high.

Default value for low is 20/255, and default value for high is 50/255.

radius

Define the radius to search around an edge pixel for local maxima.

block_pct

Determine blurriness only for the most significant blocks, given in percentage.

block_width

Determine blurriness for blocks of width block_width. If set to any value smaller 1, no blocks are used and the whole image is processed as one no matter of block_height.

block_height

Determine blurriness for blocks of height block_height. If set to any value smaller 1, no blocks are used and the whole image is processed as one no matter of block_width.

planes

Set planes to filter. Default is first only.

#### 39.16.1 Examples# TOC

- Determine blur for 80% of most significant 32x32 blocks:

```
blurdetect=block_width=32:block_height=32:block_pct=80

```

### 39.17 bm3d# TOC

Denoise frames using Block-Matching 3D algorithm.

The filter accepts the following options.

sigma

Set denoising strength. Default value is 1. Allowed range is from 0 to 999.9. The denoising algorithm is very sensitive to sigma, so adjust it according to the source.

block

Set local patch size. This sets dimensions in 2D.

bstep

Set sliding step for processing blocks. Default value is 4. Allowed range is from 1 to 64. Smaller values allows processing more reference blocks and is slower.

group

Set maximal number of similar blocks for 3rd dimension. Default value is 1. When set to 1, no block matching is done. Larger values allows more blocks in single group. Allowed range is from 1 to 256.

range

Set radius for search block matching. Default is 9. Allowed range is from 1 to INT32_MAX.

mstep

Set step between two search locations for block matching. Default is 1. Allowed range is from 1 to 64. Smaller is slower.

thmse

Set threshold of mean square error for block matching. Valid range is 0 to INT32_MAX.

hdthr

Set thresholding parameter for hard thresholding in 3D transformed domain. Larger values results in stronger hard-thresholding filtering in frequency domain.

estim

Set filtering estimation mode. Can be basic or final. Default is basic.

ref

If enabled, filter will use 2nd stream for block matching. Default is disabled for basic value of estim option, and always enabled if value of estim is final.

planes

Set planes to filter. Default is all available except alpha.

#### 39.17.1 Examples# TOC

- Basic filtering with bm3d:

```
bm3d=sigma=3:block=4:bstep=2:group=1:estim=basic

```

- Same as above, but filtering only luma:

```
bm3d=sigma=3:block=4:bstep=2:group=1:estim=basic:planes=1

```

- Same as above, but with both estimation modes:

```
split[a][b],[a]bm3d=sigma=3:block=4:bstep=2:group=1:estim=basic[a],[b][a]bm3d=sigma=3:block=4:bstep=2:group=16:estim=final:ref=1

```

- Same as above, but prefilter with nlmeans filter instead:

```
split[a][b],[a]nlmeans=s=3:r=7:p=3[a],[b][a]bm3d=sigma=3:block=4:bstep=2:group=16:estim=final:ref=1

```

### 39.18 boxblur# TOC

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

#### 39.18.1 Examples# TOC

- Apply a boxblur filter with the luma, chroma, and alpha radii set to 2:

```
boxblur=luma_radius=2:luma_power=1
boxblur=2:1

```

- Set the luma radius to 2, and alpha and chroma radius to 0:

```
boxblur=2:1:cr=0:ar=0

```

- Set the luma and chroma radii to a fraction of the video dimension:

```
boxblur=luma_radius=min(h\,w)/10:luma_power=1:chroma_radius=min(cw\,ch)/10:chroma_power=1

```

### 39.19 bwdif# TOC

Deinterlace the input video ("bwdif" stands for "Bob Weaver Deinterlacing Filter").

Motion adaptive deinterlacing based on yadif with the use of w3fdif and cubic interpolation algorithms. It accepts the following parameters:

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

### 39.20 ccrepack# TOC

Repack CEA-708 closed captioning side data

This filter fixes various issues seen with commercial encoders related to upstream malformed CEA-708 payloads, specifically incorrect number of tuples (wrong cc_count for the target FPS), and incorrect ordering of tuples (i.e. the CEA-608 tuples are not at the first entries in the payload).

### 39.21 cas# TOC

Apply Contrast Adaptive Sharpen filter to video stream.

The filter accepts the following options:

strength

Set the sharpening strength. Default value is 0.

planes

Set planes to filter. Default value is to filter all planes except alpha plane.

#### 39.21.1 Commands# TOC

This filter supports same commands as options.

### 39.22 chromahold# TOC

Remove all color information for all colors except for certain one.

The filter accepts the following options:

color

The color which will not be replaced with neutral chroma.

similarity

Similarity percentage with the above color. 0.01 matches only the exact key color, while 1.0 matches everything.

blend

Blend percentage. 0.0 makes pixels either fully gray, or not gray at all. Higher values result in more preserved color.

yuv

Signals that the color passed is already in YUV instead of RGB.

Literal colors like "green" or "red" don’t make sense with this enabled anymore. This can be used to pass exact YUV values as hexadecimal numbers.

#### 39.22.1 Commands# TOC

This filter supports same commands as options. The command accepts the same syntax of the corresponding option.

If the specified expression is not valid, it is kept at its current value.

### 39.23 chromakey# TOC

YUV colorspace color/chroma keying.

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

yuv

Signals that the color passed is already in YUV instead of RGB.

Literal colors like "green" or "red" don’t make sense with this enabled anymore. This can be used to pass exact YUV values as hexadecimal numbers.

#### 39.23.1 Commands# TOC

This filter supports same commands as options. The command accepts the same syntax of the corresponding option.

If the specified expression is not valid, it is kept at its current value.

#### 39.23.2 Examples# TOC

- Make every green pixel in the input image transparent:

```
ffmpeg -i input.png -vf chromakey=green out.png

```

- Overlay a greenscreen-video on top of a static black background.

```
ffmpeg -f lavfi -i color=c=black:s=1280x720 -i video.mp4 -shortest -filter_complex "[1:v]chromakey=0x70de77:0.1:0.2[ckout];[0:v][ckout]overlay[out]" -map "[out]" output.mkv

```

### 39.24 chromanr# TOC

Reduce chrominance noise.

The filter accepts the following options:

thres

Set threshold for averaging chrominance values. Sum of absolute difference of Y, U and V pixel components of current pixel and neighbour pixels lower than this threshold will be used in averaging. Luma component is left unchanged and is copied to output. Default value is 30. Allowed range is from 1 to 200.

sizew

Set horizontal radius of rectangle used for averaging. Allowed range is from 1 to 100. Default value is 5.

sizeh

Set vertical radius of rectangle used for averaging. Allowed range is from 1 to 100. Default value is 5.

stepw

Set horizontal step when averaging. Default value is 1. Allowed range is from 1 to 50. Mostly useful to speed-up filtering.

steph

Set vertical step when averaging. Default value is 1. Allowed range is from 1 to 50. Mostly useful to speed-up filtering.

threy

Set Y threshold for averaging chrominance values. Set finer control for max allowed difference between Y components of current pixel and neighbour pixels. Default value is 200. Allowed range is from 1 to 200.

threu

Set U threshold for averaging chrominance values. Set finer control for max allowed difference between U components of current pixel and neighbour pixels. Default value is 200. Allowed range is from 1 to 200.

threv

Set V threshold for averaging chrominance values. Set finer control for max allowed difference between V components of current pixel and neighbour pixels. Default value is 200. Allowed range is from 1 to 200.

distance

Set distance type used in calculations.

‘manhattan’

Absolute difference.

‘euclidean’

Difference squared.

Default distance type is manhattan.

#### 39.24.1 Commands# TOC

This filter supports same commands as options. The command accepts the same syntax of the corresponding option.

### 39.25 chromashift# TOC

Shift chroma pixels horizontally and/or vertically.

The filter accepts the following options:

cbh

Set amount to shift chroma-blue horizontally.

cbv

Set amount to shift chroma-blue vertically.

crh

Set amount to shift chroma-red horizontally.

crv

Set amount to shift chroma-red vertically.

edge

Set edge mode, can be smear, default, or warp.

#### 39.25.1 Commands# TOC

This filter supports the all above options as commands.

### 39.26 ciescope# TOC

Display CIE color diagram with pixels overlaid onto it.

The filter accepts the following options:

system

Set color system.

‘ntsc, 470m’

‘ebu, 470bg’

‘smpte’

‘240m’

‘apple’

‘widergb’

‘cie1931’

‘rec709, hdtv’

‘uhdtv, rec2020’

‘dcip3’

cie

Set CIE system.

‘xyy’

‘ucs’

‘luv’

gamuts

Set what gamuts to draw.

See system option for available values.

size, s

Set ciescope size, by default set to 512.

intensity, i

Set intensity used to map input pixel values to CIE diagram.

contrast

Set contrast used to draw tongue colors that are out of active color system gamut.

corrgamma

Correct gamma displayed on scope, by default enabled.

showwhite

Show white point on CIE diagram, by default disabled.

gamma

Set input gamma. Used only with XYZ input color space.

fill

Fill with CIE colors. By default is enabled.

### 39.27 codecview# TOC

Visualize information exported by some codecs.

Some codecs can export information through frames using side-data or other means. For example, some MPEG based codecs export motion vectors through the export_mvs flag in the codec flags2 option.

The filter accepts the following option:

block

Display block partition structure using the luma plane.

mv

Set motion vectors to visualize.

Available flags for mv are:

‘pf’

forward predicted MVs of P-frames

‘bf’

forward predicted MVs of B-frames

‘bb’

backward predicted MVs of B-frames

qp

Display quantization parameters using the chroma planes.

mv_type, mvt

Set motion vectors type to visualize. Includes MVs from all frames unless specified by frame_type option.

Available flags for mv_type are:

‘fp’

forward predicted MVs

‘bp’

backward predicted MVs

frame_type, ft

Set frame type to visualize motion vectors of.

Available flags for frame_type are:

‘if’

intra-coded frames (I-frames)

‘pf’

predicted frames (P-frames)

‘bf’

bi-directionally predicted frames (B-frames)

#### 39.27.1 Examples# TOC

- Visualize forward predicted MVs of all frames using ffplay:

```
ffplay -flags2 +export_mvs input.mp4 -vf codecview=mv_type=fp

```

- Visualize multi-directionals MVs of P and B-Frames using ffplay:

```
ffplay -flags2 +export_mvs input.mp4 -vf codecview=mv=pf+bf+bb

```

### 39.28 colorbalance# TOC

Modify intensity of primary colors (red, green and blue) of input frames.

The filter allows an input frame to be adjusted in the shadows, midtones or highlights regions for the red-cyan, green-magenta or blue-yellow balance.

A positive adjustment value shifts the balance towards the primary color, a negative value towards the complementary color.

The filter accepts the following options:

rs

gs

bs

Adjust red, green and blue shadows (darkest pixels).

rm

gm

bm

Adjust red, green and blue midtones (medium pixels).

rh

gh

bh

Adjust red, green and blue highlights (brightest pixels).

Allowed ranges for options are [-1.0, 1.0]. Defaults are 0.

pl

Preserve lightness when changing color balance. Default is disabled.

#### 39.28.1 Examples# TOC

- Add red color cast to shadows:

```
colorbalance=rs=.3

```

#### 39.28.2 Commands# TOC

This filter supports the all above options as commands.

### 39.29 colorcontrast# TOC

Adjust color contrast between RGB components.

The filter accepts the following options:

rc

Set the red-cyan contrast. Defaults is 0.0. Allowed range is from -1.0 to 1.0.

gm

Set the green-magenta contrast. Defaults is 0.0. Allowed range is from -1.0 to 1.0.

by

Set the blue-yellow contrast. Defaults is 0.0. Allowed range is from -1.0 to 1.0.

rcw

gmw

byw

Set the weight of each rc, gm, by option value. Default value is 0.0. Allowed range is from 0.0 to 1.0. If all weights are 0.0 filtering is disabled.

pl

Set the amount of preserving lightness. Default value is 0.0. Allowed range is from 0.0 to 1.0.

#### 39.29.1 Commands# TOC

This filter supports the all above options as commands.

### 39.30 colorcorrect# TOC

Adjust color white balance selectively for blacks and whites. This filter operates in YUV colorspace.

The filter accepts the following options:

rl

Set the red shadow spot. Allowed range is from -1.0 to 1.0. Default value is 0.

bl

Set the blue shadow spot. Allowed range is from -1.0 to 1.0. Default value is 0.

rh

Set the red highlight spot. Allowed range is from -1.0 to 1.0. Default value is 0.

bh

Set the blue highlight spot. Allowed range is from -1.0 to 1.0. Default value is 0.

saturation

Set the amount of saturation. Allowed range is from -3.0 to 3.0. Default value is 1.

analyze

If set to anything other than manual it will analyze every frame and use derived parameters for filtering output frame.

Possible values are:

‘manual’

‘average’

‘minmax’

‘median’

Default value is manual.

#### 39.30.1 Commands# TOC

This filter supports the all above options as commands.

### 39.31 colorchannelmixer# TOC

Adjust video input frames by re-mixing color channels.

This filter modifies a color channel by adding the values associated to the other channels of the same pixels. For example if the value to modify is red, the output value will be:

```
red=red*rr + blue*rb + green*rg + alpha*ra

```

The filter accepts the following options:

rr

rg

rb

ra

Adjust contribution of input red, green, blue and alpha channels for output red channel. Default is 1 for rr, and 0 for rg, rb and ra.

gr

gg

gb

ga

Adjust contribution of input red, green, blue and alpha channels for output green channel. Default is 1 for gg, and 0 for gr, gb and ga.

br

bg

bb

ba

Adjust contribution of input red, green, blue and alpha channels for output blue channel. Default is 1 for bb, and 0 for br, bg and ba.

ar

ag

ab

aa

Adjust contribution of input red, green, blue and alpha channels for output alpha channel. Default is 1 for aa, and 0 for ar, ag and ab.

Allowed ranges for options are [-2.0, 2.0].

pc

Set preserve color mode. The accepted values are:

‘none’

Disable color preserving, this is default.

‘lum’

Preserve luminance.

‘max’

Preserve max value of RGB triplet.

‘avg’

Preserve average value of RGB triplet.

‘sum’

Preserve sum value of RGB triplet.

‘nrm’

Preserve normalized value of RGB triplet.

‘pwr’

Preserve power value of RGB triplet.

pa

Set the preserve color amount when changing colors. Allowed range is from [0.0, 1.0]. Default is 0.0, thus disabled.

#### 39.31.1 Examples# TOC

- Convert source to grayscale:

```
colorchannelmixer=.3:.4:.3:0:.3:.4:.3:0:.3:.4:.3

```

- Simulate sepia tones:

```
colorchannelmixer=.393:.769:.189:0:.349:.686:.168:0:.272:.534:.131

```

#### 39.31.2 Commands# TOC

This filter supports the all above options as commands.

### 39.32 colordetect# TOC

Analyze the video frames to determine the effective value range and alpha mode.

The filter accepts the following options:

mode

Set of properties to detect. Unavailable properties, such as alpha mode for an input image without an alpha channel, will be ignored automatically.

Accepts a combination of the following flags:

‘color_range’

Detect if the source contains luma pixels outside the limited (MPEG) range, which indicates that this is a full range YUV source.

‘alpha_mode’

Detect if the source contains color values above the alpha channel, which indicates that the alpha channel is independent (straight), rather than premultiplied. Also detects if the alpha plane is fully opaque or not.

‘all’

Enable detection of all of the above properties. This is the default.

threshold

Allow pixels to exceed the expected bounds by this fraction of the full scale value range before treating it as evidence of (respectively) full range or straight alpha. Value range is from 0 to 0.05. Defaults to 0.001 (=0.1%).

### 39.33 colorize# TOC

Overlay a solid color on the video stream.

The filter accepts the following options:

hue

Set the color hue. Allowed range is from 0 to 360. Default value is 0.

saturation

Set the color saturation. Allowed range is from 0 to 1. Default value is 0.5.

lightness

Set the color lightness. Allowed range is from 0 to 1. Default value is 0.5.

mix

Set the mix of source lightness. By default is set to 1.0. Allowed range is from 0.0 to 1.0.

#### 39.33.1 Commands# TOC

This filter supports the all above options as commands.

### 39.34 colorkey# TOC

RGB colorspace color keying. This filter operates on 8-bit RGB format frames by setting the alpha component of each pixel which falls within the similarity radius of the key color to 0. The alpha value for pixels outside the similarity radius depends on the value of the blend option.

The filter accepts the following options:

color

Set the color for which alpha will be set to 0 (full transparency). See "Color" section in the ffmpeg-utils manual. Default is black.

similarity

Set the radius from the key color within which other colors also have full transparency. The computed distance is related to the unit fractional distance in 3D space between the RGB values of the key color and the pixel’s color. Range is 0.01 to 1.0. 0.01 matches within a very small radius around the exact key color, while 1.0 matches everything. Default is 0.01.

blend

Set how the alpha value for pixels that fall outside the similarity radius is computed. 0.0 makes pixels either fully transparent or fully opaque. Higher values result in semi-transparent pixels, with greater transparency the more similar the pixel color is to the key color. Range is 0.0 to 1.0. Default is 0.0.

#### 39.34.1 Examples# TOC

- Make every green pixel in the input image transparent:

```
ffmpeg -i input.png -vf colorkey=green out.png

```

- Overlay a greenscreen-video on top of a static background image.

```
ffmpeg -i background.png -i video.mp4 -filter_complex "[1:v]colorkey=0x3BBD1E:0.3:0.2[ckout];[0:v][ckout]overlay[out]" -map "[out]" output.flv

```

#### 39.34.2 Commands# TOC

This filter supports same commands as options. The command accepts the same syntax of the corresponding option.

If the specified expression is not valid, it is kept at its current value.

### 39.35 colorhold# TOC

Remove all color information for all RGB colors except for certain one.

The filter accepts the following options:

color

The color which will not be replaced with neutral gray.

similarity

Similarity percentage with the above color. 0.01 matches only the exact key color, while 1.0 matches everything.

blend

Blend percentage. 0.0 makes pixels fully gray. Higher values result in more preserved color.

#### 39.35.1 Commands# TOC

This filter supports same commands as options. The command accepts the same syntax of the corresponding option.

If the specified expression is not valid, it is kept at its current value.

### 39.36 colorlevels# TOC

Adjust video input frames using levels.

The filter accepts the following options:

rimin

gimin

bimin

aimin

Adjust red, green, blue and alpha input black point. Allowed ranges for options are [-1.0, 1.0]. Defaults are 0.

rimax

gimax

bimax

aimax

Adjust red, green, blue and alpha input white point. Allowed ranges for options are [-1.0, 1.0]. Defaults are 1.

Input levels are used to lighten highlights (bright tones), darken shadows (dark tones), change the balance of bright and dark tones.

romin

gomin

bomin

aomin

Adjust red, green, blue and alpha output black point. Allowed ranges for options are [0, 1.0]. Defaults are 0.

romax

gomax

bomax

aomax

Adjust red, green, blue and alpha output white point. Allowed ranges for options are [0, 1.0]. Defaults are 1.

Output levels allows manual selection of a constrained output level range.

preserve

Set preserve color mode. The accepted values are:

‘none’

Disable color preserving, this is default.

‘lum’

Preserve luminance.

‘max’

Preserve max value of RGB triplet.

‘avg’

Preserve average value of RGB triplet.

‘sum’

Preserve sum value of RGB triplet.

‘nrm’

Preserve normalized value of RGB triplet.

‘pwr’

Preserve power value of RGB triplet.

#### 39.36.1 Examples# TOC

- Make video output darker:

```
colorlevels=rimin=0.058:gimin=0.058:bimin=0.058

```

- Increase contrast:

```
colorlevels=rimin=0.039:gimin=0.039:bimin=0.039:rimax=0.96:gimax=0.96:bimax=0.96

```

- Make video output lighter:

```
colorlevels=rimax=0.902:gimax=0.902:bimax=0.902

```

- Increase brightness:

```
colorlevels=romin=0.5:gomin=0.5:bomin=0.5

```

#### 39.36.2 Commands# TOC

This filter supports the all above options as commands.

### 39.37 colormap# TOC

Apply custom color maps to video stream.

This filter needs three input video streams. First stream is video stream that is going to be filtered out. Second and third video stream specify color patches for source color to target color mapping.

The filter accepts the following options:

patch_size

Set the source and target video stream patch size in pixels.

nb_patches

Set the max number of used patches from source and target video stream. Default value is number of patches available in additional video streams. Max allowed number of patches is 64.

type

Set the adjustments used for target colors. Can be relative or absolute. Defaults is absolute.

kernel

Set the kernel used to measure color differences between mapped colors.

The accepted values are:

‘euclidean’

‘weuclidean’

Default is euclidean.

### 39.38 colormatrix# TOC

Convert color matrix.

The filter accepts the following options:

src

dst

Specify the source and destination color matrix. Both values must be specified.

The accepted values are:

‘bt709’

BT.709

‘fcc’

FCC

‘bt601’

BT.601

‘bt470’

BT.470

‘bt470bg’

BT.470BG

‘smpte170m’

SMPTE-170M

‘smpte240m’

SMPTE-240M

‘bt2020’

BT.2020

For example to convert from BT.601 to SMPTE-240M, use the command:

```
colormatrix=bt601:smpte240m

```

### 39.39 colorspace# TOC

Convert colorspace, transfer characteristics or color primaries. Input video needs to have an even size.

The filter accepts the following options:

all

Specify all color properties at once.

The accepted values are:

‘bt470m’

BT.470M

‘bt470bg’

BT.470BG

‘bt601-6-525’

BT.601-6 525

‘bt601-6-625’

BT.601-6 625

‘bt709’

BT.709

‘smpte170m’

SMPTE-170M

‘smpte240m’

SMPTE-240M

‘bt2020’

BT.2020

space

Specify output colorspace.

The accepted values are:

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

‘ycgco’

YCgCo

‘bt2020ncl’

BT.2020 with non-constant luminance

trc

Specify output transfer characteristics.

The accepted values are:

‘bt709’

BT.709

‘bt470m’

BT.470M

‘bt470bg’

BT.470BG

‘gamma22’

Constant gamma of 2.2

‘gamma28’

Constant gamma of 2.8

‘smpte170m’

SMPTE-170M, BT.601-6 625 or BT.601-6 525

‘smpte240m’

SMPTE-240M

‘srgb’

SRGB

‘iec61966-2-1’

iec61966-2-1

‘iec61966-2-4’

iec61966-2-4

‘xvycc’

xvycc

‘bt2020-10’

BT.2020 for 10-bits content

‘bt2020-12’

BT.2020 for 12-bits content

primaries

Specify output color primaries.

The accepted values are:

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

‘smpte431’

SMPTE-431

‘smpte432’

SMPTE-432

‘bt2020’

BT.2020

‘jedec-p22’

JEDEC P22 phosphors

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

format

Specify output color format.

The accepted values are:

‘yuv420p’

YUV 4:2:0 planar 8-bits

‘yuv420p10’

YUV 4:2:0 planar 10-bits

‘yuv420p12’

YUV 4:2:0 planar 12-bits

‘yuv422p’

YUV 4:2:2 planar 8-bits

‘yuv422p10’

YUV 4:2:2 planar 10-bits

‘yuv422p12’

YUV 4:2:2 planar 12-bits

‘yuv444p’

YUV 4:4:4 planar 8-bits

‘yuv444p10’

YUV 4:4:4 planar 10-bits

‘yuv444p12’

YUV 4:4:4 planar 12-bits

fast

Do a fast conversion, which skips gamma/primary correction. This will take significantly less CPU, but will be mathematically incorrect. To get output compatible with that produced by the colormatrix filter, use fast=1.

dither

Specify dithering mode.

The accepted values are:

‘none’

No dithering

‘fsb’

Floyd-Steinberg dithering

wpadapt

Whitepoint adaptation mode.

The accepted values are:

‘bradford’

Bradford whitepoint adaptation

‘vonkries’

von Kries whitepoint adaptation

‘identity’

identity whitepoint adaptation (i.e. no whitepoint adaptation)

clipgamut

Controls how to clip out-of-gamut colors that arise as a result of colorspace conversion.

The accepted values are:

‘none’

No clipping of out of gamut colors.

‘rgb’

Clips the RGB values to the [0, 1] range when building the gamma transfer LUTs.

iall

Override all input properties at once. Same accepted values as all.

ispace

Override input colorspace. Same accepted values as space.

iprimaries

Override input color primaries. Same accepted values as primaries.

itrc

Override input transfer characteristics. Same accepted values as trc.

irange

Override input color range. Same accepted values as range.

The filter converts the transfer characteristics, color space and color primaries to the specified user values. The output value, if not specified, is set to a default value based on the "all" property. If that property is also not specified, the filter will log an error. The output color range and format default to the same value as the input color range and format. The input transfer characteristics, color space, color primaries and color range should be set on the input data. If any of these are missing, the filter will log an error and no conversion will take place.

For example to convert the input to SMPTE-240M, use the command:

```
colorspace=smpte240m

```

### 39.40 colortemperature# TOC

Adjust color temperature in video to simulate variations in ambient color temperature.

The filter accepts the following options:

temperature

Set the temperature in Kelvin. Allowed range is from 1000 to 40000. Default value is 6500 K.

mix

Set mixing with filtered output. Allowed range is from 0 to 1. Default value is 1.

pl

Set the amount of preserving lightness. Allowed range is from 0 to 1. Default value is 0.

#### 39.40.1 Commands# TOC

This filter supports same commands as options.

### 39.41 convolution# TOC

Apply convolution of 3x3, 5x5, 7x7 or horizontal/vertical up to 49 elements.

The filter accepts the following options:

0m

1m

2m

3m

Set matrix for each plane. Matrix is sequence of 9, 25 or 49 signed integers in square mode, and from 1 to 49 odd number of signed integers in row mode.

0rdiv

1rdiv

2rdiv

3rdiv

Set multiplier for calculated value for each plane. If unset or 0, it will be 1/sum of all matrix elements.

0bias

1bias

2bias

3bias

Set bias for each plane. This value is added to the result of the multiplication. Useful for making the overall image brighter or darker. Default is 0.0.

0mode

1mode

2mode

3mode

Set matrix mode for each plane. Can be square, row or column. Default is square.

#### 39.41.1 Commands# TOC

This filter supports the all above options as commands.

#### 39.41.2 Examples# TOC

- Apply sharpen:

```
convolution="0 -1 0 -1 5 -1 0 -1 0:0 -1 0 -1 5 -1 0 -1 0:0 -1 0 -1 5 -1 0 -1 0:0 -1 0 -1 5 -1 0 -1 0"

```

- Apply blur:

```
convolution="1 1 1 1 1 1 1 1 1:1 1 1 1 1 1 1 1 1:1 1 1 1 1 1 1 1 1:1 1 1 1 1 1 1 1 1:1/9:1/9:1/9:1/9"

```

- Apply edge enhance:

```
convolution="0 0 0 -1 1 0 0 0 0:0 0 0 -1 1 0 0 0 0:0 0 0 -1 1 0 0 0 0:0 0 0 -1 1 0 0 0 0:5:1:1:1:0:128:128:128"

```

- Apply edge detect:

```
convolution="0 1 0 1 -4 1 0 1 0:0 1 0 1 -4 1 0 1 0:0 1 0 1 -4 1 0 1 0:0 1 0 1 -4 1 0 1 0:5:5:5:1:0:128:128:128"

```

- Apply laplacian edge detector which includes diagonals:

```
convolution="1 1 1 1 -8 1 1 1 1:1 1 1 1 -8 1 1 1 1:1 1 1 1 -8 1 1 1 1:1 1 1 1 -8 1 1 1 1:5:5:5:1:0:128:128:0"

```

- Apply emboss:

```
convolution="-2 -1 0 -1 1 1 0 1 2:-2 -1 0 -1 1 1 0 1 2:-2 -1 0 -1 1 1 0 1 2:-2 -1 0 -1 1 1 0 1 2"

```

### 39.42 convolve# TOC

Apply 2D convolution of video stream in frequency domain using second stream as impulse.

The filter accepts the following options:

planes

Set which planes to process.

impulse

Set which impulse video frames will be processed, can be first or all. Default is all.

The convolve filter also supports the framesync options.

### 39.43 copy# TOC

Copy the input video source unchanged to the output. This is mainly useful for testing purposes.

### 39.44 coreimage# TOC

Video filtering on GPU using Apple’s CoreImage API on OSX.

Hardware acceleration is based on an OpenGL context. Usually, this means it is processed by video hardware. However, software-based OpenGL implementations exist which means there is no guarantee for hardware processing. It depends on the respective OSX.

There are many filters and image generators provided by Apple that come with a large variety of options. The filter has to be referenced by its name along with its options.

The coreimage filter accepts the following options:

list_filters

List all available filters and generators along with all their respective options as well as possible minimum and maximum values along with the default values.

```
list_filters=true

```

filter

Specify all filters by their respective name and options. Use list_filters to determine all valid filter names and options. Numerical options are specified by a float value and are automatically clamped to their respective value range. Vector and color options have to be specified by a list of space separated float values. Character escaping has to be done. A special option name default is available to use default options for a filter.

It is required to specify either default or at least one of the filter options. All omitted options are used with their default values. The syntax of the filter string is as follows:

```
filter=<NAME>@<OPTION>=<VALUE>[@<OPTION>=<VALUE>][@...][#<NAME>@<OPTION>=<VALUE>[@<OPTION>=<VALUE>][@...]][#...]

```

output_rect

Specify a rectangle where the output of the filter chain is copied into the input image. It is given by a list of space separated float values:

```
output_rect=x\ y\ width\ height

```

If not given, the output rectangle equals the dimensions of the input image. The output rectangle is automatically cropped at the borders of the input image. Negative values are valid for each component.

```
output_rect=25\ 25\ 100\ 100

```

Several filters can be chained for successive processing without GPU-HOST transfers allowing for fast processing of complex filter chains. Currently, only filters with zero (generators) or exactly one (filters) input image and one output image are supported. Also, transition filters are not yet usable as intended.

Some filters generate output images with additional padding depending on the respective filter kernel. The padding is automatically removed to ensure the filter output has the same size as the input image.

For image generators, the size of the output image is determined by the previous output image of the filter chain or the input image of the whole filterchain, respectively. The generators do not use the pixel information of this image to generate their output. However, the generated output is blended onto this image, resulting in partial or complete coverage of the output image.

The coreimagesrc video source can be used for generating input images which are directly fed into the filter chain. By using it, providing input images by another video source or an input video is not required.

#### 39.44.1 Examples# TOC

- List all filters available:

```
coreimage=list_filters=true

```

- Use the CIBoxBlur filter with default options to blur an image:

```
coreimage=filter=CIBoxBlur@default

```

- Use a filter chain with CISepiaTone at default values and CIVignetteEffect with its center at 100x100 and a radius of 50 pixels:

```
coreimage=filter=CIBoxBlur@default#CIVignetteEffect@inputCenter=100\ 100@inputRadius=50

```

- Use nullsrc and CIQRCodeGenerator to create a QR code for the FFmpeg homepage, given as complete and escaped command-line for Apple’s standard bash shell:

```
ffmpeg -f lavfi -i nullsrc=s=100x100,coreimage=filter=CIQRCodeGenerator@inputMessage=https\\\\\://FFmpeg.org/@inputCorrectionLevel=H -frames:v 1 QRCode.png

```

### 39.45 corr# TOC

Obtain the correlation between two input videos.

This filter takes two input videos.

Both input videos must have the same resolution and pixel format for this filter to work correctly. Also it assumes that both inputs have the same number of frames, which are compared one by one.

The obtained per component, average, min and max correlation is printed through the logging system.

The filter stores the calculated correlation of each frame in frame metadata.

This filter also supports the framesync options.

In the below example the input file main.mpg being processed is compared with the reference file ref.mpg.

```
ffmpeg -i main.mpg -i ref.mpg -lavfi corr -f null -

```

### 39.46 cover_rect# TOC

Cover a rectangular object

It accepts the following options:

cover

Filepath of the optional cover image, needs to be in yuv420.

mode

Set covering mode.

It accepts the following values:

‘cover’

cover it by the supplied image

‘blur’

cover it by interpolating the surrounding pixels

Default value is blur.

#### 39.46.1 Examples# TOC

- Cover a rectangular object by the supplied image of a given video using ffmpeg:

```
ffmpeg -i file.ts -vf find_rect=newref.pgm,cover_rect=cover.jpg:mode=cover new.mkv

```

### 39.47 crop# TOC

Crop the input video to given dimensions.

It accepts the following parameters:

w, out_w

The width of the output video. It defaults to iw. This expression is evaluated during the filter configuration, when the ‘w’ or ‘out_w’ command is sent, or when the input frame size changes.

h, out_h

The height of the output video. It defaults to ih. This expression is evaluated during the filter configuration, when the ‘h’ or ‘out_h’ command is sent, or when the input frame size changes.

x

The horizontal position, in the input video, of the left edge of the output video. It defaults to (in_w-out_w)/2. This expression is evaluated per-frame.

y

The vertical position, in the input video, of the top edge of the output video. It defaults to (in_h-out_h)/2. This expression is evaluated per-frame.

keep_aspect

If set to 1 will force the output display aspect ratio to be the same of the input, by changing the output sample aspect ratio. It defaults to 0.

exact

Enable exact cropping. If enabled, subsampled videos will be cropped at exact width/height/x/y as specified and will not be rounded to nearest smaller value. It defaults to 0.

The out_w, out_h, x, y parameters are expressions containing the following constants:

x

y

The computed values for x and y. They are evaluated for each new frame.

in_w

in_h

The input width and height.

iw

ih

These are the same as in_w and in_h.

out_w

out_h

The output (cropped) width and height.

ow

oh

These are the same as out_w and out_h.

a

same as iw / ih

sar

input sample aspect ratio

dar

input display aspect ratio, it is the same as (iw / ih) * sar

hsub

vsub

horizontal and vertical chroma subsample values. For example for the pixel format "yuv422p" hsub is 2 and vsub is 1.

n

The number of the input frame, starting from 0.

pos

the position in the file of the input frame, NAN if unknown; deprecated, do not use

t

The timestamp expressed in seconds. It’s NAN if the input timestamp is unknown.

The expression for out_w may depend on the value of out_h, and the expression for out_h may depend on out_w, but they cannot depend on x and y, as x and y are evaluated after out_w and out_h.

The x and y parameters specify the expressions for the position of the top-left corner of the output (non-cropped) area. They are evaluated for each frame. If the evaluated value is not valid, it is approximated to the nearest valid value.

The expression for x may depend on y, and the expression for y may depend on x.

#### 39.47.1 Examples# TOC

- Crop area with size 100x100 at position (12,34).

```
crop=100:100:12:34

```

Using named options, the example above becomes:

```
crop=w=100:h=100:x=12:y=34

```

- Crop the central input area with size 100x100:

```
crop=100:100

```

- Crop the central input area with size 2/3 of the input video:

```
crop=2/3*in_w:2/3*in_h

```

- Crop the input video central square:

```
crop=out_w=in_h
crop=in_h

```

- Delimit the rectangle with the top-left corner placed at position 100:100 and the right-bottom corner corresponding to the right-bottom corner of the input image.

```
crop=in_w-100:in_h-100:100:100

```

- Crop 10 pixels from the left and right borders, and 20 pixels from the top and bottom borders

```
crop=in_w-2*10:in_h-2*20

```

- Keep only the bottom right quarter of the input image:

```
crop=in_w/2:in_h/2:in_w/2:in_h/2

```

- Crop height for getting Greek harmony:

```
crop=in_w:1/PHI*in_w

```

- Apply trembling effect:

```
crop=in_w/2:in_h/2:(in_w-out_w)/2+((in_w-out_w)/2)*sin(n/10):(in_h-out_h)/2 +((in_h-out_h)/2)*sin(n/7)

```

- Apply erratic camera effect depending on timestamp:

```
crop=in_w/2:in_h/2:(in_w-out_w)/2+((in_w-out_w)/2)*sin(t*10):(in_h-out_h)/2 +((in_h-out_h)/2)*sin(t*13)

```

- Set x depending on the value of y:

```
crop=in_w/2:in_h/2:y:10+10*sin(n/10)

```

#### 39.47.2 Commands# TOC

This filter supports the following commands:

w, out_w

h, out_h

x

y

Set width/height of the output video and the horizontal/vertical position in the input video. The command accepts the same syntax of the corresponding option.

If the specified expression is not valid, it is kept at its current value.

### 39.48 cropdetect# TOC

Auto-detect the crop size.

It calculates the necessary cropping parameters and prints the recommended parameters via the logging system. The detected dimensions correspond to the non-black or video area of the input video according to mode.

It accepts the following parameters:

mode

Depending on mode crop detection is based on either the mere black value of surrounding pixels or a combination of motion vectors and edge pixels.

‘black’

Detect black pixels surrounding the playing video. For fine control use option limit.

‘mvedges’

Detect the playing video by the motion vectors inside the video and scanning for edge pixels typically forming the border of a playing video.

limit

Set higher black value threshold, which can be optionally specified from nothing (0) to everything (255 for 8-bit based formats). An intensity value greater to the set value is considered non-black. It defaults to 24. You can also specify a value between 0.0 and 1.0 which will be scaled depending on the bitdepth of the pixel format.

round

The value which the width/height should be divisible by. It defaults to 16. The offset is automatically adjusted to center the video. Use 2 to get only even dimensions (needed for 4:2:2 video). 16 is best when encoding to most video codecs.

skip

Set the number of initial frames for which evaluation is skipped. Default is 2. Range is 0 to INT_MAX.

reset_count, reset

Set the counter that determines after how many frames cropdetect will reset the previously detected largest video area and start over to detect the current optimal crop area. Default value is 0.

This can be useful when channel logos distort the video area. 0 indicates ’never reset’, and returns the largest area encountered during playback.

mv_threshold

Set motion in pixel units as threshold for motion detection. It defaults to 8.

low

high

Set low and high threshold values used by the Canny thresholding algorithm.

The high threshold selects the "strong" edge pixels, which are then connected through 8-connectivity with the "weak" edge pixels selected by the low threshold.

low and high threshold values must be chosen in the range [0,1], and low should be lesser or equal to high.

Default value for low is 5/255, and default value for high is 15/255.

#### 39.48.1 Examples# TOC

- Find video area surrounded by black borders:

```
ffmpeg -i file.mp4 -vf cropdetect,metadata=mode=print -f null -

```

- Find an embedded video area, generate motion vectors beforehand:

```
ffmpeg -i file.mp4 -vf mestimate,cropdetect=mode=mvedges,metadata=mode=print -f null -

```

- Find an embedded video area, use motion vectors from decoder:

```
ffmpeg -flags2 +export_mvs -i file.mp4 -vf cropdetect=mode=mvedges,metadata=mode=print -f null -

```

#### 39.48.2 Commands# TOC

This filter supports the following commands:

limit

The command accepts the same syntax of the corresponding option. If the specified expression is not valid, it is kept at its current value.

### 39.49 cue# TOC

Delay video filtering until a given wallclock timestamp. The filter first passes on preroll amount of frames, then it buffers at most buffer amount of frames and waits for the cue. After reaching the cue it forwards the buffered frames and also any subsequent frames coming in its input.

The filter can be used synchronize the output of multiple ffmpeg processes for realtime output devices like decklink. By putting the delay in the filtering chain and pre-buffering frames the process can pass on data to output almost immediately after the target wallclock timestamp is reached.

Perfect frame accuracy cannot be guaranteed, but the result is good enough for some use cases.

cue

The cue timestamp expressed in a UNIX timestamp in microseconds. Default is 0.

preroll

The duration of content to pass on as preroll expressed in seconds. Default is 0.

buffer

The maximum duration of content to buffer before waiting for the cue expressed in seconds. Default is 0.

### 39.50 curves# TOC

Apply color adjustments using curves.

This filter is similar to the Adobe Photoshop and GIMP curves tools. Each component (red, green and blue) has its values defined by N key points tied from each other using a smooth curve. The x-axis represents the pixel values from the input frame, and the y-axis the new pixel values to be set for the output frame.

By default, a component curve is defined by the two points (0;0) and (1;1). This creates a straight line where each original pixel value is "adjusted" to its own value, which means no change to the image.

The filter allows you to redefine these two points and add some more. A new curve will be defined to pass smoothly through all these new coordinates. The new defined points need to be strictly increasing over the x-axis, and their x and y values must be in the [0;1] interval. The curve is formed by using a natural or monotonic cubic spline interpolation, depending on the interp option (default: natural). The natural spline produces a smoother curve in general while the monotonic (pchip) spline guarantees the transitions between the specified points to be monotonic. If the computed curves happened to go outside the vector spaces, the values will be clipped accordingly.

The filter accepts the following options:

preset

Select one of the available color presets. This option can be used in addition to the r, g, b parameters; in this case, the later options takes priority on the preset values. Available presets are:

‘none’

‘color_negative’

‘cross_process’

‘darker’

‘increase_contrast’

‘lighter’

‘linear_contrast’

‘medium_contrast’

‘negative’

‘strong_contrast’

‘vintage’

Default is none.

master, m

Set the master key points. These points will define a second pass mapping. It is sometimes called a "luminance" or "value" mapping. It can be used with r, g, b or all since it acts like a post-processing LUT.

red, r

Set the key points for the red component.

green, g

Set the key points for the green component.

blue, b

Set the key points for the blue component.

all

Set the key points for all components (not including master). Can be used in addition to the other key points component options. In this case, the unset component(s) will fallback on this all setting.

psfile

Specify a Photoshop curves file (.acv) to import the settings from.

plot

Save Gnuplot script of the curves in specified file.

interp

Specify the kind of interpolation. Available algorithms are:

‘natural’

Natural cubic spline using a piece-wise cubic polynomial that is twice continuously differentiable.

‘pchip’

Monotonic cubic spline using a piecewise cubic Hermite interpolating polynomial (PCHIP).

To avoid some filtergraph syntax conflicts, each key points list need to be defined using the following syntax: x0/y0 x1/y1 x2/y2 ....

#### 39.50.1 Commands# TOC

This filter supports same commands as options.

#### 39.50.2 Examples# TOC

- Increase slightly the middle level of blue:

```
curves=blue='0/0 0.5/0.58 1/1'

```

- Vintage effect:

```
curves=r='0/0.11 .42/.51 1/0.95':g='0/0 0.50/0.48 1/1':b='0/0.22 .49/.44 1/0.8'

```

Here we obtain the following coordinates for each components:

red

(0;0.11) (0.42;0.51) (1;0.95)

green

(0;0) (0.50;0.48) (1;1)

blue

(0;0.22) (0.49;0.44) (1;0.80)

- The previous example can also be achieved with the associated built-in preset:

```
curves=preset=vintage

```

- Or simply:

```
curves=vintage

```

- Use a Photoshop preset and redefine the points of the green component:

```
curves=psfile='MyCurvesPresets/purple.acv':green='0/0 0.45/0.53 1/1'

```

- Check out the curves of the cross_process profile using ffmpeg and gnuplot:

```
ffmpeg -f lavfi -i color -vf curves=cross_process:plot=/tmp/curves.plt -frames:v 1 -f null -
gnuplot -p /tmp/curves.plt

```

### 39.51 datascope# TOC

Video data analysis filter.

This filter shows hexadecimal pixel values of part of video.

The filter accepts the following options:

size, s

Set output video size.

x

Set x offset from where to pick pixels.

y

Set y offset from where to pick pixels.

mode

Set scope mode, can be one of the following:

‘mono’

Draw hexadecimal pixel values with white color on black background.

‘color’

Draw hexadecimal pixel values with input video pixel color on black background.

‘color2’

Draw hexadecimal pixel values on color background picked from input video, the text color is picked in such way so its always visible.

axis

Draw rows and columns numbers on left and top of video.

opacity

Set background opacity.

format

Set display number format. Can be hex, or dec. Default is hex.

components

Set pixel components to display. By default all pixel components are displayed.

#### 39.51.1 Commands# TOC

This filter supports same commands as options excluding size option.

### 39.52 dblur# TOC

Apply Directional blur filter.

The filter accepts the following options:

angle

Set angle of directional blur. Default is 45.

radius

Set radius of directional blur. Default is 5.

planes

Set which planes to filter. By default all planes are filtered.

#### 39.52.1 Commands# TOC

This filter supports same commands as options. The command accepts the same syntax of the corresponding option.

If the specified expression is not valid, it is kept at its current value.

### 39.53 dctdnoiz# TOC

Denoise frames using 2D DCT (frequency domain filtering).

This filter is not designed for real time.

The filter accepts the following options:

sigma, s

Set the noise sigma constant.

This sigma defines a hard threshold of 3 * sigma; every DCT coefficient (absolute value) below this threshold with be dropped.

If you need a more advanced filtering, see expr.

Default is 0.

overlap

Set number overlapping pixels for each block. Since the filter can be slow, you may want to reduce this value, at the cost of a less effective filter and the risk of various artefacts.

If the overlapping value doesn’t permit processing the whole input width or height, a warning will be displayed and according borders won’t be denoised.

Default value is blocksize-1, which is the best possible setting.

expr, e

Set the coefficient factor expression.

For each coefficient of a DCT block, this expression will be evaluated as a multiplier value for the coefficient.

If this is option is set, the sigma option will be ignored.

The absolute value of the coefficient can be accessed through the c variable.

n

Set the blocksize using the number of bits. 1<<n defines the blocksize, which is the width and height of the processed blocks.

The default value is 3 (8x8) and can be raised to 4 for a blocksize of 16x16. Note that changing this setting has huge consequences on the speed processing. Also, a larger block size does not necessarily means a better de-noising.

#### 39.53.1 Examples# TOC

Apply a denoise with a sigma of 4.5:

```
dctdnoiz=4.5

```

The same operation can be achieved using the expression system:

```
dctdnoiz=e='gte(c, 4.5*3)'

```

Violent denoise using a block size of 16x16:

```
dctdnoiz=15:n=4

```

### 39.54 deband# TOC

Remove banding artifacts from input video. It works by replacing banded pixels with average value of referenced pixels.

The filter accepts the following options:

1thr

2thr

3thr

4thr

Set banding detection threshold for each plane. Default is 0.02. Valid range is 0.00003 to 0.5. If difference between current pixel and reference pixel is less than threshold, it will be considered as banded.

range, r

Banding detection range in pixels. Default is 16. If positive, random number in range 0 to set value will be used. If negative, exact absolute value will be used. The range defines square of four pixels around current pixel.

direction, d

Set direction in radians from which four pixel will be compared. If positive, random direction from 0 to set direction will be picked. If negative, exact of absolute value will be picked. For example direction 0, -PI or -2*PI radians will pick only pixels on same row and -PI/2 will pick only pixels on same column.

blur, b

If enabled, current pixel is compared with average value of all four surrounding pixels. The default is enabled. If disabled current pixel is compared with all four surrounding pixels. The pixel is considered banded if only all four differences with surrounding pixels are less than threshold.

coupling, c

If enabled, current pixel is changed if and only if all pixel components are banded, e.g. banding detection threshold is triggered for all color components. The default is disabled.

#### 39.54.1 Commands# TOC

This filter supports the all above options as commands.

### 39.55 deblock# TOC

Remove blocking artifacts from input video.

The filter accepts the following options:

filter

Set filter type, can be weak or strong. Default is strong. This controls what kind of deblocking is applied.

block

Set size of block, allowed range is from 4 to 512. Default is 8.

alpha

beta

gamma

delta

Set blocking detection thresholds. Allowed range is 0 to 1. Defaults are: 0.098 for alpha and 0.05 for the rest. Using higher threshold gives more deblocking strength. Setting alpha controls threshold detection at exact edge of block. Remaining options controls threshold detection near the edge. Each one for below/above or left/right. Setting any of those to 0 disables deblocking.

planes

Set planes to filter. Default is to filter all available planes.

#### 39.55.1 Examples# TOC

- Deblock using weak filter and block size of 4 pixels.

```
deblock=filter=weak:block=4

```

- Deblock using strong filter, block size of 4 pixels and custom thresholds for deblocking more edges.

```
deblock=filter=strong:block=4:alpha=0.12:beta=0.07:gamma=0.06:delta=0.05

```

- Similar as above, but filter only first plane.

```
deblock=filter=strong:block=4:alpha=0.12:beta=0.07:gamma=0.06:delta=0.05:planes=1

```

- Similar as above, but filter only second and third plane.

```
deblock=filter=strong:block=4:alpha=0.12:beta=0.07:gamma=0.06:delta=0.05:planes=6

```

#### 39.55.2 Commands# TOC

This filter supports the all above options as commands.

### 39.56 decimate# TOC

Drop duplicated frames at regular intervals.

The filter accepts the following options:

cycle

Set the number of frames from which one will be dropped. Setting this to N means one frame in every batch of N frames will be dropped. Default is 5.

dupthresh

Set the threshold for duplicate detection. If the difference metric for a frame is less than or equal to this value, then it is declared as duplicate. Default is 1.1

scthresh

Set scene change threshold. Default is 15.

blockx

blocky

Set the size of the x and y-axis blocks used during metric calculations. Larger blocks give better noise suppression, but also give worse detection of small movements. Must be a power of two. Default is 32.

ppsrc

Mark main input as a pre-processed input and activate clean source input stream. This allows the input to be pre-processed with various filters to help the metrics calculation while keeping the frame selection lossless. When set to 1, the first stream is for the pre-processed input, and the second stream is the clean source from where the kept frames are chosen. Default is 0.

chroma

Set whether or not chroma is considered in the metric calculations. Default is 1.

mixed

Set whether or not the input only partially contains content to be decimated. Default is false. If enabled video output stream will be in variable frame rate.

### 39.57 deconvolve# TOC

Apply 2D deconvolution of video stream in frequency domain using second stream as impulse.

The filter accepts the following options:

planes

Set which planes to process.

impulse

Set which impulse video frames will be processed, can be first or all. Default is all.

noise

Set noise when doing divisions. Default is 0.0000001. Useful when width and height are not same and not power of 2 or if stream prior to convolving had noise.

The deconvolve filter also supports the framesync options.

### 39.58 dedot# TOC

Reduce cross-luminance (dot-crawl) and cross-color (rainbows) from video.

It accepts the following options:

m

Set mode of operation. Can be combination of dotcrawl for cross-luminance reduction and/or rainbows for cross-color reduction.

lt

Set spatial luma threshold. Lower values increases reduction of cross-luminance.

tl

Set tolerance for temporal luma. Higher values increases reduction of cross-luminance.

tc

Set tolerance for chroma temporal variation. Higher values increases reduction of cross-color.

ct

Set temporal chroma threshold. Lower values increases reduction of cross-color.

### 39.59 deflate# TOC

Apply deflate effect to the video.

This filter replaces the pixel by the local(3x3) average by taking into account only values lower than the pixel.

It accepts the following options:

threshold0

threshold1

threshold2

threshold3

Limit the maximum change for each plane, default is 65535. If 0, plane will remain unchanged.

#### 39.59.1 Commands# TOC

This filter supports the all above options as commands.

### 39.60 deflicker# TOC

Remove temporal frame luminance variations.

It accepts the following options:

size, s

Set moving-average filter size in frames. Default is 5. Allowed range is 2 - 129.

mode, m

Set averaging mode to smooth temporal luminance variations.

Available values are:

‘am’

Arithmetic mean

‘gm’

Geometric mean

‘hm’

Harmonic mean

‘qm’

Quadratic mean

‘cm’

Cubic mean

‘pm’

Power mean

‘median’

Median

bypass

Do not actually modify frame. Useful when one only wants metadata.

### 39.61 deinterlace_d3d12# TOC

Deinterlace the input video using D3D12 hardware-accelerated video processing.

This filter uses the DirectX 12 Video Processor to perform deinterlacing on GPU, supporting both simple bob and driver-defined advanced (motion-adaptive) algorithms. It requires the input to be in d3d12 hardware pixel format.

The filter automatically queries the hardware for the required number of temporal reference frames (if needed) and manages a frame queue to supply them.

It accepts the following options:

method

The deinterlacing method. It accepts one of the following values:

‘default’

Select the best deinterlacing method available on the hardware. If the driver supports custom, that method is used; otherwise falls back to bob. This is the default.

‘bob’

Bob deinterlacing. Each field is independently scaled to full frame height. Simple and fast, but may produce visible bob artifacts on moving content.

‘custom’

Driver-defined advanced deinterlacing. The exact algorithm is hardware-specific and typically employs motion-adaptive techniques with temporal reference frames for higher quality.

The default value is default.

mode

Specify the interlacing mode. It accepts one of the following values:

‘frame’

Send one frame for each frame. The output frame rate equals the input frame rate. This is the default.

‘field’

Send one frame for each field. The output frame rate is double the input frame rate.

The default value is frame.

deint

Specify which frames to deinterlace. It accepts one of the following values:

‘all’

Deinterlace all frames. This is the default.

‘interlaced’

Only deinterlace frames marked as interlaced; progressive frames are passed through unchanged.

The default value is all.

#### 39.61.1 Examples# TOC

- Deinterlace an interlaced video using software decoding and the best available hardware deinterlacing method:

```
ffmpeg -init_hw_device d3d12va=d3d12 -filter_hw_device d3d12 -i input.ts \
       -vf "format=nv12,hwupload,deinterlace_d3d12=method=default,hwdownload,format=nv12" \
       -c:v libx264 -crf 18 output.mp4

```

- Deinterlace at field rate (double the frame rate) using bob method with hardware decoding (full d3d12 pipeline):

```
ffmpeg -hwaccel d3d12va -hwaccel_output_format d3d12 -i input.ts \
       -vf "deinterlace_d3d12=method=bob:mode=field" \
       -c:v h264_d3d12va output.mp4

```

- Deinterlace only interlaced frames, passing progressive frames through:

```
ffmpeg -init_hw_device d3d12va=d3d12 -filter_hw_device d3d12 -i input.ts \
       -vf "format=nv12,hwupload,deinterlace_d3d12=deint=interlaced,hwdownload,format=nv12" \
       -c:v libx264 -crf 18 output.mp4

```

### 39.62 dejudder# TOC

Remove judder produced by partially interlaced telecined content.

Judder can be introduced, for instance, by pullup filter. If the original source was partially telecined content then the output of pullup,dejudder will have a variable frame rate. May change the recorded frame rate of the container. Aside from that change, this filter will not affect constant frame rate video.

The option available in this filter is:

cycle

Specify the length of the window over which the judder repeats.

Accepts any integer greater than 1. Useful values are:

‘4’

If the original was telecined from 24 to 30 fps (Film to NTSC).

‘5’

If the original was telecined from 25 to 30 fps (PAL to NTSC).

‘20’

If a mixture of the two.

The default is ‘4’.

### 39.63 delogo# TOC

Suppress a TV station logo by a simple interpolation of the surrounding pixels. Just set a rectangle covering the logo and watch it disappear (and sometimes something even uglier appear - your mileage may vary).

It accepts the following parameters:

x

y

Specify the top left corner coordinates of the logo. They must be specified.

w

h

Specify the width and height of the logo to clear. They must be specified.

show

When set to 1, a green rectangle is drawn on the screen to simplify finding the right x, y, w, and h parameters. The default value is 0.

The rectangle is drawn on the outermost pixels which will be (partly) replaced with interpolated values. The values of the next pixels immediately outside this rectangle in each direction will be used to compute the interpolated pixel values inside the rectangle.

#### 39.63.1 Examples# TOC

- Set a rectangle covering the area with top left corner coordinates 0,0 and size 100x77:

```
delogo=x=0:y=0:w=100:h=77

```

### 39.64 derain# TOC

Remove the rain in the input image/video by applying the derain methods based on convolutional neural networks. Supported models:

- Recurrent Squeeze-and-Excitation Context Aggregation Net (RESCAN). See http://openaccess.thecvf.com/content_ECCV_2018/papers/Xia_Li_Recurrent_Squeeze-and-Excitation_Context_ECCV_2018_paper.pdf.

Training as well as model generation scripts are provided in the repository at https://github.com/XueweiMeng/derain_filter.git.

The filter accepts the following options:

filter_type

Specify which filter to use. This option accepts the following values:

‘derain’

Derain filter. To conduct derain filter, you need to use a derain model.

‘dehaze’

Dehaze filter. To conduct dehaze filter, you need to use a dehaze model.

Default value is ‘derain’.

dnn_backend

Specify which DNN backend to use for model loading and execution. This option accepts the following values:

‘tensorflow’

TensorFlow backend. To enable this backend you need to install the TensorFlow for C library (see https://www.tensorflow.org/install/lang_c) and configure FFmpeg with --enable-libtensorflow

model

Set path to model file specifying network architecture and its parameters. Note that different backends use different file formats. TensorFlow can load files for only its format.

To get full functionality (such as async execution), please use the dnn_processing filter.

### 39.65 deshake# TOC

Attempt to fix small changes in horizontal and/or vertical shift. This filter helps remove camera shake from hand-holding a camera, bumping a tripod, moving on a vehicle, etc.

The filter accepts the following options:

x

y

w

h

Specify a rectangular area where to limit the search for motion vectors. If desired the search for motion vectors can be limited to a rectangular area of the frame defined by its top left corner, width and height. These parameters have the same meaning as the drawbox filter which can be used to visualise the position of the bounding box.

This is useful when simultaneous movement of subjects within the frame might be confused for camera motion by the motion vector search.

If any or all of x, y, w and h are set to -1 then the full frame is used. This allows later options to be set without specifying the bounding box for the motion vector search.

Default - search the whole frame.

rx

ry

Specify the maximum extent of movement in x and y directions in the range 0-64 pixels. Default 16.

edge

Specify how to generate pixels to fill blanks at the edge of the frame. Available values are:

‘blank, 0’

Fill zeroes at blank locations

‘original, 1’

Original image at blank locations

‘clamp, 2’

Extruded edge value at blank locations

‘mirror, 3’

Mirrored edge at blank locations

Default value is ‘mirror’.

blocksize

Specify the blocksize to use for motion search. Range 4-128 pixels, default 8.

contrast

Specify the contrast threshold for blocks. Only blocks with more than the specified contrast (difference between darkest and lightest pixels) will be considered. Range 1-255, default 125.

search

Specify the search strategy. Available values are:

‘exhaustive, 0’

Set exhaustive search

‘less, 1’

Set less exhaustive search.

Default value is ‘exhaustive’.

filename

If set then a detailed log of the motion search is written to the specified file.

### 39.66 despill# TOC

Remove unwanted contamination of foreground colors, caused by reflected color of greenscreen or bluescreen.

This filter accepts the following options:

type

Set what type of despill to use.

mix

Set how spillmap will be generated.

expand

Set how much to get rid of still remaining spill.

red

Controls amount of red in spill area.

green

Controls amount of green in spill area. Should be -1 for greenscreen.

blue

Controls amount of blue in spill area. Should be -1 for bluescreen.

brightness

Controls brightness of spill area, preserving colors.

alpha

Modify alpha from generated spillmap.

#### 39.66.1 Commands# TOC

This filter supports the all above options as commands.

### 39.67 detelecine# TOC

Apply an exact inverse of the telecine operation. It requires a predefined pattern specified using the pattern option which must be the same as that passed to the telecine filter.

This filter accepts the following options:

first_field

‘top, t’

top field first

‘bottom, b’

bottom field first The default value is top.

pattern

A string of numbers representing the pulldown pattern you wish to apply. The default value is 23.

start_frame

A number representing position of the first frame with respect to the telecine pattern. This is to be used if the stream is cut. The default value is 0.

### 39.68 dilation# TOC

Apply dilation effect to the video.

This filter replaces the pixel by the local(3x3) maximum.

It accepts the following options:

threshold0

threshold1

threshold2

threshold3

Limit the maximum change for each plane, default is 65535. If 0, plane will remain unchanged.

coordinates

Flag which specifies the pixel to refer to. Default is 255 i.e. all eight pixels are used.

Flags to local 3x3 coordinates maps like this:

1 2 3 4 5 6 7 8

#### 39.68.1 Commands# TOC

This filter supports the all above options as commands.

### 39.69 displace# TOC

Displace pixels as indicated by second and third input stream.

It takes three input streams and outputs one stream, the first input is the source, and second and third input are displacement maps.

The second input specifies how much to displace pixels along the x-axis, while the third input specifies how much to displace pixels along the y-axis. If one of displacement map streams terminates, last frame from that displacement map will be used.

Note that once generated, displacements maps can be reused over and over again.

A description of the accepted options follows.

edge

Set displace behavior for pixels that are out of range.

Available values are:

‘blank’

Missing pixels are replaced by black pixels.

‘smear’

Adjacent pixels will spread out to replace missing pixels.

‘wrap’

Out of range pixels are wrapped so they point to pixels of other side.

‘mirror’

Out of range pixels will be replaced with mirrored pixels.

Default is ‘smear’.

#### 39.69.1 Examples# TOC

- Add ripple effect to rgb input of video size hd720:

```
ffmpeg -i INPUT -f lavfi -i nullsrc=s=hd720,lutrgb=128:128:128 -f lavfi -i nullsrc=s=hd720,geq='r=128+30*sin(2*PI*X/400+T):g=128+30*sin(2*PI*X/400+T):b=128+30*sin(2*PI*X/400+T)' -lavfi '[0][1][2]displace' OUTPUT

```

- Add wave effect to rgb input of video size hd720:

```
ffmpeg -i INPUT -f lavfi -i nullsrc=hd720,geq='r=128+80*(sin(sqrt((X-W/2)*(X-W/2)+(Y-H/2)*(Y-H/2))/220*2*PI+T)):g=128+80*(sin(sqrt((X-W/2)*(X-W/2)+(Y-H/2)*(Y-H/2))/220*2*PI+T)):b=128+80*(sin(sqrt((X-W/2)*(X-W/2)+(Y-H/2)*(Y-H/2))/220*2*PI+T))' -lavfi '[1]split[x][y],[0][x][y]displace' OUTPUT

```

### 39.70 dnn_classify# TOC

Do classification with deep neural networks based on bounding boxes.

The filter accepts the following options:

dnn_backend

Specify which DNN backend to use for model loading and execution. This option accepts only openvino now, tensorflow backends will be added.

model

Set path to model file specifying network architecture and its parameters. Note that different backends use different file formats.

input

Set the input name of the dnn network.

output

Set the output name of the dnn network.

confidence

Set the confidence threshold (default: 0.5).

labels

Set path to label file specifying the mapping between label id and name. Each label name is written in one line, tailing spaces and empty lines are skipped. The first line is the name of label id 0, and the second line is the name of label id 1, etc. The label id is considered as name if the label file is not provided.

backend_configs

Set the configs to be passed into backend

For tensorflow backend, you can set its configs with sess_config options, please use tools/python/tf_sess_config.py to get the configs for your system.

### 39.71 dnn_detect# TOC

Do object detection with deep neural networks.

The filter accepts the following options:

dnn_backend

Specify which DNN backend to use for model loading and execution. This option accepts the following values:

‘tensorflow’

TensorFlow backend.

‘openvino’

OpenVINO backend.

‘onnx’

ONNX Runtime backend.

model

Set path to model file specifying network architecture and its parameters. Note that different backends use different file formats.

input

Set the input name of the dnn network.

output

Set the output name of the dnn network. The TensorFlow and ONNX Runtime backends accept multiple output names separated by ‘&’, e.g. output=yolo_13&yolo_26.

confidence

Set the confidence threshold (default: 0.5).

labels

Set path to label file specifying the mapping between label id and name. Each label name is written in one line, tailing spaces and empty lines are skipped. The first line is the name of label id 0 (usually it is ’background’), and the second line is the name of label id 1, etc. The label id is considered as name if the label file is not provided.

model_type

Set the detection model output format. The following values are accepted:

‘ssd’

Single-stage detector (default).

‘yolo’

YOLO v1/v2.

‘yolov3’

YOLOv3.

‘yolov4’

YOLOv4.

anchors

Anchor box dimensions, separated by ‘&’. Required for YOLO-family models. The list is consumed in output order, so the anchors of the first output come first: with output=yolo_13&yolo_26 the leading pairs belong to yolo_13.

nb_classes

Number of detection classes. Required for YOLO-family models.

backend_configs

Set the configs to be passed into backend. To use async execution, set async (default: set). Roll back to sync execution if the backend does not support async.

#### 39.71.1 Examples# TOC

- Run SSD object detection with an ONNX model (single output, DirectML on Windows):

```
ffmpeg -i input.mp4 -vf "scale=300:300,format=rgb24,dnn_detect=dnn_backend=onnx
       :model=ssd.onnx:model_type=ssd:confidence=0.5:device=dml" -f null -

```

- Run YOLOv3 object detection with an ONNX model (two outputs, CPU):

```
ffmpeg -i input.mp4 -vf "scale=416:416,format=rgb24,dnn_detect=dnn_backend=onnx
       :model=yolov3.onnx:output=yolo_13&yolo_26:model_type=yolov3:nb_classes=80
       :anchors=116&90&156&198&373&326&30&61&62&45&59&119" -f null -

```

### 39.72 dnn_processing# TOC

Do image processing with deep neural networks. It works together with another filter which converts the pixel format of the Frame to what the dnn network requires.

The filter accepts the following options:

dnn_backend

Specify which DNN backend to use for model loading and execution. This option accepts the following values:

‘tensorflow’

TensorFlow backend. To enable this backend you need to install the TensorFlow for C library (see https://www.tensorflow.org/install/lang_c) and configure FFmpeg with --enable-libtensorflow

‘openvino’

OpenVINO backend. To enable this backend you need to build and install the OpenVINO for C library (see https://github.com/openvinotoolkit/openvino/blob/master/build-instruction.md) and configure FFmpeg with --enable-libopenvino (–extra-cflags=-I... –extra-ldflags=-L... might be needed if the header files and libraries are not installed into system path)

‘torch’

Libtorch backend. To enable this backend you need to build and install Libtorch for C++ library. Please download cxx11 ABI version (see https://pytorch.org/get-started/locally) and configure FFmpeg with --enable-libtorch --extra-cflags=-I/libtorch_root/libtorch/include --extra-cflags=-I/libtorch_root/libtorch/include/torch/csrc/api/include --extra-ldflags=-L/libtorch_root/libtorch/lib/

When FFmpeg is built with CUDA support and the input frames use AV_PIX_FMT_CUDA with an underlying pixel format of rgb0, bgr0, rgb24, or bgr24, the Torch backend maps GPU frame buffers directly into LibTorch CUDA tensors using zero-copy memory mapping. This avoids host-device PCIe transfers and can significantly reduce inference latency. The zero-copy path is selected automatically when the input format qualifies; no additional options are required. When the input format is not AV_PIX_FMT_CUDA, the backend uses the standard CPU tensor path.

‘onnx’

ONNX Runtime backend. To enable this backend you need to install the ONNX Runtime library (see https://onnxruntime.ai/) and configure FFmpeg with --enable-libonnxruntime.

The current ONNX Runtime backend expects 4-D input and output tensors with NCHW layout and 32-bit floating-point element type (ONNX FLOAT); models with integer or other element types (e.g. UINT8) are not supported and will be rejected at load time. Models using NHWC layout or other ranks are not yet supported. Only single-input models are supported; the backend binds exactly one input tensor when running the model.

The input and output options are optional for the ONNX Runtime backend; when they are omitted the backend resolves the tensor names from the session. Multiple output names may be supplied separated by ‘&’ (e.g. output=out_a&out_b); however for dnn_processing only the first output tensor is used for frame post-processing.

The ONNX Runtime backend runs inference synchronously using a single inference request. The shared async and nireq options therefore have no effect for dnn_backend=onnx; inference always runs synchronously regardless of their values.

When FFmpeg is built with Direct3D 12 support and this build’s ONNX Runtime provides a working DirectML execution provider, setting device=dml together with AV_PIX_FMT_D3D12 NV12 hardware frames as input (e.g. via -hwaccel d3d12va -hwaccel_output_format d3d12) keeps frames in VRAM for the whole filter, from the decoder’s output through DNN inference and back out, without a host round-trip. Software-frame input retains the host I/O path. D3D12 input requires successful DirectML negotiation; unsupported hardware-input configurations fail during configuration. At runtime, DirectML.dll and d3dcompiler_47.dll must be loadable from the application directory or System32. Currently, only single-channel (luma-only), FLOAT/NCHW models with a [1,1,H,W] output tensor and even input/output frame dimensions are supported; the chroma plane is copied or bilinearly upscaled on the GPU without going through the model. The output frames are D3D12 hardware frames, so they must either be consumed by a D3D12 encoder or downloaded explicitly with hwdownload,format=nv12.

model

Set path to model file specifying network architecture and its parameters. Note that different backends use different file formats. TensorFlow, OpenVINO, Libtorch, and ONNX Runtime backends can load files for only their respective formats.

input

Set the input name of the dnn network. Required for the TensorFlow backend; optional for the ONNX Runtime backend.

output

Set the output name of the dnn network. Required for the TensorFlow backend; optional for the ONNX Runtime backend.

backend_configs

Set the configs to be passed into backend. To use async execution, set async (default: set). Roll back to sync execution if the backend does not support async.

For tensorflow backend, you can set its configs with sess_config options, please use tools/python/tf_sess_config.py to get the configs of TensorFlow backend for your system.

async

Use DNN async inference (default: 1). When enabled, frames are submitted to the backend without blocking the caller. Supported by the Torch, OpenVINO, and TensorFlow backends; the ONNX Runtime backend ignores this option.

nireq

Number of concurrent inference requests (default: 0, meaning auto). When set to 0, the backend automatically determines an appropriate number of requests. Higher values increase throughput by allowing multiple frames to be in flight simultaneously.

batch_size

Number of frames to batch into a single inference request (default: 1). Values greater than 1 cause the backend to accumulate frames and concatenate them along the batch dimension before running the model. This can significantly increase throughput on GPUs at the cost of slightly higher per-frame latency. Currently supported by the OpenVINO and Torch backends.

device

Set the device to run the model. For the ONNX Runtime backend this selects the execution provider: cpu (default), cuda (NVIDIA GPU), dml (DirectML, Windows only) or vitisai (AMD Ryzen AI NPU).

device_id

Set the device index used by GPU execution providers (e.g. cuda or dml) for the ONNX Runtime backend. Default is 0.

threads_per_operation

ONNX Runtime backend only. Set the number of CPU threads used per ONNX Runtime operator when running with device=cpu. Default is 0 (let ONNX Runtime choose automatically). Has no effect for GPU/NPU providers.

#### 39.72.1 Examples# TOC

- Remove rain in rgb24 frame with can.pb (see derain filter):

```
./ffmpeg -i rain.jpg -vf format=rgb24,dnn_processing=dnn_backend=tensorflow:model=can.pb:input=x:output=y derain.jpg

```

- Handle the Y channel with srcnn.pb (see sr filter) for frame with yuv420p (planar YUV formats supported):

```
./ffmpeg -i 480p.jpg -vf format=yuv420p,scale=w=iw*2:h=ih*2,dnn_processing=dnn_backend=tensorflow:model=srcnn.pb:input=x:output=y -y srcnn.jpg

```

- Handle the Y channel with espcn.pb (see sr filter), which changes frame size, for format yuv420p (planar YUV formats supported), please use tools/python/tf_sess_config.py to get the configs of TensorFlow backend for your system.

```
./ffmpeg -i 480p.jpg -vf format=yuv420p,dnn_processing=dnn_backend=tensorflow:model=espcn.pb:input=x:output=y:backend_configs=sess_config=0x10022805320e09cdccccccccccec3f20012a01303801 -y tmp.espcn.jpg

```

- Perform zero-copy GPU inference with the Libtorch backend. Because there is currently no GPU-side filter to convert from YUV to RGB, hwupload is used to upload CPU RGB frames into device memory. Once a GPU-side YUV-to-RGB filter becomes available, the hwupload step will no longer be necessary and all frames can stay in device memory throughout the pipeline:

```
./ffmpeg -init_hw_device cuda=cuda -filter_hw_device cuda -i input.mp4 \
  -vf "format=rgb24,hwupload,dnn_processing=dnn_backend=torch:model=my_model.pt,hwdownload,format=rgb0" \
  -y output.mp4

```

- Run a single-channel (luma-only) super-resolution model on D3D12 hardware frames with the ONNX Runtime backend, keeping frames in VRAM from decode through inference (Windows only, requires a build with Direct3D 12 support and --enable-libonnxruntime against a DirectML-capable ONNX Runtime). The D3D12 output frames are encoded directly by a D3D12 hardware encoder:

```
./ffmpeg -hwaccel d3d12va -hwaccel_output_format d3d12 -i input.mp4 \
  -vf dnn_processing=dnn_backend=onnx:model=sr_model.onnx:device=dml \
  -c:v h264_d3d12va -bf 0 -y output.mp4

```

- Same as above, but download the result to software frames after inference so that a software encoder can be used:

```
./ffmpeg -hwaccel d3d12va -hwaccel_output_format d3d12 -i input.mp4 \
  -vf dnn_processing=dnn_backend=onnx:model=sr_model.onnx:device=dml,hwdownload,format=nv12 \
  -y output.mp4

```

- Process rgb24 frames with a TorchScript model using the Libtorch backend:

```
./ffmpeg -i input.jpg -vf format=rgb24,dnn_processing=dnn_backend=torch:model=my_model.pt output.jpg

```

- Process rgb24 frames with the Libtorch backend using batch inference (four frames per request):

```
./ffmpeg -i input.mp4 -vf format=rgb24,dnn_processing=dnn_backend=torch:model=my_model.pt:batch_size=4 -y output.mp4

```

### 39.73 drawbox# TOC

Draw a colored box on the input image.

It accepts the following parameters:

x

y

The expressions which specify the top left corner coordinates of the box. It defaults to 0.

width, w

height, h

The expressions which specify the width and height of the box; if 0 they are interpreted as the input width and height. It defaults to 0.

color, c

Specify the color of the box to write. For the general syntax of this option, check the "Color" section in the ffmpeg-utils manual. If the special value invert is used, the box edge color is the same as the video with inverted luma.

thickness, t

The expression which sets the thickness of the box edge. A value of fill will create a filled box. Default value is 3.

See below for the list of accepted constants.

replace

Applicable if the input has alpha. With value 1, the pixels of the painted box will overwrite the video’s color and alpha pixels. Default is 0, which composites the box onto the input, leaving the video’s alpha intact.

The parameters for x, y, w and h and t are expressions containing the following constants:

dar

The input display aspect ratio, it is the same as (w / h) * sar.

hsub

vsub

horizontal and vertical chroma subsample values. For example for the pixel format "yuv422p" hsub is 2 and vsub is 1.

in_h, ih

in_w, iw

The input width and height.

sar

The input sample aspect ratio.

x

y

The x and y offset coordinates where the box is drawn.

w

h

The width and height of the drawn box.

box_source

Box source can be set as side_data_detection_bboxes if you want to use box data in detection bboxes of side data.

If box_source is set, the x, y, width and height will be ignored and still use box data in detection bboxes of side data. So please do not use this parameter if you were not sure about the box source.

t

The thickness of the drawn box.

These constants allow the x, y, w, h and t expressions to refer to each other, so you may for example specify y=x/dar or h=w/dar.

#### 39.73.1 Examples# TOC

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

#### 39.73.2 Commands# TOC

This filter supports same commands as options. The command accepts the same syntax of the corresponding option.

If the specified expression is not valid, it is kept at its current value.

### 39.74 drawgraph# TOC

Draw a graph using input video metadata.

It accepts the following parameters:

m1

Set 1st frame metadata key from which metadata values will be used to draw a graph.

fg1

Set 1st foreground color expression.

m2

Set 2nd frame metadata key from which metadata values will be used to draw a graph.

fg2

Set 2nd foreground color expression.

m3

Set 3rd frame metadata key from which metadata values will be used to draw a graph.

fg3

Set 3rd foreground color expression.

m4

Set 4th frame metadata key from which metadata values will be used to draw a graph.

fg4

Set 4th foreground color expression.

min

Set minimal value of metadata value.

max

Set maximal value of metadata value.

bg

Set graph background color. Default is white.

mode

Set graph mode.

Available values for mode is:

‘bar’

‘dot’

‘line’

Default is line.

slide

Set slide mode.

Available values for slide is:

‘frame’

Draw new frame when right border is reached.

‘replace’

Replace old columns with new ones.

‘scroll’

Scroll from right to left.

‘rscroll’

Scroll from left to right.

‘picture’

Draw single picture.

Default is frame.

size

Set size of graph video. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual. The default value is 900x256.

rate, r

Set the output frame rate. Default value is 25.

The foreground color expressions can use the following variables:

MIN

Minimal value of metadata value.

MAX

Maximal value of metadata value.

VAL

Current metadata key value.

The color is defined as 0xAABBGGRR.

Example using metadata from signalstats filter:

```
signalstats,drawgraph=lavfi.signalstats.YAVG:min=0:max=255

```

Example using metadata from ebur128 filter:

```
ebur128=metadata=1,adrawgraph=lavfi.r128.M:min=-120:max=5

```

### 39.75 drawgrid# TOC

Draw a grid on the input image.

It accepts the following parameters:

x

y

The expressions which specify the coordinates of some point of grid intersection (meant to configure offset). Both default to 0.

width, w

height, h

The expressions which specify the width and height of the grid cell, if 0 they are interpreted as the input width and height, respectively, minus thickness, so image gets framed. Default to 0.

color, c

Specify the color of the grid. For the general syntax of this option, check the "Color" section in the ffmpeg-utils manual. If the special value invert is used, the grid color is the same as the video with inverted luma.

thickness, t

The expression which sets the thickness of the grid line. Default value is 1.

See below for the list of accepted constants.

replace

Applicable if the input has alpha. With 1 the pixels of the painted grid will overwrite the video’s color and alpha pixels. Default is 0, which composites the grid onto the input, leaving the video’s alpha intact.

The parameters for x, y, w and h and t are expressions containing the following constants:

dar

The input display aspect ratio, it is the same as (w / h) * sar.

hsub

vsub

horizontal and vertical chroma subsample values. For example for the pixel format "yuv422p" hsub is 2 and vsub is 1.

in_h, ih

in_w, iw

The input grid cell width and height.

sar

The input sample aspect ratio.

x

y

The x and y coordinates of some point of grid intersection (meant to configure offset).

w

h

The width and height of the drawn cell.

t

The thickness of the drawn cell.

These constants allow the x, y, w, h and t expressions to refer to each other, so you may for example specify y=x/dar or h=w/dar.

#### 39.75.1 Examples# TOC

- Draw a grid with cell 100x100 pixels, thickness 2 pixels, with color red and an opacity of 50%:

```
drawgrid=width=100:height=100:thickness=2:color=red@0.5

```

- Draw a white 3x3 grid with an opacity of 50%:

```
drawgrid=w=iw/3:h=ih/3:t=2:c=white@0.5

```

#### 39.75.2 Commands# TOC

This filter supports same commands as options. The command accepts the same syntax of the corresponding option.

If the specified expression is not valid, it is kept at its current value.

### 39.76 drawtext# TOC

Draw a text string or text from a specified file on top of a video, using the libfreetype library.

To enable compilation of this filter, you need to configure FFmpeg with --enable-libfreetype and --enable-libharfbuzz. To enable default font fallback and the font option you need to configure FFmpeg with --enable-libfontconfig. To enable the text_shaping option, you need to configure FFmpeg with --enable-libfribidi.

#### 39.76.1 Syntax# TOC

It accepts the following parameters:

box

Used to draw a box around text using the background color. The value must be either 1 (enable) or 0 (disable). The default value of box is 0.

boxborderw

Set the width of the border to be drawn around the box using boxcolor. The value must be specified using one of the following formats:

- boxborderw=10 set the width of all the borders to 10

- boxborderw=10|20 set the width of the top and bottom borders to 10 and the width of the left and right borders to 20

- boxborderw=10|20|30 set the width of the top border to 10, the width of the bottom border to 30 and the width of the left and right borders to 20

- boxborderw=10|20|30|40 set the borders width to 10 (top), 20 (right), 30 (bottom), 40 (left)

The default value of boxborderw is "0".

boxcolor

The color to be used for drawing box around text. For the syntax of this option, check the "Color" section in the ffmpeg-utils manual.

The default value of boxcolor is "white".

line_spacing

Set the line spacing in pixels. The default value of line_spacing is 0.

text_align

Set the vertical and horizontal alignment of the text with respect to the box boundaries. The value is combination of flags, one for the vertical alignment (T=top, M=middle, B=bottom) and one for the horizontal alignment (L=left, C=center, R=right). Please note that tab characters are only supported with the left horizontal alignment.

y_align

Specify what the y value is referred to. Possible values are:

- text the top of the highest glyph of the first text line is placed at y

- baseline the baseline of the first text line is placed at y

- font the baseline of the first text line is placed at y plus the ascent (in pixels) defined in the font metrics

The default value of y_align is "text" for backward compatibility.

borderw

Set the width of the border to be drawn around the text using bordercolor. The default value of borderw is 0.

bordercolor

Set the color to be used for drawing border around text. For the syntax of this option, check the "Color" section in the ffmpeg-utils manual.

The default value of bordercolor is "black".

expansion

Select how the text is expanded. Can be either none, strftime (deprecated) or normal (default). See the Text expansion section below for details.

basetime

Set a start time for the count. Value is in microseconds. Only applied in the deprecated strftime expansion mode. To emulate in normal expansion mode use the pts function, supplying the start time (in seconds) as the second argument.

fix_bounds

If true, check and fix text coords to avoid clipping.

fontcolor

The color to be used for drawing fonts. For the syntax of this option, check the "Color" section in the ffmpeg-utils manual.

The default value of fontcolor is "black".

fontcolor_expr

String which is expanded the same way as text to obtain dynamic fontcolor value. By default this option has empty value and is not processed. When this option is set, it overrides fontcolor option.

font

The font family to be used for drawing text. By default Sans.

fontfile

The font file to be used for drawing text. The path must be included. This parameter is mandatory if the fontconfig support is disabled.

alpha

Draw the text applying alpha blending. The value can be a number between 0.0 and 1.0. The expression accepts the same variables x, y as well. The default value is 1. Please see fontcolor_expr.

fontsize

The font size to be used for drawing text. The default value of fontsize is 16.

text_shaping

If set to 1, attempt to shape the text (for example, reverse the order of right-to-left text and join Arabic characters) before drawing it. Otherwise, just draw the text exactly as given. By default 1 (if supported).

ft_load_flags

The flags to be used for loading the fonts.

The flags map the corresponding flags supported by libfreetype, and are a combination of the following values:

default

no_scale

no_hinting

render

no_bitmap

vertical_layout

force_autohint

crop_bitmap

pedantic

ignore_global_advance_width

no_recurse

ignore_transform

monochrome

linear_design

no_autohint

Default value is "default".

For more information consult the documentation for the FT_LOAD_* libfreetype flags.

shadowcolor

The color to be used for drawing a shadow behind the drawn text. For the syntax of this option, check the "Color" section in the ffmpeg-utils manual.

The default value of shadowcolor is "black".

boxw

Set the width of the box to be drawn around text. The default value of boxw is computed automatically to match the text width

boxh

Set the height of the box to be drawn around text. The default value of boxh is computed automatically to match the text height

shadowx

shadowy

The x and y offsets for the text shadow position with respect to the position of the text. They can be either positive or negative values. The default value for both is "0".

start_number

The starting frame number for the n/frame_num variable. The default value is "0".

tabsize

The size in number of spaces to use for rendering the tab. Default value is 4.

timecode

Set the initial timecode representation in "hh:mm:ss[:;.]ff" format. It can be used with or without text parameter. timecode_rate option must be specified.

timecode_rate, rate, r

Set the timecode frame rate (timecode only). Value will be rounded to nearest integer. Minimum value is "1". Drop-frame timecode is supported for frame rates 30 & 60.

tc24hmax

If set to 1, the output of the timecode option will wrap around at 24 hours. Default is 0 (disabled).

text

The text string to be drawn. The text must be a sequence of UTF-8 encoded characters. This parameter is mandatory if no file is specified with the parameter textfile.

textfile

A text file containing text to be drawn. The text must be a sequence of UTF-8 encoded characters.

This parameter is mandatory if no text string is specified with the parameter text.

If both text and textfile are specified, an error is thrown.

text_source

Text source should be set as side_data_detection_bboxes if you want to use text data in detection bboxes of side data.

If text source is set, text and textfile will be ignored and still use text data in detection bboxes of side data. So please do not use this parameter if you are not sure about the text source.

reload

The textfile will be reloaded at specified frame interval. Be sure to update textfile atomically, or it may be read partially, or even fail. Range is 0 to INT_MAX. Default is 0.

x

y

The expressions which specify the offsets where text will be drawn within the video frame. They are relative to the top/left border of the output image.

The default value of x and y is "0".

See below for the list of accepted constants and functions.

The parameters for x and y are expressions containing the following constants and functions:

dar

input display aspect ratio, it is the same as (w / h) * sar

hsub

vsub

horizontal and vertical chroma subsample values. For example for the pixel format "yuv422p" hsub is 2 and vsub is 1.

line_h, lh

the height of each text line

main_h, h, H

the input height

main_w, w, W

the input width

max_glyph_a, ascent

the maximum distance from the baseline to the highest/upper grid coordinate used to place a glyph outline point, for all the rendered glyphs. It is a positive value, due to the grid’s orientation with the Y axis upwards.

max_glyph_d, descent

the maximum distance from the baseline to the lowest grid coordinate used to place a glyph outline point, for all the rendered glyphs. This is a negative value, due to the grid’s orientation, with the Y axis upwards.

max_glyph_h

maximum glyph height, that is the maximum height for all the glyphs contained in the rendered text, it is equivalent to ascent - descent.

max_glyph_w

maximum glyph width, that is the maximum width for all the glyphs contained in the rendered text

font_a

the ascent size defined in the font metrics

font_d

the descent size defined in the font metrics

top_a

the maximum ascender of the glyphs of the first text line

bottom_d

the maximum descender of the glyphs of the last text line

n

the number of input frame, starting from 0

rand(min, max)

return a random number included between min and max

sar

The input sample aspect ratio.

t

timestamp expressed in seconds, NAN if the input timestamp is unknown

text_h, th

the height of the rendered text

text_w, tw

the width of the rendered text

x

y

the x and y offset coordinates where the text is drawn.

These parameters allow the x and y expressions to refer to each other, so you can for example specify y=x/dar.

pict_type

A one character description of the current frame’s picture type.

pkt_pos

The current packet’s position in the input file or stream (in bytes, from the start of the input). A value of -1 indicates this info is not available.

duration

The current packet’s duration, in seconds.

pkt_size

The current packet’s size (in bytes).

#### 39.76.2 Text expansion# TOC

If expansion is set to strftime, the filter recognizes sequences accepted by the strftime C function in the provided text and expands them accordingly. Check the documentation of strftime. This feature is deprecated in favor of normal expansion with the gmtime or localtime expansion functions.

If expansion is set to none, the text is printed verbatim.

If expansion is set to normal (which is the default), the following expansion mechanism is used.

The backslash character ‘\’, followed by any character, always expands to the second character.

Sequences of the form %{...} are expanded. The text between the braces is a function name, possibly followed by arguments separated by ’:’. If the arguments contain special characters or delimiters (’:’ or ’}’), they should be escaped.

Note that they probably must also be escaped as the value for the text option in the filter argument string and as the filter argument in the filtergraph description, and possibly also for the shell, that makes up to four levels of escaping; using a text file with the textfile option avoids these problems.

The following functions are available:

expr, e

The expression evaluation result.

It must take one argument specifying the expression to be evaluated, which accepts the same constants and functions as the x and y values. Note that not all constants should be used, for example the text size is not known when evaluating the expression, so the constants text_w and text_h will have an undefined value.

expr_int_format, eif

Evaluate the expression’s value and output as formatted integer.

The first argument is the expression to be evaluated, just as for the expr function. The second argument specifies the output format. Allowed values are ‘x’, ‘X’, ‘d’ and ‘u’. They are treated exactly as in the printf function. The third parameter is optional and sets the number of positions taken by the output. It can be used to add padding with zeros from the left.

gmtime

The time at which the filter is running, expressed in UTC. It can accept an argument: a strftime C function format string. The format string is extended to support the variable %[1-6]N which prints fractions of the second with optionally specified number of digits.

localtime

The time at which the filter is running, expressed in the local time zone. It can accept an argument: a strftime C function format string. The format string is extended to support the variable %[1-6]N which prints fractions of the second with optionally specified number of digits.

metadata

Frame metadata. Takes one or two arguments.

The first argument is mandatory and specifies the metadata key.

The second argument is optional and specifies a default value, used when the metadata key is not found or empty.

Available metadata can be identified by inspecting entries starting with TAG included within each frame section printed by running ffprobe -show_frames.

String metadata generated in filters leading to the drawtext filter are also available.

n, frame_num

The frame number, starting from 0.

pict_type

A one character description of the current picture type.

pts

The timestamp of the current frame. It can take up to three arguments.

The first argument is the format of the timestamp; it defaults to flt for seconds as a decimal number with microsecond accuracy; hms stands for a formatted [-]HH:MM:SS.mmm timestamp with millisecond accuracy. gmtime stands for the timestamp of the frame formatted as UTC time; localtime stands for the timestamp of the frame formatted as local time zone time.

The second argument is an offset added to the timestamp.

If the format is set to hms, a third argument 24HH may be supplied to present the hour part of the formatted timestamp in 24h format (00-23).

If the format is set to localtime or gmtime, a third argument may be supplied: a strftime C function format string. By default, YYYY-MM-DD HH:MM:SS format will be used.

#### 39.76.3 Commands# TOC

This filter supports altering parameters via commands:

reinit

Alter existing filter parameters.

Syntax for the argument is the same as for filter invocation, e.g.

```
fontsize=56:fontcolor=green:text='Hello World'

```

Full filter invocation with sendcmd would look like this:

```
sendcmd=c='56.0 drawtext reinit fontsize=56\:fontcolor=green\:text=Hello\\ World'

```

If the entire argument can’t be parsed or applied as valid values then the filter will continue with its existing parameters.

The following options are also supported as commands:

- x

- y

- alpha

- fontsize

- fontcolor

- boxcolor

- bordercolor

- shadowcolor

- box

- boxw

- boxh

- boxborderw

- line_spacing

- text_align

- shadowx

- shadowy

- borderw

#### 39.76.4 Examples# TOC

- Draw "Test Text" with font FreeSerif, using the default values for the optional parameters.

```
drawtext="fontfile=/usr/share/fonts/truetype/freefont/FreeSerif.ttf: text='Test Text'"

```

- Draw ’Test Text’ with font FreeSerif of size 24 at position x=100 and y=50 (counting from the top-left corner of the screen), text is yellow with a red box around it. Both the text and the box have an opacity of 20%.

```
drawtext="fontfile=/usr/share/fonts/truetype/freefont/FreeSerif.ttf: text='Test Text':\
          x=100: y=50: fontsize=24: fontcolor=yellow@0.2: box=1: boxcolor=red@0.2"

```

Note that the double quotes are not necessary if spaces are not used within the parameter list.

- Show the text at the center of the video frame:

```
drawtext="fontsize=30:fontfile=FreeSerif.ttf:text='hello world':x=(w-text_w)/2:y=(h-text_h)/2"

```

- Show the text at a random position, switching to a new position every 30 seconds:

```
drawtext="fontsize=30:fontfile=FreeSerif.ttf:text='hello world':x=if(eq(mod(t\,30)\,0)\,rand(0\,(w-text_w))\,x):y=if(eq(mod(t\,30)\,0)\,rand(0\,(h-text_h))\,y)"

```

- Show a text line sliding from right to left in the last row of the video frame. The file LONG_LINE is assumed to contain a single line with no newlines.

```
drawtext="fontsize=15:fontfile=FreeSerif.ttf:text=LONG_LINE:y=h-line_h:x=-50*t"

```

- Show the content of file CREDITS off the bottom of the frame and scroll up.

```
drawtext="fontsize=20:fontfile=FreeSerif.ttf:textfile=CREDITS:y=h-20*t"

```

- Draw a single green letter "g", at the center of the input video. The glyph baseline is placed at half screen height.

```
drawtext="fontsize=60:fontfile=FreeSerif.ttf:fontcolor=green:text=g:x=(w-max_glyph_w)/2:y=h/2-ascent"

```

- Show text for 1 second every 3 seconds:

```
drawtext="fontfile=FreeSerif.ttf:fontcolor=white:x=100:y=x/dar:enable=lt(mod(t\,3)\,1):text='blink'"

```

- Use fontconfig to set the font. Note that the colons need to be escaped.

```
drawtext='fontfile=Linux Libertine O-40\\:style=Semibold:text=FFmpeg'

```

- Draw "Test Text" with font size dependent on height of the video.

```
drawtext="text='Test Text': fontsize=h/30: x=(w-text_w)/2: y=(h-text_h*2)"

```

- Print the date of a real-time encoding (see documentation for the strftime C function):

```
drawtext='fontfile=FreeSans.ttf:text=%{localtime\:%a %b %d %Y}'

```

- Show text fading in and out (appearing/disappearing):

```
#!/bin/sh
DS=1.0 # display start
DE=10.0 # display end
FID=1.5 # fade in duration
FOD=5 # fade out duration
ffplay -f lavfi "color,drawtext=text=TEST:fontsize=50:fontfile=FreeSerif.ttf:fontcolor_expr=ff0000%{eif\\\\: clip(255*(1*between(t\\, $DS + $FID\\, $DE - $FOD) + ((t - $DS)/$FID)*between(t\\, $DS\\, $DS + $FID) + (-(t - $DE)/$FOD)*between(t\\, $DE - $FOD\\, $DE) )\\, 0\\, 255) \\\\: x\\\\: 2 }"

```

- Horizontally align multiple separate texts. Note that max_glyph_a and the fontsize value are included in the y offset.

```
drawtext=fontfile=FreeSans.ttf:text=DOG:fontsize=24:x=10:y=20+24-max_glyph_a,
drawtext=fontfile=FreeSans.ttf:text=cow:fontsize=24:x=80:y=20+24-max_glyph_a

```

- Plot special lavf.image2dec.source_basename metadata onto each frame if such metadata exists. Otherwise, plot the string "NA". Note that image2 demuxer must have option -export_path_metadata 1 for the special metadata fields to be available for filters.

```
drawtext="fontsize=20:fontcolor=white:fontfile=FreeSans.ttf:text='%{metadata\:lavf.image2dec.source_basename\:NA}':x=10:y=10"

```

For more information about libfreetype, check: http://www.freetype.org/.

For more information about fontconfig, check: http://freedesktop.org/software/fontconfig/fontconfig-user.html.

For more information about libfribidi, check: http://fribidi.org/.

For more information about libharfbuzz, check: https://github.com/harfbuzz/harfbuzz.

### 39.77 drawvg# TOC

Draw vector graphics on top of video frames, by executing a script written in a custom language called VGS (Vector Graphics Script).

The documentation for the language can be found in drawvg - Language Reference. A version of this reference with rendered examples can be found at the author’s site.

Graphics are rendered using the cario 2D graphics library.

To enable compilation of this filter, you need to configure FFmpeg with --enable-cairo.

#### 39.77.1 Parameters# TOC

Either script or file must be set.

s, script

Script source to draw the graphics.

file

Path of the file to load the script source.

#### 39.77.2 Pixel Formats# TOC

Since Cairo only supports RGB images, if the input video is something else (like YUV 4:2:0), before executing the script the video is converted to a format compatible with Cairo. Then, you have to use either the format filter, or the -pix_fmt option, to convert it to the expected format in the output.

#### 39.77.3 Examples# TOC

- Draw the outline of an ellipse.

```
ffmpeg -i input.webm \
    -vf 'drawvg=ellipse (w/2) (h/2) (w/3) (h/3) stroke' \
    -pix_fmt yuv420p \
    output.webm

```

-  Draw a square rotating in the middle of the frame.
The script for drawvg is in a file draw.vgs:

```
translate (w/2) (h/2)
rotate t
rect -100 -100 200 200
setcolor red@0.5
fill

```

Then:

```
ffmpeg -i input.webm -vf 'drawvg=file=draw.vgs,format=yuv420p' output.webm

```

### 39.78 edgedetect# TOC

Detect and draw edges. The filter uses the Canny Edge Detection algorithm.

The filter accepts the following options:

low

high

Set low and high threshold values used by the Canny thresholding algorithm.

The high threshold selects the "strong" edge pixels, which are then connected through 8-connectivity with the "weak" edge pixels selected by the low threshold.

low and high threshold values must be chosen in the range [0,1], and low should be lesser or equal to high.

Default value for low is 20/255, and default value for high is 50/255.

mode

Define the drawing mode.

‘wires’

Draw white/gray wires on black background.

‘colormix’

Mix the colors to create a paint/cartoon effect.

‘canny’

Apply Canny edge detector on all selected planes.

Default value is wires.

planes

Select planes for filtering. By default all available planes are filtered.

#### 39.78.1 Examples# TOC

- Standard edge detection with custom values for the hysteresis thresholding:

```
edgedetect=low=0.1:high=0.4

```

- Painting effect without thresholding:

```
edgedetect=mode=colormix:high=0

```

### 39.79 elbg# TOC

Apply a posterize effect using the ELBG (Enhanced LBG) algorithm.

For each input image, the filter will compute the optimal mapping from the input to the output given the codebook length, that is the number of distinct output colors.

This filter accepts the following options.

codebook_length, l

Set codebook length. The value must be a positive integer, and represents the number of distinct output colors. Default value is 256.

nb_steps, n

Set the maximum number of iterations to apply for computing the optimal mapping. The higher the value the better the result and the higher the computation time. Default value is 1.

seed, s

Set a random seed, must be an integer included between 0 and UINT32_MAX. If not specified, or if explicitly set to -1, the filter will try to use a good random seed on a best effort basis.

pal8

Set pal8 output pixel format. This option does not work with codebook length greater than 256. Default is disabled.

use_alpha

Include alpha values in the quantization calculation. Allows creating palettized output images (e.g. PNG8) with multiple alpha smooth blending.

### 39.80 entropy# TOC

Measure graylevel entropy in histogram of color channels of video frames.

It accepts the following parameters:

mode

Can be either normal or diff. Default is normal.

diff mode measures entropy of histogram delta values, absolute differences between neighbour histogram values.

### 39.81 epx# TOC

Apply the EPX magnification filter which is designed for pixel art.

It accepts the following option:

n

Set the scaling dimension: 2 for 2xEPX, 3 for 3xEPX. Default is 3.

### 39.82 eq# TOC

Set brightness, contrast, saturation and approximate gamma adjustment.

The filter accepts the following options:

contrast

Set the contrast expression. The value must be a float value in range -1000.0 to 1000.0. The default value is "1".

brightness

Set the brightness expression. The value must be a float value in range -1.0 to 1.0. The default value is "0".

saturation

Set the saturation expression. The value must be a float in range 0.0 to 3.0. The default value is "1".

gamma

Set the gamma expression. The value must be a float in range 0.1 to 10.0. The default value is "1".

gamma_r

Set the gamma expression for red. The value must be a float in range 0.1 to 10.0. The default value is "1".

gamma_g

Set the gamma expression for green. The value must be a float in range 0.1 to 10.0. The default value is "1".

gamma_b

Set the gamma expression for blue. The value must be a float in range 0.1 to 10.0. The default value is "1".

gamma_weight

Set the gamma weight expression. It can be used to reduce the effect of a high gamma value on bright image areas, e.g. keep them from getting overamplified and just plain white. The value must be a float in range 0.0 to 1.0. A value of 0.0 turns the gamma correction all the way down while 1.0 leaves it at its full strength. Default is "1".

eval

Set when the expressions for brightness, contrast, saturation and gamma expressions are evaluated.

It accepts the following values:

‘init’

only evaluate expressions once during the filter initialization or when a command is processed

‘frame’

evaluate expressions for each incoming frame

Default value is ‘init’.

The expressions accept the following parameters:

n

frame count of the input frame starting from 0

pos

byte position of the corresponding packet in the input file, NAN if unspecified; deprecated, do not use

r

frame rate of the input video, NAN if the input frame rate is unknown

t

timestamp expressed in seconds, NAN if the input timestamp is unknown

#### 39.82.1 Commands# TOC

The filter supports the following commands:

contrast

Set the contrast expression.

brightness

Set the brightness expression.

saturation

Set the saturation expression.

gamma

Set the gamma expression.

gamma_r

Set the gamma_r expression.

gamma_g

Set gamma_g expression.

gamma_b

Set gamma_b expression.

gamma_weight

Set gamma_weight expression.

The command accepts the same syntax of the corresponding option.

If the specified expression is not valid, it is kept at its current value.

### 39.83 erosion# TOC

Apply erosion effect to the video.

This filter replaces the pixel by the local(3x3) minimum.

It accepts the following options:

threshold0

threshold1

threshold2

threshold3

Limit the maximum change for each plane, default is 65535. If 0, plane will remain unchanged.

coordinates

Flag which specifies the pixel to refer to. Default is 255 i.e. all eight pixels are used.

Flags to local 3x3 coordinates maps like this:

1 2 3 4 5 6 7 8

#### 39.83.1 Commands# TOC

This filter supports the all above options as commands.

### 39.84 estdif# TOC

Deinterlace the input video ("estdif" stands for "Edge Slope Tracing Deinterlacing Filter").

Spatial only filter that uses edge slope tracing algorithm to interpolate missing lines. It accepts the following parameters:

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

all

Deinterlace all frames.

interlaced

Only deinterlace frames marked as interlaced.

The default value is all.

rslope

Specify the search radius for edge slope tracing. Default value is 1. Allowed range is from 1 to 15.

redge

Specify the search radius for best edge matching. Default value is 2. Allowed range is from 0 to 15.

ecost

Specify the edge cost for edge matching. Default value is 2. Allowed range is from 0 to 50.

mcost

Specify the middle cost for edge matching. Default value is 1. Allowed range is from 0 to 50.

dcost

Specify the distance cost for edge matching. Default value is 1. Allowed range is from 0 to 50.

interp

Specify the interpolation used. Default is 4-point interpolation. It accepts one of the following values:

2p

Two-point interpolation.

4p

Four-point interpolation.

6p

Six-point interpolation.

#### 39.84.1 Commands# TOC

This filter supports same commands as options.

### 39.85 exposure# TOC

Adjust exposure of the video stream.

The filter accepts the following options:

exposure

Set the exposure correction in EV. Allowed range is from -3.0 to 3.0 EV Default value is 0 EV.

black

Set the black level correction. Allowed range is from -1.0 to 1.0. Default value is 0.

#### 39.85.1 Commands# TOC

This filter supports same commands as options.

### 39.86 extractplanes# TOC

Extract color channel components from input video stream into separate grayscale video streams.

The filter accepts the following option:

planes

Set plane(s) to extract.

Available values for planes are:

‘y’

‘u’

‘v’

‘a’

‘r’

‘g’

‘b’

Choosing planes not available in the input will result in an error. That means you cannot select r, g, b planes with y, u, v planes at same time.

#### 39.86.1 Examples# TOC

- Extract luma, u and v color channel component from input video frame into 3 grayscale outputs:

```
ffmpeg -i video.avi -filter_complex 'extractplanes=y+u+v[y][u][v]' -map '[y]' y.avi -map '[u]' u.avi -map '[v]' v.avi

```

### 39.87 fade# TOC

Apply a fade-in/out effect to the input video.

It accepts the following parameters:

type, t

The effect type can be either "in" for a fade-in, or "out" for a fade-out effect. Default is in.

start_frame, s

Specify the number of the frame to start applying the fade effect at. Default is 0.

nb_frames, n

The number of frames that the fade effect lasts. At the end of the fade-in effect, the output video will have the same intensity as the input video. At the end of the fade-out transition, the output video will be filled with the selected color. Default is 25.

alpha

If set to 1, fade only alpha channel, if one exists on the input. Default value is 0.

start_time, st

Specify the timestamp (in seconds) of the frame to start to apply the fade effect. If both start_frame and start_time are specified, the fade will start at whichever comes last. Default is 0.

duration, d

The number of seconds for which the fade effect has to last. At the end of the fade-in effect the output video will have the same intensity as the input video, at the end of the fade-out transition the output video will be filled with the selected color. If both duration and nb_frames are specified, duration is used. Default is 0 (nb_frames is used by default).

color, c

Specify the color of the fade. Default is "black".

#### 39.87.1 Examples# TOC

- Fade in the first 30 frames of video:

```
fade=in:0:30

```

The command above is equivalent to:

```
fade=t=in:s=0:n=30

```

- Fade out the last 45 frames of a 200-frame video:

```
fade=out:155:45
fade=type=out:start_frame=155:nb_frames=45

```

- Fade in the first 25 frames and fade out the last 25 frames of a 1000-frame video:

```
fade=in:0:25, fade=out:975:25

```

- Make the first 5 frames yellow, then fade in from frame 5-24:

```
fade=in:5:20:color=yellow

```

- Fade in alpha over first 25 frames of video:

```
fade=in:0:25:alpha=1

```

- Make the first 5.5 seconds black, then fade in for 0.5 seconds:

```
fade=t=in:st=5.5:d=0.5

```

### 39.88 feedback# TOC

Apply feedback video filter.

This filter pass cropped input frames to 2nd output. From there it can be filtered with other video filters. After filter receives frame from 2nd input, that frame is combined on top of original frame from 1st input and passed to 1st output.

The typical usage is filter only part of frame.

The filter accepts the following options:

x

y

Set the top left crop position.

w

h

Set the crop size.

#### 39.88.1 Examples# TOC

- Blur only top left rectangular part of video frame size 100x100 with gblur filter.

```
[in][blurin]feedback=x=0:y=0:w=100:h=100[out][blurout];[blurout]gblur=8[blurin]

```

- Draw black box on top left part of video frame of size 100x100 with drawbox filter.

```
[in][blurin]feedback=x=0:y=0:w=100:h=100[out][blurout];[blurout]drawbox=x=0:y=0:w=100:h=100:t=100[blurin]

```

- Pixelize rectangular part of video frame of size 100x100 with pixelize filter.

```
[in][blurin]feedback=x=320:y=240:w=100:h=100[out][blurout];[blurout]pixelize[blurin]

```

### 39.89 fftdnoiz# TOC

Denoise frames using 3D FFT (frequency domain filtering).

The filter accepts the following options:

sigma

Set the noise sigma constant. This sets denoising strength. Default value is 1. Allowed range is from 0 to 30. Using very high sigma with low overlap may give blocking artifacts.

amount

Set amount of denoising. By default all detected noise is reduced. Default value is 1. Allowed range is from 0 to 1.

block

Set size of block in pixels, Default is 32, can be 8 to 256.

overlap

Set block overlap. Default is 0.5. Allowed range is from 0.2 to 0.8.

method

Set denoising method. Default is wiener, can also be hard.

prev

Set number of previous frames to use for denoising. By default is set to 0.

next

Set number of next frames to to use for denoising. By default is set to 0.

planes

Set planes which will be filtered, by default are all available filtered except alpha.

### 39.90 fftfilt# TOC

Apply arbitrary expressions to samples in frequency domain

dc_Y

Adjust the dc value (gain) of the luma plane of the image. The filter accepts an integer value in range 0 to 1000. The default value is set to 0.

dc_U

Adjust the dc value (gain) of the 1st chroma plane of the image. The filter accepts an integer value in range 0 to 1000. The default value is set to 0.

dc_V

Adjust the dc value (gain) of the 2nd chroma plane of the image. The filter accepts an integer value in range 0 to 1000. The default value is set to 0.

weight_Y

Set the frequency domain weight expression for the luma plane.

weight_U

Set the frequency domain weight expression for the 1st chroma plane.

weight_V

Set the frequency domain weight expression for the 2nd chroma plane.

eval

Set when the expressions are evaluated.

It accepts the following values:

‘init’

Only evaluate expressions once during the filter initialization.

‘frame’

Evaluate expressions for each incoming frame.

Default value is ‘init’.

The filter accepts the following variables:

X

Y

The coordinates of the current sample.

W

H

The width and height of the image.

N

The number of input frame, starting from 0.

WS

HS

The size of FFT array for horizontal and vertical processing.

#### 39.90.1 Examples# TOC

- High-pass:

```
fftfilt=dc_Y=128:weight_Y='squish(1-(Y+X)/100)'

```

- Low-pass:

```
fftfilt=dc_Y=0:weight_Y='squish((Y+X)/100-1)'

```

- Sharpen:

```
fftfilt=dc_Y=0:weight_Y='1+squish(1-(Y+X)/100)'

```

- Blur:

```
fftfilt=dc_Y=0:weight_Y='exp(-4 * ((Y+X)/(W+H)))'

```

### 39.91 field# TOC

Extract a single field from an interlaced image using stride arithmetic to avoid wasting CPU time. The output frames are marked as non-interlaced.

The filter accepts the following options:

type

Specify whether to extract the top (if the value is 0 or top) or the bottom field (if the value is 1 or bottom).

### 39.92 fieldhint# TOC

Create new frames by copying the top and bottom fields from surrounding frames supplied as numbers by the hint file.

hint

Set file containing hints: absolute/relative frame numbers.

There must be one line for each frame in a clip. Each line must contain two numbers separated by the comma, optionally followed by - or +. Numbers supplied on each line of file can not be out of [N-1,N+1] where N is current frame number for absolute mode or out of [-1, 1] range for relative mode. First number tells from which frame to pick up top field and second number tells from which frame to pick up bottom field.

If optionally followed by + output frame will be marked as interlaced, else if followed by - output frame will be marked as progressive, else it will be marked same as input frame. If optionally followed by t output frame will use only top field, or in case of b it will use only bottom field. If line starts with # or ; that line is skipped.

mode

Can be item absolute or relative or pattern. Default is absolute. The pattern mode is same as relative mode, except at last entry of file if there are more frames to process than hint file is seek back to start.

Example of first several lines of hint file for relative mode:

```
0,0 - # first frame
1,0 - # second frame, use third's frame top field and second's frame bottom field
1,0 - # third frame, use fourth's frame top field and third's frame bottom field
1,0 -
0,0 -
0,0 -
1,0 -
1,0 -
1,0 -
0,0 -
0,0 -
1,0 -
1,0 -
1,0 -
0,0 -

```

### 39.93 fieldmatch# TOC

Field matching filter for inverse telecine. It is meant to reconstruct the progressive frames from a telecined stream. The filter does not drop duplicated frames, so to achieve a complete inverse telecine fieldmatch needs to be followed by a decimation filter such as decimate in the filtergraph.

The separation of the field matching and the decimation is notably motivated by the possibility of inserting a de-interlacing filter fallback between the two. If the source has mixed telecined and real interlaced content, fieldmatch will not be able to match fields for the interlaced parts. But these remaining combed frames will be marked as interlaced, and thus can be de-interlaced by a later filter such as yadif before decimation.

In addition to the various configuration options, fieldmatch can take an optional second stream, activated through the ppsrc option. If enabled, the frames reconstruction will be based on the fields and frames from this second stream. This allows the first input to be pre-processed in order to help the various algorithms of the filter, while keeping the output lossless (assuming the fields are matched properly). Typically, a field-aware denoiser, or brightness/contrast adjustments can help.

Note that this filter uses the same algorithms as TIVTC/TFM (AviSynth project) and VIVTC/VFM (VapourSynth project). The later is a light clone of TFM from which fieldmatch is based on. While the semantic and usage are very close, some behaviour and options names can differ.

The decimate filter currently only works for constant frame rate input. If your input has mixed telecined (30fps) and progressive content with a lower framerate like 24fps use the following filterchain to produce the necessary cfr stream: dejudder,fps=30000/1001,fieldmatch,decimate.

The filter accepts the following options:

order

Specify the assumed field order of the input stream. Available values are:

‘auto’

Auto detect parity (use FFmpeg’s internal parity value).

‘bff’

Assume bottom field first.

‘tff’

Assume top field first.

Note that it is sometimes recommended not to trust the parity announced by the stream.

Default value is auto.

mode

Set the matching mode or strategy to use. pc mode is the safest in the sense that it won’t risk creating jerkiness due to duplicate frames when possible, but if there are bad edits or blended fields it will end up outputting combed frames when a good match might actually exist. On the other hand, pcn_ub mode is the most risky in terms of creating jerkiness, but will almost always find a good frame if there is one. The other values are all somewhere in between pc and pcn_ub in terms of risking jerkiness and creating duplicate frames versus finding good matches in sections with bad edits, orphaned fields, blended fields, etc.

More details about p/c/n/u/b are available in p/c/n/u/b meaning section.

Available values are:

‘pc’

2-way matching (p/c)

‘pc_n’

2-way matching, and trying 3rd match if still combed (p/c + n)

‘pc_u’

2-way matching, and trying 3rd match (same order) if still combed (p/c + u)

‘pc_n_ub’

2-way matching, trying 3rd match if still combed, and trying 4th/5th matches if still combed (p/c + n + u/b)

‘pcn’

3-way matching (p/c/n)

‘pcn_ub’

3-way matching, and trying 4th/5th matches if all 3 of the original matches are detected as combed (p/c/n + u/b)

The parenthesis at the end indicate the matches that would be used for that mode assuming order=tff (and field on auto or top).

In terms of speed pc mode is by far the fastest and pcn_ub is the slowest.

Default value is pc_n.

ppsrc

Mark the main input stream as a pre-processed input, and enable the secondary input stream as the clean source to pick the fields from. See the filter introduction for more details. It is similar to the clip2 feature from VFM/TFM.

Default value is 0 (disabled).

field

Set the field to match from. It is recommended to set this to the same value as order unless you experience matching failures with that setting. In certain circumstances changing the field that is used to match from can have a large impact on matching performance. Available values are:

‘auto’

Automatic (same value as order).

‘bottom’

Match from the bottom field.

‘top’

Match from the top field.

Default value is auto.

mchroma

Set whether or not chroma is included during the match comparisons. In most cases it is recommended to leave this enabled. You should set this to 0 only if your clip has bad chroma problems such as heavy rainbowing or other artifacts. Setting this to 0 could also be used to speed things up at the cost of some accuracy.

Default value is 1.

y0

y1

These define an exclusion band which excludes the lines between y0 and y1 from being included in the field matching decision. An exclusion band can be used to ignore subtitles, a logo, or other things that may interfere with the matching. y0 sets the starting scan line and y1 sets the ending line; all lines in between y0 and y1 (including y0 and y1) will be ignored. Setting y0 and y1 to the same value will disable the feature. y0 and y1 defaults to 0.

scthresh

Set the scene change detection threshold as a percentage of maximum change on the luma plane. Good values are in the [8.0, 14.0] range. Scene change detection is only relevant in case combmatch=sc. The range for scthresh is [0.0, 100.0].

Default value is 12.0.

combmatch

When combatch is not none, fieldmatch will take into account the combed scores of matches when deciding what match to use as the final match. Available values are:

‘none’

No final matching based on combed scores.

‘sc’

Combed scores are only used when a scene change is detected.

‘full’

Use combed scores all the time.

Default is sc.

combdbg

Force fieldmatch to calculate the combed metrics for certain matches and print them. This setting is known as micout in TFM/VFM vocabulary. Available values are:

‘none’

No forced calculation.

‘pcn’

Force p/c/n calculations.

‘pcnub’

Force p/c/n/u/b calculations.

Default value is none.

cthresh

This is the area combing threshold used for combed frame detection. This essentially controls how "strong" or "visible" combing must be to be detected. Larger values mean combing must be more visible and smaller values mean combing can be less visible or strong and still be detected. Valid settings are from -1 (every pixel will be detected as combed) to 255 (no pixel will be detected as combed). This is basically a pixel difference value. A good range is [8, 12].

Default value is 9.

chroma

Sets whether or not chroma is considered in the combed frame decision. Only disable this if your source has chroma problems (rainbowing, etc.) that are causing problems for the combed frame detection with chroma enabled. Actually, using chroma=0 is usually more reliable, except for the case where there is chroma only combing in the source.

Default value is 0.

blockx

blocky

Respectively set the x-axis and y-axis size of the window used during combed frame detection. This has to do with the size of the area in which combpel pixels are required to be detected as combed for a frame to be declared combed. See the combpel parameter description for more info. Possible values are any number that is a power of 2 starting at 4 and going up to 512.

Default value is 16.

combpel

The number of combed pixels inside any of the blocky by blockx size blocks on the frame for the frame to be detected as combed. While cthresh controls how "visible" the combing must be, this setting controls "how much" combing there must be in any localized area (a window defined by the blockx and blocky settings) on the frame. Minimum value is 0 and maximum is blocky x blockx (at which point no frames will ever be detected as combed). This setting is known as MI in TFM/VFM vocabulary.

Default value is 80.

#### 39.93.1 p/c/n/u/b meaning# TOC

#### 39.93.1.1 p/c/n# TOC

We assume the following telecined stream:

```
Top fields:     1 2 2 3 4
Bottom fields:  1 2 3 4 4

```

The numbers correspond to the progressive frame the fields relate to. Here, the first two frames are progressive, the 3rd and 4th are combed, and so on.

When fieldmatch is configured to run a matching from bottom (field=bottom) this is how this input stream get transformed:

```
Input stream:
                T     1 2 2 3 4
                B     1 2 3 4 4   <-- matching reference

Matches:              c c n n c

Output stream:
                T     1 2 3 4 4
                B     1 2 3 4 4

```

As a result of the field matching, we can see that some frames get duplicated. To perform a complete inverse telecine, you need to rely on a decimation filter after this operation. See for instance the decimate filter.

The same operation now matching from top fields (field=top) looks like this:

```
Input stream:
                T     1 2 2 3 4   <-- matching reference
                B     1 2 3 4 4

Matches:              c c p p c

Output stream:
                T     1 2 2 3 4
                B     1 2 2 3 4

```

In these examples, we can see what p, c and n mean; basically, they refer to the frame and field of the opposite parity:

- p matches the field of the opposite parity in the previous frame

- c matches the field of the opposite parity in the current frame

- n matches the field of the opposite parity in the next frame

#### 39.93.1.2 u/b# TOC

The u and b matching are a bit special in the sense that they match from the opposite parity flag. In the following examples, we assume that we are currently matching the 2nd frame (Top:2, bottom:2). According to the match, a ’x’ is placed above and below each matched fields.

With bottom matching (field=bottom):

```
Match:           c         p           n          b          u

                 x       x               x        x          x
  Top          1 2 2     1 2 2       1 2 2      1 2 2      1 2 2
  Bottom       1 2 3     1 2 3       1 2 3      1 2 3      1 2 3
                 x         x           x        x              x

Output frames:
                 2          1          2          2          2
                 2          2          2          1          3

```

With top matching (field=top):

```
Match:           c         p           n          b          u

                 x         x           x        x              x
  Top          1 2 2     1 2 2       1 2 2      1 2 2      1 2 2
  Bottom       1 2 3     1 2 3       1 2 3      1 2 3      1 2 3
                 x       x               x        x          x

Output frames:
                 2          2          2          1          2
                 2          1          3          2          2

```

#### 39.93.2 Examples# TOC

Simple IVTC of a top field first telecined stream:

```
fieldmatch=order=tff:combmatch=none, decimate

```

Advanced IVTC, with fallback on yadif for still combed frames:

```
fieldmatch=order=tff:combmatch=full, yadif=deint=interlaced, decimate

```

### 39.94 fieldorder# TOC

Transform the field order of the input video.

It accepts the following parameters:

order

The output field order. Valid values are tff for top field first or bff for bottom field first.

The default value is ‘tff’.

The transformation is done by shifting the picture content up or down by one line, and filling the remaining line with appropriate picture content. This method is consistent with most broadcast field order converters.

If the input video is not flagged as being interlaced, or it is already flagged as being of the required output field order, then this filter does not alter the incoming video.

It is very useful when converting to or from PAL DV material, which is bottom field first.

For example:

```
ffmpeg -i in.vob -vf "fieldorder=bff" out.dv

```

### 39.95 fillborders# TOC

Fill borders of the input video, without changing video stream dimensions. Sometimes video can have garbage at the four edges and you may not want to crop video input to keep size multiple of some number.

This filter accepts the following options:

left

Number of pixels to fill from left border.

right

Number of pixels to fill from right border.

top

Number of pixels to fill from top border.

bottom

Number of pixels to fill from bottom border.

mode

Set fill mode.

It accepts the following values:

‘smear’

fill pixels using outermost pixels

‘mirror’

fill pixels using mirroring (half sample symmetric)

‘fixed’

fill pixels with constant value

‘reflect’

fill pixels using reflecting (whole sample symmetric)

‘wrap’

fill pixels using wrapping

‘fade’

fade pixels to constant value

‘margins’

fill pixels at top and bottom with weighted averages pixels near borders

Default is smear.

color

Set color for pixels in fixed or fade mode. Default is black.

#### 39.95.1 Commands# TOC

This filter supports same commands as options. The command accepts the same syntax of the corresponding option.

If the specified expression is not valid, it is kept at its current value.

### 39.96 find_rect# TOC

Find a rectangular object in the input video.

The object to search for must be specified as a gray8 image specified with the object option.

For each possible match, a score is computed. If the score reaches the specified threshold, the object is considered found.

If the input video contains multiple instances of the object, the filter will find only one of them.

When an object is found, the following metadata entries are set in the matching frame:

lavfi.rect.w

width of object

lavfi.rect.h

height of object

lavfi.rect.x

x position of object

lavfi.rect.y

y position of object

lavfi.rect.score

match score of the found object

It accepts the following options:

object

Filepath of the object image, needs to be in gray8.

threshold

Detection threshold, expressed as a decimal number in the range 0-1.

A threshold value of 0.01 means only exact matches, a threshold of 0.99 means almost everything matches.

Default value is 0.5.

mipmaps

Number of mipmaps, default is 3.

xmin, ymin, xmax, ymax

Specifies the rectangle in which to search.

discard

Discard frames where object is not detected. Default is disabled.

#### 39.96.1 Examples# TOC

- Cover a rectangular object by the supplied image of a given video using ffmpeg:

```
ffmpeg -i file.ts -vf find_rect=newref.pgm,cover_rect=cover.jpg:mode=cover new.mkv

```

- Find the position of an object in each frame using ffprobe and write it to a log file:

```
ffprobe -f lavfi movie=test.mp4,find_rect=object=object.pgm:threshold=0.3 \
  -show_entries frame=pkt_pts_time:frame_tags=lavfi.rect.x,lavfi.rect.y \
  -of csv -o find_rect.csv

```

### 39.97 floodfill# TOC

Flood area with values of same pixel components with another values.

It accepts the following options:

x

Set pixel x coordinate.

y

Set pixel y coordinate.

s0

Set source #0 component value.

s1

Set source #1 component value.

s2

Set source #2 component value.

s3

Set source #3 component value.

d0

Set destination #0 component value.

d1

Set destination #1 component value.

d2

Set destination #2 component value.

d3

Set destination #3 component value.

### 39.98 format# TOC

Convert the input video to one of the specified pixel formats. Libavfilter will try to pick one that is suitable as input to the next filter.

It accepts the following parameters:

pix_fmts

A ’|’-separated list of pixel format names, such as "pix_fmts=yuv420p|monow|rgb24".

color_spaces

A ’|’-separated list of color space names, such as "color_spaces=bt709|bt470bg|bt2020nc".

color_ranges

A ’|’-separated list of color range names, such as "color_ranges=tv|pc".

alpha_modes

A ’|’-separated list of color range names, such as "alpha_modes=straight|premultiplied".

chroma_locations

A ’|’-separated list of chroma sample location names, such as "chroma_locations=left|topleft".

#### 39.98.1 Examples# TOC

- Convert the input video to the yuv420p format

```
format=pix_fmts=yuv420p

```

Convert the input video to any of the formats in the list

```
format=pix_fmts=yuv420p|yuv444p|yuv410p

```

### 39.99 fps# TOC

Convert the video to specified constant frame rate by duplicating or dropping frames as necessary.

It accepts the following parameters:

fps

The desired output frame rate. It accepts expressions containing the following constants:

‘source_fps’

The input’s frame rate

‘ntsc’

NTSC frame rate of 30000/1001

‘pal’

PAL frame rate of 25.0

‘film’

Film frame rate of 24.0

‘ntsc_film’

NTSC-film frame rate of 24000/1001

The default is 25.

start_time

Assume the first PTS should be the given value, in seconds. This allows for padding/trimming at the start of stream. By default, no assumption is made about the first frame’s expected PTS, so no padding or trimming is done. For example, this could be set to 0 to pad the beginning with duplicates of the first frame if a video stream starts after the audio stream or to trim any frames with a negative PTS.

round

Timestamp (PTS) rounding method.

Possible values are:

zero

round towards 0

inf

round away from 0

down

round towards -infinity

up

round towards +infinity

near

round to nearest

The default is near.

eof_action

Action performed when reading the last frame.

Possible values are:

round

Use same timestamp rounding method as used for other frames.

pass

Pass through last frame if input duration has not been reached yet.

The default is round.

If timestamp rounding would otherwise discard every frame, one frame is retained when its rounded timestamp equals both the first output timestamp and the rounded end of input. This exception extends the output beyond the rounded end of input by one output frame period. Frames whose entire interval is trimmed by start_time remain discarded.

Alternatively, the options can be specified as a flat string: fps[:start_time[:round]].

See also the setpts filter.

#### 39.99.1 Examples# TOC

- A typical usage in order to set the fps to 25:

```
fps=fps=25

```

- Sets the fps to 24, using abbreviation and rounding method to round to nearest:

```
fps=fps=film:round=near

```

### 39.100 framepack# TOC

Pack two different video streams into a stereoscopic video, setting proper metadata on supported codecs. The two views should have the same size and framerate and processing will stop when the shorter video ends. Please note that you may conveniently adjust view properties with the scale and fps filters.

It accepts the following parameters:

format

The desired packing format. Supported values are:

sbs

The views are next to each other (default).

tab

The views are on top of each other.

lines

The views are packed by line.

columns

The views are packed by column.

frameseq

The views are temporally interleaved.

Some examples:

```
# Convert left and right views into a frame-sequential video
ffmpeg -i LEFT -i RIGHT -filter_complex framepack=frameseq OUTPUT

# Convert views into a side-by-side video with the same output resolution as the input
ffmpeg -i LEFT -i RIGHT -filter_complex [0:v]scale=w=iw/2[left],[1:v]scale=w=iw/2[right],[left][right]framepack=sbs OUTPUT

```

### 39.101 framerate# TOC

Change the frame rate by interpolating new video output frames from the source frames.

This filter is not designed to function correctly with interlaced media. If you wish to change the frame rate of interlaced media then you are required to deinterlace before this filter and re-interlace after this filter.

A description of the accepted options follows.

fps

Specify the output frames per second. This option can also be specified as a value alone. The default is 50.

interp_start

Specify the start of a range where the output frame will be created as a linear interpolation of two frames. The range is [0-255], the default is 15.

interp_end

Specify the end of a range where the output frame will be created as a linear interpolation of two frames. The range is [0-255], the default is 240.

scene

Specify the level at which a scene change is detected as a value between 0 and 100 to indicate a new scene; a low value reflects a low probability for the current frame to introduce a new scene, while a higher value means the current frame is more likely to be one. The default is 8.2.

flags

Specify flags influencing the filter process.

Available value for flags is:

scene_change_detect, scd

Enable scene change detection using the value of the option scene. This flag is enabled by default.

### 39.102 frc_amf# TOC

Double the frame rate, using Frame Rate Converter (FRC) provided by AMD Advanced Media Framework library for hardware acceleration.

The filter accepts the following options:

engine_type

Specify the engine used to run shaders.

‘dx11’

DirectX 11.

‘dx12’

DirectX 12 (Default value).

enable

Boolean value: enable/disable FRC. Dynamic value, can be altered at a runtime without re-initializing the filter. (Default value: enabled).

fallback_mode

Fallback behavior in case of low interpolation confidence.

‘duplicate’

Duplicate frame.

‘blend’

Blend two frames together (Default value).

indicator

Boolean value: show FRC indicator square in the top left corner of the video (Default value: disabled).

profile

Level of hierarchical motion search.

‘low’

Less levels of hierarchical motion search. Only recommended for extremely low resolutions.

‘high’

Recommended for any resolution up to 1440p. (Default value)

‘super’

More levels of hierarchical motion search. Recommended for resolutions 1440p or higher.

mv_search_mode

Performance mode of the motion search.

‘native’

Conduct motion search on the full resolution of source images.

‘performance’

Conduct motion search on the down scaled source images. Recommended for APU or low end GPU for better performance.

use_future_frame

Boolean value: enable dependency on future frame, improves quality for the cost of latency (Default value: enabled).

### 39.103 vqe_amf# TOC

AMD AMF VQ Enhancer filter. This filter applies AMD AMF VQ Enhancement to the input video.

This filter accepts the following option:

attenuation

Set VQ Enhancer strength. Allowed range is from 0.02 to 0.4. Default is 0.1.

engine_type

Set AMF memory type used by the filter.

Possible values:

‘dx11’

DirectX 11

‘dx12’

DirectX 12

‘vulkan’

Vulkan

‘opencl’

OpenCL

Example:

```
ffmpeg -i input.mp4 -vf vqe_amf=attenuation=0.4 -c:v hevc_amf output.mp4

```

### 39.104 framestep# TOC

Select one frame every N-th frame.

This filter accepts the following option:

step

Select frame after every step frames. Allowed values are positive integers higher than 0. Default value is 1.

### 39.105 freezedetect# TOC

Detect frozen video.

This filter logs a message and sets frame metadata when it detects that the input video has no significant change in content during a specified duration. Video freeze detection calculates the mean average absolute difference of all the components of video frames and compares it to a noise floor.

The printed times and duration are expressed in seconds. The lavfi.freezedetect.freeze_start metadata key is set on the first frame whose timestamp equals or exceeds the detection duration and it contains the timestamp of the first frame of the freeze. The lavfi.freezedetect.freeze_duration and lavfi.freezedetect.freeze_end metadata keys are set on the first frame after the freeze.

The filter accepts the following options:

noise, n

Set noise tolerance. Can be specified in dB (in case "dB" is appended to the specified value) or as a difference ratio between 0 and 1. Default is -60dB, or 0.001.

duration, d

Set freeze duration until notification (default is 2 seconds).

### 39.106 freezeframes# TOC

Freeze video frames.

This filter freezes video frames using frame from 2nd input.

The filter accepts the following options:

first

Set number of first frame from which to start freeze.

last

Set number of last frame from which to end freeze.

replace

Set number of frame from 2nd input which will be used instead of replaced frames.

### 39.107 frei0r# TOC

Apply a frei0r effect to the input video.

To enable the compilation of this filter, you need to install the frei0r header and configure FFmpeg with --enable-frei0r.

It accepts the following parameters:

filter_name

The name of the frei0r effect to load. If the environment variable FREI0R_PATH is defined, the frei0r effect is searched for in each of the directories specified by the colon-separated list in FREI0R_PATH. Otherwise, the standard frei0r paths are searched, in this order: HOME/.frei0r-1/lib/, /usr/local/lib/frei0r-1/, /usr/lib/frei0r-1/.

filter_params

A ’|’-separated list of parameters to pass to the frei0r effect.

A frei0r effect parameter can be a boolean (its value is either "y" or "n"), a double, a color (specified as R/G/B, where R, G, and B are floating point numbers between 0.0 and 1.0, inclusive) or a color description as specified in the "Color" section in the ffmpeg-utils manual, a position (specified as X/Y, where X and Y are floating point numbers) and/or a string.

The number and types of parameters depend on the loaded effect. If an effect parameter is not specified, the default value is set.

#### 39.107.1 Examples# TOC

- Apply the distort0r effect, setting the first two double parameters:

```
frei0r=filter_name=distort0r:filter_params=0.5|0.01

```

- Apply the colordistance effect, taking a color as the first parameter:

```
frei0r=colordistance:0.2/0.3/0.4
frei0r=colordistance:violet
frei0r=colordistance:0x112233

```

- Apply the perspective effect, specifying the top left and top right image positions:

```
frei0r=perspective:0.2/0.2|0.8/0.2

```

For more information, see http://frei0r.dyne.org

#### 39.107.2 Commands# TOC

This filter supports the filter_params option as commands.

### 39.108 fspp# TOC

Apply fast and simple postprocessing. It is a faster version of spp.

It splits (I)DCT into horizontal/vertical passes. Unlike the simple post- processing filter, one of them is performed once per block, not per pixel. This allows for much higher speed.

The filter accepts the following options:

quality

Set quality. This option defines the number of levels for averaging. It accepts an integer in the range 4-5. Default value is 4.

qp

Force a constant quantization parameter. It accepts an integer in range 0-63. If not set, the filter will use the QP from the video stream (if available).

strength

Set filter strength. It accepts an integer in range -15 to 32. Lower values mean more details but also more artifacts, while higher values make the image smoother but also blurrier. Default value is 0 − PSNR optimal.

use_bframe_qp

Enable the use of the QP from the B-Frames if set to 1. Using this option may cause flicker since the B-Frames have often larger QP. Default is 0 (not enabled).

### 39.109 fsync# TOC

Synchronize video frames with an external mapping from a file.

For each input PTS given in the map file it either drops or creates as many frames as necessary to recreate the sequence of output frames given in the map file.

This filter is useful to recreate the output frames of a framerate conversion by the fps filter, recorded into a map file using the ffmpeg option -stats_mux_pre, and do further processing to the corresponding frames e.g. quality comparison.

Each line of the map file must contain three items per input frame, the input PTS (decimal), the output PTS (decimal) and the output TIMEBASE (decimal/decimal), separated by a space. This file format corresponds to the output of -stats_mux_pre_fmt="{ptsi} {pts} {tb}".

The filter assumes the map file is sorted by increasing input PTS.

The filter accepts the following options:

file, f

The filename of the map file to be used.

Example:

```
# Convert a video to 25 fps and record a MAP_FILE file with the default format of this filter
ffmpeg -i INPUT -vf fps=fps=25 -stats_mux_pre MAP_FILE -stats_mux_pre_fmt "{ptsi} {pts} {tb}" OUTPUT

# Sort MAP_FILE by increasing input PTS
sort -n MAP_FILE

# Use INPUT, OUTPUT and the MAP_FILE from above to compare the corresponding frames in INPUT and OUTPUT via SSIM
ffmpeg -i INPUT -i OUTPUT -filter_complex '[0:v]fsync=file=MAP_FILE[ref];[1:v][ref]ssim' -f null -

```

### 39.110 gainmap# TOC

Compute an HDR gain map from two renditions of the same image, as defined by ISO 21496-1.

The first input is the base rendition (typically SDR), and the second input is the alternate rendition (typically HDR). Both must have the same dimensions. Outputs a gain map, as either ‘gbrpf32’ or ‘grayf32’ depending on the chosen mode.

mode

Controls what quantity the gain map is computed against.

The accepted values are:

‘rgb’

One gain map channel per component.

‘luma’

A single gain map channel, computed from the luma.

‘maxrgb’

A single gain map channel, computed from ‘max(R, G, B)’.

Default is ‘rgb’.

colorspace

Chooses which colorspace to compute the gain map in.

The accepted values are:

‘base’

The base rendition’s colorspace.

‘alternate’

The alternate rendition’s colorspace.

Default is ‘base’.

min

max

Bounds on the encoded gain (log2). If unspecified, these will be measured from the frame.

gamma

Encoding gamma of the resulting gain map. If unspecified, this will be optimized for the frame in question. Setting this to 1.0 will produce a linear gain map, which may be more efficient in some applications.

base_offset

alt_offset

Offset to prevent numerical instability near zero. Both default to 1/64.

base_nits

alt_nits

Override the reference luminance of the input, in nits. If unspecified, uses the values from the input metadata.

The gainmap filter also supports the framesync options.

#### 39.110.1 Examples# TOC

- Compute a gain map between an SDR and an HDR version of the same image:

```
ffmpeg -i $sdr -i $hdr -filter_complex "[0:v][1:v]gainmap" $out

```

### 39.111 gblur# TOC

Apply Gaussian blur filter.

The filter accepts the following options:

sigma

Set horizontal sigma, standard deviation of Gaussian blur. Default is 0.5.

steps

Set number of steps for Gaussian approximation. Default is 1.

planes

Set which planes to filter. By default all planes are filtered.

sigmaV

Set vertical sigma, if negative it will be same as sigma. Default is -1.

#### 39.111.1 Commands# TOC

This filter supports same commands as options. The command accepts the same syntax of the corresponding option.

If the specified expression is not valid, it is kept at its current value.

### 39.112 geq# TOC

Apply generic equation to each pixel.

The filter accepts the following options:

lum_expr, lum

Set the luma expression.

cb_expr, cb

Set the chrominance blue expression.

cr_expr, cr

Set the chrominance red expression.

alpha_expr, a

Set the alpha expression.

red_expr, r

Set the red expression.

green_expr, g

Set the green expression.

blue_expr, b

Set the blue expression.

The colorspace is selected according to the specified options. If one of the lum_expr, cb_expr, or cr_expr options is specified, the filter will automatically select a YCbCr colorspace. If one of the red_expr, green_expr, or blue_expr options is specified, it will select an RGB colorspace.

If one of the chrominance expression is not defined, it falls back on the other one. If no alpha expression is specified it will evaluate to opaque value. If none of chrominance expressions are specified, they will evaluate to the luma expression.

The expressions can use the following variables and functions:

N

The sequential number of the filtered frame, starting from 0.

X

Y

The coordinates of the current sample.

W

H

The width and height of the image.

SW

SH

Width and height scale depending on the currently filtered plane. It is the ratio between the corresponding luma plane number of pixels and the current plane ones. E.g. for YUV4:2:0 the values are 1,1 for the luma plane, and 0.5,0.5 for chroma planes.

T

Time of the current frame, expressed in seconds.

p(x, y)

Return the value of the pixel at location (x,y) of the current plane.

lum(x, y)

Return the value of the pixel at location (x,y) of the luma plane.

cb(x, y)

Return the value of the pixel at location (x,y) of the blue-difference chroma plane. Return 0 if there is no such plane.

cr(x, y)

Return the value of the pixel at location (x,y) of the red-difference chroma plane. Return 0 if there is no such plane.

r(x, y)

g(x, y)

b(x, y)

Return the value of the pixel at location (x,y) of the red/green/blue component. Return 0 if there is no such component.

alpha(x, y)

Return the value of the pixel at location (x,y) of the alpha plane. Return 0 if there is no such plane.

psum(x,y), lumsum(x, y), cbsum(x,y), crsum(x,y), rsum(x,y), gsum(x,y), bsum(x,y), alphasum(x,y)

Sum of sample values in the rectangle from (0,0) to (x,y), this allows obtaining sums of samples within a rectangle. See the functions without the sum postfix.

interpolation

Set one of interpolation methods:

nearest, n

bilinear, b

Default is bilinear.

For functions, if x and y are outside the area, the value will be automatically clipped to the closer edge.

Please note that this filter can use multiple threads in which case each slice will have its own expression state. If you want to use only a single expression state because your expressions depend on previous state then you should limit the number of filter threads to 1.

#### 39.112.1 Examples# TOC

- Flip the image horizontally:

```
geq=p(W-X\,Y)

```

- Generate a bidimensional sine wave, with angle PI/3 and a wavelength of 100 pixels:

```
geq=128 + 100*sin(2*(PI/100)*(cos(PI/3)*(X-50*T) + sin(PI/3)*Y)):128:128

```

- Generate a fancy enigmatic moving light:

```
nullsrc=s=256x256,geq=random(1)/hypot(X-cos(N*0.07)*W/2-W/2\,Y-sin(N*0.09)*H/2-H/2)^2*1000000*sin(N*0.02):128:128

```

- Generate a quick emboss effect:

```
format=gray,geq=lum_expr='(p(X,Y)+(256-p(X-4,Y-4)))/2'

```

- Modify RGB components depending on pixel position:

```
geq=r='X/W*r(X,Y)':g='(1-X/W)*g(X,Y)':b='(H-Y)/H*b(X,Y)'

```

- Create a radial gradient that is the same size as the input (also see the vignette filter):

```
geq=lum=255*gauss((X/W-0.5)*3)*gauss((Y/H-0.5)*3)/gauss(0)/gauss(0),format=gray

```

### 39.113 gradfun# TOC

Fix the banding artifacts that are sometimes introduced into nearly flat regions by truncation to 8-bit color depth. Interpolate the gradients that should go where the bands are, and dither them.

It is designed for playback only. Do not use it prior to lossy compression, because compression tends to lose the dither and bring back the bands.

It accepts the following parameters:

strength

The maximum amount by which the filter will change any one pixel. This is also the threshold for detecting nearly flat regions. Acceptable values range from .51 to 64; the default value is 1.2. Out-of-range values will be clipped to the valid range.

radius

The neighborhood to fit the gradient to. A larger radius makes for smoother gradients, but also prevents the filter from modifying the pixels near detailed regions. Acceptable values are 8-32; the default value is 16. Out-of-range values will be clipped to the valid range.

Alternatively, the options can be specified as a flat string: strength[:radius]

#### 39.113.1 Examples# TOC

- Apply the filter with a 3.5 strength and radius of 8:

```
gradfun=3.5:8

```

- Specify radius, omitting the strength (which will fall-back to the default value):

```
gradfun=radius=8

```

### 39.114 graphmonitor# TOC

Show various filtergraph stats.

With this filter one can debug complete filtergraph. Especially issues with links filling with queued frames.

The filter accepts the following options:

size, s

Set video output size. Default is hd720.

opacity, o

Set video opacity. Default is 0.9. Allowed range is from 0 to 1.

mode, m

Set output mode flags.

Available values for flags are:

‘full’

No any filtering. Default.

‘compact’

Show only filters with queued frames.

‘nozero’

Show only filters with non-zero stats.

‘noeof’

Show only filters with non-eof stat.

‘nodisabled’

Show only filters that are enabled in timeline.

flags, f

Set flags which enable which stats are shown in video.

Available values for flags are:

‘none’

All flags turned off.

‘all’

All flags turned on.

‘queue’

Display number of queued frames in each link.

‘frame_count_in’

Display number of frames taken from filter.

‘frame_count_out’

Display number of frames given out from filter.

‘frame_count_delta’

Display delta number of frames between above two values.

‘pts’

Display current filtered frame pts.

‘pts_delta’

Display pts delta between current and previous frame.

‘time’

Display current filtered frame time.

‘time_delta’

Display time delta between current and previous frame.

‘timebase’

Display time base for filter link.

‘format’

Display used format for filter link.

‘size’

Display video size or number of audio channels in case of audio used by filter link.

‘rate’

Display video frame rate or sample rate in case of audio used by filter link.

‘eof’

Display link output status.

‘sample_count_in’

Display number of samples taken from filter.

‘sample_count_out’

Display number of samples given out from filter.

‘sample_count_delta’

Display delta number of samples between above two values.

‘disabled’

Show the timeline filter status.

rate, r

Set upper limit for video rate of output stream, Default value is 25. This guarantee that output video frame rate will not be higher than this value.

### 39.115 grayworld# TOC

A color constancy filter that applies color correction based on the grayworld assumption

See: https://www.researchgate.net/publication/275213614_A_New_Color_Correction_Method_for_Underwater_Imaging

The algorithm uses linear light, so input data should be linearized beforehand (and possibly correctly tagged).

```
ffmpeg -i INPUT -vf zscale=transfer=linear,grayworld,zscale=transfer=bt709,format=yuv420p OUTPUT

```

### 39.116 greyedge# TOC

A color constancy variation filter which estimates scene illumination via grey edge algorithm and corrects the scene colors accordingly.

See: https://staff.science.uva.nl/th.gevers/pub/GeversTIP07.pdf

The filter accepts the following options:

difford

The order of differentiation to be applied on the scene. Must be chosen in the range [0,2] and default value is 1.

minknorm

The Minkowski parameter to be used for calculating the Minkowski distance. Must be chosen in the range [0,20] and default value is 1. Set to 0 for getting max value instead of calculating Minkowski distance.

sigma

The standard deviation of Gaussian blur to be applied on the scene. Must be chosen in the range [0,1024.0] and default value = 1. floor( sigma * break_off_sigma(3) ) can’t be equal to 0 if difford is greater than 0.

#### 39.116.1 Examples# TOC

- Grey Edge:

```
greyedge=difford=1:minknorm=5:sigma=2

```

- Max Edge:

```
greyedge=difford=1:minknorm=0:sigma=2

```

### 39.117 guided# TOC

Apply guided filter for edge-preserving smoothing, dehazing and so on.

The filter accepts the following options:

radius

Set the box radius in pixels. Allowed range is 1 to 20. Default is 3.

eps

Set regularization parameter (with square). Allowed range is 0 to 1. Default is 0.01.

mode

Set filter mode. Can be basic or fast. Default is basic.

sub

Set subsampling ratio for fast mode. Range is 2 to 64. Default is 4. No subsampling occurs in basic mode.

guidance

Set guidance mode. Can be off or on. Default is off. If off, single input is required. If on, two inputs of the same resolution and pixel format are required. The second input serves as the guidance.

planes

Set planes to filter. Default is first only.

#### 39.117.1 Commands# TOC

This filter supports the all above options as commands.

#### 39.117.2 Examples# TOC

- Edge-preserving smoothing with guided filter:

```
ffmpeg -i in.png -vf guided out.png

```

- Dehazing, structure-transferring filtering, detail enhancement with guided filter. For the generation of guidance image, refer to paper "Guided Image Filtering". See: http://kaiminghe.com/publications/pami12guidedfilter.pdf.

```
ffmpeg -i in.png -i guidance.png -filter_complex guided=guidance=on out.png

```

### 39.118 haldclut# TOC

Apply a Hald CLUT to a video stream.

First input is the video stream to process, and second one is the Hald CLUT. The Hald CLUT input can be a simple picture or a complete video stream.

The filter accepts the following options:

clut

Set which CLUT video frames will be processed from second input stream, can be first or all. Default is all.

shortest

Force termination when the shortest input terminates. Default is 0.

repeatlast

Continue applying the last CLUT after the end of the stream. A value of 0 disable the filter after the last frame of the CLUT is reached. Default is 1.

haldclut also has the same interpolation options as lut3d (both filters share the same internals).

This filter also supports the framesync options.

More information about the Hald CLUT can be found on Eskil Steenberg’s website (Hald CLUT author) at http://www.quelsolaar.com/technology/clut.html.

#### 39.118.1 Commands# TOC

This filter supports the interp option as commands.

#### 39.118.2 Workflow examples# TOC

#### 39.118.2.1 Hald CLUT video stream# TOC

Generate an identity Hald CLUT stream altered with various effects:

```
ffmpeg -f lavfi -i haldclutsrc=8 -vf "hue=H=2*PI*t:s=sin(2*PI*t)+1, curves=cross_process" -t 10 -c:v ffv1 clut.nut

```

Note: make sure you use a lossless codec.

Then use it with haldclut to apply it on some random stream:

```
ffmpeg -f lavfi -i mandelbrot -i clut.nut -filter_complex '[0][1] haldclut' -t 20 mandelclut.mkv

```

The Hald CLUT will be applied to the 10 first seconds (duration of clut.nut), then the latest picture of that CLUT stream will be applied to the remaining frames of the mandelbrot stream.

#### 39.118.2.2 Hald CLUT with preview# TOC

A Hald CLUT is supposed to be a squared image of Level*Level*Level by Level*Level*Level pixels. For a given Hald CLUT, FFmpeg will select the biggest possible square starting at the top left of the picture. The remaining padding pixels (bottom or right) will be ignored. This area can be used to add a preview of the Hald CLUT.

Typically, the following generated Hald CLUT will be supported by the haldclut filter:

```
ffmpeg -f lavfi -i haldclutsrc=8 -vf "
   pad=iw+320 [padded_clut];
   smptebars=s=320x256, split [a][b];
   [padded_clut][a] overlay=W-320:h, curves=color_negative [main];
   [main][b] overlay=W-320" -frames:v 1 clut.png

```

It contains the original and a preview of the effect of the CLUT: SMPTE color bars are displayed on the right-top, and below the same color bars processed by the color changes.

Then, the effect of this Hald CLUT can be visualized with:

```
ffplay input.mkv -vf "movie=clut.png, [in] haldclut"

```

### 39.119 hflip# TOC

Flip the input video horizontally.

For example, to horizontally flip the input video with ffmpeg:

```
ffmpeg -i in.avi -vf "hflip" out.avi

```

### 39.120 histeq# TOC

This filter applies a global color histogram equalization on a per-frame basis.

It can be used to correct video that has a compressed range of pixel intensities. The filter redistributes the pixel intensities to equalize their distribution across the intensity range. It may be viewed as an "automatically adjusting contrast filter". This filter is useful only for correcting degraded or poorly captured source video.

The filter accepts the following options:

strength

Determine the amount of equalization to be applied. As the strength is reduced, the distribution of pixel intensities more-and-more approaches that of the input frame. The value must be a float number in the range [0,1] and defaults to 0.200.

intensity

Set the maximum intensity that can generated and scale the output values appropriately. The strength should be set as desired and then the intensity can be limited if needed to avoid washing-out. The value must be a float number in the range [0,1] and defaults to 0.210.

antibanding

Set the antibanding level. If enabled the filter will randomly vary the luminance of output pixels by a small amount to avoid banding of the histogram. Possible values are none, weak or strong. It defaults to none.

### 39.121 histogram# TOC

Compute and draw a color distribution histogram for the input video.

The computed histogram is a representation of the color component distribution in an image.

Standard histogram displays the color components distribution in an image. Displays color graph for each color component. Shows distribution of the Y, U, V, A or R, G, B components, depending on input format, in the current frame. Below each graph a color component scale meter is shown.

The filter accepts the following options:

level_height

Set height of level. Default value is 200. Allowed range is [50, 2048].

scale_height

Set height of color scale. Default value is 12. Allowed range is [0, 40].

display_mode

Set display mode. It accepts the following values:

‘stack’

Per color component graphs are placed below each other.

‘parade’

Per color component graphs are placed side by side.

‘overlay’

Presents information identical to that in the parade, except that the graphs representing color components are superimposed directly over one another.

Default is stack.

levels_mode

Set mode. Can be either linear, or logarithmic. Default is linear.

components

Set what color components to display. Default is 7.

fgopacity

Set foreground opacity. Default is 0.7.

bgopacity

Set background opacity. Default is 0.5.

colors_mode

Set colors mode. It accepts the following values:

‘whiteonblack’

‘blackonwhite’

‘whiteongray’

‘blackongray’

‘coloronblack’

‘coloronwhite’

‘colorongray’

‘blackoncolor’

‘whiteoncolor’

‘grayoncolor’

Default is whiteonblack.

#### 39.121.1 Examples# TOC

- Calculate and draw histogram:

```
ffplay -i input -vf histogram

```

### 39.122 hqdn3d# TOC

This is a high precision/quality 3d denoise filter. It aims to reduce image noise, producing smooth images and making still images really still. It should enhance compressibility.

It accepts the following optional parameters:

luma_spatial

A non-negative floating point number which specifies spatial luma strength. It defaults to 4.0.

chroma_spatial

A non-negative floating point number which specifies spatial chroma strength. It defaults to 3.0*luma_spatial/4.0.

luma_tmp

A floating point number which specifies luma temporal strength. It defaults to 6.0*luma_spatial/4.0.

chroma_tmp

A floating point number which specifies chroma temporal strength. It defaults to luma_tmp*chroma_spatial/luma_spatial.

#### 39.122.1 Commands# TOC

This filter supports same commands as options. The command accepts the same syntax of the corresponding option.

If the specified expression is not valid, it is kept at its current value.

### 39.123 hwdownload# TOC

Download hardware frames to system memory.

The input must be in hardware frames, and the output a non-hardware format. Not all formats will be supported on the output - it may be necessary to insert an additional format filter immediately following in the graph to get the output in a supported format.

### 39.124 hwmap# TOC

Map hardware frames to system memory or to another device.

This filter has several different modes of operation; which one is used depends on the input and output formats:

- Hardware frame input, normal frame output
Map the input frames to system memory and pass them to the output. If the original hardware frame is later required (for example, after overlaying something else on part of it), the hwmap filter can be used again in the next mode to retrieve it.

- Normal frame input, hardware frame output
If the input is actually a software-mapped hardware frame, then unmap it - that is, return the original hardware frame.

Otherwise, a device must be provided. Create new hardware surfaces on that device for the output, then map them back to the software format at the input and give those frames to the preceding filter. This will then act like the hwupload filter, but may be able to avoid an additional copy when the input is already in a compatible format.

- Hardware frame input and output
A device must be supplied for the output, either directly or with the derive_device option. The input and output devices must be of different types and compatible - the exact meaning of this is system-dependent, but typically it means that they must refer to the same underlying hardware context (for example, refer to the same graphics card).

If the input frames were originally created on the output device, then unmap to retrieve the original frames.

Otherwise, map the frames to the output device - create new hardware frames on the output corresponding to the frames on the input.

The following additional parameters are accepted:

mode

Set the frame mapping mode. Some combination of:

read

The mapped frame should be readable.

write

The mapped frame should be writeable.

overwrite

The mapping will always overwrite the entire frame.

This may improve performance in some cases, as the original contents of the frame need not be loaded.

direct

The mapping must not involve any copying.

Indirect mappings to copies of frames are created in some cases where either direct mapping is not possible or it would have unexpected properties. Setting this flag ensures that the mapping is direct and will fail if that is not possible.

Defaults to read+write if not specified.

derive_device type

Rather than using the device supplied at initialisation, instead derive a new device of type type from the device the input frames exist on.

reverse

In a hardware to hardware mapping, map in reverse - create frames in the sink and map them back to the source. This may be necessary in some cases where a mapping in one direction is required but only the opposite direction is supported by the devices being used.

This option is dangerous - it may break the preceding filter in undefined ways if there are any additional constraints on that filter’s output. Do not use it without fully understanding the implications of its use.

### 39.125 hwupload# TOC

Upload system memory frames to hardware surfaces.

The device to upload to must be supplied when the filter is initialised. If using ffmpeg, select the appropriate device with the -filter_hw_device option or with the derive_device option. The input and output devices must be of different types and compatible - the exact meaning of this is system-dependent, but typically it means that they must refer to the same underlying hardware context (for example, refer to the same graphics card).

The following additional parameters are accepted:

derive_device type

Rather than using the device supplied at initialisation, instead derive a new device of type type from the device the input frames exist on.

### 39.126 hwupload_cuda# TOC

Upload system memory frames to a CUDA device.

It accepts the following optional parameters:

device

The number of the CUDA device to use

### 39.127 hqx# TOC

Apply a high-quality magnification filter designed for pixel art. This filter was originally created by Maxim Stepin.

It accepts the following option:

n

Set the scaling dimension: 2 for hq2x, 3 for hq3x and 4 for hq4x. Default is 3.

### 39.128 hstack# TOC

Stack input videos horizontally.

All streams must be of same pixel format and of same height.

Note that this filter is faster than using overlay and pad filter to create same output.

The filter accepts the following option:

inputs

Set number of input streams. Default is 2.

shortest

If set to 1, force the output to terminate when the shortest input terminates. Default value is 0.

### 39.129 hsvhold# TOC

Turns a certain HSV range into gray values.

This filter measures color difference between set HSV color in options and ones measured in video stream. Depending on options, output colors can be changed to be gray or not.

The filter accepts the following options:

hue

Set the hue value which will be used in color difference calculation. Allowed range is from -360 to 360. Default value is 0.

sat

Set the saturation value which will be used in color difference calculation. Allowed range is from -1 to 1. Default value is 0.

val

Set the value which will be used in color difference calculation. Allowed range is from -1 to 1. Default value is 0.

similarity

Set similarity percentage with the key color. Allowed range is from 0 to 1. Default value is 0.01.

0.00001 matches only the exact key color, while 1.0 matches everything.

blend

Blend percentage. Allowed range is from 0 to 1. Default value is 0.

0.0 makes pixels either fully gray, or not gray at all.

Higher values result in more gray pixels, with a higher gray pixel the more similar the pixels color is to the key color.

### 39.130 hsvkey# TOC

Turns a certain HSV range into transparency.

This filter measures color difference between set HSV color in options and ones measured in video stream. Depending on options, output colors can be changed to transparent by adding alpha channel.

The filter accepts the following options:

hue

Set the hue value which will be used in color difference calculation. Allowed range is from -360 to 360. Default value is 0.

sat

Set the saturation value which will be used in color difference calculation. Allowed range is from -1 to 1. Default value is 0.

val

Set the value which will be used in color difference calculation. Allowed range is from -1 to 1. Default value is 0.

similarity

Set similarity percentage with the key color. Allowed range is from 0 to 1. Default value is 0.01.

0.00001 matches only the exact key color, while 1.0 matches everything.

blend

Blend percentage. Allowed range is from 0 to 1. Default value is 0.

0.0 makes pixels either fully transparent, or not transparent at all.

Higher values result in semi-transparent pixels, with a higher transparency the more similar the pixels color is to the key color.

### 39.131 hue# TOC

Modify the hue and/or the saturation of the input.

It accepts the following parameters:

h

Specify the hue angle as a number of degrees. It accepts an expression, and defaults to "0".

s

Specify the saturation in the [-10,10] range. It accepts an expression and defaults to "1".

H

Specify the hue angle as a number of radians. It accepts an expression, and defaults to "0".

b

Specify the brightness in the [-10,10] range. It accepts an expression and defaults to "0".

h and H are mutually exclusive, and can’t be specified at the same time.

The b, h, H and s option values are expressions containing the following constants:

n

frame count of the input frame starting from 0

pts

presentation timestamp of the input frame expressed in time base units

r

frame rate of the input video, NAN if the input frame rate is unknown

t

timestamp expressed in seconds, NAN if the input timestamp is unknown

tb

time base of the input video

#### 39.131.1 Examples# TOC

- Set the hue to 90 degrees and the saturation to 1.0:

```
hue=h=90:s=1

```

- Same command but expressing the hue in radians:

```
hue=H=PI/2:s=1

```

- Rotate hue and make the saturation swing between 0 and 2 over a period of 1 second:

```
hue="H=2*PI*t: s=sin(2*PI*t)+1"

```

- Apply a 3 seconds saturation fade-in effect starting at 0:

```
hue="s=min(t/3\,1)"

```

The general fade-in expression can be written as:

```
hue="s=min(0\, max((t-START)/DURATION\, 1))"

```

- Apply a 3 seconds saturation fade-out effect starting at 5 seconds:

```
hue="s=max(0\, min(1\, (8-t)/3))"

```

The general fade-out expression can be written as:

```
hue="s=max(0\, min(1\, (START+DURATION-t)/DURATION))"

```

#### 39.131.2 Commands# TOC

This filter supports the following commands:

b

s

h

H

Modify the hue and/or the saturation and/or brightness of the input video. The command accepts the same syntax of the corresponding option.

If the specified expression is not valid, it is kept at its current value.

### 39.132 huesaturation# TOC

Apply hue-saturation-intensity adjustments to input video stream.

This filter operates in RGB colorspace.

This filter accepts the following options:

hue

Set the hue shift in degrees to apply. Default is 0. Allowed range is from -180 to 180.

saturation

Set the saturation shift. Default is 0. Allowed range is from -1 to 1.

intensity

Set the intensity shift. Default is 0. Allowed range is from -1 to 1.

colors

Set which primary and complementary colors are going to be adjusted. This options is set by providing one or multiple values. This can select multiple colors at once. By default all colors are selected.

‘r’

Adjust reds.

‘y’

Adjust yellows.

‘g’

Adjust greens.

‘c’

Adjust cyans.

‘b’

Adjust blues.

‘m’

Adjust magentas.

‘a’

Adjust all colors.

strength

Set strength of filtering. Allowed range is from 0 to 100. Default value is 1.

rw, gw, bw

Set weight for each RGB component. Allowed range is from 0 to 1. By default is set to 0.333, 0.334, 0.333. Those options are used in saturation and lightess processing.

lightness

Set preserving lightness, by default is disabled. Adjusting hues can change lightness from original RGB triplet, with this option enabled lightness is kept at same value.

### 39.133 hysteresis# TOC

Grow first stream into second stream by connecting components. This makes it possible to build more robust edge masks.

This filter accepts the following options:

planes

Set which planes will be processed as bitmap, unprocessed planes will be copied from first stream. By default value 0xf, all planes will be processed.

threshold

Set threshold which is used in filtering. If pixel component value is higher than this value filter algorithm for connecting components is activated. By default value is 0.

The hysteresis filter also supports the framesync options.

### 39.134 iccdetect# TOC

Detect the colorspace from an embedded ICC profile (if present), and update the frame’s tags accordingly.

This filter accepts the following options:

force

If true, the frame’s existing colorspace tags will always be overridden by values detected from an ICC profile. Otherwise, they will only be assigned if they contain unknown. Enabled by default.

### 39.135 iccgen# TOC

Generate ICC profiles and attach them to frames.

This filter accepts the following options:

color_primaries

color_trc

Configure the colorspace that the ICC profile will be generated for. The default value of auto infers the value from the input frame’s metadata, defaulting to BT.709/sRGB as appropriate.

See the setparams filter for a list of possible values, but note that unknown are not valid values for this filter.

force

If true, an ICC profile will be generated even if it would overwrite an already existing ICC profile. Disabled by default.

### 39.136 identity# TOC

Obtain the identity score between two input videos.

This filter takes two input videos.

Both input videos must have the same resolution and pixel format for this filter to work correctly. Also it assumes that both inputs have the same number of frames, which are compared one by one.

The obtained per component, average, min and max identity score is printed through the logging system.

The filter stores the calculated identity scores of each frame in frame metadata.

This filter also supports the framesync options.

In the below example the input file main.mpg being processed is compared with the reference file ref.mpg.

```
ffmpeg -i main.mpg -i ref.mpg -lavfi identity -f null -

```

### 39.137 idet# TOC

Detect video interlacing type.

This filter tries to detect if the input frames are interlaced, progressive, top or bottom field first. It will also try to detect fields that are repeated between adjacent frames (a sign of telecine).

Single frame detection considers only immediately adjacent frames when classifying each frame. Multiple frame detection incorporates the classification history of previous frames.

The filter will log these metadata values:

single.current_frame

Detected type of current frame using single-frame detection. One of: “tff” (top field first), “bff” (bottom field first), “progressive”, or “undetermined”

single.tff

Cumulative number of frames detected as top field first using single-frame detection.

multiple.tff

Cumulative number of frames detected as top field first using multiple-frame detection.

single.bff

Cumulative number of frames detected as bottom field first using single-frame detection.

multiple.current_frame

Detected type of current frame using multiple-frame detection. One of: “tff” (top field first), “bff” (bottom field first), “progressive”, or “undetermined”

multiple.bff

Cumulative number of frames detected as bottom field first using multiple-frame detection.

single.progressive

Cumulative number of frames detected as progressive using single-frame detection.

multiple.progressive

Cumulative number of frames detected as progressive using multiple-frame detection.

single.undetermined

Cumulative number of frames that could not be classified using single-frame detection.

multiple.undetermined

Cumulative number of frames that could not be classified using multiple-frame detection.

repeated.current_frame

Which field in the current frame is repeated from the last. One of “neither”, “top”, or “bottom”.

repeated.neither

Cumulative number of frames with no repeated field.

repeated.top

Cumulative number of frames with the top field repeated from the previous frame’s top field.

repeated.bottom

Cumulative number of frames with the bottom field repeated from the previous frame’s bottom field.

The filter accepts the following options:

intl_thres

Set interlacing threshold.

prog_thres

Set progressive threshold.

rep_thres

Threshold for repeated field detection.

half_life

Number of frames after which a given frame’s contribution to the statistics is halved (i.e., it contributes only 0.5 to its classification). The default of 0 means that all frames seen are given full weight of 1.0 forever.

analyze_interlaced_flag

When this is not 0 then idet will use the specified number of frames to determine if the interlaced flag is accurate, it will not count undetermined frames. If the flag is found to be accurate it will be used without any further computations, if it is found to be inaccurate it will be cleared without any further computations. This allows inserting the idet filter as a low computational method to clean up the interlaced flag

#### 39.137.1 Examples# TOC

Inspect the field order of the first 360 frames in a video, in verbose detail:

```
ffmpeg -i INPUT -filter:v idet,metadata=mode=print -frames:v 360 -an -f null -

```

The idet filter will add analysis metadata to each frame, which will then be discarded. At the end, the filter will also print a final report with statistics.

### 39.138 il# TOC

Deinterleave or interleave fields.

This filter allows one to process interlaced images fields without deinterlacing them. Deinterleaving splits the input frame into 2 fields (so called half pictures). Odd lines are moved to the top half of the output image, even lines to the bottom half. You can process (filter) them independently and then re-interleave them.

The filter accepts the following options:

luma_mode, l

chroma_mode, c

alpha_mode, a

Available values for luma_mode, chroma_mode and alpha_mode are:

‘none’

Do nothing.

‘deinterleave, d’

Deinterleave fields, placing one above the other.

‘interleave, i’

Interleave fields. Reverse the effect of deinterleaving.

Default value is none.

luma_swap, ls

chroma_swap, cs

alpha_swap, as

Swap luma/chroma/alpha fields. Exchange even & odd lines. Default value is 0.

#### 39.138.1 Commands# TOC

This filter supports the all above options as commands.

### 39.139 inflate# TOC

Apply inflate effect to the video.

This filter replaces the pixel by the local(3x3) average by taking into account only values higher than the pixel.

It accepts the following options:

threshold0

threshold1

threshold2

threshold3

Limit the maximum change for each plane, default is 65535. If 0, plane will remain unchanged.

#### 39.139.1 Commands# TOC

This filter supports the all above options as commands.

### 39.140 interlace, interlace_vulkan# TOC

Simple interlacing filter from progressive contents. This interleaves upper (or lower) lines from odd frames with lower (or upper) lines from even frames, halving the frame rate and preserving image height.

```
   Original        Original             New Frame
   Frame 'j'      Frame 'j+1'             (tff)
  ==========      ===========       ==================
    Line 0  -------------------->    Frame 'j' Line 0
    Line 1          Line 1  ---->   Frame 'j+1' Line 1
    Line 2 --------------------->    Frame 'j' Line 2
    Line 3          Line 3  ---->   Frame 'j+1' Line 3
     ...             ...                   ...
New Frame + 1 will be generated by Frame 'j+2' and Frame 'j+3' and so on

```

It accepts the following optional parameters:

scan

This determines whether the interlaced frame is taken from the even (tff - default) or odd (bff) lines of the progressive frame.

lowpass

Vertical lowpass filter to avoid twitter interlacing and reduce moire patterns.

‘0, off’

Disable vertical lowpass filter

‘1, linear’

Enable linear filter (default)

‘2, complex’

Enable complex filter. This will slightly less reduce twitter and moire but better retain detail and subjective sharpness impression.

### 39.141 kerndeint# TOC

Deinterlace input video by applying Donald Graft’s adaptive kernel deinterling. Work on interlaced parts of a video to produce progressive frames.

The description of the accepted parameters follows.

thresh

Set the threshold which affects the filter’s tolerance when determining if a pixel line must be processed. It must be an integer in the range [0,255] and defaults to 10. A value of 0 will result in applying the process on every pixels.

map

Paint pixels exceeding the threshold value to white if set to 1. Default is 0.

order

Set the fields order. Swap fields if set to 1, leave fields alone if 0. Default is 0.

sharp

Enable additional sharpening if set to 1. Default is 0.

twoway

Enable twoway sharpening if set to 1. Default is 0.

#### 39.141.1 Examples# TOC

- Apply default values:

```
kerndeint=thresh=10:map=0:order=0:sharp=0:twoway=0

```

- Enable additional sharpening:

```
kerndeint=sharp=1

```

- Paint processed pixels in white:

```
kerndeint=map=1

```

### 39.142 kirsch# TOC

Apply kirsch operator to input video stream.

The filter accepts the following option:

planes

Set which planes will be processed, unprocessed planes will be copied. By default value 0xf, all planes will be processed.

scale

Set value which will be multiplied with filtered result.

delta

Set value which will be added to filtered result.

#### 39.142.1 Commands# TOC

This filter supports the all above options as commands.

### 39.143 lagfun# TOC

Slowly update darker pixels.

This filter makes short flashes of light appear longer. This filter accepts the following options:

decay

Set factor for decaying. Default is .95. Allowed range is from 0 to 1.

planes

Set which planes to filter. Default is all. Allowed range is from 0 to 15.

#### 39.143.1 Commands# TOC

This filter supports the all above options as commands.

### 39.144 latticepal# TOC

Convert packed RGB/BGR input to PAL8 with a per-frame palette whose colors are placed on a face-centered cubic (FCC) lattice spanning the RGB cube.

Each frame gets its own palette, built only from the lattice colors actually used by that frame. If a frame uses more than 256 lattice colors, they are reduced by iteratively dropping the color whose removal has the least impact (its pixel count times the squared distance to the nearest remaining color) and mapping its pixels to that nearest remaining color. The alpha channel, if present, is ignored unless the alpha option is set.

The filter accepts the following options:

density

Set the lattice density as the number of lattice steps spanning one color axis (0 to 255). Higher values give a finer lattice and thus more possible colors, making it more likely that the per-frame color reduction has to drop some of them. At a density of 7 with 256 palette entries no reduction ever happens since the whole lattice then holds exactly 256 points. Allowed range is 1 to 255. Default is 20.

max_colors

Set the maximum number of palette entries to use. Frames using more lattice colors than this are reduced accordingly. Allowed range is 2 to 256. Default is 256.

alpha

Quantize the alpha channel too, placing the palette colors on a 4 dimensional D4 lattice over RGBA instead of the FCC lattice over RGB. Inputs without an alpha channel are treated as opaque. With this option the density is limited to 64. Default is 0 (alpha is ignored and the palette is fully opaque).

refine

Redistribute the error introduced by dropping colors, which is otherwise uncompensated and can show as discolored patches. Frames that needed no reduction are not changed by this option.

‘none’

No refinement.

‘full’

Run a Floyd-Steinberg error diffusion pass over the whole frame against the final palette. Most accurate on average, but re-dithers everything, including regions whose colors survived.

‘residual’

Diffuse only the residual between each pixel’s first pass quantized color and its final palette color. Pixels of surviving colors that receive no residual are unchanged, keeping the character of the selected dither mode outside the reduced regions.

‘batched’

Interleave color removal and rediffusion: drop half of the excess colors, rediffuse the whole frame against the survivors, recount the colors from the actual assignments and repeat. Colors that the dithering can reproduce by mixing become free to drop while extreme colors keep their pixels and are protected; this gives the best quality at the cost of about log2 of the number of dropped colors rediffusion passes.

Default is none.

dither

Select the dithering mode. Available algorithms are:

‘none’

No dithering.

‘bayer’

Ordered 8x8 dithering using the classic swscale dither matrix with its per-channel decorrelation, offsets spanning one lattice period.

‘blue_noise’

Void-and-cluster blue noise dithering using three 64x64 masks generated at initialization, one per color channel.

‘floyd_steinberg’

Floyd-Steinberg error diffusion.

Default is floyd_steinberg.

### 39.145 lenscorrection# TOC

Correct radial lens distortion

This filter can be used to correct for radial distortion as can result from the use of wide angle lenses, and thereby re-rectify the image. To find the right parameters one can use tools available for example as part of opencv or simply trial-and-error. To use opencv use the calibration sample (under samples/cpp) from the opencv sources and extract the k1 and k2 coefficients from the resulting matrix.

Note that effectively the same filter is available in the open-source tools Krita and Digikam from the KDE project.

In contrast to the vignette filter, which can also be used to compensate lens errors, this filter corrects the distortion of the image, whereas vignette corrects the brightness distribution, so you may want to use both filters together in certain cases, though you will have to take care of ordering, i.e. whether vignetting should be applied before or after lens correction.

#### 39.145.1 Options# TOC

The filter accepts the following options:

cx

Relative x-coordinate of the focal point of the image, and thereby the center of the distortion. This value has a range [0,1] and is expressed as fractions of the image width. Default is 0.5.

cy

Relative y-coordinate of the focal point of the image, and thereby the center of the distortion. This value has a range [0,1] and is expressed as fractions of the image height. Default is 0.5.

k1

Coefficient of the quadratic correction term. This value has a range [-1,1]. 0 means no correction. Default is 0.

k2

Coefficient of the double quadratic correction term. This value has a range [-1,1]. 0 means no correction. Default is 0.

i

Set interpolation type. Can be nearest or bilinear. Default is nearest.

fc

Specify the color of the unmapped pixels. For the syntax of this option, check the "Color" section in the ffmpeg-utils manual. Default color is black@0.

The formula that generates the correction is:

r_src = r_tgt * (1 + k1 * (r_tgt / r_0)^2 + k2 * (r_tgt / r_0)^4)

where r_0 is halve of the image diagonal and r_src and r_tgt are the distances from the focal point in the source and target images, respectively.

#### 39.145.2 Commands# TOC

This filter supports the all above options as commands.

### 39.146 lensfun# TOC

Apply lens correction via the lensfun library (http://lensfun.sourceforge.net/).

The lensfun filter requires the camera make, camera model, and lens model to apply the lens correction. The filter will load the lensfun database and query it to find the corresponding camera and lens entries in the database. As long as these entries can be found with the given options, the filter can perform corrections on frames. Note that incomplete strings will result in the filter choosing the best match with the given options, and the filter will output the chosen camera and lens models (logged with level "info"). You must provide the make, camera model, and lens model as they are required.

To obtain a list of available makes and models, leave out one or both of make and model options. The filter will send the full list to the log with level INFO. The first column is the make and the second column is the model. To obtain a list of available lenses, set any values for make and model and leave out the lens_model option. The filter will send the full list of lenses in the log with level INFO. The ffmpeg tool will exit after the list is printed.

The filter accepts the following options:

make

The make of the camera (for example, "Canon"). This option is required.

model

The model of the camera (for example, "Canon EOS 100D"). This option is required.

lens_model

The model of the lens (for example, "Canon EF-S 18-55mm f/3.5-5.6 IS STM"). This option is required.

db_path

The full path to the lens database folder. If not set, the filter will attempt to load the database from the install path when the library was built. Default is unset.

mode

The type of correction to apply. The following values are valid options:

‘vignetting’

Enables fixing lens vignetting.

‘geometry’

Enables fixing lens geometry. This is the default.

‘subpixel’

Enables fixing chromatic aberrations.

‘vig_geo’

Enables fixing lens vignetting and lens geometry.

‘vig_subpixel’

Enables fixing lens vignetting and chromatic aberrations.

‘distortion’

Enables fixing both lens geometry and chromatic aberrations.

‘all’

Enables all possible corrections.

focal_length

The focal length of the image/video (zoom; expected constant for video). For example, a 18–55mm lens has focal length range of [18–55], so a value in that range should be chosen when using that lens. Default 18.

aperture

The aperture of the image/video (expected constant for video). Note that aperture is only used for vignetting correction. Default 3.5.

focus_distance

The focus distance of the image/video (expected constant for video). Note that focus distance is only used for vignetting and only slightly affects the vignetting correction process. If unknown, leave it at the default value (which is 1000).

scale

The scale factor which is applied after transformation. After correction the video is no longer necessarily rectangular. This parameter controls how much of the resulting image is visible. The value 0 means that a value will be chosen automatically such that there is little or no unmapped area in the output image. 1.0 means that no additional scaling is done. Lower values may result in more of the corrected image being visible, while higher values may avoid unmapped areas in the output.

target_geometry

The target geometry of the output image/video. The following values are valid options:

‘rectilinear (default)’

‘fisheye’

‘panoramic’

‘equirectangular’

‘fisheye_orthographic’

‘fisheye_stereographic’

‘fisheye_equisolid’

‘fisheye_thoby’

reverse

Apply the reverse of image correction (instead of correcting distortion, apply it).

interpolation

The type of interpolation used when correcting distortion. The following values are valid options:

‘nearest’

‘linear (default)’

‘lanczos’

#### 39.146.1 Examples# TOC

- Apply lens correction with make "Canon", camera model "Canon EOS 100D", and lens model "Canon EF-S 18-55mm f/3.5-5.6 IS STM" with focal length of "18" and aperture of "8.0".

```
ffmpeg -i input.mov -vf lensfun=make=Canon:model="Canon EOS 100D":lens_model="Canon EF-S 18-55mm f/3.5-5.6 IS STM":focal_length=18:aperture=8 -c:v h264 -b:v 8000k output.mov

```

- Apply the same as before, but only for the first 5 seconds of video.

```
ffmpeg -i input.mov -vf lensfun=make=Canon:model="Canon EOS 100D":lens_model="Canon EF-S 18-55mm f/3.5-5.6 IS STM":focal_length=18:aperture=8:enable='lte(t\,5)' -c:v h264 -b:v 8000k output.mov

```

### 39.147 lcevc# TOC

Low Complexity Enhancement Video Codec filter based on liblcevc_dec (https://github.com/v-novaltd/LCEVCdec).

### 39.148 libplacebo# TOC

Flexible GPU-accelerated processing filter based on libplacebo (https://code.videolan.org/videolan/libplacebo).

#### 39.148.1 Options# TOC

The options for this filter are divided into the following sections:

#### 39.148.1.1 Output mode# TOC

These options control the overall output mode. By default, libplacebo will try to preserve the source colorimetry and size as best as it can, but it will apply any embedded film grain, dolby vision metadata or anamorphic SAR present in source frames.

inputs

Set the number of inputs. This can be used, alongside the idx variable, to allow placing/blending multiple inputs inside the output frame. This effectively enables functionality similar to hstack, overlay, etc.

w

h

Set the output video dimension expression. Default values are iw and ih.

Allows for the same expressions as the scale filter.

crop_x

crop_y

Set the input crop x/y expressions, default values are (iw-cw)/2 and (ih-ch)/2.

crop_w

crop_h

Set the input crop width/height expressions, default values are iw and ih.

pos_x

pos_y

Set the output placement x/y expressions, default values are (ow-pw)/2 and (oh-ph)/2.

pos_w

pos_h

Set the output placement width/height expressions, default values are ow and oh.

rotate

Rotate the input frame clockwise by the specified angle.

‘0, 360’

‘90’

‘180’

‘270’

fps

Set the output frame rate. This can be rational, e.g. 60000/1001. If set to the special string none (the default), input timestamps will instead be passed through to the output unmodified. Otherwise, the input video frames will be interpolated as necessary to rescale the video to the specified target framerate, in a manner as determined by the frame_mixer option.

format

Set the output format override. If unset (the default), frames will be output in the same format as the respective input frames. Otherwise, format conversion will be performed.

force_original_aspect_ratio

force_divisible_by

Work the same as the identical scale filter options. Note that force_divisible_by also works with fit_sense=constraint.

reset_sar

If enabled, output frames will always have a pixel aspect ratio of 1:1. If disabled (the default), any aspect ratio mismatches, including those from e.g. anamorphic video sources, are forwarded to the output pixel aspect ratio.

normalize_sar

Like reset_sar, but instead of stretching the video content to fill the new output aspect ratio, the content is instead padded or cropped as necessary. Mutually exclusive with fit_mode. Disabled by default.

pad_crop_ratio

Specifies a ratio (between 0.0 and 1.0) between padding and cropping when the input aspect ratio does not match the output aspect ratio and normalize_sar is in effect. The default of 0.0 always pads the content with black borders, while a value of 1.0 always crops off parts of the content. Intermediate values are possible, leading to a mix of the two approaches.

fit_mode

Specify the content fit strategy according to a list of predefined modes. Determines how the input image is to be placed inside the destination crop rectangle (as defined by pos_x/y and pos_w/h). The names and their implementations are taken from the CSS ’object-fit’ property. Note that this option is mutually exclusive with normalize_sar. Defaults to fill. Valid values are:

‘fill’

Stretch the input to the output rectangle, ignoring aspect ratio mismatches. Note that unless reset_sar is also enabled, the output will still have the correct pixel aspect ratio tagged.

‘contain’

Scale the input to fit inside the output, preserving aspect ratio by padding. Equivalent to normalize_sar with pad_crop_ratio set to 0.0.

‘cover’

Scale the input to fill the output, preserving aspect ratio by cropping. Equivalent to normalize_sar with pad_crop_ratio set to 1.0.

‘none, place’

Don’t scale the input. The input will be placed inside the output rectangle at its natural size; which may result in additional padding or cropping.

‘scale_down’

Scale the input down as much as needed to fit inside the output. Equivalent to either contain or none, depending on whether the input is larger than the output or not.

fit_sense

When fit_mode is in use, this option controls how the fit strategy is applied against the specified output resolution. Mutually exclusive with force_original_aspect_ratio. Valid values are:

‘target’

The computed output resolution is taken as the exact size of the output frame. This is the default behavior.

‘constraint’

The computed output resolution is a size reference against which the fit mode is applied, enlarging or decreasing the true frame size as needed to fit the content.

fillcolor

Set the color used to fill the output area not covered by the output image, for example as a result of normalize_sar. For the general syntax of this option, check the "Color" section in the ffmpeg-utils manual. Defaults to black@0.

corner_rounding

Render frames with rounded corners. The value, given as a float ranging from 0.0 to 1.0, indicates the relative degree of rounding, from fully square to fully circular. In other words, it gives the radius divided by half the smaller side length. Defaults to 0.0.

lut

Specifies a custom LUT (in Adobe .cube format) to apply to the colors as part of color conversion. The exact interpretation depends on the value of lut_type.

lut_type

Controls the interpretation of color values fed to and from the LUT specified as lut. Valid values are:

‘auto’

Chooses the interpretation of the LUT automatically from tagged metadata, and otherwise falls back to ‘native’. (Default)

‘native’

Applied to raw image contents in its native RGB colorspace (non-linear light), before conversion to the output color space.

‘normalized’

Applied to the normalized RGB image contents, in linear light, before conversion to the output color space.

‘conversion’

Fully replaces the conversion from the image color space to the output color space. If such a LUT is present, it has the highest priority, and overrides any ICC profiles, as well as options related to tone mapping and output colorimetry (color_primaries, color_trc).

extra_opts

Pass extra libplacebo internal configuration options. These can be specified as a list of key=value pairs separated by ’:’. The following example shows how to configure a custom filter kernel ("EWA LanczosSharp") and use it to double the input image resolution:

```
-vf "libplacebo=w=iw*2:h=ih*2:extra_opts='upscaler=custom\:upscaler_preset=ewa_lanczos\:upscaler_blur=0.9812505644269356'"

```

shader_cache

File path of a cache directory that libplacebo will use to store and load cached shader objects. This cache is not cleaned up automatically. If the path does not end in a directory separator, the generated filenames will be effectively prefixed by the last path component. All directories must already exist.

```
-vf "libplacebo=shader_cache=/tmp/pl-shader-"

```

inherit_device

Take the Vulkan device from the hardware frames arriving on the input, instead of creating a private one from the filter’s own hardware device. This is useful when the input frames originate on another API (for example CUDA frames uploaded to Vulkan by hwupload) and the filter’s device is not itself a Vulkan device: libplacebo would otherwise spin up a separate Vulkan device that the input frames do not belong to, and the frames could not be mapped.

When enabled, the filter requires Vulkan hardware frames on the input and will fail negotiation otherwise. Disabled by default.

```
-init_hw_device vulkan=vk:0 -init_hw_device cuda@vk -filter_hw_device cuda0 ... -vf "hwupload=derive_device=vulkan,libplacebo=inherit_device=1"

```

colorspace

color_primaries

color_trc

range

chroma_location

Configure the colorspace that output frames will be delivered in. For any value other than the default auto, conversion will be performed. With auto, color_primaries and color_trc keep the values of the input frames, while colorspace, range and chroma_location use the values negotiated with the filtergraph, which are those of the input unless a following filter requires others.

See the setparams filter for a list of possible values.

alpha_mode

Choose the desired output alpha mode, when the output format has an alpha channel. See the setparams filter for a list of possible values.

apply_filmgrain

Apply film grain (e.g. AV1 or H.274) if present in source frames, and strip it from the output. Enabled by default.

apply_dolbyvision

Apply Dolby Vision RPU metadata if present in source frames, and strip it from the output. Enabled by default. Note that Dolby Vision will always output BT.2020+PQ, overriding the usual input frame metadata. These will also be picked as the values of auto for the respective frame output options.

In addition to the expression constants documented for the scale filter, the crop_w, crop_h, crop_x, crop_y, pos_w, pos_h, pos_x and pos_y options can also contain the following constants:

in_idx, idx

The (0-based) numeric index of the currently active input stream.

crop_w, cw

crop_h, ch

The computed values of crop_w and crop_h.

pos_w, pw

pos_h, ph

The computed values of pos_w and pos_h.

in_t, t

The input frame timestamp, in seconds. NAN if input timestamp is unknown.

out_t, ot

The input frame timestamp, in seconds. NAN if input timestamp is unknown.

n

The input frame number, starting with 0.

#### 39.148.1.2 Scaling# TOC

The options in this section control how libplacebo performs upscaling and (if necessary) downscaling. Note that libplacebo will always internally operate on 4:4:4 content, so any sub-sampled chroma formats such as yuv420p will necessarily be upsampled and downsampled as part of the rendering process. That means scaling might be in effect even if the source and destination resolution are the same.

upscaler

downscaler

Configure the filter kernel used for upscaling and downscaling. The respective defaults are spline36 and mitchell. For a full list of possible values, pass help to these options. The most important values are:

‘none’

Forces the use of built-in GPU texture sampling (typically bilinear). Extremely fast but poor quality, especially when downscaling.

‘bilinear’

Bilinear interpolation. Can generally be done for free on GPUs, except when doing so would lead to aliasing. Fast and low quality.

‘nearest’

Nearest-neighbour interpolation. Sharp but highly aliasing.

‘oversample’

Algorithm that looks visually similar to nearest-neighbour interpolation but tries to preserve pixel aspect ratio. Good for pixel art, since it results in minimal distortion of the artistic appearance.

‘lanczos’

Standard sinc-sinc interpolation kernel.

‘spline36’

Cubic spline approximation of lanczos. No difference in performance, but has very slightly less ringing.

‘ewa_lanczos’

Elliptically weighted average version of lanczos, based on a jinc-jinc kernel. This is also popularly referred to as just "Jinc scaling". Slow but very high quality.

‘gaussian’

Gaussian kernel. Has certain ideal mathematical properties, but subjectively very blurry.

‘mitchell’

Cubic BC spline with parameters recommended by Mitchell and Netravali. Very little ringing.

frame_mixer

Controls the kernel used for mixing frames temporally. The default value is none, which disables frame mixing. For a full list of possible values, pass help to this option. The most important values are:

‘none’

Disables frame mixing, giving a result equivalent to "nearest neighbour" semantics.

‘oversample’

Oversamples the input video to create a "Smooth Motion"-type effect: if an output frame would exactly fall on the transition between two video frames, it is blended according to the relative overlap. This is the recommended option whenever preserving the original subjective appearance is desired.

‘mitchell_clamp’

Larger filter kernel that smoothly interpolates multiple frames in a manner designed to eliminate ringing and other artefacts as much as possible. This is the recommended option wherever maximum visual smoothness is desired.

‘linear’

Linear blend/fade between frames. Especially useful for constructing e.g. slideshows.

antiringing

Enables anti-ringing (for non-EWA filters). The value (between 0.0 and 1.0) configures the strength of the anti-ringing algorithm. May increase aliasing if set too high. Disabled by default.

sigmoid

Enable sigmoidal compression during upscaling. Reduces ringing slightly. Enabled by default.

#### 39.148.1.3 Deinterlacing# TOC

Deinterlacing is automatically supported when frames are tagged as interlaced, however frames are not deinterlaced unless a deinterlacing algorithm is chosen.

deinterlace

The the deinterlacing algorithm to use.

‘weave’

No deinterlacing, weave fields together into a single frame. This is the default.

‘bob’

Naive bob deinterlacing, simply repeat each field line twice.

‘yadif’

Yet another deinterlacing filter. See the yadif filter for more details.

‘bwdif’

Bob weaver deinterlacing filter. See the bwdif filter for more details.

skip_spatial_check

Skip the spatial deinterlacing check when using yadif deinterlacing.

send_fields

Output a frame for each field, rather than for each frame. Note that this will always double the tagged output frame rate, even if the input does not contain any interlaced frames. Disabled by default.

#### 39.148.1.4 Debanding# TOC

Libplacebo comes with a built-in debanding filter that is good at counteracting many common sources of banding and blocking. Turning this on is highly recommended whenever quality is desired.

deband

Enable (fast) debanding algorithm. Disabled by default.

deband_iterations

Number of deband iterations of the debanding algorithm. Each iteration is performed with progressively increased radius (and diminished threshold). Recommended values are in the range 1 to 4. Defaults to 1.

deband_threshold

Debanding filter strength. Higher numbers lead to more aggressive debanding. Defaults to 4.0.

deband_radius

Debanding filter radius. A higher radius is better for slow gradients, while a lower radius is better for steep gradients. Defaults to 16.0.

deband_grain

Amount of extra output grain to add. Helps hide imperfections. Defaults to 6.0.

#### 39.148.1.5 Color adjustment# TOC

A collection of subjective color controls. Not very rigorous, so the exact effect will vary somewhat depending on the input primaries and colorspace.

brightness

Brightness boost, between -1.0 and 1.0. Defaults to 0.0.

contrast

Contrast gain, between 0.0 and 16.0. Defaults to 1.0.

saturation

Saturation gain, between 0.0 and 16.0. Defaults to 1.0.

hue

Hue shift in radians, between -3.14 and 3.14. Defaults to 0.0. This will rotate the UV subvector, defaulting to BT.709 coefficients for RGB inputs.

gamma

Gamma adjustment, between 0.0 and 16.0. Defaults to 1.0.

temperature

Color temperature adjustment. Lower values make the output warmer/redder, down to 1667, while higher values make the output cooler/bluer, up to 25000. Defaults to 6500 (neutral white).

cones

Cone model to use for color blindness simulation. Accepts any combination of l, m and s. Here are some examples:

‘m’

Deuteranomaly / deuteranopia (affecting 3%-4% of the population)

‘l’

Protanomaly / protanopia (affecting 1%-2% of the population)

‘l+m’

Monochromacy (very rare)

‘l+m+s’

Achromatopsy (complete loss of daytime vision, extremely rare)

cone-strength

Gain factor for the cones specified by cones, between 0.0 and 10.0. A value of 1.0 results in no change to color vision. A value of 0.0 (the default) simulates complete loss of those cones. Values above 1.0 result in exaggerating the differences between cones, which may help compensate for reduced color vision.

#### 39.148.1.6 Peak detection# TOC

To help deal with sources that only have static HDR10 metadata (or no tagging whatsoever), libplacebo uses its own internal frame analysis compute shader to analyze source frames and adapt the tone mapping function in realtime. If this is too slow, or if exactly reproducible frame-perfect results are needed, it’s recommended to turn this feature off.

peak_detect

Enable HDR peak detection. Ignores static MaxCLL/MaxFALL values in favor of dynamic detection from the input. Note that the detected values do not get written back to the output frames, they merely guide the internal tone mapping process. Enabled by default.

smoothing_period

Peak detection smoothing period, between 0.0 and 1000.0. Higher values result in peak detection becoming less responsive to changes in the input. Defaults to 20.0.

scene_threshold_low

scene_threshold_high

Lower and upper thresholds for scene change detection. Expressed in a logarithmic scale between 0.0 and 100.0. Default to 1.0 and 3.0, respectively. Setting either to a negative value disables this functionality.

percentile

Which percentile of the frame brightness histogram to use as the source peak for tone-mapping. Defaults to 99.995, a fairly conservative value. Setting this to 100.0 disables frame histogram measurement and instead uses the true peak brightness for tone-mapping.

#### 39.148.1.7 Tone mapping# TOC

The options in this section control how libplacebo performs tone-mapping and gamut-mapping when dealing with mismatches between wide-gamut or HDR content. In general, libplacebo relies on accurate source tagging and mastering display gamut information to produce the best results.

gamut_mode

How to handle out-of-gamut colors that can occur as a result of colorimetric gamut mapping.

‘clip’

Do nothing, simply clip out-of-range colors to the RGB volume. Low quality but extremely fast.

‘perceptual’

Perceptually soft-clip colors to the gamut volume. This is the default.

‘relative’

Relative colorimetric hard-clip. Similar to perceptual but without the soft knee.

‘saturation’

Saturation mapping, maps primaries directly to primaries in RGB space. Not recommended except for artificial computer graphics for which a bright, saturated display is desired.

‘absolute’

Absolute colorimetric hard-clip. Performs no adjustment of the white point.

‘desaturate’

Hard-desaturates out-of-gamut colors towards white, while preserving the luminance. Has a tendency to distort the visual appearance of bright objects.

‘darken’

Linearly reduces content brightness to preserves saturated details, followed by clipping the remaining out-of-gamut colors.

‘warn’

Highlight out-of-gamut pixels (by inverting/marking them).

‘linear’

Linearly reduces chromaticity of the entire image to make it fit within the target color volume. Be careful when using this on BT.2020 sources without proper mastering metadata, as doing so will lead to excessive desaturation.

tonemapping

Tone-mapping algorithm to use. Available values are:

‘auto’

Automatic selection based on internal heuristics. This is the default.

‘clip’

Performs no tone-mapping, just clips out-of-range colors. Retains perfect color accuracy for in-range colors but completely destroys out-of-range information. Does not perform any black point adaptation. Not configurable.

‘st2094-40’

EETF from SMPTE ST 2094-40 Annex B, which applies the Bezier curves from HDR10+ dynamic metadata based on Bezier curves to perform tone-mapping. The OOTF used is adjusted based on the ratio between the targeted and actual display peak luminances.

‘st2094-10’

EETF from SMPTE ST 2094-10 Annex B.2, which takes into account the input signal average luminance in addition to the maximum/minimum. The configurable contrast parameter influences the slope of the linear output segment, defaulting to 1.0 for no increase/decrease in contrast. Note that this does not currently include the subjective gain/offset/gamma controls defined in Annex B.3.

‘bt.2390’

EETF from the ITU-R Report BT.2390, a hermite spline roll-off with linear segment. The knee point offset is configurable. Note that this parameter defaults to 1.0, rather than the value of 0.5 from the ITU-R spec.

‘bt.2446a’

EETF from ITU-R Report BT.2446, method A. Designed for well-mastered HDR sources. Can be used for both forward and inverse tone mapping. Not configurable.

‘spline’

Simple spline consisting of two polynomials, joined by a single pivot point. The parameter gives the pivot point (in PQ space), defaulting to 0.30. Can be used for both forward and inverse tone mapping.

‘reinhard’

Simple non-linear, global tone mapping algorithm. The parameter specifies the local contrast coefficient at the display peak. Essentially, a parameter of 0.5 implies that the reference white will be about half as bright as when clipping. Defaults to 0.5, which results in the simplest formulation of this function.

‘mobius’

Generalization of the reinhard tone mapping algorithm to support an additional linear slope near black. The tone mapping parameter indicates the trade-off between the linear section and the non-linear section. Essentially, for a given parameter x, every color value below x will be mapped linearly, while higher values get non-linearly tone-mapped. Values near 1.0 make this curve behave like clip, while values near 0.0 make this curve behave like reinhard. The default value is 0.3, which provides a good balance between colorimetric accuracy and preserving out-of-gamut details.

‘hable’

Piece-wise, filmic tone-mapping algorithm developed by John Hable for use in Uncharted 2, inspired by a similar tone-mapping algorithm used by Kodak. Popularized by its use in video games with HDR rendering. Preserves both dark and bright details very well, but comes with the drawback of changing the average brightness quite significantly. This is sort of similar to reinhard with parameter 0.24.

‘gamma’

Fits a gamma (power) function to transfer between the source and target color spaces, effectively resulting in a perceptual hard-knee joining two roughly linear sections. This preserves details at all scales fairly accurately, but can result in an image with a muted or dull appearance. The parameter is used as the cutoff point, defaulting to 0.5.

‘linear’

Linearly stretches the input range to the output range, in PQ space. This will preserve all details accurately, but results in a significantly different average brightness. Can be used for inverse tone-mapping in addition to regular tone-mapping. The parameter can be used as an additional linear gain coefficient (defaulting to 1.0).

tonemapping_param

For tunable tone mapping functions, this parameter can be used to fine-tune the curve behavior. Refer to the documentation of tonemapping. The default value of 0.0 is replaced by the curve’s preferred default setting.

inverse_tonemapping

If enabled, this filter will also attempt stretching SDR signals to fill HDR output color volumes. Disabled by default.

tonemapping_lut_size

Size of the tone-mapping LUT, between 2 and 1024. Defaults to 256. Note that this figure is squared when combined with peak_detect.

contrast_recovery

Contrast recovery strength. If set to a value above 0.0, the source image will be divided into high-frequency and low-frequency components, and a portion of the high-frequency image is added back onto the tone-mapped output. May cause excessive ringing artifacts for some HDR sources, but can improve the subjective sharpness and detail left over in the image after tone-mapping. Defaults to 0.30.

contrast_smoothness

Contrast recovery lowpass kernel size. Defaults to 3.5. Increasing or decreasing this will affect the visual appearance substantially. Has no effect when contrast_recovery is disabled.

#### 39.148.1.8 Dithering# TOC

By default, libplacebo will dither whenever necessary, which includes rendering to any integer format below 16-bit precision. It’s recommended to always leave this on, since not doing so may result in visible banding in the output, even if the debanding filter is enabled. If maximum performance is needed, use ordered_fixed instead of disabling dithering.

dithering

Dithering method to use. Accepts the following values:

‘none’

Disables dithering completely. May result in visible banding.

‘blue’

Dither with pseudo-blue noise. This is the default.

‘ordered’

Tunable ordered dither pattern.

‘ordered_fixed’

Faster ordered dither with a fixed size of 6. Texture-less.

‘white’

Dither with white noise. Texture-less.

dither_lut_size

Dither LUT size, as log base2 between 1 and 8. Defaults to 6, corresponding to a LUT size of 64x64.

dither_temporal

Enables temporal dithering. Disabled by default.

#### 39.148.1.9 Custom shaders# TOC

libplacebo supports a number of custom shaders based on the mpv .hook GLSL syntax. A collection of such shaders can be found here: https://github.com/mpv-player/mpv/wiki/User-Scripts#user-shaders

A full description of the mpv shader format is beyond the scope of this section, but a summary can be found here: https://mpv.io/manual/master/#options-glsl-shader

custom_shader_path

Specifies a path to a custom shader file to load at runtime.

custom_shader_bin

Specifies a complete custom shader as a raw string.

#### 39.148.1.10 Debugging / performance# TOC

All of the options in this section default off. They may be of assistance when attempting to squeeze the maximum performance at the cost of quality.

skip_aa

Disable anti-aliasing when downscaling.

disable_linear

Disable linear light scaling.

disable_builtin

Disable built-in GPU sampling (forces LUT).

disable_fbos

Forcibly disable FBOs, resulting in loss of almost all functionality, but offering the maximum possible speed.

#### 39.148.2 Commands# TOC

This filter supports almost all of the above options as commands. The options negotiated with the filtergraph, format, colorspace, range, chroma_location and alpha_mode, are fixed once the filtergraph is configured and can not be changed with commands.

#### 39.148.3 Examples# TOC

- Tone-map input to standard gamut BT.709 output:

```
libplacebo=colorspace=bt709:color_primaries=bt709:color_trc=bt709:range=tv

```

- Rescale input to fit into standard 1080p, with high quality scaling:

```
libplacebo=w=1920:h=1080:force_original_aspect_ratio=decrease:normalize_sar=true:upscaler=ewa_lanczos:downscaler=ewa_lanczos

```

- Interpolate low FPS / VFR input to smoothed constant 60 fps output:

```
libplacebo=fps=60:frame_mixer=mitchell_clamp

```

- Convert input to standard sRGB JPEG:

```
libplacebo=format=yuv420p:colorspace=bt470bg:color_primaries=bt709:color_trc=iec61966-2-1:range=pc

```

- Use higher quality debanding settings:

```
libplacebo=deband=true:deband_iterations=3:deband_radius=8:deband_threshold=6

```

- Run this filter on the CPU, on systems with Mesa installed (and with the most expensive options disabled):

```
ffmpeg ... -init_hw_device vulkan:llvmpipe ... -vf libplacebo=upscaler=none:downscaler=none:peak_detect=false

```

- Suppress CPU-based AV1/H.274 film grain application in the decoder, in favor of doing it with this filter. Note that this is only a gain if the frames are either already on the GPU, or if you’re using libplacebo for other purposes, since otherwise the VRAM roundtrip will more than offset any expected speedup.

```
ffmpeg -export_side_data +film_grain ... -vf libplacebo=apply_filmgrain=true

```

- Interop with VAAPI hwdec to avoid round-tripping through RAM:

```
ffmpeg -init_hw_device vulkan -hwaccel vaapi -hwaccel_output_format vaapi ... -vf libplacebo

```

### 39.149 libvmaf# TOC

Calculate the VMAF (Video Multi-Method Assessment Fusion) score for a reference/distorted pair of input videos.

The first input is the distorted video, and the second input is the reference video.

The obtained VMAF score is printed through the logging system.

It requires Netflix’s vmaf library (libvmaf) as a pre-requisite. After installing the library it can be enabled using: ./configure --enable-libvmaf.

The filter has following options:

model

A ‘|‘ delimited list of vmaf models. Each model can be configured with a number of parameters. Default value: "version=vmaf_v0.6.1"

feature

A ‘|‘ delimited list of features. Each feature can be configured with a number of parameters.

log_path

Set the file path to be used to store log files.

log_fmt

Set the format of the log file (xml, json, csv, or sub).

pool

Set the pool method to be used for computing vmaf. Options are min, harmonic_mean or mean (default).

n_threads

Set number of threads to be used when initializing libvmaf. Default value: 0, no threads.

n_subsample

Set frame subsampling interval to be used.

This filter also supports the framesync options.

#### 39.149.1 Examples# TOC

- In the examples below, a distorted video distorted.mpg is compared with a reference file reference.mpg.

- Basic usage:

```
ffmpeg -i distorted.mpg -i reference.mpg -lavfi libvmaf=log_path=output.xml -f null -

```

- Example with multiple models:

```
ffmpeg -i distorted.mpg -i reference.mpg -lavfi libvmaf='model=version=vmaf_v0.6.1\\:name=vmaf|version=vmaf_v0.6.1neg\\:name=vmaf_neg' -f null -

```

- Example with multiple additional features:

```
ffmpeg -i distorted.mpg -i reference.mpg -lavfi libvmaf='feature=name=psnr|name=ciede' -f null -

```

- Example with options and different containers:

```
ffmpeg -i distorted.mpg -i reference.mkv -lavfi "[0:v]settb=AVTB,setpts=PTS-STARTPTS[main];[1:v]settb=AVTB,setpts=PTS-STARTPTS[ref];[main][ref]libvmaf=log_fmt=json:log_path=output.json" -f null -

```

### 39.150 libvmaf_cuda# TOC

This is the CUDA variant of the libvmaf filter. It only accepts CUDA frames.

It requires Netflix’s vmaf library (libvmaf) as a pre-requisite. After installing the library it can be enabled using: ./configure --enable-nonfree --enable-ffnvcodec --enable-libvmaf.

#### 39.150.1 Examples# TOC

- Basic usage showing CUVID hardware decoding and CUDA scaling with scale_cuda:

```
ffmpeg \
    -hwaccel cuda -hwaccel_output_format cuda -codec:v av1_cuvid -i dis.obu \
    -hwaccel cuda -hwaccel_output_format cuda -codec:v av1_cuvid -i ref.obu \
    -filter_complex "
        [0:v]scale_cuda=format=yuv420p[dis]; \
        [1:v]scale_cuda=format=yuv420p[ref]; \
        [dis][ref]libvmaf_cuda=log_fmt=json:log_path=output.json
    " \
    -f null -

```

### 39.151 limitdiff# TOC

Apply limited difference filter using second and optionally third video stream.

The filter accepts the following options:

threshold

Set the threshold to use when allowing certain differences between video streams. Any absolute difference value lower or exact than this threshold will pick pixel components from first video stream.

elasticity

Set the elasticity of soft thresholding when processing video streams. This value multiplied with first one sets second threshold. Any absolute difference value greater or exact than second threshold will pick pixel components from second video stream. For values between those two threshold linear interpolation between first and second video stream will be used.

reference

Enable the reference (third) video stream processing. By default is disabled. If set, this video stream will be used for calculating absolute difference with first video stream.

planes

Specify which planes will be processed. Defaults to all available.

#### 39.151.1 Commands# TOC

This filter supports the all above options as commands except option ‘reference’.

### 39.152 limiter# TOC

Limits the pixel components values to the specified range [min, max].

The filter accepts the following options:

min

Lower bound. Defaults to the lowest representable value for the input. Set to auto to use the minimum signal level for the input colorspace (only affects TV-range YUV signals).

max

Upper bound. Defaults to the highest representable value for the input. Set to auto to use the maximum signal level for the input colorspace (only affects TV-range YUV signals).

planes

Specify which planes will be processed. Defaults to all available.

#### 39.152.1 Commands# TOC

This filter supports the all above options as commands.

### 39.153 loop# TOC

Loop video frames.

The filter accepts the following options:

loop

Set the number of loops. Setting this value to -1 will result in infinite loops. Default is 0.

size

Set maximal size in number of frames. Default is 0.

start

Set first frame of loop. Default is 0.

time

Set the time of loop start in seconds. Only used if option named start is set to -1.

#### 39.153.1 Examples# TOC

- Loop single first frame infinitely:

```
loop=loop=-1:size=1:start=0

```

- Loop single first frame 10 times:

```
loop=loop=10:size=1:start=0

```

- Loop 10 first frames 5 times:

```
loop=loop=5:size=10:start=0

```

### 39.154 lut1d# TOC

Apply a 1D LUT to an input video.

The filter accepts the following options:

file

Set the 1D LUT file name.

Currently supported formats:

‘cube’

Iridas

‘csp’

cineSpace

interp

Select interpolation mode.

Available values are:

‘nearest’

Use values from the nearest defined point.

‘linear’

Interpolate values using the linear interpolation.

‘cosine’

Interpolate values using the cosine interpolation.

‘cubic’

Interpolate values using the cubic interpolation.

‘spline’

Interpolate values using the spline interpolation.

#### 39.154.1 Commands# TOC

This filter supports the all above options as commands.

### 39.155 lut3d# TOC

Apply a 3D LUT to an input video.

The filter accepts the following options:

file

Set the 3D LUT file name.

Currently supported formats:

‘3dl’

AfterEffects

‘cube’

Iridas

‘dat’

DaVinci

‘m3d’

Pandora

‘csp’

cineSpace

interp

Select interpolation mode.

Available values are:

‘nearest’

Use values from the nearest defined point.

‘trilinear’

Interpolate values using the 8 points defining a cube.

‘tetrahedral’

Interpolate values using a tetrahedron.

‘pyramid’

Interpolate values using a pyramid.

‘prism’

Interpolate values using a prism.

#### 39.155.1 Commands# TOC

This filter supports the interp option as commands.

### 39.156 lumakey# TOC

Turn certain luma values into transparency.

The filter accepts the following options:

threshold

Set the luma which will be used as base for transparency. Default value is 0.

tolerance

Set the range of luma values to be keyed out. Default value is 0.01.

softness

Set the range of softness. Default value is 0. Use this to control gradual transition from zero to full transparency.

#### 39.156.1 Commands# TOC

This filter supports same commands as options. The command accepts the same syntax of the corresponding option.

If the specified expression is not valid, it is kept at its current value.

### 39.157 lut, lutrgb, lutyuv# TOC

Compute a look-up table for binding each pixel component input value to an output value, and apply it to the input video.

lutyuv applies a lookup table to a YUV input video, lutrgb to an RGB input video.

These filters accept the following parameters:

c0

set first pixel component expression

c1

set second pixel component expression

c2

set third pixel component expression

c3

set fourth pixel component expression, corresponds to the alpha component

r

set red component expression

g

set green component expression

b

set blue component expression

a

alpha component expression

y

set Y/luma component expression

u

set U/Cb component expression

v

set V/Cr component expression

Each of them specifies the expression to use for computing the lookup table for the corresponding pixel component values.

The exact component associated to each of the c* options depends on the format in input.

The lut filter requires either YUV or RGB pixel formats in input, lutrgb requires RGB pixel formats in input, and lutyuv requires YUV.

The expressions can contain the following constants and functions:

w

h

The input width and height.

val

The input value for the pixel component.

clipval

The input value, clipped to the minval-maxval range.

maxval

The maximum value for the pixel component.

minval

The minimum value for the pixel component.

negval

The negated value for the pixel component value, clipped to the minval-maxval range; it corresponds to the expression "maxval-clipval+minval".

clip(val)

The computed value in val, clipped to the minval-maxval range.

gammaval(gamma)

The computed gamma correction value of the pixel component value, clipped to the minval-maxval range. It corresponds to the expression "pow((clipval-minval)/(maxval-minval)\,gamma)*(maxval-minval)+minval"

All expressions default to "clipval".

#### 39.157.1 Commands# TOC

This filter supports same commands as options.

#### 39.157.2 Examples# TOC

- Negate input video:

```
lutrgb="r=maxval+minval-val:g=maxval+minval-val:b=maxval+minval-val"
lutyuv="y=maxval+minval-val:u=maxval+minval-val:v=maxval+minval-val"

```

The above is the same as:

```
lutrgb="r=negval:g=negval:b=negval"
lutyuv="y=negval:u=negval:v=negval"

```

- Negate luma:

```
lutyuv=y=negval

```

- Remove chroma components, turning the video into a graytone image:

```
lutyuv="u=128:v=128"

```

- Apply a luma burning effect:

```
lutyuv="y=2*val"

```

- Remove green and blue components:

```
lutrgb="g=0:b=0"

```

- Set a constant alpha channel value on input:

```
format=rgba,lutrgb=a="maxval-minval/2"

```

- Correct luma gamma by a factor of 0.5:

```
lutyuv=y=gammaval(0.5)

```

- Discard least significant bits of luma:

```
lutyuv=y='bitand(val, 128+64+32)'

```

- Technicolor like effect:

```
lutyuv=u='(val-maxval/2)*2+maxval/2':v='(val-maxval/2)*2+maxval/2'

```

### 39.158 lut2, tlut2# TOC

The lut2 filter takes two input streams and outputs one stream.

The tlut2 (time lut2) filter takes two consecutive frames from one single stream.

This filter accepts the following parameters:

c0

set first pixel component expression

c1

set second pixel component expression

c2

set third pixel component expression

c3

set fourth pixel component expression, corresponds to the alpha component

d

set output bit depth, only available for lut2 filter. By default is 0, which means bit depth is automatically picked from first input format.

The lut2 filter also supports the framesync options.

Each of them specifies the expression to use for computing the lookup table for the corresponding pixel component values.

The exact component associated to each of the c* options depends on the format in inputs.

The expressions can contain the following constants:

w

h

The input width and height.

x

The first input value for the pixel component.

y

The second input value for the pixel component.

bdx

The first input video bit depth.

bdy

The second input video bit depth.

All expressions default to "x".

#### 39.158.1 Commands# TOC

This filter supports the all above options as commands except option d.

#### 39.158.2 Examples# TOC

- Highlight differences between two RGB video streams:

```
lut2='ifnot(x-y,0,pow(2,bdx)-1):ifnot(x-y,0,pow(2,bdx)-1):ifnot(x-y,0,pow(2,bdx)-1)'

```

- Highlight differences between two YUV video streams:

```
lut2='ifnot(x-y,0,pow(2,bdx)-1):ifnot(x-y,pow(2,bdx-1),pow(2,bdx)-1):ifnot(x-y,pow(2,bdx-1),pow(2,bdx)-1)'

```

- Show max difference between two video streams:

```
lut2='if(lt(x,y),0,if(gt(x,y),pow(2,bdx)-1,pow(2,bdx-1))):if(lt(x,y),0,if(gt(x,y),pow(2,bdx)-1,pow(2,bdx-1))):if(lt(x,y),0,if(gt(x,y),pow(2,bdx)-1,pow(2,bdx-1)))'

```

### 39.159 maskedclamp# TOC

Clamp the first input stream with the second input and third input stream.

Returns the value of first stream to be between second input stream - undershoot and third input stream + overshoot.

This filter accepts the following options:

undershoot

Default value is 0.

overshoot

Default value is 0.

planes

Set which planes will be processed as bitmap, unprocessed planes will be copied from first stream. By default value 0xf, all planes will be processed.

#### 39.159.1 Commands# TOC

This filter supports the all above options as commands.

### 39.160 maskedmax# TOC

Merge the second and third input stream into output stream using absolute differences between second input stream and first input stream and absolute difference between third input stream and first input stream. The picked value will be from second input stream if second absolute difference is greater than first one or from third input stream otherwise.

This filter accepts the following options:

planes

Set which planes will be processed as bitmap, unprocessed planes will be copied from first stream. By default value 0xf, all planes will be processed.

#### 39.160.1 Commands# TOC

This filter supports the all above options as commands.

### 39.161 maskedmerge# TOC

Merge the first input stream with the second input stream using per pixel weights in the third input stream.

A value of 0 in the third stream pixel component means that pixel component from first stream is returned unchanged, while maximum value (eg. 255 for 8-bit videos) means that pixel component from second stream is returned unchanged. Intermediate values define the amount of merging between both input stream’s pixel components.

This filter accepts the following options:

planes

Set which planes will be processed as bitmap, unprocessed planes will be copied from first stream. By default value 0xf, all planes will be processed.

#### 39.161.1 Commands# TOC

This filter supports the all above options as commands.

### 39.162 maskedmin# TOC

Merge the second and third input stream into output stream using absolute differences between second input stream and first input stream and absolute difference between third input stream and first input stream. The picked value will be from second input stream if second absolute difference is less than first one or from third input stream otherwise.

This filter accepts the following options:

planes

Set which planes will be processed as bitmap, unprocessed planes will be copied from first stream. By default value 0xf, all planes will be processed.

#### 39.162.1 Commands# TOC

This filter supports the all above options as commands.

### 39.163 maskedthreshold# TOC

Pick pixels comparing absolute difference of two video streams with fixed threshold.

If absolute difference between pixel component of first and second video stream is equal or lower than user supplied threshold than pixel component from first video stream is picked, otherwise pixel component from second video stream is picked.

This filter accepts the following options:

threshold

Set threshold used when picking pixels from absolute difference from two input video streams.

planes

Set which planes will be processed as bitmap, unprocessed planes will be copied from second stream. By default value 0xf, all planes will be processed.

mode

Set mode of filter operation. Can be abs or diff. Default is abs.

#### 39.163.1 Commands# TOC

This filter supports the all above options as commands.

### 39.164 maskfun# TOC

Create mask from input video.

For example it is useful to create motion masks after tblend filter.

This filter accepts the following options:

low

Set low threshold. Any pixel component lower or exact than this value will be set to 0.

high

Set high threshold. Any pixel component higher than this value will be set to max value allowed for current pixel format.

planes

Set planes to filter, by default all available planes are filtered.

fill

Fill all frame pixels with this value.

sum

Set max average pixel value for frame. If sum of all pixel components is higher that this average, output frame will be completely filled with value set by fill option. Typically useful for scene changes when used in combination with tblend filter.

#### 39.164.1 Commands# TOC

This filter supports the all above options as commands.

### 39.165 mcdeint# TOC

Apply motion-compensation deinterlacing.

It needs one field per frame as input and must thus be used together with yadif=1/3 or equivalent.

This filter accepts the following options:

mode

Set the deinterlacing mode.

It accepts one of the following values:

‘fast’

‘medium’

‘slow’

use iterative motion estimation

‘extra_slow’

like ‘slow’, but use multiple reference frames.

Default value is ‘fast’.

parity

Set the picture field parity assumed for the input video. It must be one of the following values:

‘0, tff’

assume top field first

‘1, bff’

assume bottom field first

Default value is ‘bff’.

qp

Set per-block quantization parameter (QP) used by the internal encoder.

Higher values should result in a smoother motion vector field but less optimal individual vectors. Default value is 1.

### 39.166 median# TOC

Pick median pixel from certain rectangle defined by radius.

This filter accepts the following options:

radius

Set horizontal radius size. Default value is 1. Allowed range is integer from 1 to 127.

planes

Set which planes to process. Default is 15, which is all available planes.

radiusV

Set vertical radius size. Default value is 0. Allowed range is integer from 0 to 127. If it is 0, value will be picked from horizontal radius option.

percentile

Set median percentile. Default value is 0.5. Default value of 0.5 will pick always median values, while 0 will pick minimum values, and 1 maximum values.

#### 39.166.1 Commands# TOC

This filter supports same commands as options. The command accepts the same syntax of the corresponding option.

If the specified expression is not valid, it is kept at its current value.

### 39.167 mergeplanes# TOC

Merge color channel components from several video streams.

The filter accepts up to 4 input streams, and merge selected input planes to the output video.

This filter accepts the following options:

mapping

Set input to output plane mapping. Default is 0.

The mappings is specified as a bitmap. It should be specified as a hexadecimal number in the form 0xAa[Bb[Cc[Dd]]]. ’Aa’ describes the mapping for the first plane of the output stream. ’A’ sets the number of the input stream to use (from 0 to 3), and ’a’ the plane number of the corresponding input to use (from 0 to 3). The rest of the mappings is similar, ’Bb’ describes the mapping for the output stream second plane, ’Cc’ describes the mapping for the output stream third plane and ’Dd’ describes the mapping for the output stream fourth plane.

format

Set output pixel format. Default is yuva444p.

map0s

map1s

map2s

map3s

Set input to output stream mapping for output Nth plane. Default is 0.

map0p

map1p

map2p

map3p

Set input to output plane mapping for output Nth plane. Default is 0.

#### 39.167.1 Examples# TOC

- Merge three gray video streams of same width and height into single video stream:

```
[a0][a1][a2]mergeplanes=0x001020:yuv444p

```

- Merge 1st yuv444p stream and 2nd gray video stream into yuva444p video stream:

```
[a0][a1]mergeplanes=0x00010210:yuva444p

```

- Swap Y and A plane in yuva444p stream:

```
format=yuva444p,mergeplanes=0x03010200:yuva444p

```

- Swap U and V plane in yuv420p stream:

```
format=yuv420p,mergeplanes=0x000201:yuv420p

```

- Cast a rgb24 clip to yuv444p:

```
format=rgb24,mergeplanes=0x000102:yuv444p

```

### 39.168 mestimate# TOC

Estimate and export motion vectors using block matching algorithms. Motion vectors are stored in frame side data to be used by other filters.

This filter accepts the following options:

method

Specify the motion estimation method. Accepts one of the following values:

‘esa’

Exhaustive search algorithm.

‘tss’

Three step search algorithm.

‘tdls’

Two dimensional logarithmic search algorithm.

‘ntss’

New three step search algorithm.

‘fss’

Four step search algorithm.

‘ds’

Diamond search algorithm.

‘hexbs’

Hexagon-based search algorithm.

‘epzs’

Enhanced predictive zonal search algorithm.

‘umh’

Uneven multi-hexagon search algorithm.

Default value is ‘esa’.

mb_size

Macroblock size. Default 16.

search_param

Search parameter. Default 7.

### 39.169 mestimate_d3d12# TOC

Estimate and export motion vectors using D3D12 hardware-accelerated motion estimation. This filter uses GPU hardware motion estimation capabilities available in DirectX 12 Video APIs to achieve significant performance improvements over the software-based mestimate filter.

Motion vectors are stored in frame side data to be used by other filters.

This filter requires the input to be in d3d12 hardware pixel format. The filter uses quarter-pixel precision for motion vector estimation.

This filter accepts the following options:

mb_size

Macroblock size. Only 8 and 16 are supported. Default 16.

#### 39.169.1 Examples# TOC

Estimate motion vectors using D3D12 hardware acceleration with 16x16 blocks, and visualize them:

```
ffmpeg -hwaccel d3d12va -hwaccel_output_format d3d12 -i input.mp4 \
        -vf mestimate_d3d12=mb_size=16,hwdownload,format=nv12,codecview=mv=pf \
        -c:v libx264 -preset fast -b:v 5M output.mp4

```

### 39.170 midequalizer# TOC

Apply Midway Image Equalization effect using two video streams.

Midway Image Equalization adjusts a pair of images to have the same histogram, while maintaining their dynamics as much as possible. It’s useful for e.g. matching exposures from a pair of stereo cameras.

This filter has two inputs and one output, which must be of same pixel format, but may be of different sizes. The output of filter is first input adjusted with midway histogram of both inputs.

This filter accepts the following option:

planes

Set which planes to process. Default is 15, which is all available planes.

### 39.171 minterpolate# TOC

Convert the video to specified frame rate using motion interpolation.

This filter accepts the following options:

fps

Specify the output frame rate. This can be rational e.g. 60000/1001. Frames are dropped if fps is lower than source fps. Default 60.

mi_mode

Motion interpolation mode. Following values are accepted:

‘dup’

Duplicate previous or next frame for interpolating new ones.

‘blend’

Blend source frames. Interpolated frame is mean of previous and next frames.

‘mci’

Motion compensated interpolation. Following options are effective when this mode is selected:

‘mc_mode’

Motion compensation mode. Following values are accepted:

‘obmc’

Overlapped block motion compensation.

‘aobmc’

Adaptive overlapped block motion compensation. Window weighting coefficients are controlled adaptively according to the reliabilities of the neighboring motion vectors to reduce oversmoothing.

Default mode is ‘obmc’.

‘me_mode’

Motion estimation mode. Following values are accepted:

‘bidir’

Bidirectional motion estimation. Motion vectors are estimated for each source frame in both forward and backward directions.

‘bilat’

Bilateral motion estimation. Motion vectors are estimated directly for interpolated frame.

Default mode is ‘bilat’.

‘me’

The algorithm to be used for motion estimation. Following values are accepted:

‘esa’

Exhaustive search algorithm.

‘tss’

Three step search algorithm.

‘tdls’

Two dimensional logarithmic search algorithm.

‘ntss’

New three step search algorithm.

‘fss’

Four step search algorithm.

‘ds’

Diamond search algorithm.

‘hexbs’

Hexagon-based search algorithm.

‘epzs’

Enhanced predictive zonal search algorithm.

‘umh’

Uneven multi-hexagon search algorithm.

Default algorithm is ‘epzs’.

‘mb_size’

Macroblock size. Default 16.

‘search_param’

Motion estimation search parameter. Default 32.

‘vsbmc’

Enable variable-size block motion compensation. Motion estimation is applied with smaller block sizes at object boundaries in order to make them less blurry. Default is 0 (disabled).

scd

Scene change detection method. Scene change leads motion vectors to be in random direction. Scene change detection replace interpolated frames by duplicate ones. May not be needed for other modes. Following values are accepted:

‘none’

Disable scene change detection.

‘fdiff’

Frame difference. Corresponding pixel values are compared and if it satisfies scd_threshold scene change is detected.

Default method is ‘fdiff’.

scd_threshold

Scene change detection threshold. Default is 10..

### 39.172 mix# TOC

Mix several video input streams into one video stream.

A description of the accepted options follows.

inputs

The number of inputs. If unspecified, it defaults to 2.

weights

Specify weight of each input video stream as sequence. Each weight is separated by space. If number of weights is smaller than number of frames last specified weight will be used for all remaining unset weights.

scale

Specify scale, if it is set it will be multiplied with sum of each weight multiplied with pixel values to give final destination pixel value. By default scale is auto scaled to sum of weights.

planes

Set which planes to filter. Default is all. Allowed range is from 0 to 15.

duration

Specify how end of stream is determined.

‘longest’

The duration of the longest input. (default)

‘shortest’

The duration of the shortest input.

‘first’

The duration of the first input.

#### 39.172.1 Commands# TOC

This filter supports the following commands:

weights

scale

planes

Syntax is same as option with same name.

### 39.173 monochrome# TOC

Convert video to gray using custom color filter.

A description of the accepted options follows.

cb

Set the chroma blue spot. Allowed range is from -1 to 1. Default value is 0.

cr

Set the chroma red spot. Allowed range is from -1 to 1. Default value is 0.

size

Set the color filter size. Allowed range is from .1 to 10. Default value is 1.

high

Set the highlights strength. Allowed range is from 0 to 1. Default value is 0.

#### 39.173.1 Commands# TOC

This filter supports the all above options as commands.

### 39.174 morpho# TOC

This filter allows to apply main morphological grayscale transforms, erode and dilate with arbitrary structures set in second input stream.

Unlike naive implementation and much slower performance in erosion and dilation filters, when speed is critical morpho filter should be used instead.

A description of accepted options follows,

mode

Set morphological transform to apply, can be:

‘erode’

‘dilate’

‘open’

‘close’

‘gradient’

‘tophat’

‘blackhat’

Default is erode.

planes

Set planes to filter, by default all planes except alpha are filtered.

structure

Set which structure video frames will be processed from second input stream, can be first or all. Default is all.

The morpho filter also supports the framesync options.

#### 39.174.1 Commands# TOC

This filter supports same commands as options.

### 39.175 mpdecimate# TOC

Drop frames that do not differ greatly from the previous frame in order to reduce frame rate.

The main use of this filter is for very-low-bitrate encoding (e.g. streaming over dialup modem), but it could in theory be used for fixing movies that were inverse-telecined incorrectly.

A description of the accepted options follows.

mode

Set the mode. If the value is 0, the filter drops similar frames. If the value is 1, the filter keeps only frames that are one representative of sufficiently long duplicate runs.

Default value is 0.

max

For mode 0: Set the maximum number of consecutive frames which can be dropped (if positive), or the minimum interval between dropped frames (if negative). If the value is 0, the frame is dropped disregarding the number of previous sequentially dropped frames.

Default value is 0.

min

For mode 1: Set the minimum number of frame duplicates to mark the frame as non-unique and keep the first occurrence of it.

Default value is 1.

keep

For mode 0: Set the maximum number of consecutive similar frames to ignore before to start dropping them. If the value is 0, the frame is dropped disregarding the number of previous sequentially similar frames.

Default value is 0.

hi

lo

frac

Set the dropping threshold values.

Values for hi and lo are for 8x8 pixel blocks and represent actual pixel value differences, so a threshold of 64 corresponds to 1 unit of difference for each pixel, or the same spread out differently over the block.

A frame is a candidate for dropping if no 8x8 blocks differ by more than a threshold of hi, and if no more than frac blocks (1 meaning the whole image) differ by more than a threshold of lo.

Default value for hi is 64*12, default value for lo is 64*5, and default value for frac is 0.33.

### 39.176 msad# TOC

Obtain the MSAD (Mean Sum of Absolute Differences) between two input videos.

This filter takes two input videos.

Both input videos must have the same resolution and pixel format for this filter to work correctly. Also it assumes that both inputs have the same number of frames, which are compared one by one.

The obtained per component, average, min and max MSAD is printed through the logging system.

The filter stores the calculated MSAD of each frame in frame metadata.

This filter also supports the framesync options.

In the below example the input file main.mpg being processed is compared with the reference file ref.mpg.

```
ffmpeg -i main.mpg -i ref.mpg -lavfi msad -f null -

```

### 39.177 multiply# TOC

Multiply first video stream pixels values with second video stream pixels values.

The filter accepts the following options:

scale

Set the scale applied to second video stream. By default is 1. Allowed range is from 0 to 9.

offset

Set the offset applied to second video stream. By default is 0.5. Allowed range is from -1 to 1.

planes

Specify planes from input video stream that will be processed. By default all planes are processed.

#### 39.177.1 Commands# TOC

This filter supports same commands as options.

### 39.178 negate# TOC

Negate (invert) the input video.

It accepts the following option:

components

Set components to negate.

Available values for components are:

‘y’

‘u’

‘v’

‘a’

‘r’

‘g’

‘b’

negate_alpha

With value 1, it negates the alpha component, if present. Default value is 0.

#### 39.178.1 Commands# TOC

This filter supports same commands as options.

### 39.179 nlmeans# TOC

Denoise frames using Non-Local Means algorithm.

Each pixel is adjusted by looking for other pixels with similar contexts. This context similarity is defined by comparing their surrounding patches of size pxp. Patches are searched in an area of rxr around the pixel.

Note that the research area defines centers for patches, which means some patches will be made of pixels outside that research area.

The filter accepts the following options.

s

Set denoising strength. Default is 1.0. Must be in range [1.0, 30.0].

p

Set patch size. Default is 7. Must be odd number in range [0, 99].

pc

Same as p but for chroma planes.

The default value is 0 and means automatic.

r

Set research size. Default is 15. Must be odd number in range [0, 99].

rc

Same as r but for chroma planes.

The default value is 0 and means automatic.

### 39.180 nnedi# TOC

Deinterlace video using neural network edge directed interpolation.

This filter accepts the following options:

weights

Mandatory option, without binary file filter can not work. Currently file can be found here: https://github.com/dubhater/vapoursynth-nnedi3/blob/master/src/nnedi3_weights.bin

deint

Set which frames to deinterlace, by default it is all. Can be all or interlaced.

field

Set mode of operation.

Can be one of the following:

‘af’

Use frame flags, both fields.

‘a’

Use frame flags, single field.

‘t’

Use top field only.

‘b’

Use bottom field only.

‘tf’

Use both fields, top first.

‘bf’

Use both fields, bottom first.

planes

Set which planes to process, by default filter process all frames.

nsize

Set size of local neighborhood around each pixel, used by the predictor neural network.

Can be one of the following:

‘s8x6’

‘s16x6’

‘s32x6’

‘s48x6’

‘s8x4’

‘s16x4’

‘s32x4’

nns

Set the number of neurons in predictor neural network. Can be one of the following:

‘n16’

‘n32’

‘n64’

‘n128’

‘n256’

qual

Controls the number of different neural network predictions that are blended together to compute the final output value. Can be fast, default or slow.

etype

Set which set of weights to use in the predictor. Can be one of the following:

‘a, abs’

weights trained to minimize absolute error

‘s, mse’

weights trained to minimize squared error

pscrn

Controls whether or not the prescreener neural network is used to decide which pixels should be processed by the predictor neural network and which can be handled by simple cubic interpolation. The prescreener is trained to know whether cubic interpolation will be sufficient for a pixel or whether it should be predicted by the predictor nn. The computational complexity of the prescreener nn is much less than that of the predictor nn. Since most pixels can be handled by cubic interpolation, using the prescreener generally results in much faster processing. The prescreener is pretty accurate, so the difference between using it and not using it is almost always unnoticeable.

Can be one of the following:

‘none’

‘original’

‘new’

‘new2’

‘new3’

Default is new.

#### 39.180.1 Commands# TOC

This filter supports same commands as options, excluding weights option.

### 39.181 noformat# TOC

Force libavfilter not to use any of the specified pixel formats for the input to the next filter.

It accepts the following parameters:

pix_fmts

A ’|’-separated list of pixel format names, such as pix_fmts=yuv420p|monow|rgb24".

#### 39.181.1 Examples# TOC

- Force libavfilter to use a format different from yuv420p for the input to the vflip filter:

```
noformat=pix_fmts=yuv420p,vflip

```

- Convert the input video to any of the formats not contained in the list:

```
noformat=yuv420p|yuv444p|yuv410p

```

### 39.182 noise# TOC

Add noise on video input frame.

The filter accepts the following options:

all_seed

c0_seed

c1_seed

c2_seed

c3_seed

Set noise seed for specific pixel component or all pixel components in case of all_seed. Default value is 123457.

all_strength, alls

c0_strength, c0s

c1_strength, c1s

c2_strength, c2s

c3_strength, c3s

Set noise strength for specific pixel component or all pixel components in case all_strength. Default value is 0. Allowed range is [0, 100].

all_flags, allf

c0_flags, c0f

c1_flags, c1f

c2_flags, c2f

c3_flags, c3f

Set pixel component flags or set flags for all components if all_flags. Available values for component flags are:

‘a’

averaged temporal noise (smoother)

‘p’

mix random noise with a (semi)regular pattern

‘t’

temporal noise (noise pattern changes between frames)

‘u’

uniform noise (gaussian otherwise)

#### 39.182.1 Examples# TOC

Add temporal and uniform noise to input video:

```
noise=alls=20:allf=t+u

```

### 39.183 normalize# TOC

Normalize RGB video (aka histogram stretching, contrast stretching). See: https://en.wikipedia.org/wiki/Normalization_(image_processing)

For each channel of each frame, the filter computes the input range and maps it linearly to the user-specified output range. The output range defaults to the full dynamic range from pure black to pure white.

Temporal smoothing can be used on the input range to reduce flickering (rapid changes in brightness) caused when small dark or bright objects enter or leave the scene. This is similar to the auto-exposure (automatic gain control) on a video camera, and, like a video camera, it may cause a period of over- or under-exposure of the video.

The R,G,B channels can be normalized independently, which may cause some color shifting, or linked together as a single channel, which prevents color shifting. Linked normalization preserves hue. Independent normalization does not, so it can be used to remove some color casts. Independent and linked normalization can be combined in any ratio.

The normalize filter accepts the following options:

blackpt

whitept

Colors which define the output range. The minimum input value is mapped to the blackpt. The maximum input value is mapped to the whitept. The defaults are black and white respectively. Specifying white for blackpt and black for whitept will give color-inverted, normalized video. Shades of grey can be used to reduce the dynamic range (contrast). Specifying saturated colors here can create some interesting effects.

smoothing

The number of previous frames to use for temporal smoothing. The input range of each channel is smoothed using a rolling average over the current frame and the smoothing previous frames. The default is 0 (no temporal smoothing).

independence

Controls the ratio of independent (color shifting) channel normalization to linked (color preserving) normalization. 0.0 is fully linked, 1.0 is fully independent. Defaults to 1.0 (fully independent).

strength

Overall strength of the filter. 1.0 is full strength. 0.0 is a rather expensive no-op. Defaults to 1.0 (full strength).

#### 39.183.1 Commands# TOC

This filter supports same commands as options, excluding smoothing option. The command accepts the same syntax of the corresponding option.

If the specified expression is not valid, it is kept at its current value.

#### 39.183.2 Examples# TOC

Stretch video contrast to use the full dynamic range, with no temporal smoothing; may flicker depending on the source content:

```
normalize=blackpt=black:whitept=white:smoothing=0

```

As above, but with 50 frames of temporal smoothing; flicker should be reduced, depending on the source content:

```
normalize=blackpt=black:whitept=white:smoothing=50

```

As above, but with hue-preserving linked channel normalization:

```
normalize=blackpt=black:whitept=white:smoothing=50:independence=0

```

As above, but with half strength:

```
normalize=blackpt=black:whitept=white:smoothing=50:independence=0:strength=0.5

```

Map the darkest input color to red, the brightest input color to cyan:

```
normalize=blackpt=red:whitept=cyan

```

### 39.184 null# TOC

Pass the video source unchanged to the output.

### 39.185 ocio# TOC

OpenColorIO library filter

This filter allows you to do color management using the OpenColorIO library. See https://opencolorio.org/ for more details. To Enable compilation of this filter, you need to configure FFmpeg with --enable-libopencolorio.

It accepts the following options:

config

By default the filter will use the OCIO config defined by the OCIO environment variable, but this parameter allows you to explicitly specify its location. If you are getting started, you can use config=ocio://studio-config-v1.0.0_aces-v1.3_ocio-v2.1 which specifies one of the built in defaults.

input

Set the input colorspace.

output

Set the output colorspace.

display

Set the display colorspace, used in combination with view.

view

Set the view colorspace, used in combination with display.

inverse

When used in combination with display and view, this inverts the transform, so going from a display/view to the "input colorspace".

filetransform

Allows you to specify an external file-transform to use instead of the OCIO config file. This is useful for applying a single transform without needing a full OCIO config file.

format

Allow you to specify the output pix_fmt of the OCIO filter. This *has* to be a RGB colorspace, so you are limited to rgb24, rgba, rgb48, rgba64, gbrp10, gbrap10, gbrp12, gbrap12, gbrpf32 and gbrapf32; for most encoding we would recommend rgb48.

Half-float (gbrpf16, gbrapf16) is accepted as input but is not a valid output format, because swscale has no half-float write support and its legacy half-float read path clamps values to [0,1]. When this option is not set, the output format defaults to the input format, except that half-float input is promoted to the matching float format. Where negotiation cannot yet tell whether the input will be half-float, the output falls back to float, so a float output may be selected even when the input turns out to be an integer format.

context_params

Allow you to specify additional context parameters for the OCIO filter. This is a list of key=value pairs, separated by colons.

#### 39.185.1 Examples# TOC

Map from ACEScg to ACEScct, this assumes the OCIO file is defined with the OCIO environment variable.

```
input=ACEScg:output=ACEScct:format=rgb48

```

Map from ACEScg to a sRGB display using the "ACES 1.0 - SDR Video" view transform, this assumes the OCIO file is defined with the OCIO environment variable. Note you will need to wrap the argument in quotes to ensure that the spaces are interpreted correctly.

```
input=ACEScg:display=sRGB - Display:view=ACES 1.0 - SDR Video:format=rgb48

```

As above but using the OCIO file studio-config-v1.0.0_aces-v1.3_ocio-v2.1_ns.ocio rather than the OCIO environment variable.

```
config=studio-config-v1.0.0_aces-v1.3_ocio-v2.1_ns.ocio:input=ACEScg:display=sRGB - Display:view=ACES 1.0 - SDR Video:format=rgb48

```

If you are converting to YCrCb you still will want to set the color matrix for the conversion. This is a good example of combining the two.

```
ffmpeg -y -i SOURCEFRAMES.%05d.exr -c:v libx265 -vf "ocio=input=ACEScg:output=ACEScct:format=rgb48,scale=in_color_matrix=bt709:out_color_matrix=bt709,format=yuv444p10"  OUTPUTFILE.mov

```

### 39.186 ocr# TOC

Optical Character Recognition

This filter uses Tesseract for optical character recognition. To enable compilation of this filter, you need to configure FFmpeg with --enable-libtesseract.

It accepts the following options:

datapath

Set datapath to tesseract data. Default is to use whatever was set at installation.

language

Set language, default is "eng".

whitelist

Set character whitelist.

blacklist

Set character blacklist.

The filter exports recognized text as the frame metadata lavfi.ocr.text. The filter exports confidence of recognized words as the frame metadata lavfi.ocr.confidence.

### 39.187 ocv# TOC

Apply a video transform using libopencv.

To enable this filter, install the libopencv library and headers and configure FFmpeg with --enable-libopencv.

It accepts the following parameters:

filter_name

The name of the libopencv filter to apply.

filter_params

The parameters to pass to the libopencv filter. If not specified, the default values are assumed.

Refer to the official libopencv documentation for more precise information: http://docs.opencv.org/master/modules/imgproc/doc/filtering.html

Several libopencv filters are supported; see the following subsections.

#### 39.187.1 dilate# TOC

Dilate an image by using a specific structuring element. It corresponds to the libopencv function cvDilate.

It accepts the parameters: struct_el|nb_iterations.

struct_el represents a structuring element, and has the syntax: colsxrows+anchor_xxanchor_y/shape

cols and rows represent the number of columns and rows of the structuring element, anchor_x and anchor_y the anchor point, and shape the shape for the structuring element. shape must be "rect", "cross", "ellipse", or "custom".

If the value for shape is "custom", it must be followed by a string of the form "=filename". The file with name filename is assumed to represent a binary image, with each printable character corresponding to a bright pixel. When a custom shape is used, cols and rows are ignored, the number or columns and rows of the read file are assumed instead.

The default value for struct_el is "3x3+0x0/rect".

nb_iterations specifies the number of times the transform is applied to the image, and defaults to 1.

Some examples:

```
# Use the default values
ocv=dilate

# Dilate using a structuring element with a 5x5 cross, iterating two times
ocv=filter_name=dilate:filter_params=5x5+2x2/cross|2

# Read the shape from the file diamond.shape, iterating two times.
# The file diamond.shape may contain a pattern of characters like this
#   *
#  ***
# *****
#  ***
#   *
# The specified columns and rows are ignored
# but the anchor point coordinates are not
ocv=dilate:0x0+2x2/custom=diamond.shape|2

```

#### 39.187.2 erode# TOC

Erode an image by using a specific structuring element. It corresponds to the libopencv function cvErode.

It accepts the parameters: struct_el:nb_iterations, with the same syntax and semantics as the dilate filter.

#### 39.187.3 smooth# TOC

Smooth the input video.

The filter takes the following parameters: type|param1|param2|param3|param4.

type is the type of smooth filter to apply, and must be one of the following values: "blur", "blur_no_scale", "median", "gaussian", or "bilateral". The default value is "gaussian".

The meaning of param1, param2, param3, and param4 depends on the smooth type. param1 and param2 accept integer positive values or 0. param3 and param4 accept floating point values.

The default value for param1 is 3. The default value for the other parameters is 0.

These parameters correspond to the parameters assigned to the libopencv function cvSmooth.

### 39.188 oscilloscope# TOC

2D Video Oscilloscope.

Useful to measure spatial impulse, step responses, chroma delays, etc.

It accepts the following parameters:

x

Set scope center x position.

y

Set scope center y position.

s

Set scope size, relative to frame diagonal.

t

Set scope tilt/rotation.

o

Set trace opacity.

tx

Set trace center x position.

ty

Set trace center y position.

tw

Set trace width, relative to width of frame.

th

Set trace height, relative to height of frame.

c

Set which components to trace. By default it traces first three components.

g

Draw trace grid. By default is enabled.

st

Draw some statistics. By default is enabled.

sc

Draw scope. By default is enabled.

#### 39.188.1 Commands# TOC

This filter supports same commands as options. The command accepts the same syntax of the corresponding option.

If the specified expression is not valid, it is kept at its current value.

#### 39.188.2 Examples# TOC

- Inspect full first row of video frame.

```
oscilloscope=x=0.5:y=0:s=1

```

- Inspect full last row of video frame.

```
oscilloscope=x=0.5:y=1:s=1

```

- Inspect full 5th line of video frame of height 1080.

```
oscilloscope=x=0.5:y=5/1080:s=1

```

- Inspect full last column of video frame.

```
oscilloscope=x=1:y=0.5:s=1:t=1

```

### 39.189 overlay# TOC

Overlay one video on top of another.

It takes two inputs and has one output. The first input is the "main" video on which the second input is overlaid.

It accepts the following parameters:

A description of the accepted options follows.

x

y

Set the expression for the x and y coordinates of the overlaid video on the main video. Default value is "0" for both expressions. In case the expression is invalid, it is set to a huge value (meaning that the overlay will not be displayed within the output visible area).

eof_action

See framesync.

eval

Set when the expressions for x, and y are evaluated.

It accepts the following values:

‘init’

only evaluate expressions once during the filter initialization or when a command is processed

‘frame’

evaluate expressions for each incoming frame

Default value is ‘frame’.

shortest

See framesync.

format

Set the format for the output video.

It accepts the following values:

‘yuv420’

force YUV 4:2:0 8-bit planar output

‘yuv420p10’

force YUV 4:2:0 10-bit planar output

‘yuv422’

force YUV 4:2:2 8-bit planar output

‘yuv422p10’

force YUV 4:2:2 10-bit planar output

‘yuv444’

force YUV 4:4:4 8-bit planar output

‘yuv444p10’

force YUV 4:4:4 10-bit planar output

‘rgb’

force RGB 8-bit packed output

‘gbrp’

force RGB 8-bit planar output

‘auto’

automatically pick format

Default value is ‘yuv420’.

repeatlast

See framesync.

alpha

Set format of alpha of the overlaid video, it can be straight or premultiplied, or auto to choose the alpha mode automatically. Default is auto.

The x, and y expressions can contain the following parameters.

main_w, W

main_h, H

The main input width and height.

overlay_w, w

overlay_h, h

The overlay input width and height.

x

y

The computed values for x and y. They are evaluated for each new frame.

hsub

vsub

horizontal and vertical chroma subsample values of the output format. For example for the pixel format "yuv422p" hsub is 2 and vsub is 1.

n

the number of input frame, starting from 0

pos

the position in the file of the input frame, NAN if unknown; deprecated, do not use

t

The timestamp, expressed in seconds. It’s NAN if the input timestamp is unknown.

This filter also supports the framesync options.

Note that the n, t variables are available only when evaluation is done per frame, and will evaluate to NAN when eval is set to ‘init’.

Be aware that frames are taken from each input video in timestamp order, hence, if their initial timestamps differ, it is a good idea to pass the two inputs through a setpts=PTS-STARTPTS filter to have them begin in the same zero timestamp, as the example for the movie filter does.

You can chain together more overlays but you should test the efficiency of such approach.

#### 39.189.1 Commands# TOC

This filter supports the following commands:

x

y

Modify the x and y of the overlay input. The command accepts the same syntax of the corresponding option.

If the specified expression is not valid, it is kept at its current value.

#### 39.189.2 Examples# TOC

- Draw the overlay at 10 pixels from the bottom right corner of the main video:

```
overlay=main_w-overlay_w-10:main_h-overlay_h-10

```

Using named options the example above becomes:

```
overlay=x=main_w-overlay_w-10:y=main_h-overlay_h-10

```

- Insert a transparent PNG logo in the bottom left corner of the input, using the ffmpeg tool with the -filter_complex option:

```
ffmpeg -i input -i logo -filter_complex 'overlay=10:main_h-overlay_h-10' output

```

- Insert 2 different transparent PNG logos (second logo on bottom right corner) using the ffmpeg tool:

```
ffmpeg -i input -i logo1 -i logo2 -filter_complex 'overlay=x=10:y=H-h-10,overlay=x=W-w-10:y=H-h-10' output

```

- Add a transparent color layer on top of the main video; WxH must specify the size of the main input to the overlay filter:

```
color=color=red@.3:size=WxH [over]; [in][over] overlay [out]

```

- Play an original video and a filtered version (here with the deshake filter) side by side using the ffplay tool:

```
ffplay input.avi -vf 'split[a][b]; [a]pad=iw*2:ih[src]; [b]deshake[filt]; [src][filt]overlay=w'

```

The above command is the same as:

```
ffplay input.avi -vf 'split[b], pad=iw*2[src], [b]deshake, [src]overlay=w'

```

- Make a sliding overlay appearing from the left to the right top part of the screen starting since time 2:

```
overlay=x='if(gte(t,2), -w+(t-2)*20, NAN)':y=0

```

- Compose output by putting two input videos side to side:

```
ffmpeg -i left.avi -i right.avi -filter_complex "
nullsrc=size=200x100 [background];
[0:v] setpts=PTS-STARTPTS, scale=100x100 [left];
[1:v] setpts=PTS-STARTPTS, scale=100x100 [right];
[background][left]       overlay=shortest=1       [background+left];
[background+left][right] overlay=shortest=1:x=100 [left+right]
"

```

- Mask 10-20 seconds of a video by applying the delogo filter to a section

```
ffmpeg -i test.avi -codec:v:0 wmv2 -ar 11025 -b:v 9000k
-vf '[in]split[split_main][split_delogo];[split_delogo]trim=start=360:end=371,delogo=0:0:640:480[delogoed];[split_main][delogoed]overlay=eof_action=pass[out]'
masked.avi

```

- Chain several overlays in cascade:

```
nullsrc=s=200x200 [bg];
testsrc=s=100x100, split=4 [in0][in1][in2][in3];
[in0] lutrgb=r=0, [bg]   overlay=0:0     [mid0];
[in1] lutrgb=g=0, [mid0] overlay=100:0   [mid1];
[in2] lutrgb=b=0, [mid1] overlay=0:100   [mid2];
[in3] null,       [mid2] overlay=100:100 [out0]

```

### 39.190 owdenoise# TOC

Apply Overcomplete Wavelet denoiser.

The filter accepts the following options:

depth

Set depth.

Larger depth values will denoise lower frequency components more, but slow down filtering.

Must be an int in the range 8-16, default is 8.

luma_strength, ls

Set luma strength.

Must be a double value in the range 0-1000, default is 1.0.

chroma_strength, cs

Set chroma strength.

Must be a double value in the range 0-1000, default is 1.0.

### 39.191 pad# TOC

Add paddings to the input image, and place the original input at the provided x, y coordinates.

It accepts the following parameters:

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

The default value of color is "black".

eval

Specify when to evaluate width, height, x and y expression.

It accepts the following values:

‘init’

Only evaluate expressions once during the filter initialization or when a command is processed.

‘frame’

Evaluate expressions for each incoming frame.

Default value is ‘init’.

aspect

Pad to aspect instead to a resolution.

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

hsub

vsub

The horizontal and vertical chroma subsample values. For example for the pixel format "yuv422p" hsub is 2 and vsub is 1.

#### 39.191.1 Examples# TOC

- Add paddings with the color "violet" to the input video. The output video size is 640x480, and the top-left corner of the input video is placed at column 0, row 40

```
pad=640:480:0:40:violet

```

The example above is equivalent to the following command:

```
pad=width=640:height=480:x=0:y=40:color=violet

```

- Pad the input to get an output with dimensions increased by 3/2, and put the input video at the center of the padded area:

```
pad="3/2*iw:3/2*ih:(ow-iw)/2:(oh-ih)/2"

```

- Pad the input to get a squared output with size equal to the maximum value between the input width and height, and put the input video at the center of the padded area:

```
pad="max(iw\,ih):ow:(ow-iw)/2:(oh-ih)/2"

```

- Pad the input to get a final w/h ratio of 16:9:

```
pad="ih*16/9:ih:(ow-iw)/2:(oh-ih)/2"

```

- In case of anamorphic video, in order to set the output display aspect correctly, it is necessary to use sar in the expression, according to the relation:

```
(ih * X / ih) * sar = output_dar
X = output_dar / sar

```

Thus the previous example needs to be modified to:

```
pad="ih*16/9/sar:ih:(ow-iw)/2:(oh-ih)/2"

```

- Double the output size and put the input video in the bottom-right corner of the output padded area:

```
pad="2*iw:2*ih:ow-iw:oh-ih"

```

### 39.192 palettegen# TOC

Generate one palette for a whole video stream.

It accepts the following options:

max_colors

Set the maximum number of colors to quantize in the palette. Note: the palette will still contain 256 colors; the unused palette entries will be black.

reserve_transparent

Create a palette of 255 colors maximum and reserve the last one for transparency. Reserving the transparency color is useful for GIF optimization. If not set, the maximum of colors in the palette will be 256. You probably want to disable this option for a standalone image. Set by default.

transparency_color

Set the color that will be used as background for transparency.

stats_mode

Set statistics mode.

It accepts the following values:

‘full’

Compute full frame histograms.

‘diff’

Compute histograms only for the part that differs from previous frame. This might be relevant to give more importance to the moving part of your input if the background is static.

‘single’

Compute new histogram for each frame.

Default value is full.

The filter also exports the frame metadata lavfi.color_quant_ratio (nb_color_in / nb_color_out) which you can use to evaluate the degree of color quantization of the palette. This information is also visible at info logging level.

#### 39.192.1 Examples# TOC

- Generate a representative palette of a given video using ffmpeg:

```
ffmpeg -i input.mkv -vf palettegen palette.png

```

### 39.193 paletteuse# TOC

Use a palette to downsample an input video stream.

The filter takes two inputs: one video stream and a palette. The palette must be a 256 pixels image.

It accepts the following options:

dither

Select dithering mode. Available algorithms are:

‘bayer’

Ordered 8x8 bayer dithering (deterministic)

‘heckbert’

Dithering as defined by Paul Heckbert in 1982 (simple error diffusion). Note: this dithering is sometimes considered "wrong" and is included as a reference.

‘floyd_steinberg’

Floyd and Steingberg dithering (error diffusion)

‘sierra2’

Frankie Sierra dithering v2 (error diffusion)

‘sierra2_4a’

Frankie Sierra dithering v2 "Lite" (error diffusion)

‘sierra3’

Frankie Sierra dithering v3 (error diffusion)

‘burkes’

Burkes dithering (error diffusion)

‘atkinson’

Atkinson dithering by Bill Atkinson at Apple Computer (error diffusion)

‘none’

Disable dithering.

Default is sierra2_4a.

bayer_scale

When bayer dithering is selected, this option defines the scale of the pattern (how much the crosshatch pattern is visible). A low value means more visible pattern for less banding, and higher value means less visible pattern at the cost of more banding.

The option must be an integer value in the range [0,5]. Default is 2.

diff_mode

If set, define the zone to process

‘rectangle’

Only the changing rectangle will be reprocessed. This is similar to GIF cropping/offsetting compression mechanism. This option can be useful for speed if only a part of the image is changing, and has use cases such as limiting the scope of the error diffusal dither to the rectangle that bounds the moving scene (it leads to more deterministic output if the scene doesn’t change much, and as a result less moving noise and better GIF compression).

Default is none.

new

Take new palette for each output frame.

alpha_threshold

Sets the alpha threshold for transparency. Alpha values above this threshold will be treated as completely opaque, and values below this threshold will be treated as completely transparent.

The option must be an integer value in the range [0,255]. Default is 128.

#### 39.193.1 Examples# TOC

- Use a palette (generated for example with palettegen) to encode a GIF using ffmpeg:

```
ffmpeg -i input.mkv -i palette.png -lavfi paletteuse output.gif

```

### 39.194 perspective# TOC

Correct perspective of video not recorded perpendicular to the screen.

A description of the accepted parameters follows.

x0

y0

x1

y1

x2

y2

x3

y3

Set coordinates expression for top left, top right, bottom left and bottom right corners. Default values are 0:0:W:0:0:H:W:H with which perspective will remain unchanged. If the sense option is set to source, then the specified points will be sent to the corners of the destination. If the sense option is set to destination, then the corners of the source will be sent to the specified coordinates.

The expressions can use the following variables:

W

H

the width and height of video frame.

in

Input frame count.

on

Output frame count.

interpolation

Set interpolation for perspective correction.

It accepts the following values:

‘linear’

‘cubic’

Default value is ‘linear’.

sense

Set interpretation of coordinate options.

It accepts the following values:

‘0, source’

Send point in the source specified by the given coordinates to the corners of the destination.

‘1, destination’

Send the corners of the source to the point in the destination specified by the given coordinates.

Default value is ‘source’.

eval

Set when the expressions for coordinates x0,y0,...x3,y3 are evaluated.

It accepts the following values:

‘init’

only evaluate expressions once during the filter initialization or when a command is processed

‘frame’

evaluate expressions for each incoming frame

Default value is ‘init’.

### 39.195 phase# TOC

Delay interlaced video by one field time so that the field order changes.

The intended use is to fix PAL movies that have been captured with the opposite field order to the film-to-video transfer.

A description of the accepted parameters follows.

mode

Set phase mode.

It accepts the following values:

‘t’

Capture field order top-first, transfer bottom-first. Filter will delay the bottom field.

‘b’

Capture field order bottom-first, transfer top-first. Filter will delay the top field.

‘p’

Capture and transfer with the same field order. This mode only exists for the documentation of the other options to refer to, but if you actually select it, the filter will faithfully do nothing.

‘a’

Capture field order determined automatically by field flags, transfer opposite. Filter selects among ‘t’ and ‘b’ modes on a frame by frame basis using field flags. If no field information is available, then this works just like ‘u’.

‘u’

Capture unknown or varying, transfer opposite. Filter selects among ‘t’ and ‘b’ on a frame by frame basis by analyzing the images and selecting the alternative that produces best match between the fields.

‘T’

Capture top-first, transfer unknown or varying. Filter selects among ‘t’ and ‘p’ using image analysis.

‘B’

Capture bottom-first, transfer unknown or varying. Filter selects among ‘b’ and ‘p’ using image analysis.

‘A’

Capture determined by field flags, transfer unknown or varying. Filter selects among ‘t’, ‘b’ and ‘p’ using field flags and image analysis. If no field information is available, then this works just like ‘U’. This is the default mode.

‘U’

Both capture and transfer unknown or varying. Filter selects among ‘t’, ‘b’ and ‘p’ using image analysis only.

#### 39.195.1 Commands# TOC

This filter supports the all above options as commands.

### 39.196 photosensitivity# TOC

Reduce various flashes in video, so to help users with epilepsy.

It accepts the following options:

frames, f

Set how many frames to use when filtering. Default is 30.

threshold, t

Set detection threshold factor. Default is 1. Lower is stricter.

skip

Set how many pixels to skip when sampling frames. Default is 1. Allowed range is from 1 to 1024.

bypass

Leave frames unchanged. Default is disabled.

blend

Set the blending factor for frames that exceed the detection threshold. A value of 0 duplicates the last accepted frame, and a value of 1 blends up to the detection threshold. Default is 1. Allowed range is from 0 to 1.

### 39.197 pixdesctest# TOC

Pixel format descriptor test filter, mainly useful for internal testing. The output video should be equal to the input video.

For example:

```
format=monow, pixdesctest

```

can be used to test the monowhite pixel format descriptor definition.

### 39.198 pixelize# TOC

Apply pixelization to video stream.

The filter accepts the following options:

width, w

height, h

Set block dimensions that will be used for pixelization. Default value is 16.

mode, m

Set the mode of pixelization used.

Possible values are:

‘avg’

‘min’

‘max’

Default value is avg.

planes, p

Set what planes to filter. Default is to filter all planes.

#### 39.198.1 Commands# TOC

This filter supports all options as commands.

### 39.199 pixscope# TOC

Display sample values of color channels. Mainly useful for checking color and levels. Minimum supported resolution is 640x480.

The filters accept the following options:

x

Set scope X position, relative offset on X axis.

y

Set scope Y position, relative offset on Y axis.

w

Set scope width.

h

Set scope height.

o

Set window opacity. This window also holds statistics about pixel area.

wx

Set window X position, relative offset on X axis.

wy

Set window Y position, relative offset on Y axis.

#### 39.199.1 Commands# TOC

This filter supports same commands as options.

### 39.200 pp7# TOC

Apply Postprocessing filter 7. It is variant of the spp filter, similar to spp = 6 with 7 point DCT, where only the center sample is used after IDCT.

The filter accepts the following options:

qp

Force a constant quantization parameter. It accepts an integer in range 0 to 63. If not set, the filter will use the QP from the video stream (if available).

mode

Set thresholding mode. Available modes are:

‘hard’

Set hard thresholding.

‘soft’

Set soft thresholding (better de-ringing effect, but likely blurrier).

‘medium’

Set medium thresholding (good results, default).

### 39.201 premultiply# TOC

Apply alpha premultiply effect to input video stream using first plane of second stream as alpha.

Both streams must have same dimensions and same pixel format.

The filter accepts the following option:

planes

Set which planes will be processed, unprocessed planes will be copied. By default value 0xf, all planes will be processed.

inplace

Do not require 2nd input for processing, instead use alpha plane from input stream.

### 39.202 premultiply_dynamic# TOC

Dynamically premultiply or unpremultiply the input video stream as needed, to match the requirements of the downstream filter graph. This is roughly equivalent to either premultiply:inplace=yes or unpremultiply:inplace=yes, or otherwise a noop.

The filter accepts the following option:

planes

Set which planes will be processed, unprocessed planes will be copied. By default value 0xf, all planes will be processed.

### 39.203 prewitt# TOC

Apply prewitt operator to input video stream.

The filter accepts the following option:

planes

Set which planes will be processed, unprocessed planes will be copied. By default value 0xf, all planes will be processed.

scale

Set value which will be multiplied with filtered result.

delta

Set value which will be added to filtered result.

#### 39.203.1 Commands# TOC

This filter supports the all above options as commands.

### 39.204 pseudocolor# TOC

Alter frame colors in video with pseudocolors.

This filter accepts the following options:

c0

set pixel first component expression

c1

set pixel second component expression

c2

set pixel third component expression

c3

set pixel fourth component expression, corresponds to the alpha component

index, i

set component to use as base for altering colors

preset, p

Pick one of built-in LUTs. By default is set to none.

Available LUTs:

‘magma’

‘inferno’

‘plasma’

‘viridis’

‘turbo’

‘cividis’

‘range1’

‘range2’

‘shadows’

‘highlights’

‘solar’

‘nominal’

‘preferred’

‘total’

‘spectral’

‘cool’

‘heat’

‘fiery’

‘blues’

‘green’

‘helix’

opacity

Set opacity of output colors. Allowed range is from 0 to 1. Default value is set to 1.

Each of the expression options specifies the expression to use for computing the lookup table for the corresponding pixel component values.

The expressions can contain the following constants and functions:

w

h

The input width and height.

val

The input value for the pixel component.

ymin, umin, vmin, amin

The minimum allowed component value.

ymax, umax, vmax, amax

The maximum allowed component value.

All expressions default to "val".

#### 39.204.1 Commands# TOC

This filter supports the all above options as commands.

#### 39.204.2 Examples# TOC

- Change too high luma values to gradient:

```
pseudocolor="'if(between(val,ymax,amax),lerp(ymin,ymax,(val-ymax)/(amax-ymax)),-1):if(between(val,ymax,amax),lerp(umax,umin,(val-ymax)/(amax-ymax)),-1):if(between(val,ymax,amax),lerp(vmin,vmax,(val-ymax)/(amax-ymax)),-1):-1'"

```

### 39.205 psnr# TOC

Obtain the average, maximum and minimum PSNR (Peak Signal to Noise Ratio) between two input videos.

This filter takes in input two input videos, the first input is considered the "main" source and is passed unchanged to the output. The second input is used as a "reference" video for computing the PSNR.

Both video inputs must have the same resolution and pixel format for this filter to work correctly. Also it assumes that both inputs have the same number of frames, which are compared one by one.

The obtained average PSNR is printed through the logging system.

The filter stores the accumulated MSE (mean squared error) of each frame, and at the end of the processing it is averaged across all frames equally, and the following formula is applied to obtain the PSNR:

```
PSNR = 10*log10(MAX^2/MSE)

```

Where MAX is the average of the maximum values of each component of the image.

The description of the accepted parameters follows.

stats_file, f

If specified the filter will use the named file to save the PSNR of each individual frame. When filename equals "-" the data is sent to standard output.

stats_version

Specifies which version of the stats file format to use. Details of each format are written below. Default value is 1.

output_max

Determines whether the max value is output to the stats log. Default value is 0. Requires stats_version >= 2. If this is set and stats_version < 2, the filter will return an error.

This filter also supports the framesync options.

The file printed if stats_file is selected, contains a sequence of key/value pairs of the form key:value for each compared couple of frames.

If a stats_version greater than 1 is specified, a header line precedes the list of per-frame-pair stats, with key value pairs following the frame format with the following parameters:

psnr_log_version

The version of the log file format. Will match stats_version.

fields

A comma separated list of the per-frame-pair parameters included in the log.

A description of each shown per-frame-pair parameter follows:

n

sequential number of the input frame, starting from 1

mse_avg

Mean Square Error pixel-by-pixel average difference of the compared frames, averaged over all the image components.

mse_y, mse_u, mse_v, mse_r, mse_g, mse_b, mse_a

Mean Square Error pixel-by-pixel average difference of the compared frames for the component specified by the suffix.

psnr_y, psnr_u, psnr_v, psnr_r, psnr_g, psnr_b, psnr_a

Peak Signal to Noise ratio of the compared frames for the component specified by the suffix.

max_avg, max_y, max_u, max_v

Maximum allowed value for each channel, and average over all channels.

#### 39.205.1 Examples# TOC

- For example:

```
movie=ref_movie.mpg, setpts=PTS-STARTPTS [main];
[main][ref] psnr="stats_file=stats.log" [out]

```

On this example the input file being processed is compared with the reference file ref_movie.mpg. The PSNR of each individual frame is stored in stats.log.

- Another example with different containers:

```
ffmpeg -i main.mpg -i ref.mkv -lavfi  "[0:v]settb=AVTB,setpts=PTS-STARTPTS[main];[1:v]settb=AVTB,setpts=PTS-STARTPTS[ref];[main][ref]psnr" -f null -

```

### 39.206 pullup# TOC

Pulldown reversal (inverse telecine) filter, capable of handling mixed hard-telecine, 24000/1001 fps progressive, and 30000/1001 fps progressive content.

The pullup filter is designed to take advantage of future context in making its decisions. This filter is stateless in the sense that it does not lock onto a pattern to follow, but it instead looks forward to the following fields in order to identify matches and rebuild progressive frames.

To produce content with an even framerate, insert the fps filter after pullup, use fps=24000/1001 if the input frame rate is 29.97fps, fps=24 for 30fps and the (rare) telecined 25fps input.

The filter accepts the following options:

jl

jr

jt

jb

These options set the amount of "junk" to ignore at the left, right, top, and bottom of the image, respectively. Left and right are in units of 8 pixels, while top and bottom are in units of 2 lines. The default is 8 pixels on each side.

sb

Set the strict breaks. Setting this option to 1 will reduce the chances of filter generating an occasional mismatched frame, but it may also cause an excessive number of frames to be dropped during high motion sequences. Conversely, setting it to -1 will make filter match fields more easily. This may help processing of video where there is slight blurring between the fields, but may also cause there to be interlaced frames in the output. Default value is 0.

mp

Set the metric plane to use. It accepts the following values:

‘l’

Use luma plane.

‘u’

Use chroma blue plane.

‘v’

Use chroma red plane.

This option may be set to use chroma plane instead of the default luma plane for doing filter’s computations. This may improve accuracy on very clean source material, but more likely will decrease accuracy, especially if there is chroma noise (rainbow effect) or any grayscale video. The main purpose of setting mp to a chroma plane is to reduce CPU load and make pullup usable in realtime on slow machines.

For best results (without duplicated frames in the output file) it is necessary to change the output frame rate. For example, to inverse telecine NTSC input:

```
ffmpeg -i input -vf pullup -r 24000/1001 ...

```

### 39.207 qp# TOC

Change video quantization parameters (QP).

The filter accepts the following option:

qp

Set expression for quantization parameter.

The expression is evaluated through the eval API and can contain, among others, the following constants:

known

1 if index is not 129, 0 otherwise.

qp

Sequential index starting from -129 to 128.

#### 39.207.1 Examples# TOC

- Some equation like:

```
qp=2+2*sin(PI*qp)

```

### 39.208 qrencode# TOC

Generate a QR code using the libqrencode library (see https://fukuchi.org/works/qrencode/), and overlay it on top of the current frame.

To enable the compilation of this filter, you need to configure FFmpeg with --enable-libqrencode.

The QR code is generated from the provided text or text pattern. The corresponding QR code is scaled and overlaid into the video output according to the specified options.

In case no text is specified, no QR code is overlaied.

This filter accepts the following options:

qrcode_width, q

padded_qrcode_width, Q

Specify an expression for the width of the rendered QR code, with and without padding. The qrcode_width expression can reference the value set by the padded_qrcode_width expression, and vice versa. By default padded_qrcode_width is set to qrcode_width, meaning that there is no padding.

These expressions are evaluated for each new frame.

See the qrencode Expressions section for details.

x

y

Specify an expression for positioning the padded QR code top-left corner. The x expression can reference the value set by the y expression, and vice.

By default x and y are set set to 0, meaning that the QR code is placed in the top left corner of the input.

These expressions are evaluated for each new frame.

See the qrencode Expressions section for details.

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

Select how the input text is expanded. Can be either none, or normal (default). See the qrencode Text expansion section below for details.

text

textfile

Define the text to be rendered. In case neither is specified, no QR is encoded (just an empty colored frame).

In case expansion is enabled, the text is treated as a text template, using the qrencode expansion mechanism. See the qrencode Text expansion section below for details.

background_color, bc

foreground_color, fc

Set the QR code and background color. The default value of foreground_color is "black", the default value of background_color is "white".

For the syntax of the color options, check the "Color" section in the ffmpeg-utils manual.

#### 39.208.1 qrencode Expressions# TOC

The expressions set by the options contain the following constants and functions.

dar

input display aspect ratio, it is the same as (w / h) * sar

duration

the current frame’s duration, in seconds

hsub

vsub

horizontal and vertical chroma subsample values. For example for the pixel format "yuv422p" hsub is 2 and vsub is 1.

main_h, H

the input height

main_w, W

the input width

n

the number of input frame, starting from 0

pict_type

a number representing the picture type

qr_w, w

the width of the encoded QR code

rendered_qr_w, q

rendered_padded_qr_w, Q

the width of the rendered QR code, without and without padding.

These parameters allow the q and Q expressions to refer to each other, so you can for example specify q=3/4*Q.

rand(min, max)

return a random number included between min and max

sar

the input sample aspect ratio

t

timestamp expressed in seconds, NAN if the input timestamp is unknown

x

y

the x and y offset coordinates where the text is drawn.

These parameters allow the x and y expressions to refer to each other, so you can for example specify y=x/dar.

#### 39.208.2 qrencode Text expansion# TOC

If expansion is set to none, the text is printed verbatim.

If expansion is set to normal (which is the default), the following expansion mechanism is used.

The backslash character ‘\’, followed by any character, always expands to the second character.

Sequences of the form %{...} are expanded. The text between the braces is a function name, possibly followed by arguments separated by ’:’. If the arguments contain special characters or delimiters (’:’ or ’}’), they should be escaped.

Note that they probably must also be escaped as the value for the text option in the filter argument string and as the filter argument in the filtergraph description, and possibly also for the shell, that makes up to four levels of escaping; using a text file with the textfile option avoids these problems.

The following functions are available:

n, frame_num

return the frame number

pts

Return the presentation timestamp of the current frame.

It can take up to two arguments.

The first argument is the format of the timestamp; it defaults to flt for seconds as a decimal number with microsecond accuracy; hms stands for a formatted [-]HH:MM:SS.mmm timestamp with millisecond accuracy. gmtime stands for the timestamp of the frame formatted as UTC time; localtime stands for the timestamp of the frame formatted as local time zone time. If the format is set to hms24hh, the time is formatted in 24h format (00-23).

The second argument is an offset added to the timestamp.

If the format is set to localtime or gmtime, a third argument may be supplied: a strftime C function format string. By default, YYYY-MM-DD HH:MM:SS format will be used.

expr, e

Evaluate the expression’s value and output as a double.

It must take one argument specifying the expression to be evaluated, accepting the constants and functions defined in qrencode_expressions.

expr_formatted, ef

Evaluate the expression’s value and output as a formatted string.

The first argument is the expression to be evaluated, just as for the expr function. The second argument specifies the output format. Allowed values are ‘x’, ‘X’, ‘d’ and ‘u’. They are treated exactly as in the printf function. The third parameter is optional and sets the number of positions taken by the output. It can be used to add padding with zeros from the left.

gmtime

The time at which the filter is running, expressed in UTC. It can accept an argument: a strftime C function format string. The format string is extended to support the variable %[1-6]N which prints fractions of the second with optionally specified number of digits.

localtime

The time at which the filter is running, expressed in the local time zone. It can accept an argument: a strftime C function format string. The format string is extended to support the variable %[1-6]N which prints fractions of the second with optionally specified number of digits.

metadata

Frame metadata. Takes one or two arguments.

The first argument is mandatory and specifies the metadata key.

The second argument is optional and specifies a default value, used when the metadata key is not found or empty.

Available metadata can be identified by inspecting entries starting with TAG included within each frame section printed by running ffprobe -show_frames.

String metadata generated in filters leading to the qrencode filter are also available.

rand(min, max)

return a random number included between min and max

#### 39.208.3 Examples# TOC

- Generate a QR code encoding the specified text with the default size, overalaid in the top left corner of the input video, with the default size:

```
qrencode=text=www.ffmpeg.org

```

- Same as below, but select blue on pink colors:

```
qrencode=text=www.ffmpeg.org:bc=pink@0.5:fc=blue

```

- Place the QR code in the bottom right corner of the input video:

```
qrencode=text=www.ffmpeg.org:x=W-Q:y=H-Q

```

- Generate a QR code with width of 200 pixels and padding, making the padded width 4/3 of the QR code width:

```
qrencode=text=www.ffmpeg.org:q=200:Q=4/3*q

```

- Generate a QR code with padded width of 200 pixels and padding, making the QR code width 3/4 of the padded width:

```
qrencode=text=www.ffmpeg.org:Q=200:q=3/4*Q

```

- Make the QR code a fraction of the input video width:

```
qrencode=text=www.ffmpeg.org:q=W/5

```

- Generate a QR code encoding the frame number:

```
qrencode=text=%{n}

```

- Generate a QR code encoding the GMT timestamp:

```
qrencode=text=%{gmtime}

```

- Generate a QR code encoding the timestamp expressed as a float:

```
qrencode=text=%{pts}

```

### 39.209 quirc# TOC

Identify and decode a QR code using the libquirc library (see https://github.com/dlbeer/quirc/), and print the identified QR codes positions and payload as metadata.

To enable the compilation of this filter, you need to configure FFmpeg with --enable-libquirc.

For each found QR code in the input video, some metadata entries are added with the prefix lavfi.quirc.N, where N is the index, starting from 0, associated to the QR code.

A description of each metadata value follows:

lavfi.quirc.count

the number of found QR codes, it is not set in case none was found

lavfi.quirc.N.corner.M.x

lavfi.quirc.N.coreer.M.y

the x/y positions of the four corners of the square containing the QR code, where M is the index of the corner starting from 0

lavfi.quirc.N.payload

the payload of the QR code

### 39.210 random# TOC

Flush video frames from internal cache of frames into a random order. No frame is discarded. Inspired by frei0r nervous filter.

frames

Set size in number of frames of internal cache, in range from 2 to 512. Default is 30.

seed

Set seed for random number generator, must be an integer included between 0 and UINT32_MAX. If not specified, or if explicitly set to less than 0, the filter will try to use a good random seed on a best effort basis.

### 39.211 readeia608# TOC

Read closed captioning (EIA-608) information from the top lines of a video frame.

This filter adds frame metadata for lavfi.readeia608.X.cc and lavfi.readeia608.X.line, where X is the number of the identified line with EIA-608 data (starting from 0). A description of each metadata value follows:

lavfi.readeia608.X.cc

The two bytes stored as EIA-608 data (printed in hexadecimal).

lavfi.readeia608.X.line

The number of the line on which the EIA-608 data was identified and read.

This filter accepts the following options:

scan_min

Set the line to start scanning for EIA-608 data. Default is 0.

scan_max

Set the line to end scanning for EIA-608 data. Default is 29.

spw

Set the ratio of width reserved for sync code detection. Default is 0.27. Allowed range is [0.1 - 0.7].

chp

Enable checking the parity bit. In the event of a parity error, the filter will output 0x00 for that character. Default is false.

lp

Lowpass lines prior to further processing. Default is enabled.

#### 39.211.1 Commands# TOC

This filter supports the all above options as commands.

#### 39.211.2 Examples# TOC

- Output a csv with presentation time and the first two lines of identified EIA-608 captioning data.

```
ffprobe -f lavfi -i movie=captioned_video.mov,readeia608 -show_entries frame=pts_time:frame_tags=lavfi.readeia608.0.cc,lavfi.readeia608.1.cc -of csv

```

### 39.212 readvitc# TOC

Read vertical interval timecode (VITC) information from the top lines of a video frame.

The filter adds frame metadata key lavfi.readvitc.tc_str with the timecode value, if a valid timecode has been detected. Further metadata key lavfi.readvitc.found is set to 0/1 depending on whether timecode data has been found or not.

This filter accepts the following options:

scan_max

Set the maximum number of lines to scan for VITC data. If the value is set to -1 the full video frame is scanned. Default is 45.

thr_b

Set the luma threshold for black. Accepts float numbers in the range [0.0,1.0], default value is 0.2. The value must be equal or less than thr_w.

thr_w

Set the luma threshold for white. Accepts float numbers in the range [0.0,1.0], default value is 0.6. The value must be equal or greater than thr_b.

#### 39.212.1 Examples# TOC

- Detect and draw VITC data onto the video frame; if no valid VITC is detected, draw --:--:--:-- as a placeholder:

```
ffmpeg -i input.avi -filter:v 'readvitc,drawtext=fontfile=FreeMono.ttf:text=%{metadata\\:lavfi.readvitc.tc_str\\:--\\\\\\:--\\\\\\:--\\\\\\:--}:x=(w-tw)/2:y=400-ascent'

```

### 39.213 remap# TOC

Remap pixels using 2nd: Xmap and 3rd: Ymap input video stream.

Destination pixel at position (X, Y) will be picked from source (x, y) position where x = Xmap(X, Y) and y = Ymap(X, Y). If mapping values are out of range, zero value for pixel will be used for destination pixel.

Xmap and Ymap input video streams must be of same dimensions. Output video stream will have Xmap/Ymap video stream dimensions. Xmap and Ymap input video streams are 16bit depth, single channel.

format

Specify pixel format of output from this filter. Can be color or gray. Default is color.

fill

Specify the color of the unmapped pixels. For the syntax of this option, check the "Color" section in the ffmpeg-utils manual. Default color is black.

### 39.214 removegrain# TOC

The removegrain filter is a spatial denoiser for progressive video.

m0

Set mode for the first plane.

m1

Set mode for the second plane.

m2

Set mode for the third plane.

m3

Set mode for the fourth plane.

Range of mode is from 0 to 24. Description of each mode follows:

0

Leave input plane unchanged. Default.

1

Clips the pixel with the minimum and maximum of the 8 neighbour pixels.

2

Clips the pixel with the second minimum and maximum of the 8 neighbour pixels.

3

Clips the pixel with the third minimum and maximum of the 8 neighbour pixels.

4

Clips the pixel with the fourth minimum and maximum of the 8 neighbour pixels. This is equivalent to a median filter.

5

Line-sensitive clipping giving the minimal change.

6

Line-sensitive clipping, intermediate.

7

Line-sensitive clipping, intermediate.

8

Line-sensitive clipping, intermediate.

9

Line-sensitive clipping on a line where the neighbours pixels are the closest.

10

Replaces the target pixel with the closest neighbour.

11

[1 2 1] horizontal and vertical kernel blur.

12

Same as mode 11.

13

Bob mode, interpolates top field from the line where the neighbours pixels are the closest.

14

Bob mode, interpolates bottom field from the line where the neighbours pixels are the closest.

15

Bob mode, interpolates top field. Same as 13 but with a more complicated interpolation formula.

16

Bob mode, interpolates bottom field. Same as 14 but with a more complicated interpolation formula.

17

Clips the pixel with the minimum and maximum of respectively the maximum and minimum of each pair of opposite neighbour pixels.

18

Line-sensitive clipping using opposite neighbours whose greatest distance from the current pixel is minimal.

19

Replaces the pixel with the average of its 8 neighbours.

20

Averages the 9 pixels ([1 1 1] horizontal and vertical blur).

21

Clips pixels using the averages of opposite neighbour.

22

Same as mode 21 but simpler and faster.

23

Small edge and halo removal, but reputed useless.

24

Similar as 23.

### 39.215 removelogo# TOC

Suppress a TV station logo, using an image file to determine which pixels comprise the logo. It works by filling in the pixels that comprise the logo with neighboring pixels.

The filter accepts the following options:

filename, f

Set the filter bitmap file, which can be any image format supported by libavformat. The width and height of the image file must match those of the video stream being processed.

Pixels in the provided bitmap image with a value of zero are not considered part of the logo, non-zero pixels are considered part of the logo. If you use white (255) for the logo and black (0) for the rest, you will be safe. For making the filter bitmap, it is recommended to take a screen capture of a black frame with the logo visible, and then using a threshold filter followed by the erode filter once or twice.

If needed, little splotches can be fixed manually. Remember that if logo pixels are not covered, the filter quality will be much reduced. Marking too many pixels as part of the logo does not hurt as much, but it will increase the amount of blurring needed to cover over the image and will destroy more information than necessary, and extra pixels will slow things down on a large logo.

### 39.216 repeatfields# TOC

This filter uses the repeat_field flag from the Video ES headers and hard repeats fields based on its value.

### 39.217 reverse# TOC

Reverse a video clip.

Warning: This filter requires memory to buffer the entire clip, so trimming is suggested.

#### 39.217.1 Examples# TOC

- Take the first 5 seconds of a clip, and reverse it.

```
trim=end=5,reverse

```

### 39.218 rgbashift# TOC

Shift R/G/B/A pixels horizontally and/or vertically.

The filter accepts the following options:

rh

Set amount to shift red horizontally.

rv

Set amount to shift red vertically.

gh

Set amount to shift green horizontally.

gv

Set amount to shift green vertically.

bh

Set amount to shift blue horizontally.

bv

Set amount to shift blue vertically.

ah

Set amount to shift alpha horizontally.

av

Set amount to shift alpha vertically.

edge

Set edge mode, can be smear, default, or warp.

#### 39.218.1 Commands# TOC

This filter supports the all above options as commands.

### 39.219 roberts# TOC

Apply roberts cross operator to input video stream.

The filter accepts the following option:

planes

Set which planes will be processed, unprocessed planes will be copied. By default value 0xf, all planes will be processed.

scale

Set value which will be multiplied with filtered result.

delta

Set value which will be added to filtered result.

#### 39.219.1 Commands# TOC

This filter supports the all above options as commands.

### 39.220 rotate# TOC

Rotate video by an arbitrary angle expressed in radians.

The filter accepts the following options:

A description of the optional parameters follows.

angle, a

Set an expression for the angle by which to rotate the input video clockwise, expressed as a number of radians. A negative value will result in a counter-clockwise rotation. By default it is set to "0".

This expression is evaluated for each frame.

out_w, ow

Set the output width expression, default value is "iw". This expression is evaluated just once during configuration.

out_h, oh

Set the output height expression, default value is "ih". This expression is evaluated just once during configuration.

bilinear

Enable bilinear interpolation if set to 1, a value of 0 disables it. Default value is 1.

fillcolor, c

Set the color used to fill the output area not covered by the rotated image. For the general syntax of this option, check the "Color" section in the ffmpeg-utils manual. If the special value "none" is selected then no background is printed (useful for example if the background is never shown).

Default value is "black".

The expressions for the angle and the output size can contain the following constants and functions:

n

sequential number of the input frame, starting from 0. It is always NAN before the first frame is filtered.

t

time in seconds of the input frame, it is set to 0 when the filter is configured. It is always NAN before the first frame is filtered.

hsub

vsub

horizontal and vertical chroma subsample values. For example for the pixel format "yuv422p" hsub is 2 and vsub is 1.

in_w, iw

in_h, ih

the input video width and height

out_w, ow

out_h, oh

the output width and height, that is the size of the padded area as specified by the width and height expressions

rotw(a)

roth(a)

the minimal width/height required for completely containing the input video rotated by a radians.

These are only available when computing the out_w and out_h expressions.

#### 39.220.1 Examples# TOC

- Rotate the input by PI/6 radians clockwise:

```
rotate=PI/6

```

- Rotate the input by PI/6 radians counter-clockwise:

```
rotate=-PI/6

```

- Rotate the input by 45 degrees clockwise:

```
rotate=45*PI/180

```

- Apply a constant rotation with period T, starting from an angle of PI/3:

```
rotate=PI/3+2*PI*t/T

```

- Make the input video rotation oscillating with a period of T seconds and an amplitude of A radians:

```
rotate=A*sin(2*PI/T*t)

```

- Rotate the video, output size is chosen so that the whole rotating input video is always completely contained in the output:

```
rotate='2*PI*t:ow=hypot(iw,ih):oh=ow'

```

- Rotate the video, reduce the output size so that no background is ever shown:

```
rotate=2*PI*t:ow='min(iw,ih)/sqrt(2)':oh=ow:c=none

```

#### 39.220.2 Commands# TOC

The filter supports the following commands:

a, angle

Set the angle expression. The command accepts the same syntax of the corresponding option.

If the specified expression is not valid, it is kept at its current value.

### 39.221 sab# TOC

Apply Shape Adaptive Blur.

The filter accepts the following options:

luma_radius, lr

Set luma blur filter strength, must be a value in range 0.1-4.0, default value is 1.0. A greater value will result in a more blurred image, and in slower processing.

luma_pre_filter_radius, lpfr

Set luma pre-filter radius, must be a value in the 0.1-2.0 range, default value is 1.0.

luma_strength, ls

Set luma maximum difference between pixels to still be considered, must be a value in the 0.1-100.0 range, default value is 1.0.

chroma_radius, cr

Set chroma blur filter strength, must be a value in range -0.9-4.0. A greater value will result in a more blurred image, and in slower processing.

chroma_pre_filter_radius, cpfr

Set chroma pre-filter radius, must be a value in the -0.9-2.0 range.

chroma_strength, cs

Set chroma maximum difference between pixels to still be considered, must be a value in the -0.9-100.0 range.

Each chroma option value, if not explicitly specified, is set to the corresponding luma option value.

### 39.222 scale# TOC

Scale (resize) the input video, using the libswscale library.

The scale filter forces the output display aspect ratio to be the same of the input, by changing the output sample aspect ratio.

If the input image format is different from the format requested by the next filter, the scale filter will convert the input to the requested format.

#### 39.222.1 Options# TOC

The filter accepts the following options, any of the options supported by the libswscale scaler, as well as any of the framesync options.

See the ffmpeg-scaler manual for the complete list of scaler options.

width, w

height, h

Set the output video dimension expression. Default value is the input dimension.

If the width or w value is 0, the input width is used for the output. If the height or h value is 0, the input height is used for the output.

If one and only one of the values is -n with n >= 1, the scale filter will use a value that maintains the aspect ratio of the input image, calculated from the other specified dimension. After that it will, however, make sure that the calculated dimension is divisible by n and adjust the value if necessary.

If both values are -n with n >= 1, the behavior will be identical to both values being set to 0 as previously detailed.

See below for the list of accepted constants for use in the dimension expression.

eval

Specify when to evaluate width and height expression. It accepts the following values:

‘init’

Only evaluate expressions once during the filter initialization or when a command is processed.

‘frame’

Evaluate expressions for each incoming frame.

Default value is ‘init’.

interl

Set the interlacing mode. It accepts the following values:

‘1’

Force interlaced aware scaling.

‘0’

Do not apply interlaced scaling.

‘-1’

Select interlaced aware scaling depending on whether the source frames are flagged as interlaced or not.

Default value is ‘0’.

flags

Set libswscale scaling flags. See the ffmpeg-scaler manual for the complete list of values. If not explicitly specified the filter applies the default flags.

param0, param1

Set libswscale input parameters for scaling algorithms that need them. See the ffmpeg-scaler manual for the complete documentation. If not explicitly specified the filter applies empty parameters.

intent

Set the ICC rendering intent to use when transforming between different color spaces. It accepts the following values:

‘perceptual’

Use a perceptually guided tone and gamut mapping curve. The exact details of the mapping used may change at any time and should not be relied on as stable. This intent is recommended for final viewing of image/video content in typical viewing settings.

‘relative_colorimetric’

Statically clip out-of-gamut colors using a colorimetric clipping curve which attempts to find the colorimetrically least dissimilar in-gamut color. This intent performs white point adaptation and black point adaptation. This is the default. This intent is recommended wherever faithful color reproduction is of the utmost importance, even at the cost of clipping.

‘absolute_colorimetric’

Hard clip out-of-gamut colors with no attempt at white or black point reproduction. This intent will reproduce in-gamut colors 1:1 on the output display as they would appear on the reference display, assuming the output display is appropriately calibrated.

‘saturation’

Performs saturation mapping - that is, stretches the input color volume directly onto the output color volume, in non-linear fashion that preserves the original signal appearance as much as possible. This intent is recommended for signal content evaluation, as it will not lead to any clipping. It is roughly analogous to not performing any color mapping, although it still takes into account the mastering display primaries and any differences in encoding TRC.

size, s

Set the video size. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual.

in_color_matrix

out_color_matrix

Set in/output YCbCr color space type.

This allows the autodetected value to be overridden as well as allows forcing a specific value used for the output and encoder.

If not specified, the color space type depends on the pixel format.

Possible values:

‘auto’

Choose automatically.

‘bt709’

Format conforming to International Telecommunication Union (ITU) Recommendation BT.709.

‘fcc’

Set color space conforming to the United States Federal Communications Commission (FCC) Code of Federal Regulations (CFR) Title 47 (2003) 73.682 (a).

‘bt601’

‘bt470’

‘smpte170m’

Set color space conforming to:

- ITU Radiocommunication Sector (ITU-R) Recommendation BT.601

- ITU-R Rec. BT.470-6 (1998) Systems B, B1, and G

- Society of Motion Picture and Television Engineers (SMPTE) ST 170:2004

‘smpte240m’

Set color space conforming to SMPTE ST 240:1999.

‘bt2020’

Set color space conforming to ITU-R BT.2020 non-constant luminance system.

in_range

out_range

Set in/output YCbCr sample range.

This allows the autodetected value to be overridden as well as allows forcing a specific value used for the output and encoder. If not specified, the range depends on the pixel format. Possible values:

‘auto/unknown’

Choose automatically.

‘jpeg/full/pc’

Set full range (0-255 in case of 8-bit luma).

‘mpeg/limited/tv’

Set "MPEG" range (16-235 in case of 8-bit luma).

in_chroma_loc

out_chroma_loc

Set in/output chroma sample location. If in_chroma_loc is not specified, the chroma location tagged on the input frame is used, and untagged input is assumed to be sited like the output, so it is tagged but not converted. If out_chroma_loc is not specified, the output is converted to the chroma location negotiated with the rest of the filtergraph, or keeps the input location if none was negotiated. Possible values:

‘auto, unknown’

‘left’

‘center’

‘topleft’

‘top’

‘bottomleft’

‘bottom’

in_primaries

out_primaries

Set in/output RGB primaries.

This allows the autodetected value to be overridden as well as allows forcing a specific value used for the output and encoder. Possible values:

‘auto’

Choose automatically. This is the default.

‘bt709’

‘bt470m’

‘bt470bg’

‘smpte170m’

‘smpte240m’

‘film’

‘bt2020’

‘smpte428’

‘smpte431’

‘smpte432’

‘jedec-p22’

‘ebu3213’

in_transfer

out_transfer

Set in/output transfer response curve (TRC).

This allows the autodetected value to be overridden as well as allows forcing a specific value used for the output and encoder. Possible values:

‘auto’

Choose automatically. This is the default.

‘bt709’

‘bt470m’

‘gamma22’

‘bt470bg’

‘gamma28’

‘smpte170m’

‘smpte240m’

‘linear’

‘iec61966-2-1’

‘srgb’

‘iec61966-2-4’

‘xvycc’

‘bt1361e’

‘bt2020-10’

‘bt2020-12’

‘smpte2084’

‘smpte428’

‘arib-std-b67’

force_original_aspect_ratio

Enable decreasing or increasing output video width or height if necessary to keep the original aspect ratio. Possible values:

‘disable’

Scale the video as specified and disable this feature.

‘decrease’

The output video dimensions will automatically be decreased if needed.

‘increase’

The output video dimensions will automatically be increased if needed.

One useful instance of this option is that when you know a specific device’s maximum allowed resolution, you can use this to limit the output video to that, while retaining the aspect ratio. For example, device A allows 1280x720 playback, and your video is 1920x800. Using this option (set it to decrease) and specifying 1280x720 to the command line makes the output 1280x533.

Please note that this is a different thing than specifying -1 for w or h, you still need to specify the output resolution for this option to work.

force_divisible_by

Ensures that both the output dimensions, width and height, are divisible by the given integer when used together with force_original_aspect_ratio. This works similar to using -n in the w and h options.

This option respects the value set for force_original_aspect_ratio, increasing or decreasing the resolution accordingly. The video’s aspect ratio may be slightly modified.

This option can be handy if you need to have a video fit within or exceed a defined resolution using force_original_aspect_ratio but also have encoder restrictions on width or height divisibility.

reset_sar

Enabling this option leads to the output SAR being reset to 1. Additionally, if the user requests proportional scaling either through the width or height expressions, e.g. w=-4:h=360 or w=iw/2:h=-1 or by enabling force_original_aspect_ratio, then the input DAR is taken into account and the output is scaled to produce square pixels. Default is false.

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

n

The (sequential) number of the input frame, starting from 0. Only available with eval=frame.

t

The presentation timestamp of the input frame, expressed as a number of seconds. Only available with eval=frame.

pos

The position (byte offset) of the frame in the input stream, or NaN if this information is unavailable and/or meaningless (for example in case of synthetic video). Only available with eval=frame. Deprecated, do not use.

ref_w, rw

ref_h, rh

ref_a

ref_dar, rdar

ref_n

ref_t

ref_pos

Eqvuialent to the above, but for a second reference input. If any of these variables are present, this filter accepts two inputs.

#### 39.222.2 Examples# TOC

- Scale the input video to a size of 200x100

```
scale=w=200:h=100

```

This is equivalent to:

```
scale=200:100

```

or:

```
scale=200x100

```

- Specify a size abbreviation for the output size:

```
scale=qcif

```

which can also be written as:

```
scale=size=qcif

```

- Scale the input to 2x:

```
scale=w=2*iw:h=2*ih

```

- The above is the same as:

```
scale=2*in_w:2*in_h

```

- Scale the input to 2x with forced interlaced scaling:

```
scale=2*iw:2*ih:interl=1

```

- Scale the input to half size:

```
scale=w=iw/2:h=ih/2

```

- Increase the width, and set the height to the same size:

```
scale=3/2*iw:ow

```

- Seek Greek harmony:

```
scale=iw:1/PHI*iw
scale=ih*PHI:ih

```

- Increase the height, and set the width to 3/2 of the height:

```
scale=w=3/2*oh:h=3/5*ih

```

- Increase the size, making the size a multiple of the chroma subsample values:

```
scale="trunc(3/2*iw/hsub)*hsub:trunc(3/2*ih/vsub)*vsub"

```

- Increase the width to a maximum of 500 pixels, keeping the same aspect ratio as the input:

```
scale=w='min(500\, iw*3/2):h=-1'

```

- Make pixels square by combining scale and setsar:

```
scale='trunc(ih*dar):ih',setsar=1/1

```

- Make pixels square using reset_sar, making sure the resulting resolution is even (required by some codecs):

```
scale='-2:ih-mod(ih,2):reset_sar=1'

```

- Scale to target exactly, however reset SAR to 1:

```
scale='400:300:reset_sar=1'

```

- Scale to even dimensions that fit within 400x300, preserving input SAR:

```
scale='400:300:force_original_aspect_ratio=decrease:force_divisible_by=2'

```

- Scale to produce square pixels with even dimensions that fit within 400x300:

```
scale='400:300:force_original_aspect_ratio=decrease:force_divisible_by=2:reset_sar=1'

```

- Scale a subtitle stream (sub) to match the main video (main) in size before overlaying. ("scale2ref")

```
'[main]split[a][b]; [ref][a]scale=rw:rh[c]; [b][c]overlay'

```

- Scale a logo to 1/10th the height of a video, while preserving its display aspect ratio.

```
[logo-in][video-in]scale=w=oh*dar:h=rh/10[logo-out]

```

#### 39.222.3 Commands# TOC

This filter supports the following commands:

width, w

height, h

Set the output video dimension expression. The command accepts the same syntax of the corresponding option.

If the specified expression is not valid, it is kept at its current value.

### 39.223 scharr# TOC

Apply scharr operator to input video stream.

The filter accepts the following option:

planes

Set which planes will be processed, unprocessed planes will be copied. By default value 0xf, all planes will be processed.

scale

Set value which will be multiplied with filtered result.

delta

Set value which will be added to filtered result.

#### 39.223.1 Commands# TOC

This filter supports the all above options as commands.

### 39.224 scroll# TOC

Scroll input video horizontally and/or vertically by constant speed.

The filter accepts the following options:

horizontal, h

Set the horizontal scrolling speed. Default is 0. Allowed range is from -1 to 1. Negative values changes scrolling direction.

vertical, v

Set the vertical scrolling speed. Default is 0. Allowed range is from -1 to 1. Negative values changes scrolling direction.

hpos

Set the initial horizontal scrolling position. Default is 0. Allowed range is from 0 to 1.

vpos

Set the initial vertical scrolling position. Default is 0. Allowed range is from 0 to 1.

#### 39.224.1 Commands# TOC

This filter supports the following commands:

horizontal, h

Set the horizontal scrolling speed.

vertical, v

Set the vertical scrolling speed.

### 39.225 scdet# TOC

Detect video scene change.

This filter sets frame metadata with mafd between frame, the scene score, and forward the frame to the next filter, so they can use these metadata to detect scene change or others.

In addition, this filter logs a message and sets frame metadata when it detects a scene change by threshold.

lavfi.scd.mafd metadata keys are set with mafd for every frame.

lavfi.scd.score metadata keys are set with scene change score for every frame to detect scene change.

lavfi.scd.time metadata keys are set with current filtered frame time which detect scene change with threshold.

The filter accepts the following options:

threshold, t

Set the scene change detection threshold as a percentage of maximum change. Good values are in the [8.0, 14.0] range. The range for threshold is [0., 100.].

Default value is 10..

sc_pass, s

Set the flag to pass scene change frames to the next filter. Default value is 0 You can enable it if you want to get snapshot of scene change frames only.

### 39.226 selectivecolor# TOC

Adjust cyan, magenta, yellow and black (CMYK) to certain ranges of colors (such as "reds", "yellows", "greens", "cyans", ...). The adjustment range is defined by the "purity" of the color (that is, how saturated it already is).

This filter is similar to the Adobe Photoshop Selective Color tool.

The filter accepts the following options:

correction_method

Select color correction method.

Available values are:

‘absolute’

Specified adjustments are applied "as-is" (added/subtracted to original pixel component value).

‘relative’

Specified adjustments are relative to the original component value.

Default is absolute.

reds

Adjustments for red pixels (pixels where the red component is the maximum)

yellows

Adjustments for yellow pixels (pixels where the blue component is the minimum)

greens

Adjustments for green pixels (pixels where the green component is the maximum)

cyans

Adjustments for cyan pixels (pixels where the red component is the minimum)

blues

Adjustments for blue pixels (pixels where the blue component is the maximum)

magentas

Adjustments for magenta pixels (pixels where the green component is the minimum)

whites

Adjustments for white pixels (pixels where all components are greater than 128)

neutrals

Adjustments for all pixels except pure black and pure white

blacks

Adjustments for black pixels (pixels where all components are lesser than 128)

psfile

Specify a Photoshop selective color file (.asv) to import the settings from.

All the adjustment settings (reds, yellows, ...) accept up to 4 space separated floating point adjustment values in the [-1,1] range, respectively to adjust the amount of cyan, magenta, yellow and black for the pixels of its range.

#### 39.226.1 Examples# TOC

- Increase cyan by 50% and reduce yellow by 33% in every green areas, and increase magenta by 27% in blue areas:

```
selectivecolor=greens=.5 0 -.33 0:blues=0 .27

```

- Use a Photoshop selective color preset:

```
selectivecolor=psfile=MySelectiveColorPresets/Misty.asv

```

### 39.227 separatefields# TOC

The separatefields takes a frame-based video input and splits each frame into its components fields, producing a new half height clip with twice the frame rate and twice the frame count.

This filter use field-dominance information in frame to decide which of each pair of fields to place first in the output. If it gets it wrong use setfield filter before separatefields filter.

### 39.228 setdar, setsar# TOC

The setdar filter sets the Display Aspect Ratio for the filter output video.

This is done by changing the specified Sample (aka Pixel) Aspect Ratio, according to the following equation:

```
DAR = HORIZONTAL_RESOLUTION / VERTICAL_RESOLUTION * SAR

```

Keep in mind that the setdar filter does not modify the pixel dimensions of the video frame. Also, the display aspect ratio set by this filter may be changed by later filters in the filterchain, e.g. in case of scaling or if another "setdar" or a "setsar" filter is applied.

The setsar filter sets the Sample (aka Pixel) Aspect Ratio for the filter output video.

Note that as a consequence of the application of this filter, the output display aspect ratio will change according to the equation above.

Keep in mind that the sample aspect ratio set by the setsar filter may be changed by later filters in the filterchain, e.g. if another "setsar" or a "setdar" filter is applied.

It accepts the following parameters:

r, ratio, dar (setdar only), sar (setsar only)

Set the aspect ratio used by the filter.

The parameter can be a floating point number string, or an expression. If the parameter is not specified, the value "0" is assumed, meaning that the same input value is used.

max

Set the maximum integer value to use for expressing numerator and denominator when reducing the expressed aspect ratio to a rational. Default value is 100.

The parameter sar is an expression containing the following constants:

w, h

The input width and height.

a

Same as w / h.

sar

The input sample aspect ratio.

dar

The input display aspect ratio. It is the same as (w / h) * sar.

hsub, vsub

Horizontal and vertical chroma subsample values. For example, for the pixel format "yuv422p" hsub is 2 and vsub is 1.

#### 39.228.1 Examples# TOC

- To change the display aspect ratio to 16:9, specify one of the following:

```
setdar=dar=1.77777
setdar=dar=16/9

```

- To change the sample aspect ratio to 10:11, specify:

```
setsar=sar=10/11

```

- To set a display aspect ratio of 16:9, and specify a maximum integer value of 1000 in the aspect ratio reduction, use the command:

```
setdar=ratio=16/9:max=1000

```

### 39.229 setfield# TOC

Force field for the output video frame.

The setfield filter marks the interlace type field for the output frames. It does not change the input frame, but only sets the corresponding property, which affects how the frame is treated by following filters (e.g. fieldorder or yadif).

The filter accepts the following options:

mode

Available values are:

‘auto’

Keep the same field property.

‘bff’

Mark the frame as bottom-field-first.

‘tff’

Mark the frame as top-field-first.

‘prog’

Mark the frame as progressive.

### 39.230 setparams# TOC

Force frame parameter for the output video frame.

The setparams filter marks interlace and color range for the output frames. It does not change the input frame, but only sets the corresponding property, which affects how the frame is treated by filters/encoders.

field_mode

Available values are:

‘auto’

Keep the same field property (default).

‘bff’

Mark the frame as bottom-field-first.

‘tff’

Mark the frame as top-field-first.

‘prog’

Mark the frame as progressive.

range

Available values are:

‘auto’

Keep the same color range property (default).

‘unspecified, unknown’

Mark the frame as unspecified color range.

‘limited, tv, mpeg’

Mark the frame as limited range.

‘full, pc, jpeg’

Mark the frame as full range.

color_primaries

Set the color primaries. Available values are:

‘auto’

Keep the same color primaries property (default).

‘bt709’

‘unknown’

‘bt470m’

‘bt470bg’

‘smpte170m’

‘smpte240m’

‘film’

‘bt2020’

‘smpte428’

‘smpte431’

‘smpte432’

‘jedec-p22’

color_trc

Set the color transfer. Available values are:

‘auto’

Keep the same color trc property (default).

‘bt709’

‘unknown’

‘bt470m’

‘bt470bg’

‘smpte170m’

‘smpte240m’

‘linear’

‘log100’

‘log316’

‘iec61966-2-4’

‘bt1361e’

‘iec61966-2-1’

‘bt2020-10’

‘bt2020-12’

‘smpte2084’

‘smpte428’

‘arib-std-b67’

colorspace

Set the colorspace. Available values are:

‘auto’

Keep the same colorspace property (default).

‘gbr’

‘bt709’

‘unknown’

‘fcc’

‘bt470bg’

‘smpte170m’

‘smpte240m’

‘ycgco’

‘bt2020nc’

‘bt2020c’

‘smpte2085’

‘chroma-derived-nc’

‘chroma-derived-c’

‘ictcp’

chroma_location

Set the chroma sample location. Available values are:

‘auto’

Keep the same chroma location (default).

‘unspecified, unknown’

‘left’

‘center’

‘topleft’

‘top’

‘bottomleft’

‘bottom’

alpha_mode

Set the alpha moda. Available values are:

‘auto’

Keep the same alpha mode (default).

‘unspecified, unknown’

‘premultiplied’

‘straight’

### 39.231 shear# TOC

Apply shear transform to input video.

This filter supports the following options:

shx

Shear factor in X-direction. Default value is 0. Allowed range is from -2 to 2.

shy

Shear factor in Y-direction. Default value is 0. Allowed range is from -2 to 2.

fillcolor, c

Set the color used to fill the output area not covered by the transformed video. For the general syntax of this option, check the "Color" section in the ffmpeg-utils manual. If the special value "none" is selected then no background is printed (useful for example if the background is never shown).

Default value is "black".

interp

Set interpolation type. Can be bilinear or nearest. Default is bilinear.

#### 39.231.1 Commands# TOC

This filter supports the all above options as commands.

### 39.232 showinfo# TOC

Show a line containing various information for each input video frame. The input video is not modified.

This filter supports the following options:

checksum

Calculate checksums of each plane. By default enabled.

udu_sei_as_ascii

Try to print user data unregistered SEI as ascii character when possible, in hex format otherwise.

The shown line contains a sequence of key/value pairs of the form key:value.

The following values are shown in the output:

n

The (sequential) number of the input frame, starting from 0.

pts

The Presentation TimeStamp of the input frame, expressed as a number of time base units. The time base unit depends on the filter input pad.

pts_time

The Presentation TimeStamp of the input frame, expressed as a number of seconds.

fmt

The pixel format name.

sar

The sample aspect ratio of the input frame, expressed in the form num/den.

s

The size of the input frame. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual.

i

The type of interlaced mode ("P" for "progressive", "T" for top field first, "B" for bottom field first).

iskey

This is 1 if the frame is a key frame, 0 otherwise.

type

The picture type of the input frame ("I" for an I-frame, "P" for a P-frame, "B" for a B-frame, or "?" for an unknown type). Also refer to the documentation of the AVPictureType enum and of the av_get_picture_type_char function defined in libavutil/avutil.h.

checksum

The Adler-32 checksum (printed in hexadecimal) of all the planes of the input frame.

plane_checksum

The Adler-32 checksum (printed in hexadecimal) of each plane of the input frame, expressed in the form "[c0 c1 c2 c3]".

mean

The mean value of pixels in each plane of the input frame, expressed in the form "[mean0 mean1 mean2 mean3]".

stdev

The standard deviation of pixel values in each plane of the input frame, expressed in the form "[stdev0 stdev1 stdev2 stdev3]".

### 39.233 showpalette# TOC

Displays the 256 colors palette of each frame. This filter is only relevant for pal8 pixel format frames.

It accepts the following option:

s

Set the size of the box used to represent one palette color entry. Default is 30 (for a 30x30 pixel box).

### 39.234 shuffleframes# TOC

Reorder and/or duplicate and/or drop video frames.

It accepts the following parameters:

mapping

Set the destination indexes of input frames. This is space or ’|’ separated list of indexes that maps input frames to output frames. Number of indexes also sets maximal value that each index may have. ’-1’ index have special meaning and that is to drop frame.

The first frame has the index 0. The default is to keep the input unchanged.

#### 39.234.1 Examples# TOC

- Swap second and third frame of every three frames of the input:

```
ffmpeg -i INPUT -vf "shuffleframes=0 2 1" OUTPUT

```

- Swap 10th and 1st frame of every ten frames of the input:

```
ffmpeg -i INPUT -vf "shuffleframes=9 1 2 3 4 5 6 7 8 0" OUTPUT

```

### 39.235 shufflepixels# TOC

Reorder pixels in video frames.

This filter accepts the following options:

direction, d

Set shuffle direction. Can be forward or inverse direction. Default direction is forward.

mode, m

Set shuffle mode. Can be horizontal, vertical or block mode.

width, w

height, h

Set shuffle block_size. In case of horizontal shuffle mode only width part of size is used, and in case of vertical shuffle mode only height part of size is used.

seed, s

Set random seed used with shuffling pixels. Mainly useful to set to be able to reverse filtering process to get original input. For example, to reverse forward shuffle you need to use same parameters and exact same seed and to set direction to inverse.

### 39.236 shuffleplanes# TOC

Reorder and/or duplicate video planes.

It accepts the following parameters:

map0

The index of the input plane to be used as the first output plane.

map1

The index of the input plane to be used as the second output plane.

map2

The index of the input plane to be used as the third output plane.

map3

The index of the input plane to be used as the fourth output plane.

The first plane has the index 0. The default is to keep the input unchanged.

#### 39.236.1 Examples# TOC

- Swap the second and third planes of the input:

```
ffmpeg -i INPUT -vf shuffleplanes=0:2:1:3 OUTPUT

```

### 39.237 signalstats# TOC

Evaluate various visual metrics that assist in determining issues associated with the digitization of analog video media.

By default the filter will log these metadata values:

YMIN

Display the minimal Y value contained within the input frame. Expressed in range of [0-255].

YLOW

Display the Y value at the 10% percentile within the input frame. Expressed in range of [0-255].

YAVG

Display the average Y value within the input frame. Expressed in range of [0-255].

YHIGH

Display the Y value at the 90% percentile within the input frame. Expressed in range of [0-255].

YMAX

Display the maximum Y value contained within the input frame. Expressed in range of [0-255].

UMIN

Display the minimal U value contained within the input frame. Expressed in range of [0-255].

ULOW

Display the U value at the 10% percentile within the input frame. Expressed in range of [0-255].

UAVG

Display the average U value within the input frame. Expressed in range of [0-255].

UHIGH

Display the U value at the 90% percentile within the input frame. Expressed in range of [0-255].

UMAX

Display the maximum U value contained within the input frame. Expressed in range of [0-255].

VMIN

Display the minimal V value contained within the input frame. Expressed in range of [0-255].

VLOW

Display the V value at the 10% percentile within the input frame. Expressed in range of [0-255].

VAVG

Display the average V value within the input frame. Expressed in range of [0-255].

VHIGH

Display the V value at the 90% percentile within the input frame. Expressed in range of [0-255].

VMAX

Display the maximum V value contained within the input frame. Expressed in range of [0-255].

SATMIN

Display the minimal saturation value contained within the input frame. Expressed in range of [0-~181.02].

SATLOW

Display the saturation value at the 10% percentile within the input frame. Expressed in range of [0-~181.02].

SATAVG

Display the average saturation value within the input frame. Expressed in range of [0-~181.02].

SATHIGH

Display the saturation value at the 90% percentile within the input frame. Expressed in range of [0-~181.02].

SATMAX

Display the maximum saturation value contained within the input frame. Expressed in range of [0-~181.02].

HUEMED

Display the median value for hue within the input frame. Expressed in range of [0-360].

HUEAVG

Display the average value for hue within the input frame. Expressed in range of [0-360].

YDIF

Display the average of sample value difference between all values of the Y plane in the current frame and corresponding values of the previous input frame. Expressed in range of [0-255].

UDIF

Display the average of sample value difference between all values of the U plane in the current frame and corresponding values of the previous input frame. Expressed in range of [0-255].

VDIF

Display the average of sample value difference between all values of the V plane in the current frame and corresponding values of the previous input frame. Expressed in range of [0-255].

YBITDEPTH

Display bit depth of Y plane in current frame. Expressed in range of [0-16].

UBITDEPTH

Display bit depth of U plane in current frame. Expressed in range of [0-16].

VBITDEPTH

Display bit depth of V plane in current frame. Expressed in range of [0-16].

The filter accepts the following options:

stat

out

stat specify an additional form of image analysis. out output video with the specified type of pixel highlighted.

Both options accept the following values:

‘tout’

Identify temporal outliers pixels. A temporal outlier is a pixel unlike the neighboring pixels of the same field. Examples of temporal outliers include the results of video dropouts, head clogs, or tape tracking issues.

‘vrep’

Identify vertical line repetition. Vertical line repetition includes similar rows of pixels within a frame. In born-digital video vertical line repetition is common, but this pattern is uncommon in video digitized from an analog source. When it occurs in video that results from the digitization of an analog source it can indicate concealment from a dropout compensator.

‘brng’

Identify pixels that fall outside of legal broadcast range.

color, c

Set the highlight color for the out option. The default color is yellow.

#### 39.237.1 Examples# TOC

- Output data of various video metrics:

```
ffprobe -f lavfi movie=example.mov,signalstats="stat=tout+vrep+brng" -show_frames

```

- Output specific data about the minimum and maximum values of the Y plane per frame:

```
ffprobe -f lavfi movie=example.mov,signalstats -show_entries frame_tags=lavfi.signalstats.YMAX,lavfi.signalstats.YMIN

```

- Playback video while highlighting pixels that are outside of broadcast range in red.

```
ffplay example.mov -vf signalstats="out=brng:color=red"

```

- Playback video with signalstats metadata drawn over the frame.

```
ffplay example.mov -vf signalstats=stat=brng+vrep+tout,drawtext=fontfile=FreeSerif.ttf:textfile=signalstat_drawtext.txt

```

The contents of signalstat_drawtext.txt used in the command are:

```
time %{pts:hms}
Y (%{metadata:lavfi.signalstats.YMIN}-%{metadata:lavfi.signalstats.YMAX})
U (%{metadata:lavfi.signalstats.UMIN}-%{metadata:lavfi.signalstats.UMAX})
V (%{metadata:lavfi.signalstats.VMIN}-%{metadata:lavfi.signalstats.VMAX})
saturation maximum: %{metadata:lavfi.signalstats.SATMAX}

```

### 39.238 signature# TOC

Calculates the MPEG-7 Video Signature. The filter can handle more than one input. In this case the matching between the inputs can be calculated additionally. The filter always passes through the first input. The signature of each stream can be written into a file.

It accepts the following options:

detectmode

Enable or disable the matching process.

Available values are:

‘off’

Disable the calculation of a matching (default).

‘full’

Calculate the matching for the whole video and output whether the whole video matches or only parts.

‘fast’

Calculate only until a matching is found or the video ends. Should be faster in some cases.

nb_inputs

Set the number of inputs. The option value must be a non negative integer. Default value is 1.

filename

Set the path to which the output is written. If there is more than one input, the path must be a prototype, i.e. must contain %d or %0nd (where n is a positive integer), that will be replaced with the input number. If no filename is specified, no output will be written. This is the default.

format

Choose the output format.

Available values are:

‘binary’

Use the specified binary representation (default).

‘xml’

Use the specified xml representation.

th_d

Set threshold to detect one word as similar. The option value must be an integer greater than zero. The default value is 9000.

th_dc

Set threshold to detect all words as similar. The option value must be an integer greater than zero. The default value is 60000.

th_xh

Set threshold to detect frames as similar. The option value must be an integer greater than zero. The default value is 116.

th_di

Set the minimum length of a sequence in frames to recognize it as matching sequence. The option value must be a non negative integer value. The default value is 0.

th_it

Set the minimum relation, that matching frames to all frames must have. The option value must be a double value between 0 and 1. The default value is 0.5.

#### 39.238.1 Examples# TOC

- To calculate the signature of an input video and store it in signature.bin:

```
ffmpeg -i input.mkv -vf signature=filename=signature.bin -map 0:v -f null -

```

- To detect whether two videos match and store the signatures in XML format in signature0.xml and signature1.xml:

```
ffmpeg -i input1.mkv -i input2.mkv -filter_complex "[0:v][1:v] signature=nb_inputs=2:detectmode=full:format=xml:filename=signature%d.xml" -map :v -f null -

```

### 39.239 siti# TOC

Calculate Spatial Information (SI) and Temporal Information (TI) scores for a video, as defined in ITU-T Rec. P.910 (11/21): Subjective video quality assessment methods for multimedia applications. Available PDF at https://www.itu.int/rec/T-REC-P.910-202111-S/en. Note that this is a legacy implementation that corresponds to a superseded recommendation. Refer to ITU-T Rec. P.910 (07/22) for the latest version: https://www.itu.int/rec/T-REC-P.910-202207-I/en

It accepts the following option:

print_summary

If set to 1, Summary statistics will be printed to the console. Default 0.

#### 39.239.1 Examples# TOC

- To calculate SI/TI metrics and print summary:

```
ffmpeg -i input.mp4 -vf siti=print_summary=1 -f null -

```

### 39.240 smartblur# TOC

Blur the input video without impacting the outlines.

It accepts the following options:

luma_radius, lr

Set the luma radius. The option value must be a float number in the range [0.1,5.0] that specifies the variance of the gaussian filter used to blur the image (slower if larger). Default value is 1.0.

luma_strength, ls

Set the luma strength. The option value must be a float number in the range [-1.0,1.0] that configures the blurring. A value included in [0.0,1.0] will blur the image whereas a value included in [-1.0,0.0] will sharpen the image. Default value is 1.0.

luma_threshold, lt

Set the luma threshold used as a coefficient to determine whether a pixel should be blurred or not. The option value must be an integer in the range [-30,30]. A value of 0 will filter all the image, a value included in [0,30] will filter flat areas and a value included in [-30,0] will filter edges. Default value is 0.

chroma_radius, cr

Set the chroma radius. The option value must be a float number in the range [0.1,5.0] that specifies the variance of the gaussian filter used to blur the image (slower if larger). Default value is luma_radius.

chroma_strength, cs

Set the chroma strength. The option value must be a float number in the range [-1.0,1.0] that configures the blurring. A value included in [0.0,1.0] will blur the image whereas a value included in [-1.0,0.0] will sharpen the image. Default value is luma_strength.

chroma_threshold, ct

Set the chroma threshold used as a coefficient to determine whether a pixel should be blurred or not. The option value must be an integer in the range [-30,30]. A value of 0 will filter all the image, a value included in [0,30] will filter flat areas and a value included in [-30,0] will filter edges. Default value is luma_threshold.

alpha_radius, ar

Set the alpha radius. The option value must be a float number in the range [0.1,5.0] that specifies the variance of the gaussian filter used to blur the image (slower if larger). Default value is luma_radius.

alpha_strength, as

Set the alpha strength. The option value must be a float number in the range [-1.0,1.0] that configures the blurring. A value included in [0.0,1.0] will blur the image whereas a value included in [-1.0,0.0] will sharpen the image. Default value is luma_strength.

alpha_threshold, at

Set the alpha threshold used as a coefficient to determine whether a pixel should be blurred or not. The option value must be an integer in the range [-30,30]. A value of 0 will filter all the image, a value included in [0,30] will filter flat areas and a value included in [-30,0] will filter edges. Default value is luma_threshold.

If a chroma or alpha option is not explicitly set, the corresponding luma value is set.

### 39.241 sobel# TOC

Apply sobel operator to input video stream.

The filter accepts the following option:

planes

Set which planes will be processed, unprocessed planes will be copied. By default value 0xf, all planes will be processed.

scale

Set value which will be multiplied with filtered result.

delta

Set value which will be added to filtered result.

#### 39.241.1 Commands# TOC

This filter supports the all above options as commands.

### 39.242 spp# TOC

Apply a simple postprocessing filter that compresses and decompresses the image at several (or - in the case of quality level 6 - all) shifts and average the results.

The filter accepts the following options:

quality

Set quality. This option defines the number of levels for averaging. It accepts an integer in the range 0-6. If set to 0, the filter will have no effect. A value of 6 means the higher quality. For each increment of that value the speed drops by a factor of approximately 2. Default value is 3.

qp

Force a constant quantization parameter. If not set, the filter will use the QP from the video stream (if available).

mode

Set thresholding mode. Available modes are:

‘hard’

Set hard thresholding (default).

‘soft’

Set soft thresholding (better de-ringing effect, but likely blurrier).

use_bframe_qp

Enable the use of the QP from the B-Frames if set to 1. Using this option may cause flicker since the B-Frames have often larger QP. Default is 0 (not enabled).

#### 39.242.1 Commands# TOC

This filter supports the following commands:

quality, level

Set quality level. The value max can be used to set the maximum level, currently 6.

### 39.243 sr# TOC

Scale the input by applying one of the super-resolution methods based on convolutional neural networks. Supported models:

- Super-Resolution Convolutional Neural Network model (SRCNN). See https://arxiv.org/abs/1501.00092.

- Efficient Sub-Pixel Convolutional Neural Network model (ESPCN). See https://arxiv.org/abs/1609.05158.

Training scripts as well as scripts for model file (.pb) saving can be found at https://github.com/XueweiMeng/sr/tree/sr_dnn_native. Original repository is at https://github.com/HighVoltageRocknRoll/sr.git.

The filter accepts the following options:

dnn_backend

Specify which DNN backend to use for model loading and execution. This option accepts the following values:

‘tensorflow’

TensorFlow backend. To enable this backend you need to install the TensorFlow for C library (see https://www.tensorflow.org/install/lang_c) and configure FFmpeg with --enable-libtensorflow

model

Set path to model file specifying network architecture and its parameters. Note that different backends use different file formats. TensorFlow, OpenVINO backend can load files for only its format.

scale_factor

Set scale factor for SRCNN model. Allowed values are 2, 3 and 4. Default value is 2. Scale factor is necessary for SRCNN model, because it accepts input upscaled using bicubic upscaling with proper scale factor.

To get full functionality (such as async execution), please use the dnn_processing filter.

### 39.244 sr_amf# TOC

Upscale (size increasing) for the input video using AMD Advanced Media Framework library for hardware acceleration. Use advanced algorithms for upscaling with higher output quality. Setting the output width and height works in the same way as for the scale filter.

The filter accepts the following options:

w

h

Set the output video dimension expression. Default value is the input dimension.

Allows for the same expressions as the scale filter.

algorithm

Sets the algorithm used for scaling:

bilinear

Bilinear

bicubic

Bicubic

sr1-0

Video SR1.0 This is a default value

point

Point AMF returns an unwritten surface for this algorithm when the format is nv12 or p010, so inputs in those formats are converted to a packed RGB format automatically. This is a driver bug rather than a documented restriction; the conversion can be dropped once a driver that scales nv12 and p010 correctly with point is in wide use.

sr1-1

Video SR1.1 This algorithm only supports packed RGB formats and requires a DirectX 11 or DirectX 12 device, so it is available on Windows only. Inputs in other formats such as nv12 or p010 are converted to a packed RGB format automatically. Note that the VideoSR algorithms (sr1-0 and sr1-1) do not preserve the alpha channel (it is left zeroed); drop it after the download, e.g. with hwdownload,format=rgba,format=rgb24, if an opaque result is required.

sharpness

Control hq scaler sharpening. The value is a float in the range of [0.0, 2.0]

format

Controls the output pixel format. By default, or if none is specified, the input pixel format is used.

The point and sr1-1 algorithms emit the packed RGB format the scaler receives, so for them this option must name one of rgba, bgra, x2bgr10le or rgbaf16le. A named format also decides what software input is converted to, and what a hardware surface in another format is converted to on the GPU. Without it, x2bgr10le is selected for p010 input and rgba for other non-RGB input, and the result is tagged as full range RGB. libswscale cannot convert other software formats to rgbaf16le; use software input already in that format or a hardware input for GPU conversion.

keep-ratio

Force the scaler to keep the aspect ratio of the input image when the output size has a different aspect ratio. Default value is false.

fill

Specifies whether the output image outside the region of interest, which does not fill the entire output surface should be filled with a solid color.

#### 39.244.1 Examples# TOC

- Upscale to 720p, keeping aspect ratio, and read the result back into system memory. The filter always outputs AMF surfaces, so a hwdownload is needed to feed a software encoder.

```
sr_amf=-2:720,hwdownload,format=nv12

```

- Upscale to 4K with algorithm video SR1.1.

```
sr_amf=4096:2160:algorithm=sr1-1

```

### 39.245 ssim# TOC

Obtain the SSIM (Structural SImilarity Metric) between two input videos.

This filter takes in input two input videos, the first input is considered the "main" source and is passed unchanged to the output. The second input is used as a "reference" video for computing the SSIM.

Both video inputs must have the same resolution and pixel format for this filter to work correctly. Also it assumes that both inputs have the same number of frames, which are compared one by one.

The filter stores the calculated SSIM of each frame.

The description of the accepted parameters follows.

stats_file, f

If specified the filter will use the named file to save the SSIM of each individual frame. When filename equals "-" the data is sent to standard output.

The file printed if stats_file is selected, contains a sequence of key/value pairs of the form key:value for each compared couple of frames.

A description of each shown parameter follows:

n

sequential number of the input frame, starting from 1

Y, U, V, R, G, B

SSIM of the compared frames for the component specified by the suffix.

All

SSIM of the compared frames for the whole frame.

dB

Same as above but in dB representation.

This filter also supports the framesync options.

#### 39.245.1 Examples# TOC

- For example:

```
movie=ref_movie.mpg, setpts=PTS-STARTPTS [main];
[main][ref] ssim="stats_file=stats.log" [out]

```

On this example the input file being processed is compared with the reference file ref_movie.mpg. The SSIM of each individual frame is stored in stats.log.

- Another example with both psnr and ssim at same time:

```
ffmpeg -i main.mpg -i ref.mpg -lavfi  "ssim;[0:v][1:v]psnr" -f null -

```

- Another example with different containers:

```
ffmpeg -i main.mpg -i ref.mkv -lavfi  "[0:v]settb=AVTB,setpts=PTS-STARTPTS[main];[1:v]settb=AVTB,setpts=PTS-STARTPTS[ref];[main][ref]ssim" -f null -

```

### 39.246 stereo3d# TOC

Convert between different stereoscopic image formats.

The filters accept the following options:

in

Set stereoscopic image format of input.

Available values for input image formats are:

‘sbsl’

side by side parallel (left eye left, right eye right)

‘sbsr’

side by side crosseye (right eye left, left eye right)

‘sbs2l’

side by side parallel with half width resolution (left eye left, right eye right)

‘sbs2r’

side by side crosseye with half width resolution (right eye left, left eye right)

‘abl’

‘tbl’

above-below (left eye above, right eye below)

‘abr’

‘tbr’

above-below (right eye above, left eye below)

‘ab2l’

‘tb2l’

above-below with half height resolution (left eye above, right eye below)

‘ab2r’

‘tb2r’

above-below with half height resolution (right eye above, left eye below)

‘al’

alternating frames (left eye first, right eye second)

‘ar’

alternating frames (right eye first, left eye second)

‘irl’

interleaved rows (left eye has top row, right eye starts on next row)

‘irr’

interleaved rows (right eye has top row, left eye starts on next row)

‘icl’

interleaved columns, left eye first

‘icr’

interleaved columns, right eye first

Default value is ‘sbsl’.

out

Set stereoscopic image format of output.

‘sbsl’

side by side parallel (left eye left, right eye right)

‘sbsr’

side by side crosseye (right eye left, left eye right)

‘sbs2l’

side by side parallel with half width resolution (left eye left, right eye right)

‘sbs2r’

side by side crosseye with half width resolution (right eye left, left eye right)

‘abl’

‘tbl’

above-below (left eye above, right eye below)

‘abr’

‘tbr’

above-below (right eye above, left eye below)

‘ab2l’

‘tb2l’

above-below with half height resolution (left eye above, right eye below)

‘ab2r’

‘tb2r’

above-below with half height resolution (right eye above, left eye below)

‘al’

alternating frames (left eye first, right eye second)

‘ar’

alternating frames (right eye first, left eye second)

‘irl’

interleaved rows (left eye has top row, right eye starts on next row)

‘irr’

interleaved rows (right eye has top row, left eye starts on next row)

‘arbg’

anaglyph red/blue gray (red filter on left eye, blue filter on right eye)

‘argg’

anaglyph red/green gray (red filter on left eye, green filter on right eye)

‘arcg’

anaglyph red/cyan gray (red filter on left eye, cyan filter on right eye)

‘arch’

anaglyph red/cyan half colored (red filter on left eye, cyan filter on right eye)

‘arcc’

anaglyph red/cyan color (red filter on left eye, cyan filter on right eye)

‘arcd’

anaglyph red/cyan color optimized with the least squares projection of dubois (red filter on left eye, cyan filter on right eye)

‘agmg’

anaglyph green/magenta gray (green filter on left eye, magenta filter on right eye)

‘agmh’

anaglyph green/magenta half colored (green filter on left eye, magenta filter on right eye)

‘agmc’

anaglyph green/magenta colored (green filter on left eye, magenta filter on right eye)

‘agmd’

anaglyph green/magenta color optimized with the least squares projection of dubois (green filter on left eye, magenta filter on right eye)

‘aybg’

anaglyph yellow/blue gray (yellow filter on left eye, blue filter on right eye)

‘aybh’

anaglyph yellow/blue half colored (yellow filter on left eye, blue filter on right eye)

‘aybc’

anaglyph yellow/blue colored (yellow filter on left eye, blue filter on right eye)

‘aybd’

anaglyph yellow/blue color optimized with the least squares projection of dubois (yellow filter on left eye, blue filter on right eye)

‘ml’

mono output (left eye only)

‘mr’

mono output (right eye only)

‘chl’

checkerboard, left eye first

‘chr’

checkerboard, right eye first

‘icl’

interleaved columns, left eye first

‘icr’

interleaved columns, right eye first

‘hdmi’

HDMI frame pack

Default value is ‘arcd’.

#### 39.246.1 Examples# TOC

- Convert input video from side by side parallel to anaglyph yellow/blue dubois:

```
stereo3d=sbsl:aybd

```

- Convert input video from above below (left eye above, right eye below) to side by side crosseye.

```
stereo3d=abl:sbsr

```

### 39.247 streamselect, astreamselect# TOC

Select video or audio streams.

The filter accepts the following options:

inputs

Set number of inputs. Default is 2.

map

Set input indexes to remap to outputs.

#### 39.247.1 Commands# TOC

The streamselect and astreamselect filter supports the following commands:

map

Set input indexes to remap to outputs.

#### 39.247.2 Examples# TOC

- Select first 5 seconds 1st stream and rest of time 2nd stream:

```
sendcmd='5.0 streamselect map 1',streamselect=inputs=2:map=0

```

- Same as above, but for audio:

```
asendcmd='5.0 astreamselect map 1',astreamselect=inputs=2:map=0

```

### 39.248 subtitles# TOC

Draw subtitles on top of input video using the libass library.

To enable compilation of this filter you need to configure FFmpeg with --enable-libass. This filter also requires a build with libavcodec and libavformat to convert the passed subtitles file to ASS (Advanced Substation Alpha) subtitles format.

The filter accepts the following options:

filename, f

Set the filename of the subtitle file to read. It must be specified.

original_size

Specify the size of the original video, the video for which the ASS file was composed. For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual. Due to a misdesign in ASS aspect ratio arithmetic, this is necessary to correctly scale the fonts if the aspect ratio has been changed.

fontsdir

Set a directory path containing fonts that can be used by the filter. These fonts will be used in addition to whatever the font provider uses.

alpha

Process alpha channel, by default alpha channel is untouched.

charenc

Set subtitles input character encoding. subtitles filter only. Only useful if not UTF-8.

stream_index, si

Set subtitles stream index. subtitles filter only.

force_style

Override default style or script info parameters of the subtitles. It accepts a string containing ASS style format KEY=VALUE couples separated by ",".

wrap_unicode

Break lines according to the Unicode Line Breaking Algorithm. Availability requires at least libass release 0.17.0 (or LIBASS_VERSION 0x01600010), and libass must have been built with libunibreak.

The option is enabled by default except for native ASS.

shaping

Set the shaping engine.

Available values are:

‘auto’

The default libass shaping engine, which is the best available.

‘simple’

Fast, font-agnostic shaper that can do only substitutions.

‘complex’

Slower shaper using OpenType for substitutions and positioning. Required for correct rendering of complex scripts such as Arabic, Hebrew, Devanagari and Thai. Requires libass to be built with HarfBuzz.

The default is auto.

If the first key is not specified, it is assumed that the first value specifies the filename.

For example, to render the file sub.srt on top of the input video, use the command:

```
subtitles=sub.srt

```

which is equivalent to:

```
subtitles=filename=sub.srt

```

To render the default subtitles stream from file video.mkv, use:

```
subtitles=video.mkv

```

To render the second subtitles stream from that file, use:

```
subtitles=video.mkv:si=1

```

To make the subtitles stream from sub.srt appear in 80% transparent blue DejaVu Serif, use:

```
subtitles=sub.srt:force_style='Fontname=DejaVu Serif,PrimaryColour=&HCCFF0000'

```

### 39.249 super2xsai# TOC

Scale the input by 2x and smooth using the Super2xSaI (Scale and Interpolate) pixel art scaling algorithm.

Useful for enlarging pixel art images without reducing sharpness.

### 39.250 swaprect# TOC

Swap two rectangular objects in video.

This filter accepts the following options:

w

Set object width.

h

Set object height.

x1

Set 1st rect x coordinate.

y1

Set 1st rect y coordinate.

x2

Set 2nd rect x coordinate.

y2

Set 2nd rect y coordinate.

All expressions are evaluated once for each frame.

The all options are expressions containing the following constants:

w

h

The input width and height.

a

same as w / h

sar

input sample aspect ratio

dar

input display aspect ratio, it is the same as (w / h) * sar

n

The number of the input frame, starting from 0.

t

The timestamp expressed in seconds. It’s NAN if the input timestamp is unknown.

pos

the position in the file of the input frame, NAN if unknown; deprecated, do not use

#### 39.250.1 Commands# TOC

This filter supports the all above options as commands.

### 39.251 swapuv# TOC

Swap U & V plane.

### 39.252 tblend# TOC

Blend successive video frames.

See blend

### 39.253 telecine# TOC

Apply telecine process to the video.

This filter accepts the following options:

first_field

‘top, t’

top field first

‘bottom, b’

bottom field first The default value is top.

pattern

A string of numbers representing the pulldown pattern you wish to apply. The default value is 23.

```
Some typical patterns:

NTSC output (30i):
27.5p: 32222
24p: 23 (classic)
24p: 2332 (preferred)
20p: 33
18p: 334
16p: 3444

PAL output (25i):
27.5p: 12222
24p: 222222222223 ("Euro pulldown")
16.67p: 33
16p: 33333334

```

### 39.254 thistogram# TOC

Compute and draw a color distribution histogram for the input video across time.

Unlike histogram video filter which only shows histogram of single input frame at certain time, this filter shows also past histograms of number of frames defined by width option.

The computed histogram is a representation of the color component distribution in an image.

The filter accepts the following options:

width, w

Set width of single color component output. Default value is 0. Value of 0 means width will be picked from input video. This also set number of passed histograms to keep. Allowed range is [0, 8192].

display_mode, d

Set display mode. It accepts the following values:

‘stack’

Per color component graphs are placed below each other.

‘parade’

Per color component graphs are placed side by side.

‘overlay’

Presents information identical to that in the parade, except that the graphs representing color components are superimposed directly over one another.

Default is stack.

levels_mode, m

Set mode. Can be either linear, or logarithmic. Default is linear.

components, c

Set what color components to display. Default is 7.

bgopacity, b

Set background opacity. Default is 0.9.

envelope, e

Show envelope. Default is disabled.

ecolor, ec

Set envelope color. Default is gold.

slide

Set slide mode.

Available values for slide is:

‘frame’

Draw new frame when right border is reached.

‘replace’

Replace old columns with new ones.

‘scroll’

Scroll from right to left.

‘rscroll’

Scroll from left to right.

‘picture’

Draw single picture.

Default is replace.

### 39.255 threshold# TOC

Apply threshold effect to video stream.

This filter needs four video streams to perform thresholding. First stream is stream we are filtering. Second stream is holding threshold values, third stream is holding min values, and last, fourth stream is holding max values.

The filter accepts the following option:

planes

Set which planes will be processed, unprocessed planes will be copied. By default value 0xf, all planes will be processed.

For example if first stream pixel’s component value is less then threshold value of pixel component from 2nd threshold stream, third stream value will picked, otherwise fourth stream pixel component value will be picked.

Using color source filter one can perform various types of thresholding:

#### 39.255.1 Commands# TOC

This filter supports the all options as commands.

#### 39.255.2 Examples# TOC

- Binary threshold, using gray color as threshold:

```
ffmpeg -i 320x240.avi -f lavfi -i color=gray -f lavfi -i color=black -f lavfi -i color=white -lavfi threshold output.avi

```

- Inverted binary threshold, using gray color as threshold:

```
ffmpeg -i 320x240.avi -f lavfi -i color=gray -f lavfi -i color=white -f lavfi -i color=black -lavfi threshold output.avi

```

- Truncate binary threshold, using gray color as threshold:

```
ffmpeg -i 320x240.avi -f lavfi -i color=gray -i 320x240.avi -f lavfi -i color=gray -lavfi threshold output.avi

```

- Threshold to zero, using gray color as threshold:

```
ffmpeg -i 320x240.avi -f lavfi -i color=gray -f lavfi -i color=white -i 320x240.avi -lavfi threshold output.avi

```

- Inverted threshold to zero, using gray color as threshold:

```
ffmpeg -i 320x240.avi -f lavfi -i color=gray -i 320x240.avi -f lavfi -i color=white -lavfi threshold output.avi

```

### 39.256 thumbnail# TOC

Select the most representative frame in a given sequence of consecutive frames.

The filter accepts the following options:

n

Set the frames batch size to analyze; in a set of n frames, the filter will pick one of them, and then handle the next batch of n frames until the end. Default is 100.

log

Set the log level to display picked frame stats. Default is info.

Since the filter keeps track of the whole frames sequence, a bigger n value will result in a higher memory usage, so a high value is not recommended.

#### 39.256.1 Examples# TOC

- Extract one picture each 50 frames:

```
thumbnail=50

```

- Complete example of a thumbnail creation with ffmpeg:

```
ffmpeg -i in.avi -vf thumbnail,scale=300:200 -frames:v 1 out.png

```

### 39.257 tile# TOC

Tile several successive frames together.

The untile filter can do the reverse.

The filter accepts the following options:

layout

Set the grid size in the form COLUMNSxROWS. Range is up to UINT_MAX cells. Default is 6x5.

nb_frames

Set the maximum number of frames to render in the given area. It must be less than or equal to wxh. The default value is 0, meaning all the area will be used.

margin

Set the outer border margin in pixels. Range is 0 to 1024. Default is 0.

padding

Set the inner border thickness (i.e. the number of pixels between frames). For more advanced padding options (such as having different values for the edges), refer to the pad video filter. Range is 0 to 1024. Default is 0.

color

Specify the color of the unused area. For the syntax of this option, check the "Color" section in the ffmpeg-utils manual. The default value of color is "black".

overlap

Set the number of frames to overlap when tiling several successive frames together. The value must be between 0 and nb_frames - 1. Default is 0.

init_padding

Set the number of frames to initially be empty before displaying first output frame. This controls how soon will one get first output frame. The value must be between 0 and nb_frames - 1. Default is 0.

#### 39.257.1 Examples# TOC

- Produce 8x8 PNG tiles of all keyframes (-skip_frame nokey) in a movie:

```
ffmpeg -skip_frame nokey -i file.avi -vf 'scale=128:72,tile=8x8' -an -fps_mode passthrough keyframes%03d.png

```

The -fps_mode passthrough is necessary to prevent ffmpeg from duplicating each output frame to accommodate the originally detected frame rate.

- Display 5 pictures in an area of 3x2 frames, with 7 pixels between them, and 2 pixels of initial margin, using mixed flat and named options:

```
tile=3x2:nb_frames=5:padding=7:margin=2

```

### 39.258 tiltandshift# TOC

Apply tilt-and-shift effect.

What happens when you invert time and space?

Normally a video is composed of several frames that represent a different instant of time and shows a scene that evolves in the space captured by the frame. This filter is the antipode of that concept, taking inspiration from tilt and shift photography.

A filtered frame contains the whole timeline of events composing the sequence, and this is obtained by placing a slice of pixels from each frame into a single one. However, since there are no infinite-width frames, this is done up the width of the input frame, and a video is recomposed by shifting away one column for each subsequent frame. In order to map space to time, the filter tilts each input frame as well, so that motion is preserved. This is accomplished by progressively selecting a different column from each input frame.

The end result is a sort of inverted parallax, so that far away objects move much faster that the ones in the front. The ideal conditions for this video effect are when there is either very little motion and the background is static, or when there is a lot of motion and a very wide depth of field (e.g. wide panorama, while moving on a train).

The filter accepts the following parameters:

tilt

Tilt video while shifting (default). When unset, video will be sliding a static image, composed of the first column of each frame.

start

What to do at the start of filtering (see below).

end

What to do at the end of filtering (see below).

hold

How many columns should pass through before start of filtering.

pad

How many columns should be inserted before end of filtering.

Normally the filter shifts and tilts from the very first frame, and stops when the last one is received. However, before filtering starts, normal video may be preserved, so that the effect is slowly shifted in its place. Similarly, the last video frame may be reconstructed at the end. Alternatively it is possible to just start and end with black.

‘none’

Filtering starts immediately and ends when the last frame is received.

‘frame’

The first frames or the very last frame are kept intact during processing.

‘black’

Black is padded at the beginning or at the end of filtering.

### 39.259 tinterlace# TOC

Perform various types of temporal field interlacing.

Frames are counted starting from 1, so the first input frame is considered odd.

The filter accepts the following options:

mode

Specify the mode of the interlacing. This option can also be specified as a value alone. See below for a list of values for this option.

Available values are:

‘merge, 0’

Move odd frames into the upper field, even into the lower field, generating a double height frame at half frame rate.

```
 ------> time
Input:
Frame 1         Frame 2         Frame 3         Frame 4

11111           22222           33333           44444
11111           22222           33333           44444
11111           22222           33333           44444
11111           22222           33333           44444

Output:
11111                           33333
22222                           44444
11111                           33333
22222                           44444
11111                           33333
22222                           44444
11111                           33333
22222                           44444

```

‘drop_even, 1’

Only output odd frames, even frames are dropped, generating a frame with unchanged height at half frame rate.

```
 ------> time
Input:
Frame 1         Frame 2         Frame 3         Frame 4

11111           22222           33333           44444
11111           22222           33333           44444
11111           22222           33333           44444
11111           22222           33333           44444

Output:
11111                           33333
11111                           33333
11111                           33333
11111                           33333

```

‘drop_odd, 2’

Only output even frames, odd frames are dropped, generating a frame with unchanged height at half frame rate.

```
 ------> time
Input:
Frame 1         Frame 2         Frame 3         Frame 4

11111           22222           33333           44444
11111           22222           33333           44444
11111           22222           33333           44444
11111           22222           33333           44444

Output:
                22222                           44444
                22222                           44444
                22222                           44444
                22222                           44444

```

‘pad, 3’

Expand each frame to full height, but pad alternate lines with black, generating a frame with double height at the same input frame rate.

```
 ------> time
Input:
Frame 1         Frame 2         Frame 3         Frame 4

11111           22222           33333           44444
11111           22222           33333           44444
11111           22222           33333           44444
11111           22222           33333           44444

Output:
11111           .....           33333           .....
.....           22222           .....           44444
11111           .....           33333           .....
.....           22222           .....           44444
11111           .....           33333           .....
.....           22222           .....           44444
11111           .....           33333           .....
.....           22222           .....           44444

```

‘interleave_top, 4’

Interleave the upper field from odd frames with the lower field from even frames, generating a frame with unchanged height at half frame rate.

```
 ------> time
Input:
Frame 1         Frame 2         Frame 3         Frame 4

11111<-         22222           33333<-         44444
11111           22222<-         33333           44444<-
11111<-         22222           33333<-         44444
11111           22222<-         33333           44444<-

Output:
11111                           33333
22222                           44444
11111                           33333
22222                           44444

```

‘interleave_bottom, 5’

Interleave the lower field from odd frames with the upper field from even frames, generating a frame with unchanged height at half frame rate.

```
 ------> time
Input:
Frame 1         Frame 2         Frame 3         Frame 4

11111           22222<-         33333           44444<-
11111<-         22222           33333<-         44444
11111           22222<-         33333           44444<-
11111<-         22222           33333<-         44444

Output:
22222                           44444
11111                           33333
22222                           44444
11111                           33333

```

‘interlacex2, 6’

Double frame rate with unchanged height. Frames are inserted each containing the second temporal field from the previous input frame and the first temporal field from the next input frame. This mode relies on the top_field_first flag. Useful for interlaced video displays with no field synchronisation.

```
 ------> time
Input:
Frame 1         Frame 2         Frame 3         Frame 4

11111           22222           33333           44444
 11111           22222           33333           44444
11111           22222           33333           44444
 11111           22222           33333           44444

Output:
11111   22222   22222   33333   33333   44444   44444
 11111   11111   22222   22222   33333   33333   44444
11111   22222   22222   33333   33333   44444   44444
 11111   11111   22222   22222   33333   33333   44444

```

‘mergex2, 7’

Move odd frames into the upper field, even into the lower field, generating a double height frame at same frame rate.

```
 ------> time
Input:
Frame 1         Frame 2         Frame 3         Frame 4

11111           22222           33333           44444
11111           22222           33333           44444
11111           22222           33333           44444
11111           22222           33333           44444

Output:
11111           33333           33333           55555
22222           22222           44444           44444
11111           33333           33333           55555
22222           22222           44444           44444
11111           33333           33333           55555
22222           22222           44444           44444
11111           33333           33333           55555
22222           22222           44444           44444

```

Numeric values are deprecated but are accepted for backward compatibility reasons.

Default mode is merge.

flags

Specify flags influencing the filter process.

Available value for flags is:

low_pass_filter, vlpf

Enable linear vertical low-pass filtering in the filter. Vertical low-pass filtering is required when creating an interlaced destination from a progressive source which contains high-frequency vertical detail. Filtering will reduce interlace ’twitter’ and Moire patterning.

complex_filter, cvlpf

Enable complex vertical low-pass filtering. This will slightly less reduce interlace ’twitter’ and Moire patterning but better retain detail and subjective sharpness impression.

bypass_il

Bypass already interlaced frames, only adjust the frame rate.

Vertical low-pass filtering and bypassing already interlaced frames can only be enabled for mode interleave_top and interleave_bottom.

### 39.260 tmedian# TOC

Pick median pixels from several successive input video frames.

The filter accepts the following options:

radius

Set radius of median filter. Default is 1. Allowed range is from 1 to 127.

planes

Set which planes to filter. Default value is 15, by which all planes are processed.

percentile

Set median percentile. Default value is 0.5. Default value of 0.5 will pick always median values, while 0 will pick minimum values, and 1 maximum values.

#### 39.260.1 Commands# TOC

This filter supports all above options as commands, excluding option radius.

### 39.261 tmidequalizer# TOC

Apply Temporal Midway Video Equalization effect.

Midway Video Equalization adjusts a sequence of video frames to have the same histograms, while maintaining their dynamics as much as possible. It’s useful for e.g. matching exposures from a video frames sequence.

This filter accepts the following option:

radius

Set filtering radius. Default is 5. Allowed range is from 1 to 127.

sigma

Set filtering sigma. Default is 0.5. This controls strength of filtering. Setting this option to 0 effectively does nothing.

planes

Set which planes to process. Default is 15, which is all available planes.

### 39.262 tmix# TOC

Mix successive video frames.

A description of the accepted options follows.

frames

The number of successive frames to mix. If unspecified, it defaults to 3.

weights

Specify weight of each input video frame. Each weight is separated by space. If number of weights is smaller than number of frames last specified weight will be used for all remaining unset weights.

scale

Specify scale, if it is set it will be multiplied with sum of each weight multiplied with pixel values to give final destination pixel value. By default scale is auto scaled to sum of weights.

planes

Set which planes to filter. Default is all. Allowed range is from 0 to 15.

#### 39.262.1 Examples# TOC

- Average 7 successive frames:

```
tmix=frames=7:weights="1 1 1 1 1 1 1"

```

- Apply simple temporal convolution:

```
tmix=frames=3:weights="-1 3 -1"

```

- Similar as above but only showing temporal differences:

```
tmix=frames=3:weights="-1 2 -1":scale=1

```

#### 39.262.2 Commands# TOC

This filter supports the following commands:

weights

scale

planes

Syntax is same as option with same name.

### 39.263 tonemap# TOC

Tone map colors from different dynamic ranges.

This filter expects data in single precision floating point, as it needs to operate on (and can output) out-of-range values. Another filter, such as zscale, is needed to convert the resulting frame to a usable format.

The tonemapping algorithms implemented only work on linear light, so input data should be linearized beforehand (and possibly correctly tagged).

```
ffmpeg -i INPUT -vf zscale=transfer=linear,tonemap=clip,zscale=transfer=bt709,format=yuv420p OUTPUT

```

#### 39.263.1 Options# TOC

The filter accepts the following options.

tonemap

Set the tone map algorithm to use.

Possible values are:

none

Do not apply any tone map, only desaturate overbright pixels.

clip

Hard-clip any out-of-range values. Use it for perfect color accuracy for in-range values, while distorting out-of-range values.

linear

Stretch the entire reference gamut to a linear multiple of the display.

gamma

Fit a logarithmic transfer between the tone curves.

reinhard

Preserve overall image brightness with a simple curve, using nonlinear contrast, which results in flattening details and degrading color accuracy.

hable

Preserve both dark and bright details better than reinhard, at the cost of slightly darkening everything. Use it when detail preservation is more important than color and brightness accuracy.

mobius

Smoothly map out-of-range values, while retaining contrast and colors for in-range material as much as possible. Use it when color accuracy is more important than detail preservation.

Default is none.

param

Tune the tone mapping algorithm.

This affects the following algorithms:

none

Ignored.

linear

Specifies the scale factor to use while stretching. Default to 1.0.

gamma

Specifies the exponent of the function. Default to 1.8.

clip

Specify an extra linear coefficient to multiply into the signal before clipping. Default to 1.0.

reinhard

Specify the local contrast coefficient at the display peak. Default to 0.5, which means that in-gamut values will be about half as bright as when clipping.

hable

Ignored.

mobius

Specify the transition point from linear to mobius transform. Every value below this point is guaranteed to be mapped 1:1. The higher the value, the more accurate the result will be, at the cost of losing bright details. Default to 0.3, which due to the steep initial slope still preserves in-range colors fairly accurately.

desat

Apply desaturation for highlights that exceed this level of brightness. The higher the parameter, the more color information will be preserved. This setting helps prevent unnaturally blown-out colors for super-highlights, by (smoothly) turning into white instead. This makes images feel more natural, at the cost of reducing information about out-of-range colors.

The default of 2.0 is somewhat conservative and will mostly just apply to skies or directly sunlit surfaces. A setting of 0.0 disables this option.

This option works only if the input frame has a supported color tag.

peak

Override signal/nominal/reference peak with this value. Useful when the embedded peak information in display metadata is not reliable or when tone mapping from a lower range to a higher range.

### 39.264 tpad# TOC

Temporarily pad video frames.

The filter accepts the following options:

start

Specify number of delay frames before input video stream. Default is 0.

stop

Specify number of padding frames after input video stream. Set to -1 to pad indefinitely. Default is 0.

start_mode

Set kind of frames added to beginning of stream. Can be either add or clone. With add frames of solid-color are added. With clone frames are clones of first frame. Default is add.

stop_mode

Set kind of frames added to end of stream. Can be either add or clone. With add frames of solid-color are added. With clone frames are clones of last frame. Default is add.

start_duration, stop_duration

Specify the duration of the start/stop delay. See the Time duration section in the ffmpeg-utils(1) manual for the accepted syntax. These options override start and stop. Default is 0.

color

Specify the color of the padded area. For the syntax of this option, check the "Color" section in the ffmpeg-utils manual.

The default value of color is "black".

### 39.265 transpose# TOC

Transpose rows with columns in the input video and optionally flip it.

It accepts the following parameters:

dir

Specify the transposition direction.

Can assume the following values:

‘0, 4, cclock_flip’

Rotate by 90 degrees counterclockwise and vertically flip (default), that is:

```
L.R     L.l
. . ->  . .
l.r     R.r

```

‘1, 5, clock’

Rotate by 90 degrees clockwise, that is:

```
L.R     l.L
. . ->  . .
l.r     r.R

```

‘2, 6, cclock’

Rotate by 90 degrees counterclockwise, that is:

```
L.R     R.r
. . ->  . .
l.r     L.l

```

‘3, 7, clock_flip’

Rotate by 90 degrees clockwise and vertically flip, that is:

```
L.R     r.R
. . ->  . .
l.r     l.L

```

For values between 4-7, the transposition is only done if the input video geometry is portrait and not landscape. These values are deprecated, the passthrough option should be used instead.

Numerical values are deprecated, and should be dropped in favor of symbolic constants.

passthrough

Do not apply the transposition if the input geometry matches the one specified by the specified value. It accepts the following values:

‘none’

Always apply transposition.

‘portrait’

Preserve portrait geometry (when height >= width).

‘landscape’

Preserve landscape geometry (when width >= height).

Default value is none.

For example to rotate by 90 degrees clockwise and preserve portrait layout:

```
transpose=dir=1:passthrough=portrait

```

The command above can also be specified as:

```
transpose=1:portrait

```

### 39.266 trim# TOC

Trim the input so that the output contains one continuous subpart of the input.

It accepts the following parameters:

start

Specify the time of the start of the kept section, i.e. the frame with the timestamp start will be the first frame in the output.

end

Specify the time of the first frame that will be dropped, i.e. the frame immediately preceding the one with the timestamp end will be the last frame in the output.

start_pts

This is the same as start, except this option sets the start timestamp in timebase units instead of seconds.

end_pts

This is the same as end, except this option sets the end timestamp in timebase units instead of seconds.

duration

The maximum duration of the output in seconds.

start_frame

The number of the first frame that should be passed to the output.

end_frame

The number of the first frame that should be dropped.

start, end, and duration are expressed as time duration specifications; see the Time duration section in the ffmpeg-utils(1) manual for the accepted syntax.

Note that the first two sets of the start/end options and the duration option look at the frame timestamp, while the _frame variants simply count the frames that pass through the filter. Also note that this filter does not modify the timestamps. If you wish for the output timestamps to start at zero, insert a setpts filter after the trim filter.

If multiple start or end options are set, this filter tries to be greedy and keep all the frames that match at least one of the specified constraints. To keep only the part that matches all the constraints at once, chain multiple trim filters.

The defaults are such that all the input is kept. So it is possible to set e.g. just the end values to keep everything before the specified time.

Examples:

- Drop everything except the second minute of input:

```
ffmpeg -i INPUT -vf trim=60:120

```

- Keep only the first second:

```
ffmpeg -i INPUT -vf trim=duration=1

```

### 39.267 unpremultiply# TOC

Apply alpha unpremultiply effect to input video stream using first plane of second stream as alpha.

Both streams must have same dimensions and same pixel format.

The filter accepts the following option:

planes

Set which planes will be processed, unprocessed planes will be copied. By default value 0xf, all planes will be processed.

If the format has 1 or 2 components, then luma is bit 0. If the format has 3 or 4 components: for RGB formats bit 0 is green, bit 1 is blue and bit 2 is red; for YUV formats bit 0 is luma, bit 1 is chroma-U and bit 2 is chroma-V. If present, the alpha channel is always the last bit.

inplace

Do not require 2nd input for processing, instead use alpha plane from input stream.

### 39.268 unsharp# TOC

Sharpen or blur the input video.

It accepts the following parameters:

luma_msize_x, lx

Set the luma matrix horizontal size. It must be an odd integer between 3 and 23. The default value is 5.

luma_msize_y, ly

Set the luma matrix vertical size. It must be an odd integer between 3 and 23. The default value is 5.

luma_amount, la

Set the luma effect strength. It must be a floating point number, reasonable values lay between -1.5 and 1.5.

Negative values will blur the input video, while positive values will sharpen it, a value of zero will disable the effect.

Default value is 1.0.

chroma_msize_x, cx

Set the chroma matrix horizontal size. It must be an odd integer between 3 and 23. The default value is 5.

chroma_msize_y, cy

Set the chroma matrix vertical size. It must be an odd integer between 3 and 23. The default value is 5.

chroma_amount, ca

Set the chroma effect strength. It must be a floating point number, reasonable values lay between -1.5 and 1.5.

Negative values will blur the input video, while positive values will sharpen it, a value of zero will disable the effect.

Default value is 0.0.

alpha_msize_x, ax

Set the alpha matrix horizontal size. It must be an odd integer between 3 and 23. The default value is 5.

alpha_msize_y, ay

Set the alpha matrix vertical size. It must be an odd integer between 3 and 23. The default value is 5.

alpha_amount, aa

Set the alpha effect strength. It must be a floating point number, reasonable values lay between -1.5 and 1.5.

Negative values will blur the input video, while positive values will sharpen it, a value of zero will disable the effect.

Default value is 0.0.

All parameters are optional and default to the equivalent of the string ’5:5:1.0:5:5:0.0’.

#### 39.268.1 Examples# TOC

- Apply strong luma sharpen effect:

```
unsharp=luma_msize_x=7:luma_msize_y=7:luma_amount=2.5

```

- Apply a strong blur of both luma and chroma parameters:

```
unsharp=7:7:-2:7:7:-2

```

### 39.269 untile# TOC

Decompose a video made of tiled images into the individual images.

The frame rate of the output video is the frame rate of the input video multiplied by the number of tiles.

This filter does the reverse of tile.

The filter accepts the following options:

layout

Set the grid size (i.e. the number of lines and columns). For the syntax of this option, check the "Video size" section in the ffmpeg-utils manual.

#### 39.269.1 Examples# TOC

- Produce a 1-second video from a still image file made of 25 frames stacked vertically, like an analogic film reel:

```
ffmpeg -r 1 -i image.jpg -vf untile=1x25 movie.mkv

```

### 39.270 uspp# TOC

Apply ultra slow/simple postprocessing filter that compresses and decompresses the image at several (or - in the case of quality level 8 - all) shifts and average the results.

The way this differs from the behavior of spp is that uspp actually encodes & decodes each case with libavcodec Snow, whereas spp uses a simplified intra only 8x8 DCT similar to MJPEG.

This filter is not available in ffmpeg versions between 5.0 and 6.0.

The filter accepts the following options:

quality

Set quality. This option defines the number of levels for averaging. It accepts an integer in the range 0-8. If set to 0, the filter will have no effect. A value of 8 means the higher quality. For each increment of that value the speed drops by a factor of approximately 2. Default value is 3.

qp

Force a constant quantization parameter. If not set, the filter will use the QP from the video stream (if available).

codec

Use specified codec instead of snow.

### 39.271 v360# TOC

Convert 360 videos between various formats.

The filter accepts the following options:

input

output

Set format of the input/output video.

Available formats:

‘e’

‘equirect’

Equirectangular projection.

‘c3x2’

‘c6x1’

‘c1x6’

Cubemap with 3x2/6x1/1x6 layout.

Format specific options:

in_pad

out_pad

Set padding proportion for the input/output cubemap. Values in decimals.

Example values:

‘0’

No padding.

‘0.01’

1% of face is padding. For example, with 1920x1280 resolution face size would be 640x640 and padding would be 3 pixels from each side. (640 * 0.01 = 6 pixels)

Default value is ‘0’. Maximum value is ‘0.1’.

fin_pad

fout_pad

Set fixed padding for the input/output cubemap. Values in pixels.

Default value is ‘0’. If greater than zero it overrides other padding options.

in_forder

out_forder

Set order of faces for the input/output cubemap. Choose one direction for each position.

Designation of directions:

‘r’

right

‘l’

left

‘u’

up

‘d’

down

‘f’

forward

‘b’

back

Default value is ‘rludfb’.

in_frot

out_frot

Set rotation of faces for the input/output cubemap. Choose one angle for each position.

Designation of angles:

‘0’

0 degrees clockwise

‘1’

90 degrees clockwise

‘2’

180 degrees clockwise

‘3’

270 degrees clockwise

Default value is ‘000000’.

‘eac’

Equi-Angular Cubemap.

‘flat’

‘gnomonic’

‘rectilinear’

Regular video.

Format specific options:

h_fov

v_fov

d_fov

Set output horizontal/vertical/diagonal field of view. Values in degrees.

If diagonal field of view is set it overrides horizontal and vertical field of view.

ih_fov

iv_fov

id_fov

Set input horizontal/vertical/diagonal field of view. Values in degrees.

If diagonal field of view is set it overrides horizontal and vertical field of view.

‘dfisheye’

Dual fisheye.

Format specific options:

h_fov

v_fov

d_fov

Set output horizontal/vertical/diagonal field of view. Values in degrees.

If diagonal field of view is set it overrides horizontal and vertical field of view.

ih_fov

iv_fov

id_fov

Set input horizontal/vertical/diagonal field of view. Values in degrees.

If diagonal field of view is set it overrides horizontal and vertical field of view.

‘barrel’

‘fb’

‘barrelsplit’

Facebook’s 360 formats.

‘sg’

Stereographic format.

Format specific options:

h_fov

v_fov

d_fov

Set output horizontal/vertical/diagonal field of view. Values in degrees.

If diagonal field of view is set it overrides horizontal and vertical field of view.

ih_fov

iv_fov

id_fov

Set input horizontal/vertical/diagonal field of view. Values in degrees.

If diagonal field of view is set it overrides horizontal and vertical field of view.

‘mercator’

Mercator format.

‘ball’

Ball format, gives significant distortion toward the back.

‘hammer’

Hammer-Aitoff map projection format.

‘sinusoidal’

Sinusoidal map projection format.

‘fisheye’

Fisheye projection.

Format specific options:

h_fov

v_fov

d_fov

Set output horizontal/vertical/diagonal field of view. Values in degrees.

If diagonal field of view is set it overrides horizontal and vertical field of view.

ih_fov

iv_fov

id_fov

Set input horizontal/vertical/diagonal field of view. Values in degrees.

If diagonal field of view is set it overrides horizontal and vertical field of view.

‘pannini’

Pannini projection.

Format specific options:

h_fov

Set output pannini parameter.

ih_fov

Set input pannini parameter.

‘cylindrical’

Cylindrical projection.

Format specific options:

h_fov

v_fov

d_fov

Set output horizontal/vertical/diagonal field of view. Values in degrees.

If diagonal field of view is set it overrides horizontal and vertical field of view.

ih_fov

iv_fov

id_fov

Set input horizontal/vertical/diagonal field of view. Values in degrees.

If diagonal field of view is set it overrides horizontal and vertical field of view.

‘perspective’

Perspective projection. (output only)

Format specific options:

v_fov

Set perspective parameter.

‘tetrahedron’

Tetrahedron projection.

‘tsp’

Truncated square pyramid projection.

‘he’

‘hequirect’

Half equirectangular projection.

‘equisolid’

Equisolid format.

Format specific options:

h_fov

v_fov

d_fov

Set output horizontal/vertical/diagonal field of view. Values in degrees.

If diagonal field of view is set it overrides horizontal and vertical field of view.

ih_fov

iv_fov

id_fov

Set input horizontal/vertical/diagonal field of view. Values in degrees.

If diagonal field of view is set it overrides horizontal and vertical field of view.

‘og’

Orthographic format.

Format specific options:

h_fov

v_fov

d_fov

Set output horizontal/vertical/diagonal field of view. Values in degrees.

If diagonal field of view is set it overrides horizontal and vertical field of view.

ih_fov

iv_fov

id_fov

Set input horizontal/vertical/diagonal field of view. Values in degrees.

If diagonal field of view is set it overrides horizontal and vertical field of view.

‘octahedron’

Octahedron projection.

‘cylindricalea’

Cylindrical Equal Area projection.

interp

Set interpolation method.
 Note: more complex interpolation methods require much more memory to run.

Available methods:

‘near’

‘nearest’

Nearest neighbour.

‘line’

‘linear’

Bilinear interpolation.

‘lagrange9’

Lagrange9 interpolation.

‘cube’

‘cubic’

Bicubic interpolation.

‘lanc’

‘lanczos’

Lanczos interpolation.

‘sp16’

‘spline16’

Spline16 interpolation.

‘gauss’

‘gaussian’

Gaussian interpolation.

‘mitchell’

Mitchell interpolation.

Default value is ‘line’.

w

h

Set the output video resolution.

Default resolution depends on formats.

in_stereo

out_stereo

Set the input/output stereo format.

‘2d’

2D mono

‘sbs’

Side by side

‘tb’

Top bottom

Default value is ‘2d’ for input and output format.

yaw

pitch

roll

Set rotation for the output video. Values in degrees.

rorder

Set rotation order for the output video. Choose one item for each position.

‘y, Y’

yaw

‘p, P’

pitch

‘r, R’

roll

Default value is ‘ypr’.

h_flip

v_flip

d_flip

Flip the output video horizontally(swaps left-right)/vertically(swaps up-down)/in-depth(swaps back-forward). Boolean values.

ih_flip

iv_flip

Set if input video is flipped horizontally/vertically. Boolean values.

in_trans

Set if input video is transposed. Boolean value, by default disabled.

out_trans

Set if output video needs to be transposed. Boolean value, by default disabled.

h_offset

v_offset

Set output horizontal/vertical off-axis offset. Default is set to 0. Allowed range is from -1 to 1.

alpha_mask

Build mask in alpha plane for all unmapped pixels by marking them fully transparent. Boolean value, by default disabled.

reset_rot

Reset rotation of output video. Boolean value, by default disabled.

#### 39.271.1 Examples# TOC

- Convert equirectangular video to cubemap with 3x2 layout and 1% padding using bicubic interpolation:

```
ffmpeg -i input.mkv -vf v360=e:c3x2:cubic:out_pad=0.01 output.mkv

```

- Extract back view of Equi-Angular Cubemap:

```
ffmpeg -i input.mkv -vf v360=eac:flat:yaw=180 output.mkv

```

- Convert transposed and horizontally flipped Equi-Angular Cubemap in side-by-side stereo format to equirectangular top-bottom stereo format:

```
v360=eac:equirect:in_stereo=sbs:in_trans=1:ih_flip=1:out_stereo=tb

```

#### 39.271.2 Commands# TOC

This filter supports subset of above options as commands.

### 39.272 vaguedenoiser# TOC

Apply a wavelet based denoiser.

It transforms each frame from the video input into the wavelet domain, using Cohen-Daubechies-Feauveau 9/7. Then it applies some filtering to the obtained coefficients. It does an inverse wavelet transform after. Due to wavelet properties, it should give a nice smoothed result, and reduced noise, without blurring picture features.

This filter accepts the following options:

threshold

The filtering strength. The higher, the more filtered the video will be. Hard thresholding can use a higher threshold than soft thresholding before the video looks overfiltered. Default value is 2.

method

The filtering method the filter will use.

It accepts the following values:

‘hard’

All values under the threshold will be zeroed.

‘soft’

All values under the threshold will be zeroed. All values above will be reduced by the threshold.

‘garrote’

Scales or nullifies coefficients - intermediary between (more) soft and (less) hard thresholding.

Default is garrote.

nsteps

Number of times, the wavelet will decompose the picture. Picture can’t be decomposed beyond a particular point (typically, 8 for a 640x480 frame - as 2^9 = 512 > 480). Valid values are integers between 1 and 32. Default value is 6.

percent

Partial of full denoising (limited coefficients shrinking), from 0 to 100. Default value is 85.

planes

A list of the planes to process. By default all planes are processed.

type

The threshold type the filter will use.

It accepts the following values:

‘universal’

Threshold used is same for all decompositions.

‘bayes’

Threshold used depends also on each decomposition coefficients.

Default is universal.

### 39.273 varblur# TOC

Apply variable blur filter by using 2nd video stream to set blur radius. The 2nd stream must have the same dimensions.

This filter accepts the following options:

min_r

Set min allowed radius. Allowed range is from 0 to 254. Default is 0.

max_r

Set max allowed radius. Allowed range is from 1 to 255. Default is 8.

planes

Set which planes to process. By default, all are used.

The varblur filter also supports the framesync options.

#### 39.273.1 Commands# TOC

This filter supports all the above options as commands.

### 39.274 vectorscope# TOC

Display 2 color component values in the two dimensional graph (which is called a vectorscope).

This filter accepts the following options:

mode, m

Set vectorscope mode.

It accepts the following values:

‘gray’

‘tint’

Gray values are displayed on graph, higher brightness means more pixels have same component color value on location in graph. This is the default mode.

‘color’

Gray values are displayed on graph. Surrounding pixels values which are not present in video frame are drawn in gradient of 2 color components which are set by option x and y. The 3rd color component is static.

‘color2’

Actual color components values present in video frame are displayed on graph.

‘color3’

Similar as color2 but higher frequency of same values x and y on graph increases value of another color component, which is luminance by default values of x and y.

‘color4’

Actual colors present in video frame are displayed on graph. If two different colors map to same position on graph then color with higher value of component not present in graph is picked.

‘color5’

Gray values are displayed on graph. Similar to color but with 3rd color component picked from radial gradient.

x

Set which color component will be represented on X-axis. Default is 1.

y

Set which color component will be represented on Y-axis. Default is 2.

intensity, i

Set intensity, used by modes: gray, color, color3 and color5 for increasing brightness of color component which represents frequency of (X, Y) location in graph.

envelope, e

‘none’

No envelope, this is default.

‘instant’

Instant envelope, even darkest single pixel will be clearly highlighted.

‘peak’

Hold maximum and minimum values presented in graph over time. This way you can still spot out of range values without constantly looking at vectorscope.

‘peak+instant’

Peak and instant envelope combined together.

graticule, g

Set what kind of graticule to draw.

‘none’

‘green’

‘color’

‘invert’

opacity, o

Set graticule opacity.

flags, f

Set graticule flags.

‘white’

Draw graticule for white point.

‘black’

Draw graticule for black point.

‘name’

Draw color points short names.

bgopacity, b

Set background opacity.

lthreshold, l

Set low threshold for color component not represented on X or Y axis. Values lower than this value will be ignored. Default is 0. Note this value is multiplied with actual max possible value one pixel component can have. So for 8-bit input and low threshold value of 0.1 actual threshold is 0.1 * 255 = 25.

hthreshold, h

Set high threshold for color component not represented on X or Y axis. Values higher than this value will be ignored. Default is 1. Note this value is multiplied with actual max possible value one pixel component can have. So for 8-bit input and high threshold value of 0.9 actual threshold is 0.9 * 255 = 230.

colorspace, c

Set what kind of colorspace to use when drawing graticule.

‘auto’

‘601’

‘709’

Default is auto.

tint0, t0

tint1, t1

Set color tint for gray/tint vectorscope mode. By default both options are zero. This means no tint, and output will remain gray.

### 39.275 vidstabdetect# TOC

Analyze video stabilization/deshaking. Perform pass 1 of 2, see vidstabtransform for pass 2.

This filter generates a file with relative translation and rotation transform information about subsequent frames, which is then used by the vidstabtransform filter.

To enable compilation of this filter you need to configure FFmpeg with --enable-libvidstab.

This filter accepts the following options:

result

Set the path to the file used to write the transforms information. Default value is transforms.trf.

shakiness

Set how shaky the video is and how quick the camera is. It accepts an integer in the range 1-10, a value of 1 means little shakiness, a value of 10 means strong shakiness. Default value is 5.

accuracy

Set the accuracy of the detection process. It must be a value in the range 1-15. A value of 1 means low accuracy, a value of 15 means high accuracy. Default value is 15.

stepsize

Set stepsize of the search process. The region around minimum is scanned with 1 pixel resolution. Default value is 6.

mincontrast

Set minimum contrast. Below this value a local measurement field is discarded. Must be a floating point value in the range 0-1. Default value is 0.3.

tripod

Set reference frame number for tripod mode.

If enabled, the motion of the frames is compared to a reference frame in the filtered stream, identified by the specified number. The idea is to compensate all movements in a more-or-less static scene and keep the camera view absolutely still.

If set to 0, it is disabled. The frames are counted starting from 1.

show

