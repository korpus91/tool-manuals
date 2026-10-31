Read a rawvideo with ffplay, assuming a pixel format of yuv420p, a video size of 1080x1920, has 8 bytes of padding in each line of Y plane, and 4 bytes of padding with UV plane,

```
ffplay -f rawvideo -pixel_format yuv420p -video_size 1080x1920 -stride 1088,544,544 input.raw

```

### 20.25 rcwt# TOC

RCWT (Raw Captions With Time) is a format native to ccextractor, a commonly used open source tool for processing 608/708 Closed Captions (CC) sources. For more information on the format, see (ffmpeg-formats)rcwtenc.

This demuxer implements the specification as of March 2024, which has been stable and unchanged since April 2014.

#### 20.25.1 Examples# TOC

- Render CC to ASS using the built-in decoder:

```
ffmpeg -i CC.rcwt.bin CC.ass

```

Note that if your output appears to be empty, you may have to manually set the decoder’s data_field option to pick the desired CC substream.

- Convert an RCWT backup to Scenarist (SCC) format:

```
ffmpeg -i CC.rcwt.bin -c:s copy CC.scc

```

Note that the SCC format does not support all of the possible CC extensions that can be stored in RCWT (such as EIA-708).

### 20.26 sbg# TOC

SBaGen script demuxer.

This demuxer reads the script language used by SBaGen http://uazu.net/sbagen/ to generate binaural beats sessions. A SBG script looks like that:

```
-SE
a: 300-2.5/3 440+4.5/0
b: 300-2.5/0 440+4.5/3
off: -
NOW      == a
+0:07:00 == b
+0:14:00 == a
+0:21:00 == b
+0:30:00    off

```

A SBG script can mix absolute and relative timestamps. If the script uses either only absolute timestamps (including the script start time) or only relative ones, then its layout is fixed, and the conversion is straightforward. On the other hand, if the script mixes both kind of timestamps, then the NOW reference for relative timestamps will be taken from the current time of day at the time the script is read, and the script layout will be frozen according to that reference. That means that if the script is directly played, the actual times will match the absolute timestamps up to the sound controller’s clock accuracy, but if the user somehow pauses the playback or seeks, all times will be shifted accordingly.

### 20.27 tedcaptions# TOC

JSON captions used for TED Talks.

TED does not provide links to the captions, but they can be guessed from the page. The file tools/bookmarklets.html from the FFmpeg source tree contains a bookmarklet to expose them.

This demuxer accepts the following option:

start_time

Set the start time of the TED talk, in milliseconds. The default is 15000 (15s). It is used to sync the captions with the downloadable videos, because they include a 15s intro.

Example: convert the captions to a format most players understand:

```
ffmpeg -i http://www.ted.com/talks/subtitles/id/1/lang/en talk1-en.srt

```

### 20.28 vapoursynth# TOC

Vapoursynth wrapper.

Due to security concerns, Vapoursynth scripts will not be autodetected so the input format has to be forced. For ff* CLI tools, add -f vapoursynth before the input -i yourscript.vpy.

This demuxer accepts the following option:

max_script_size

The demuxer buffers the entire script into memory. Adjust this value to set the maximum buffer size, which in turn, acts as a ceiling for the size of scripts that can be read. Default is 1 MiB.

### 20.29 w64# TOC

Sony Wave64 Audio demuxer.

This demuxer accepts the following options:

max_size

See the same option for the wav demuxer.

### 20.30 wav# TOC

RIFF Wave Audio demuxer.

This demuxer accepts the following options:

ignore_length bool

Ignore the size of the data chunk and keep reading until the end of the file if set. May be useful to read broken or partial files where the header was not properly updated, but will misinterpret files with non-audio chunks after the data chunk. Default is disabled.

max_size

Specify the maximum packet size in bytes for the demuxed packets. By default this is set to 0, which means that a sensible value is chosen based on the input format.

### 20.31 webp# TOC

Animated WebP demuxer.

It accepts the following options:

-min_delay int

Set the minimum valid delay between frames in milliseconds. Range is 0 to 60000. Default value is 10.

-max_webp_delay int

Set the maximum valid delay between frames in milliseconds. Range is 0 to 16777215. Default value is 16777215 (over four hours), the maximum value allowed by the specification.

-default_delay int

Set the default delay between frames in milliseconds. Range is 0 to 60000. Default value is 100.

-ignore_loop bool

WebP files can contain information to loop a certain number of times (or infinitely). If ignore_loop is set to true, then the loop setting from the input will be ignored and looping will not occur. If set to false, then looping will occur and will cycle the number of times according to the WebP. Default value is true.

usebgcolor bool

WebP files contain a background color hint in the ANIM chunk, but the WebP specification says that viewer applications are not required to use it. If usebgcolor is set to true, then the background color hint will be used, otherwise transparent black will be used for the background. Default value is false.

## 21 Muxers# TOC

Muxers are configured elements in FFmpeg which allow writing multimedia streams to a particular type of file.

When you configure your FFmpeg build, all the supported muxers are enabled by default. You can list all available muxers using the configure option --list-muxers.

You can disable all the muxers with the configure option --disable-muxers and selectively enable / disable single muxers with the options --enable-muxer=MUXER / --disable-muxer=MUXER.

The option -muxers of the ff* tools will display the list of enabled muxers. Use -formats to view a combined list of enabled demuxers and muxers.

A description of some of the currently available muxers follows.

### 21.1 Raw muxers# TOC

This section covers raw muxers. They accept a single stream matching the designated codec. They do not store timestamps or metadata. The recognized extension is the same as the muxer name unless indicated otherwise.

It comprises the following muxers. The media type and the eventual extensions used to automatically selects the muxer from the output extensions are also shown.

‘ac3 audio’

Dolby Digital, also known as AC-3.

‘adx audio’

CRI Middleware ADX audio.

This muxer will write out the total sample count near the start of the first packet when the output is seekable and the count can be stored in 32 bits.

‘aptx audio’

aptX (Audio Processing Technology for Bluetooth)

‘aptx_hd audio (aptxdh)’

aptX HD (Audio Processing Technology for Bluetooth) audio

‘avs2 video (avs, avs2)’

AVS2-P2 (Audio Video Standard - Second generation - Part 2) / IEEE 1857.4 video

‘avs3 video (avs3)’

AVS3-P2 (Audio Video Standard - Third generation - Part 2) / IEEE 1857.10 video

‘cavsvideo video (cavs)’

Chinese AVS (Audio Video Standard - First generation)

‘codec2raw audio’

Codec 2 audio.

No extension is registered so format name has to be supplied e.g. with the ffmpeg CLI tool -f codec2raw.

‘data any’

Generic data muxer.

This muxer accepts a single stream with any codec of any type. The input stream has to be selected using the -map option with the ffmpeg CLI tool.

No extension is registered so format name has to be supplied e.g. with the ffmpeg CLI tool -f data.

‘dfpwm audio (dfpwm)’

Raw DFPWM1a (Dynamic Filter Pulse With Modulation) audio muxer.

‘dirac video (drc, vc2)’

BBC Dirac video.

The Dirac Pro codec is a subset and is standardized as SMPTE VC-2.

‘dnxhd video (dnxhd, dnxhr)’

Avid DNxHD video.

It is standardized as SMPTE VC-3. Accepts DNxHR streams.

‘dts audio’

DTS Coherent Acoustics (DCA) audio

‘eac3 audio’

Dolby Digital Plus, also known as Enhanced AC-3

‘evc video (evc)’

MPEG-5 Essential Video Coding (EVC) / EVC / MPEG-5 Part 1 EVC video

‘g722 audio’

ITU-T G.722 audio

‘g723_1 audio (tco, rco)’

ITU-T G.723.1 audio

‘g726 audio’

ITU-T G.726 big-endian ("left-justified") audio.

No extension is registered so format name has to be supplied e.g. with the ffmpeg CLI tool -f g726.

‘g726le audio’

ITU-T G.726 little-endian ("right-justified") audio.

No extension is registered so format name has to be supplied e.g. with the ffmpeg CLI tool -f g726le.

‘gsm audio’

Global System for Mobile Communications audio

‘h261 video’

ITU-T H.261 video

‘h263 video’

ITU-T H.263 / H.263-1996, H.263+ / H.263-1998 / H.263 version 2 video

‘h264 video (h264, 264)’

ITU-T H.264 / MPEG-4 Part 10 AVC video. Bitstream shall be converted to Annex B syntax if it’s in length-prefixed mode.

‘hevc video (hevc, h265, 265)’

ITU-T H.265 / MPEG-H Part 2 HEVC video. Bitstream shall be converted to Annex B syntax if it’s in length-prefixed mode.

‘m4v video’

MPEG-4 Part 2 video

‘mjpeg video (mjpg, mjpeg)’

Motion JPEG video

‘mlp audio’

Meridian Lossless Packing, also known as Packed PCM

‘mp2 audio (mp2, m2a, mpa)’

MPEG-1 Audio Layer II audio

‘mpeg1video video (mpg, mpeg, m1v)’

MPEG-1 Part 2 video.

‘mpeg2video video (m2v)’

ITU-T H.262 / MPEG-2 Part 2 video

‘obu video’

AV1 low overhead Open Bitstream Units muxer.

Temporal delimiter OBUs will be inserted in all temporal units of the stream.

‘rawvideo video (yuv, rgb)’

Raw uncompressed video.

‘sbc audio (sbc, msbc)’

Bluetooth SIG low-complexity subband codec audio

‘truehd audio (thd)’

Dolby TrueHD audio

‘vc1 video’

SMPTE 421M / VC-1 video

#### 21.1.1 Examples# TOC

- Store raw video frames with the ‘rawvideo’ muxer using ffmpeg:

```
ffmpeg -f lavfi -i testsrc -t 10 -s hd1080p testsrc.yuv

```

Since the rawvideo muxer do not store the information related to size and format, this information must be provided when demuxing the file:

```
ffplay -video_size 1920x1080 -pixel_format rgb24 -f rawvideo testsrc.rgb

```

### 21.2 Raw PCM muxers# TOC

This section covers raw PCM (Pulse-Code Modulation) audio muxers.

They accept a single stream matching the designated codec. They do not store timestamps or metadata. The recognized extension is the same as the muxer name.

It comprises the following muxers. The optional additional extension used to automatically select the muxer from the output extension is also shown in parentheses.

‘alaw (al)’

PCM A-law

‘f32be’

PCM 32-bit floating-point big-endian

‘f32le’

PCM 32-bit floating-point little-endian

‘f64be’

PCM 64-bit floating-point big-endian

‘f64le’

PCM 64-bit floating-point little-endian

‘mulaw (ul)’

PCM mu-law

‘s16be’

PCM signed 16-bit big-endian

‘s16le’

PCM signed 16-bit little-endian

‘s24be’

PCM signed 24-bit big-endian

‘s24le’

PCM signed 24-bit little-endian

‘s32be’

PCM signed 32-bit big-endian

‘s32le’

PCM signed 32-bit little-endian

‘s8 (sb)’

PCM signed 8-bit

‘u16be’

PCM unsigned 16-bit big-endian

‘u16le’

PCM unsigned 16-bit little-endian

‘u24be’

PCM unsigned 24-bit big-endian

‘u24le’

PCM unsigned 24-bit little-endian

‘u32be’

PCM unsigned 32-bit big-endian

‘u32le’

PCM unsigned 32-bit little-endian

‘u8 (ub)’

PCM unsigned 8-bit

‘vidc’

PCM Archimedes VIDC

### 21.3 MPEG-1/MPEG-2 program stream muxers# TOC

This section covers formats belonging to the MPEG-1 and MPEG-2 Systems family.

The MPEG-1 Systems format (also known as ISO/IEEC 11172-1 or MPEG-1 program stream) has been adopted for the format of media track stored in VCD (Video Compact Disc).

The MPEG-2 Systems standard (also known as ISO/IEEC 13818-1) covers two containers formats, one known as transport stream and one known as program stream; only the latter is covered here.

The MPEG-2 program stream format (also known as VOB due to the corresponding file extension) is an extension of MPEG-1 program stream: in addition to support different codecs for the audio and video streams, it also stores subtitles and navigation metadata. MPEG-2 program stream has been adopted for storing media streams in SVCD and DVD storage devices.

This section comprises the following muxers.

‘mpeg (mpg,mpeg)’

MPEG-1 Systems / MPEG-1 program stream muxer.

‘vcd’

MPEG-1 Systems / MPEG-1 program stream (VCD) muxer.

This muxer can be used to generate tracks in the format accepted by the VCD (Video Compact Disc) storage devices.

It is the same as the ‘mpeg’ muxer with a few differences.

‘vob’

MPEG-2 program stream (VOB) muxer.

‘dvd’

MPEG-2 program stream (DVD VOB) muxer.

This muxer can be used to generate tracks in the format accepted by the DVD (Digital Versatile Disc) storage devices.

This is the same as the ‘vob’ muxer with a few differences.

‘svcd (vob)’

MPEG-2 program stream (SVCD VOB) muxer.

This muxer can be used to generate tracks in the format accepted by the SVCD (Super Video Compact Disc) storage devices.

This is the same as the ‘vob’ muxer with a few differences.

#### 21.3.1 Options# TOC

muxrate rate

Set user-defined mux rate expressed as a number of bits/s. If not specified the automatically computed mux rate is employed. Default value is 0.

preload delay

Set initial demux-decode delay in microseconds. Default value is 500000.

### 21.4 MOV/MPEG-4/ISOMBFF muxers# TOC

This section covers formats belonging to the QuickTime / MOV family, including the MPEG-4 Part 14 format and ISO base media file format (ISOBMFF). These formats share a common structure based on the ISO base media file format (ISOBMFF).

The MOV format was originally developed for use with Apple QuickTime. It was later used as the basis for the MPEG-4 Part 1 (later Part 14) format, also known as ISO/IEC 14496-1. That format was then generalized into ISOBMFF, also named MPEG-4 Part 12 format, ISO/IEC 14496-12, or ISO/IEC 15444-12.

It comprises the following muxers.

‘3gp’

Third Generation Partnership Project (3GPP) format for 3G UMTS multimedia services

‘3g2’

Third Generation Partnership Project 2 (3GP2 or 3GPP2) format for 3G CDMA2000 multimedia services, similar to ‘3gp’ with extensions and limitations

‘f4v’

Adobe Flash Video format

‘ipod’

MPEG-4 audio file format, as MOV/MP4 but limited to contain only audio streams, typically played with the Apple ipod device

‘ismv’

Microsoft IIS (Internet Information Services) Smooth Streaming Audio/Video (ISMV or ISMA) format. This is based on MPEG-4 Part 14 format with a few incompatible variants, used to stream media files for the Microsoft IIS server.

‘mov’

QuickTime player format identified by the .mov extension

‘mp4’

MP4 or MPEG-4 Part 14 format

‘psp’

PlayStation Portable MP4/MPEG-4 Part 14 format variant. This is based on MPEG-4 Part 14 format with a few incompatible variants, used to play files on PlayStation devices.

#### 21.4.1 Stereoscopic 3D# TOC

When the output stream has stereoscopic 3D side data (see the -stereo3d option), these muxers write:

- MP4: Google spatial-media st3d and Apple vexu can be written for supported metadata with -strict unofficial. Stricter compliance levels skip these boxes. Warnings are logged when stereoscopic or spherical side data is present, naming st3d or sv3d, respectively; there is no corresponding compliance warning for vexu. Monoscopic layouts do not produce an eyes box.

- MOV: Apple vexu eyes only. st3d is not written.

#### 21.4.2 Fragmentation# TOC

The ‘mov’, ‘mp4’, and ‘ismv’ muxers support fragmentation. Normally, a MOV/MP4 file has all the metadata about all packets stored in one location.

This data is usually written at the end of the file, but it can be moved to the start for better playback by adding +faststart to the -movflags, or using the qt-faststart tool).

A fragmented file consists of a number of fragments, where packets and metadata about these packets are stored together. Writing a fragmented file has the advantage that the file is decodable even if the writing is interrupted (while a normal MOV/MP4 is undecodable if it is not properly finished), and it requires less memory when writing very long files (since writing normal MOV/MP4 files stores info about every single packet in memory until the file is closed). The downside is that it is less compatible with other applications.

Fragmentation is enabled by setting one of the options that define how to cut the file into fragments:

frag_duration

frag_size

min_frag_duration

movflags +frag_keyframe

movflags +frag_custom

If more than one condition is specified, fragments are cut when one of the specified conditions is fulfilled. The exception to this is the option min_frag_duration, which has to be fulfilled for any of the other conditions to apply.

#### 21.4.3 Options# TOC

brand brand_string

Override major brand.

empty_hdlr_name bool

Enable to skip writing the name inside a hdlr box. Default is false.

encryption_key key

set the media encryption key in hexadecimal format

encryption_kid kid

set the media encryption key identifier in hexadecimal format

encryption_scheme scheme

configure the encryption scheme, allowed values are ‘none’, and ‘cenc-aes-ctr’

frag_duration duration

Create fragments that are duration microseconds long.

frag_interleave number

Interleave samples within fragments (max number of consecutive samples, lower is tighter interleaving, but with more overhead. It is set to 0 by default.

frag_size size

create fragments that contain up to size bytes of payload data

iods_audio_profile profile

specify iods number for the audio profile atom (from -1 to 255), default is -1

iods_video_profile profile

specify iods number for the video profile atom (from -1 to 255), default is -1

ism_lookahead num_entries

specify number of lookahead entries for ISM files (from 0 to 255), default is 0

min_frag_duration duration

do not create fragments that are shorter than duration microseconds long

moov_size bytes

Reserves space for the moov atom at the beginning of the file instead of placing the moov atom at the end. If the space reserved is insufficient, muxing will fail.

mov_gamma gamma

specify gamma value for gama atom (as a decimal number from 0 to 10), default is 0.0, must be set together with + movflags

movflags flags

Set various muxing switches. The following flags can be used:

‘cmaf’

write CMAF (Common Media Application Format) compatible fragmented MP4 output

‘dash’

write DASH (Dynamic Adaptive Streaming over HTTP) compatible fragmented MP4 output

‘default_base_moof’

Similarly to the ‘omit_tfhd_offset’ flag, this flag avoids writing the absolute base_data_offset field in tfhd atoms, but does so by using the new default-base-is-moof flag instead. This flag is new from 14496-12:2012. This may make the fragments easier to parse in certain circumstances (avoiding basing track fragment location calculations on the implicit end of the previous track fragment).

‘delay_moov’

delay writing the initial moov until the first fragment is cut, or until the first fragment flush

‘disable_chpl’

Disable Nero chapter markers (chpl atom). Normally, both Nero chapters and a QuickTime chapter track are written to the file. With this option set, only the QuickTime chapter track will be written. Nero chapters can cause failures when the file is reprocessed with certain tagging programs, like mp3Tag 2.61a and iTunes 11.3, most likely other versions are affected as well.

‘faststart’

Run a second pass moving the index (moov atom) to the beginning of the file. This operation can take a while, and will not work in various situations such as fragmented output, thus it is not enabled by default.

‘frag_custom’

Allow the caller to manually choose when to cut fragments, by calling av_write_frame(ctx, NULL) to write a fragment with the packets written so far. (This is only useful with other applications integrating libavformat, not from ffmpeg.)

‘frag_discont’

signal that the next fragment is discontinuous from earlier ones

‘frag_every_frame’

fragment at every frame

‘frag_keyframe’

start a new fragment at each video keyframe

‘global_sidx’

write a global sidx index at the start of the file

‘isml’

create a live smooth streaming feed (for pushing to a publishing point)

‘negative_cts_offsets’

Enables utilization of version 1 of the CTTS box, in which the CTS offsets can be negative. This enables the initial sample to have DTS/CTS of zero, and reduces the need for edit lists for some cases such as video tracks with B-frames. Additionally, eases conformance with the DASH-IF interoperability guidelines.

This option is implicitly set when writing ‘ismv’ (Smooth Streaming) files.

‘omit_tfhd_offset’

Do not write any absolute base_data_offset in tfhd atoms. This avoids tying fragments to absolute byte positions in the file/streams.

‘prefer_icc’

If writing colr atom prioritise usage of ICC profile if it exists in stream packet side data.

‘rtphint’

add RTP hinting tracks to the output file

‘separate_moof’

Write a separate moof (movie fragment) atom for each track. Normally, packets for all tracks are written in a moof atom (which is slightly more efficient), but with this option set, the muxer writes one moof/mdat pair for each track, making it easier to separate tracks.

‘skip_sidx’

Skip writing of sidx atom. When bitrate overhead due to sidx atom is high, this option could be used for cases where sidx atom is not mandatory. When the ‘global_sidx’ flag is enabled, this option is ignored.

‘skip_trailer’

skip writing the mfra/tfra/mfro trailer for fragmented files

‘use_metadata_tags’

use mdta atom for metadata

‘write_colr’

write colr atom even if the color info is unspecified. This flag is experimental, may be renamed or changed, do not use from scripts.

‘write_gama’

write deprecated gama atom

‘hybrid_fragmented’

For recoverability - write the output file as a fragmented file. This allows the intermediate file to be read while being written (in particular, if the writing process is aborted uncleanly). When writing is finished, the file is converted to a regular, non-fragmented file, which is more compatible and allows easier and quicker seeking.

If writing is aborted, the intermediate file can manually be remuxed to get a regular, non-fragmented file of what had been written into the unfinished file.

movie_timescale scale

Set the timescale written in the movie header box (mvhd). Range is 1 to INT_MAX. Default is 1000.

rtpflags flags

Add RTP hinting tracks to the output file.

The following flags can be used:

‘h264_mode0’

use mode 0 for H.264 in RTP

‘latm’

use MP4A-LATM packetization instead of MPEG4-GENERIC for AAC

‘rfc2190’

use RFC 2190 packetization instead of RFC 4629 for H.263

‘send_bye’

send RTCP BYE packets when finishing

‘skip_rtcp’

do not send RTCP sender reports

skip_iods bool

skip writing iods atom (default value is true)

use_editlist bool

use edit list (default value is auto)

use_stream_ids_as_track_ids bool

use stream ids as track ids (default value is false)

video_track_timescale scale

Set the timescale used for video tracks. Range is 0 to INT_MAX. If set to 0, the timescale is automatically set based on the native stream time base. Default is 0.

write_btrt bool

Force or disable writing bitrate box inside stsd box of a track. The box contains decoding buffer size (in bytes), maximum bitrate and average bitrate for the track. The box will be skipped if none of these values can be computed. Default is -1 or auto, which will write the box only in MP4 mode.

write_prft option

Write producer time reference box (PRFT) with a specified time source for the NTP field in the PRFT box. Set value as ‘wallclock’ to specify timesource as wallclock time and ‘pts’ to specify timesource as input packets’ PTS values.

write_tmcd bool

Specify on to force writing a timecode track, off to disable it and auto to write a timecode track only for mov and mp4 output (default).

Setting value to ‘pts’ is applicable only for a live encoding use case, where PTS values are set as as wallclock time at the source. For example, an encoding use case with decklink capture source where video_pts and audio_pts are set to ‘abs_wallclock’.

#### 21.4.4 Examples# TOC

- Push Smooth Streaming content in real time to a publishing point on IIS with the ‘ismv’ muxer using ffmpeg:

```
ffmpeg -re <normal input/transcoding options> -movflags isml+frag_keyframe -f ismv http://server/publishingpoint.isml/Streams(Encoder1)

```

### 21.5 a64# TOC

A64 Commodore 64 video muxer.

This muxer accepts a single a64_multi or a64_multi5 codec video stream.

### 21.6 ac4# TOC

Raw AC-4 audio muxer.

This muxer accepts a single ac4 audio stream.

#### 21.6.1 Options# TOC

write_crc bool

when enabled, write a CRC checksum for each packet to the output, default is false

### 21.7 adts# TOC

Audio Data Transport Stream muxer.

It accepts a single AAC stream.

#### 21.7.1 Options# TOC

write_id3v2 bool

Enable to write ID3v2.4 tags at the start of the stream. Default is disabled.

write_apetag bool

Enable to write APE tags at the end of the stream. Default is disabled.

write_mpeg2 bool

Enable to set MPEG version bit in the ADTS frame header to 1 which indicates MPEG-2. Default is 0, which indicates MPEG-4.

### 21.8 aea# TOC

MD STUDIO audio muxer.

This muxer accepts a single ATRAC1 audio stream with either one or two channels and a sample rate of 44100Hz.

As AEA supports storing the track title, this muxer will also write the title from stream’s metadata to the container.

### 21.9 aiff# TOC

Audio Interchange File Format muxer.

#### 21.9.1 Options# TOC

write_id3v2 bool

Enable ID3v2 tags writing when set to 1. Default is 0 (disabled).

id3v2_version bool

Select ID3v2 version to write. Currently only version 3 and 4 (aka. ID3v2.3 and ID3v2.4) are supported. The default is version 4.

### 21.10 alp# TOC

High Voltage Software’s Lego Racers game audio muxer.

It accepts a single ADPCM_IMA_ALP stream with no more than 2 channels and a sample rate not greater than 44100 Hz.

Extensions: tun, pcm

#### 21.10.1 Options# TOC

type type

Set file type.

type accepts the following values:

‘tun’

Set file type as music. Must have a sample rate of 22050 Hz.

‘pcm’

Set file type as sfx.

‘auto’

Set file type as per output file extension. .pcm results in type pcm else type tun is set. (default)

### 21.11 amr# TOC

3GPP AMR (Adaptive Multi-Rate) audio muxer.

It accepts a single audio stream containing an AMR NB stream.

### 21.12 amv# TOC

AMV (Actions Media Video) format muxer.

### 21.13 apm# TOC

Ubisoft Rayman 2 APM audio muxer.

It accepts a single ADPCM IMA APM audio stream.

### 21.14 apng# TOC

Animated Portable Network Graphics muxer.

It accepts a single APNG video stream.

#### 21.14.1 Options# TOC

final_delay delay

Force a delay expressed in seconds after the last frame of each repetition. Default value is 0.0.

plays repetitions

specify how many times to play the content, 0 causes an infinite loop, with 1 there is no loop

#### 21.14.2 Examples# TOC

- Use ffmpeg to generate an APNG output with 2 repetitions, and with a delay of half a second after the first repetition:

```
ffmpeg -i INPUT -final_delay 0.5 -plays 2 out.apng

```

### 21.15 argo_asf# TOC

Argonaut Games ASF audio muxer.

It accepts a single ADPCM audio stream.

#### 21.15.1 Options# TOC

version_major version

override file major version, specified as an integer, default value is 2

version_minor version

override file minor version, specified as an integer, default value is 1

name name

Embed file name into file, if not specified use the output file name. The name is truncated to 8 characters.

### 21.16 argo_cvg# TOC

Argonaut Games CVG audio muxer.

It accepts a single one-channel ADPCM 22050Hz audio stream.

The loop and reverb options set the corresponding flags in the header which can be later retrieved to process the audio stream accordingly.

#### 21.16.1 Options# TOC

skip_rate_check bool

skip sample rate check (default is false)

loop bool

set loop flag (default is false)

reverb boolean

set reverb flag (default is true)

### 21.17 asf, asf_stream# TOC

Advanced / Active Systems (or Streaming) Format audio muxer.

The ‘asf_stream’ variant should be selected for streaming.

Note that Windows Media Audio (wma) and Windows Media Video (wmv) use this muxer too.

#### 21.17.1 Options# TOC

packet_size size

Set the muxer packet size as a number of bytes. By tuning this setting you may reduce data fragmentation or muxer overhead depending on your source. Default value is 3200, minimum is 100, maximum is 64Ki.

### 21.18 ass# TOC

ASS/SSA (SubStation Alpha) subtitles muxer.

It accepts a single ASS subtitles stream.

#### 21.18.1 Options# TOC

ignore_readorder bool

Write dialogue events immediately, even if they are out-of-order, default is false, otherwise they are cached until the expected time event is found.

### 21.19 ast# TOC

AST (Audio Stream) muxer.

This format is used to play audio on some Nintendo Wii games.

It accepts a single audio stream.

The loopstart and loopend options can be used to define a section of the file to loop for players honoring such options.

#### 21.19.1 Options# TOC

loopstart start

Specify loop start position expressesd in milliseconds, from -1 to INT_MAX, in case -1 is set then no loop is specified (default -1) and the loopend value is ignored.

loopend end

Specify loop end position expressed in milliseconds, from 0 to INT_MAX, default is 0, in case 0 is set it assumes the total stream duration.

### 21.20 astc# TOC

ASTC (Adaptive Scalable Texture Compression) muxer.

This muxer accepts a single ‘libastcenc’ video stream and writes one image: the 16-byte .astc header, taken from the encoder’s extradata, followed by the raw ASTC bitstream. The block footprint and the image dimensions come from the same extradata, and a second packet is rejected.

Use the .ktx container for a texture that also needs its color space or row order recorded.

### 21.21 au# TOC

SUN AU audio muxer.

It accepts a single audio stream.

### 21.22 avi# TOC

Audio Video Interleaved muxer.

AVI is a proprietary format developed by Microsoft, and later formally specified through the Open DML specification.

Because of differences in players implementations, it might be required to set some options to make sure that the generated output can be correctly played by the target player.

#### 21.22.1 Options# TOC

flipped_raw_rgb bool

If set to true, store positive height for raw RGB bitmaps, which indicates bitmap is stored bottom-up. Note that this option does not flip the bitmap which has to be done manually beforehand, e.g. by using the ‘vflip’ filter. Default is false and indicates bitmap is stored top down.

reserve_index_space size

Reserve the specified amount of bytes for the OpenDML master index of each stream within the file header. By default additional master indexes are embedded within the data packets if there is no space left in the first master index and are linked together as a chain of indexes. This index structure can cause problems for some use cases, e.g. third-party software strictly relying on the OpenDML index specification or when file seeking is slow. Reserving enough index space in the file header avoids these problems.

The required index space depends on the output file size and should be about 16 bytes per gigabyte. When this option is omitted or set to zero the necessary index space is guessed.

Default value is 0.

write_channel_mask bool

Write the channel layout mask into the audio stream header.

This option is enabled by default. Disabling the channel mask can be useful in specific scenarios, e.g. when merging multiple audio streams into one for compatibility with software that only supports a single audio stream in AVI (see the "amerge" section in the ffmpeg-filters manual).

### 21.23 avif# TOC

AV1 (Alliance for Open Media Video codec 1) image format muxer.

This muxers stores images encoded using the AV1 codec.

It accepts one or two video streams. In case two video streams are provided, the second one shall contain a single plane storing the alpha mask.

In case more than one image is provided, the generated output is considered an animated AVIF and the number of loops can be specified with the loop option.

This is based on the specification by Alliance for Open Media at url https://aomediacodec.github.io/av1-avif.

#### 21.23.1 Options# TOC

loop count

number of times to loop an animated AVIF, 0 specify an infinite loop, default is 0

movie_timescale timescale

Set the timescale written in the movie header box (mvhd). Range is 1 to INT_MAX. Default is 1000.

### 21.24 avm2# TOC

ShockWave Flash (SWF) / ActionScript Virtual Machine 2 (AVM2) format muxer.

It accepts one audio stream, one video stream, or both.

### 21.25 bit# TOC

G.729 (.bit) file format muxer.

It accepts a single G.729 audio stream.

### 21.26 caf# TOC

Apple CAF (Core Audio Format) muxer.

It accepts a single audio stream.

### 21.27 codec2# TOC

Codec2 audio audio muxer.

It accepts a single codec2 audio stream.

### 21.28 chromaprint# TOC

Chromaprint fingerprinter muxers.

To enable compilation of this filter you need to configure FFmpeg with --enable-chromaprint.

This muxer feeds audio data to the Chromaprint library, which generates a fingerprint for the provided audio data. See: https://acoustid.org/chromaprint

It takes a single signed native-endian 16-bit raw audio stream of at most 2 channels.

#### 21.28.1 Options# TOC

algorithm version

Select version of algorithm to fingerprint with. Range is 0 to 4. Version 3 enables silence detection. Default is 1.

fp_format format

Format to output the fingerprint as. Accepts the following options:

‘base64’

Base64 compressed fingerprint (default)

‘compressed’

Binary compressed fingerprint

‘raw’

Binary raw fingerprint

silence_threshold threshold

Threshold for detecting silence. Range is from -1 to 32767, where -1 disables silence detection. Silence detection can only be used with version 3 of the algorithm.

Silence detection must be disabled for use with the AcoustID service. Default is -1.

### 21.29 crc# TOC

CRC (Cyclic Redundancy Check) muxer.

This muxer computes and prints the Adler-32 CRC of all the input audio and video frames. By default audio frames are converted to signed 16-bit raw audio and video frames to raw video before computing the CRC.

The output of the muxer consists of a single line of the form: CRC=0xCRC, where CRC is a hexadecimal number 0-padded to 8 digits containing the CRC for all the decoded input frames.

See also the framecrc muxer.

#### 21.29.1 Examples# TOC

- Use ffmpeg to compute the CRC of the input, and store it in the file out.crc:

```
ffmpeg -i INPUT -f crc out.crc

```

- Use ffmpeg to print the CRC to stdout with the command:

```
ffmpeg -i INPUT -f crc -

```

- You can select the output format of each frame with ffmpeg by specifying the audio and video codec and format. For example, to compute the CRC of the input audio converted to PCM unsigned 8-bit and the input video converted to MPEG-2 video, use the command:

```
ffmpeg -i INPUT -c:a pcm_u8 -c:v mpeg2video -f crc -

```

### 21.30 dash# TOC

Dynamic Adaptive Streaming over HTTP (DASH) muxer.

This muxer creates segments and manifest files according to the MPEG-DASH standard ISO/IEC 23009-1:2014 and following standard updates.

For more information see:

- ISO DASH Specification: http://standards.iso.org/ittf/PubliclyAvailableStandards/c065274_ISO_IEC_23009-1_2014.zip

- WebM DASH Specification: https://sites.google.com/a/webmproject.org/wiki/adaptive-streaming/webm-dash-specification

This muxer creates an MPD (Media Presentation Description) manifest file and segment files for each stream. Segment files are placed in the same directory of the MPD manifest file.

The segment filename might contain pre-defined identifiers used in the manifest SegmentTemplate section as defined in section 5.3.9.4.4 of the standard.

Available identifiers are $RepresentationID$, $Number$, $Bandwidth$, and $Time$. In addition to the standard identifiers, an ffmpeg-specific $ext$ identifier is also supported. When specified, ffmpeg will replace $ext$ in the file name with muxing format’s extensions such as mp4, webm etc.

#### 21.30.1 Options# TOC

adaptation_sets adaptation_sets

Assign streams to adaptation sets, specified in the MPD manifest AdaptationSets section.

An adaptation set contains a set of one or more streams accessed as a single subset, e.g. corresponding streams encoded at different size selectable by the user depending on the available bandwidth, or to different audio streams with a different language.

Each adaptation set is specified with the syntax:

```
id=index,streams=streams

```

where index must be a numerical index, and streams is a sequence of ,-separated stream indices. Multiple adaptation sets can be specified, separated by spaces.

To map all video (or audio) streams to an adaptation set, v (or a) can be used as stream identifier instead of IDs.

When no assignment is defined, this defaults to an adaptation set for each stream.

The following optional fields can also be specified:

descriptor

Define the descriptor as defined by ISO/IEC 23009-1:2014/Amd.2:2015.

For example:

```
<SupplementalProperty schemeIdUri=\"urn:mpeg:dash:srd:2014\" value=\"0,0,0,1,1,2,2\"/>

```

The descriptor string should be a self-closing XML tag.

frag_duration

Override the global fragment duration specified with the frag_duration option.

frag_type

Override the global fragment type specified with the frag_type option.

seg_duration

Override the global segment duration specified with the seg_duration option.

trick_id

Mark an adaptation set as containing streams meant to be used for Trick Mode for the referenced adaptation set.

A few examples of possible values for the adaptation_sets option follow:

```
id=0,seg_duration=2,frag_duration=1,frag_type=duration,streams=v id=1,seg_duration=2,frag_type=none,streams=a

```

```
id=0,seg_duration=2,frag_type=none,streams=0 id=1,seg_duration=10,frag_type=none,trick_id=0,streams=1

```

dash_segment_type type

Set DASH segment files type.

Possible values:

‘auto’

The dash segment files format will be selected based on the stream codec. This is the default mode.

‘mp4’

the dash segment files will be in ISOBMFF/MP4 format

‘webm’

the dash segment files will be in WebM format

extra_window_size size

Set the maximum number of segments kept outside of the manifest before removing from disk.

format_options options_list

Set container format (mp4/webm) options using a :-separated list of key=value parameters. Values containing : special characters must be escaped.

frag_duration duration

Set the length in seconds of fragments within segments, fractional value can also be set.

frag_type type

Set the type of interval for fragmentation.

Possible values:

‘auto’

set one fragment per segment

‘every_frame’

fragment at every frame

‘duration’

fragment at specific time intervals

‘pframes’

fragment at keyframes and following P-Frame reordering (Video only, experimental)

global_sidx bool

Write global SIDX atom. Applicable only for single file, mp4 output, non-streaming mode.

hls_master_name file_name

HLS master playlist name. Default is master.m3u8.

hls_playlist bool

Generate HLS playlist files. The master playlist is generated with filename specified by the hls_master_name option. One media playlist file is generated for each stream with filenames media_0.m3u8, media_1.m3u8, etc.

http_opts http_opts

Specify a list of :-separated key=value options to pass to the underlying HTTP protocol. Applicable only for HTTP output.

http_persistent bool

Use persistent HTTP connections. Applicable only for HTTP output.

http_user_agent user_agent

Override User-Agent field in HTTP header. Applicable only for HTTP output.

ignore_io_errors bool

Ignore IO errors during open and write. Useful for long-duration runs with network output. This is disabled by default.

index_correction bool

Enable or disable segment index correction logic. Applicable only when use_template is enabled and use_timeline is disabled. This is disabled by default.

When enabled, the logic monitors the flow of segment indexes. If a streams’s segment index value is not at the expected real time position, then the logic corrects that index value.

Typically this logic is needed in live streaming use cases. The network bandwidth fluctuations are common during long run streaming. Each fluctuation can cause the segment indexes fall behind the expected real time position.

init_seg_name init_name

DASH-templated name to use for the initialization segment. Default is init-stream$RepresentationID$.$ext$. $ext$ is replaced with the file name extension specific for the segment format.

ldash bool

Enable Low-latency Dash by constraining the presence and values of some elements. This is disabled by default.

lhls bool

Enable Low-latency HLS (LHLS). Add #EXT-X-PREFETCH tag with current segment’s URI. hls.js player folks are trying to standardize an open LHLS spec. The draft spec is available at https://github.com/video-dev/hlsjs-rfcs/blob/lhls-spec/proposals/0001-lhls.md.

This option tries to comply with the above open spec. It enables streaming and hls_playlist options automatically. This is an experimental feature.

Note: This is not Apple’s version LHLS. See https://datatracker.ietf.org/doc/html/draft-pantos-hls-rfc8216bis

master_m3u8_publish_rate segment_intervals_count

Publish master playlist repeatedly every after specified number of segment intervals.

max_playback_rate rate

Set the maximum playback rate indicated as appropriate for the purposes of automatically adjusting playback latency and buffer occupancy during normal playback by clients.

media_seg_name segment_name

DASH-templated name to use for the media segments. Default is chunk-stream$RepresentationID$-$Number%05d$.$ext$. $ext$ is replaced with the file name extension specific for the segment format.

method method

Use the given HTTP method to create output files. Generally set to PUT or POST.

min_playback_rate rate

Set the minimum playback rate indicated as appropriate for the purposes of automatically adjusting playback latency and buffer occupancy during normal playback by clients.

mpd_profile flags

Set one or more MPD manifest profiles.

Possible values:

‘dash’

MPEG-DASH ISO Base media file format live profile

‘dvb_dash’

DVB-DASH profile

Default value is dash.

remove_at_exit bool

Enable or disable removal of all segments when finished. This is disabled by default.

seg_duration duration

Set the segment length in seconds (fractional value can be set). The value is treated as average segment duration when the use_template option is enabled and the use_timeline option is disabled and as minimum segment duration for all the other use cases.

Default value is 5.

single_file bool

Enable or disable storing all segments in one file, accessed using byte ranges. This is disabled by default.

The name of the single file can be specified with the single_file_name option, if not specified assume the basename of the manifest file with the output format extension.

single_file_name file_name

DASH-templated name to use for the manifest baseURL element. Imply that the single_file option is set to true. In the template, $ext$ is replaced with the file name extension specific for the segment format.

availability_start_time_ms milliseconds

Set the MPD availabilityStartTime attribute as Unix epoch time in milliseconds. If set to 0, the wall clock is used when the first packet is written. This is useful for live outputs that need a stable availability start time across restarts.

streaming bool

Enable or disable chunk streaming mode of output. In chunk streaming mode, each frame will be a moof fragment which forms a chunk. This is disabled by default.

suggested_presentation_delay duration

Set the MPD suggestedPresentationDelay attribute. If set to 0, the last segment duration is used.

target_latency target_latency

Set an intended target latency in seconds for serving (fractional value can be set). Applicable only when the streaming and write_prft options are enabled. This is an informative fields clients can use to measure the latency of the service.

timeout timeout

Set timeout for socket I/O operations expressed in seconds (fractional value can be set). Applicable only for HTTP output.

update_period period

Set the MPD update period, for dynamic content. The unit is second. If set to 0, the period is automatically computed.

Default value is 0.

use_template bool

Enable or disable use of SegmentTemplate instead of SegmentList in the manifest. This is enabled by default.

use_timeline bool

Enable or disable use of SegmentTimeline within the SegmentTemplate manifest section. This is enabled by default.

utc_timing_url url

URL of the page that will return the UTC timestamp in ISO format, for example https://time.akamai.com/?iso

window_size size

Set the maximum number of segments kept in the manifest, discard the oldest one. This is useful for live streaming.

If the value is 0, all segments are kept in the manifest. Default value is 0.

write_prft write_prft

Write Producer Reference Time elements on supported streams. This also enables writing prft boxes in the underlying muxer. Applicable only when the utc_url option is enabled. It is set to auto by default, in which case the muxer will attempt to enable it only in modes that require it.

#### 21.30.2 Example# TOC

Generate a DASH output reading from an input source in realtime using ffmpeg.

Two multimedia streams are generated from the input file, both containing a video stream encoded through ‘libx264’, and an audio stream encoded with ‘libfdk_aac’. The first multimedia stream contains video with a bitrate of 800k and audio at the default rate, the second with video scaled to 320x170 pixels at 300k and audio resampled at 22005 Hz.

The window_size option keeps only the latest 5 segments with the default duration of 5 seconds.

```
ffmpeg -re -i <input> -map 0 -map 0 -c:a libfdk_aac -c:v libx264 \
-b:v:0 800k -profile:v:0 main \
-b:v:1 300k -s:v:1 320x170 -profile:v:1 baseline -ar:a:1 22050 \
-bf 1 -keyint_min 120 -g 120 -sc_threshold 0 -b_strategy 0 \
-use_timeline 1 -use_template 1 -window_size 5 \
-adaptation_sets "id=0,streams=v id=1,streams=a" \
-f dash /path/to/out.mpd

```

### 21.31 daud# TOC

D-Cinema audio muxer.

It accepts a single 6-channels audio stream resampled at 96000 Hz encoded with the ‘pcm_24daud’ codec.

#### 21.31.1 Example# TOC

Use ffmpeg to mux input audio to a ‘5.1’ channel layout resampled at 96000Hz:

```
ffmpeg -i INPUT -af aresample=96000,pan=5.1 slow.302

```

For ffmpeg versions before 7.0 you might have to use the ‘asetnsamples’ filter to limit the muxed packet size, because this format does not support muxing packets larger than 65535 bytes (3640 samples). For newer ffmpeg versions audio is automatically packetized to 36000 byte (2000 sample) packets.

### 21.32 dv# TOC

DV (Digital Video) muxer.

It accepts exactly one ‘dvvideo’ video stream and at most two ‘pcm_s16’ audio streams. More constraints are defined by the property of the video, which must correspond to a DV video supported profile, and on the framerate.

#### 21.32.1 Example# TOC

Use ffmpeg to convert the input:

```
ffmpeg -i INPUT -s:v 720x480 -pix_fmt yuv411p -r 29.97 -ac 2 -ar 48000 -y out.dv

```

### 21.33 ffmetadata# TOC

FFmpeg metadata muxer.

This muxer writes the streams metadata in the ‘ffmetadata’ format.

See the Metadata chapter for information about the format.

#### 21.33.1 Example# TOC

Use ffmpeg to extract metadata from an input file to a metadata.ffmeta file in ‘ffmetadata’ format:

```
ffmpeg -i INPUT -f ffmetadata metadata.ffmeta

```

### 21.34 fifo# TOC

FIFO (First-In First-Out) muxer.

The ‘fifo’ pseudo-muxer allows the separation of encoding and muxing by using a first-in-first-out queue and running the actual muxer in a separate thread.

This is especially useful in combination with the tee muxer and can be used to send data to several destinations with different reliability/writing speed/latency.

The target muxer is either selected from the output name or specified through the fifo_format option.

The behavior of the ‘fifo’ muxer if the queue fills up or if the output fails (e.g. if a packet cannot be written to the output) is selectable:

- Output can be transparently restarted with configurable delay between retries based on real time or time of the processed stream.

- Encoding can be blocked during temporary failure, or continue transparently dropping packets in case the FIFO queue fills up.

API users should be aware that callback functions (interrupt_callback, io_open and io_close) used within its AVFormatContext must be thread-safe.

#### 21.34.1 Options# TOC

attempt_recovery bool

If failure occurs, attempt to recover the output. This is especially useful when used with network output, since it makes it possible to restart streaming transparently. By default this option is set to false.

drop_pkts_on_overflow bool

If set to true, in case the fifo queue fills up, packets will be dropped rather than blocking the encoder. This makes it possible to continue streaming without delaying the input, at the cost of omitting part of the stream. By default this option is set to false, so in such cases the encoder will be blocked until the muxer processes some of the packets and none of them is lost.

fifo_format format_name

Specify the format name. Useful if it cannot be guessed from the output name suffix.

format_opts options

Specify format options for the underlying muxer. Muxer options can be specified as a list of key=value pairs separated by ’:’.

max_recovery_attempts count

Set maximum number of successive unsuccessful recovery attempts after which the output fails permanently. By default this option is set to 0 (unlimited).

queue_size size

Specify size of the queue as a number of packets. Default value is 60.

recover_any_error bool

If set to true, recovery will be attempted regardless of type of the error causing the failure. By default this option is set to false and in case of certain (usually permanent) errors the recovery is not attempted even when the attempt_recovery option is set to true.

recovery_wait_streamtime bool

If set to false, the real time is used when waiting for the recovery attempt (i.e. the recovery will be attempted after the time specified by the recovery_wait_time option).

If set to true, the time of the processed stream is taken into account instead (i.e. the recovery will be attempted after discarding the packets corresponding to the recovery_wait_time option).

By default this option is set to false.

recovery_wait_time duration

Specify waiting time in seconds before the next recovery attempt after previous unsuccessful recovery attempt. Default value is 5.

restart_with_keyframe bool

Specify whether to wait for the keyframe after recovering from queue overflow or failure. This option is set to false by default.

timeshift duration

Buffer the specified amount of packets and delay writing the output. Note that the value of the queue_size option must be big enough to store the packets for timeshift. At the end of the input the fifo buffer is flushed at realtime speed.

#### 21.34.2 Example# TOC

Use ffmpeg to stream to an RTMP server, continue processing the stream at real-time rate even in case of temporary failure (network outage) and attempt to recover streaming every second indefinitely:

```
ffmpeg -re -i ... -c:v libx264 -c:a aac -f fifo -fifo_format flv \
  -drop_pkts_on_overflow 1 -attempt_recovery 1 -recovery_wait_time 1 \
  -map 0:v -map 0:a rtmp://example.com/live/stream_name

```

### 21.35 film_cpk# TOC

Sega film (.cpk) muxer.

This format was used as internal format for several Sega games.

For more information regarding the Sega film file format, visit http://wiki.multimedia.cx/index.php?title=Sega_FILM.

It accepts at maximum one ‘cinepak’ or raw video stream, and at maximum one audio stream.

### 21.36 filmstrip# TOC

Adobe Filmstrip muxer.

This format is used by several Adobe tools to store a generated filmstrip export. It accepts a single raw video stream.

### 21.37 fits# TOC

Flexible Image Transport System (FITS) muxer.

This image format is used to store astronomical data.

For more information regarding the format, visit https://fits.gsfc.nasa.gov.

### 21.38 flac# TOC

Raw FLAC audio muxer.

This muxer accepts exactly one FLAC audio stream. Additionally, it is possible to add images with disposition ‘attached_pic’.

#### 21.38.1 Options# TOC

write_header bool

write the file header if set to true, default is true

#### 21.38.2 Example# TOC

Use ffmpeg to store the audio stream from an input file, together with several pictures used with ‘attached_pic’ disposition:

```
ffmpeg -i INPUT -i pic1.png -i pic2.jpg -map 0:a -map 1 -map 2 -disposition:v attached_pic OUTPUT

```

### 21.39 flv# TOC

Adobe Flash Video Format muxer.

#### 21.39.1 Options# TOC

flvflags flags

Possible values:

‘aac_seq_header_detect’

Place AAC sequence header based on audio stream data.

‘no_sequence_end’

Disable sequence end tag.

‘no_metadata’

Disable metadata tag.

‘no_duration_filesize’

Disable duration and filesize in metadata when they are equal to zero at the end of stream. (Be used to non-seekable living stream).

‘add_keyframe_index’

Used to facilitate seeking; particularly for HTTP pseudo streaming.

### 21.40 framecrc# TOC

Per-packet CRC (Cyclic Redundancy Check) testing format.

This muxer computes and prints the Adler-32 CRC for each audio and video packet. By default audio frames are converted to signed 16-bit raw audio and video frames to raw video before computing the CRC.

The output of the muxer consists of a line for each audio and video packet of the form:

```
stream_index, packet_dts, packet_pts, packet_duration, packet_size, 0xCRC

```

CRC is a hexadecimal number 0-padded to 8 digits containing the CRC of the packet.

#### 21.40.1 Examples# TOC

For example to compute the CRC of the audio and video frames in INPUT, converted to raw audio and video packets, and store it in the file out.crc:

```
ffmpeg -i INPUT -f framecrc out.crc

```

To print the information to stdout, use the command:

```
ffmpeg -i INPUT -f framecrc -

```

With ffmpeg, you can select the output format to which the audio and video frames are encoded before computing the CRC for each packet by specifying the audio and video codec. For example, to compute the CRC of each decoded input audio frame converted to PCM unsigned 8-bit and of each decoded input video frame converted to MPEG-2 video, use the command:

```
ffmpeg -i INPUT -c:a pcm_u8 -c:v mpeg2video -f framecrc -

```

See also the crc muxer.

### 21.41 framehash# TOC

Per-packet hash testing format.

This muxer computes and prints a cryptographic hash for each audio and video packet. This can be used for packet-by-packet equality checks without having to individually do a binary comparison on each.

By default audio frames are converted to signed 16-bit raw audio and video frames to raw video before computing the hash, but the output of explicit conversions to other codecs can also be used. It uses the SHA-256 cryptographic hash function by default, but supports several other algorithms.

The output of the muxer consists of a line for each audio and video packet of the form:

```
stream_index, packet_dts, packet_pts, packet_duration, packet_size, hash

```

hash is a hexadecimal number representing the computed hash for the packet.

hash algorithm

Use the cryptographic hash function specified by the string algorithm. Supported values include MD5, murmur3, RIPEMD128, RIPEMD160, RIPEMD256, RIPEMD320, SHA160, SHA224, SHA256 (default), SHA512/224, SHA512/256, SHA384, SHA512, CRC32 and adler32.

#### 21.41.1 Examples# TOC

To compute the SHA-256 hash of the audio and video frames in INPUT, converted to raw audio and video packets, and store it in the file out.sha256:

```
ffmpeg -i INPUT -f framehash out.sha256

```

To print the information to stdout, using the MD5 hash function, use the command:

```
ffmpeg -i INPUT -f framehash -hash md5 -

```

See also the hash muxer.

### 21.42 framemd5# TOC

Per-packet MD5 testing format.

This is a variant of the framehash muxer. Unlike that muxer, it defaults to using the MD5 hash function.

#### 21.42.1 Examples# TOC

To compute the MD5 hash of the audio and video frames in INPUT, converted to raw audio and video packets, and store it in the file out.md5:

```
ffmpeg -i INPUT -f framemd5 out.md5

```

To print the information to stdout, use the command:

```
ffmpeg -i INPUT -f framemd5 -

```

See also the framehash and md5 muxers.

### 21.43 gif# TOC

Animated GIF muxer.

Note that the GIF format has a very large time base: the delay between two frames can therefore not be smaller than one centisecond.

#### 21.43.1 Options# TOC

loop bool

Set the number of times to loop the output. Use -1 for no loop, 0 for looping indefinitely (default).

final_delay delay

Force the delay (expressed in centiseconds) after the last frame. Each frame ends with a delay until the next frame. The default is -1, which is a special value to tell the muxer to reuse the previous delay. In case of a loop, you might want to customize this value to mark a pause for instance.

#### 21.43.2 Example# TOC

Encode a gif looping 10 times, with a 5 seconds delay between the loops:

```
ffmpeg -i INPUT -loop 10 -final_delay 500 out.gif

```

Note 1: if you wish to extract the frames into separate GIF files, you need to force the image2 muxer:

```
ffmpeg -i INPUT -c:v gif -f image2 "out%d.gif"

```

### 21.44 gxf# TOC

General eXchange Format (GXF) muxer.

GXF was developed by Grass Valley Group, then standardized by SMPTE as SMPTE 360M and was extended in SMPTE RDD 14-2007 to include high-definition video resolutions.

It accepts at most one video stream with codec ‘mjpeg’, or ‘mpeg1video’, or ‘mpeg2video’, or ‘dvvideo’ with resolution ‘512x480’ or ‘608x576’, and several audio streams with rate 48000Hz and codec ‘pcm16_le’.

### 21.45 hash# TOC

Hash testing format.

This muxer computes and prints a cryptographic hash of all the input audio and video frames. This can be used for equality checks without having to do a complete binary comparison.

By default audio frames are converted to signed 16-bit raw audio and video frames to raw video before computing the hash, but the output of explicit conversions to other codecs can also be used. Timestamps are ignored. It uses the SHA-256 cryptographic hash function by default, but supports several other algorithms.

The output of the muxer consists of a single line of the form: algo=hash, where algo is a short string representing the hash function used, and hash is a hexadecimal number representing the computed hash.

hash algorithm

Use the cryptographic hash function specified by the string algorithm. Supported values include MD5, murmur3, RIPEMD128, RIPEMD160, RIPEMD256, RIPEMD320, SHA160, SHA224, SHA256 (default), SHA512/224, SHA512/256, SHA384, SHA512, CRC32 and adler32.

#### 21.45.1 Examples# TOC

To compute the SHA-256 hash of the input converted to raw audio and video, and store it in the file out.sha256:

```
ffmpeg -i INPUT -f hash out.sha256

```

To print an MD5 hash to stdout use the command:

```
ffmpeg -i INPUT -f hash -hash md5 -

```

See also the framehash muxer.

### 21.46 hds# TOC

HTTP Dynamic Streaming (HDS) muxer.

HTTP dynamic streaming, or HDS, is an adaptive bitrate streaming method developed by Adobe. HDS delivers MP4 video content over HTTP connections. HDS can be used for on-demand streaming or live streaming.

This muxer creates an .f4m (Adobe Flash Media Manifest File) manifest, an .abst (Adobe Bootstrap File) for each stream, and segment files in a directory specified as the output.

These needs to be accessed by an HDS player through HTTPS for it to be able to perform playback on the generated stream.

#### 21.46.1 Options# TOC

extra_window_size int

number of fragments kept outside of the manifest before removing from disk

min_frag_duration microseconds

minimum fragment duration (in microseconds), default value is 1 second (10000000)

remove_at_exit bool

remove all fragments when finished when set to true

window_size int

number of fragments kept in the manifest, if set to a value different from 0. By default all segments are kept in the output directory.

#### 21.46.2 Example# TOC

Use ffmpeg to generate HDS files to the output.hds directory in real-time rate:

```
ffmpeg -re -i INPUT -f hds -b:v 200k output.hds

```

### 21.47 hls# TOC

Apple HTTP Live Streaming muxer that segments MPEG-TS according to the HTTP Live Streaming (HLS) specification.

It creates a playlist file, and one or more segment files. The output filename specifies the playlist filename.

By default, the muxer creates a file for each segment produced. These files have the same name as the playlist, followed by a sequential number and a .ts extension.

Make sure to require a closed GOP when encoding and to set the GOP size to fit your segment time constraint.

For example, to convert an input file with ffmpeg:

```
ffmpeg -i in.mkv -c:v h264 -flags +cgop -g 30 -hls_time 1 out.m3u8

```

This example will produce the playlist, out.m3u8, and segment files: out0.ts, out1.ts, out2.ts, etc.

See also the segment muxer, which provides a more generic and flexible implementation of a segmenter, and can be used to perform HLS segmentation.

#### 21.47.1 Options# TOC

hls_init_time duration

Set the initial target segment length. Default value is 0.

duration must be a time duration specification, see the Time duration section in the ffmpeg-utils(1) manual.

Segment will be cut on the next key frame after this time has passed on the first m3u8 list. After the initial playlist is filled, ffmpeg will cut segments at duration equal to hls_time.

hls_time duration

Set the target segment length. Default value is 2.

duration must be a time duration specification, see the Time duration section in the ffmpeg-utils(1) manual. Segment will be cut on the next key frame after this time has passed.

hls_list_size size

Set the maximum number of playlist entries. If set to 0 the list file will contain all the segments. Default value is 5.

hls_delete_threshold size

Set the number of unreferenced segments to keep on disk before hls_flags delete_segments deletes them. Increase this to allow continue clients to download segments which were recently referenced in the playlist. Default value is 1, meaning segments older than hls_list_size+1 will be deleted.

hls_start_number_source source

Start the playlist sequence number (#EXT-X-MEDIA-SEQUENCE) according to the specified source. Unless hls_flags single_file is set, it also specifies source of starting sequence numbers of segment and subtitle filenames. In any case, if hls_flags append_list is set and read playlist sequence number is greater than the specified start sequence number, then that value will be used as start value.

It accepts the following values:

generic (default)

Set the start numbers according to the start_number option value.

epoch

Set the start number as the seconds since epoch (1970-01-01 00:00:00).

epoch_us

Set the start number as the microseconds since epoch (1970-01-01 00:00:00).

datetime

Set the start number based on the current date/time as YYYYmmddHHMMSS. e.g. 20161231235759.

start_number number

Start the playlist sequence number (#EXT-X-MEDIA-SEQUENCE) from the specified number when hls_start_number_source value is generic. (This is the default case.) Unless hls_flags single_file is set, it also specifies starting sequence numbers of segment and subtitle filenames. Default value is 0.

hls_allow_cache bool

Explicitly set whether the client MAY (1) or MUST NOT (0) cache media segments.

hls_base_url baseurl

Append baseurl to every entry in the playlist. Useful to generate playlists with absolute paths.

Note that the playlist sequence number must be unique for each segment and it is not to be confused with the segment filename sequence number which can be cyclic, for example if the wrap option is specified.

hls_segment_filename filename

Set the segment filename. Unless the hls_flags option is set with ‘single_file’, filename is used as a string format with the segment number appended.

For example:

```
ffmpeg -i in.nut -hls_segment_filename 'file%03d.ts' out.m3u8

```

will produce the playlist, out.m3u8, and segment files: file000.ts, file001.ts, file002.ts, etc.

filename may contain a full path or relative path specification, but only the file name part without any path will be contained in the m3u8 segment list. Should a relative path be specified, the path of the created segment files will be relative to the current working directory. When strftime_mkdir is set, the whole expanded value of filename will be written into the m3u8 segment list.

When var_stream_map is set with two or more variant streams, the filename pattern must contain the string "%v", and this string will be expanded to the position of variant stream index in the generated segment file names.

For example:

```
ffmpeg -i in.ts -b:v:0 1000k -b:v:1 256k -b:a:0 64k -b:a:1 32k \
  -map 0:v -map 0:a -map 0:v -map 0:a -f hls -var_stream_map "v:0,a:0 v:1,a:1" \
  -hls_segment_filename 'file_%v_%03d.ts' out_%v.m3u8

```

will produce the playlists segment file sets: file_0_000.ts, file_0_001.ts, file_0_002.ts, etc. and file_1_000.ts, file_1_001.ts, file_1_002.ts, etc.

The string "%v" may be present in the filename or in the last directory name containing the file, but only in one of them. (Additionally, %v may appear multiple times in the last sub-directory or filename.) If the string %v is present in the directory name, then sub-directories are created after expanding the directory name pattern. This enables creation of segments corresponding to different variant streams in subdirectories.

For example:

```
ffmpeg -i in.ts -b:v:0 1000k -b:v:1 256k -b:a:0 64k -b:a:1 32k \
  -map 0:v -map 0:a -map 0:v -map 0:a -f hls -var_stream_map "v:0,a:0 v:1,a:1" \
  -hls_segment_filename 'vs%v/file_%03d.ts' vs%v/out.m3u8

```

will produce the playlists segment file sets: vs0/file_000.ts, vs0/file_001.ts, vs0/file_002.ts, etc. and vs1/file_000.ts, vs1/file_001.ts, vs1/file_002.ts, etc.

strftime bool

Use strftime() on filename to expand the segment filename with localtime. The segment number is also available in this mode, but to use it, you need to set ‘second_level_segment_index’ in the hls_flag and %%d will be the specifier.

For example:

```
ffmpeg -i in.nut -strftime 1 -hls_segment_filename 'file-%Y%m%d-%s.ts' out.m3u8

```

will produce the playlist, out.m3u8, and segment files: file-20160215-1455569023.ts, file-20160215-1455569024.ts, etc. Note: On some systems/environments, the %s specifier is not available. See strftime() documentation.

For example:

```
ffmpeg -i in.nut -strftime 1 -hls_flags second_level_segment_index -hls_segment_filename 'file-%Y%m%d-%%04d.ts' out.m3u8

```

will produce the playlist, out.m3u8, and segment files: file-20160215-0001.ts, file-20160215-0002.ts, etc.

strftime_mkdir bool

Used together with strftime, it will create all subdirectories which are present in the expanded values of option hls_segment_filename.

For example:

```
ffmpeg -i in.nut -strftime 1 -strftime_mkdir 1 -hls_segment_filename '%Y%m%d/file-%Y%m%d-%s.ts' out.m3u8

```

will create a directory 201560215 (if it does not exist), and then produce the playlist, out.m3u8, and segment files: 20160215/file-20160215-1455569023.ts, 20160215/file-20160215-1455569024.ts, etc.

For example:

```
ffmpeg -i in.nut -strftime 1 -strftime_mkdir 1 -hls_segment_filename '%Y/%m/%d/file-%Y%m%d-%s.ts' out.m3u8

```

will create a directory hierarchy 2016/02/15 (if any of them do not exist), and then produce the playlist, out.m3u8, and segment files: 2016/02/15/file-20160215-1455569023.ts, 2016/02/15/file-20160215-1455569024.ts, etc.

hls_segment_options options_list

Set output format options using a :-separated list of key=value parameters. Values containing : special characters must be escaped.

hls_key_info_file key_info_file

Use the information in key_info_file for segment encryption. The first line of key_info_file specifies the key URI written to the playlist. The key URL is used to access the encryption key during playback. The second line specifies the path to the key file used to obtain the key during the encryption process. The key file is read as a single packed array of 16 octets in binary format. The optional third line specifies the initialization vector (IV) as a hexadecimal string to be used instead of the segment sequence number (default) for encryption. Changes to key_info_file will result in segment encryption with the new key/IV and an entry in the playlist for the new key URI/IV if hls_flags periodic_rekey is enabled.

Key info file format:

```
key URI
key file path
IV (optional)

```

Example key URIs:

```
http://server/file.key
/path/to/file.key
file.key

```

Example key file paths:

```
file.key
/path/to/file.key

```

Example IV:

```
0123456789ABCDEF0123456789ABCDEF

```

Key info file example:

```
http://server/file.key
/path/to/file.key
0123456789ABCDEF0123456789ABCDEF

```

Example shell script:

```
#!/bin/sh
BASE_URL=${1:-'.'}
openssl rand 16 > file.key
echo $BASE_URL/file.key > file.keyinfo
echo file.key >> file.keyinfo
echo $(openssl rand -hex 16) >> file.keyinfo
ffmpeg -f lavfi -re -i testsrc -c:v h264 -hls_flags delete_segments \
  -hls_key_info_file file.keyinfo out.m3u8

```

hls_enc bool

Enable (1) or disable (0) the AES128 encryption. When enabled every segment generated is encrypted and the encryption key is saved as playlist name.key.

hls_enc_key key

Specify a 16-octet key to encrypt the segments, by default it is randomly generated.

hls_enc_key_url keyurl

If set, keyurl is prepended instead of baseurl to the key filename in the playlist.

hls_enc_iv iv

Specify the 16-octet initialization vector for every segment instead of the autogenerated ones.

hls_segment_type flags

Possible values:

‘mpegts’

Output segment files in MPEG-2 Transport Stream format. This is compatible with all HLS versions.

‘fmp4’

Output segment files in fragmented MP4 format, similar to MPEG-DASH. fmp4 files may be used in HLS version 7 and above.

hls_fmp4_init_filename filename

Set filename for the fragment files header file, default filename is init.mp4.

When strftime is enabled, filename is expanded to the segment filename with localtime.

For example:

```
ffmpeg -i in.nut -hls_segment_type fmp4 -strftime 1 -hls_fmp4_init_filename "%s_init.mp4" out.m3u8

```

will produce init like this 1602678741_init.mp4.

hls_fmp4_init_resend bool

Resend init file after m3u8 file refresh every time, default is 0.

When var_stream_map is set with two or more variant streams, the filename pattern must contain the string "%v", this string specifies the position of variant stream index in the generated init file names. The string "%v" may be present in the filename or in the last directory name containing the file. If the string is present in the directory name, then sub-directories are created after expanding the directory name pattern. This enables creation of init files corresponding to different variant streams in subdirectories.

hls_flags flags

Possible values:

‘single_file’

If this flag is set, the muxer will store all segments in a single MPEG-TS file, and will use byte ranges in the playlist. HLS playlists generated with this way will have the version number 4.

For example:

```
ffmpeg -i in.nut -hls_flags single_file out.m3u8

```

will produce the playlist, out.m3u8, and a single segment file, out.ts.

‘delete_segments’

Segment files removed from the playlist are deleted after a period of time equal to the duration of the segment plus the duration of the playlist.

‘append_list’

Append new segments into the end of old segment list, and remove the #EXT-X-ENDLIST from the old segment list.

‘round_durations’

Round the duration info in the playlist file segment info to integer values, instead of using floating point. If there are no other features requiring higher HLS versions be used, then this will allow ffmpeg to output a HLS version 2 m3u8.

‘discont_start’

Add the #EXT-X-DISCONTINUITY tag to the playlist, before the first segment’s information.

‘omit_endlist’

Do not append the EXT-X-ENDLIST tag at the end of the playlist.

‘periodic_rekey’

The file specified by hls_key_info_file will be checked periodically and detect updates to the encryption info. Be sure to replace this file atomically, including the file containing the AES encryption key.

‘independent_segments’

Add the #EXT-X-INDEPENDENT-SEGMENTS tag to playlists that has video segments and when all the segments of that playlist are guaranteed to start with a key frame.

‘iframes_only’

Add the #EXT-X-I-FRAMES-ONLY tag to playlists that has video segments and can play only I-frames in the #EXT-X-BYTERANGE mode.

‘split_by_time’

Allow segments to start on frames other than key frames. This improves behavior on some players when the time between key frames is inconsistent, but may make things worse on others, and can cause some oddities during seeking. This flag should be used with the hls_time option.

‘program_date_time’

Generate EXT-X-PROGRAM-DATE-TIME tags.

‘second_level_segment_index’

Make it possible to use segment indexes as %%d in the hls_segment_filename option expression besides date/time values when strftime option is on. To get fixed width numbers with trailing zeroes, %%0xd format is available where x is the required width.

‘second_level_segment_size’

Make it possible to use segment sizes (counted in bytes) as %%s in hls_segment_filename option expression besides date/time values when strftime is on. To get fixed width numbers with trailing zeroes, %%0xs format is available where x is the required width.

‘second_level_segment_duration’

Make it possible to use segment duration (calculated in microseconds) as %%t in hls_segment_filename option expression besides date/time values when strftime is on. To get fixed width numbers with trailing zeroes, %%0xt format is available where x is the required width.

For example:

```
ffmpeg -i sample.mpeg \
   -f hls -hls_time 3 -hls_list_size 5 \
   -hls_flags second_level_segment_index+second_level_segment_size+second_level_segment_duration \
   -strftime 1 -strftime_mkdir 1 -hls_segment_filename "segment_%Y%m%d%H%M%S_%%04d_%%08s_%%013t.ts" stream.m3u8

```

will produce segments like this: segment_20170102194334_0003_00122200_0000003000000.ts, segment_20170102194334_0004_00120072_0000003000000.ts etc.

‘temp_file’

Write segment data to filename.tmp and rename to filename only once the segment is complete.

A webserver serving up segments can be configured to reject requests to *.tmp to prevent access to in-progress segments before they have been added to the m3u8 playlist.

This flag also affects how m3u8 playlist files are created. If this flag is set, all playlist files will be written into a temporary file and renamed after they are complete, similarly as segments are handled. But playlists with file protocol and with hls_playlist_type type other than ‘vod’ are always written into a temporary file regardless of this flag.

Master playlist files specified with master_pl_name, if any, with file protocol, are always written into temporary file regardless of this flag if master_pl_publish_rate value is other than zero.

hls_playlist_type type

If type is ‘event’, emit #EXT-X-PLAYLIST-TYPE:EVENT in the m3u8 header. This forces hls_list_size to 0; the playlist can only be appended to.

If type is ‘vod’, emit #EXT-X-PLAYLIST-TYPE:VOD in the m3u8 header. This forces hls_list_size to 0; the playlist must not change.

method method

Use the given HTTP method to create the hls files.

For example:

```
ffmpeg -re -i in.ts -f hls -method PUT http://example.com/live/out.m3u8

```

will upload all the mpegts segment files to the HTTP server using the HTTP PUT method, and update the m3u8 files every refresh times using the same method. Note that the HTTP server must support the given method for uploading files.

http_user_agent agent

Override User-Agent field in HTTP header. Applicable only for HTTP output.

var_stream_map stream_map

Specify a map string defining how to group the audio, video and subtitle streams into different variant streams. The variant stream groups are separated by space.

Expected string format is like this "a:0,v:0 a:1,v:1 ....". Here a:, v:, s: are the keys to specify audio, video and subtitle streams respectively. Allowed values are 0 to 9 (limited just based on practical usage).

When there are two or more variant streams, the output filename pattern must contain the string "%v": this string specifies the position of variant stream index in the output media playlist filenames. The string "%v" may be present in the filename or in the last directory name containing the file. If the string is present in the directory name, then sub-directories are created after expanding the directory name pattern. This enables creation of variant streams in subdirectories.

A few examples follow.

- Create two hls variant streams. The first variant stream will contain video stream of bitrate 1000k and audio stream of bitrate 64k and the second variant stream will contain video stream of bitrate 256k and audio stream of bitrate 32k. Here, two media playlist with file names out_0.m3u8 and out_1.m3u8 will be created.

```
ffmpeg -re -i in.ts -b:v:0 1000k -b:v:1 256k -b:a:0 64k -b:a:1 32k \
  -map 0:v -map 0:a -map 0:v -map 0:a -f hls -var_stream_map "v:0,a:0 v:1,a:1" \
  http://example.com/live/out_%v.m3u8

```

- If you want something meaningful text instead of indexes in result names, you may specify names for each or some of the variants. The following example will create two hls variant streams as in the previous one. But here, the two media playlist with file names out_my_hd.m3u8 and out_my_sd.m3u8 will be created.

```
ffmpeg -re -i in.ts -b:v:0 1000k -b:v:1 256k -b:a:0 64k -b:a:1 32k \
  -map 0:v -map 0:a -map 0:v -map 0:a -f hls -var_stream_map "v:0,a:0,name:my_hd v:1,a:1,name:my_sd" \
  http://example.com/live/out_%v.m3u8

```

- Create three hls variant streams. The first variant stream will be a video only stream with video bitrate 1000k, the second variant stream will be an audio only stream with bitrate 64k and the third variant stream will be a video only stream with bitrate 256k. Here, three media playlist with file names out_0.m3u8, out_1.m3u8 and out_2.m3u8 will be created.

```
ffmpeg -re -i in.ts -b:v:0 1000k -b:v:1 256k -b:a:0 64k \
  -map 0:v -map 0:a -map 0:v -f hls -var_stream_map "v:0 a:0 v:1" \
  http://example.com/live/out_%v.m3u8

```

- Create the variant streams in subdirectories. Here, the first media playlist is created at http://example.com/live/vs_0/out.m3u8 and the second one at http://example.com/live/vs_1/out.m3u8.

```
ffmpeg -re -i in.ts -b:v:0 1000k -b:v:1 256k -b:a:0 64k -b:a:1 32k \
  -map 0:v -map 0:a -map 0:v -map 0:a -f hls -var_stream_map "v:0,a:0 v:1,a:1" \
  http://example.com/live/vs_%v/out.m3u8

```

- Create two audio only and two video only variant streams. In addition to the #EXT-X-STREAM-INF tag for each variant stream in the master playlist, the #EXT-X-MEDIA tag is also added for the two audio only variant streams and they are mapped to the two video only variant streams with audio group names ’aud_low’ and ’aud_high’. By default, a single hls variant containing all the encoded streams is created.

```
ffmpeg -re -i in.ts -b:a:0 32k -b:a:1 64k -b:v:0 1000k -b:v:1 3000k  \
  -map 0:a -map 0:a -map 0:v -map 0:v -f hls \
  -var_stream_map "a:0,agroup:aud_low a:1,agroup:aud_high v:0,agroup:aud_low v:1,agroup:aud_high" \
  -master_pl_name master.m3u8 \
  http://example.com/live/out_%v.m3u8

```

-  Create two audio only and one video only variant streams. In addition to the #EXT-X-STREAM-INF tag for each variant stream in the master playlist, the #EXT-X-MEDIA tag is also added for the two audio only variant streams and they are mapped to the one video only variant streams with audio group name ’aud_low’, and the audio group have default stat is NO or YES. By default, a single hls variant containing all the encoded streams is created.

```
ffmpeg -re -i in.ts -b:a:0 32k -b:a:1 64k -b:v:0 1000k \
  -map 0:a -map 0:a -map 0:v -f hls \
  -var_stream_map "a:0,agroup:aud_low,default:yes a:1,agroup:aud_low v:0,agroup:aud_low" \
  -master_pl_name master.m3u8 \
  http://example.com/live/out_%v.m3u8

```

- Create two audio only and one video only variant streams. In addition to the #EXT-X-STREAM-INF tag for each variant stream in the master playlist, the #EXT-X-MEDIA tag is also added for the two audio only variant streams and they are mapped to the one video only variant streams with audio group name ’aud_low’, and the audio group have default stat is NO or YES, and one audio have and language is named ENG, the other audio language is named CHN. By default, a single hls variant containing all the encoded streams is created.

```
ffmpeg -re -i in.ts -b:a:0 32k -b:a:1 64k -b:v:0 1000k \
  -map 0:a -map 0:a -map 0:v -f hls \
  -var_stream_map "a:0,agroup:aud_low,default:yes,language:ENG a:1,agroup:aud_low,language:CHN v:0,agroup:aud_low" \
  -master_pl_name master.m3u8 \
  http://example.com/live/out_%v.m3u8

```

- Create a single variant stream. Add the #EXT-X-MEDIA tag with TYPE=SUBTITLES in the master playlist with webvtt subtitle group name ’subtitle’ and optional subtitle name, e.g. ’English’. Make sure the input file has one text subtitle stream at least.

```
ffmpeg -y -i input_with_subtitle.mkv \
 -b:v:0 5250k -c:v h264 -pix_fmt yuv420p -profile:v main -level 4.1 \
 -b:a:0 256k \
 -c:s webvtt -c:a mp2 -ar 48000 -ac 2 -map 0:v -map 0:a:0 -map 0:s:0 \
 -f hls -var_stream_map "v:0,a:0,s:0,sgroup:subtitle,sname:English" \
 -master_pl_name master.m3u8 -t 300 -hls_time 10 -hls_init_time 4 -hls_list_size \
 10 -master_pl_publish_rate 10 -hls_flags \
 delete_segments+discont_start+split_by_time ./tmp/video.m3u8

```

cc_stream_map cc_stream_map

Map string which specifies different closed captions groups and their attributes. The closed captions stream groups are separated by space.

Expected string format is like this "ccgroup:<group name>,instreamid:<INSTREAM-ID>,language:<language code> ....". ’ccgroup’ and ’instreamid’ are mandatory attributes. ’language’ is an optional attribute.

The closed captions groups configured using this option are mapped to different variant streams by providing the same ’ccgroup’ name in the var_stream_map string.

For example:

```
ffmpeg -re -i in.ts -b:v:0 1000k -b:v:1 256k -b:a:0 64k -b:a:1 32k \
  -a53cc:0 1 -a53cc:1 1 \
  -map 0:v -map 0:a -map 0:v -map 0:a -f hls \
  -cc_stream_map "ccgroup:cc,instreamid:CC1,language:en ccgroup:cc,instreamid:CC2,language:sp" \
  -var_stream_map "v:0,a:0,ccgroup:cc v:1,a:1,ccgroup:cc" \
  -master_pl_name master.m3u8 \
  http://example.com/live/out_%v.m3u8

```

will add two #EXT-X-MEDIA tags with TYPE=CLOSED-CAPTIONS in the master playlist for the INSTREAM-IDs ’CC1’ and ’CC2’. Also, it will add CLOSED-CAPTIONS attribute with group name ’cc’ for the two output variant streams.

If var_stream_map is not set, then the first available ccgroup in cc_stream_map is mapped to the output variant stream.

For example:

```
ffmpeg -re -i in.ts -b:v 1000k -b:a 64k -a53cc 1 -f hls \
  -cc_stream_map "ccgroup:cc,instreamid:CC1,language:en" \
  -master_pl_name master.m3u8 \
  http://example.com/live/out.m3u8

```

this will add #EXT-X-MEDIA tag with TYPE=CLOSED-CAPTIONS in the master playlist with group name ’cc’, language ’en’ (english) and INSTREAM-ID ’CC1’. Also, it will add CLOSED-CAPTIONS attribute with group name ’cc’ for the output variant stream.

master_pl_name name

Create HLS master playlist with the given name.

For example:

```
ffmpeg -re -i in.ts -f hls -master_pl_name master.m3u8 http://example.com/live/out.m3u8

```

creates an HLS master playlist with name master.m3u8 which is published at http://example.com/live/.

master_pl_publish_rate count

Publish master play list repeatedly every after specified number of segment intervals.

For example:

```
ffmpeg -re -i in.ts -f hls -master_pl_name master.m3u8 \
-hls_time 2 -master_pl_publish_rate 30 http://example.com/live/out.m3u8

```

creates an HLS master playlist with name master.m3u8 and keeps publishing it repeatedly every after 30 segments i.e. every after 60s.

http_persistent bool

Use persistent HTTP connections. Applicable only for HTTP output.

timeout timeout

Set timeout for socket I/O operations. Applicable only for HTTP output.

ignore_io_errors bool

Ignore IO errors during open, write and delete. Useful for long-duration runs with network output.

headers headers

Set custom HTTP headers, can override built in default headers. Applicable only for HTTP output.

### 21.48 iamf# TOC

Immersive Audio Model and Formats (IAMF) muxer.

IAMF is used to provide immersive audio content for presentation on a wide range of devices in both streaming and offline applications. These applications include internet audio streaming, multicasting/broadcasting services, file download, gaming, communication, virtual and augmented reality, and others. In these applications, audio may be played back on a wide range of devices, e.g., headphones, mobile phones, tablets, TVs, sound bars, home theater systems, and big screens.

This format was promoted and designed by Alliance for Open Media.

For more information about this format, see https://aomedia.org/iamf/.

### 21.49 ico# TOC

ICO file muxer.

Microsoft’s icon file format (ICO) has some strict limitations that should be noted:

- Size cannot exceed 256 pixels in any dimension

- Only BMP and PNG images can be stored

- If a BMP image is used, it must be one of the following pixel formats:

```
BMP Bit Depth      FFmpeg Pixel Format
1bit               pal8
4bit               pal8
8bit               pal8
16bit              rgb555le
24bit              bgr24
32bit              bgra

```

- If a BMP image is used, it must use the BITMAPINFOHEADER DIB header

- If a PNG image is used, it must use the rgba pixel format

### 21.50 ilbc# TOC

Internet Low Bitrate Codec (iLBC) raw muxer.

It accepts a single ‘ilbc’ audio stream.

### 21.51 image2, image2pipe# TOC

Image file muxer.

The ‘image2’ muxer writes video frames to image files.

The output filenames are specified by a pattern, which can be used to produce sequentially numbered series of files. The pattern may contain the string "%d" or "%0Nd", this string specifies the position of the characters representing a numbering in the filenames. If the form "%0Nd" is used, the string representing the number in each filename is 0-padded to N digits. The literal character ’%’ can be specified in the pattern with the string "%%".

If the pattern contains "%d" or "%0Nd", the first filename of the file list specified will contain the number 1, all the following numbers will be sequential.

The pattern may contain a suffix which is used to automatically determine the format of the image files to write.

For example the pattern "img-%03d.bmp" will specify a sequence of filenames of the form img-001.bmp, img-002.bmp, ..., img-010.bmp, etc. The pattern "img%%-%d.jpg" will specify a sequence of filenames of the form img%-1.jpg, img%-2.jpg, ..., img%-10.jpg, etc.

The image muxer supports the .Y.U.V image file format. This format is special in that each image frame consists of three files, for each of the YUV420P components. To read or write this image file format, specify the name of the ’.Y’ file. The muxer will automatically open the ’.U’ and ’.V’ files as required.

The ‘image2pipe’ muxer accepts the same options as the ‘image2’ muxer, but ignores the pattern verification and expansion, as it is supposed to write to the command output rather than to an actual stored file.

#### 21.51.1 Options# TOC

frame_pts bool

If set to 1, expand the filename with the packet PTS (presentation time stamp). Default value is 0.

start_number count

Start the sequence from the specified number. Default value is 1.

update bool

If set to 1, the filename will always be interpreted as just a filename, not a pattern, and the corresponding file will be continuously overwritten with new images. Default value is 0.

strftime bool

If set to 1, expand the filename with date and time information from strftime(). Default value is 0.

atomic_writing bool

Write output to a temporary file, which is renamed to target filename once writing is completed. Default is disabled.

protocol_opts options_list

Set protocol options as a :-separated list of key=value parameters. Values containing the : special character must be escaped.

update_filemtime bool

If set to 1, set each output file’s modification time to the creation_time metadata value plus the frame’s PTS offset. If creation_time is missing or unparsable, a warning is logged and the option is ignored. Default value is 0.

#### 21.51.2 Examples# TOC

- Use ffmpeg for creating a sequence of files img-001.jpeg, img-002.jpeg, ..., taking one image every second from the input video:

```
ffmpeg -i in.avi -fps_mode cfr -r 1 -f image2 'img-%03d.jpeg'

```

Note that with ffmpeg, if the format is not specified with the -f option and the output filename specifies an image file format, the image2 muxer is automatically selected, so the previous command can be written as:

```
ffmpeg -i in.avi -fps_mode cfr -r 1 'img-%03d.jpeg'

```

Note also that the pattern must not necessarily contain "%d" or "%0Nd", for example to create a single image file img.jpeg from the start of the input video you can employ the command:

```
ffmpeg -i in.avi -f image2 -frames:v 1 img.jpeg

```

- The strftime option allows you to expand the filename with date and time information. Check the documentation of the strftime() function for the syntax.
To generate image files from the strftime() "%Y-%m-%d_%H-%M-%S" pattern, the following ffmpeg command can be used:

```
ffmpeg -f v4l2 -r 1 -i /dev/video0 -f image2 -strftime 1 "%Y-%m-%d_%H-%M-%S.jpg"

```

- Set the file name with current frame’s PTS:

```
ffmpeg -f v4l2 -r 1 -i /dev/video0 -copyts -f image2 -frame_pts true %d.jpg

```

- Publish contents of your desktop directly to a WebDAV server every second:

```
ffmpeg -f x11grab -framerate 1 -i :0.0 -q:v 6 -update 1 -protocol_opts method=PUT http://example.com/desktop.jpg

```

### 21.52 ircam# TOC

Berkeley / IRCAM / CARL Sound Filesystem (BICSF) format muxer.

The Berkeley/IRCAM/CARL Sound Format, developed in the 1980s, is a result of the merging of several different earlier sound file formats and systems including the csound system developed by Dr Gareth Loy at the Computer Audio Research Lab (CARL) at UC San Diego, the IRCAM sound file system developed by Rob Gross and Dan Timis at the Institut de Recherche et Coordination Acoustique / Musique in Paris and the Berkeley Fast Filesystem.

It was developed initially as part of the Berkeley/IRCAM/CARL Sound Filesystem, a suite of programs designed to implement a filesystem for audio applications running under Berkeley UNIX. It was particularly popular in academic music research centres, and was used a number of times in the creation of early computer-generated compositions.

This muxer accepts a single audio stream containing PCM data.

### 21.53 iterm2# TOC

iTerm2 inline image protocol muxer.

This muxer writes video frames as OSC 1337 inline images for display in terminals that support the iTerm2 image protocol. Use -re to limit the output rate to the source framerate; without it, frames are emitted as fast as they are encoded, which is usually not desired for live display.

Frames are sent with the multipart form of the protocol, which splits each image across several short control sequences. This avoids the per-sequence size limit that otherwise discards large frames, and requires iTerm2 3.5 or newer.

The output is a self-contained byte stream and can be redirected to a file. Replaying the file with cat displays the images in the terminal.

#### 21.53.1 Options# TOC

display_width size

Set the displayed image width. size can be ‘auto’, N terminal cells, Npx pixels, or N% of the terminal width. When unset, the terminal derives the width from the image.

display_height size

Set the displayed image height. size uses the same syntax as display_width. When unset, the terminal derives the height from the image.

keep_aspect bool

Preserve the input aspect ratio when scaling. Default is enabled.

tmux bool

Wrap image data in tmux DCS passthrough. This requires a tmux version whose passthrough sequence size limit is large enough for image data, with passthrough enabled via tmux set -g allow-passthrough on. Default is disabled.

#### 21.53.2 Examples# TOC

Display a video in an iTerm2 terminal:

```
ffmpeg -re -i input.mp4 -f iterm2 -

```

Scale the displayed image to 40 terminal cells tall. Inside tmux, enable passthrough first with tmux set -g allow-passthrough on, then add tmux:

```
ffmpeg -re -i input.mp4 -f iterm2 -display_height 40 -tmux 1 -

```

### 21.54 jpeg_mpf# TOC

JPEG Multi-Picture Format muxer.

Stores multiple JPEG images in a single file using the CIPA DC-007 MP extensions. The first input stream is always the primary image. Every other stream must be specified by a stream group describing what it is; see the -stream_group option of the ffmpeg tool.

Note: Currently, the only implemented type of stream group is ‘gain_map’, which may be used to store a gain map for JPEG Ultra HDR.

#### 21.54.1 Examples# TOC

Encode an SDR tone-mapped image and an HDR gain map computed from it:

```
ffmpeg -i input-hdr.png -filter_complex
"[0:v] scale=out_transfer=srgb:out_primaries=bt709,split [base][sdr];
[base][0:v] gainmap [gain]" -map "[sdr]" -map "[gain]" -c:v mjpeg
-stream_group type=gain_map:st=0:st=1:el_index=1 -f jpeg_mpf output.jpg

```

### 21.55 ivf# TOC

On2 IVF muxer.

IVF was developed by On2 Technologies (formerly known as Duck Corporation), to store internally developed codecs.

This muxer accepts a single ‘vp8’, ‘vp9’, or ‘av1’ video stream.

### 21.56 jacosub# TOC

JACOsub subtitle format muxer.

This muxer accepts a single ‘jacosub’ subtitles stream.

For more information about the format, see http://unicorn.us.com/jacosub/jscripts.html.

### 21.57 ktx# TOC

Khronos Texture 1.0 muxer for ASTC textures.

This muxer accepts a single ‘libastcenc’ video stream and writes one image: the ASTC block size and the image dimensions are taken from the encoder’s extradata, and a second packet is rejected. The stored row order is recorded in a KTXorientation key.

#### 21.57.1 Options# TOC

srgb integer

Select the GL internal format color space. Possible values:

‘auto’

Use the color profile published by the encoder, which is the default.

‘linear’

Write the linear ASTC format.

‘srgb’

Write the sRGB ASTC format.

An explicit value that contradicts a known encoder profile is rejected. A raw .astc input does not carry a color profile, so remuxing it to .ktx with auto writes the sRGB format; pass -srgb linear to keep a linear texture.

### 21.58 kvag# TOC

Simon & Schuster Interactive VAG muxer.

This custom VAG container is used by some Simon & Schuster Interactive games such as "Real War", and "Real War: Rogue States".

This muxer accepts a single ‘adpcm_ima_ssi’ audio stream.

### 21.59 lc3# TOC

Bluetooth SIG Low Complexity Communication Codec audio (LC3), or ETSI TS 103 634 Low Complexity Communication Codec plus (LC3plus).

This muxer accepts a single ‘lc3’ audio stream.

### 21.60 lrc# TOC

LRC lyrics file format muxer.

LRC (short for LyRiCs) is a computer file format that synchronizes song lyrics with an audio file, such as MP3, Vorbis, or MIDI.

This muxer accepts a single ‘subrip’ or ‘text’ subtitles stream.

#### 21.60.1 Options# TOC

precision number

Set the number of decimal digits used for the fractional (sub-second) part of the timestamps. Range is 1 to 6. Default is 2, i.e. centiseconds.

#### 21.60.2 Metadata# TOC

The following metadata tags are converted to the format corresponding metadata:

title

album

artist

author

creator

encoder

encoder_version

If ‘encoder_version’ is not explicitly set, it is automatically set to the libavformat version.

### 21.61 matroska# TOC

Matroska container muxer.

This muxer implements the matroska and webm container specs.

#### 21.61.1 Metadata# TOC

The recognized metadata settings in this muxer are:

title

Set title name provided to a single track. This gets mapped to the FileDescription element for a stream written as attachment.

language

Specify the language of the track in the Matroska languages form.

The language can be either the 3 letters bibliographic ISO-639-2 (ISO 639-2/B) form (like "fre" for French), or a language code mixed with a country code for specialities in languages (like "fre-ca" for Canadian French).

stereo_mode

Set stereo 3D video layout of two views in a single video track. The -stereo3d option overrides existing stereoscopic side data and stereo_mode metadata for the selected output stream. Otherwise, stream-level stereo_mode metadata takes priority over global metadata, and stereoscopic side data is used when neither tag is present.

The following values are recognized:

‘mono’

video is not stereo

‘left_right’

Both views are arranged side by side, Left-eye view is on the left

‘bottom_top’

Both views are arranged in top-bottom orientation, Left-eye view is at bottom

‘top_bottom’

Both views are arranged in top-bottom orientation, Left-eye view is on top

‘checkerboard_rl’

Each view is arranged in a checkerboard interleaved pattern, Left-eye view being first

‘checkerboard_lr’

Each view is arranged in a checkerboard interleaved pattern, Right-eye view being first

‘row_interleaved_rl’

Each view is constituted by a row based interleaving, Right-eye view is first row

‘row_interleaved_lr’

Each view is constituted by a row based interleaving, Left-eye view is first row

‘col_interleaved_rl’

Both views are arranged in a column based interleaving manner, Right-eye view is first column

‘col_interleaved_lr’

Both views are arranged in a column based interleaving manner, Left-eye view is first column

‘anaglyph_cyan_red’

All frames are in anaglyph format viewable through red-cyan filters

‘right_left’

Both views are arranged side by side, Right-eye view is on the left

‘anaglyph_green_magenta’

All frames are in anaglyph format viewable through green-magenta filters

‘block_lr’

Both eyes laced in one Block, Left-eye view is first

‘block_rl’

Both eyes laced in one Block, Right-eye view is first

For example a 3D WebM clip can be created using the following command line:

```
ffmpeg -i sample_left_right_clip.mpg -an -c:v libvpx -metadata stereo_mode=left_right -y stereo_clip.webm

```

#### 21.61.2 Options# TOC

reserve_index_space size

By default, this muxer writes the index for seeking (called cues in Matroska terms) at the end of the file, because it cannot know in advance how much space to leave for the index at the beginning of the file. However for some use cases – e.g. streaming where seeking is possible but slow – it is useful to put the index at the beginning of the file.

If this option is set to a non-zero value, the muxer will reserve size bytes of space in the file header and then try to write the cues there when the muxing finishes. If the reserved space does not suffice, no Cues will be written, the file will be finalized and writing the trailer will return an error. A safe size for most use cases should be about 50kB per hour of video.

Note that cues are only written if the output is seekable and this option will have no effect if it is not.

cues_to_front bool

If set, the muxer will write the index at the beginning of the file by shifting the main data if necessary. This can be combined with reserve_index_space in which case the data is only shifted if the initially reserved space turns out to be insufficient.

This option is ignored if the output is unseekable.

cluster_size_limit size

Store at most the provided amount of bytes in a cluster.

If not specified, the limit is set automatically to a sensible hardcoded fixed value.

cluster_time_limit duration

Store at most the provided number of milliseconds in a cluster.

If not specified, the limit is set automatically to a sensible hardcoded fixed value.

dash bool

Create a WebM file conforming to WebM DASH specification. By default it is set to false.

dash_track_number index

Track number for the DASH stream. By default it is set to 1.

live bool

Write files assuming it is a live stream. By default it is set to false.

allow_raw_vfw bool

Allow raw VFW mode. By default it is set to false.

flipped_raw_rgb bool

If set to true, store positive height for raw RGB bitmaps, which indicates bitmap is stored bottom-up. Note that this option does not flip the bitmap which has to be done manually beforehand, e.g. by using the ‘vflip’ filter. Default is false and indicates bitmap is stored top down.

write_crc32 bool

Write a CRC32 element inside every Level 1 element. By default it is set to true. This option is ignored for WebM.

default_mode mode

Control how the FlagDefault of the output tracks will be set. It influences which tracks players should play by default. The default mode is ‘passthrough’.

‘infer’

Every track with disposition default will have the FlagDefault set. Additionally, for each type of track (audio, video or subtitle), if no track with disposition default of this type exists, then the first track of this type will be marked as default (if existing). This ensures that the default flag is set in a sensible way even if the input originated from containers that lack the concept of default tracks.

‘infer_no_subs’

This mode is the same as infer except that if no subtitle track with disposition default exists, no subtitle track will be marked as default.

‘passthrough’

In this mode the FlagDefault is set if and only if the AV_DISPOSITION_DEFAULT flag is set in the disposition of the corresponding stream.

### 21.62 md5# TOC

MD5 testing format.

This is a variant of the hash muxer. Unlike that muxer, it defaults to using the MD5 hash function.

See also the hash and framemd5 muxers.

#### 21.62.1 Examples# TOC

- To compute the MD5 hash of the input converted to raw audio and video, and store it in the file out.md5:

```
ffmpeg -i INPUT -f md5 out.md5

```

- To print the MD5 hash to stdout:

```
ffmpeg -i INPUT -f md5 -

```

### 21.63 mcc# TOC

Muxer for MacCaption MCC files, it supports MCC versions 1.0 and 2.0. MCC files store VANC data, which can include closed captions (EIA-608 and CEA-708), ancillary time code, pan-scan data, etc.

#### 21.63.1 Options# TOC

The muxer options are:

override_time_code_rate

Override the Time Code Rate value in the output. Defaults to trying to deduce from the stream’s time_base, which often doesn’t work.

use_u_alias

Use the U alias for the byte sequence E1h 00h 00h 00h. Disabled by default because some .mcc files disagree on whether it has 2 or 3 zero bytes.

mcc_version

The MCC file format version. Must be either 1 or 2, defaults to 2.

creation_program

The creation program. Defaults to this version of FFmpeg.

creation_time

The creation time. Defaults to the current time.

#### 21.63.2 Examples# TOC

- Extract a MXF SMPTE_436M_ANC stream from a MXF file and write it to a MCC file at 30 fps.

```
ffmpeg -i input.mxf -c copy -map 0:d -override_time_code_rate 30 out.mcc

```

- Extract EIA-608/CTA-708 closed captions from a .mp4 file and write them to a MCC file at 29.97 fps.

```
ffmpeg -f lavfi -i "movie=input.mp4[out+subcc]" -c:s copy -map 0:s -override_time_code_rate 30000/1001 out.mcc

```

### 21.64 microdvd# TOC

MicroDVD subtitle format muxer.

This muxer accepts a single ‘microdvd’ subtitles stream.

### 21.65 mmf# TOC

Synthetic music Mobile Application Format (SMAF) format muxer.

SMAF is a music data format specified by Yamaha for portable electronic devices, such as mobile phones and personal digital assistants.

This muxer accepts a single ‘adpcm_yamaha’ audio stream.

### 21.66 mp3# TOC

The MP3 muxer writes a raw MP3 stream with the following optional features:

- An ID3v2 metadata header at the beginning (enabled by default). Versions 2.3 and 2.4 are supported, the id3v2_version private option controls which one is used (3 or 4). Setting id3v2_version to 0 disables the ID3v2 header completely.
The muxer supports writing attached pictures (APIC frames) to the ID3v2 header. The pictures are supplied to the muxer in form of a video stream with a single packet. There can be any number of those streams, each will correspond to a single APIC frame. The stream metadata tags title and comment map to APIC description and picture type respectively. See http://id3.org/id3v2.4.0-frames for allowed picture types.

Note that the APIC frames must be written at the beginning, so the muxer will buffer the audio frames until it gets all the pictures. It is therefore advised to provide the pictures as soon as possible to avoid excessive buffering.

- A Xing/LAME frame right after the ID3v2 header (if present). It is enabled by default, but will be written only if the output is seekable. The write_xing private option can be used to disable it. The frame contains various information that may be useful to the decoder, like the audio duration or encoder delay.

- A legacy ID3v1 tag at the end of the file (disabled by default). It may be enabled with the write_id3v1 private option, but as its capabilities are very limited, its usage is not recommended.

Examples:

Write an mp3 with an ID3v2.3 header and an ID3v1 footer:

```
ffmpeg -i INPUT -id3v2_version 3 -write_id3v1 1 out.mp3

```

To attach a picture to an mp3 file select both the audio and the picture stream with map:

```
ffmpeg -i input.mp3 -i cover.png -c copy -map 0 -map 1
-metadata:s:v title="Album cover" -metadata:s:v comment="Cover (Front)" out.mp3

```

Write a "clean" MP3 without any extra features:

```
ffmpeg -i input.wav -write_xing 0 -id3v2_version 0 out.mp3

```

### 21.67 mpegts# TOC

MPEG transport stream muxer.

This muxer implements ISO 13818-1 and part of ETSI EN 300 468.

The recognized metadata settings in mpegts muxer are service_provider and service_name. If they are not set the default for service_provider is ‘FFmpeg’ and the default for service_name is ‘Service01’.

#### 21.67.1 Options# TOC

The muxer options are:

mpegts_transport_stream_id integer

Set the ‘transport_stream_id’. This identifies a transponder in DVB. Default is 0x0001.

mpegts_original_network_id integer

Set the ‘original_network_id’. This is unique identifier of a network in DVB. Its main use is in the unique identification of a service through the path ‘Original_Network_ID, Transport_Stream_ID’. Default is 0xff01.

mpegts_service_id integer

Set the ‘service_id’, also known as program in DVB. Default is 0x0001.

mpegts_service_type integer

Set the program ‘service_type’. Default is digital_tv. Accepts the following options:

‘hex_value’

Any hexadecimal value between 0x01 and 0xff as defined in ETSI 300 468.

‘digital_tv’

Digital TV service.

‘digital_radio’

Digital Radio service.

‘teletext’

Teletext service.

‘advanced_codec_digital_radio’

Advanced Codec Digital Radio service.

‘mpeg2_digital_hdtv’

MPEG2 Digital HDTV service.

‘advanced_codec_digital_sdtv’

Advanced Codec Digital SDTV service.

‘advanced_codec_digital_hdtv’

Advanced Codec Digital HDTV service.

‘hevc_digital_hdtv’

HEVC Digital Television service.

mpegts_pmt_start_pid integer

Set the first PID for PMTs. Default is 0x1000, minimum is 0x0020, maximum is 0x1ffa. This option has no effect in m2ts mode where the PMT PID is fixed 0x0100.

mpegts_start_pid integer

Set the first PID for elementary streams. Default is 0x0100, minimum is 0x0020, maximum is 0x1ffa. This option has no effect in m2ts mode where the elementary stream PIDs are fixed.

mpegts_m2ts_mode boolean

Enable m2ts mode if set to 1. Default value is -1 which disables m2ts mode.

muxrate integer

Set a constant muxrate. Default is VBR.

pes_payload_size integer

Set minimum PES packet payload in bytes. Default is 2930.

mpegts_flags flags

Set mpegts flags. Accepts the following options:

‘resend_headers’

Reemit PAT/PMT before writing the next packet.

‘latm’

Use LATM packetization for AAC.

‘pat_pmt_at_frames’

Reemit PAT and PMT at each video frame.

‘system_b’

Conform to System B (DVB) instead of System A (ATSC).

‘initial_discontinuity’

Mark the initial packet of each stream as discontinuity.

‘nit’

Emit NIT table.

‘omit_rai’

Disable writing of random access indicator.

mpegts_copyts boolean

Preserve original timestamps, if value is set to 1. Default value is -1, which results in shifting timestamps so that they start from 0.

omit_video_pes_length boolean

Omit the PES packet length for video packets. Default is 1 (true).

pcr_period integer

Override the default PCR retransmission time in milliseconds. Default is -1 which means that the PCR interval will be determined automatically: 20 ms is used for CBR streams, the highest multiple of the frame duration which is less than 100 ms is used for VBR streams.

mpegts_pcr_pid integer

Set a separate PID for PCR packets. When set to a valid PID value, PCR is carried in adaptation-field-only packets on the specified PID, separate from the elementary stream PIDs. This is required for example by ARIB TR-B14. Default is -1 which means PCR is placed on the elementary stream PIDs.

pat_period duration

Maximum time in seconds between PAT/PMT tables. Default is 0.1.

sdt_period duration

Maximum time in seconds between SDT tables. Default is 0.5.

nit_period duration

Maximum time in seconds between NIT tables. Default is 0.5.

tables_version integer

Set PAT, PMT, SDT and NIT version (default 0, valid values are from 0 to 31, inclusively). This option allows updating stream structure so that standard consumer may detect the change. To do so, reopen output AVFormatContext (in case of API usage) or restart ffmpeg instance, cyclically changing tables_version value:

```
ffmpeg -i source1.ts -codec copy -f mpegts -tables_version 0 udp://1.1.1.1:1111
ffmpeg -i source2.ts -codec copy -f mpegts -tables_version 1 udp://1.1.1.1:1111
...
ffmpeg -i source3.ts -codec copy -f mpegts -tables_version 31 udp://1.1.1.1:1111
ffmpeg -i source1.ts -codec copy -f mpegts -tables_version 0 udp://1.1.1.1:1111
ffmpeg -i source2.ts -codec copy -f mpegts -tables_version 1 udp://1.1.1.1:1111
...

```

#### 21.67.2 Example# TOC

```
ffmpeg -i file.mpg -c copy \
     -mpegts_original_network_id 0x1122 \
     -mpegts_transport_stream_id 0x3344 \
     -mpegts_service_id 0x5566 \
     -mpegts_pmt_start_pid 0x1500 \
     -mpegts_start_pid 0x150 \
     -metadata service_provider="Some provider" \
     -metadata service_name="Some Channel" \
     out.ts

```

### 21.68 mxf, mxf_d10, mxf_opatom# TOC

MXF muxer.

#### 21.68.1 Options# TOC

The muxer options are:

store_user_comments bool

Set if user comments should be stored if available or never. IRT D-10 does not allow user comments. The default is thus to write them for mxf and mxf_opatom but not for mxf_d10

### 21.69 null# TOC

Null muxer.

This muxer does not generate any output file, it is mainly useful for testing or benchmarking purposes.

For example to benchmark decoding with ffmpeg you can use the command:

```
ffmpeg -benchmark -i INPUT -f null out.null

```

Note that the above command does not read or write the out.null file, but specifying the output file is required by the ffmpeg syntax.

Alternatively you can write the command as:

```
ffmpeg -benchmark -i INPUT -f null -

```

### 21.70 nut# TOC

-syncpoints flags

Change the syncpoint usage in nut:

default use the normal low-overhead seeking aids.

none do not use the syncpoints at all, reducing the overhead but making the stream non-seekable;

Use of this option is not recommended, as the resulting files are very damage sensitive and seeking is not possible. Also in general the overhead from syncpoints is negligible. Note, -write_index 0 can be used to disable all growing data tables, allowing to mux endless streams with limited memory and without these disadvantages.

timestamped extend the syncpoint with a wallclock field.

The none and timestamped flags are experimental.

-write_index bool

Write index at the end, the default is to write an index.

```
ffmpeg -i INPUT -f_strict experimental -syncpoints none - | processor

```

### 21.71 ogg# TOC

Ogg container muxer.

-page_duration duration

Preferred page duration, in microseconds. The muxer will attempt to create pages that are approximately duration microseconds long. This allows the user to compromise between seek granularity and container overhead. The default is 1 second. A value of 0 will fill all segments, making pages as large as possible. A value of 1 will effectively use 1 packet-per-page in most situations, giving a small seek granularity at the cost of additional container overhead.

-serial_offset value

Serial number of the first stream in bitexact mode, the others following consecutively. Chained links need distinct serial numbers, which disjoint ranges of values guarantee. The default of -1 derives each serial number from the stream’s headers instead. This makes links with different headers or tags unlikely to share a serial number, without ruling it out. Links with identical headers and tags always share one, which separately muxed outputs avoid with explicit offsets.

A link the muxer starts itself on new stream metadata keeps the offset of the link before it. With an explicit offset it then reuses its serial number. With the default it does so when its headers and tags are unchanged.

### 21.72 pdv# TOC

Playdate Video muxer.

This muxer writes the Playdate video container used by Panic’s Playdate SDK. It requires a seekable output and a single PDV video stream.

max_frames frames

Reserve space for at most frames video frames in the file header. This option is mandatory.

### 21.73 rcwt# TOC

RCWT (Raw Captions With Time) is a format native to ccextractor, a commonly used open source tool for processing 608/708 Closed Captions (CC) sources. It can be used to archive the original extracted CC bitstream and to produce a source file for later processing or conversion. The format allows for interoperability between ccextractor and FFmpeg, is simple to parse, and can be used to create a backup of the CC presentation.

This muxer implements the specification as of March 2024, which has been stable and unchanged since April 2014.

This muxer will have some nuances from the way that ccextractor muxes RCWT. No compatibility issues when processing the output with ccextractor have been observed as a result of this so far, but mileage may vary and outputs will not be a bit-exact match.

A free specification of RCWT can be found here: https://github.com/CCExtractor/ccextractor/blob/master/docs/BINARY_FILE_FORMAT.TXT

#### 21.73.1 Examples# TOC

- Extract Closed Captions to RCWT using lavfi:

```
ffmpeg -f lavfi -i "movie=INPUT.mkv[out+subcc]" -map 0:s:0 -c:s copy -f rcwt CC.rcwt.bin

```

### 21.74 segment, stream_segment, ssegment# TOC

Basic stream segmenter.

This muxer outputs streams to a number of separate files of nearly fixed duration. Output filename pattern can be set in a fashion similar to image2, or by using a strftime template if the strftime option is enabled.

stream_segment is a variant of the muxer used to write to streaming output formats, i.e. which do not require global headers, and is recommended for outputting e.g. to MPEG transport stream segments. ssegment is a shorter alias for stream_segment.

Every segment starts with a keyframe of the selected reference stream, which is set through the reference_stream option.

Note that if you want accurate splitting for a video file, you need to make the input key frames correspond to the exact splitting times expected by the segmenter, or the segment muxer will start the new segment with the key frame found next after the specified start time.

The segment muxer works best with a single constant frame rate video.

Optionally it can generate a list of the created segments, by setting the option segment_list. The list type is specified by the segment_list_type option. The entry filenames in the segment list are set by default to the basename of the corresponding segment files.

See also the hls muxer, which provides a more specific implementation for HLS segmentation.

#### 21.74.1 Options# TOC

The segment muxer supports the following options:

increment_tc 1|0

if set to 1, increment timecode between each segment If this is selected, the input need to have a timecode in the first video stream. Default value is 0.

reference_stream specifier

Set the reference stream, as specified by the string specifier. If specifier is set to auto, the reference is chosen automatically. Otherwise it must be a stream specifier (see the “Stream specifiers” chapter in the ffmpeg manual) which specifies the reference stream. The default value is auto.

segment_format format

Override the inner container format, by default it is guessed by the filename extension.

segment_format_options options_list

Set output format options using a :-separated list of key=value parameters. Values containing the : special character must be escaped.

segment_list name

Generate also a listfile named name. If not specified no listfile is generated.

segment_list_flags flags

Set flags affecting the segment list generation.

It currently supports the following flags:

‘cache’

Allow caching (only affects M3U8 list files).

‘live’

Allow live-friendly file generation.

segment_list_size size

Update the list file so that it contains at most size segments. If 0 the list file will contain all the segments. Default value is 0.

segment_list_entry_prefix prefix

Prepend prefix to each entry. Useful to generate absolute paths. By default no prefix is applied.

segment_list_type type

Select the listing format.

The following values are recognized:

‘flat’

Generate a flat list for the created segments, one segment per line.

‘csv, ext’

Generate a list for the created segments, one segment per line, each line matching the format (comma-separated values):

```
segment_filename,segment_start_time,segment_end_time

```

segment_filename is the name of the output file generated by the muxer according to the provided pattern. CSV escaping (according to RFC4180) is applied if required.

segment_start_time and segment_end_time specify the segment start and end time expressed in seconds.

A list file with the suffix ".csv" or ".ext" will auto-select this format.

‘ext’ is deprecated in favor or ‘csv’.

‘ffconcat’

Generate an ffconcat file for the created segments. The resulting file can be read using the FFmpeg concat demuxer.

A list file with the suffix ".ffcat" or ".ffconcat" will auto-select this format.

‘m3u8’

Generate an extended M3U8 file, version 3, compliant with http://tools.ietf.org/id/draft-pantos-http-live-streaming.

A list file with the suffix ".m3u8" will auto-select this format.

If not specified the type is guessed from the list file name suffix.

segment_time time

Set segment duration to time, the value must be a duration specification. Default value is "2". See also the segment_times option.

Note that splitting may not be accurate, unless you force the reference stream key-frames at the given time. See the introductory notice and the examples below.

min_seg_duration time

Set minimum segment duration to time, the value must be a duration specification. This prevents the muxer ending segments at a duration below this value. Only effective with segment_time. Default value is "0".

segment_atclocktime 1|0

If set to "1" split at regular clock time intervals starting from 00:00 o’clock. The time value specified in segment_time is used for setting the length of the splitting interval.

For example with segment_time set to "900" this makes it possible to create files at 12:00 o’clock, 12:15, 12:30, etc.

Default value is "0".

segment_clocktime_offset duration

Delay the segment splitting times with the specified duration when using segment_atclocktime.

For example with segment_time set to "900" and segment_clocktime_offset set to "300" this makes it possible to create files at 12:05, 12:20, 12:35, etc.

Default value is "0".

segment_clocktime_wrap_duration duration

Force the segmenter to only start a new segment if a packet reaches the muxer within the specified duration after the segmenting clock time. This way you can make the segmenter more resilient to backward local time jumps, such as leap seconds or transition to standard time from daylight savings time.

Default is the maximum possible duration which means starting a new segment regardless of the elapsed time since the last clock time.

segment_time_delta delta

Specify the accuracy time when selecting the start time for a segment, expressed as a duration specification. Default value is "0".

When delta is specified a key-frame will start a new segment if its PTS satisfies the relation:

```
PTS >= start_time - time_delta

```

This option is useful when splitting video content, which is always split at GOP boundaries, in case a key frame is found just before the specified split time.

In particular may be used in combination with the ffmpeg option force_key_frames. The key frame times specified by force_key_frames may not be set accurately because of rounding issues, with the consequence that a key frame time may result set just before the specified time. For constant frame rate videos a value of 1/(2*frame_rate) should address the worst case mismatch between the specified time and the time set by force_key_frames.

segment_times times

Specify a list of split points. times contains a list of comma separated duration specifications, in increasing order. See also the segment_time option.

segment_frames frames

Specify a list of split video frame numbers. frames contains a list of comma separated integer numbers, in increasing order.

This option specifies to start a new segment whenever a reference stream key frame is found and the sequential number (starting from 0) of the frame is greater or equal to the next value in the list.

segment_wrap limit

Wrap around segment index once it reaches limit.

segment_start_number number

Set the sequence number of the first segment. Defaults to 0.

segment_wrap_number number

Set the number of times the segment index is assumed to have already wrapped when generating the indexes reported in the segment list. Together with segment_wrap and segment_start_number it offsets the reported index, which is computed as segment_start_number + segment_wrap * segment_wrap_number. Defaults to 0.

strftime 1|0

Use the strftime function to define the name of the new segments to write. If this is selected, the output segment name must contain a strftime function template. Default value is 0.

break_non_keyframes 1|0

If enabled, allow segments to start on frames other than keyframes. This improves behavior on some players when the time between keyframes is inconsistent, but may make things worse on others, and can cause some oddities during seeking. Defaults to 0.

reset_timestamps 1|0

Reset timestamps at the beginning of each segment, so that each segment will start with near-zero timestamps. It is meant to ease the playback of the generated segments. May not work with some combinations of muxers/codecs. It is set to 0 by default.

initial_offset offset

Specify timestamp offset to apply to the output packet timestamps. The argument must be a time duration specification, and defaults to 0.

write_empty_segments 1|0

If enabled, write an empty segment if there are no packets during the period a segment would usually span. Otherwise, the segment will be filled with the next packet written. Defaults to 0.

write_header_trailer bool

Write a header to the first segment and a trailer to the last one, instead of writing a header and a trailer to every individual segment. Disabling it (false) also forces individual_header_trailer to false, so that no segment is given a header or trailer. Default value is true.

individual_header_trailer bool

If enabled, write a complete header and trailer to every segment, making each segment an independently usable file. If disabled (false), only the first segment is given a header and only the last one a trailer. It is forced to false when write_header_trailer is false or when segment_header_filename is set. Default value is true.

segment_header_filename name

Write the stream header to a separate file named name instead of storing it in the segments. Setting it forces write_header_trailer to true and individual_header_trailer to false, so the header is written only once, to name. Unset by default.

Make sure to require a closed GOP when encoding and to set the GOP size to fit your segment time constraint.

#### 21.74.2 Examples# TOC

- Remux the content of file in.mkv to a list of segments out-000.nut, out-001.nut, etc., and write the list of generated segments to out.list:

```
ffmpeg -i in.mkv -codec hevc -flags +cgop -g 60 -map 0 -f segment -segment_list out.list out%03d.nut

```

- Segment input and set output format options for the output segments:

```
ffmpeg -i in.mkv -f segment -segment_time 10 -segment_format_options movflags=+faststart out%03d.mp4

```

- Segment the input file according to the split points specified by the segment_times option:

```
ffmpeg -i in.mkv -codec copy -map 0 -f segment -segment_list out.csv -segment_times 1,2,3,5,8,13,21 out%03d.nut

```

- Use the ffmpeg force_key_frames option to force key frames in the input at the specified location, together with the segment option segment_time_delta to account for possible roundings operated when setting key frame times.

```
ffmpeg -i in.mkv -force_key_frames 1,2,3,5,8,13,21 -codec:v mpeg4 -codec:a pcm_s16le -map 0 \
-f segment -segment_list out.csv -segment_times 1,2,3,5,8,13,21 -segment_time_delta 0.05 out%03d.nut

```

In order to force key frames on the input file, transcoding is required.

- Segment the input file by splitting the input file according to the frame numbers sequence specified with the segment_frames option:

```
ffmpeg -i in.mkv -codec copy -map 0 -f segment -segment_list out.csv -segment_frames 100,200,300,500,800 out%03d.nut

```

- Convert the in.mkv to TS segments using the libx264 and aac encoders:

```
ffmpeg -i in.mkv -map 0 -codec:v libx264 -codec:a aac -f ssegment -segment_list out.list out%03d.ts

```

- Segment the input file, and create an M3U8 live playlist (can be used as live HLS source):

```
ffmpeg -re -i in.mkv -codec copy -map 0 -f segment -segment_list playlist.m3u8 \
-segment_list_flags +live -segment_time 10 out%03d.mkv

```

### 21.75 smoothstreaming# TOC

Smooth Streaming muxer generates a set of files (Manifest, chunks) suitable for serving with conventional web server.

window_size

Specify the number of fragments kept in the manifest. Default 0 (keep all).

extra_window_size

Specify the number of fragments kept outside of the manifest before removing from disk. Default 5.

lookahead_count

Specify the number of lookahead fragments. Default 2.

min_frag_duration

Specify the minimum fragment duration (in microseconds). Default 5000000.

remove_at_exit

Specify whether to remove all fragments when finished. Default 0 (do not remove).

### 21.76 streamhash# TOC

Per stream hash testing format.

This muxer computes and prints a cryptographic hash of all the input frames, on a per-stream basis. This can be used for equality checks without having to do a complete binary comparison.

By default audio frames are converted to signed 16-bit raw audio and video frames to raw video before computing the hash, but the output of explicit conversions to other codecs can also be used. Timestamps are ignored. It uses the SHA-256 cryptographic hash function by default, but supports several other algorithms.

The output of the muxer consists of one line per stream of the form: streamindex,streamtype,algo=hash, where streamindex is the index of the mapped stream, streamtype is a single character indicating the type of stream, algo is a short string representing the hash function used, and hash is a hexadecimal number representing the computed hash.

hash algorithm

Use the cryptographic hash function specified by the string algorithm. Supported values include MD5, murmur3, RIPEMD128, RIPEMD160, RIPEMD256, RIPEMD320, SHA160, SHA224, SHA256 (default), SHA512/224, SHA512/256, SHA384, SHA512, CRC32 and adler32.

#### 21.76.1 Examples# TOC

To compute the SHA-256 hash of the input converted to raw audio and video, and store it in the file out.sha256:

```
ffmpeg -i INPUT -f streamhash out.sha256

```

To print an MD5 hash to stdout use the command:

```
ffmpeg -i INPUT -f streamhash -hash md5 -

```

See also the hash and framehash muxers.

### 21.77 tee# TOC

The tee muxer can be used to write the same data to several outputs, such as files or streams. It can be used, for example, to stream a video over a network and save it to disk at the same time.

It is different from specifying several outputs to the ffmpeg command-line tool. With the tee muxer, the audio and video data will be encoded only once. With conventional multiple outputs, multiple encoding operations in parallel are initiated, which can be a very expensive process. The tee muxer is not useful when using the libavformat API directly because it is then possible to feed the same packets to several muxers directly.

Since the tee muxer does not represent any particular output format, ffmpeg cannot auto-select output streams. So all streams intended for output must be specified using -map. See the examples below.

Some encoders may need different options depending on the output format; the auto-detection of this can not work with the tee muxer, so they need to be explicitly specified. The main example is the global_header flag.

The slave outputs are specified in the file name given to the muxer, separated by ’|’. If any of the slave name contains the ’|’ separator, leading or trailing spaces or any special character, those must be escaped (see the "Quoting and escaping" section in the ffmpeg-utils(1) manual).

#### 21.77.1 Options# TOC

use_fifo bool

If set to 1, slave outputs will be processed in separate threads using the fifo muxer. This allows to compensate for different speed/latency/reliability of outputs and setup transparent recovery. By default this feature is turned off.

fifo_options

Options to pass to fifo pseudo-muxer instances. See fifo.

Muxer options can be specified for each slave by prepending them as a list of key=value pairs separated by ’:’, between square brackets. If the options values contain a special character or the ’:’ separator, they must be escaped; note that this is a second level escaping.

The following special options are also recognized:

f

Specify the format name. Required if it cannot be guessed from the output URL.

bsfs[/spec]

Specify a list of bitstream filters to apply to the specified output.

It is possible to specify to which streams a given bitstream filter applies, by appending a stream specifier to the option separated by /. spec must be a stream specifier (see Format stream specifiers).

If the stream specifier is not specified, the bitstream filters will be applied to all streams in the output. This will cause that output operation to fail if the output contains streams to which the bitstream filter cannot be applied e.g. h264_mp4toannexb being applied to an output containing an audio stream.

Options for a bitstream filter must be specified in the form of opt=value.

Several bitstream filters can be specified, separated by ",".

use_fifo bool

This allows to override tee muxer use_fifo option for individual slave muxer.

fifo_options

This allows to override tee muxer fifo_options for individual slave muxer. See fifo.

select

Select the streams that should be mapped to the slave output, specified by a stream specifier. If not specified, this defaults to all the mapped streams. This will cause that output operation to fail if the output format does not accept all mapped streams.

You may use multiple stream specifiers separated by commas (,) e.g.: a:0,v

onfail

Specify behaviour on output failure. This can be set to either abort (which is default) or ignore. abort will cause whole process to fail in case of failure on this slave output. ignore will ignore failure on this output, so other outputs will continue without being affected.

#### 21.77.2 Examples# TOC

- Encode something and both archive it in a WebM file and stream it as MPEG-TS over UDP:

```
ffmpeg -i ... -c:v libx264 -c:a mp2 -f tee -map 0:v -map 0:a
  "archive-20121107.mkv|[f=mpegts]udp://10.0.1.255:1234/"

```

- As above, but continue streaming even if output to local file fails (for example local drive fills up):

```
ffmpeg -i ... -c:v libx264 -c:a mp2 -f tee -map 0:v -map 0:a
  "[onfail=ignore]archive-20121107.mkv|[f=mpegts]udp://10.0.1.255:1234/"

```

- Use ffmpeg to encode the input, and send the output to three different destinations. The dump_extra bitstream filter is used to add extradata information to all the output video keyframes packets, as requested by the MPEG-TS format. The select option is applied to out.aac in order to make it contain only audio packets.

```
ffmpeg -i ... -map 0 -flags +global_header -c:v libx264 -c:a aac
       -f tee "[bsfs/v=dump_extra=freq=keyframe]out.ts|[movflags=+faststart]out.mp4|[select=a]out.aac"

```

- As above, but select only stream a:1 for the audio output. Note that a second level escaping must be performed, as ":" is a special character used to separate options.

```
ffmpeg -i ... -map 0 -flags +global_header -c:v libx264 -c:a aac
       -f tee "[bsfs/v=dump_extra=freq=keyframe]out.ts|[movflags=+faststart]out.mp4|[select=\'a:1\']out.aac"

```

### 21.78 wav# TOC

RIFF Wave Audio muxer.

#### 21.78.1 Options# TOC

rf64 mode

Choose whether to use the RF64 file format instead of RIFF. RF64 allows files larger than 4 gigabytes, but RF64 support is not as universal as RIFF.

The following modes are recognized:

‘auto’

Start writing a standard RIFF file to retain compatibility with non-RF64-aware software, but switch to RF64 if the output file grows larger than 4 gigabytes. Reserves a small amount of extra space in the header using a JUNK chunk, which should be ignored by all compliant RIFF readers, but some extremely simplistic WAV readers may be confused by this.

‘always’

Always use the RF64 format regardless of file size. The output file will only be readable by RF64-compatible software and is no longer a standard RIFF WAVE file.

‘never’

Always use plain RIFF, never RF64. This mode is the most compatible with legacy software, but if the output file grows beyond 4 gigabytes, the 32-bit size field in the data chunk will no longer be able to correctly represent the size, and most audio software will not be able to read some or all of the data. (The wav demuxer’s ignore_length option can be used to recover such a file.) This is the default mode.

write_bext bool

Add a Broadcast Wave Format BEXT chunk containing extended audio metadata if enabled. Defaults to false.

write_peak mode

Add a Peak Envelope chunk (EBU Tech 3285 Supplement 3) if enabled. Defaults to off.

‘off’

Do not add the Peak Envelope chunk.

‘on’

Add the Peak Envelope chunk, calculating the peak values based on the peak_block_size, peak_format, and peak_ppv options.

‘only’

Like on, but skip writing the actual audio data (no data chunk will be written to the file; only the Peak Envelope and other metadata chunks will be written.)

peak_block_size int

Number of audio samples used to generate each peak frame, up to 65536. Default is 256.

peak_format format

The format of the peak envelope data (1: uint8, 2: uint16). Default is 2 (uint16).

peak_ppv int

Number of peak points per peak value (1 or 2). Default is 2.

### 21.79 webm_chunk# TOC

WebM Live Chunk Muxer.

This muxer writes out WebM headers and chunks as separate files which can be consumed by clients that support WebM Live streams via DASH.

#### 21.79.1 Options# TOC

This muxer supports the following options:

chunk_start_index

Index of the first chunk (defaults to 0).

header

Filename of the header where the initialization data will be written.

audio_chunk_duration

Duration of each audio chunk in milliseconds (defaults to 5000).

#### 21.79.2 Example# TOC

```
ffmpeg -f v4l2 -i /dev/video0 \
       -f alsa -i hw:0 \
       -map 0:0 \
       -c:v libvpx-vp9 \
       -s 640x360 -keyint_min 30 -g 30 \
       -f webm_chunk \
       -header webm_live_video_360.hdr \
       -chunk_start_index 1 \
       webm_live_video_360_%d.chk \
       -map 1:0 \
       -c:a libvorbis \
       -b:a 128k \
       -f webm_chunk \
       -header webm_live_audio_128.hdr \
       -chunk_start_index 1 \
       -audio_chunk_duration 1000 \
       webm_live_audio_128_%d.chk

```

### 21.80 webm_dash_manifest# TOC

WebM DASH Manifest muxer.

This muxer implements the WebM DASH Manifest specification to generate the DASH manifest XML. It also supports manifest generation for DASH live streams.

For more information see:

- WebM DASH Specification: https://sites.google.com/a/webmproject.org/wiki/adaptive-streaming/webm-dash-specification

- ISO DASH Specification: http://standards.iso.org/ittf/PubliclyAvailableStandards/c065274_ISO_IEC_23009-1_2014.zip

#### 21.80.1 Options# TOC

This muxer supports the following options:

adaptation_sets

This option has the following syntax: "id=x,streams=a,b,c id=y,streams=d,e" where x and y are the unique identifiers of the adaptation sets and a,b,c,d and e are the indices of the corresponding audio and video streams. Any number of adaptation sets can be added using this option.

live

Set this to 1 to create a live stream DASH Manifest. Default: 0.

chunk_start_index

Start index of the first chunk. This will go in the ‘startNumber’ attribute of the ‘SegmentTemplate’ element in the manifest. Default: 0.

chunk_duration_ms

Duration of each chunk in milliseconds. This will go in the ‘duration’ attribute of the ‘SegmentTemplate’ element in the manifest. Default: 1000.

utc_timing_url

URL of the page that will return the UTC timestamp in ISO format. This will go in the ‘value’ attribute of the ‘UTCTiming’ element in the manifest. Default: None.

time_shift_buffer_depth

Smallest time (in seconds) shifting buffer for which any Representation is guaranteed to be available. This will go in the ‘timeShiftBufferDepth’ attribute of the ‘MPD’ element. Default: 60.

minimum_update_period

Minimum update period (in seconds) of the manifest. This will go in the ‘minimumUpdatePeriod’ attribute of the ‘MPD’ element. Default: 0.

#### 21.80.2 Example# TOC

```
ffmpeg -f webm_dash_manifest -i video1.webm \
       -f webm_dash_manifest -i video2.webm \
       -f webm_dash_manifest -i audio1.webm \
       -f webm_dash_manifest -i audio2.webm \
       -map 0 -map 1 -map 2 -map 3 \
       -c copy \
       -f webm_dash_manifest \
       -adaptation_sets "id=0,streams=0,1 id=1,streams=2,3" \
       manifest.xml

```

### 21.81 whip# TOC

WebRTC (Real-Time Communication) muxer that supports sub-second latency streaming according to the WHIP (WebRTC-HTTP ingestion protocol) specification.

This is an experimental feature.

It uses HTTP as a signaling protocol to exchange SDP capabilities and ICE lite candidates. Then, it uses STUN binding requests and responses to establish a session over UDP. Subsequently, it initiates a DTLS handshake to exchange the SRTP encryption keys. Lastly, it splits video and audio frames into RTP packets and encrypts them using SRTP.

Ensure that you use H.264 without B frames and Opus for the audio codec. For example, to convert an input file with ffmpeg to WebRTC:

```
ffmpeg -re -i input.mp4 -acodec libopus -ar 48000 -ac 2 \
  -vcodec libx264 -profile:v baseline -tune zerolatency -threads 1 -bf 0 \
  -f whip "http://localhost:1985/rtc/v1/whip/?app=live&stream=livestream"

```

For this example, we have employed low latency options, resulting in an end-to-end latency of approximately 150ms.

#### 21.81.1 Options# TOC

This muxer supports the following options:

handshake_timeout integer

Set the timeout in milliseconds for ICE and DTLS handshake. Default value is 5000.

timeout integer

Set timeout in seconds for socket I/O operations. Applicable only for HTTP output. Default value is -1.

pkt_size integer

Set the maximum size, in bytes, of RTP packets that send out. Default value is 1200.

ts_buffer_size integer

Set the buffer size, in bytes, of underlying protocol. Default value is -1(auto). The UDP auto selects a reasonable value.

whip_flags flags

Possible values:

‘dtls_active’

The muxer will try to set dtls active role and send the first client hello.

rtp_history integer

Set the number of RTP history items to store. Default value is 512.

authorization string

The optional Bearer token for WHIP Authorization.

cert_file string

The optional certificate file path for DTLS.

key_file string

The optional private key file path for DTLS.

## 22 Metadata# TOC

FFmpeg is able to dump metadata from media files into a simple UTF-8-encoded INI-like text file and then load it back using the metadata muxer/demuxer.

The file format is as follows:

-  A file consists of a header and a number of metadata tags divided into sections, each on its own line.

-  The header is a ‘;FFMETADATA’ string, followed by a version number (now 1).

-  Metadata tags are of the form ‘key=value’

-  Immediately after header follows global metadata

-  After global metadata there may be sections with per-stream/per-chapter metadata.

-  A section starts with the section name in uppercase (i.e. STREAM or CHAPTER) in brackets (‘[’, ‘]’) and ends with next section or end of file.

-  At the beginning of a chapter section there may be an optional timebase to be used for start/end values. It must be in form ‘TIMEBASE=num/den’, where num and den are integers. If the timebase is missing then start/end times are assumed to be in nanoseconds.
Next a chapter section must contain chapter start and end times in form ‘START=num’, ‘END=num’, where num is a positive integer.

-  Empty lines and lines starting with ‘;’ or ‘#’ are ignored.

-  Metadata keys or values containing special characters (‘=’, ‘;’, ‘#’, ‘\’ and a newline) must be escaped with a backslash ‘\’.

-  Note that whitespace in metadata (e.g. ‘foo = bar’) is considered to be a part of the tag (in the example above key is ‘foo ’, value is ‘ bar’).

A ffmetadata file might look like this:

```
;FFMETADATA1
title=bike\\shed
;this is a comment
artist=FFmpeg troll team

[CHAPTER]
TIMEBASE=1/1000
START=0
#chapter ends at 0:01:00
END=60000
title=chapter \#1
[STREAM]
title=multi\
line

```

By using the ffmetadata muxer and demuxer it is possible to extract metadata from an input file to an ffmetadata file, and then transcode the file into an output file with the edited ffmetadata file.

Extracting an ffmetadata file with ffmpeg goes as follows:

```
ffmpeg -i INPUT -f ffmetadata FFMETADATAFILE

```

Reinserting edited metadata information from the FFMETADATAFILE file can be done as:

```
ffmpeg -i INPUT -i FFMETADATAFILE -map_metadata 1 -codec copy OUTPUT

```

## 23 Protocol Options# TOC

The libavformat library provides some generic global options, which can be set on all the protocols. In addition each protocol may support so-called private options, which are specific for that component.

Options may be set by specifying -option value in the FFmpeg tools, or by setting the value explicitly in the AVFormatContext options or using the libavutil/opt.h API for programmatic use.

The list of supported options follows:

protocol_whitelist list (input)

Set a ","-separated list of allowed protocols. "ALL" matches all protocols. Protocols prefixed by "-" are disabled. All protocols are allowed by default but protocols used by an another protocol (nested protocols) are restricted to a per protocol subset.

## 24 Protocols# TOC

Protocols are configured elements in FFmpeg that enable access to resources that require specific protocols.

When you configure your FFmpeg build, all the supported protocols are enabled by default. You can list all available ones using the configure option "–list-protocols".

You can disable all the protocols using the configure option "–disable-protocols", and selectively enable a protocol using the option "–enable-protocol=PROTOCOL", or you can disable a particular protocol using the option "–disable-protocol=PROTOCOL".

The option "-protocols" of the ff* tools will display the list of supported protocols.

All protocols accept the following options:

rw_timeout

Maximum time to wait for (network) read/write operations to complete, in microseconds.

A description of the currently available protocols follows.

### 24.1 amqp# TOC

Advanced Message Queueing Protocol (AMQP) version 0-9-1 is a broker based publish-subscribe communication protocol.

FFmpeg must be compiled with –enable-librabbitmq to support AMQP. A separate AMQP broker must also be run. An example open-source AMQP broker is RabbitMQ.

After starting the broker, an FFmpeg client may stream data to the broker using the command:

```
ffmpeg -re -i input -f mpegts amqp://[[user]:[password]@]hostname[:port][/vhost]

```

Where hostname and port (default is 5672) is the address of the broker. The client may also set a user/password for authentication. The default for both fields is "guest". Name of virtual host on broker can be set with vhost. The default value is "/".

Multiple subscribers may stream from the broker using the command:

```
ffplay amqp://[[user]:[password]@]hostname[:port][/vhost]

```

In RabbitMQ all data published to the broker flows through a specific exchange, and each subscribing client has an assigned queue/buffer. When a packet arrives at an exchange, it may be copied to a client’s queue depending on the exchange and routing_key fields.

The following options are supported:

exchange

Sets the exchange to use on the broker. RabbitMQ has several predefined exchanges: "amq.direct" is the default exchange, where the publisher and subscriber must have a matching routing_key; "amq.fanout" is the same as a broadcast operation (i.e. the data is forwarded to all queues on the fanout exchange independent of the routing_key); and "amq.topic" is similar to "amq.direct", but allows for more complex pattern matching (refer to the RabbitMQ documentation).

routing_key

Sets the routing key. The default value is "amqp". The routing key is used on the "amq.direct" and "amq.topic" exchanges to decide whether packets are written to the queue of a subscriber.

pkt_size

Maximum size of each packet sent/received to the broker. Default is 131072. Minimum is 4096 and max is any large value (representable by an int). When receiving packets, this sets an internal buffer size in FFmpeg. It should be equal to or greater than the size of the published packets to the broker. Otherwise the received message may be truncated causing decoding errors.

connection_timeout

The timeout in seconds during the initial connection to the broker. The default value is rw_timeout, or 5 seconds if rw_timeout is not set.

delivery_mode mode

Sets the delivery mode of each message sent to broker. The following values are accepted:

‘persistent’

Delivery mode set to "persistent" (2). This is the default value. Messages may be written to the broker’s disk depending on its setup.

‘non-persistent’

Delivery mode set to "non-persistent" (1). Messages will stay in broker’s memory unless the broker is under memory pressure.

### 24.2 async# TOC

Asynchronous data filling wrapper for input stream.

Fill data in a background thread, to decouple I/O operation from demux thread.

```
async:URL
async:http://host/resource
async:cache:http://host/resource

```

### 24.3 bluray# TOC

Read BluRay playlist.

The accepted options are:

angle

BluRay angle

chapter

Start chapter (1...N)

playlist

Playlist to read (BDMV/PLAYLIST/?????.mpls)

Examples:

Read longest playlist from BluRay mounted to /mnt/bluray:

```
bluray:/mnt/bluray

```

Read angle 2 of playlist 4 from BluRay mounted to /mnt/bluray, start from chapter 2:

```
-playlist 4 -angle 2 -chapter 2 bluray:/mnt/bluray

```

### 24.4 cache# TOC

Caching wrapper for input stream.

Cache the input stream to temporary file. It brings seeking capability to live streams.

The accepted options are:

read_ahead_limit

Amount in bytes that may be read ahead when seeking isn’t supported. Range is -1 to INT_MAX. -1 for unlimited. Default is 65536.

URL Syntax is

```
cache:URL

```

### 24.5 concat# TOC

Physical concatenation protocol.

Read and seek from many resources in sequence as if they were a unique resource.

A URL accepted by this protocol has the syntax:

```
concat:URL1|URL2|...|URLN

```

where URL1, URL2, ..., URLN are the urls of the resource to be concatenated, each one possibly specifying a distinct protocol.

For example to read a sequence of files split1.mpeg, split2.mpeg, split3.mpeg with ffplay use the command:

```
ffplay concat:split1.mpeg\|split2.mpeg\|split3.mpeg

```

Note that you may need to escape the character "|" which is special for many shells.

### 24.6 concatf# TOC

Physical concatenation protocol using a line break delimited list of resources.

Read and seek from many resources in sequence as if they were a unique resource.

A URL accepted by this protocol has the syntax:

```
concatf:URL

```

where URL is the url containing a line break delimited list of resources to be concatenated, each one possibly specifying a distinct protocol. Special characters must be escaped with backslash or single quotes. See the "Quoting and escaping" section in the ffmpeg-utils(1) manual.

For example to read a sequence of files split1.mpeg, split2.mpeg, split3.mpeg listed in separate lines within a file split.txt with ffplay use the command:

```
ffplay concatf:split.txt

```

Where split.txt contains the lines:

```
split1.mpeg
split2.mpeg
split3.mpeg

```

### 24.7 crypto# TOC

AES-encrypted stream reading protocol.

The accepted options are:

key

Set the AES decryption key binary block from given hexadecimal representation.

iv

Set the AES decryption initialization vector binary block from given hexadecimal representation.

Accepted URL formats:

```
crypto:URL
crypto+URL

```

### 24.8 data# TOC

Data in-line in the URI. See http://en.wikipedia.org/wiki/Data_URI_scheme.

For example, to convert a GIF file given inline with ffmpeg:

```
ffmpeg -i "data:image/gif;base64,R0lGODdhCAAIAMIEAAAAAAAA//8AAP//AP///////////////ywAAAAACAAIAAADF0gEDLojDgdGiJdJqUX02iB4E8Q9jUMkADs=" smiley.png

```

### 24.9 fd# TOC

File descriptor access protocol.

The accepted syntax is:

```
fd: -fd file_descriptor

```

If fd is not specified, by default the stdout file descriptor will be used for writing, stdin for reading. Unlike the pipe protocol, fd protocol has seek support if it corresponding to a regular file. fd protocol doesn’t support pass file descriptor via URL for security.

This protocol accepts the following options:

blocksize

Set I/O operation maximum block size, in bytes. Default value is INT_MAX, which results in not limiting the requested block size. Setting this value reasonably low improves user termination request reaction time, which is valuable if data transmission is slow.

fd

Set file descriptor.

### 24.10 file# TOC

File access protocol.

Read from or write to a file.

A file URL can have the form:

```
file:filename

```

where filename is the path of the file to read.

An URL that does not have a protocol prefix will be assumed to be a file URL. Depending on the build, an URL that looks like a Windows path with the drive letter at the beginning will also be assumed to be a file URL (usually not the case in builds for unix-like systems).

For example to read from a file input.mpeg with ffmpeg use the command:

```
ffmpeg -i file:input.mpeg output.mpeg

```

This protocol accepts the following options:

truncate

Truncate existing files on write, if set to 1. A value of 0 prevents truncating. Default value is 1.

blocksize

Set I/O operation maximum block size, in bytes. Default value is INT_MAX, which results in not limiting the requested block size. Setting this value reasonably low improves user termination request reaction time, which is valuable for files on slow medium.

follow

If set to 1, the protocol will retry reading at the end of the file, allowing reading files that still are being written. In order for this to terminate, you either need to use the rw_timeout option, or use the interrupt callback (for API users). Setting this option also ignores the file size reported by the file system.

seekable

Controls if seekability is advertised on the file. 0 means non-seekable, -1 means auto (seekable for normal files, non-seekable for named pipes).

Many demuxers handle seekable and non-seekable resources differently, overriding this might speed up opening certain files at the cost of losing some features (e.g. accurate seeking).

pkt_size

Set the maximum packet size used for file I/O. A smaller value may reduce memory usage. A higher value may increase throughput especially with networked filesystems.

For reading, if explicitly set, it overrides the default internal buffer size (32 KB) and limits the maximum amount of data read per operation.

For writing, this sets the size of each write operation. The default is 256 KB for regular files, 32 KB otherwise.

### 24.11 ftp# TOC

FTP (File Transfer Protocol).

Read from or write to remote resources using FTP protocol.

Following syntax is required.

```
ftp://[user[:password]@]server[:port]/path/to/remote/resource.mpeg

```

This protocol accepts the following options.

timeout

Set timeout in microseconds of socket I/O operations used by the underlying low level operation. By default it is set to -1, which means that the timeout is not specified.

ftp-user

Set a user to be used for authenticating to the FTP server. This is overridden by the user in the FTP URL.

ftp-password

Set a password to be used for authenticating to the FTP server. This is overridden by the password in the FTP URL, or by ftp-anonymous-password if no user is set.

ftp-anonymous-password

Password used when login as anonymous user. Typically an e-mail address should be used.

ftp-write-seekable

Control seekability of connection during encoding. If set to 1 the resource is supposed to be seekable, if set to 0 it is assumed not to be seekable. Default value is 0.

NOTE: Protocol can be used as output, but it is recommended to not do it, unless special care is taken (tests, customized server configuration etc.). Different FTP servers behave in different way during seek operation. ff* tools may produce incomplete content due to server limitations.

### 24.12 gopher# TOC

Gopher protocol.

### 24.13 gophers# TOC

Gophers protocol.

The Gopher protocol with TLS encapsulation.

### 24.14 handle# TOC

Windows handle access protocol.

The accepted syntax is:

```
handle: -handle handle

```

If handle is not specified, by default the output handle will be used for writing, input handle for reading. This protocol is only available on Windows. It has seek support if the handle corresponds to a regular file. It doesn’t support passing the handle via URL.

This protocol accepts the following options:

blocksize

Set I/O operation maximum block size, in bytes. Default value is INT_MAX, which results in not limiting the requested block size. Setting this value reasonably low improves user termination request reaction time, which is valuable if data transmission is slow.

handle

Set Windows handle.

The supplied handle must already be valid in the calling process. When launching ffmpeg, arrange for the child process to inherit the handle before passing its numeric value with handle. Handles opened with FILE_FLAG_OVERLAPPED are not supported. Closing the protocol does not close the caller’s original handle.

### 24.15 http# TOC

HTTP (Hyper Text Transfer Protocol).

This protocol accepts the following options:

seekable

Control seekability of connection. If set to 1 the resource is supposed to be seekable, if set to 0 it is assumed not to be seekable, if set to -1 it will try to autodetect if it is seekable. Default value is -1.

chunked_post

If set to 1 use chunked Transfer-Encoding for posts, default is 1.

http_proxy

set HTTP proxy to tunnel through e.g. http://example.com:1234

headers

Set custom HTTP headers, can override built in default headers. The value must be a string encoding the headers.

content_type

Set a specific content type for the POST messages or for listen mode.

user_agent

Override the User-Agent header. If not specified the protocol will use a string describing the libavformat build. ("Lavf/<version>")

referer

Set the Referer header. Include ’Referer: URL’ header in HTTP request.

multiple_requests

Force persistent connections if set to 1, or disable if 0. Default is -1, which means auto (implies keep-alive when using -request_size or -initial_request_size).

request_size

Limit the size of requests made. This is useful for some pathological servers that throttle unbounded range requests, as well as when expecting to seek frequently. Disabled (set to 0) by default.

Note that if enabling this option, it’s strongly recommended to also set short_seek_size to the same value or higher. Doing so allows FFmpeg to reuse a single HTTP connection wherever possible.

initial_request_size

Limit the size of initial requests. Similar to request_size, but only used during initial format parsing. Useful for formats like MXF or MOV that require frequent seeks during header parsing. Lasts until the demuxer makes a read request larger than this size (without a seek in between), after which the implementation will continue using requests as usual. Disabled (set to 0) by default.

Note that if enabling this option, it’s strongly recommended to also enable the multiple_requests option, as well as setting short_seek_size to the same value or higher.

post_data

Set custom HTTP post data.

mime_type

Export the MIME type.

http_version

Exports the HTTP response version number. Usually "1.0" or "1.1".

cookies

Set the cookies to be sent in future requests. The format of each cookie is the same as the value of a Set-Cookie HTTP response field. Multiple cookies can be delimited by a newline character. A cookie without a Domain attribute is only sent to the host of the URL it is set for.

icy

If set to 1 request ICY (SHOUTcast) metadata from the server. If the server supports this, the metadata has to be retrieved by the application by reading the icy_metadata_headers and icy_metadata_packet options. The default is 1.

icy_metadata_headers

If the server supports ICY metadata, this contains the ICY-specific HTTP reply headers, separated by newline characters.

icy_metadata_packet

If the server supports ICY metadata, and icy was set to 1, this contains the last non-empty metadata packet sent by the server. It should be polled in regular intervals by applications interested in mid-stream metadata updates.

metadata

Set an exported dictionary containing Icecast metadata from the bitstream, if present. Only useful with the C API.

auth_type

Set HTTP authentication type. No option for Digest, since this method requires getting nonce parameters from the server first and can’t be used straight away like Basic.

none

Choose the HTTP authentication type automatically. This is the default.

basic

Choose the HTTP basic authentication.

Basic authentication sends a Base64-encoded string that contains a user name and password for the client. Base64 is not a form of encryption and should be considered the same as sending the user name and password in clear text (Base64 is a reversible encoding). If a resource needs to be protected, strongly consider using an authentication scheme other than basic authentication. HTTPS/TLS should be used with basic authentication. Without these additional security enhancements, basic authentication should not be used to protect sensitive or valuable information.

send_expect_100

Send an Expect: 100-continue header for POST. If set to 1 it will send, if set to 0 it won’t, if set to -1 it will try to send if it is applicable. Default value is -1.

location

An exported dictionary containing the content location. Only useful with the C API.

offset

Set initial byte offset.

end_offset

Try to limit the request to bytes preceding this offset.

method

When used as a client option it sets the HTTP method for the request.

When used as a server option it sets the HTTP method that is going to be expected from the client(s). If the expected and the received HTTP method do not match the client will be given a Bad Request response. When unset the HTTP method is not checked for now. This will be replaced by autodetection in the future.

reconnect

Reconnect automatically when disconnected before EOF is hit.

reconnect_at_eof

If set then eof is treated like an error and causes reconnection, this is useful for live / endless streams. This does not apply to the deliberately established end of a resource whose complete size is unknown, i.e. when a ranged request past the end is answered with 416. Such an end is reported as a clean EOF and is not retried, unless reconnect_on_http_error lists 416 by number.

reconnect_on_network_error

Reconnect automatically in case of TCP/TLS errors during connect.

reconnect_on_http_error

A comma separated list of HTTP status codes to reconnect on. The list can include specific status codes (e.g. ’503’) or the strings ’4xx’ / ’5xx’. A 416 that ends a read or a seek past the end of a resource whose complete size is unknown is reported as EOF. It is retried first only if 416 is listed by number, for example to read a resource that is still being written. ’4xx’ does not cover it.

reconnect_streamed

If set then even streamed/non seekable streams will be reconnected on errors.

reconnect_delay_max

Set the maximum delay in seconds after which to give up reconnecting.

reconnect_max_retries

Set the maximum number of times to retry a connection. Default unset.

reconnect_delay_total_max

Set the maximum total delay in seconds after which to give up reconnecting.

respect_retry_after

If enabled, and a Retry-After header is encountered, its requested reconnection delay will be honored, rather than using exponential backoff. Useful for 429 and 503 errors. Default enabled.

listen

If set to 1 enables experimental HTTP server. This can be used to send data when used as an output option, or read data from a client with HTTP POST when used as an input option. If set to 2 enables experimental multi-client HTTP server. This is not yet implemented in ffmpeg.c and thus must not be used as a command line option.

```
# Server side (sending):
ffmpeg -i somefile.ogg -c copy -listen 1 -f ogg http://server:port

# Client side (receiving):
ffmpeg -i http://server:port -c copy somefile.ogg

# Client can also be done with wget:
wget http://server:port -O somefile.ogg

# Server side (receiving):
ffmpeg -listen 1 -i http://server:port -c copy somefile.ogg

# Client side (sending):
ffmpeg -i somefile.ogg -chunked_post 0 -c copy -f ogg http://server:port

# Client can also be done with wget:
wget --post-file=somefile.ogg http://server:port

```

resource

The resource requested by a client, when the experimental HTTP server is in use.

reply_code

The HTTP code returned to the client, when the experimental HTTP server is in use.

short_seek_size

Set the threshold, in bytes, for when a readahead should be preferred over a seek and new HTTP request. This is useful, for example, to make sure the same connection is used for reading large video packets with small audio packets in between.

#### 24.15.1 HTTP Cookies# TOC

Some HTTP requests will be denied unless cookie values are passed in with the request. The cookies option allows these cookies to be specified. At the very least, each cookie must specify a value. HTTP requests that match both the domain and path will automatically include the cookie value in the HTTP Cookie header field. Multiple cookies can be delimited by a newline.

The required syntax to play a stream specifying a cookie is:

```
ffplay -cookies "nlqptid=nltid=tsn; path=/; domain=somedomain.com;" http://somedomain.com/somestream.m3u8

```

### 24.16 Icecast# TOC

Icecast protocol (stream to Icecast servers)

This protocol accepts the following options:

ice_genre

Set the stream genre.

ice_name

Set the stream name.

ice_description

Set the stream description.

ice_url

Set the stream website URL.

ice_public

Set if the stream should be public. The default is 0 (not public).

user_agent

Override the User-Agent header. If not specified a string of the form "Lavf/<version>" will be used.

password

Set the Icecast mountpoint password.

content_type

Set the stream content type. This must be set if it is different from audio/mpeg.

legacy_icecast

This enables support for Icecast versions < 2.4.0, that do not support the HTTP PUT method but the SOURCE method.

tls

Establish a TLS (HTTPS) connection to Icecast.

```
icecast://[username[:password]@]server:port/mountpoint

```

### 24.17 ipfs# TOC

InterPlanetary File System (IPFS) protocol support. One can access files stored on the IPFS network through so-called gateways. These are http(s) endpoints. This protocol wraps the IPFS native protocols (ipfs:// and ipns://) to be sent to such a gateway. Users can (and should) host their own node which means this protocol will use one’s local gateway to access files on the IPFS network.

This protocol accepts the following options:

gateway

Defines the gateway to use. When not set, the protocol will first try locating the local gateway by looking at $IPFS_GATEWAY, $IPFS_PATH and $HOME/.ipfs/, in that order.

One can use this protocol in 2 ways. Using IPFS:

```
ffplay ipfs://<hash>

```

Or the IPNS protocol (IPNS is mutable IPFS):

```
ffplay ipns://<hash>

```

### 24.18 mmst# TOC

MMS (Microsoft Media Server) protocol over TCP.

### 24.19 mmsh# TOC

MMS (Microsoft Media Server) protocol over HTTP.

The required syntax is:

```
mmsh://server[:port][/app][/playpath]

```

### 24.20 md5# TOC

MD5 output protocol.

Computes the MD5 hash of the data to be written, and on close writes this to the designated output or stdout if none is specified. It can be used to test muxers without writing an actual file.

Some examples follow.

```
# Write the MD5 hash of the encoded AVI file to the file output.avi.md5.
ffmpeg -i input.flv -f avi -y md5:output.avi.md5

# Write the MD5 hash of the encoded AVI file to stdout.
ffmpeg -i input.flv -f avi -y md5:

```

Note that some formats (typically MOV) require the output protocol to be seekable, so they will fail with the MD5 output protocol.

### 24.21 pipe# TOC

UNIX pipe access protocol.

Read and write from UNIX pipes.

The accepted syntax is:

```
pipe:[number]

```

If fd isn’t specified, number is the number corresponding to the file descriptor of the pipe (e.g. 0 for stdin, 1 for stdout, 2 for stderr). If number is not specified, by default the stdout file descriptor will be used for writing, stdin for reading.

For example to read from stdin with ffmpeg:

```
cat test.wav | ffmpeg -i pipe:0
# ...this is the same as...
cat test.wav | ffmpeg -i pipe:

```

For writing to stdout with ffmpeg:

```
ffmpeg -i test.wav -f avi pipe:1 | cat > test.avi
# ...this is the same as...
ffmpeg -i test.wav -f avi pipe: | cat > test.avi

```

This protocol accepts the following options:

blocksize

Set I/O operation maximum block size, in bytes. Default value is INT_MAX, which results in not limiting the requested block size. Setting this value reasonably low improves user termination request reaction time, which is valuable if data transmission is slow.

fd

Set file descriptor.

Note that some formats (typically MOV), require the output protocol to be seekable, so they will fail with the pipe output protocol.

### 24.22 prompeg# TOC

Pro-MPEG Code of Practice #3 Release 2 FEC protocol.

The Pro-MPEG CoP#3 FEC is a 2D parity-check forward error correction mechanism for MPEG-2 Transport Streams sent over RTP.

This protocol must be used in conjunction with the rtp_mpegts muxer and the rtp protocol.

The required syntax is:

```
-f rtp_mpegts -fec prompeg=option=val... rtp://hostname:port

```

The destination UDP ports are port + 2 for the column FEC stream and port + 4 for the row FEC stream.

This protocol accepts the following options:

l=n

The number of columns (4-20, LxD <= 100)

d=n

The number of rows (4-20, LxD <= 100)

Example usage:

```
-f rtp_mpegts -fec prompeg=l=8:d=4 rtp://hostname:port

```

### 24.23 rist# TOC

Reliable Internet Streaming Transport protocol

The accepted options are:

rist_profile

Supported values:

‘simple’

‘main’

This one is default.

‘advanced’

buffer_size

Set internal RIST buffer size in milliseconds for retransmission of data. Default value is 0 which means the librist default (1 sec). Maximum value is 30 seconds.

fifo_size

Size of the librist receiver output fifo in number of packets. This must be a power of 2. Defaults to 8192 (vs the librist default of 1024).

overrun_nonfatal=1|0

Survive in case of librist fifo buffer overrun. Default value is 0.

pkt_size

Set maximum packet size for sending data. 1316 by default.

log_level

Set loglevel for RIST logging messages. You only need to set this if you explicitly want to enable debug level messages or packet loss simulation, otherwise the regular loglevel is respected.

secret

Set override of encryption secret, by default is unset.

encryption

Set encryption type, by default is disabled. Acceptable values are 128 and 256.

### 24.24 rtmp# TOC

Real-Time Messaging Protocol.

The Real-Time Messaging Protocol (RTMP) is used for streaming multimedia content across a TCP/IP network.

The required syntax is:

```
rtmp://[username:password@]server[:port][/app][/instance][/playpath]

```

The accepted parameters are:

username

An optional username (mostly for publishing).

password

An optional password (mostly for publishing).

server

The address of the RTMP server.

port

The number of the TCP port to use (by default is 1935).

app

It is the name of the application to access. It usually corresponds to the path where the application is installed on the RTMP server (e.g. /ondemand/, /flash/live/, etc.). You can override the value parsed from the URI through the rtmp_app option, too.

playpath

It is the path or name of the resource to play with reference to the application specified in app, may be prefixed by "mp4:". You can override the value parsed from the URI through the rtmp_playpath option, too.

listen

Act as a server, listening for an incoming connection.

timeout

Maximum time to wait for the incoming connection. Implies listen.

Additionally, the following parameters can be set via command line options (or in code via AVOptions):

rtmp_app

Name of application to connect on the RTMP server. This option overrides the parameter specified in the URI.

rtmp_buffer

Set the client buffer time in milliseconds. The default is 3000.

rtmp_conn

Extra arbitrary AMF connection parameters, parsed from a string, e.g. like B:1 S:authMe O:1 NN:code:1.23 NS:flag:ok O:0. Each value is prefixed by a single character denoting the type, B for Boolean, N for number, S for string, O for object, or Z for null, followed by a colon. For Booleans the data must be either 0 or 1 for FALSE or TRUE, respectively. Likewise for Objects the data must be 0 or 1 to end or begin an object, respectively. Data items in subobjects may be named, by prefixing the type with ’N’ and specifying the name before the value (i.e. NB:myFlag:1). This option may be used multiple times to construct arbitrary AMF sequences.

rtmp_enhanced_codecs

Specify the list of codecs the client advertises to support in an enhanced RTMP stream. This option should be set to a comma separated list of fourcc values, like hvc1,av01,vp09 for multiple codecs or hvc1 for only one codec. The specified list will be presented in the "fourCcLive" property of the Connect Command Message.

rtmp_flashver

Version of the Flash plugin used to run the SWF player. The default is LNX 9,0,124,2. (When publishing, the default is FMLE/3.0 (compatible; <libavformat version>).)

rtmp_flush_interval

Number of packets flushed in the same request (RTMPT only). The default is 10.

rtmp_live

Specify that the media is a live stream. No resuming or seeking in live streams is possible. The default value is any, which means the subscriber first tries to play the live stream specified in the playpath. If a live stream of that name is not found, it plays the recorded stream. The other possible values are live and recorded.

rtmp_pageurl

URL of the web page in which the media was embedded. By default no value will be sent.

rtmp_playpath

Stream identifier to play or to publish. This option overrides the parameter specified in the URI.

rtmp_subscribe

Name of live stream to subscribe to. By default no value will be sent. It is only sent if the option is specified or if rtmp_live is set to live.

rtmp_swfhash

SHA256 hash of the decompressed SWF file (32 bytes).

rtmp_swfsize

Size of the decompressed SWF file, required for SWFVerification.

rtmp_swfurl

URL of the SWF player for the media. By default no value will be sent.

rtmp_swfverify

URL to player swf file, compute hash/size automatically.

rtmp_tcurl

URL of the target stream. Defaults to proto://host[:port]/app.

tcp_nodelay=1|0

Set TCP_NODELAY to disable Nagle’s algorithm. Default value is 0.

Remark: Writing to the socket is currently not optimized to minimize system calls and reduces the efficiency / effect of TCP_NODELAY.

tcp_keepalive=1|0

Enable the TCP keepalive mechanism to detect dead peers and help maintain long-lived idle connections. Default value is 0.

Only the basic keepalive option (SO_KEEPALIVE) can be enabled or disabled. Platform-specific tuning parameters such as TCP_KEEPIDLE, TCP_KEEPINTVL, or TCP_KEEPCNT are not configurable and will use the operating system’s default values.

For example to read with ffplay a multimedia resource named "sample" from the application "vod" from an RTMP server "myserver":

```
ffplay rtmp://myserver/vod/sample

```

To publish to a password protected server, passing the playpath and app names separately:

```
ffmpeg -re -i <input> -f flv -rtmp_playpath some/long/path -rtmp_app long/app/name rtmp://username:password@myserver/

```

### 24.25 rtmpe# TOC

Encrypted Real-Time Messaging Protocol.

The Encrypted Real-Time Messaging Protocol (RTMPE) is used for streaming multimedia content within standard cryptographic primitives, consisting of Diffie-Hellman key exchange and HMACSHA256, generating a pair of RC4 keys.

### 24.26 rtmps# TOC

Real-Time Messaging Protocol over a secure SSL connection.

The Real-Time Messaging Protocol (RTMPS) is used for streaming multimedia content across an encrypted connection.

### 24.27 rtmpt# TOC

Real-Time Messaging Protocol tunneled through HTTP.

The Real-Time Messaging Protocol tunneled through HTTP (RTMPT) is used for streaming multimedia content within HTTP requests to traverse firewalls.

### 24.28 rtmpte# TOC

Encrypted Real-Time Messaging Protocol tunneled through HTTP.

The Encrypted Real-Time Messaging Protocol tunneled through HTTP (RTMPTE) is used for streaming multimedia content within HTTP requests to traverse firewalls.

### 24.29 rtmpts# TOC

Real-Time Messaging Protocol tunneled through HTTPS.

The Real-Time Messaging Protocol tunneled through HTTPS (RTMPTS) is used for streaming multimedia content within HTTPS requests to traverse firewalls.

### 24.30 libcurl# TOC

HTTP and HTTPS access through the libcurl library, available as an alternative to the native http protocol when FFmpeg is built with --enable-libcurl. It runs transfers on a dedicated event-loop thread shared per AVFormatContext, so all of a demuxer’s connections (for example HLS segments) reuse libcurl’s connection cache and HTTP/2 and HTTP/3 multiplexing.

The native http protocol stays the default. There are two ways to use libcurl instead:

- Prefix the URL with libcurl: to force it explicitly, for example libcurl:https://example.com/video.mp4.

- Set the prefer_libcurl option to route http:// and https:// URLs through libcurl transparently.

prefer_libcurl

When set to 1, open http(s) URLs with the libcurl protocol instead of the native one. This is a generic IO option rather than a libcurl-specific one, so it also applies on builds without libcurl (where it has no effect). Default is 0.

The libcurl protocol accepts the following options.

user_agent

Override the User-Agent header. Defaults to Lavf/<version>.

referer

Set the Referer header.

headers

Set custom HTTP headers, overriding internal defaults. Multiple headers are separated by newlines.

http_proxy

Set the HTTP proxy to tunnel through.

cookies

Cookies to be sent in future requests, given as newline-delimited Set-Cookie-style values.

location

The actual location of the data after following redirects. This is an output option, read with av_opt_get; demuxers use it to resolve relative URLs.

offset

Initial byte offset of the request. Default is 0.

end_offset

If greater than 0, limit the request to the bytes preceding this offset. Together with offset this requests a sub-range of the resource, as used for HLS byte-range segments.

seekable

Control seekability of the connection. If set to 0 the stream is treated as non-seekable, 1 forces seekable, and -1 (the default) lets it be detected from the server response.

tls_verify

Verify the peer certificate and host name. Enabled by default.

ca_file

Path to a certificate authority bundle that overrides the system store.

cert_file

key_file

Client certificate and private key files for mutual TLS.

connect_timeout

Connection timeout in seconds. 0 (the default) uses libcurl’s own timeout.

max_redirects

Maximum number of redirects to follow. Default is 16.

multiple_requests

Reuse the connection across requests (HTTP keep-alive). Enabled by default; setting it to 0 uses a fresh connection per transfer.

http_version

HTTP version to use: auto (default), 1.0, 1.1, 2, 2tls, 2-prior-knowledge, 3 or 3only.

buffer_size

Size in bytes of the receive buffer. Default is 4 MiB.

request_size

If greater than 0, split a seekable transfer into ranged requests of at most this many bytes each. Default is 0 (a single request).

initial_request_size

Limit the size of initial requests. Similar to request_size, but only used during initial format parsing. Useful for formats like MXF or MOV that require frequent seeks during header parsing. Lasts until the demuxer makes a read request larger than this size (without a seek in between), after which the implementation will continue using requests as usual. Disabled (set to 0) by default.

Note that if enabling this option, it’s strongly recommended to also set short_seek_size to the same value or higher, otherwise the HTTP connection may be closed and recreated for each subsequent initial request.

max_retries

Maximum number of retries after a recoverable error on a seekable transfer. Default is 5.

short_seek_size

Set the threshold, in bytes, for when a readahead should be preferred over a seek and new HTTP request. This is useful, for example, to make sure the same connection is used for reading large video packets with small audio packets in between.

icy

If set to 1 request ICY (SHOUTcast) metadata from the server. If the server supports this, the metadata has to be retrieved by the application by reading the icy_metadata_headers and icy_metadata_packet options. The default is 1.

icy_status

If set to 1 accept the legacy Shoutcast v1 ICY 200 OK status line in place of an HTTP one. Any reply whose status line starts with ICY 200 is then treated as a successful HTTP 200. The default is 1.

icy_metadata_headers

If the server supports ICY metadata, this contains the ICY-specific HTTP reply headers, separated by newline characters.

icy_metadata_packet

If the server supports ICY metadata, and icy was set to 1, this contains the last non-empty metadata packet sent by the server. It should be polled in regular intervals by applications interested in mid-stream metadata updates.

metadata

Set an exported dictionary containing Icecast metadata from the bitstream, if present. Only useful with the C API.

A stream carrying in-band ICY metadata is always treated as non-seekable, since its byte offsets do not address the payload. seekable, request_size and max_retries therefore have no effect on such a stream.

For more information see: https://curl.se/libcurl/.

### 24.31 libsmbclient# TOC

libsmbclient permits one to manipulate CIFS/SMB network resources.

Following syntax is required.

```
smb://[[domain:]user[:password@]]server[/share[/path[/file]]]

```

This protocol accepts the following options.

timeout

Set timeout in milliseconds of socket I/O operations used by the underlying low level operation. By default it is set to -1, which means that the timeout is not specified.

truncate

Truncate existing files on write, if set to 1. A value of 0 prevents truncating. Default value is 1.

workgroup

Set the workgroup used for making connections. By default workgroup is not specified.

For more information see: http://www.samba.org/.

### 24.32 libssh# TOC

Secure File Transfer Protocol via libssh

Read from or write to remote resources using SFTP protocol.

Following syntax is required.

```
sftp://[user[:password]@]server[:port]/path/to/remote/resource.mpeg

```

This protocol accepts the following options.

timeout

Set timeout of socket I/O operations used by the underlying low level operation. By default it is set to -1, which means that the timeout is not specified.

truncate

Truncate existing files on write, if set to 1. A value of 0 prevents truncating. Default value is 1.

private_key

Specify the path of the file containing private key to use during authorization. By default libssh searches for keys in the ~/.ssh/ directory.

verify

Verify the server host key against the known_hosts file before authenticating, if set to 1. Servers that are not in the file, or whose key differs from the one recorded there, are refused. Default value is 1.

Example: Play a file stored on remote server.

```
ffplay sftp://user:password@server_address:22/home/user/resource.mpeg

```

### 24.33 librtmp rtmp, rtmpe, rtmps, rtmpt, rtmpte# TOC

Real-Time Messaging Protocol and its variants supported through librtmp.

Requires the presence of the librtmp headers and library during configuration. You need to explicitly configure the build with "–enable-librtmp". If enabled this will replace the native RTMP protocol.

This protocol provides most client functions and a few server functions needed to support RTMP, RTMP tunneled in HTTP (RTMPT), encrypted RTMP (RTMPE), RTMP over SSL/TLS (RTMPS) and tunneled variants of these encrypted types (RTMPTE, RTMPTS).

The required syntax is:

```
rtmp_proto://server[:port][/app][/playpath] options

```

where rtmp_proto is one of the strings "rtmp", "rtmpt", "rtmpe", "rtmps", "rtmpte", "rtmpts" corresponding to each RTMP variant, and server, port, app and playpath have the same meaning as specified for the RTMP native protocol. options contains a list of space-separated options of the form key=val.

See the librtmp manual page (man 3 librtmp) for more information.

For example, to stream a file in real-time to an RTMP server using ffmpeg:

```
ffmpeg -re -i myfile -f flv rtmp://myserver/live/mystream

```

To play the same stream using ffplay:

```
ffplay "rtmp://myserver/live/mystream live=1"

```

### 24.34 rtp# TOC

Real-time Transport Protocol.

The required syntax for an RTP URL is:

```
rtp://hostname[:port][?options]

```

port specifies the RTP port to use.

options contains a list of &-separated options of the form key=val. Standard percent-encoding (and using the plus sign for space) can be used to escape keys and values.

Options can also can be specified via command line options (or in code via AVOptions).

The list of supported options follows.

ttl=n

Set the TTL (Time-To-Live) value (for multicast only).

rtcpport=n

Set the remote RTCP port to n.

localport, local_rtpport, localrtpport=n

Set the local RTP port to n.

Using the localport option name is deprecated and should not be used.

local_rtcpport, localrtcpport=n'

Set the local RTCP port to n.

pkt_size=n

Set max packet size (in bytes) to n.

buffer_size=size

Set the maximum UDP socket buffer size in bytes.

connect=0|1

Do a connect() on the UDP socket (if set to 1) or not (if set to 0).

sources=ip[,ip]

List allowed source IP addresses.

block=ip[,ip]

List disallowed (blocked) source IP addresses.

write_to_source=0|1

Send packets to the source address of the latest received packet (if set to 1) or to a default remote address (if set to 0).

localaddr=addr

Local IP address of a network interface used for sending packets or joining multicast groups.

timeout=n

Set timeout (in microseconds) of socket I/O operations to n.

Important notes:

-  If rtcpport is not set the RTCP port will be set to the RTP port value plus 1.

-  If localrtpport (the local RTP port) is not set any available port will be used for the local RTP and RTCP ports.

-  If localrtcpport (the local RTCP port) is not set it will be set to the local RTP port value plus 1.

### 24.35 rtsp# TOC

Real-Time Streaming Protocol.

RTSP is not technically a protocol handler in libavformat, it is a demuxer and muxer. The demuxer supports both normal RTSP (with data transferred over RTP; this is used by e.g. Apple and Microsoft) and Real-RTSP (with data transferred over RDT).

The muxer can be used to send a stream using RTSP ANNOUNCE to a server supporting it (currently Darwin Streaming Server and Mischa Spiegelmock’s RTSP server).

The required syntax for a RTSP url is:

```
rtsp://hostname[:port]/path

```

Options can be set on the ffmpeg/ffplay command line, or set in code via AVOptions or in avformat_open_input.

#### 24.35.1 Muxer# TOC

The following options are supported.

rtsp_transport

Set RTSP transport protocols.

It accepts the following values:

‘udp’

Use UDP as lower transport protocol.

‘tcp’

Use TCP (interleaving within the RTSP control channel) as lower transport protocol.

Default value is ‘0’.

rtsp_flags

Set RTSP flags.

The following values are accepted:

‘latm’

Use MP4A-LATM packetization instead of MPEG4-GENERIC for AAC.

‘rfc2190’

Use RFC 2190 packetization instead of RFC 4629 for H.263.

‘skip_rtcp’

Don’t send RTCP sender reports.

‘h264_mode0’

Use mode 0 for H.264 in RTP.

‘send_bye’

Send RTCP BYE packets when finishing.

Default value is ‘0’.

min_port

Set minimum local UDP port. Default value is 5000.

max_port

Set maximum local UDP port. Default value is 65000.

buffer_size

Set the maximum socket buffer size in bytes.

pkt_size

Set max send packet size (in bytes). Default value is 1472.

#### 24.35.2 Demuxer# TOC

The following options are supported.

initial_pause

Do not start playing the stream immediately if set to 1. Default value is 0.

rtsp_transport

Set RTSP transport protocols.

It accepts the following values:

‘udp’

Use UDP as lower transport protocol.

‘tcp’

Use TCP (interleaving within the RTSP control channel) as lower transport protocol.

‘udp_multicast’

Use UDP multicast as lower transport protocol.

‘http’

Use HTTP tunneling as lower transport protocol, which is useful for passing proxies.

‘https’

Use HTTPs tunneling as lower transport protocol, which is useful for passing proxies and widely used for security consideration.

Multiple lower transport protocols may be specified, in that case they are tried one at a time (if the setup of one fails, the next one is tried). For the muxer, only the ‘tcp’ and ‘udp’ options are supported.

rtsp_flags

Set RTSP flags.

The following values are accepted:

‘filter_src’

Accept packets only from negotiated peer address and port.

‘listen’

Act as a server, listening for an incoming connection.

‘prefer_tcp’

Try TCP for RTP transport first, if TCP is available as RTSP RTP transport.

‘satip_raw’

Export raw MPEG-TS stream instead of demuxing. The flag will simply write out the raw stream, with the original PAT/PMT/PIDs intact.

Default value is ‘none’.

allowed_media_types

Set media types to accept from the server.

The following flags are accepted:

‘video’

‘audio’

‘data’

‘subtitle’

By default it accepts all media types.

min_port

Set minimum local UDP port. Default value is 5000.

max_port

Set maximum local UDP port. Default value is 65000.

listen_timeout

Set maximum timeout (in seconds) to establish an initial connection. Setting listen_timeout > 0 sets rtsp_flags to ‘listen’. Default is -1 which means an infinite timeout when ‘listen’ mode is set.

reorder_queue_size

Set number of packets to buffer for handling of reordered packets.

timeout

Set socket TCP I/O timeout in microseconds.

user_agent

Override User-Agent header. If not specified, it defaults to the libavformat identifier string.

buffer_size

Set the maximum socket buffer size in bytes.

When receiving data over UDP, the demuxer tries to reorder received packets (since they may arrive out of order, or packets may get lost totally). This can be disabled by setting the maximum demuxing delay to zero (via the max_delay field of AVFormatContext).

When watching multi-bitrate Real-RTSP streams with ffplay, the streams to display can be chosen with -vst n and -ast n for video and audio respectively, and can be switched on the fly by pressing v and a.

#### 24.35.3 Examples# TOC

The following examples all make use of the ffplay and ffmpeg tools.

- Watch a stream over UDP, with a max reordering delay of 0.5 seconds:

```
ffplay -max_delay 500000 -rtsp_transport udp rtsp://server/video.mp4

```

- Watch a stream tunneled over HTTP:

```
ffplay -rtsp_transport http rtsp://server/video.mp4

```

- Send a stream in realtime to a RTSP server, for others to watch:

```
ffmpeg -re -i input -f rtsp -muxdelay 0.1 rtsp://server/live.sdp

```

- Receive a stream in realtime:

```
ffmpeg -rtsp_flags listen -i rtsp://ownaddress/live.sdp output

```

### 24.36 sap# TOC

Session Announcement Protocol (RFC 2974). This is not technically a protocol handler in libavformat, it is a muxer and demuxer. It is used for signalling of RTP streams, by announcing the SDP for the streams regularly on a separate port.

#### 24.36.1 Muxer# TOC

The syntax for a SAP url given to the muxer is:

```
sap://destination[:port][?options]

```

The RTP packets are sent to destination on port port, or to port 5004 if no port is specified. options is a &-separated list. The following options are supported:

announce_addr=address

Specify the destination IP address for sending the announcements to. If omitted, the announcements are sent to the commonly used SAP announcement multicast address 224.2.127.254 (sap.mcast.net), or ff0e::2:7ffe if destination is an IPv6 address.

announce_port=port

Specify the port to send the announcements on, defaults to 9875 if not specified.

ttl=ttl

Specify the time to live value for the announcements and RTP packets, defaults to 255.

same_port=0|1

If set to 1, send all RTP streams on the same port pair. If zero (the default), all streams are sent on unique ports, with each stream on a port 2 numbers higher than the previous. VLC/Live555 requires this to be set to 1, to be able to receive the stream. The RTP stack in libavformat for receiving requires all streams to be sent on unique ports.

Example command lines follow.

To broadcast a stream on the local subnet, for watching in VLC:

```
ffmpeg -re -i input -f sap sap://224.0.0.255?same_port=1

```

Similarly, for watching in ffplay:

```
ffmpeg -re -i input -f sap sap://224.0.0.255

```

And for watching in ffplay, over IPv6:

```
ffmpeg -re -i input -f sap sap://[ff0e::1:2:3:4]

```

#### 24.36.2 Demuxer# TOC

The syntax for a SAP url given to the demuxer is:

```
sap://[address][:port]

```

address is the multicast address to listen for announcements on, if omitted, the default 224.2.127.254 (sap.mcast.net) is used. port is the port that is listened on, 9875 if omitted.

The demuxers listens for announcements on the given address and port. Once an announcement is received, it tries to receive that particular stream.

Example command lines follow.

To play back the first stream announced on the normal SAP multicast address:

```
ffplay sap://

```

To play back the first stream announced on one the default IPv6 SAP multicast address:

```
ffplay sap://[ff0e::2:7ffe]

```

### 24.37 sctp# TOC

Stream Control Transmission Protocol.

The accepted URL syntax is:

```
sctp://host:port[?options]

```

options contains a list of &-separated options of the form key=val. Standard percent-encoding (and using the plus sign for space) can be used to escape keys and values.

Options can also can be specified via command line options (or in code via AVOptions).

The list of supported options follows.

listen

If set to any value, listen for an incoming connection. Outgoing connection is done by default.

max_streams

Set the maximum number of streams. By default no limit is set.

### 24.38 shared# TOC

Thread-safe, persistent, cross-process cache wrapper for input streams. Caches the input stream to a file in the specified directory. This is similar to cache, but with a persistent cache on disk that may be shared between multiple processes or demuxers, even concurrently.

The filename of the cache is obtained by hashing the input URL, so there is some risk of collision if the same URL is used for different content (e.g. as a result of extra POST data being used to select the stream ID). To avoid this, make sure to only use this protocol for URLs that uniquely identify the content; otherwise you may get a garbled mix of sources. This includes content selected by request options such as headers, cookies or credentials: data cached for one user is returned to every other user of the same cache directory.

The accepted options are:

cache_dir

Path to the directory where cache files are stored. This option is required. Anyone who can write to this directory or to metadata_dir can alter the data read by all users of the cache, or make them crash, so neither may be writable by untrusted users.

metadata_dir

Path to the directory where metadata files are stored. Optional. If not specified, metadata is stored in the same directory as the cache file.

block_shift

Shift factor (log2) of the block size used for internal reads/writes. Defaults to 15, i.e. 32KB blocks. If this does not match the value that was specified when an existing cache file was created, the previously specified value will be used instead.

cache_read_only

If true, use the shared cache for reads but don’t write any new blocks to it. Default is false. Note that even with this option enabled, the cache file will be initialized if it does not already exist.

cache_verify

If true, verify any data read from the cache against the underlying input stream, and error out on any mismatches. Note that this will make the cache layer effectively useless. This is purely a debug option.

cache_timeout

If set to a nonzero value, specifies the maximum time (in microseconds) to wait for data to become available, if another process is currently trying to fetch and cache the same block at the same time. If this timeout elapses, it’s assumed that the other process may have gotten stuck or died in the meantime.

If set to zero, no waiting is done and all processes will immediately race to try and fetch the same missing blocks themselves. Defaults to 10000 (10 ms).

ignore_errors

If true, failures of the underlying input stream are not treated as fatal, and playback continues using only the data already present in the cache file. Default is false. Any attempt to read into uncached data will result in an unrecoverable IO error.

retry_errors

If true (the default), transient read errors from the underlying input stream are ignored and retried again. If false, any blocks that previously failed being read from will be treated as permanently inaccessible.

retry_corrupt

If true (the default), blocks whose contents fail the CRC integrity check are re-fetched from the underlying input stream, overwriting the corrupt cached data. If false, cache corruption is treated as a fatal read error.

cache_size_max

Maximum amount of data to cache, in bytes, rounded down to a multiple of the chosen block size. Accepts the usual size suffixes, e.g. 10G for 10*10^9 bytes, or 10Gi for 10*2^30 bytes. Defaults to 0, meaning no limit.

Once this limit is reached, the protocol switches to read-only mode (see cache_read_only). Already cached data is never evicted, so once this limit is reached, no new data will ever be cached until the cache file is deleted.

Note that this option is best-effort only, and may over-write up to N-1 blocks, where N is the number of concurrent processes using the same cache file. Note also that the underlying file system may reserve more space than written, if the underlying allocation granularity is larger than the block size.

offset

Initial byte offset to start reading from. This option is not passed on to the underlying protocol; it instead gets a regular seek on the first cache miss. Defaults to 0.

URL Syntax is

```
shared:URL

```

### 24.39 srt# TOC

Haivision Secure Reliable Transport Protocol via libsrt.

The supported syntax for a SRT URL is:

```
srt://hostname:port[?options]

```

options contains a list of &-separated options of the form key=val. Standard percent-encoding (and using the plus sign for space) can be used to escape keys and values.

Options can also can be specified via command line options (or in code via AVOptions).

The list of supported options follows.

connect_timeout=milliseconds

Connection timeout; SRT cannot connect for RTT > 1500 msec (2 handshake exchanges) with the default connect timeout of 3 seconds. This option applies to the caller and rendezvous connection modes. The connect timeout is 10 times the value set for the rendezvous mode (which can be used as a workaround for this connection problem with earlier versions).

ffs=bytes

Flight Flag Size (Window Size), in bytes. FFS is actually an internal parameter and you should set it to not less than recv_buffer_size and mss. The default value is relatively large, therefore unless you set a very large receiver buffer, you do not need to change this option. Default value is 25600.

inputbw=bytes/seconds

Sender nominal input rate, in bytes per seconds. Used along with oheadbw, when maxbw is set to relative (0), to calculate maximum sending rate when recovery packets are sent along with the main media stream: inputbw * (100 + oheadbw) / 100 if inputbw is not set while maxbw is set to relative (0), the actual input rate is evaluated inside the library. Default value is 0.

iptos=tos

IP Type of Service. Applies to sender only. Default value is 0xB8.

ipttl=ttl

IP Time To Live. Applies to sender only. Default value is 64.

latency=microseconds

Timestamp-based Packet Delivery Delay. Used to absorb bursts of missed packet retransmissions. This flag sets both rcvlatency and peerlatency to the same value. Note that prior to version 1.3.0 this is the only flag to set the latency, however this is effectively equivalent to setting peerlatency, when side is sender and rcvlatency when side is receiver, and the bidirectional stream sending is not supported.

listen_timeout=microseconds

Set socket listen timeout.

maxbw=bytes/seconds

Maximum sending bandwidth, in bytes per seconds. -1 infinite (CSRTCC limit is 30mbps) 0 relative to input rate (see inputbw) >0 absolute limit value Default value is 0 (relative)

mode=caller|listener|rendezvous

Connection mode. caller opens client connection. listener starts server to listen for incoming connections. rendezvous use Rendez-Vous connection mode. Default value is caller.

mss=bytes

Maximum Segment Size, in bytes. Used for buffer allocation and rate calculation using a packet counter assuming fully filled packets. The smallest MSS between the peers is used. This is 1500 by default in the overall internet. This is the maximum size of the UDP packet and can be only decreased, unless you have some unusual dedicated network settings. Default value is 1500.

nakreport=1|0

If set to 1, Receiver will send ‘UMSG_LOSSREPORT‘ messages periodically until a lost packet is retransmitted or intentionally dropped. Default value is 1.

oheadbw=percents

Recovery bandwidth overhead above input rate, in percents. See inputbw. Default value is 25%.

passphrase=string

HaiCrypt Encryption/Decryption Passphrase string, length from 10 to 79 characters. The passphrase is the shared secret between the sender and the receiver. It is used to generate the Key Encrypting Key using PBKDF2 (Password-Based Key Derivation Function). It is used only if pbkeylen is non-zero. It is used on the receiver only if the received data is encrypted. The configured passphrase cannot be recovered (write-only).

enforced_encryption=1|0

If true, both connection parties must have the same password set (including empty, that is, with no encryption). If the password doesn’t match or only one side is unencrypted, the connection is rejected. Default is true.

kmrefreshrate=packets

The number of packets to be transmitted after which the encryption key is switched to a new key. Default is -1. -1 means auto (0x1000000 in srt library). The range for this option is integers in the 0 - INT_MAX.

kmpreannounce=packets

The interval between when a new encryption key is sent and when switchover occurs. This value also applies to the subsequent interval between when switchover occurs and when the old encryption key is decommissioned. Default is -1. -1 means auto (0x1000 in srt library). The range for this option is integers in the 0 - INT_MAX.

snddropdelay=microseconds

The sender’s extra delay before dropping packets. This delay is added to the default drop delay time interval value.

Special value -1: Do not drop packets on the sender at all.

payload_size=bytes

Sets the maximum declared size of a packet transferred during the single call to the sending function in Live mode. Use 0 if this value isn’t used (which is default in file mode). Default is -1 (automatic), which typically means MPEG-TS; if you are going to use SRT to send any different kind of payload, such as, for example, wrapping a live stream in very small frames, then you can use a bigger maximum frame size, though not greater than 1456 bytes.

pkt_size=bytes

Alias for ‘payload_size’.

peerlatency=microseconds

The latency value (as described in rcvlatency) that is set by the sender side as a minimum value for the receiver.

pbkeylen=bytes

Sender encryption key length, in bytes. Only can be set to 0, 16, 24 and 32. Enable sender encryption if not 0. Not required on receiver (set to 0), key size obtained from sender in HaiCrypt handshake. Default value is 0.

rcvlatency=microseconds

The time that should elapse since the moment when the packet was sent and the moment when it’s delivered to the receiver application in the receiving function. This time should be a buffer time large enough to cover the time spent for sending, unexpectedly extended RTT time, and the time needed to retransmit the lost UDP packet. The effective latency value will be the maximum of this options’ value and the value of peerlatency set by the peer side. Before version 1.3.0 this option is only available as latency.

recv_buffer_size=bytes

Set UDP receive buffer size, expressed in bytes.

send_buffer_size=bytes

Set UDP send buffer size, expressed in bytes.

timeout=microseconds

Set raise error timeouts for read, write and connect operations. Note that the SRT library has internal timeouts which can be controlled separately, the value set here is only a cap on those.

tlpktdrop=1|0

Too-late Packet Drop. When enabled on receiver, it skips missing packets that have not been delivered in time and delivers the following packets to the application when their time-to-play has come. It also sends a fake ACK to the sender. When enabled on sender and enabled on the receiving peer, the sender drops the older packets that have no chance of being delivered in time. It was automatically enabled in the sender if the receiver supports it.

sndbuf=bytes

Set send buffer size, expressed in bytes.

rcvbuf=bytes

Set receive buffer size, expressed in bytes.

Receive buffer must not be greater than ffs.

lossmaxttl=packets

The value up to which the Reorder Tolerance may grow. When Reorder Tolerance is > 0, then packet loss report is delayed until that number of packets come in. Reorder Tolerance increases every time a "belated" packet has come, but it wasn’t due to retransmission (that is, when UDP packets tend to come out of order), with the difference between the latest sequence and this packet’s sequence, and not more than the value of this option. By default it’s 0, which means that this mechanism is turned off, and the loss report is always sent immediately upon experiencing a "gap" in sequences.

minversion

The minimum SRT version that is required from the peer. A connection to a peer that does not satisfy the minimum version requirement will be rejected.

The version format in hex is 0xXXYYZZ for x.y.z in human readable form.

streamid=string

A string limited to 512 characters that can be set on the socket prior to connecting. This stream ID will be able to be retrieved by the listener side from the socket that is returned from srt_accept and was connected by a socket with that set stream ID. SRT does not enforce any special interpretation of the contents of this string. This option doesn’t make sense in Rendezvous connection; the result might be that simply one side will override the value from the other side and it’s the matter of luck which one would win

srt_streamid=string

Alias for ‘streamid’ to avoid conflict with ffmpeg command line option.

smoother=live|file

The type of Smoother used for the transmission for that socket, which is responsible for the transmission and congestion control. The Smoother type must be exactly the same on both connecting parties, otherwise the connection is rejected.

messageapi=1|0

When set, this socket uses the Message API, otherwise it uses Buffer API. Note that in live mode (see transtype) there’s only message API available. In File mode you can chose to use one of two modes:

Stream API (default, when this option is false). In this mode you may send as many data as you wish with one sending instruction, or even use dedicated functions that read directly from a file. The internal facility will take care of any speed and congestion control. When receiving, you can also receive as many data as desired, the data not extracted will be waiting for the next call. There is no boundary between data portions in the Stream mode.

Message API. In this mode your single sending instruction passes exactly one piece of data that has boundaries (a message). Contrary to Live mode, this message may span across multiple UDP packets and the only size limitation is that it shall fit as a whole in the sending buffer. The receiver shall use as large buffer as necessary to receive the message, otherwise the message will not be given up. When the message is not complete (not all packets received or there was a packet loss) it will not be given up.

transtype=live|file

Sets the transmission type for the socket, in particular, setting this option sets multiple other parameters to their default values as required for a particular transmission type.

live: Set options as for live transmission. In this mode, you should send by one sending instruction only so many data that fit in one UDP packet, and limited to the value defined first in payload_size (1316 is default in this mode). There is no speed control in this mode, only the bandwidth control, if configured, in order to not exceed the bandwidth with the overhead transmission (retransmitted and control packets).

file: Set options as for non-live transmission. See messageapi for further explanations

linger=seconds

The number of seconds that the socket waits for unsent data when closing. Default is -1. -1 means auto (off with 0 seconds in live mode, on with 180 seconds in file mode). The range for this option is integers in the 0 - INT_MAX.

tsbpd=1|0

When true, use Timestamp-based Packet Delivery mode. The default behavior depends on the transmission type: enabled in live mode, disabled in file mode.

ipv6only=1|0

Accept IPv4 or not while using the IPv6 wildcard address. This should be set when listening on a IPv6 wildcard address.

For more information see: https://github.com/Haivision/srt.

### 24.40 srtp# TOC

Secure Real-time Transport Protocol.

The accepted options are:

srtp_in_suite

srtp_out_suite

Select input and output encoding suites.

Supported values:

‘AES_CM_128_HMAC_SHA1_80’

‘SRTP_AES128_CM_HMAC_SHA1_80’

‘AES_CM_128_HMAC_SHA1_32’

‘SRTP_AES128_CM_HMAC_SHA1_32’

srtp_in_params

srtp_out_params

Set input and output encoding parameters, which are expressed by a base64-encoded representation of a binary block. The first 16 bytes of this binary block are used as master key, the following 14 bytes are used as master salt.

### 24.41 subfile# TOC

Virtually extract a segment of a file or another stream. The underlying stream must be seekable.

Accepted options:

start

Start offset of the extracted segment, in bytes.

end

End offset of the extracted segment, in bytes. If set to 0, extract till end of file.

Examples:

Extract a chapter from a DVD VOB file (start and end sectors obtained externally and multiplied by 2048):

```
subfile,,start,153391104,end,268142592,,:/media/dvd/VIDEO_TS/VTS_08_1.VOB

```

Play an AVI file directly from a TAR archive:

```
subfile,,start,183241728,end,366490624,,:archive.tar

```

Play a MPEG-TS file from start offset till end:

```
subfile,,start,32815239,end,0,,:video.ts

```

### 24.42 tee# TOC

Writes the output to multiple protocols. The individual outputs are separated by |

```
tee:file://path/to/local/this.avi|file://path/to/local/that.avi

```

### 24.43 tcp# TOC

Transmission Control Protocol.

The required syntax for a TCP url is:

```
tcp://hostname:port[?options]

```

options contains a list of &-separated options of the form key=val. Standard percent-encoding (and using the plus sign for space) can be used to escape keys and values.

Options can also can be specified via command line options (or in code via AVOptions).

The list of supported options follows.

listen=2|1|0

Listen for an incoming connection. 0 disables listen, 1 enables listen in single client mode, 2 enables listen in multi-client mode. Default value is 0.

local_addr=addr

Local IP address of a network interface used for tcp socket connect.

local_port=port

Local port used for tcp socket connect.

timeout=microseconds

Set raise error timeout, expressed in microseconds.

This option is only relevant in read mode: if no data arrived in more than this time interval, raise error.

listen_timeout=milliseconds

Set listen timeout, expressed in milliseconds.

recv_buffer_size=bytes

Set receive buffer size, expressed bytes.

send_buffer_size=bytes

Set send buffer size, expressed bytes.

tcp_nodelay=1|0

Set TCP_NODELAY to disable Nagle’s algorithm. Default value is 0.

Remark: Writing to the socket is currently not optimized to minimize system calls and reduces the efficiency / effect of TCP_NODELAY.

tcp_mss=bytes

Set maximum segment size for outgoing TCP packets, expressed in bytes.

The following example shows how to setup a listening TCP connection with ffmpeg, which is then accessed with ffplay:

```
ffmpeg -i input -f format tcp://hostname:port?listen
ffplay tcp://hostname:port

```

### 24.44 tls# TOC

Transport Layer Security (TLS) / Secure Sockets Layer (SSL)

The required syntax for a TLS/SSL url is:

```
tls://hostname:port[?options]

```

options contains a list of &-separated options of the form key=val. Standard percent-encoding (and using the plus sign for space) can be used to escape keys and values.

Options can also can be specified via command line options (or in code via AVOptions).

The list of supported options follows.

ca_file, cafile=filename

A file containing certificate authority (CA) root certificates to treat as trusted. If the linked TLS library contains a default this might not need to be specified for verification to work, but not all libraries and setups have defaults built in. The file must be in OpenSSL PEM format.

tls_verify, verify=1|0

If enabled, try to verify the peer that we are communicating with. Note, if using OpenSSL, this currently only makes sure that the peer certificate is signed by one of the root certificates in the CA database, but it does not validate that the certificate actually matches the host name we are trying to connect to. (With other backends, the host name is validated as well.)

This is enabled by default. Verifying the peer requires a CA database, which in some cases has to be provided by the caller.

cert_file, cert=filename

A file containing a certificate to use in the handshake with the peer. (When operating as server, in listen mode, this is more often required by the peer, while client certificates only are mandated in certain setups.)

key_file, key=filename

A file containing the private key for the certificate.

listen=1|0

If enabled, listen for connections on the provided port, and assume the server role in the handshake instead of the client role.

http_proxy

The HTTP proxy to tunnel through, e.g. http://example.com:1234. The proxy must support the CONNECT method.

Example command lines:

To create a TLS/SSL server that serves an input stream.

```
ffmpeg -i input -f format tls://hostname:port?listen&cert=server.crt&key=server.key

```

To play back a stream from the TLS/SSL server using ffplay:

```
ffplay tls://hostname:port

```

### 24.45 dtls# TOC

Datagram Transport Layer Security (DTLS)

The required syntax for a DTLS URL is:

```
dtls://hostname:port[?options]

```

options contains a list of &-separated options of the form key=val. Standard percent-encoding (and using the plus sign for space) can be used to escape keys and values.

Options can also can be specified via command line options (or in code via AVOptions).

DTLS shares most options with TLS, but operates over UDP instead of TCP.

The list of supported options follows.

ca_file, cafile=filename

A file containing certificate authority (CA) root certificates to treat as trusted. If the linked TLS library contains a default this might not need to be specified for verification to work, but not all libraries and setups have defaults built in. The file must be in OpenSSL PEM format.

tls_verify, verify=1|0

If enabled, try to verify the peer that we are communicating with. Note, if using OpenSSL, this currently only makes sure that the peer certificate is signed by one of the root certificates in the CA database, but it does not validate that the certificate actually matches the host name we are trying to connect to.

This is enabled by default. Verifying the peer requires a CA database, which in some cases has to be provided by the caller.

cert_file, cert=filename

A file containing a certificate to use in the handshake with the peer. (When operating as server, in listen mode, this is more often required by the peer, while client certificates only are mandated in certain setups.)

key_file, key=filename

A file containing the private key for the certificate.

cert_pem=string

Certificate PEM string

key_pem=string

Private key PEM string

listen=1|0

If enabled, listen for connections on the provided port, and assume the server role in the handshake instead of the client role.

mtu=size

Set the Maximum Transmission Unit (MTU) for DTLS packets.

use_srtp=1|0

Enable the use_srtp DTLS extension. This is used in WebRTC applications to establish SRTP encryption keys through the DTLS handshake. Default is disabled.

external_sock=1|0

Use an external socket instead of creating a new one. This option only makes sense to pass when interacting with the code via API, enabling this from CLI will cause immediate failure. Default is disabled.

Example command lines:

To create a DTLS server:

```
ffmpeg -listen 1 -i dtls://hostname:port output

```

To create a DTLS client and send data to server:

```
ffmpeg -i input -f format dtls://hostname:port

```

### 24.46 udp# TOC

User Datagram Protocol.

The required syntax for an UDP URL is:

```
udp://hostname:port[?options]

```

options contains a list of &-separated options of the form key=val. Standard percent-encoding (and using the plus sign for space) can be used to escape keys and values.

Options can also can be specified via command line options (or in code via AVOptions).

In case threading is enabled on the system, a circular buffer is used to store the incoming data, which allows one to reduce loss of data due to UDP socket buffer overruns. The fifo_size and overrun_nonfatal options are related to this buffer.

The list of supported options follows.

buffer_size=size

Set the UDP maximum socket buffer size in bytes. This is used to set either the receive or send buffer size, depending on what the socket is used for. Default is 32 KB for output, 384 KB for input. See also fifo_size.

bitrate=bitrate

If set to nonzero, the output will have the specified constant bitrate if the input has enough packets to sustain it.

burst_bits=bits

When using bitrate this specifies the maximum number of bits in packet bursts.

localport=port

Override the local UDP port to bind with.

localaddr=addr

Local IP address of a network interface used for sending packets or joining multicast groups.

pkt_size=size

Set the size in bytes of UDP packets.

reuse=1|0

Explicitly allow or disallow reusing UDP sockets.

ttl=ttl

Set the time to live value (for multicast only).

dscp=dscp

Set the 6-bit DSCP field for outgoing packets.

connect=1|0

Initialize the UDP socket with connect(). In this case, the destination address can’t be changed with ff_udp_set_remote_url later. If the destination address isn’t known at the start, this option can be specified in ff_udp_set_remote_url, too. This allows finding out the source address for the packets with getsockname, and makes writes return with AVERROR(ECONNREFUSED) if "destination unreachable" is received. For receiving, this gives the benefit of only receiving packets from the specified peer address/port.

sources=address[,address]

Only receive packets sent from the specified addresses. In case of multicast, also subscribe to multicast traffic coming from these addresses only.

block=address[,address]

Ignore packets sent from the specified addresses. In case of multicast, also exclude the source addresses in the multicast subscription.

fifo_size=units

Set the UDP receiving circular buffer size, expressed as a number of packets with size of 188 bytes. If not specified defaults to 7*4096. Set to 0 to disable the receiving circular buffer and its receive thread.

overrun_nonfatal=1|0

Survive in case of UDP receiving circular buffer overrun. Default value is 0.

timeout=microseconds

Set raise error timeout, expressed in microseconds.

This option is only relevant in read mode: if no data arrived in more than this time interval, raise error.

broadcast=1|0

Explicitly allow or disallow UDP broadcasting.

Note that broadcasting may not work properly on networks having a broadcast storm protection.

#### 24.46.1 Examples# TOC

- Use ffmpeg to stream over UDP to a remote endpoint:

```
ffmpeg -i input -f format udp://hostname:port

```

- Use ffmpeg to stream in mpegts format over UDP using 188 sized UDP packets, using a large input buffer:

```
ffmpeg -i input -f mpegts udp://hostname:port?pkt_size=188&buffer_size=65535

```

- Use ffmpeg to receive over UDP from a remote endpoint:

```
ffmpeg -i udp://[multicast-address]:port ...

```

### 24.47 unix# TOC

Unix local socket

The required syntax for a Unix socket URL is:

```
unix://filepath

```

The following parameters can be set via command line options (or in code via AVOptions):

timeout

Timeout in ms.

listen

Create the Unix socket in listening mode.

type

Select socket type.

‘stream Corresponds to SOCK_STREAM (reliable stream-oriented)’

‘datagram Corresponds to SOCK_DGRAM (unreliable packet-oriented)’

‘seqpacket Corresponds to SOCK_SEQPACKET (reliable packet-oriented)’

pkt_size

Maximum packet size for packet-oriented sockets (SOCK_DGRAM and SOCK_SEQPACKET). If greater than zero, this value is used as max_packet_size. Ignored for SOCK_STREAM. Default is 0.

### 24.48 zmq# TOC

ZeroMQ asynchronous messaging using the libzmq library.

This library supports unicast streaming to multiple clients without relying on an external server.

The required syntax for streaming or connecting to a stream is:

```
zmq:tcp://ip-address:port

```

Example: Create a localhost stream on port 5555:

```
ffmpeg -re -i input -f mpegts zmq:tcp://127.0.0.1:5555

```

Multiple clients may connect to the stream using:

```
ffplay zmq:tcp://127.0.0.1:5555

```

Streaming to multiple clients is implemented using a ZeroMQ Pub-Sub pattern. The server side binds to a port and publishes data. Clients connect to the server (via IP address/port) and subscribe to the stream. The order in which the server and client start generally does not matter.

ffmpeg must be compiled with the –enable-libzmq option to support this protocol.

Options can be set on the ffmpeg/ffplay command line. The following options are supported:

pkt_size

Forces the maximum packet size for sending/receiving data. The default value is 131,072 bytes. On the server side, this sets the maximum size of sent packets via ZeroMQ. On the clients, it sets an internal buffer size for receiving packets. Note that pkt_size on the clients should be equal to or greater than pkt_size on the server. Otherwise the received message may be truncated causing decoding errors.

## 25 Device Options# TOC

The libavdevice library provides the same interface as libavformat. Namely, an input device is considered like a demuxer, and an output device like a muxer, and the interface and generic device options are the same provided by libavformat (see the ffmpeg-formats manual).

In addition each input or output device may support so-called private options, which are specific for that component.

Options may be set by specifying -option value in the FFmpeg tools, or by setting the value explicitly in the device AVFormatContext options or using the libavutil/opt.h API for programmatic use.

## 26 Input Devices# TOC

Input devices are configured elements in FFmpeg which enable accessing the data coming from a multimedia device attached to your system.

When you configure your FFmpeg build, all the supported input devices are enabled by default. You can list all available ones using the configure option "–list-indevs".

You can disable all the input devices using the configure option "–disable-indevs", and selectively enable an input device using the option "–enable-indev=INDEV", or you can disable a particular input device using the option "–disable-indev=INDEV".

The option "-devices" of the ff* tools will display the list of supported input devices.

A description of the currently available input devices follows.

### 26.1 alsa# TOC

ALSA (Advanced Linux Sound Architecture) input device.

To enable this input device during configuration you need libasound installed on your system.

This device allows capturing from an ALSA device. The name of the device to capture has to be an ALSA card identifier.

An ALSA identifier has the syntax:

```
hw:CARD[,DEV[,SUBDEV]]

```

where the DEV and SUBDEV components are optional.

The three arguments (in order: CARD,DEV,SUBDEV) specify card number or identifier, device number and subdevice number (-1 means any).

To see the list of cards currently recognized by your system check the files /proc/asound/cards and /proc/asound/devices.

For example to capture with ffmpeg from an ALSA device with card id 0, you may run the command:

```
ffmpeg -f alsa -i hw:0 alsaout.wav

```

For more information see: http://www.alsa-project.org/alsa-doc/alsa-lib/pcm.html

#### 26.1.1 Options# TOC

sample_rate

Set the sample rate in Hz. Default is 48000.

ch_layout

Set the channel layout. When unset, the layout defaults to stereo, or to the minimum channel count supported by the device, and is filled in from the ALSA channel map on a best-effort basis.

### 26.2 android_camera# TOC

Android camera input device.

This input devices uses the Android Camera2 NDK API which is available on devices with API level 24+. The availability of android_camera is autodetected during configuration.

This device allows capturing from all cameras on an Android device, which are integrated into the Camera2 NDK API.

The available cameras are enumerated internally and can be selected with the camera_index parameter. The input file string is discarded.

Generally the back facing camera has index 0 while the front facing camera has index 1.

#### 26.2.1 Options# TOC

video_size

Set the video size given as a string such as 640x480 or hd720. Falls back to the first available configuration reported by Android if requested video size is not available or by default.

framerate

Set the video framerate. Falls back to the first available configuration reported by Android if requested framerate is not available or by default (-1).

camera_index

Set the index of the camera to use. Default is 0.

input_queue_size

Set the maximum number of frames to buffer. Default is 5.

### 26.3 avfoundation# TOC

AVFoundation input device.

AVFoundation is the currently recommended framework by Apple for streamgrabbing on OSX >= 10.7 as well as on iOS.

The input filename has to be given in the following syntax:

```
-i "[[VIDEO]:[AUDIO]]"

```

The first entry selects the video input while the latter selects the audio input. The stream has to be specified by the device name or the device index as shown by the device list. Alternatively, the video and/or audio input device can be chosen by index using the  -video_device_index <INDEX>  and/or  -audio_device_index <INDEX>  , overriding any device name or index given in the input filename.

All available devices can be enumerated by using -list_devices true, listing all device names and corresponding indices.

There are two device name aliases:

default

Select the AVFoundation default device of the corresponding type.

none

Do not record the corresponding media type. This is equivalent to specifying an empty device name or index.

#### 26.3.1 Options# TOC

AVFoundation supports the following options:

-list_devices <TRUE|FALSE>

If set to true, a list of all available input devices is given showing their index, name, unique ID, and USB serial number (when available).

-video_device_index <INDEX>

Specify the video device by its index. Overrides anything given in the input filename.

-audio_device_index <INDEX>

Specify the audio device by its index. Overrides anything given in the input filename.

-video_device_id <ID>

Specify the video device by a prefixed identifier, as shown by -list_devices: uid:<UID> selects by AVFoundation unique ID, serial:<SERIAL> by USB serial number. The unique ID of a UVC device may not be stable across reboots. Only UVC devices expose a serial number. Overrides anything given in the input filename.

-audio_device_id <ID>

Specify the audio device by a prefixed identifier. See -video_device_id; for audio, the serial is only available for class-compliant USB devices.

-pixel_format <FORMAT>

Request the video device to use a specific pixel format. If the specified format is not supported, a list of available formats is given and the first one in this list is used instead. Available pixel formats are: monob, rgb555be, rgb555le, rgb565be, rgb565le, rgb24, bgr24, 0rgb, bgr0, 0bgr, rgb0, bgr48be, uyvy422, yuva444p, yuva444p16le, yuv444p, yuv422p16, yuv422p10, yuv444p10, yuv420p, nv12, yuyv422, gray

-framerate

Set the grabbing frame rate. Default is ntsc, corresponding to a frame rate of 30000/1001.

-video_size

Set the video frame size.

-capture_cursor

Capture the mouse pointer. Default is 0.

-capture_mouse_clicks

Capture the screen mouse clicks. Default is 0.

-capture_raw_data

Capture the raw device data. Default is 0. Using this option may result in receiving the underlying data delivered to the AVFoundation framework. E.g. for muxed devices that sends raw DV data to the framework (like tape-based camcorders), setting this option to false results in extracted video frames captured in the designated pixel format only. Setting this option to true results in receiving the raw DV stream untouched.

#### 26.3.2 Examples# TOC

- Print the list of AVFoundation supported devices and exit:

```
$ ffmpeg -f avfoundation -list_devices true -i ""

```

- Record video from video device 0 and audio from audio device 0 into out.avi:

```
$ ffmpeg -f avfoundation -i "0:0" out.avi

```

- Record video from video device 2 and audio from audio device 1 into out.avi:

```
$ ffmpeg -f avfoundation -video_device_index 2 -i ":1" out.avi

```

- Record video from the system default video device using the pixel format bgr0 and do not record any audio into out.avi:

```
$ ffmpeg -f avfoundation -pixel_format bgr0 -i "default:none" out.avi

```

- Record raw DV data from a suitable input device and write the output into out.dv:

```
$ ffmpeg -f avfoundation -capture_raw_data true -i "zr100:none" out.dv

```

### 26.4 decklink# TOC

The decklink input device provides capture capabilities for Blackmagic DeckLink devices.

To enable this input device, you need the Blackmagic DeckLink SDK and you need to configure with the appropriate --extra-cflags, --extra-cxxflags and --extra-ldflags. The SDK include directory must be available to both the C and C++ compilers. On Windows, you need to run the IDL files through widl.

DeckLink is very picky about the formats it supports. Pixel format of the input can be set with raw_format. Framerate and video size must be determined for your device with -list_formats 1. Audio sample rate is always 48 kHz and the number of channels can be 2, 8 or 16. Note that all audio channels are bundled in one single audio track.

#### 26.4.1 Options# TOC

list_devices

If set to true, print a list of devices and exit. Defaults to false. This option is deprecated, please use the -sources option of ffmpeg to list the available input devices.

list_formats

If set to true, print a list of supported formats and exit. Defaults to false.

format_code <FourCC>

This sets the input video format to the format given by the FourCC. To see the supported values of your device(s) use list_formats. Note that there is a FourCC 'pal ' that can also be used as pal (3 letters). Default behavior is autodetection of the input video format, if the hardware supports it.

raw_format

Set the pixel format of the captured video. Available values are:

‘auto’

This is the default which means 8-bit YUV 422 or 8-bit ARGB if format autodetection is used, 8-bit YUV 422 otherwise.

‘uyvy422’

8-bit YUV 422.

‘yuv422p10’

10-bit YUV 422.

‘argb’

8-bit RGB.

‘bgra’

8-bit RGB.

‘rgb10’

10-bit RGB.

teletext_lines

If set to nonzero, an additional teletext stream will be captured from the vertical ancillary data. Both SD PAL (576i) and HD (1080i or 1080p) sources are supported. In case of HD sources, OP47 packets are decoded.

This option is a bitmask of the SD PAL VBI lines captured, specifically lines 6 to 22, and lines 318 to 335. Line 6 is the LSB in the mask. Selected lines which do not contain teletext information will be ignored. You can use the special all constant to select all possible lines, or standard to skip lines 6, 318 and 319, which are not compatible with all receivers.

For SD sources, ffmpeg needs to be compiled with --enable-libzvbi. For HD sources, on older (pre-4K) DeckLink card models you have to capture in 10 bit mode.

channels

Defines number of audio channels to capture. Must be ‘2’, ‘8’ or ‘16’. Defaults to ‘2’.

duplex_mode

Sets the decklink device duplex/profile mode. Must be ‘unset’, ‘half’, ‘full’, ‘one_sub_device_full’, ‘one_sub_device_half’, ‘two_sub_device_full’, ‘four_sub_device_half’ Defaults to ‘unset’.

Note: DeckLink SDK 11.0 have replaced the duplex property by a profile property. For the DeckLink Duo 2 and DeckLink Quad 2, a profile is shared between any 2 sub-devices that utilize the same connectors. For the DeckLink 8K Pro, a profile is shared between all 4 sub-devices. So DeckLink 8K Pro support four profiles.

Valid profile modes for DeckLink 8K Pro(with DeckLink SDK >= 11.0): ‘one_sub_device_full’, ‘one_sub_device_half’, ‘two_sub_device_full’, ‘four_sub_device_half’

Valid profile modes for DeckLink Quad 2 and DeckLink Duo 2: ‘half’, ‘full’

timecode_format

Timecode type to include in the frame and video stream metadata. Must be ‘none’, ‘rp188vitc’, ‘rp188vitc2’, ‘rp188ltc’, ‘rp188hfr’, ‘rp188any’, ‘vitc’, ‘vitc2’, or ‘serial’. Defaults to ‘none’ (not included).

In order to properly support 50/60 fps timecodes, the ordering of the queried timecode types for ‘rp188any’ is HFR, VITC1, VITC2 and LTC for >30 fps content. Note that this is slightly different to the ordering used by the DeckLink API, which is HFR, VITC1, LTC, VITC2.

video_input

Sets the video input source. Must be ‘unset’, ‘sdi’, ‘hdmi’, ‘optical_sdi’, ‘component’, ‘composite’ or ‘s_video’. Defaults to ‘unset’.

audio_input

Sets the audio input source. Must be ‘unset’, ‘embedded’, ‘aes_ebu’, ‘analog’, ‘analog_xlr’, ‘analog_rca’ or ‘microphone’. Defaults to ‘unset’.

video_pts

Sets the video packet timestamp source. Must be ‘video’, ‘audio’, ‘reference’, ‘wallclock’ or ‘abs_wallclock’. Defaults to ‘video’.

audio_pts

Sets the audio packet timestamp source. Must be ‘video’, ‘audio’, ‘reference’, ‘wallclock’ or ‘abs_wallclock’. Defaults to ‘audio’.

draw_bars

If set to ‘true’, color bars are drawn in the event of a signal loss. Defaults to ‘true’. This option is deprecated, please use the signal_loss_action option.

signal_loss_action

Sets the action to take in the event of a signal loss. Accepts one of the following values:

1, none

Do nothing on signal loss. This usually results in black frames.

2, bars

Draw color bars on signal loss. Only supported for 8-bit input signals.

3, repeat

Repeat the last video frame on signal loss.

Defaults to ‘bars’.

queue_size

Sets maximum input buffer size in bytes. If the buffering reaches this value, incoming frames will be dropped. Defaults to ‘1073741824’.

audio_depth

Sets the audio sample bit depth. Must be ‘16’ or ‘32’. Defaults to ‘16’.

decklink_copyts

If set to true, timestamps are forwarded as they are without removing the initial offset. Defaults to false.

timestamp_align

Capture start time alignment in seconds. If set to nonzero, input frames are dropped till the system timestamp aligns with configured value. Alignment difference of up to one frame duration is tolerated. This is useful for maintaining input synchronization across N different hardware devices deployed for ’N-way’ redundancy. The system time of different hardware devices should be synchronized with protocols such as NTP or PTP, before using this option. Note that this method is not foolproof. In some border cases input synchronization may not happen due to thread scheduling jitters in the OS. Either sync could go wrong by 1 frame or in a rarer case timestamp_align seconds. Defaults to ‘0’.

wait_for_tc (bool)

Drop frames till a frame with timecode is received. Sometimes serial timecode isn’t received with the first input frame. If that happens, the stored stream timecode will be inaccurate. If this option is set to true, input frames are dropped till a frame with timecode is received. Option timecode_format must be specified. Defaults to false.

enable_klv(bool)

If set to true, extracts KLV data from VANC and outputs KLV packets. KLV VANC packets are joined based on MID and PSC fields and aggregated into one KLV packet. Defaults to false.

#### 26.4.2 Examples# TOC

- List input devices:

```
ffmpeg -sources decklink

```

- List supported formats:

```
ffmpeg -f decklink -list_formats 1 -i 'Intensity Pro'

```

- Capture video clip at 1080i50:

```
ffmpeg -format_code Hi50 -f decklink -i 'Intensity Pro' -c:a copy -c:v copy output.avi

```

- Capture video clip at 1080i50 10 bit:

```
ffmpeg -raw_format yuv422p10 -format_code Hi50 -f decklink -i 'UltraStudio Mini Recorder' -c:a copy -c:v copy output.avi

```

- Capture video clip at 1080i50 with 16 audio channels:

```
ffmpeg -channels 16 -format_code Hi50 -f decklink -i 'UltraStudio Mini Recorder' -c:a copy -c:v copy output.avi

```

### 26.5 dshow# TOC

Windows DirectShow input device.

DirectShow support is enabled when FFmpeg is built with the mingw-w64 project. Currently only audio and video devices are supported.

Multiple devices may be opened as separate inputs, but they may also be opened on the same input, which should improve synchronism between them.

The input name should be in the format:

```
TYPE=NAME[:TYPE=NAME]

```

where TYPE can be either audio or video, and NAME is the device’s name or alternative name..

#### 26.5.1 Options# TOC

If no options are specified, the device’s defaults are used. If the device does not support the requested options, it will fail to open.

video_size

Set the video size in the captured video.

framerate

Set the frame rate in the captured video.

sample_rate

Set the sample rate (in Hz) of the captured audio.

sample_size

Set the sample size (in bits) of the captured audio.

channels

Set the number of channels in the captured audio.

list_devices

If set to true, print a list of devices and exit.

list_options

If set to true, print a list of selected device’s options and exit.

video_device_number

Set video device number for devices with the same name (starts at 0, defaults to 0).

audio_device_number

Set audio device number for devices with the same name (starts at 0, defaults to 0).

pixel_format

Select pixel format to be used by DirectShow. This may only be set when the video codec is not set or set to rawvideo.

audio_buffer_size

Set audio device buffer size in milliseconds (which can directly impact latency, depending on the device). Defaults to using the audio device’s default buffer size (typically some multiple of 500ms). Setting this value too low can degrade performance. See also http://msdn.microsoft.com/en-us/library/windows/desktop/dd377582(v=vs.85).aspx

video_pin_name

Select video capture pin to use by name or alternative name.

audio_pin_name

Select audio capture pin to use by name or alternative name.

crossbar_video_input_pin_number

Select video input pin number for crossbar device. This will be routed to the crossbar device’s Video Decoder output pin. Note that changing this value can affect future invocations (sets a new default) until system reboot occurs.

crossbar_audio_input_pin_number

Select audio input pin number for crossbar device. This will be routed to the crossbar device’s Audio Decoder output pin. Note that changing this value can affect future invocations (sets a new default) until system reboot occurs.

show_video_device_dialog

If set to true, before capture starts, popup a display dialog to the end user, allowing them to change video filter properties and configurations manually. Note that for crossbar devices, adjusting values in this dialog may be needed at times to toggle between PAL (25 fps) and NTSC (29.97) input frame rates, sizes, interlacing, etc. Changing these values can enable different scan rates/frame rates and avoiding green bars at the bottom, flickering scan lines, etc. Note that with some devices, changing these properties can also affect future invocations (sets new defaults) until system reboot occurs.

show_audio_device_dialog

If set to true, before capture starts, popup a display dialog to the end user, allowing them to change audio filter properties and configurations manually.

show_video_crossbar_connection_dialog

If set to true, before capture starts, popup a display dialog to the end user, allowing them to manually modify crossbar pin routings, when it opens a video device.

show_audio_crossbar_connection_dialog

If set to true, before capture starts, popup a display dialog to the end user, allowing them to manually modify crossbar pin routings, when it opens an audio device.

show_analog_tv_tuner_dialog

If set to true, before capture starts, popup a display dialog to the end user, allowing them to manually modify TV channels and frequencies.

show_analog_tv_tuner_audio_dialog

If set to true, before capture starts, popup a display dialog to the end user, allowing them to manually modify TV audio (like mono vs. stereo, Language A,B or C).

audio_device_load

Load an audio capture filter device from file instead of searching it by name. It may load additional parameters too, if the filter supports the serialization of its properties to. To use this an audio capture source has to be specified, but it can be anything even fake one.

audio_device_save

Save the currently used audio capture filter device and its parameters (if the filter supports it) to a file. If a file with the same name exists it will be overwritten.

video_device_load

Load a video capture filter device from file instead of searching it by name. It may load additional parameters too, if the filter supports the serialization of its properties to. To use this a video capture source has to be specified, but it can be anything even fake one.

video_device_save

Save the currently used video capture filter device and its parameters (if the filter supports it) to a file. If a file with the same name exists it will be overwritten.

use_video_device_timestamps

If set to false, the timestamp for video frames will be derived from the wallclock instead of the timestamp provided by the capture device. This allows working around devices that provide unreliable timestamps.

#### 26.5.2 Examples# TOC

- Print the list of DirectShow supported devices and exit:

```
$ ffmpeg -list_devices true -f dshow -i dummy

```

- Open video device Camera:

```
$ ffmpeg -f dshow -i video="Camera"

```

- Open second video device with name Camera:

```
$ ffmpeg -f dshow -video_device_number 1 -i video="Camera"

```

- Open video device Camera and audio device Microphone:

```
$ ffmpeg -f dshow -i video="Camera":audio="Microphone"

```

- Print the list of supported options in selected device and exit:

```
$ ffmpeg -list_options true -f dshow -i video="Camera"

```

- Specify pin names to capture by name or alternative name, specify alternative device name:

```
$ ffmpeg -f dshow -audio_pin_name "Audio Out" -video_pin_name 2 -i video=video="@device_pnp_\\?\pci#ven_1a0a&dev_6200&subsys_62021461&rev_01#4&e2c7dd6&0&00e1#{65e8773d-8f56-11d0-a3b9-00a0c9223196}\{ca465100-deb0-4d59-818f-8c477184adf6}":audio="Microphone"

```

- Configure a crossbar device, specifying crossbar pins, allow user to adjust video capture properties at startup:

```
$ ffmpeg -f dshow -show_video_device_dialog true -crossbar_video_input_pin_number 0
     -crossbar_audio_input_pin_number 3 -i video="AVerMedia BDA Analog Capture":audio="AVerMedia BDA Analog Capture"

```

### 26.6 fbdev# TOC

Linux framebuffer input device.

The Linux framebuffer is a graphic hardware-independent abstraction layer to show graphics on a computer monitor, typically on the console. It is accessed through a file device node, usually /dev/fb0.

For more detailed information read the file Documentation/fb/framebuffer.txt included in the Linux source tree.

See also http://linux-fbdev.sourceforge.net/, and fbset(1).

To record from the framebuffer device /dev/fb0 with ffmpeg:

```
ffmpeg -f fbdev -framerate 10 -i /dev/fb0 out.avi

```

You can take a single screenshot image with the command:

```
ffmpeg -f fbdev -framerate 1 -i /dev/fb0 -frames:v 1 screenshot.jpeg

```

#### 26.6.1 Options# TOC

framerate

Set the frame rate. Default is 25.

### 26.7 gdigrab# TOC

Win32 GDI-based screen capture device.

This device allows you to capture a region of the display on Windows.

Amongst options for the input filenames are such elements as:

```
desktop

```

or

```
title=window_title

```

or

```
hwnd=window_hwnd

```

The first option will capture the entire desktop, or a fixed region of the desktop. The second and third options will instead capture the contents of a single window, regardless of its position on the screen.

For example, to grab the entire desktop using ffmpeg:

```
ffmpeg -f gdigrab -framerate 6 -i desktop out.mpg

```

Grab a 640x480 region at position 10,20:

```
ffmpeg -f gdigrab -framerate 6 -offset_x 10 -offset_y 20 -video_size vga -i desktop out.mpg

```

Grab the contents of the window named "Calculator"

```
ffmpeg -f gdigrab -framerate 6 -i title=Calculator out.mpg

```

#### 26.7.1 Options# TOC

draw_mouse

Specify whether to draw the mouse pointer. Use the value 0 to not draw the pointer. Default value is 1.

framerate

Set the grabbing frame rate. Default value is ntsc, corresponding to a frame rate of 30000/1001.

show_region

Show grabbed region on screen.

If show_region is specified with 1, then the grabbing region will be indicated on screen. With this option, it is easy to know what is being grabbed if only a portion of the screen is grabbed.

Note that show_region is incompatible with grabbing the contents of a single window.

For example:

```
ffmpeg -f gdigrab -show_region 1 -framerate 6 -video_size cif -offset_x 10 -offset_y 20 -i desktop out.mpg

```

video_size

Set the video frame size. The default is to capture the full screen if desktop is selected, or the full window size if title=window_title is selected.

offset_x

When capturing a region with video_size, set the distance from the left edge of the screen or desktop.

Note that the offset calculation is from the top left corner of the primary monitor on Windows. If you have a monitor positioned to the left of your primary monitor, you will need to use a negative offset_x value to move the region to that monitor.

offset_y

When capturing a region with video_size, set the distance from the top edge of the screen or desktop.

Note that the offset calculation is from the top left corner of the primary monitor on Windows. If you have a monitor positioned above your primary monitor, you will need to use a negative offset_y value to move the region to that monitor.

### 26.8 iec61883# TOC

FireWire DV/HDV input device using libiec61883.

To enable this input device, you need libiec61883, libraw1394 and libavc1394 installed on your system. Use the configure option --enable-libiec61883 to compile with the device enabled.

The iec61883 capture device supports capturing from a video device connected via IEEE1394 (FireWire), using libiec61883 and the new Linux FireWire stack (juju). This is the default DV/HDV input method in Linux Kernel 2.6.37 and later, since the old FireWire stack was removed.

Specify the FireWire port to be used as input file, or "auto" to choose the first port connected.

#### 26.8.1 Options# TOC

dvtype

Override autodetection of DV/HDV. This should only be used if auto detection does not work, or if usage of a different device type should be prohibited. Treating a DV device as HDV (or vice versa) will not work and result in undefined behavior. The values auto, dv and hdv are supported.

dvbuffer

Set maximum size of buffer for incoming data, in frames. For DV, this is an exact value. For HDV, it is not frame exact, since HDV does not have a fixed frame size.

dvguid

Select the capture device by specifying its GUID. Capturing will only be performed from the specified device and fails if no device with the given GUID is found. This is useful to select the input if multiple devices are connected at the same time. Look at /sys/bus/firewire/devices to find out the GUIDs.

#### 26.8.2 Examples# TOC

- Grab and show the input of a FireWire DV/HDV device.

```
ffplay -f iec61883 -i auto

```

- Grab and record the input of a FireWire DV/HDV device, using a packet buffer of 100000 packets if the source is HDV.

```
ffmpeg -f iec61883 -i auto -dvbuffer 100000 out.mpg

```

### 26.9 jack# TOC

JACK input device.

To enable this input device during configuration you need libjack installed on your system.

A JACK input device creates one or more JACK writable clients, one for each audio channel, with name client_name:input_N, where client_name is the name provided by the application, and N is a number which identifies the channel. Each writable client will send the acquired data to the FFmpeg input device.

Once you have created one or more JACK readable clients, you need to connect them to one or more JACK writable clients.

To connect or disconnect JACK clients you can use the jack_connect and jack_disconnect programs, or do it through a graphical interface, for example with qjackctl.

To list the JACK clients and their properties you can invoke the command jack_lsp.

Follows an example which shows how to capture a JACK readable client with ffmpeg.

```
# Create a JACK writable client with name "ffmpeg".
$ ffmpeg -f jack -i ffmpeg -y out.wav

# Start the sample jack_metro readable client.
$ jack_metro -b 120 -d 0.2 -f 4000

# List the current JACK clients.
$ jack_lsp -c
system:capture_1
system:capture_2
system:playback_1
system:playback_2
ffmpeg:input_1
metro:120_bpm

# Connect metro to the ffmpeg writable client.
$ jack_connect metro:120_bpm ffmpeg:input_1

```

For more information read: http://jackaudio.org/

#### 26.9.1 Options# TOC

channels

Set the number of channels. Default is 2.

### 26.10 kmsgrab# TOC

KMS video input device.

Captures the KMS scanout framebuffer associated with a specified CRTC or plane as a DRM object that can be passed to other hardware functions.

Requires either DRM master or CAP_SYS_ADMIN to run.

If you don’t understand what all of that means, you probably don’t want this. Look at x11grab instead.

#### 26.10.1 Options# TOC

device

DRM device to capture on. Defaults to /dev/dri/card0.

format

Pixel format of the framebuffer. This can be autodetected if you are running Linux 5.7 or later, but needs to be provided for earlier versions. Defaults to bgr0, which is the most common format used by the Linux console and Xorg X server.

format_modifier

Format modifier to signal on output frames. This is necessary to import correctly into some APIs. It can be autodetected if you are running Linux 5.7 or later, but will need to be provided explicitly when needed in earlier versions. See the libdrm documentation for possible values.

crtc_id

KMS CRTC ID to define the capture source. The first active plane on the given CRTC will be used.

plane_id

KMS plane ID to define the capture source. Defaults to the first active plane found if neither crtc_id nor plane_id are specified.

framerate

Framerate to capture at. This is not synchronised to any page flipping or framebuffer changes - it just defines the interval at which the framebuffer is sampled. Sampling faster than the framebuffer update rate will generate independent frames with the same content. Defaults to 30.

#### 26.10.2 Examples# TOC

- Capture from the first active plane, download the result to normal frames and encode. This will only work if the framebuffer is both linear and mappable - if not, the result may be scrambled or fail to download.

```
ffmpeg -f kmsgrab -i - -vf 'hwdownload,format=bgr0' output.mp4

```

- Capture from CRTC ID 42 at 60fps, map the result to VAAPI, convert to NV12 and encode as H.264.

```
ffmpeg -crtc_id 42 -framerate 60 -f kmsgrab -i - -vf 'hwmap=derive_device=vaapi,scale_vaapi=w=1920:h=1080:format=nv12' -c:v h264_vaapi output.mp4

```

- To capture only part of a plane the output can be cropped - this can be used to capture a single window, as long as it has a known absolute position and size. For example, to capture and encode the middle quarter of a 1920x1080 plane:

```
ffmpeg -f kmsgrab -i - -vf 'hwmap=derive_device=vaapi,crop=960:540:480:270,scale_vaapi=960:540:nv12' -c:v h264_vaapi output.mp4

```

### 26.11 lavfi# TOC

Libavfilter input virtual device.

This input device reads data from the open output pads of a libavfilter filtergraph.

For each filtergraph open output, the input device will create a corresponding stream which is mapped to the generated output. The filtergraph is specified through the option graph.

#### 26.11.1 Options# TOC

graph

Specify the filtergraph to use as input. Each video open output must be labelled by a unique string of the form "outN", where N is a number starting from 0 corresponding to the mapped input stream generated by the device. The first unlabelled output is automatically assigned to the "out0" label, but all the others need to be specified explicitly.

The suffix "+subcc" can be appended to the output label to create an extra stream with the closed captions packets attached to that output (experimental; only for EIA-608 / CEA-708 for now). The subcc streams are created after all the normal streams, in the order of the corresponding stream. For example, if there is "out19+subcc", "out7+subcc" and up to "out42", the stream #43 is subcc for stream #7 and stream #44 is subcc for stream #19.

If not specified defaults to the filename specified for the input device.

graph_file

Set the filename of the filtergraph to be read and sent to the other filters. Syntax of the filtergraph is the same as the one specified by the option graph.

dumpgraph

Dump graph to stderr.

#### 26.11.2 Examples# TOC

- Create a color video stream and play it back with ffplay:

```
ffplay -f lavfi -graph "color=c=pink [out0]" dummy

```

- As the previous example, but use filename for specifying the graph description, and omit the "out0" label:

```
ffplay -f lavfi color=c=pink

```

- Create three different video test filtered sources and play them:

```
ffplay -f lavfi -graph "testsrc [out0]; testsrc,hflip [out1]; testsrc,negate [out2]" test3

```

- Read an audio stream from a file using the amovie source and play it back with ffplay:

```
ffplay -f lavfi "amovie=test.wav"

```

- Read an audio stream and a video stream and play it back with ffplay:

```
ffplay -f lavfi "movie=test.avi[out0];amovie=test.wav[out1]"

```

- Dump decoded frames to images and Closed Captions to an RCWT backup:

```
ffmpeg -f lavfi -i "movie=test.ts[out0+subcc]" -map v frame%08d.png -map s -c copy -f rcwt subcc.bin

```

### 26.12 libcdio# TOC

Audio-CD input device based on libcdio.

To enable this input device during configuration you need libcdio installed on your system. It requires the configure option --enable-libcdio.

This device allows playing and grabbing from an Audio-CD.

For example to copy with ffmpeg the entire Audio-CD in /dev/sr0, you may run the command:

```
ffmpeg -f libcdio -i /dev/sr0 cd.wav

```

#### 26.12.1 Options# TOC

speed

Set drive reading speed. Default value is 0.

The speed is specified CD-ROM speed units. The speed is set through the libcdio cdio_cddap_speed_set function. On many CD-ROM drives, specifying a value too large will result in using the fastest speed.

paranoia_mode

Set paranoia recovery mode flags. It accepts one of the following values:

‘disable’

‘verify’

‘overlap’

‘neverskip’

‘full’

Default value is ‘disable’.

For more information about the available recovery modes, consult the paranoia project documentation.

### 26.13 libdc1394# TOC

IIDC1394 input device, based on libdc1394 and libraw1394.

Requires the configure option --enable-libdc1394.

#### 26.13.1 Options# TOC

framerate

Set the frame rate. Default is ntsc, corresponding to a frame rate of 30000/1001.

pixel_format

Select the pixel format. Default is uyvy422.

video_size

Set the video size given as a string such as 640x480 or hd720. Default is qvga.

### 26.14 openal# TOC

The OpenAL input device provides audio capture on all systems with a working OpenAL 1.1 implementation.

To enable this input device during configuration, you need OpenAL headers and libraries installed on your system, and need to configure FFmpeg with --enable-openal.

OpenAL headers and libraries should be provided as part of your OpenAL implementation, or as an additional download (an SDK). Depending on your installation you may need to specify additional flags via the --extra-cflags and --extra-ldflags for allowing the build system to locate the OpenAL headers and libraries.

An incomplete list of OpenAL implementations follows:

Creative

The official Windows implementation, providing hardware acceleration with supported devices and software fallback. See http://openal.org/.

OpenAL Soft

Portable, open source (LGPL) software implementation. Includes backends for the most common sound APIs on the Windows, Linux, Solaris, and BSD operating systems. See http://kcat.strangesoft.net/openal.html.

Apple

OpenAL is part of Core Audio, the official Mac OS X Audio interface. See http://developer.apple.com/technologies/mac/audio-and-video.html

This device allows one to capture from an audio input device handled through OpenAL.

You need to specify the name of the device to capture in the provided filename. If the empty string is provided, the device will automatically select the default device. You can get the list of the supported devices by using the option list_devices.

#### 26.14.1 Options# TOC

channels

Set the number of channels in the captured audio. Only the values 1 (monaural) and 2 (stereo) are currently supported. Defaults to 2.

sample_size

Set the sample size (in bits) of the captured audio. Only the values 8 and 16 are currently supported. Defaults to 16.

sample_rate

Set the sample rate (in Hz) of the captured audio. Defaults to 44.1k.

list_devices

If set to true, print a list of devices and exit. Defaults to false.

#### 26.14.2 Examples# TOC

Print the list of OpenAL supported devices and exit:

```
$ ffmpeg -list_devices true -f openal -i dummy out.ogg

```

Capture from the OpenAL device DR-BT101 via PulseAudio:

```
$ ffmpeg -f openal -i 'DR-BT101 via PulseAudio' out.ogg

```

Capture from the default device (note the empty string ” as filename):

```
$ ffmpeg -f openal -i '' out.ogg

```

Capture from two devices simultaneously, writing to two different files, within the same ffmpeg command:

```
$ ffmpeg -f openal -i 'DR-BT101 via PulseAudio' out1.ogg -f openal -i 'ALSA Default' out2.ogg

```

Note: not all OpenAL implementations support multiple simultaneous capture - try the latest OpenAL Soft if the above does not work.

### 26.15 oss# TOC

Open Sound System input device.

The filename to provide to the input device is the device node representing the OSS input device, and is usually set to /dev/dsp.

For example to grab from /dev/dsp using ffmpeg use the command:

```
ffmpeg -f oss -i /dev/dsp /tmp/oss.wav

```

For more information about OSS see: http://manuals.opensound.com/usersguide/dsp.html

#### 26.15.1 Options# TOC

sample_rate

Set the sample rate in Hz. Default is 48000.

channels

Set the number of channels. Default is 2.

### 26.16 pulse# TOC

PulseAudio input device.

To enable this output device you need to configure FFmpeg with --enable-libpulse.

The filename to provide to the input device is a source device or the string "default"

To list the PulseAudio source devices and their properties you can invoke the command pactl list sources.

More information about PulseAudio can be found on http://www.pulseaudio.org.

#### 26.16.1 Options# TOC

server

Connect to a specific PulseAudio server, specified by an IP address. Default server is used when not provided.

name

Specify the application name PulseAudio will use when showing active clients, by default it is the LIBAVFORMAT_IDENT string.

stream_name

Specify the stream name PulseAudio will use when showing active streams, by default it is "record".

sample_rate

Specify the samplerate in Hz, by default 48kHz is used.

channels

Specify the channels in use, by default 2 (stereo) is set.

frame_size

This option does nothing and is deprecated.

fragment_size

Specify the size in bytes of the minimal buffering fragment in PulseAudio, it will affect the audio latency. By default it is set to 50 ms amount of data.

wallclock

Set the initial PTS using the current time. Default is 1.

#### 26.16.2 Examples# TOC

Record a stream from default device:

```
ffmpeg -f pulse -i default /tmp/pulse.wav

```

### 26.17 sndio# TOC

sndio input device.

To enable this input device during configuration you need libsndio installed on your system.

The filename to provide to the input device is the device node representing the sndio input device, and is usually set to /dev/audio0.

For example to grab from /dev/audio0 using ffmpeg use the command:

```
ffmpeg -f sndio -i /dev/audio0 /tmp/oss.wav

```

#### 26.17.1 Options# TOC

sample_rate

Set the sample rate in Hz. Default is 48000.

channels

Set the number of channels. Default is 2.

### 26.18 video4linux2, v4l2# TOC

Video4Linux2 input video device.

"v4l2" can be used as alias for "video4linux2".

If FFmpeg is built with v4l-utils support (by using the --enable-libv4l2 configure option), it is possible to use it with the -use_libv4l2 input device option.

The name of the device to grab is a file device node, usually Linux systems tend to automatically create such nodes when the device (e.g. an USB webcam) is plugged into the system, and has a name of the kind /dev/videoN, where N is a number associated to the device.

Video4Linux2 devices usually support a limited set of widthxheight sizes and frame rates. You can check which are supported using -list_formats all for Video4Linux2 devices. Some devices, like TV cards, support one or more standards. It is possible to list all the supported standards using -list_standards all.

The time base for the timestamps is 1 microsecond. Depending on the kernel version and configuration, the timestamps may be derived from the real time clock (origin at the Unix Epoch) or the monotonic clock (origin usually at boot time, unaffected by NTP or manual changes to the clock). The -timestamps abs or -ts abs option can be used to force conversion into the real time clock.

Some usage examples of the video4linux2 device with ffmpeg and ffplay:

- List supported formats for a video4linux2 device:

```
ffplay -f video4linux2 -list_formats all /dev/video0

```

- Grab and show the input of a video4linux2 device:

```
ffplay -f video4linux2 -framerate 30 -video_size hd720 /dev/video0

```

- Grab and record the input of a video4linux2 device, leave the frame rate and size as previously set:

```
ffmpeg -f video4linux2 -input_format mjpeg -i /dev/video0 out.mpeg

```

For more information about Video4Linux, check http://linuxtv.org/.

#### 26.18.1 Options# TOC

standard

Set the standard. Must be the name of a supported standard. To get a list of the supported standards, use the list_standards option.

channel

Set the input channel number. Default to -1, which means using the previously selected channel.

video_size

Set the video frame size. The argument must be a string in the form WIDTHxHEIGHT or a valid size abbreviation.

pixel_format

Select the pixel format (only valid for raw video input).

input_format

Set the preferred pixel format (for raw video) or a codec name. This option allows one to select the input format, when several are available.

framerate

Set the preferred video frame rate.

list_formats

List available formats (supported pixel formats, codecs, and frame sizes) and exit.

Available values are:

‘all’

Show all available (compressed and non-compressed) formats.

‘raw’

Show only raw video (non-compressed) formats.

‘compressed’

Show only compressed formats.

list_standards

List supported standards and exit.

Available values are:

‘all’

Show all supported standards.

timestamps, ts

Set type of timestamps for grabbed frames.

Available values are:

‘default’

Use timestamps from the kernel.

‘abs’

Use absolute timestamps (wall clock).

‘mono2abs’

Force conversion from monotonic to absolute timestamps.

Default value is default.

use_libv4l2

Use libv4l2 (v4l-utils) conversion functions. Default is 0.

### 26.19 vfwcap# TOC

VfW (Video for Windows) capture input device.

The filename passed as input is the capture driver number, ranging from 0 to 9. You may use "list" as filename to print a list of drivers. Any other filename will be interpreted as device number 0.

#### 26.19.1 Options# TOC

video_size

Set the video frame size.

framerate

Set the grabbing frame rate. Default value is ntsc, corresponding to a frame rate of 30000/1001.

### 26.20 x11grab# TOC

X11 video input device.

To enable this input device during configuration you need libxcb installed on your system. It will be automatically detected during configuration.

This device allows one to capture a region of an X11 display.

The filename passed as input has the syntax:

```
[hostname]:display_number.screen_number[+x_offset,y_offset]

```

hostname:display_number.screen_number specifies the X11 display name of the screen to grab from. hostname can be omitted, and defaults to "localhost". The environment variable DISPLAY contains the default display name.

x_offset and y_offset specify the offsets of the grabbed area with respect to the top-left border of the X11 screen. They default to 0.

Check the X11 documentation (e.g. man X) for more detailed information.

Use the xdpyinfo program for getting basic information about the properties of your X11 display (e.g. grep for "name" or "dimensions").

For example to grab from :0.0 using ffmpeg:

```
ffmpeg -f x11grab -framerate 25 -video_size cif -i :0.0 out.mpg

```

Grab at position 10,20:

```
ffmpeg -f x11grab -framerate 25 -video_size cif -i :0.0+10,20 out.mpg

```

#### 26.20.1 Options# TOC

select_region

Specify whether to select the grabbing area graphically using the pointer. A value of 1 prompts the user to select the grabbing area graphically by clicking and dragging. A single click with no dragging will select the whole screen. A region with zero width or height will also select the whole screen. This option overwrites the video_size, grab_x, and grab_y options. Default value is 0.

draw_mouse

Specify whether to draw the mouse pointer. A value of 0 specifies not to draw the pointer. Default value is 1.

follow_mouse

Make the grabbed area follow the mouse. The argument can be centered or a number of pixels PIXELS.

When it is specified with "centered", the grabbing region follows the mouse pointer and keeps the pointer at the center of region; otherwise, the region follows only when the mouse pointer reaches within PIXELS (greater than zero) to the edge of region.

For example:

```
ffmpeg -f x11grab -follow_mouse centered -framerate 25 -video_size cif -i :0.0 out.mpg

```

To follow only when the mouse pointer reaches within 100 pixels to edge:

```
ffmpeg -f x11grab -follow_mouse 100 -framerate 25 -video_size cif -i :0.0 out.mpg

```

framerate

Set the grabbing frame rate. Default value is ntsc, corresponding to a frame rate of 30000/1001.

show_region

Show grabbed region on screen.

If show_region is specified with 1, then the grabbing region will be indicated on screen. With this option, it is easy to know what is being grabbed if only a portion of the screen is grabbed.

region_border

Set the region border thickness if -show_region 1 is used. Range is 1 to 128 and default is 3 (XCB-based x11grab only).

For example:

```
ffmpeg -f x11grab -show_region 1 -framerate 25 -video_size cif -i :0.0+10,20 out.mpg

```

With follow_mouse:

```
ffmpeg -f x11grab -follow_mouse centered -show_region 1 -framerate 25 -video_size cif -i :0.0 out.mpg

```

window_id

Grab this window, instead of the whole screen. Default value is 0, which maps to the whole screen (root window).

The id of a window can be found using the xwininfo program, possibly with options -tree and -root.

If the window is later enlarged, the new area is not recorded. Video ends when the window is closed, unmapped (i.e., iconified) or shrunk beyond the video size (which defaults to the initial window size).

This option disables options follow_mouse and select_region.

video_size

Set the video frame size. Default is the full desktop or window.

grab_x

grab_y

Set the grabbing region coordinates. They are expressed as offset from the top left corner of the X11 window and correspond to the x_offset and y_offset parameters in the device name. The default value for both options is 0.

## 27 Output Devices# TOC

Output devices are configured elements in FFmpeg that can write multimedia data to an output device attached to your system.

When you configure your FFmpeg build, all the supported output devices are enabled by default. You can list all available ones using the configure option "–list-outdevs".

You can disable all the output devices using the configure option "–disable-outdevs", and selectively enable an output device using the option "–enable-outdev=OUTDEV", or you can disable a particular input device using the option "–disable-outdev=OUTDEV".

The option "-devices" of the ff* tools will display the list of enabled output devices.

A description of the currently available output devices follows.

### 27.1 alsa# TOC

ALSA (Advanced Linux Sound Architecture) output device.

#### 27.1.1 Examples# TOC

- Play a file on default ALSA device:

```
ffmpeg -i INPUT -f alsa default

```

- Play a file on soundcard 1, audio device 7:

```
ffmpeg -i INPUT -f alsa hw:1,7

```

### 27.2 AudioToolbox# TOC

AudioToolbox output device.

Allows native output to CoreAudio devices on OSX.

The output filename can be empty (or -) to refer to the default system output device or a number that refers to the device index as shown using: -list_devices true.

Alternatively, the audio input device can be chosen by index using the  -audio_device_index <INDEX>  , overriding any device name or index given in the input filename.

All available devices can be enumerated by using -list_devices true, listing all device names, UIDs and corresponding indices.

#### 27.2.1 Options# TOC

AudioToolbox supports the following options:

-audio_device_index <INDEX>

Specify the audio device by its index. Overrides anything given in the output filename.

#### 27.2.2 Examples# TOC

- Print the list of supported devices and output a sine wave to the default device:

```
$ ffmpeg -f lavfi -i sine=r=44100 -f audiotoolbox -list_devices true -

```

- Output a sine wave to the device with the index 2, overriding any output filename:

```
$ ffmpeg -f lavfi -i sine=r=44100 -f audiotoolbox -audio_device_index 2 -

```

### 27.3 caca# TOC

CACA output device.

This output device allows one to show a video stream in CACA window. Only one CACA window is allowed per application, so you can have only one instance of this output device in an application.

To enable this output device you need to configure FFmpeg with --enable-libcaca. libcaca is a graphics library that outputs text instead of pixels.

For more information about libcaca, check: http://caca.zoy.org/wiki/libcaca

#### 27.3.1 Options# TOC

window_title

Set the CACA window title, if not specified default to the filename specified for the output device.

window_size

Set the CACA window size, can be a string of the form widthxheight or a video size abbreviation. If not specified it defaults to the size of the input video.

driver

Set display driver.

algorithm

Set dithering algorithm. Dithering is necessary because the picture being rendered has usually far more colours than the available palette. The accepted values are listed with -list_dither algorithms.

antialias

Set antialias method. Antialiasing smoothens the rendered image and avoids the commonly seen staircase effect. The accepted values are listed with -list_dither antialiases.

charset

Set which characters are going to be used when rendering text. The accepted values are listed with -list_dither charsets.

color

Set color to be used when rendering text. The accepted values are listed with -list_dither colors.

list_drivers

If set to true, print a list of available drivers and exit.

list_dither

List available dither options related to the argument. The argument must be one of algorithms, antialiases, charsets, colors.

#### 27.3.2 Examples# TOC

- The following command shows the ffmpeg output is an CACA window, forcing its size to 80x25:

```
ffmpeg -i INPUT -c:v rawvideo -pix_fmt rgb24 -window_size 80x25 -f caca -

```

- Show the list of available drivers and exit:

```
ffmpeg -i INPUT -pix_fmt rgb24 -f caca -list_drivers true -

```

- Show the list of available dither colors and exit:

```
ffmpeg -i INPUT -pix_fmt rgb24 -f caca -list_dither colors -

```

### 27.4 decklink# TOC

The decklink output device provides playback capabilities for Blackmagic DeckLink devices.

To enable this output device, you need the Blackmagic DeckLink SDK and you need to configure with the appropriate --extra-cflags, --extra-cxxflags and --extra-ldflags. The SDK include directory must be available to both the C and C++ compilers. On Windows, you need to run the IDL files through widl.

DeckLink is very picky about the formats it supports. Pixel format is always uyvy422, framerate, field order and video size must be determined for your device with -list_formats 1. Audio sample rate is always 48 kHz.

#### 27.4.1 Options# TOC

list_devices

If set to true, print a list of devices and exit. Defaults to false. This option is deprecated, please use the -sinks option of ffmpeg to list the available output devices.

list_formats

If set to true, print a list of supported formats and exit. Defaults to false.

preroll

Amount of time to preroll video in seconds. Defaults to 0.5.

duplex_mode

Sets the decklink device duplex/profile mode. Must be ‘unset’, ‘half’, ‘full’, ‘one_sub_device_full’, ‘one_sub_device_half’, ‘two_sub_device_full’, ‘four_sub_device_half’ Defaults to ‘unset’.

Note: DeckLink SDK 11.0 have replaced the duplex property by a profile property. For the DeckLink Duo 2 and DeckLink Quad 2, a profile is shared between any 2 sub-devices that utilize the same connectors. For the DeckLink 8K Pro, a profile is shared between all 4 sub-devices. So DeckLink 8K Pro support four profiles.

Valid profile modes for DeckLink 8K Pro(with DeckLink SDK >= 11.0): ‘one_sub_device_full’, ‘one_sub_device_half’, ‘two_sub_device_full’, ‘four_sub_device_half’

Valid profile modes for DeckLink Quad 2 and DeckLink Duo 2: ‘half’, ‘full’

timing_offset

Sets the genlock timing pixel offset on the used output. Defaults to ‘unset’.

link

Sets the SDI video link configuration on the used output. Must be ‘unset’, ‘single’ link SDI, ‘dual’ link SDI or ‘quad’ link SDI. Defaults to ‘unset’.

sqd

Enable Square Division Quad Split mode for Quad-link SDI output. Must be ‘unset’, ‘true’ or ‘false’. Defaults to unset.

level_a

Enable SMPTE Level A mode on the used output. Must be ‘unset’, ‘true’ or ‘false’. Defaults to unset.

vanc_queue_size

Sets maximum output buffer size in bytes for VANC data. If the buffering reaches this value, outgoing VANC data will be dropped. Defaults to ‘1048576’.

#### 27.4.2 Examples# TOC

- List output devices:

```
ffmpeg -sinks decklink

```

- List supported formats:

```
ffmpeg -i test.avi -f decklink -list_formats 1 'DeckLink Mini Monitor'

```

- Play video clip:

```
ffmpeg -i test.avi -f decklink -pix_fmt uyvy422 'DeckLink Mini Monitor'

```

- Play video clip with non-standard framerate or video size:

```
ffmpeg -i test.avi -f decklink -pix_fmt uyvy422 -s 720x486 -r 24000/1001 'DeckLink Mini Monitor'

```

### 27.5 fbdev# TOC

Linux framebuffer output device.

The Linux framebuffer is a graphic hardware-independent abstraction layer to show graphics on a computer monitor, typically on the console. It is accessed through a file device node, usually /dev/fb0.

For more detailed information read the file Documentation/fb/framebuffer.txt included in the Linux source tree.

#### 27.5.1 Options# TOC

xoffset

yoffset

Set x/y coordinate of top left corner. Default is 0.

#### 27.5.2 Examples# TOC

Play a file on framebuffer device /dev/fb0. Required pixel format depends on current framebuffer settings.

```
ffmpeg -re -i INPUT -c:v rawvideo -pix_fmt bgra -f fbdev /dev/fb0

```

See also http://linux-fbdev.sourceforge.net/, and fbset(1).

### 27.6 oss# TOC

OSS (Open Sound System) output device.

### 27.7 pulse# TOC

PulseAudio output device.

To enable this output device you need to configure FFmpeg with --enable-libpulse.

More information about PulseAudio can be found on http://www.pulseaudio.org

#### 27.7.1 Options# TOC

server

Connect to a specific PulseAudio server, specified by an IP address. Default server is used when not provided.

name

Specify the application name PulseAudio will use when showing active clients, by default it is the LIBAVFORMAT_IDENT string.

stream_name

Specify the stream name PulseAudio will use when showing active streams, by default it is set to the specified output name.

device

Specify the device to use. Default device is used when not provided. List of output devices can be obtained with command pactl list sinks.

buffer_size

buffer_duration

Control the size and duration of the PulseAudio buffer. A small buffer gives more control, but requires more frequent updates.

buffer_size specifies size in bytes while buffer_duration specifies duration in milliseconds.

When both options are provided then the highest value is used (duration is recalculated to bytes using stream parameters). If they are set to 0 (which is default), the device will use the default PulseAudio duration value. By default PulseAudio set buffer duration to around 2 seconds.

prebuf

Specify pre-buffering size in bytes. The server does not start with playback before at least prebuf bytes are available in the buffer. By default this option is initialized to the same value as buffer_size or buffer_duration (whichever is bigger).

minreq

Specify minimum request size in bytes. The server does not request less than minreq bytes from the client, instead waits until the buffer is free enough to request more bytes at once. It is recommended to not set this option, which will initialize this to a value that is deemed sensible by the server.

#### 27.7.2 Examples# TOC

Play a file on default device on default server:

```
ffmpeg  -i INPUT -f pulse "stream name"

```

### 27.8 sndio# TOC

sndio audio output device.

### 27.9 v4l2# TOC

Video4Linux2 output device.

### 27.10 xv# TOC

XV (XVideo) output device.

This output device allows one to show a video stream in a X Window System window.

#### 27.10.1 Options# TOC

display_name

Specify the hardware display name, which determines the display and communications domain to be used.

The display name or DISPLAY environment variable can be a string in the format hostname[:number[.screen_number]].

hostname specifies the name of the host machine on which the display is physically attached. number specifies the number of the display server on that host machine. screen_number specifies the screen to be used on that server.

If unspecified, it defaults to the value of the DISPLAY environment variable.

For example, dual-headed:0.1 would specify screen 1 of display 0 on the machine named “dual-headed”.

Check the X11 specification for more detailed information about the display name format.

window_id

When set to non-zero value then device doesn’t create new window, but uses existing one with provided window_id. By default this options is set to zero and device creates its own window.

window_size

Set the created window size, can be a string of the form widthxheight or a video size abbreviation. If not specified it defaults to the size of the input video. Ignored when window_id is set.

window_x

window_y

Set the X and Y window offsets for the created window. They are both set to 0 by default. The values may be ignored by the window manager. Ignored when window_id is set.

window_title

Set the window title, if not specified default to the filename specified for the output device. Ignored when window_id is set.

For more information about XVideo see http://www.x.org/.

#### 27.10.2 Examples# TOC

- Decode, display and encode video input with ffmpeg at the same time:

```
ffmpeg -i INPUT OUTPUT -f xv display

```

- Decode and display the input video to multiple X11 windows:

```
ffmpeg -i INPUT -f xv normal -vf negate -f xv negated

```

## 28 Resampler Options# TOC

The audio resampler supports the following named options.

Options may be set by specifying -option value in the FFmpeg tools, option=value for the aresample filter, by setting the value explicitly in the SwrContext options or using the libavutil/opt.h API for programmatic use.

uchl, used_chlayout

Set used input channel layout. Default is unset. This option is only used for special remapping.

isr, in_sample_rate

Set the input sample rate. Default value is 0.

osr, out_sample_rate

Set the output sample rate. Default value is 0.

isf, in_sample_fmt

Specify the input sample format. It is set by default to none.

osf, out_sample_fmt

Specify the output sample format. It is set by default to none.

tsf, internal_sample_fmt

Set the internal sample format. Default value is none. This will automatically be chosen when it is not explicitly set.

ichl, in_chlayout

ochl, out_chlayout

Set the input/output channel layout.

See the Channel Layout section in the ffmpeg-utils(1) manual for the required syntax.

clev, center_mix_level

Set the center mix level. It is a value expressed in deciBel, and must be in the interval [-32,32].

slev, surround_mix_level

Set the surround mix level. It is a value expressed in deciBel, and must be in the interval [-32,32].

lfe_mix_level

Set LFE mix into non LFE level. It is used when there is a LFE input but no LFE output. It is a value expressed in deciBel, and must be in the interval [-32,32].

rmvol, rematrix_volume

Set rematrix volume. Default value is 1.0.

rematrix_maxval

Set maximum output value for rematrixing. This can be used to prevent clipping vs. preventing volume reduction. A value of 1.0 prevents clipping.

flags, swr_flags

Set flags used by the converter. Default value is 0.

It supports the following individual flags:

res

force resampling, this flag forces resampling to be used even when the input and output sample rates match.

dither_scale

Set the dither scale. Default value is 1.

dither_method

Set dither method. Default value is 0.

Supported values:

‘rectangular’

select rectangular dither

‘triangular’

select triangular dither

‘triangular_hp’

select triangular dither with high pass

‘lipshitz’

select Lipshitz noise shaping dither.

‘shibata’

select Shibata noise shaping dither.

‘low_shibata’

select low Shibata noise shaping dither.

‘high_shibata’

select high Shibata noise shaping dither.

‘f_weighted’

select f-weighted noise shaping dither

‘modified_e_weighted’

select modified-e-weighted noise shaping dither

‘improved_e_weighted’

select improved-e-weighted noise shaping dither

resampler

Set resampling engine. Default value is swr.

Supported values:

‘swr’

select the native SW Resampler; filter options precision and cheby are not applicable in this case.

‘soxr’

select the SoX Resampler (where available); compensation, and filter options filter_size, phase_shift, exact_rational, filter_type & kaiser_beta, are not applicable in this case.

filter_size

For swr only, set resampling filter size, default value is 32.

phase_shift

For swr only, set resampling phase shift, default value is 10, and must be in the interval [0,30].

linear_interp

Use linear interpolation when enabled (the default). Disable it if you want to preserve speed instead of quality when exact_rational fails.

exact_rational

For swr only, when enabled, try to use exact phase_count based on input and output sample rate. However, if it is larger than 1 << phase_shift, the phase_count will be 1 << phase_shift as fallback. Default is enabled.

cutoff

Set cutoff frequency (swr: 6dB point; soxr: 0dB point) ratio; must be a float value between 0 and 1. Default value is 0.97 with swr, and 0.91 with soxr (which, with a sample-rate of 44100, preserves the entire audio band to 20kHz).

precision

For soxr only, the precision in bits to which the resampled signal will be calculated. The default value of 20 (which, with suitable dithering, is appropriate for a destination bit-depth of 16) gives SoX’s ’High Quality’; a value of 28 gives SoX’s ’Very High Quality’.

cheby

For soxr only, selects passband rolloff none (Chebyshev) & higher-precision approximation for ’irrational’ ratios. Default value is 0.

async

For swr only, simple 1 parameter audio sync to timestamps using stretching, squeezing, filling and trimming. Setting this to 1 will enable filling and trimming, larger values represent the maximum amount in samples that the data may be stretched or squeezed for each second. Default value is 0, thus no compensation is applied to make the samples match the audio timestamps.

first_pts

For swr only, assume the first pts should be this value. The time unit is 1 / sample rate. This allows for padding/trimming at the start of stream. By default, no assumption is made about the first frame’s expected pts, so no padding or trimming is done. For example, this could be set to 0 to pad the beginning with silence if an audio stream starts after the video stream or to trim any samples with a negative pts due to encoder delay.

min_comp

For swr only, set the minimum difference between timestamps and audio data (in seconds) to trigger stretching/squeezing/filling or trimming of the data to make it match the timestamps. The default is that stretching/squeezing/filling and trimming is disabled (min_comp = FLT_MAX).

min_hard_comp

For swr only, set the minimum difference between timestamps and audio data (in seconds) to trigger adding/dropping samples to make it match the timestamps. This option effectively is a threshold to select between hard (trim/fill) and soft (squeeze/stretch) compensation. Note that all compensation is by default disabled through min_comp. The default is 0.1.

comp_duration

For swr only, set duration (in seconds) over which data is stretched/squeezed to make it match the timestamps. Must be a non-negative double float value, default value is 1.0.

max_soft_comp

For swr only, set maximum factor by which data is stretched/squeezed to make it match the timestamps. Must be a non-negative double float value, default value is 0.

matrix_encoding

Select matrixed stereo encoding.

It accepts the following values:

‘none’

select none

‘dolby’

select Dolby

‘dplii’

select Dolby Pro Logic II

Default value is none.

filter_type

For swr only, select resampling filter type. This only affects resampling operations.

It accepts the following values:

‘cubic’

select cubic

‘blackman_nuttall’

select Blackman Nuttall windowed sinc

‘kaiser’

select Kaiser windowed sinc

kaiser_beta

For swr only, set Kaiser window beta value. Must be a double float value in the interval [2,16], default value is 9.

output_sample_bits

For swr only, set number of used output sample bits for dithering. Must be an integer in the interval [0,64], default value is 0, which means it’s not used.

## 29 Scaler Options# TOC

The video scaler supports the following named options.

Options may be set by specifying -option value in the FFmpeg tools, with a few API-only exceptions noted below. For programmatic use, they can be set explicitly in the SwsContext options or through the libavutil/opt.h API.

scaler, scaler_sub

Choose the scaling algorithm to use. Default value is ‘auto’ for both. It accepts the following values:

‘auto’

Aumotic choice. For ‘scaler_sub’, this means the same algorithm as ‘scaler’. For ‘scaler’, this defaults to the scaler flag selected by ‘sws_flags’.

‘bilinear’

Bilinear filter. (AKA triangle filter)

‘bicubic’

2-tap cubic BC-spline (AKA Mitchell-Netravali spline). The B and C parameters can be configured by setting param0 and param1, defaulting to 0.0 and 0.6 respectively.

‘point, neighbor’

Point sampling (AKA nearest neighbor).

‘area’

Area averaging. Equivalent to ‘bilinear’ for upscaling.

‘gaussian’

2-tap Gaussian filter approximation. The sharpness parameter can be configured by setting param0, defaulting to 3.0.

‘sinc’

Unwindowed sinc filter.

‘lanczos’

Lanczos resampling (sinc windowed sinc). The number of filter taps can be configured by setting param0, defaulting to 3.

‘spline’

Unwindowed natural bicubic spline.

sws_flags

Set the scaler flags. This is also used to set the scaling algorithm, though this usage is deprecated in favor of setting ‘scaler’. Only a single algorithm may be selected. Default value is ‘bicubic’.

It accepts the following values:

‘fast_bilinear’

Select fast bilinear scaling algorithm. (Deprecated)

‘bilinear’

Select bilinear scaling algorithm. (Deprecated)

‘bicubic’

Select bicubic scaling algorithm. (Deprecated)

‘experimental’

Select experimental scaling algorithm. (Deprecated)

‘neighbor’

Select nearest neighbor rescaling algorithm. (Deprecated)

‘area’

Select averaging area rescaling algorithm. (Deprecated)

‘bicublin’

Select bicubic scaling algorithm for the luma component, bilinear for chroma components. (Deprecated)

‘gauss’

Select Gaussian rescaling algorithm. (Deprecated)

‘sinc’

Select sinc rescaling algorithm. (Deprecated)

‘lanczos’

Select Lanczos rescaling algorithm. The default width (alpha) is 3 and can be changed by setting param0. (Deprecated)

‘spline’

Select natural bicubic spline rescaling algorithm. (Deprecated)

‘print_info’

Enable printing/debug logging.

‘accurate_rnd’

Enable accurate rounding.

‘full_chroma_int’

Enable full chroma interpolation.

‘full_chroma_inp’

Select full chroma input.

‘bitexact’

Enable bitexact output.

‘unstable’

Allow the use of experimental new code. May subtly affect the output or even produce wrong results. For testing only.

srcw (API only)

Set source width.

srch (API only)

Set source height.

dstw (API only)

Set destination width.

dsth (API only)

Set destination height.

src_format (API only)

Set source pixel format (must be expressed as an integer).

dst_format (API only)

Set destination pixel format (must be expressed as an integer).

src_range (boolean)

If value is set to 1, indicates source is full range. Default value is 0, which indicates source is limited range.

dst_range (boolean)

If value is set to 1, enable full range for destination. Default value is 0, which enables limited range.

gamma (boolean)

If value is set to 1, enable gamma correct scaling. Default value is 0.

param0, param1

Set scaling algorithm parameters. The specified values are specific of some scaling algorithms and ignored by others. The specified values are floating point number values.

sws_dither

Set the dithering algorithm. Accepts one of the following values. Default value is ‘auto’.

‘auto’

automatic choice

‘none’

no dithering

‘bayer’

bayer dither

‘ed’

error diffusion dither

‘a_dither’

arithmetic dither, based using addition

‘x_dither’

arithmetic dither, based using xor (more random/less apparent patterning that a_dither).

alphablend

Set the alpha blending to use when the input has alpha but the output does not. Default value is ‘none’.

‘uniform_color’

Blend onto a uniform background color

‘checkerboard’

Blend onto a checkerboard

‘none’

No blending

sws_backends

Set the allowed swscale backends. This is a flags option, so multiple backends may be combined.

‘auto’

Automatic selection. Equal to either ‘stable’ or ‘all’ depending on whether or not the ‘unstable’ flag is set. This is the default value.

‘stable’

All stable backends.

‘unstable’

All unstable backends.

‘all’

All available backends.

‘legacy’

Legacy swscale code.

‘c’

Template-based reference code.

‘memcpy’

Fast path using libc memcpy.

‘x86’

x86 SIMD kernels.

‘aarch64’

AArch64 NEON kernels.

‘spirv’

Vulkan SPIR-V backend.

## 30 Filtering Introduction# TOC

Filtering in FFmpeg is enabled through the libavfilter library.

In libavfilter, a filter can have multiple inputs and multiple outputs. To illustrate the sorts of things that are possible, we consider the following filtergraph.

```
                [main]
input --> split ---------------------> overlay --> output
            |                             ^
            |[tmp]                  [flip]|
            +-----> crop --> vflip -------+

```

This filtergraph splits the input stream in two streams, then sends one stream through the crop filter and the vflip filter, before merging it back with the other stream by overlaying it on top. You can use the following command to achieve this:

```
ffmpeg -i INPUT -vf "split [main][tmp]; [tmp] crop=iw:ih/2:0:0, vflip [flip]; [main][flip] overlay=0:H/2" OUTPUT

```

The result will be that the top half of the video is mirrored onto the bottom half of the output video.

Filters in the same linear chain are separated by commas, and distinct linear chains of filters are separated by semicolons. In our example, crop,vflip are in one linear chain, split and overlay are separately in another. The points where the linear chains join are labelled by names enclosed in square brackets. In the example, the split filter generates two outputs that are associated to the labels [main] and [tmp].

The stream sent to the second output of split, labelled as [tmp], is processed through the crop filter, which crops away the lower half part of the video, and then vertically flipped. The overlay filter takes in input the first unchanged output of the split filter (which was labelled as [main]), and overlay on its lower half the output generated by the crop,vflip filterchain.

Some filters take in input a list of parameters: they are specified after the filter name and an equal sign, and are separated from each other by a colon.

There exist so-called source filters that do not have an audio/video input, and sink filters that will not have audio/video output.

## 31 graph2dot# TOC

The graph2dot program included in the FFmpeg tools directory can be used to parse a filtergraph description and issue a corresponding textual representation in the dot language.

Invoke the command:

```
graph2dot -h

```

to see how to use graph2dot.

You can then pass the dot description to the dot program (from the graphviz suite of programs) and obtain a graphical representation of the filtergraph.

For example the sequence of commands:

```
echo GRAPH_DESCRIPTION | \
tools/graph2dot -o graph.tmp && \
dot -Tpng graph.tmp -o graph.png && \
display graph.png

```

can be used to create and display an image representing the graph described by the GRAPH_DESCRIPTION string. Note that this string must be a complete self-contained graph, with its inputs and outputs explicitly defined. For example if your command line is of the form:

```
ffmpeg -i infile -vf scale=640:360 outfile

```

your GRAPH_DESCRIPTION string will need to be of the form:

```
nullsrc,scale=640:360,nullsink

```

you may also need to set the nullsrc parameters and add a format filter in order to simulate a specific input file.

## 32 Filtergraph description# TOC

A filtergraph is a directed graph of connected filters. It can contain cycles, and there can be multiple links between a pair of filters. Each link has one input pad on one side connecting it to one filter from which it takes its input, and one output pad on the other side connecting it to one filter accepting its output.

Each filter in a filtergraph is an instance of a filter class registered in the application, which defines the features and the number of input and output pads of the filter.

A filter with no input pads is called a "source", and a filter with no output pads is called a "sink".

### 32.1 Filtergraph syntax# TOC

A filtergraph has a textual representation, which is recognized by the -filter/-vf/-af and -filter_complex options in ffmpeg and -vf/-af in ffplay, and by the avfilter_graph_parse_ptr() function defined in libavfilter/avfilter.h.

A filterchain consists of a sequence of connected filters, each one connected to the previous one in the sequence. A filterchain is represented by a list of ","-separated filter descriptions.

A filtergraph consists of a sequence of filterchains. A sequence of filterchains is represented by a list of ";"-separated filterchain descriptions.

A filter is represented by a string of the form: [in_link_1]...[in_link_N]filter_name@id=arguments[out_link_1]...[out_link_M]

filter_name is the name of the filter class of which the described filter is an instance of, and has to be the name of one of the filter classes registered in the program optionally followed by "@id". The name of the filter class is optionally followed by a string "=arguments".

arguments is a string which contains the parameters used to initialize the filter instance. It may have one of two forms:

- A ’:’-separated list of key=value pairs.

- A ’:’-separated list of value. In this case, the keys are assumed to be the option names in the order they are declared. E.g. the fade filter declares three options in this order – type, start_frame and nb_frames. Then the parameter list in:0:30 means that the value in is assigned to the option type, 0 to start_frame and 30 to nb_frames.

- A ’:’-separated list of mixed direct value and long key=value pairs. The direct value must precede the key=value pairs, and follow the same constraints order of the previous point. The following key=value pairs can be set in any preferred order.

If the option value itself is a list of items (e.g. the format filter takes a list of pixel formats), the items in the list are usually separated by ‘|’.

The list of arguments can be quoted using the character ‘'’ as initial and ending mark, and the character ‘\’ for escaping the characters within the quoted text; otherwise the argument string is considered terminated when the next special character (belonging to the set ‘[]=;,’) is encountered.

A special syntax implemented in the ffmpeg CLI tool allows loading option values from files. This is done be prepending a slash ’/’ to the option name, then the supplied value is interpreted as a path from which the actual value is loaded. E.g.

```
ffmpeg -i <INPUT> -vf drawtext=/text=/tmp/some_text <OUTPUT>

```

will load the text to be drawn from /tmp/some_text. API users wishing to implement a similar feature should use the avfilter_graph_segment_*() functions together with custom IO code.

The name and arguments of the filter are optionally preceded and followed by a list of link labels. A link label allows one to name a link and associate it to a filter output or input pad. The preceding labels in_link_1 ... in_link_N, are associated to the filter input pads, the following labels out_link_1 ... out_link_M, are associated to the output pads.

When two link labels with the same name are found in the filtergraph, a link between the corresponding input and output pad is created.

If an output pad is not labelled, it is linked by default to the first unlabelled input pad of the next filter in the filterchain. For example in the filterchain

```
nullsrc, split[L1], [L2]overlay, nullsink

```

the split filter instance has two output pads, and the overlay filter instance two input pads. The first output pad of split is labelled "L1", the first input pad of overlay is labelled "L2", and the second output pad of split is linked to the second input pad of overlay, which are both unlabelled.

In a filter description, if the input label of the first filter is not specified, "in" is assumed; if the output label of the last filter is not specified, "out" is assumed.

In a complete filterchain all the unlabelled filter input and output pads must be connected. A filtergraph is considered valid if all the filter input and output pads of all the filterchains are connected.

Leading and trailing whitespaces (space, tabs, or line feeds) separating tokens in the filtergraph specification are ignored. This means that the filtergraph can be expressed using empty lines and spaces to improve readability.

For example, the filtergraph:

```
testsrc,split[L1],hflip[L2];[L1][L2] hstack

```

can be represented as:

```
testsrc,
split [L1], hflip [L2];

[L1][L2] hstack

```

Libavfilter will automatically insert scale filters where format conversion is required. It is possible to specify swscale flags for those automatically inserted scalers by prepending sws_flags=flags; to the filtergraph description.

Here is a BNF description of the filtergraph syntax:

```
NAME             ::= sequence of alphanumeric characters and '_'
FILTER_NAME      ::= NAME["@"NAME]
LINKLABEL        ::= "[" NAME "]"
LINKLABELS       ::= LINKLABEL [LINKLABELS]
FILTER_ARGUMENTS ::= sequence of chars (possibly quoted)
FILTER           ::= [LINKLABELS] FILTER_NAME ["=" FILTER_ARGUMENTS] [LINKLABELS]
FILTERCHAIN      ::= FILTER [,FILTERCHAIN]
FILTERGRAPH      ::= [sws_flags=flags;] FILTERCHAIN [;FILTERGRAPH]

```

### 32.2 Notes on filtergraph escaping# TOC

Filtergraph description composition entails several levels of escaping. See the "Quoting and escaping" section in the ffmpeg-utils(1) manual for more information about the employed escaping procedure.

A first level escaping affects the content of each filter option value, which may contain the special character : used to separate values, or one of the escaping characters \'.

A second level escaping affects the whole filter description, which may contain the escaping characters \' or the special characters [],; used by the filtergraph description.

Finally, when you specify a filtergraph on a shell commandline, you need to perform a third level escaping for the shell special characters contained within it.

For example, consider the following string to be embedded in the drawtext filter description text value:

```
this is a 'string': may contain one, or more, special characters

```

This string contains the ' special escaping character, and the : special character, so it needs to be escaped in this way:

```
text=this is a \'string\'\: may contain one, or more, special characters

```

A second level of escaping is required when embedding the filter description in a filtergraph description, in order to escape all the filtergraph special characters. Thus the example above becomes:

```
drawtext=text=this is a \\\'string\\\'\\: may contain one\, or more\, special characters

```

(note that in addition to the \' escaping special characters, also , needs to be escaped).

Finally an additional level of escaping is needed when writing the filtergraph description in a shell command, which depends on the escaping rules of the adopted shell. For example, assuming that \ is special and needs to be escaped with another \, the previous string will finally result in:

```
-vf "drawtext=text=this is a \\\\\\'string\\\\\\'\\\\: may contain one\\, or more\\, special characters"

```

In order to avoid cumbersome escaping when using a commandline tool accepting a filter specification as input, it is advisable to avoid direct inclusion of the filter or options specification in the shell.

For example, in case of the drawtext filter, you might prefer to use the textfile option in place of text to specify the text to render.

## 33 Timeline editing# TOC

Some filters support a generic enable option. For the filters supporting timeline editing, this option can be set to an expression which is evaluated before sending a frame to the filter. If the evaluation is non-zero, the filter will be enabled, otherwise the frame will be sent unchanged to the next filter in the filtergraph.

The expression accepts the following values:

‘t’

timestamp expressed in seconds, NAN if the input timestamp is unknown

‘n’

sequential number of the input frame, starting from 0

‘pos’

the position in the file of the input frame, NAN if unknown; deprecated, do not use

‘w’

‘h’

width and height of the input frame if video

Additionally, these filters support an enable command that can be used to re-define the expression.

Like any other filtering option, the enable option follows the same rules.

For example, to enable a blur filter (smartblur) from 10 seconds to 3 minutes, and a curves filter starting at 3 seconds:

```
smartblur = enable='between(t,10,3*60)',
curves    = enable='gte(t,3)' : preset=cross_process

```

See ffmpeg -filters to view which filters have timeline support.

## 34 Changing options at runtime with a command# TOC

Some options can be changed during the operation of the filter using a command. These options are marked ’T’ on the output of ffmpeg -h filter=<name of filter>. The name of the command is the name of the option and the argument is the new value.

## 35 Options for filters with several inputs (framesync)# TOC

Some filters with several inputs support a common set of options. These options can only be set by name, not with the short notation.

eof_action

The action to take when EOF is encountered on the secondary input; it accepts one of the following values:

repeat

Repeat the last frame (the default).

endall

End both streams.

pass

Pass the main input through.

shortest

If set to 1, force the output to terminate when the shortest input terminates. Default value is 0.

repeatlast

If set to 1, force the filter to extend the last frame of secondary streams until the end of the primary stream. A value of 0 disables this behavior. Default value is 1.

ts_sync_mode

How strictly to sync streams based on secondary input timestamps; it accepts one of the following values:

default

Frame from secondary input with the nearest lower or equal timestamp to the primary input frame.

nearest

Frame from secondary input with the absolute nearest timestamp to the primary input frame.

## 36 Audio Filters# TOC

When you configure your FFmpeg build, you can disable any of the existing filters using --disable-filters. The configure output will show the audio filters included in your build.

Below is a description of the currently available audio filters.

### 36.1 aap# TOC

Apply Affine Projection algorithm to the first audio stream using the second audio stream.

This adaptive filter is used to estimate unknown audio based on multiple input audio samples. Affine projection algorithm can make trade-offs between computation complexity with convergence speed.

A description of the accepted options follows.

order

Set the filter order.

projection

Set the projection order.

mu

Set the filter mu.

delta

Set the coefficient to initialize internal covariance matrix.

out_mode

Set the filter output samples. It accepts the following values:

i

Pass the 1st input.

d

Pass the 2nd input.

o

Pass difference between desired, 2nd input and error signal estimate.

n

Pass difference between input, 1st input and error signal estimate.

e

Pass error signal estimated samples.

Default value is o.

precision

Set which precision to use when processing samples.

auto

Auto pick internal sample format depending on other filters.

float

Always use single-floating point precision sample format.

double

Always use double-floating point precision sample format.

### 36.2 acompressor# TOC

A compressor is mainly used to reduce the dynamic range of a signal. Especially modern music is mostly compressed at a high ratio to improve the overall loudness. It’s done to get the highest attention of a listener, "fatten" the sound and bring more "power" to the track. If a signal is compressed too much it may sound dull or "dead" afterwards or it may start to "pump" (which could be a powerful effect but can also destroy a track completely). The right compression is the key to reach a professional sound and is the high art of mixing and mastering. Because of its complex settings it may take a long time to get the right feeling for this kind of effect.

Compression is done by detecting the volume above a chosen level threshold and dividing it by the factor set with ratio. So if you set the threshold to -12dB and your signal reaches -6dB a ratio of 2:1 will result in a signal at -9dB. Because an exact manipulation of the signal would cause distortion of the waveform the reduction can be levelled over the time. This is done by setting "Attack" and "Release". attack determines how long the signal has to rise above the threshold before any reduction will occur and release sets the time the signal has to fall below the threshold to reduce the reduction again. Shorter signals than the chosen attack time will be left untouched. The overall reduction of the signal can be made up afterwards with the makeup setting. So compressing the peaks of a signal about 6dB and raising the makeup to this level results in a signal twice as loud than the source. To gain a softer entry in the compression the knee flattens the hard edge at the threshold in the range of the chosen decibels.

The filter accepts the following options:

level_in

Set input gain. Default is 1. Range is between 0.015625 and 64.

mode

Set mode of compressor operation. Can be upward or downward. Default is downward.

threshold

If a signal of stream rises above this level it will affect the gain reduction. By default it is 0.125. Range is between 0.00097563 and 1.

ratio

Set a ratio by which the signal is reduced. 1:2 means that if the level rose 4dB above the threshold, it will be only 2dB above after the reduction. Default is 2. Range is between 1 and 20.

attack

Amount of milliseconds the signal has to rise above the threshold before gain reduction starts. Default is 20. Range is between 0.01 and 2000.

release

Amount of milliseconds the signal has to fall below the threshold before reduction is decreased again. Default is 250. Range is between 0.01 and 9000.

makeup

Set the amount by how much signal will be amplified after processing. Default is 1. Range is from 1 to 64.

knee

Curve the sharp knee around the threshold to enter gain reduction more softly. Default is 2.82843. Range is between 1 and 8.

link

Choose if the average level between all channels of input stream or the louder(maximum) channel of input stream affects the reduction. Default is average.

detection

Should the exact signal be taken in case of peak or an RMS one in case of rms. Default is rms which is mostly smoother.

mix

How much to use compressed signal in output. Default is 1. Range is between 0 and 1.

#### 36.2.1 Commands# TOC

This filter supports the all above options as commands.

### 36.3 acontrast# TOC

Simple audio dynamic range compression/expansion filter.

The filter accepts the following options:

contrast

Set contrast. Default is 33. Allowed range is between 0 and 100.

### 36.4 acopy# TOC

Copy the input audio source unchanged to the output. This is mainly useful for testing purposes.

### 36.5 acrossfade# TOC

Apply cross fade from one input audio stream to another input audio stream. The cross fade is applied for specified duration near the end of first stream.

The filter accepts the following options:

inputs, n

Specify the number of inputs to crossfade. When crossfading multiple inputs, each input will be concatenated and crossfaded in sequence, similar to the concat filter. Default is 2.

nb_samples, ns

Specify the number of samples for which the cross fade effect has to last. At the end of the cross fade effect the first input audio will be completely silent. Default is 44100.

duration, d

Specify the duration of the cross fade effect. See the Time duration section in the ffmpeg-utils(1) manual for the accepted syntax. By default the duration is determined by nb_samples. If set this option is used instead of nb_samples.

overlap, o

Should first stream end overlap with second stream start. Default is enabled.

curve1

Set curve for cross fade transition for first stream.

curve2

Set curve for cross fade transition for second stream.

For description of available curve types see afade filter description.

#### 36.5.1 Examples# TOC

- Cross fade from one input to another:

```
ffmpeg -i first.flac -i second.flac -filter_complex acrossfade=d=10:c1=exp:c2=exp output.flac

```

- Cross fade from one input to another but without overlapping:

```
ffmpeg -i first.flac -i second.flac -filter_complex acrossfade=d=10:o=0:c1=exp:c2=exp output.flac

```

Concatenate multiple inputs with cross fade between each:

```
ffmpeg -i first.flac -i second.flac -i third.flac -filter_complex acrossfade=n=3 output.flac

```

### 36.6 acrossover# TOC

Split audio stream into several bands.

This filter splits audio stream into two or more frequency ranges. Summing all streams back will give flat output.

The filter accepts the following options:

split

Set split frequencies. Those must be positive and increasing.

order

Set filter order for each band split. This controls filter roll-off or steepness of filter transfer function. Available values are:

‘2nd’

12 dB per octave.

‘4th’

24 dB per octave.

‘6th’

36 dB per octave.

‘8th’

48 dB per octave.

‘10th’

60 dB per octave.

‘12th’

72 dB per octave.

‘14th’

84 dB per octave.

‘16th’

96 dB per octave.

‘18th’

108 dB per octave.

‘20th’

120 dB per octave.

Default is 4th.

level

Set input gain level. Allowed range is from 0 to 1. Default value is 1.

gains

Set output gain for each band. Default value is 1 for all bands.

precision

Set which precision to use when processing samples.

auto

Auto pick internal sample format depending on other filters.

float

Always use single-floating point precision sample format.

double

Always use double-floating point precision sample format.

Default value is auto.

#### 36.6.1 Examples# TOC

- Split input audio stream into two bands (low and high) with split frequency of 1500 Hz, each band will be in separate stream:

```
ffmpeg -i in.flac -filter_complex 'acrossover=split=1500[LOW][HIGH]' -map '[LOW]' low.wav -map '[HIGH]' high.wav

```

- Same as above, but with higher filter order:

```
ffmpeg -i in.flac -filter_complex 'acrossover=split=1500:order=8th[LOW][HIGH]' -map '[LOW]' low.wav -map '[HIGH]' high.wav

```

- Same as above, but also with additional middle band (frequencies between 1500 and 8000):

```
ffmpeg -i in.flac -filter_complex 'acrossover=split=1500 8000:order=8th[LOW][MID][HIGH]' -map '[LOW]' low.wav -map '[MID]' mid.wav -map '[HIGH]' high.wav

```

### 36.7 acrusher# TOC

Reduce audio bit resolution.

This filter is bit crusher with enhanced functionality. A bit crusher is used to audibly reduce number of bits an audio signal is sampled with. This doesn’t change the bit depth at all, it just produces the effect. Material reduced in bit depth sounds more harsh and "digital". This filter is able to even round to continuous values instead of discrete bit depths. Additionally it has a D/C offset which results in different crushing of the lower and the upper half of the signal. An Anti-Aliasing setting is able to produce "softer" crushing sounds.

Another feature of this filter is the logarithmic mode. This setting switches from linear distances between bits to logarithmic ones. The result is a much more "natural" sounding crusher which doesn’t gate low signals for example. The human ear has a logarithmic perception, so this kind of crushing is much more pleasant. Logarithmic crushing is also able to get anti-aliased.

The filter accepts the following options:

level_in

Set level in.

level_out

Set level out.

bits

Set bit reduction.

mix

Set mixing amount.

mode

Can be linear: lin or logarithmic: log.

dc

Set DC.

aa

Set anti-aliasing.

samples

Set sample reduction.

lfo

Enable LFO. By default disabled.

lforange

Set LFO range.

lforate

Set LFO rate.

#### 36.7.1 Commands# TOC

This filter supports the all above options as commands.

### 36.8 acue# TOC

Delay audio filtering until a given wallclock timestamp. See the cue filter.

### 36.9 adeclick# TOC

Remove impulsive noise from input audio.

Samples detected as impulsive noise are replaced by interpolated samples using autoregressive modelling.

window, w

Set window size, in milliseconds. Allowed range is from 10 to 100. Default value is 55 milliseconds. This sets size of window which will be processed at once.

overlap, o

Set window overlap, in percentage of window size. Allowed range is from 50 to 95. Default value is 75 percent. Setting this to a very high value increases impulsive noise removal but makes whole process much slower.

arorder, a

Set autoregression order, in percentage of window size. Allowed range is from 0 to 25. Default value is 2 percent. This option also controls quality of interpolated samples using neighbour good samples.

threshold, t

Set threshold value. Allowed range is from 1 to 100. Default value is 2. This controls the strength of impulsive noise which is going to be removed. The lower value, the more samples will be detected as impulsive noise.

burst, b

Set burst fusion, in percentage of window size. Allowed range is 0 to 10. Default value is 2. If any two samples detected as noise are spaced less than this value then any sample between those two samples will be also detected as noise.

method, m

Set overlap method.

It accepts the following values:

add, a

Select overlap-add method. Even not interpolated samples are slightly changed with this method.

save, s

Select overlap-save method. Not interpolated samples remain unchanged.

Default value is a.

### 36.10 adeclip# TOC

Remove clipped samples from input audio.

Samples detected as clipped are replaced by interpolated samples using autoregressive modelling.

window, w

Set window size, in milliseconds. Allowed range is from 10 to 100. Default value is 55 milliseconds. This sets size of window which will be processed at once.

overlap, o

Set window overlap, in percentage of window size. Allowed range is from 50 to 95. Default value is 75 percent.

arorder, a

Set autoregression order, in percentage of window size. Allowed range is from 0 to 25. Default value is 8 percent. This option also controls quality of interpolated samples using neighbour good samples.

threshold, t

Set threshold value. Allowed range is from 1 to 100. Default value is 10. Higher values make clip detection less aggressive.

hsize, n

Set size of histogram used to detect clips. Allowed range is from 100 to 9999. Default value is 1000. Higher values make clip detection less aggressive.

method, m

Set overlap method.

It accepts the following values:

add, a

Select overlap-add method. Even not interpolated samples are slightly changed with this method.

save, s

Select overlap-save method. Not interpolated samples remain unchanged.

Default value is a.

### 36.11 adecorrelate# TOC

Apply decorrelation to input audio stream.

The filter accepts the following options:

stages

Set decorrelation stages of filtering. Allowed range is from 1 to 16. Default value is 6.

seed

Set random seed used for setting delay in samples across channels.

### 36.12 adelay# TOC

Delay one or more audio channels.

Samples in delayed channel are filled with silence.

The filter accepts the following option:

delays

Set list of delays in milliseconds for each channel separated by ’|’. Unused delays will be silently ignored. If number of given delays is smaller than number of channels all remaining channels will not be delayed. If you want to delay exact number of samples, append ’S’ to number. If you want instead to delay in seconds, append ’s’ to number.

all

Use last set delay for all remaining channels. By default is disabled. This option if enabled changes how option delays is interpreted.

#### 36.12.1 Examples# TOC

- Delay first channel by 1.5 seconds, the third channel by 0.5 seconds and leave the second channel (and any other channels that may be present) unchanged.

```
adelay=1500|0|500

```

- Delay second channel by 500 samples, the third channel by 700 samples and leave the first channel (and any other channels that may be present) unchanged.

```
adelay=0|500S|700S

```

- Delay all channels by same number of samples:

```
adelay=delays=64S:all=1

```

### 36.13 adenorm# TOC

Remedy denormals in audio by adding extremely low-level noise.

This filter shall be placed before any filter that can produce denormals.

A description of the accepted parameters follows.

level

Set level of added noise in dB. Default is -351. Allowed range is from -451 to -90.

type

Set type of added noise.

dc

Add DC signal.

ac

Add AC signal.

square

Add square signal.

pulse

Add pulse signal.

Default is dc.

#### 36.13.1 Commands# TOC

This filter supports the all above options as commands.

### 36.14 aderivative, aintegral# TOC

Compute derivative/integral of audio stream.

Applying both filters one after another produces original audio.

### 36.15 adrc# TOC

Apply spectral dynamic range controller filter to input audio stream.

A description of the accepted options follows.

transfer

Set the transfer expression.

The expression can contain the following constants:

ch

current channel number

sn

current sample number

nb_channels

number of channels

t

timestamp expressed in seconds

sr

sample rate

p

current frequency power value, in dB

f

current frequency in Hz

Default value is p.

attack

Set the attack in milliseconds. Default is 50 milliseconds. Allowed range is from 1 to 1000 milliseconds.

release

Set the release in milliseconds. Default is 100 milliseconds. Allowed range is from 5 to 2000 milliseconds.

channels

Set which channels to filter, by default all channels in audio stream are filtered.

#### 36.15.1 Commands# TOC

This filter supports the all above options as commands.

#### 36.15.2 Examples# TOC

- Apply spectral compression to all frequencies with threshold of -50 dB and 1:6 ratio:

```
adrc=transfer='if(gt(p,-50),-50+(p-(-50))/6,p)':attack=50:release=100

```

- Similar to above but with 1:2 ratio and filtering only front center channel:

```
adrc=transfer='if(gt(p,-50),-50+(p-(-50))/2,p)':attack=50:release=100:channels=FC

```

- Apply spectral noise gate to all frequencies with threshold of -85 dB and with short attack time and short release time:

```
adrc=transfer='if(lte(p,-85),p-800,p)':attack=1:release=5

```

- Apply spectral expansion to all frequencies with threshold of -10 dB and 1:2 ratio:

```
adrc=transfer='if(lt(p,-10),-10+(p-(-10))*2,p)':attack=50:release=100

```

- Apply limiter to max -60 dB to all frequencies, with attack of 2 ms and release of 10 ms:

```
adrc=transfer='min(p,-60)':attack=2:release=10

```

### 36.16 adynamicequalizer# TOC

Apply dynamic equalization to input audio stream.

A description of the accepted options follows.

threshold

Set the detection threshold used to trigger equalization. Threshold detection is using detection filter. Default value is 0. Allowed range is from 0 to 100.

dfrequency

Set the detection frequency in Hz used for detection filter used to trigger equalization. Default value is 1000 Hz. Allowed range is between 2 and 1000000 Hz.

dqfactor

Set the detection resonance factor for detection filter used to trigger equalization. Default value is 1. Allowed range is from 0.001 to 1000.

tfrequency

Set the target frequency of equalization filter. Default value is 1000 Hz. Allowed range is between 2 and 1000000 Hz.

tqfactor

Set the target resonance factor for target equalization filter. Default value is 1. Allowed range is from 0.001 to 1000.

attack

Set the amount of milliseconds the signal from detection has to rise above the detection threshold before equalization starts. Default is 20. Allowed range is between 1 and 2000.

release

Set the amount of milliseconds the signal from detection has to fall below the detection threshold before equalization ends. Default is 200. Allowed range is between 1 and 2000.

ratio

Set the ratio by which the equalization gain is raised. Default is 1. Allowed range is between 0 and 30.

makeup

Set the makeup offset by which the equalization gain is raised. Default is 0. Allowed range is between 0 and 100.

range

Set the max allowed cut/boost amount. Default is 50. Allowed range is from 1 to 200.

mode

Set the mode of filter operation, can be one of the following:

‘listen’

Output only isolated detection signal.

‘cutbelow’

Cut frequencies below detection threshold.

‘cutabove’

Cut frequencies above detection threshold.

‘boostbelow’

Boost frequencies below detection threshold.

‘boostabove’

Boost frequencies above detection threshold.

Default mode is ‘cutbelow’.

dftype

Set the type of detection filter, can be one of the following:

‘bandpass’

‘lowpass’

‘highpass’

‘peak’

Default type is ‘bandpass’.

tftype

Set the type of target filter, can be one of the following:

‘bell’

‘lowshelf’

‘highshelf’

Default type is ‘bell’.

auto

Automatically gather threshold from detection filter. By default is ‘disabled’. This option is useful to detect threshold in certain time frame of input audio stream, in such case option value is changed at runtime.

Available values are:

‘disabled’

Disable using automatically gathered threshold value.

‘off’

Stop picking threshold value.

‘on’

Start picking threshold value.

‘adaptive’

Adaptively pick threshold value, by calculating sliding window entropy.

precision

Set which precision to use when processing samples.

auto

Auto pick internal sample format depending on other filters.

float

Always use single-floating point precision sample format.

double

Always use double-floating point precision sample format.

#### 36.16.1 Commands# TOC

This filter supports the all above options as commands.

### 36.17 adynamicsmooth# TOC

Apply dynamic smoothing to input audio stream.

A description of the accepted options follows.

sensitivity

Set an amount of sensitivity to frequency fluctations. Default is 2. Allowed range is from 0 to 1e+06.

basefreq

Set a base frequency for smoothing. Default value is 22050. Allowed range is from 2 to 1e+06.

#### 36.17.1 Commands# TOC

This filter supports the all above options as commands.

### 36.18 aecho# TOC

Apply echoing to the input audio.

Echoes are reflected sound and can occur naturally amongst mountains (and sometimes large buildings) when talking or shouting; digital echo effects emulate this behaviour and are often used to help fill out the sound of a single instrument or vocal. The time difference between the original signal and the reflection is the delay, and the loudness of the reflected signal is the decay. Multiple echoes can have different delays and decays.

A description of the accepted parameters follows.

in_gain

Set input gain of reflected signal. Default is 0.6.

out_gain

Set output gain of reflected signal. Default is 0.3.

delays

Set list of time intervals in milliseconds between original signal and reflections separated by ’|’. Allowed range for each delay is (0 - 90000.0]. Default is 1000.

decays

Set list of loudness of reflected signals separated by ’|’. Allowed range for each decay is (0 - 1.0]. Default is 0.5.

#### 36.18.1 Examples# TOC

- Make it sound as if there are twice as many instruments as are actually playing:

```
aecho=0.8:0.88:60:0.4

```

- If delay is very short, then it sounds like a (metallic) robot playing music:

```
aecho=0.8:0.88:6:0.4

```

- A longer delay will sound like an open air concert in the mountains:

```
aecho=0.8:0.9:1000:0.3

```

- Same as above but with one more mountain:

```
aecho=0.8:0.9:1000|1800:0.3|0.25

```

### 36.19 aemphasis# TOC

Audio emphasis filter creates or restores material directly taken from LPs or emphased CDs with different filter curves. E.g. to store music on vinyl the signal has to be altered by a filter first to even out the disadvantages of this recording medium. Once the material is played back the inverse filter has to be applied to restore the distortion of the frequency response.

The filter accepts the following options:

level_in

Set input gain.

level_out

Set output gain.

mode

Set filter mode. For restoring material use reproduction mode, otherwise use production mode. Default is reproduction mode.

type

Set filter type. Selects medium. Can be one of the following:

col

select Columbia.

emi

select EMI.

bsi

select BSI (78RPM).

riaa

select RIAA.

cd

select Compact Disc (CD).

50fm

select 50µs (FM).

75fm

select 75µs (FM).

50kf

select 50µs (FM-KF).

75kf

select 75µs (FM-KF).

#### 36.19.1 Commands# TOC

This filter supports the all above options as commands.

### 36.20 aeval# TOC

Modify an audio signal according to the specified expressions.

This filter accepts one or more expressions (one for each channel), which are evaluated and used to modify a corresponding audio signal.

It accepts the following parameters:

exprs

Set the ’|’-separated expressions list for each separate channel. If the number of input channels is greater than the number of expressions, the last specified expression is used for the remaining output channels.

channel_layout, c

Set output channel layout. If not specified, the channel layout is specified by the number of expressions. If set to ‘same’, it will use by default the same input channel layout.

Each expression in exprs can contain the following constants and functions:

ch

channel number of the current expression

n

number of the evaluated sample, starting from 0

s

sample rate

t

time of the evaluated sample expressed in seconds

nb_in_channels

nb_out_channels

input and output number of channels

val(CH)

the value of input channel with number CH

Note: this filter is slow. For faster processing you should use a dedicated filter.

#### 36.20.1 Examples# TOC

- Half volume:

```
aeval=val(ch)/2:c=same

```

- Invert phase of the second channel:

```
aeval=val(0)|-val(1)

```

### 36.21 aexciter# TOC

An exciter is used to produce high sound that is not present in the original signal. This is done by creating harmonic distortions of the signal which are restricted in range and added to the original signal. An Exciter raises the upper end of an audio signal without simply raising the higher frequencies like an equalizer would do to create a more "crisp" or "brilliant" sound.

The filter accepts the following options:

level_in

Set input level prior processing of signal. Allowed range is from 0 to 64. Default value is 1.

level_out

Set output level after processing of signal. Allowed range is from 0 to 64. Default value is 1.

amount

Set the amount of harmonics added to original signal. Allowed range is from 0 to 64. Default value is 1.

drive

Set the amount of newly created harmonics. Allowed range is from 0.1 to 10. Default value is 8.5.

blend

Set the octave of newly created harmonics. Allowed range is from -10 to 10. Default value is 0.

freq

Set the lower frequency limit of producing harmonics in Hz. Allowed range is from 2000 to 12000 Hz. Default is 7500 Hz.

ceil

Set the upper frequency limit of producing harmonics. Allowed range is from 9999 to 20000 Hz. If value is lower than 10000 Hz no limit is applied.

listen

Mute the original signal and output only added harmonics. By default is disabled.

#### 36.21.1 Commands# TOC

This filter supports the all above options as commands.

### 36.22 afade# TOC

Apply fade-in/out effect to input audio.

A description of the accepted parameters follows.

type, t

Specify the effect type, can be either in for fade-in, or out for a fade-out effect. Default is in.

start_sample, ss

Specify the number of the start sample for starting to apply the fade effect. Default is 0.

nb_samples, ns

Specify the number of samples for which the fade effect has to last. At the end of the fade-in effect the output audio will have the same volume as the input audio, at the end of the fade-out transition the output audio will be silence. Default is 44100.

start_time, st

Specify the start time of the fade effect. Default is 0. The value must be specified as a time duration; see the Time duration section in the ffmpeg-utils(1) manual for the accepted syntax. If set this option is used instead of start_sample.

duration, d

Specify the duration of the fade effect. See the Time duration section in the ffmpeg-utils(1) manual for the accepted syntax. At the end of the fade-in effect the output audio will have the same volume as the input audio, at the end of the fade-out transition the output audio will be silence. By default the duration is determined by nb_samples. If set this option is used instead of nb_samples.

curve

Set curve for fade transition.

It accepts the following values:

tri

select triangular, linear slope (default)

qsin

select quarter of sine wave

hsin

select half of sine wave

esin

select exponential sine wave

log

select logarithmic

ipar

select inverted parabola

qua

select quadratic

cub

select cubic

squ

select square root

cbr

select cubic root

par

select parabola

exp

select exponential

iqsin

select inverted quarter of sine wave

ihsin

select inverted half of sine wave

dese

select double-exponential seat

desi

select double-exponential sigmoid

losi

select logistic sigmoid

sinc

select sine cardinal function

isinc

select inverted sine cardinal function

quat

select quartic

quatr

select quartic root

qsin2

select squared quarter of sine wave

hsin2

select squared half of sine wave

nofade

no fade applied

silence

Set the initial gain for fade-in or final gain for fade-out. Default value is 0.0.

unity

Set the initial gain for fade-out or final gain for fade-in. Default value is 1.0.

#### 36.22.1 Commands# TOC

This filter supports the all above options as commands.

#### 36.22.2 Examples# TOC

- Fade in first 15 seconds of audio:

```
afade=t=in:ss=0:d=15

```

- Fade out last 25 seconds of a 900 seconds audio:

```
afade=t=out:st=875:d=25

```

### 36.23 afftdn# TOC

Denoise audio samples with FFT.

A description of the accepted parameters follows.

noise_reduction, nr

Set the noise reduction in dB, allowed range is 0.01 to 97. Default value is 12 dB.

noise_floor, nf

Set the noise floor in dB, allowed range is -80 to -20. Default value is -50 dB.

noise_type, nt

Set the noise type.

It accepts the following values:

white, w

Select white noise.

vinyl, v

Select vinyl noise.

shellac, s

Select shellac noise.

custom, c

Select custom noise, defined in bn option.

Default value is white noise.

band_noise, bn

Set custom band noise profile for every one of 15 bands. Bands are separated by ’ ’ or ’|’.

residual_floor, rf

Set the residual floor in dB, allowed range is -80 to -20. Default value is -38 dB.

track_noise, tn

Enable noise floor tracking. By default is disabled. With this enabled, noise floor is automatically adjusted.

track_residual, tr

Enable residual tracking. By default is disabled.

output_mode, om

Set the output mode.

It accepts the following values:

input, i

Pass input unchanged.

output, o

Pass noise filtered out.

noise, n

Pass only noise.

Default value is output.

adaptivity, ad

Set the adaptivity factor, used how fast to adapt gains adjustments per each frequency bin. Value 0 enables instant adaptation, while higher values react much slower. Allowed range is from 0 to 1. Default value is 0.5.

floor_offset, fo

Set the noise floor offset factor. This option is used to adjust offset applied to measured noise floor. It is only effective when noise floor tracking is enabled. Allowed range is from -2.0 to 2.0. Default value is 1.0.

noise_link, nl

Set the noise link used for multichannel audio.

It accepts the following values:

none

Use unchanged channel’s noise floor.

min

Use measured min noise floor of all channels.

max

Use measured max noise floor of all channels.

average

Use measured average noise floor of all channels.

Default value is min.

band_multiplier, bm

Set the band multiplier factor, used how much to spread bands across frequency bins. Allowed range is from 0.2 to 5. Default value is 1.25.

sample_noise, sn

Toggle capturing and measurement of noise profile from input audio.

It accepts the following values:

start, begin

Start sample noise capture.

stop, end

Stop sample noise capture and measure new noise band profile.

Default value is none.

gain_smooth, gs

Set gain smooth spatial radius, used to smooth gains applied to each frequency bin. Useful to reduce random music noise artefacts. Higher values increases smoothing of gains. Allowed range is from 0 to 50. Default value is 0.

#### 36.23.1 Commands# TOC

This filter supports the some above mentioned options as commands.

#### 36.23.2 Examples# TOC

- Reduce white noise by 10dB, and use previously measured noise floor of -40dB:

```
afftdn=nr=10:nf=-40

```

- Reduce white noise by 10dB, also set initial noise floor to -80dB and enable automatic tracking of noise floor so noise floor will gradually change during processing:

```
afftdn=nr=10:nf=-80:tn=1

```

- Reduce noise by 20dB, using noise floor of -40dB and using commands to take noise profile of first 0.4 seconds of input audio:

```
asendcmd=0.0 afftdn sn start,asendcmd=0.4 afftdn sn stop,afftdn=nr=20:nf=-40

```

### 36.24 afftfilt# TOC

Apply arbitrary expressions to samples in frequency domain.

real

Set frequency domain real expression for each separate channel separated by ’|’. Default is "re". If the number of input channels is greater than the number of expressions, the last specified expression is used for the remaining output channels.

imag

Set frequency domain imaginary expression for each separate channel separated by ’|’. Default is "im".

Each expression in real and imag can contain the following constants and functions:

sr

sample rate

b

current frequency bin number

nb

number of available bins

ch

channel number of the current expression

chs

number of channels

pts

current frame pts

re

current real part of frequency bin of current channel

im

current imaginary part of frequency bin of current channel

real(b, ch)

Return the value of real part of frequency bin at location (bin,channel)

imag(b, ch)

Return the value of imaginary part of frequency bin at location (bin,channel)

win_size

Set window size. Allowed range is from 16 to 131072. Default is 4096

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

Set window overlap. If set to 1, the recommended overlap for selected window function will be picked. Default is 0.75.

#### 36.24.1 Examples# TOC

- Leave almost only low frequencies in audio:

```
afftfilt="'real=re * (1-clip((b/nb)*b,0,1))':imag='im * (1-clip((b/nb)*b,0,1))'"

```

- Apply robotize effect:

```
afftfilt="real='hypot(re,im)*sin(0)':imag='hypot(re,im)*cos(0)':win_size=512:overlap=0.75"

```

- Apply whisper effect:

```
afftfilt="real='hypot(re,im)*cos((random(0)*2-1)*2*3.14)':imag='hypot(re,im)*sin((random(1)*2-1)*2*3.14)':win_size=128:overlap=0.8"

```

- Apply phase shift:

```
afftfilt="real=re*cos(1)-im*sin(1):imag=re*sin(1)+im*cos(1)"

```

### 36.25 afir# TOC

Apply an arbitrary Finite Impulse Response filter.

This filter is designed for applying long FIR filters, up to 60 seconds long.

It can be used as component for digital crossover filters, room equalization, cross talk cancellation, wavefield synthesis, auralization, ambiophonics, ambisonics and spatialization.

This filter uses the streams higher than first one as FIR coefficients. If the non-first stream holds a single channel, it will be used for all input channels in the first stream, otherwise the number of channels in the non-first stream must be same as the number of channels in the first stream.

It accepts the following parameters:

dry

Set dry gain. This sets input gain.

wet

Set wet gain. This sets final output gain.

length

Set Impulse Response filter length. Default is 1, which means whole IR is processed.

gtype

This option is deprecated, and does nothing.

irnorm

Set norm to be applied to IR coefficients before filtering. Allowed range is from -1 to 2. IR coefficients are normalized with calculated vector norm set by this option. For negative values, no norm is calculated, and IR coefficients are not modified at all. Default is 1.

irlink

For multichannel IR if this option is set to true, all IR channels will be normalized with maximal measured gain of all IR channels coefficients as set by irnorm option. When disabled, all IR coefficients in each IR channel will be normalized independently. Default is true.

irgain

Set gain to be applied to IR coefficients before filtering. Allowed range is 0 to 1. This gain is applied after any gain applied with irnorm option.

irfmt

Set format of IR stream. Can be mono or input. Default is input.

maxir

Set max allowed Impulse Response filter duration in seconds. Default is 30 seconds. Allowed range is 0.1 to 60 seconds.

response

This option is deprecated, and does nothing.

channel

This option is deprecated, and does nothing.

size

This option is deprecated, and does nothing.

rate

This option is deprecated, and does nothing.

minp

Set minimal partition size used for convolution. Default is 8192. Allowed range is from 1 to 65536. Lower values decreases latency at cost of higher CPU usage.

maxp

Set maximal partition size used for convolution. Default is 8192. Allowed range is from 8 to 65536. Lower values may increase CPU usage.

nbirs

Set number of input impulse responses streams which will be switchable at runtime. Allowed range is from 1 to 32. Default is 1.

ir

Set IR stream which will be used for convolution, starting from 0, should always be lower than supplied value by nbirs option. Default is 0. This option can be changed at runtime via commands.

precision

Set which precision to use when processing samples.

auto

Auto pick internal sample format depending on other filters.

float

Always use single-floating point precision sample format.

double

Always use double-floating point precision sample format.

Default value is auto.

irload

Set when to load IR stream. Can be init or access. First one load and prepares all IRs on initialization, second one once on first access of specific IR. Default is init.

#### 36.25.1 Examples# TOC

- Apply reverb to stream using mono IR file as second input, complete command using ffmpeg:

```
ffmpeg -i input.wav -i middle_tunnel_1way_mono.wav -lavfi afir output.wav

```

- Apply true stereo processing given input stereo stream, and two stereo impulse responses for left and right channel, the impulse response files are files with names l_ir.wav and r_ir.wav, and setting irnorm option value:

```
"pan=4C|c0=FL|c1=FL|c2=FR|c3=FR[a];amovie=l_ir.wav[LIR];amovie=r_ir.wav[RIR];[LIR][RIR]amerge[ir];[a][ir]afir=irfmt=input:irnorm=1.2,pan=stereo|FL<c0+c2|FR<c1+c3"

```

- Similar to above example, but with irgain explicitly set to estimated value and with irnorm disabled:

```
"pan=4C|c0=FL|c1=FL|c2=FR|c3=FR[a];amovie=l_ir.wav[LIR];amovie=r_ir.wav[RIR];[LIR][RIR]amerge[ir];[a][ir]afir=irfmt=input:irgain=-5dB:irnom=-1,pan=stereo|FL<c0+c2|FR<c1+c3"

```

### 36.26 aformat# TOC

Set output format constraints for the input audio. The framework will negotiate the most appropriate format to minimize conversions.

It accepts the following parameters:

sample_fmts, f

A ’|’-separated list of requested sample formats.

sample_rates, r

A ’|’-separated list of requested sample rates.

channel_layouts, cl

A ’|’-separated list of requested channel layouts.

See the Channel Layout section in the ffmpeg-utils(1) manual for the required syntax.

If a parameter is omitted, all values are allowed.

Force the output to either unsigned 8-bit or signed 16-bit stereo

```
aformat=sample_fmts=u8|s16:channel_layouts=stereo

```

### 36.27 afreqshift# TOC

Apply frequency shift to input audio samples.

The filter accepts the following options:

shift

Specify frequency shift. Allowed range is -INT_MAX to INT_MAX. Default value is 0.0.

level

Set output gain applied to final output. Allowed range is from 0.0 to 1.0. Default value is 1.0.

order

Set filter order used for filtering. Allowed range is from 1 to 16. Default value is 8.

#### 36.27.1 Commands# TOC

This filter supports the all above options as commands.

### 36.28 afwtdn# TOC

Reduce broadband noise from input samples using Wavelets.

A description of the accepted options follows.

sigma

Set the noise sigma, allowed range is from 0 to 1. Default value is 0. This option controls strength of denoising applied to input samples. Most useful way to set this option is via decibels, eg. -45dB.

levels

Set the number of wavelet levels of decomposition. Allowed range is from 1 to 12. Default value is 10. Setting this too low make denoising performance very poor.

wavet

Set wavelet type for decomposition of input frame. They are sorted by number of coefficients, from lowest to highest. More coefficients means worse filtering speed, but overall better quality. Available wavelets are:

‘sym2’

‘sym4’

‘rbior68’

‘deb10’

‘sym10’

‘coif5’

‘bl3’

percent

Set percent of full denoising. Allowed range is from 0 to 100 percent. Default value is 85 percent or partial denoising.

profile

If enabled, first input frame will be used as noise profile. If first frame samples contain non-noise performance will be very poor.

adaptive

If enabled, input frames are analyzed for presence of noise. If noise is detected with high possibility then input frame profile will be used for processing following frames, until new noise frame is detected.

samples

Set size of single frame in number of samples. Allowed range is from 512 to 65536. Default frame size is 8192 samples.

softness

Set softness applied inside thresholding function. Allowed range is from 0 to 10. Default softness is 1.

#### 36.28.1 Commands# TOC

This filter supports the all above options as commands.

### 36.29 agate# TOC

A gate is mainly used to reduce lower parts of a signal. This kind of signal processing reduces disturbing noise between useful signals.

Gating is done by detecting the volume below a chosen level threshold and dividing it by the factor set with ratio. The bottom of the noise floor is set via range. Because an exact manipulation of the signal would cause distortion of the waveform the reduction can be levelled over time. This is done by setting attack and release.

attack determines how long the signal has to fall below the threshold before any reduction will occur and release sets the time the signal has to rise above the threshold to reduce the reduction again. Shorter signals than the chosen attack time will be left untouched.

level_in

Set input level before filtering. Default is 1. Allowed range is from 0.015625 to 64.

mode

Set the mode of operation. Can be upward or downward. Default is downward. If set to upward mode, higher parts of signal will be amplified, expanding dynamic range in upward direction. Otherwise, in case of downward lower parts of signal will be reduced.

range

Set the level of gain reduction when the signal is below the threshold. Default is 0.06125. Allowed range is from 0 to 1. Setting this to 0 disables reduction and then filter behaves like expander.

threshold

If a signal rises above this level the gain reduction is released. Default is 0.125. Allowed range is from 0 to 1.

ratio

Set a ratio by which the signal is reduced. Default is 2. Allowed range is from 1 to 9000.

attack

Amount of milliseconds the signal has to rise above the threshold before gain reduction stops. Default is 20 milliseconds. Allowed range is from 0.01 to 9000.

release

Amount of milliseconds the signal has to fall below the threshold before the reduction is increased again. Default is 250 milliseconds. Allowed range is from 0.01 to 9000.

makeup

Set amount of amplification of signal after processing. Default is 1. Allowed range is from 1 to 64.

knee

Curve the sharp knee around the threshold to enter gain reduction more softly. Default is 2.828427125. Allowed range is from 1 to 8.

detection

Choose if exact signal should be taken for detection or an RMS like one. Default is rms. Can be peak or rms.

link

Choose if the average level between all channels or the louder channel affects the reduction. Default is average. Can be average or maximum.

#### 36.29.1 Commands# TOC

This filter supports the all above options as commands.

### 36.30 aiir# TOC

Apply an arbitrary Infinite Impulse Response filter.

It accepts the following parameters:

zeros, z

Set B/numerator/zeros/reflection coefficients.

poles, p

Set A/denominator/poles/ladder coefficients.

gains, k

Set channels gains.

dry_gain

Set input gain.

wet_gain

Set output gain.

format, f

Set coefficients format.

‘ll’

lattice-ladder function

‘sf’

analog transfer function

‘tf’

digital transfer function

‘zp’

Z-plane zeros/poles, cartesian (default)

‘pr’

Z-plane zeros/poles, polar radians

‘pd’

Z-plane zeros/poles, polar degrees

‘sp’

S-plane zeros/poles

process, r

Set type of processing.

‘d’

direct processing

‘s’

serial processing

‘p’

parallel processing

precision, e

Set filtering precision.

‘dbl’

double-precision floating-point (default)

‘flt’

single-precision floating-point

‘i32’

32-bit integers

‘i16’

16-bit integers

normalize, n

Normalize filter coefficients, by default is enabled. Enabling it will normalize magnitude response at DC to 0dB.

mix

How much to use filtered signal in output. Default is 1. Range is between 0 and 1.

response

Show IR frequency response, magnitude(magenta), phase(green) and group delay(yellow) in additional video stream. By default it is disabled.

channel

Set for which IR channel to display frequency response. By default is first channel displayed. This option is used only when response is enabled.

size

Set video stream size. This option is used only when response is enabled.

Coefficients in tf and sf format are separated by spaces and are in ascending order.

Coefficients in zp format are separated by spaces and order of coefficients doesn’t matter. Coefficients in zp format are complex numbers with i imaginary unit.

Different coefficients and gains can be provided for every channel, in such case use ’|’ to separate coefficients or gains. Last provided coefficients will be used for all remaining channels.

#### 36.30.1 Examples# TOC

- Apply 2 pole elliptic notch at around 5000Hz for 48000 Hz sample rate:

```
aiir=k=1:z=7.957584807809675810E-1 -2.575128568908332300 3.674839853930788710 -2.57512875289799137 7.957586296317130880E-1:p=1 -2.86950072432325953 3.63022088054647218 -2.28075678147272232 6.361362326477423500E-1:f=tf:r=d

```

- Same as above but in zp format:

```
aiir=k=0.79575848078096756:z=0.80918701+0.58773007i 0.80918701-0.58773007i 0.80884700+0.58784055i 0.80884700-0.58784055i:p=0.63892345+0.59951235i 0.63892345-0.59951235i 0.79582691+0.44198673i 0.79582691-0.44198673i:f=zp:r=s

```

- Apply 3-rd order analog normalized Butterworth low-pass filter, using analog transfer function format:

```
aiir=z=1.3057 0 0 0:p=1.3057 2.3892 2.1860 1:f=sf:r=d

```

### 36.31 alimiter# TOC

The limiter prevents an input signal from rising over a desired threshold. This limiter uses lookahead technology to prevent your signal from distorting. It means that there is a small delay after the signal is processed. Keep in mind that the delay it produces is the attack time you set.

The filter accepts the following options:

level_in

Set input gain. Default is 1.

level_out

Set output gain. Default is 1.

limit

Don’t let signals above this level pass the limiter. Default is 1.

attack

The limiter will reach its attenuation level in this amount of time in milliseconds. Default is 5 milliseconds.

release

Come back from limiting to attenuation 1.0 in this amount of milliseconds. Default is 50 milliseconds.

asc

When gain reduction is always needed ASC takes care of releasing to an average reduction level rather than reaching a reduction of 0 in the release time.

asc_level

Select how much the release time is affected by ASC, 0 means nearly no changes in release time while 1 produces higher release times.

level

Auto level output signal. Default is enabled. This normalizes audio back to 0dB if enabled.

latency

Compensate the delay introduced by using the lookahead buffer set with attack parameter. Also flush the valid audio data in the lookahead buffer when the stream hits EOF.

Depending on picked setting it is recommended to upsample input 2x or 4x times with aresample before applying this filter.

### 36.32 allpass# TOC

Apply a two-pole all-pass filter with central frequency (in Hz) frequency, and filter-width width. An all-pass filter changes the audio’s frequency to phase relationship without changing its frequency to amplitude relationship.

The filter accepts the following options:

frequency, f

Set frequency in Hz.

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

Specify the band-width of a filter in width_type units.

mix, m

How much to use filtered signal in output. Default is 1. Range is between 0 and 1.

channels, c

Specify which channels to filter, by default all available are filtered.

normalize, n

Normalize biquad coefficients, by default is disabled. Enabling it will normalize magnitude response at DC to 0dB.

order, o

Set the filter order, can be 1 or 2. Default is 2.

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

#### 36.32.1 Commands# TOC

This filter supports the following commands:

frequency, f

Change allpass frequency. Syntax for the command is : "frequency"

width_type, t

Change allpass width_type. Syntax for the command is : "width_type"

width, w

Change allpass width. Syntax for the command is : "width"

mix, m

Change allpass mix. Syntax for the command is : "mix"

### 36.33 aloop# TOC

Loop audio samples.

The filter accepts the following options:

loop

Set the number of loops. Setting this value to -1 will result in infinite loops. Default is 0.

size

Set maximal number of samples. Default is 0.

start

Set first sample of loop. Default is 0.

time

Set the time of loop start in seconds. Only used if option named start is set to -1.

### 36.34 amerge# TOC

Merge two or more audio streams into a single multi-channel stream.

All inputs must have the same sample rate, and format.

If inputs do not have the same duration, the output will stop with the shortest.

The filter accepts the following options:

inputs

Set the number of inputs. Default is 2.

layout_mode

This option controls how the output channel layout is determined and if the audio channels are reordered during merge.

legacy

This is the mode how the filter behaved historically so it is the default.

If the channel layouts of the inputs are known and disjoint, and therefore compatible, the channel layout of the output will be set accordingly and the channels will be reordered as necessary. If the channel layouts of the inputs are not disjoint, some of them are unknown, or they are using special channel layouts, such as ambisonics, the output will have all the channels of the first input then all the channels of the second input, in that order, and the channel layout of the output will be the default value corresponding to the total number of channels.

For example, if the first input is in 2.1 (FL+FR+LF) and the second input is FC+BL+BR, then the output will be in 5.1, with the channels in the following order: a1, a2, b1, a3, b2, b3 (a1 is the first channel of the first input, b1 is the first channel of the second input).

On the other hand, if both input are in stereo, the output channels will be in the default order: a1, a2, b1, b2, and the channel layout will be arbitrarily set to 4.0, which may or may not be the expected value.

reset

This mode ignores the input channel layouts and does no channel reordering. The output will have all the channels of the first input, then all the channels of the second input, in that order, and so on.

The output channel layout will only specify the total channel count.

normal

This mode keeps channel name and designation information from the input channels and does no channel reordering. The output will have all the channels of the first input, then all the channels of the second input, in that order, and so on.

#### 36.34.1 Examples# TOC

- Merge two mono files into a stereo stream:

```
amovie=left.wav [l] ; amovie=right.mp3 [r] ; [l] [r] amerge

```

- Multiple merges assuming 1 video stream and 6 audio streams in input.mkv:

```
ffmpeg -i input.mkv -filter_complex "[0:1][0:2][0:3][0:4][0:5][0:6] amerge=inputs=6" -c:a pcm_s16le output.mkv

```

### 36.35 amix# TOC

Mixes multiple audio inputs into a single output.

Note that this filter only supports float samples (the amerge and pan audio filters support many formats). If the amix input has integer samples then aresample will be automatically inserted to perform the conversion to float samples.

It accepts the following parameters:

inputs

The number of inputs. If unspecified, it defaults to 2.

duration

How to determine the end-of-stream.

longest

The duration of the longest input. (default)

shortest

The duration of the shortest input.

first

The duration of the first input.

dropout_transition

The transition time, in seconds, for volume renormalization when an input stream ends. The default value is 2 seconds.

weights

Specify weight of each input audio stream as a sequence of numbers separated by a space. If fewer weights are specified compared to number of inputs, the last weight is assigned to the remaining inputs. Default weight for each input is 1.

normalize

Always scale inputs instead of only doing summation of samples. Beware of heavy clipping if inputs are not normalized prior or after filtering by this filter if this option is disabled. By default is enabled.

#### 36.35.1 Examples# TOC

- This will mix 3 input audio streams to a single output with the same duration as the first input and a dropout transition time of 3 seconds:

```
ffmpeg -i INPUT1 -i INPUT2 -i INPUT3 -filter_complex amix=inputs=3:duration=first:dropout_transition=3 OUTPUT

```

- This will mix one vocal and one music input audio stream to a single output with the same duration as the longest input. The music will have quarter the weight as the vocals, and the inputs are not normalized:

```
ffmpeg -i VOCALS -i MUSIC -filter_complex amix=inputs=2:duration=longest:dropout_transition=0:weights="1 0.25":normalize=0 OUTPUT

```

#### 36.35.2 Commands# TOC

This filter supports the following commands:

weights

normalize

Syntax is same as option with same name.

### 36.36 amultiply# TOC

Multiply first audio stream with second audio stream and store result in output audio stream. Multiplication is done by multiplying each sample from first stream with sample at same position from second stream.

With this element-wise multiplication one can create amplitude fades and amplitude modulations.

### 36.37 anequalizer# TOC

High-order parametric multiband equalizer for each channel.

It accepts the following parameters:

params

This option string is in format: "cchn f=cf w=w g=g t=f | ..." Each equalizer band is separated by ’|’.

chn

Set channel number to which equalization will be applied. If input doesn’t have that channel the entry is ignored.

f

Set central frequency for band. If input doesn’t have that frequency the entry is ignored.

w

Set band width in Hertz.

g

Set band gain in dB.

t

Set filter type for band, optional, can be:

‘0’

Butterworth, this is default.

‘1’

Chebyshev type 1.

‘2’

Chebyshev type 2.

curves

With this option activated frequency response of anequalizer is displayed in video stream.

size

Set video stream size. Only useful if curves option is activated.

mgain

Set max gain that will be displayed. Only useful if curves option is activated. Setting this to a reasonable value makes it possible to display gain which is derived from neighbour bands which are too close to each other and thus produce higher gain when both are activated.

fscale

Set frequency scale used to draw frequency response in video output. Can be linear or logarithmic. Default is logarithmic.

colors

Set color for each channel curve which is going to be displayed in video stream. This is list of color names separated by space or by ’|’. Unrecognised or missing colors will be replaced by white color.

#### 36.37.1 Examples# TOC

- Lower gain by 10 of central frequency 200Hz and width 100 Hz for first 2 channels using Chebyshev type 1 filter:

```
anequalizer=c0 f=200 w=100 g=-10 t=1|c1 f=200 w=100 g=-10 t=1

```

#### 36.37.2 Commands# TOC

This filter supports the following commands:

change

Alter existing filter parameters. Syntax for the commands is : "fN|f=freq|w=width|g=gain"

fN is existing filter number, starting from 0, if no such filter is available error is returned. freq set new frequency parameter. width set new width parameter in Hertz. gain set new gain parameter in dB.

Full filter invocation with asendcmd may look like this: asendcmd=c=’4.0 anequalizer change 0|f=200|w=50|g=1’,anequalizer=...

### 36.38 anlmdn# TOC

Reduce broadband noise in audio samples using Non-Local Means algorithm.

Each sample is adjusted by looking for other samples with similar contexts. This context similarity is defined by comparing their surrounding patches of size p. Patches are searched in an area of r around the sample.

The filter accepts the following options:

strength, s

Set denoising strength. Allowed range is from 0.00001 to 10000. Default value is 0.00001.

patch, p

Set patch radius duration. Allowed range is from 1 to 100 milliseconds. Default value is 2 milliseconds.

research, r

Set research radius duration. Allowed range is from 2 to 300 milliseconds. Default value is 6 milliseconds.

output, o

Set the output mode.

It accepts the following values:

i

Pass input unchanged.

o

Pass noise filtered out.

n

Pass only noise.

Default value is o.

smooth, m

Set smooth factor. Default value is 11. Allowed range is from 1 to 1000.

#### 36.38.1 Commands# TOC

This filter supports the all above options as commands.

### 36.39 anlmf, anlms# TOC

Apply Normalized Least-Mean-(Squares|Fourth) algorithm to the first audio stream using the second audio stream.

This adaptive filter is used to mimic a desired filter by finding the filter coefficients that relate to producing the least mean square of the error signal (difference between the desired, 2nd input audio stream and the actual signal, the 1st input audio stream).

A description of the accepted options follows.

order

Set filter order.

mu

Set filter mu.

eps

Set the filter eps.

leakage

Set the filter leakage.

out_mode

It accepts the following values:

i

Pass the 1st input.

d

Pass the 2nd input.

o

Pass difference between desired, 2nd input and error signal estimate.

n

Pass difference between input, 1st input and error signal estimate.

e

Pass error signal estimated samples.

Default value is o.

precision

Set which precision to use when processing samples.

auto

Auto pick internal sample format depending on other filters.

float

Always use single-floating point precision sample format.

double

Always use double-floating point precision sample format.

#### 36.39.1 Examples# TOC

- One of many usages of this filter is noise reduction, input audio is filtered with same samples that are delayed by fixed amount, one such example for stereo audio is:

```
asplit[a][b],[a]adelay=32S|32S[a],[b][a]anlms=order=128:leakage=0.0005:mu=.5:out_mode=o

```

#### 36.39.2 Commands# TOC

This filter supports the same commands as options, excluding option order.

### 36.40 anull# TOC

Pass the audio source unchanged to the output.

### 36.41 apad# TOC

Pad the end of an audio stream with silence.

This can be used together with ffmpeg -shortest to extend audio streams to the same length as the video stream.

A description of the accepted options follows.

packet_size

Set silence packet size. Default value is 4096.

pad_len

Set the number of samples of silence to add to the end. After the value is reached, the stream is terminated. This option is mutually exclusive with whole_len.

whole_len

Set the minimum total number of samples in the output audio stream. If the value is longer than the input audio length, silence is added to the end, until the value is reached. This option is mutually exclusive with pad_len.

pad_dur

Specify the duration of samples of silence to add. See the Time duration section in the ffmpeg-utils(1) manual for the accepted syntax. Used only if set to non-negative value.

whole_dur

Specify the minimum total duration in the output audio stream. See the Time duration section in the ffmpeg-utils(1) manual for the accepted syntax. Used only if set to non-negative value. If the value is longer than the input audio length, silence is added to the end, until the value is reached. This option is mutually exclusive with pad_dur

If neither the pad_len nor the whole_len nor pad_dur nor whole_dur option is set, the filter will add silence to the end of the input stream indefinitely.

Note that for ffmpeg 4.4 and earlier a zero pad_dur or whole_dur also caused the filter to add silence indefinitely.

#### 36.41.1 Examples# TOC

- Add 1024 samples of silence to the end of the input:

```
apad=pad_len=1024

```

- Make sure the audio output will contain at least 10000 samples, pad the input with silence if required:

```
apad=whole_len=10000

```

- Use ffmpeg to pad the audio input with silence, so that the video stream will always result the shortest and will be converted until the end in the output file when using the shortest option:

```
ffmpeg -i VIDEO -i AUDIO -filter_complex "[1:0]apad" -shortest OUTPUT

```

### 36.42 aphaser# TOC

Add a phasing effect to the input audio.

A phaser filter creates series of peaks and troughs in the frequency spectrum. The position of the peaks and troughs are modulated so that they vary over time, creating a sweeping effect.

A description of the accepted parameters follows.

in_gain

Set input gain. Default is 0.4.

out_gain

Set output gain. Default is 0.74

delay

Set delay in milliseconds. Default is 3.0.

decay

Set decay. Default is 0.4.

speed

Set modulation speed in Hz. Default is 0.5.

type

Set modulation type. Default is triangular.

It accepts the following values:

‘triangular, t’

‘sinusoidal, s’

### 36.43 aphaseshift# TOC

Apply phase shift to input audio samples.

The filter accepts the following options:

shift

Specify phase shift. Allowed range is from -1.0 to 1.0. Default value is 0.0.

level

Set output gain applied to final output. Allowed range is from 0.0 to 1.0. Default value is 1.0.

order

Set filter order used for filtering. Allowed range is from 1 to 16. Default value is 8.

#### 36.43.1 Commands# TOC

This filter supports the all above options as commands.

### 36.44 apsnr# TOC

Measure Audio Peak Signal-to-Noise Ratio.

This filter takes two audio streams for input, and outputs first audio stream. Results are in dB per channel at end of either input.

### 36.45 apsyclip# TOC

Apply Psychoacoustic clipper to input audio stream.

The filter accepts the following options:

level_in

Set input gain. By default it is 1. Range is [0.015625 - 64].

level_out

Set output gain. By default it is 1. Range is [0.015625 - 64].

clip

Set the clipping start value. Default value is 0dBFS or 1.

diff

Output only difference samples, useful to hear introduced distortions. By default is disabled.

adaptive

Set strength of adaptive distortion applied. Default value is 0.5. Allowed range is from 0 to 1.

iterations

Set number of iterations of psychoacoustic clipper. Allowed range is from 1 to 20. Default value is 10.

level

Auto level output signal. Default is disabled. This normalizes audio back to 0dBFS if enabled.

#### 36.45.1 Commands# TOC

This filter supports the all above options as commands.

### 36.46 apulsator# TOC

Audio pulsator is something between an autopanner and a tremolo. But it can produce funny stereo effects as well. Pulsator changes the volume of the left and right channel based on a LFO (low frequency oscillator) with different waveforms and shifted phases. This filter have the ability to define an offset between left and right channel. An offset of 0 means that both LFO shapes match each other. The left and right channel are altered equally - a conventional tremolo. An offset of 50% means that the shape of the right channel is exactly shifted in phase (or moved backwards about half of the frequency) - pulsator acts as an autopanner. At 1 both curves match again. Every setting in between moves the phase shift gapless between all stages and produces some "bypassing" sounds with sine and triangle waveforms. The more you set the offset near 1 (starting from the 0.5) the faster the signal passes from the left to the right speaker.

The filter accepts the following options:

level_in

Set input gain. By default it is 1. Range is [0.015625 - 64].

level_out

Set output gain. By default it is 1. Range is [0.015625 - 64].

mode

Set waveform shape the LFO will use. Can be one of: sine, triangle, square, sawup or sawdown. Default is sine.

amount

Set modulation. Define how much of original signal is affected by the LFO.

offset_l

Set left channel offset. Default is 0. Allowed range is [0 - 1].

offset_r

Set right channel offset. Default is 0.5. Allowed range is [0 - 1].

width

Set pulse width. Default is 1. Allowed range is [0 - 2].

timing

Set possible timing mode. Can be one of: bpm, ms or hz. Default is hz.

bpm

Set bpm. Default is 120. Allowed range is [30 - 300]. Only used if timing is set to bpm.

ms

Set ms. Default is 500. Allowed range is [10 - 2000]. Only used if timing is set to ms.

hz

Set frequency in Hz. Default is 2. Allowed range is [0.01 - 100]. Only used if timing is set to hz.

### 36.47 aresample# TOC

Resample the input audio to the specified parameters, using the libswresample library. If none are specified then the filter will automatically convert between its input and output.

This filter is also able to stretch/squeeze the audio data to make it match the timestamps or to inject silence / cut out audio to make it match the timestamps, do a combination of both or do neither.

The filter accepts the syntax [sample_rate:]resampler_options, where sample_rate expresses a sample rate and resampler_options is a list of key=value pairs, separated by ":". See the "Resampler Options" section in the ffmpeg-resampler(1) manual for the complete list of supported options.

#### 36.47.1 Examples# TOC

- Resample the input audio to 44100Hz:

```
aresample=44100

```

- Stretch/squeeze samples to the given timestamps, with a maximum of 1000 samples per second compensation:

```
aresample=async=1000

```

### 36.48 areverse# TOC

Reverse an audio clip.

Warning: This filter requires memory to buffer the entire clip, so trimming is suggested.

#### 36.48.1 Examples# TOC

- Take the first 5 seconds of a clip, and reverse it.

```
atrim=end=5,areverse

```

### 36.49 arls# TOC

Apply Recursive Least Squares algorithm to the first audio stream using the second audio stream.

This adaptive filter is used to mimic a desired filter by recursively finding the filter coefficients that relate to producing the minimal weighted linear least squares cost function of the error signal (difference between the desired, 2nd input audio stream and the actual signal, the 1st input audio stream).

A description of the accepted options follows.

order

Set the filter order.

lambda

Set the forgetting factor.

delta

Set the coefficient to initialize internal covariance matrix.

out_mode

Set the filter output samples. It accepts the following values:

i

Pass the 1st input.

d

Pass the 2nd input.

o

Pass difference between desired, 2nd input and error signal estimate.

n

Pass difference between input, 1st input and error signal estimate.

e

Pass error signal estimated samples.

Default value is o.

precision

Set which precision to use when processing samples.

auto

Auto pick internal sample format depending on other filters.

float

Always use single-floating point precision sample format.

double

Always use double-floating point precision sample format.

### 36.50 arnndn# TOC

Reduce noise from speech using Recurrent Neural Networks.

This filter accepts the following options:

model, m

Set train model file to load. This option is always required.

mix

Set how much to mix filtered samples into final output. Allowed range is from -1 to 1. Default value is 1. Negative values are special, they set how much to keep filtered noise in the final filter output. Set this option to -1 to hear actual noise removed from input signal.

#### 36.50.1 Commands# TOC

This filter supports the all above options as commands.

### 36.51 asdr# TOC

Measure Audio Signal-to-Distortion Ratio.

This filter takes two audio streams for input, and outputs first audio stream. Results are in dB per channel at end of either input.

### 36.52 asetnsamples# TOC

Set the number of samples per each output audio frame.

The last output packet may contain a different number of samples, as the filter will flush all the remaining samples when the input audio signals its end.

The filter accepts the following options:

nb_out_samples, n

Set the number of frames per each output audio frame. The number is intended as the number of samples per each channel. Default value is 1024.

pad, p

If set to 1, the filter will pad the last audio frame with zeroes, so that the last frame will contain the same number of samples as the previous ones. Default value is 1.

For example, to set the number of per-frame samples to 1234 and disable padding for the last frame, use:

```
asetnsamples=n=1234:p=0

```

### 36.53 asetrate# TOC

Set the sample rate without altering the PCM data. This will result in a change of speed and pitch.

The filter accepts the following options:

sample_rate, r

Set the output sample rate. Default is 44100 Hz.

### 36.54 ashowinfo# TOC

Show a line containing various information for each input audio frame. The input audio is not modified.

The shown line contains a sequence of key/value pairs of the form key:value.

The following values are shown in the output:

n

The (sequential) number of the input frame, starting from 0.

pts

The presentation timestamp of the input frame, in time base units; the time base depends on the filter input pad, and is usually 1/sample_rate.

pts_time

The presentation timestamp of the input frame in seconds.

fmt

The sample format.

chlayout

The channel layout.

rate

The sample rate for the audio frame.

nb_samples

The number of samples (per channel) in the frame.

checksum

The Adler-32 checksum (printed in hexadecimal) of the audio data. For planar audio, the data is treated as if all the planes were concatenated.

plane_checksums

A list of Adler-32 checksums for each data plane.

### 36.55 asisdr# TOC

Measure Audio Scaled-Invariant Signal-to-Distortion Ratio.

This filter takes two audio streams for input, and outputs first audio stream. Results are in dB per channel at end of either input.

### 36.56 asoftclip# TOC

Apply audio soft clipping.

Soft clipping is a type of distortion effect where the amplitude of a signal is saturated along a smooth curve, rather than the abrupt shape of hard-clipping.

This filter accepts the following options:

type

Set type of soft-clipping.

It accepts the following values:

hard

tanh

atan

cubic

exp

alg

quintic

sin

erf

threshold

Set threshold from where to start clipping. Default value is 0dB or 1.

output

Set gain applied to output. Default value is 0dB or 1.

param

Set additional parameter which controls sigmoid function.

oversample

Set oversampling factor.

#### 36.56.1 Commands# TOC

This filter supports the all above options as commands.

### 36.57 aspectralstats# TOC

Display frequency domain statistical information about the audio channels. Statistics are calculated and stored as metadata for each audio channel and for each audio frame.

It accepts the following option:

win_size

Set the window length in samples. Default value is 2048. Allowed range is from 32 to 65536.

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

Set window overlap. Allowed range is from 0 to 1. Default value is 0.5.

measure

Select the parameters which are measured. The metadata keys can be used as flags, default is all which measures everything. none disables all measurement.

A list of each metadata key follows:

mean

variance

centroid

spread

skewness

kurtosis

entropy

flatness

crest

flux

slope

decrease

rolloff

### 36.58 asr# TOC

Automatic Speech Recognition

This filter uses PocketSphinx for speech recognition. To enable compilation of this filter, you need to configure FFmpeg with --enable-pocketsphinx.

It accepts the following options:

rate

Set sampling rate of input audio. Defaults is 16000. This need to match speech models, otherwise one will get poor results.

hmm

Set dictionary containing acoustic model files.

dict

Set pronunciation dictionary.

lm

Set language model file.

lmctl

Set language model set.

lmname

Set which language model to use.

logfn

Set output for log messages.

The filter exports recognized speech as the frame metadata lavfi.asr.text.

### 36.59 astats# TOC

Display time domain statistical information about the audio channels. Statistics are calculated and displayed for each audio channel and, where applicable, an overall figure is also given.

It accepts the following option:

length

Short window length in seconds, used for peak and through RMS measurement. Default is 0.05 (50 milliseconds). Allowed range is [0 - 10].

metadata

Set metadata injection. All the metadata keys are prefixed with lavfi.astats.X, where X is channel number starting from 1 or string Overall. Default is disabled.

Available keys for each channel are: Bit_depth Crest_factor DC_offset Dynamic_range Entropy Flat_factor Max_difference Max_level Mean_difference Min_difference Min_level Noise_floor Noise_floor_count Number_of_Infs Number_of_NaNs Number_of_denormals Peak_count Abs_Peak_count Peak_level RMS_difference RMS_peak RMS_trough Zero_crossings Zero_crossings_rate

and for Overall: Bit_depth DC_offset Entropy Flat_factor Max_difference Max_level Mean_difference Min_difference Min_level Noise_floor Noise_floor_count Number_of_Infs Number_of_NaNs Number_of_denormals Number_of_samples Peak_count Abs_Peak_count Peak_level RMS_difference RMS_level RMS_peak RMS_trough

For example, a full key looks like lavfi.astats.1.DC_offset or lavfi.astats.Overall.Peak_count.

Read below for the description of the keys.

reset

Set the number of frames over which cumulative stats are calculated before being reset. Default is disabled.

measure_perchannel

Select the parameters which are measured per channel. The metadata keys can be used as flags, default is all which measures everything. none disables all per channel measurement.

measure_overall

Select the parameters which are measured overall. The metadata keys can be used as flags, default is all which measures everything. none disables all overall measurement.

A description of the measure keys follow:

none

no measures

all

all measures

Bit_depth

overall bit depth of audio, i.e. number of bits used for each sample

Crest_factor

standard ratio of peak to RMS level (note: not in dB)

DC_offset

mean amplitude displacement from zero

Dynamic_range

measured dynamic range of audio in dB

Entropy

entropy measured across whole audio, entropy of value near 1.0 is typically measured for white noise

Flat_factor

flatness (i.e. consecutive samples with the same value) of the signal at its peak levels (i.e. either Min_level or Max_level)

Max_difference

maximal difference between two consecutive samples

Max_level

maximal sample level

Mean_difference

mean difference between two consecutive samples, i.e. the average of each difference between two consecutive samples

Min_difference

minimal difference between two consecutive samples

Min_level

minimal sample level

Noise_floor

minimum local peak measured in dBFS over a short window

Noise_floor_count

number of occasions (not the number of samples) that the signal attained Noise floor

Number_of_Infs

number of samples with an infinite value

Number_of_NaNs

number of samples with a NaN (not a number) value

Number_of_denormals

number of samples with a subnormal value

Number_of_samples

number of samples

Peak_count

number of occasions (not the number of samples) that the signal attained either Min_level or Max_level

Abs_Peak_count

number of occasions that the absolute samples taken from the signal attained max absolute value of Min_level and Max_level

Peak_level

standard peak level measured in dBFS

RMS_difference

Root Mean Square difference between two consecutive samples

RMS_level

standard RMS level measured in dBFS

RMS_peak

RMS_trough

peak and through values for RMS level measured over a short window, measured in dBFS.

Zero crossings

number of points where the waveform crosses the zero level axis

Zero crossings rate

rate of Zero crossings and number of audio samples

### 36.60 asubboost# TOC

Boost subwoofer frequencies.

The filter accepts the following options:

dry

Set dry gain, how much of original signal is kept. Allowed range is from 0 to 1. Default value is 1.0.

wet

Set wet gain, how much of filtered signal is kept. Allowed range is from 0 to 1. Default value is 1.0.

boost

Set max boost factor. Allowed range is from 1 to 12. Default value is 2.

decay

Set delay line decay gain value. Allowed range is from 0 to 1. Default value is 0.0.

feedback

Set delay line feedback gain value. Allowed range is from 0 to 1. Default value is 0.9.

cutoff

Set cutoff frequency in Hertz. Allowed range is 50 to 900. Default value is 100.

slope

Set slope amount for cutoff frequency. Allowed range is 0.0001 to 1. Default value is 0.5.

delay

Set delay. Allowed range is from 1 to 100. Default value is 20.

channels

Set the channels to process. Default value is all available.

#### 36.60.1 Commands# TOC

This filter supports the all above options as commands.

### 36.61 asubcut# TOC

Cut subwoofer frequencies.

This filter allows to set custom, steeper roll off than highpass filter, and thus is able to more attenuate frequency content in stop-band.

The filter accepts the following options:

cutoff

Set cutoff frequency in Hertz. Allowed range is 2 to 200. Default value is 20.

order

Set filter order. Available values are from 3 to 20. Default value is 10.

level

Set input gain level. Allowed range is from 0 to 1. Default value is 1.

#### 36.61.1 Commands# TOC

This filter supports the all above options as commands.

### 36.62 asupercut# TOC

Cut super frequencies.

The filter accepts the following options:

cutoff

Set cutoff frequency in Hertz. Allowed range is 20000 to 192000. Default value is 20000.

order

Set filter order. Available values are from 3 to 20. Default value is 10.

level

Set input gain level. Allowed range is from 0 to 1. Default value is 1.

#### 36.62.1 Commands# TOC

This filter supports the all above options as commands.

### 36.63 asuperpass# TOC

Apply high order Butterworth band-pass filter.

The filter accepts the following options:

centerf

Set center frequency in Hertz. Allowed range is 2 to 999999. Default value is 1000.

order

Set filter order. Available values are from 4 to 20. Default value is 4.

qfactor

Set Q-factor. Allowed range is from 0.01 to 100. Default value is 1.

level

Set input gain level. Allowed range is from 0 to 2. Default value is 1.

#### 36.63.1 Commands# TOC

This filter supports the all above options as commands.

### 36.64 asuperstop# TOC

Apply high order Butterworth band-stop filter.

The filter accepts the following options:

centerf

Set center frequency in Hertz. Allowed range is 2 to 999999. Default value is 1000.

order

Set filter order. Available values are from 4 to 20. Default value is 4.

qfactor

Set Q-factor. Allowed range is from 0.01 to 100. Default value is 1.

level

Set input gain level. Allowed range is from 0 to 2. Default value is 1.

#### 36.64.1 Commands# TOC

This filter supports the all above options as commands.

### 36.65 atempo# TOC

Adjust audio tempo.

The filter accepts exactly one parameter, the audio tempo. If not specified then the filter will assume nominal 1.0 tempo. Tempo must be in the [0.5, 100.0] range.

Note that tempo greater than 2 will skip some samples rather than blend them in. If for any reason this is a concern it is always possible to daisy-chain several instances of atempo to achieve the desired product tempo.

#### 36.65.1 Examples# TOC

- Slow down audio to 80% tempo:

```
atempo=0.8

```

- To speed up audio to 300% tempo:

```
atempo=3

```

- To speed up audio to 300% tempo by daisy-chaining two atempo instances:

```
atempo=sqrt(3),atempo=sqrt(3)

```

#### 36.65.2 Commands# TOC

This filter supports the following commands:

tempo

Change filter tempo scale factor. Syntax for the command is : "tempo"

### 36.66 atilt# TOC

Apply spectral tilt filter to audio stream.

This filter apply any spectral roll-off slope over any specified frequency band.

The filter accepts the following options:

freq

Set central frequency of tilt in Hz. Default is 10000 Hz.

slope

Set slope direction of tilt. Default is 0. Allowed range is from -1 to 1.

width

Set width of tilt. Default is 1000. Allowed range is from 100 to 10000.

order

Set order of tilt filter.

level

Set input volume level. Allowed range is from 0 to 4. Default is 1.

#### 36.66.1 Commands# TOC

This filter supports the all above options as commands.

### 36.67 atrim# TOC

Trim the input so that the output contains one continuous subpart of the input.

It accepts the following parameters:

start

Timestamp (in seconds) of the start of the section to keep. I.e. the audio sample with the timestamp start will be the first sample in the output.

end

Specify time of the first audio sample that will be dropped, i.e. the audio sample immediately preceding the one with the timestamp end will be the last sample in the output.

start_pts

Same as start, except this option sets the start timestamp in samples instead of seconds.

end_pts

Same as end, except this option sets the end timestamp in samples instead of seconds.

duration

The maximum duration of the output in seconds.

start_sample

The number of the first sample that should be output.

end_sample

The number of the first sample that should be dropped.

start, end, and duration are expressed as time duration specifications; see the Time duration section in the ffmpeg-utils(1) manual.

Note that the first two sets of the start/end options and the duration option look at the frame timestamp, while the _sample options simply count the samples that pass through the filter. So start/end_pts and start/end_sample will give different results when the timestamps are wrong, inexact or do not start at zero. Also note that this filter does not modify the timestamps. If you wish to have the output timestamps start at zero, insert the asetpts filter after the atrim filter.

If multiple start or end options are set, this filter tries to be greedy and keep all samples that match at least one of the specified constraints. To keep only the part that matches all the constraints at once, chain multiple atrim filters.

The defaults are such that all the input is kept. So it is possible to set e.g. just the end values to keep everything before the specified time.

Examples:

- Drop everything except the second minute of input:

```
ffmpeg -i INPUT -af atrim=60:120

```

- Keep only the first 1000 samples:

```
ffmpeg -i INPUT -af atrim=end_sample=1000

```

### 36.68 axcorrelate# TOC

Calculate normalized windowed cross-correlation between two input audio streams.

Resulted samples are always between -1 and 1 inclusive. If result is 1 it means two input samples are highly correlated in that selected segment. Result 0 means they are not correlated at all. If result is -1 it means two input samples are out of phase, which means they cancel each other.

The filter accepts the following options:

size

Set size of segment over which cross-correlation is calculated. Default is 256. Allowed range is from 2 to 131072.

algo

Set algorithm for cross-correlation. Can be slow or fast or best. Default is best. Fast algorithm assumes mean values over any given segment are always zero and thus need much less calculations to make. This is generally not true, but is valid for typical audio streams.

#### 36.68.1 Examples# TOC

- Calculate correlation between channels in stereo audio stream:

```
ffmpeg -i stereo.wav -af channelsplit,axcorrelate=size=1024:algo=fast correlation.wav

```

### 36.69 bandpass# TOC

Apply a two-pole Butterworth band-pass filter with central frequency frequency, and (3dB-point) band-width width. The csg option selects a constant skirt gain (peak gain = Q) instead of the default: constant 0dB peak gain. The filter roll off at 6dB per octave (20dB per decade).

The filter accepts the following options:

frequency, f

Set the filter’s central frequency. Default is 3000.

csg

Constant skirt gain if set to 1. Defaults to 0.

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

Specify the band-width of a filter in width_type units.

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

#### 36.69.1 Commands# TOC

This filter supports the following commands:

frequency, f

Change bandpass frequency. Syntax for the command is : "frequency"

width_type, t

Change bandpass width_type. Syntax for the command is : "width_type"

width, w

Change bandpass width. Syntax for the command is : "width"

mix, m

Change bandpass mix. Syntax for the command is : "mix"

### 36.70 bandreject# TOC

Apply a two-pole Butterworth band-reject filter with central frequency frequency, and (3dB-point) band-width width. The filter roll off at 6dB per octave (20dB per decade).

The filter accepts the following options:

frequency, f

Set the filter’s central frequency. Default is 3000.

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

Specify the band-width of a filter in width_type units.

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

#### 36.70.1 Commands# TOC

This filter supports the following commands:

frequency, f

Change bandreject frequency. Syntax for the command is : "frequency"

width_type, t

Change bandreject width_type. Syntax for the command is : "width_type"

width, w

Change bandreject width. Syntax for the command is : "width"

mix, m

Change bandreject mix. Syntax for the command is : "mix"

### 36.71 bass, lowshelf# TOC

Boost or cut the bass (lower) frequencies of the audio using a two-pole shelving filter with a response similar to that of a standard hi-fi’s tone-controls. This is also known as shelving equalisation (EQ).

The filter accepts the following options:

gain, g

Give the gain at 0 Hz. Its useful range is about -20 (for a large cut) to +20 (for a large boost). Beware of clipping when using a positive gain.

frequency, f

Set the filter’s central frequency and so can be used to extend or reduce the frequency range to be boosted or cut. The default value is 100 Hz.

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

#### 36.71.1 Commands# TOC

This filter supports the following commands:

frequency, f

Change bass frequency. Syntax for the command is : "frequency"

width_type, t

Change bass width_type. Syntax for the command is : "width_type"

width, w

Change bass width. Syntax for the command is : "width"

gain, g

Change bass gain. Syntax for the command is : "gain"

mix, m

Change bass mix. Syntax for the command is : "mix"

### 36.72 biquad# TOC

Apply a biquad IIR filter with the given coefficients. Where b0, b1, b2 and a0, a1, a2 are the numerator and denominator coefficients respectively. and channels, c specify which channels to filter, by default all available are filtered.

#### 36.72.1 Commands# TOC

This filter supports the following commands:

a0

a1

a2

b0

b1

b2

Change biquad parameter. Syntax for the command is : "value"

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

### 36.73 bs2b# TOC

Bauer stereo to binaural transformation, which improves headphone listening of stereo audio records.

To enable compilation of this filter you need to configure FFmpeg with --enable-libbs2b.

It accepts the following parameters:

profile

Pre-defined crossfeed level.

default

Default level (fcut=700, feed=50).

cmoy

Chu Moy circuit (fcut=700, feed=60).

jmeier

Jan Meier circuit (fcut=650, feed=95).

fcut

Cut frequency (in Hz).

feed

Feed level (in Hz).

### 36.74 channelmap# TOC

Remap input channels to new locations.

It accepts the following parameters:

map

Map channels from input to output. The argument is a ’|’-separated list of mappings, each in the in_channel-out_channel or in_channel form. in_channel can be either the name of the input channel (e.g. FL for front left) or its index in the input channel layout. out_channel is the name of the output channel or its index in the output channel layout. If out_channel is not given then it is implicitly an index, starting with zero and increasing by one for each mapping. Mixing different types of mappings is not allowed and will result in a parse error.

channel_layout

The channel layout of the output stream. If not specified, then filter will guess it based on the out_channel names or the number of mappings. Guessed layouts will not necessarily contain channels in the order of the mappings.

If no mapping is present, the filter will implicitly map input channels to output channels, preserving indices.

#### 36.74.1 Examples# TOC

- For example, assuming a 5.1+downmix input MOV file,

```
ffmpeg -i in.mov -filter 'channelmap=map=DL-FL|DR-FR' out.wav

```

will create an output WAV file tagged as stereo from the downmix channels of the input.

- To fix a 5.1 WAV improperly encoded in AAC’s native channel order

```
ffmpeg -i in.wav -filter 'channelmap=1|2|0|5|3|4:5.1' out.wav

```

### 36.75 channelsplit# TOC

Split each channel from an input audio stream into a separate output stream.

It accepts the following parameters:

channel_layout

The channel layout of the input stream. The default is "stereo".

channels

A channel layout describing the channels to be extracted as separate output streams or "all" to extract each input channel as a separate stream. The default is "all".

Choosing channels not present in channel layout in the input will result in an error.

#### 36.75.1 Examples# TOC

- For example, assuming a stereo input MP3 file,

```
ffmpeg -i in.mp3 -filter_complex channelsplit out.mkv

```

will create an output Matroska file with two audio streams, one containing only the left channel and the other the right channel.

- Split a 5.1 WAV file into per-channel files:

```
ffmpeg -i in.wav -filter_complex
'channelsplit=channel_layout=5.1[FL][FR][FC][LFE][SL][SR]'
-map '[FL]' front_left.wav -map '[FR]' front_right.wav -map '[FC]'
front_center.wav -map '[LFE]' lfe.wav -map '[SL]' side_left.wav -map '[SR]'
side_right.wav

```

- Extract only LFE from a 5.1 WAV file:

```
ffmpeg -i in.wav -filter_complex 'channelsplit=channel_layout=5.1:channels=LFE[LFE]'
-map '[LFE]' lfe.wav

```

### 36.76 chorus# TOC

Add a chorus effect to the audio.

Can make a single vocal sound like a chorus, but can also be applied to instrumentation.

Chorus resembles an echo effect with a short delay, but whereas with echo the delay is constant, with chorus, it is varied using sinusoidal or triangular modulation. The modulation depth defines the range the modulated delay is played before or after the delay. Hence the delayed sound will sound slower or faster, that is the delayed sound tuned around the original one, like in a chorus where some vocals are slightly off key.

It accepts the following parameters:

in_gain

Set input gain. Default is 0.4.

out_gain

Set output gain. Default is 0.4.

delays

Set delays. A typical delay is around 40ms to 60ms.

decays

Set decays.

speeds

Set speeds.

depths

Set depths.

#### 36.76.1 Examples# TOC

- A single delay:

```
chorus=0.7:0.9:55:0.4:0.25:2

```

- Two delays:

```
chorus=0.6:0.9:50|60:0.4|0.32:0.25|0.4:2|1.3

```

- Fuller sounding chorus with three delays:

```
chorus=0.5:0.9:50|60|40:0.4|0.32|0.3:0.25|0.4|0.3:2|2.3|1.3

```

### 36.77 compand# TOC

Compress or expand the audio’s dynamic range.

It accepts the following parameters:

attacks

decays

A list of times in seconds for each channel over which the instantaneous level of the input signal is averaged to determine its volume. attacks refers to increase of volume and decays refers to decrease of volume. For most situations, the attack time (response to the audio getting louder) should be shorter than the decay time, because the human ear is more sensitive to sudden loud audio than sudden soft audio. A typical value for attack is 0.3 seconds and a typical value for decay is 0.8 seconds. If specified number of attacks & decays is lower than number of channels, the last set attack/decay will be used for all remaining channels.

points

A list of points for the transfer function, specified in dB relative to the maximum possible signal amplitude. Each key points list must be defined using the following syntax: x0/y0|x1/y1|x2/y2|.... or x0/y0 x1/y1 x2/y2 ....

The input values must be in strictly increasing order but the transfer function does not have to be monotonically rising. The point 0/0 is assumed but may be overridden (by 0/out-dBn). Typical values for the transfer function are -70/-70|-60/-20|1/0.

soft-knee

Set the curve radius in dB for all joints. It defaults to 0.01.

gain

Set the additional gain in dB to be applied at all points on the transfer function. This allows for easy adjustment of the overall gain. It defaults to 0.

volume

Set an initial volume, in dB, to be assumed for each channel when filtering starts. This permits the user to supply a nominal level initially, so that, for example, a very large gain is not applied to initial signal levels before the companding has begun to operate. A typical value for audio which is initially quiet is -90 dB. It defaults to 0.

delay

Set a delay, in seconds. The input audio is analyzed immediately, but audio is delayed before being fed to the volume adjuster. Specifying a delay approximately equal to the attack/decay times allows the filter to effectively operate in predictive rather than reactive mode. It defaults to 0.

#### 36.77.1 Examples# TOC

- Make music with both quiet and loud passages suitable for listening to in a noisy environment:

```
compand=.3|.3:1|1:-90/-60|-60/-40|-40/-30|-20/-20:6:0:-90:0.2

```

Another example for audio with whisper and explosion parts:

```
compand=0|0:1|1:-90/-900|-70/-70|-30/-9|0/-3:6:0:0:0

```

- A noise gate for when the noise is at a lower level than the signal:

```
compand=.1|.1:.2|.2:-900/-900|-50.1/-900|-50/-50:.01:0:-90:.1

```

- Here is another noise gate, this time for when the noise is at a higher level than the signal (making it, in some ways, similar to squelch):

```
compand=.1|.1:.1|.1:-45.1/-45.1|-45/-900|0/-900:.01:45:-90:.1

```

- 2:1 compression starting at -6dB:

```
compand=points=-80/-80|-6/-6|0/-3.8|20/3.5

```

- 2:1 compression starting at -9dB:

```
compand=points=-80/-80|-9/-9|0/-5.3|20/2.9

```

- 2:1 compression starting at -12dB:

```
compand=points=-80/-80|-12/-12|0/-6.8|20/1.9

```

- 2:1 compression starting at -18dB:

```
compand=points=-80/-80|-18/-18|0/-9.8|20/0.7

```

- 3:1 compression starting at -15dB:

```
compand=points=-80/-80|-15/-15|0/-10.8|20/-5.2

```

- Compressor/Gate:

```
compand=points=-80/-105|-62/-80|-15.4/-15.4|0/-12|20/-7.6

```

- Expander:

```
compand=attacks=0:points=-80/-169|-54/-80|-49.5/-64.6|-41.1/-41.1|-25.8/-15|-10.8/-4.5|0/0|20/8.3

```

- Hard limiter at -6dB:

```
compand=attacks=0:points=-80/-80|-6/-6|20/-6

```

- Hard limiter at -12dB:

```
compand=attacks=0:points=-80/-80|-12/-12|20/-12

```

- Hard noise gate at -35 dB:

```
compand=attacks=0:points=-80/-115|-35.1/-80|-35/-35|20/20

```

- Soft limiter:

```
compand=attacks=0:points=-80/-80|-12.4/-12.4|-6/-8|0/-6.8|20/-2.8

```

### 36.78 compensationdelay# TOC

Compensation Delay Line is a metric based delay to compensate differing positions of microphones or speakers.

For example, you have recorded guitar with two microphones placed in different locations. Because the front of sound wave has fixed speed in normal conditions, the phasing of microphones can vary and depends on their location and interposition. The best sound mix can be achieved when these microphones are in phase (synchronized). Note that a distance of ~30 cm between microphones makes one microphone capture the signal in antiphase to the other microphone. That makes the final mix sound moody. This filter helps to solve phasing problems by adding different delays to each microphone track and make them synchronized.

The best result can be reached when you take one track as base and synchronize other tracks one by one with it. Remember that synchronization/delay tolerance depends on sample rate, too. Higher sample rates will give more tolerance.

The filter accepts the following parameters:

mm

Set millimeters distance. This is compensation distance for fine tuning. Default is 0.

cm

Set cm distance. This is compensation distance for tightening distance setup. Default is 0.

m

Set meters distance. This is compensation distance for hard distance setup. Default is 0.

dry

Set dry amount. Amount of unprocessed (dry) signal. Default is 0.

wet

Set wet amount. Amount of processed (wet) signal. Default is 1.

temp

Set temperature in degrees Celsius. This is the temperature of the environment. Default is 20.

#### 36.78.1 Commands# TOC

This filter supports the all above options as commands.

### 36.79 crossfeed# TOC

Apply headphone crossfeed filter.

Crossfeed is the process of blending the left and right channels of stereo audio recording. It is mainly used to reduce extreme stereo separation of low frequencies.

The intent is to produce more speaker like sound to the listener.

The filter accepts the following options:

strength

Set strength of crossfeed. Default is 0.2. Allowed range is from 0 to 1. This sets gain of low shelf filter for side part of stereo image. Default is -6dB. Max allowed is -30db when strength is set to 1.

range

Set soundstage wideness. Default is 0.5. Allowed range is from 0 to 1. This sets cut off frequency of low shelf filter. Default is cut off near 1550 Hz. With range set to 1 cut off frequency is set to 2100 Hz.

slope

Set curve slope of low shelf filter. Default is 0.5. Allowed range is from 0.01 to 1.

level_in

Set input gain. Default is 0.9.

level_out

Set output gain. Default is 1.

block_size

Set block size used for reverse IIR processing. If this value is set to high enough value (higher than impulse response length truncated when reaches near zero values) filtering will become linear phase otherwise if not big enough it will just produce nasty artifacts.

Note that filter delay will be exactly this many samples when set to non-zero value.

#### 36.79.1 Commands# TOC

This filter supports the all above options as commands.

### 36.80 crystalizer# TOC

Simple algorithm for audio noise sharpening.

This filter linearly increases differences between each audio sample.

The filter accepts the following options:

i

Sets the intensity of effect (default: 2.0). Must be in range between -10.0 to 0 (unchanged sound) to 10.0 (maximum effect). To inverse filtering use negative value.

c

Enable clipping. By default is enabled.

#### 36.80.1 Commands# TOC

This filter supports the all above options as commands.

### 36.81 dcshift# TOC

Apply a DC shift to the audio.

This can be useful to remove a DC offset (caused perhaps by a hardware problem in the recording chain) from the audio. The effect of a DC offset is reduced headroom and hence volume. The astats filter can be used to determine if a signal has a DC offset.

shift

Set the DC shift, allowed range is [-1, 1]. It indicates the amount to shift the audio.

limitergain

Optional. It should have a value much less than 1 (e.g. 0.05 or 0.02) and is used to prevent clipping.

### 36.82 deesser# TOC

Apply de-essing to the audio samples.

i

Set intensity for triggering de-essing. Allowed range is from 0 to 1. Default is 0.

m

Set amount of ducking on treble part of sound. Allowed range is from 0 to 1. Default is 0.5.

f

How much of original frequency content to keep when de-essing. Allowed range is from 0 to 1. Default is 0.5.

s

Set the output mode.

It accepts the following values:

i

Pass input unchanged.

o

Pass ess filtered out.

e

Pass only ess.

Default value is o.

### 36.83 dialoguenhance# TOC

Enhance dialogue in stereo audio.

This filter accepts stereo input and produce surround (3.0) channels output. The newly produced front center channel have enhanced speech dialogue originally available in both stereo channels. This filter outputs front left and front right channels same as available in stereo input.

The filter accepts the following options:

original

Set the original center factor to keep in front center channel output. Allowed range is from 0 to 1. Default value is 1.

enhance

Set the dialogue enhance factor to put in front center channel output. Allowed range is from 0 to 3. Default value is 1.

voice

Set the voice detection factor. Allowed range is from 2 to 32. Default value is 2.

#### 36.83.1 Commands# TOC

This filter supports the all above options as commands.

### 36.84 drmeter# TOC

Measure audio dynamic range.

DR values of 14 and higher is found in very dynamic material. DR of 8 to 13 is found in transition material. And anything less that 8 have very poor dynamics and is very compressed.

The filter accepts the following options:

length

Set window length in seconds used to split audio into segments of equal length. Default is 3 seconds.

### 36.85 dynaudnorm# TOC

Dynamic Audio Normalizer.

This filter applies a certain amount of gain to the input audio in order to bring its peak magnitude to a target level (e.g. 0 dBFS). However, in contrast to more "simple" normalization algorithms, the Dynamic Audio Normalizer *dynamically* re-adjusts the gain factor to the input audio. This allows for applying extra gain to the "quiet" sections of the audio while avoiding distortions or clipping the "loud" sections. In other words: The Dynamic Audio Normalizer will "even out" the volume of quiet and loud sections, in the sense that the volume of each section is brought to the same target level. Note, however, that the Dynamic Audio Normalizer achieves this goal *without* applying "dynamic range compressing". It will retain 100% of the dynamic range *within* each section of the audio file.

framelen, f

Set the frame length in milliseconds. In range from 10 to 8000 milliseconds. Default is 500 milliseconds. The Dynamic Audio Normalizer processes the input audio in small chunks, referred to as frames. This is required, because a peak magnitude has no meaning for just a single sample value. Instead, we need to determine the peak magnitude for a contiguous sequence of sample values. While a "standard" normalizer would simply use the peak magnitude of the complete file, the Dynamic Audio Normalizer determines the peak magnitude individually for each frame. The length of a frame is specified in milliseconds. By default, the Dynamic Audio Normalizer uses a frame length of 500 milliseconds, which has been found to give good results with most files. Note that the exact frame length, in number of samples, will be determined automatically, based on the sampling rate of the individual input audio file.

gausssize, g

Set the Gaussian filter window size. In range from 3 to 301, must be odd number. Default is 31. Probably the most important parameter of the Dynamic Audio Normalizer is the window size of the Gaussian smoothing filter. The filter’s window size is specified in frames, centered around the current frame. For the sake of simplicity, this must be an odd number. Consequently, the default value of 31 takes into account the current frame, as well as the 15 preceding frames and the 15 subsequent frames. Using a larger window results in a stronger smoothing effect and thus in less gain variation, i.e. slower gain adaptation. Conversely, using a smaller window results in a weaker smoothing effect and thus in more gain variation, i.e. faster gain adaptation. In other words, the more you increase this value, the more the Dynamic Audio Normalizer will behave like a "traditional" normalization filter. On the contrary, the more you decrease this value, the more the Dynamic Audio Normalizer will behave like a dynamic range compressor.

peak, p

Set the target peak value. This specifies the highest permissible magnitude level for the normalized audio input. This filter will try to approach the target peak magnitude as closely as possible, but at the same time it also makes sure that the normalized signal will never exceed the peak magnitude. A frame’s maximum local gain factor is imposed directly by the target peak magnitude. The default value is 0.95 and thus leaves a headroom of 5%*. It is not recommended to go above this value.

maxgain, m

Set the maximum gain factor. In range from 1.0 to 100.0. Default is 10.0. The Dynamic Audio Normalizer determines the maximum possible (local) gain factor for each input frame, i.e. the maximum gain factor that does not result in clipping or distortion. The maximum gain factor is determined by the frame’s highest magnitude sample. However, the Dynamic Audio Normalizer additionally bounds the frame’s maximum gain factor by a predetermined (global) maximum gain factor. This is done in order to avoid excessive gain factors in "silent" or almost silent frames. By default, the maximum gain factor is 10.0, For most inputs the default value should be sufficient and it usually is not recommended to increase this value. Though, for input with an extremely low overall volume level, it may be necessary to allow even higher gain factors. Note, however, that the Dynamic Audio Normalizer does not simply apply a "hard" threshold (i.e. cut off values above the threshold). Instead, a "sigmoid" threshold function will be applied. This way, the gain factors will smoothly approach the threshold value, but never exceed that value.

targetrms, r

Set the target RMS. In range from 0.0 to 1.0. Default is 0.0 - disabled. By default, the Dynamic Audio Normalizer performs "peak" normalization. This means that the maximum local gain factor for each frame is defined (only) by the frame’s highest magnitude sample. This way, the samples can be amplified as much as possible without exceeding the maximum signal level, i.e. without clipping. Optionally, however, the Dynamic Audio Normalizer can also take into account the frame’s root mean square, abbreviated RMS. In electrical engineering, the RMS is commonly used to determine the power of a time-varying signal. It is therefore considered that the RMS is a better approximation of the "perceived loudness" than just looking at the signal’s peak magnitude. Consequently, by adjusting all frames to a constant RMS value, a uniform "perceived loudness" can be established. If a target RMS value has been specified, a frame’s local gain factor is defined as the factor that would result in exactly that RMS value. Note, however, that the maximum local gain factor is still restricted by the frame’s highest magnitude sample, in order to prevent clipping.

coupling, n

Enable channels coupling. By default is enabled. By default, the Dynamic Audio Normalizer will amplify all channels by the same amount. This means the same gain factor will be applied to all channels, i.e. the maximum possible gain factor is determined by the "loudest" channel. However, in some recordings, it may happen that the volume of the different channels is uneven, e.g. one channel may be "quieter" than the other one(s). In this case, this option can be used to disable the channel coupling. This way, the gain factor will be determined independently for each channel, depending only on the individual channel’s highest magnitude sample. This allows for harmonizing the volume of the different channels.

correctdc, c

Enable DC bias correction. By default is disabled. An audio signal (in the time domain) is a sequence of sample values. In the Dynamic Audio Normalizer these sample values are represented in the -1.0 to 1.0 range, regardless of the original input format. Normally, the audio signal, or "waveform", should be centered around the zero point. That means if we calculate the mean value of all samples in a file, or in a single frame, then the result should be 0.0 or at least very close to that value. If, however, there is a significant deviation of the mean value from 0.0, in either positive or negative direction, this is referred to as a DC bias or DC offset. Since a DC bias is clearly undesirable, the Dynamic Audio Normalizer provides optional DC bias correction. With DC bias correction enabled, the Dynamic Audio Normalizer will determine the mean value, or "DC correction" offset, of each input frame and subtract that value from all of the frame’s sample values which ensures those samples are centered around 0.0 again. Also, in order to avoid "gaps" at the frame boundaries, the DC correction offset values will be interpolated smoothly between neighbouring frames.

altboundary, b

Enable alternative boundary mode. By default is disabled. The Dynamic Audio Normalizer takes into account a certain neighbourhood around each frame. This includes the preceding frames as well as the subsequent frames. However, for the "boundary" frames, located at the very beginning and at the very end of the audio file, not all neighbouring frames are available. In particular, for the first few frames in the audio file, the preceding frames are not known. And, similarly, for the last few frames in the audio file, the subsequent frames are not known. Thus, the question arises which gain factors should be assumed for the missing frames in the "boundary" region. The Dynamic Audio Normalizer implements two modes to deal with this situation. The default boundary mode assumes a gain factor of exactly 1.0 for the missing frames, resulting in a smooth "fade in" and "fade out" at the beginning and at the end of the input, respectively.

compress, s

Set the compress factor. In range from 0.0 to 30.0. Default is 0.0. By default, the Dynamic Audio Normalizer does not apply "traditional" compression. This means that signal peaks will not be pruned and thus the full dynamic range will be retained within each local neighbourhood. However, in some cases it may be desirable to combine the Dynamic Audio Normalizer’s normalization algorithm with a more "traditional" compression. For this purpose, the Dynamic Audio Normalizer provides an optional compression (thresholding) function. If (and only if) the compression feature is enabled, all input frames will be processed by a soft knee thresholding function prior to the actual normalization process. Put simply, the thresholding function is going to prune all samples whose magnitude exceeds a certain threshold value. However, the Dynamic Audio Normalizer does not simply apply a fixed threshold value. Instead, the threshold value will be adjusted for each individual frame. In general, smaller parameters result in stronger compression, and vice versa. Values below 3.0 are not recommended, because audible distortion may appear.

threshold, t

Set the target threshold value. This specifies the lowest permissible magnitude level for the audio input which will be normalized. If input frame volume is above this value frame will be normalized. Otherwise frame may not be normalized at all. The default value is set to 0, which means all input frames will be normalized. This option is mostly useful if digital noise is not wanted to be amplified.

channels, h

Specify which channels to filter, by default all available channels are filtered.

overlap, o

Specify overlap for frames. If set to 0 (default) no frame overlapping is done. Using >0 and <1 values will make less conservative gain adjustments, like when framelen option is set to smaller value, if framelen option value is compensated for non-zero overlap then gain adjustments will be smoother across time compared to zero overlap case.

curve, v

Specify the peak mapping curve expression which is going to be used when calculating gain applied to frames. The max output frame gain will still be limited by other options mentioned previously for this filter.

The expression can contain the following constants:

ch

current channel number

sn

current sample number

nb_channels

number of channels

t

timestamp expressed in seconds

sr

sample rate

p

current frame peak value

#### 36.85.1 Commands# TOC

This filter supports the all above options as commands.

### 36.86 earwax# TOC

Make audio easier to listen to on headphones.

This filter adds ‘cues’ to 44.1kHz stereo (i.e. audio CD format) audio so that when listened to on headphones the stereo image is moved from inside your head (standard for headphones) to outside and in front of the listener (standard for speakers).

Ported from SoX.

### 36.87 equalizer# TOC

Apply a two-pole peaking equalisation (EQ) filter. With this filter, the signal-level at and around a selected frequency can be increased or decreased, whilst (unlike bandpass and bandreject filters) that at all other frequencies is unchanged.

In order to produce complex equalisation curves, this filter can be given several times, each with a different central frequency.

The filter accepts the following options:

frequency, f

Set the filter’s central frequency in Hz.

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

Specify the band-width of a filter in width_type units.

gain, g

Set the required gain or attenuation in dB. Beware of clipping when using a positive gain.

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

#### 36.87.1 Examples# TOC

- Attenuate 10 dB at 1000 Hz, with a bandwidth of 200 Hz:

```
equalizer=f=1000:t=h:width=200:g=-10

```

- Apply 2 dB gain at 1000 Hz with Q 1 and attenuate 5 dB at 100 Hz with Q 2:

```
equalizer=f=1000:t=q:w=1:g=2,equalizer=f=100:t=q:w=2:g=-5

```

#### 36.87.2 Commands# TOC

This filter supports the following commands:

frequency, f

Change equalizer frequency. Syntax for the command is : "frequency"

width_type, t

Change equalizer width_type. Syntax for the command is : "width_type"

width, w

Change equalizer width. Syntax for the command is : "width"

gain, g

Change equalizer gain. Syntax for the command is : "gain"

mix, m

Change equalizer mix. Syntax for the command is : "mix"

### 36.88 extrastereo# TOC

Linearly increases the difference between left and right channels which adds some sort of "live" effect to playback.

The filter accepts the following options:

m

Sets the difference coefficient (default: 2.5). 0.0 means mono sound (average of both channels), with 1.0 sound will be unchanged, with -1.0 left and right channels will be swapped.

c

Enable clipping. By default is enabled.

#### 36.88.1 Commands# TOC

This filter supports the all above options as commands.

### 36.89 firequalizer# TOC

Apply FIR Equalization using arbitrary frequency response.

The filter accepts the following option:

gain

Set gain curve equation (in dB). The expression can contain variables:

f

the evaluated frequency

sr

sample rate

ch

channel number, set to 0 when multichannels evaluation is disabled

chid

channel id, see libavutil/channel_layout.h, set to the first channel id when multichannels evaluation is disabled

chs

number of channels

chlayout

channel_layout, see libavutil/channel_layout.h

and functions:

gain_interpolate(f)

interpolate gain on frequency f based on gain_entry

cubic_interpolate(f)

same as gain_interpolate, but smoother

This option is also available as command. Default is gain_interpolate(f).

gain_entry

Set gain entry for gain_interpolate function. The expression can contain functions:

entry(f, g)

store gain entry at frequency f with value g

This option is also available as command.

delay

Set filter delay in seconds. Higher value means more accurate. Default is 0.01.

accuracy

Set filter accuracy in Hz. Lower value means more accurate. Default is 5.

wfunc

Set window function. Acceptable values are:

rectangular

rectangular window, useful when gain curve is already smooth

hann

hann window (default)

hamming

hamming window

blackman

blackman window

nuttall3

3-terms continuous 1st derivative nuttall window

mnuttall3

minimum 3-terms discontinuous nuttall window

nuttall

4-terms continuous 1st derivative nuttall window

bnuttall

minimum 4-terms discontinuous nuttall (blackman-nuttall) window

bharris

blackman-harris window

tukey

tukey window

fixed

If enabled, use fixed number of audio samples. This improves speed when filtering with large delay. Default is disabled.

multi

Enable multichannels evaluation on gain. Default is disabled.

zero_phase

Enable zero phase mode by subtracting timestamp to compensate delay. Default is disabled.

scale

Set scale used by gain. Acceptable values are:

linlin

linear frequency, linear gain

linlog

linear frequency, logarithmic (in dB) gain (default)

loglin

logarithmic (in octave scale where 20 Hz is 0) frequency, linear gain

loglog

logarithmic frequency, logarithmic gain

dumpfile

Set file for dumping, suitable for gnuplot.

dumpscale

Set scale for dumpfile. Acceptable values are same with scale option. Default is linlog.

fft2

Enable 2-channel convolution using complex FFT. This improves speed significantly. Default is disabled.

min_phase

Enable minimum phase impulse response. Default is disabled.

#### 36.89.1 Examples# TOC

- lowpass at 1000 Hz:

```
firequalizer=gain='if(lt(f,1000), 0, -INF)'

```

- lowpass at 1000 Hz with gain_entry:

```
firequalizer=gain_entry='entry(1000,0); entry(1001, -INF)'

```

- custom equalization:

```
firequalizer=gain_entry='entry(100,0); entry(400, -4); entry(1000, -6); entry(2000, 0)'

```

- higher delay with zero phase to compensate delay:

```
firequalizer=delay=0.1:fixed=on:zero_phase=on

```

- lowpass on left channel, highpass on right channel:

```
firequalizer=gain='if(eq(chid,1), gain_interpolate(f), if(eq(chid,2), gain_interpolate(1e6+f), 0))'
:gain_entry='entry(1000, 0); entry(1001,-INF); entry(1e6+1000,0)':multi=on

```

### 36.90 flanger# TOC

Apply a flanging effect to the audio.

The filter accepts the following options:

delay

Set base delay in milliseconds. Range from 0 to 30. Default value is 0.

depth

Set added sweep delay in milliseconds. Range from 0 to 10. Default value is 2.

regen

Set percentage regeneration (delayed signal feedback). Range from -95 to 95. Default value is 0.

width

Set percentage of delayed signal mixed with original. Range from 0 to 100. Default value is 71.

speed

Set sweeps per second (Hz). Range from 0.1 to 10. Default value is 0.5.

shape

Set swept wave shape, can be triangular or sinusoidal. Default value is sinusoidal.

phase

Set swept wave percentage-shift for multi channel. Range from 0 to 100. Default value is 25.

interp

Set delay-line interpolation, linear or quadratic. Default is linear.

### 36.91 haas# TOC

Apply Haas effect to audio.

Note that this makes most sense to apply on mono signals. With this filter applied to mono signals it give some directionality and stretches its stereo image.

The filter accepts the following options:

level_in

Set input level. By default is 1, or 0dB

level_out

Set output level. By default is 1, or 0dB.

side_gain

Set gain applied to side part of signal. By default is 1.

middle_source

Set kind of middle source. Can be one of the following:

‘left’

Pick left channel.

‘right’

Pick right channel.

‘mid’

Pick middle part signal of stereo image.

‘side’

Pick side part signal of stereo image.

middle_phase

Change middle phase. By default is disabled.

left_delay

Set left channel delay. By default is 2.05 milliseconds.

left_balance

Set left channel balance. By default is -1.

left_gain

Set left channel gain. By default is 1.

left_phase

Change left phase. By default is disabled.

right_delay

Set right channel delay. By defaults is 2.12 milliseconds.

right_balance

Set right channel balance. By default is 1.

right_gain

Set right channel gain. By default is 1.

right_phase

Change right phase. By default is enabled.

### 36.92 hdcd# TOC

Decodes High Definition Compatible Digital (HDCD) data. A 16-bit PCM stream with embedded HDCD codes is expanded into a 20-bit PCM stream.

The filter supports the Peak Extend and Low-level Gain Adjustment features of HDCD, and detects the Transient Filter flag.

```
ffmpeg -i HDCD16.flac -af hdcd OUT24.flac

```

When using the filter with wav, note the default encoding for wav is 16-bit, so the resulting 20-bit stream will be truncated back to 16-bit. Use something like -acodec pcm_s24le after the filter to get 24-bit PCM output.

```
ffmpeg -i HDCD16.wav -af hdcd OUT16.wav
ffmpeg -i HDCD16.wav -af hdcd -c:a pcm_s24le OUT24.wav

```

The filter accepts the following options:

disable_autoconvert

Disable any automatic format conversion or resampling in the filter graph.

process_stereo

Process the stereo channels together. If target_gain does not match between channels, consider it invalid and use the last valid target_gain.

cdt_ms

Set the code detect timer period in ms.

force_pe

Always extend peaks above -3dBFS even if PE isn’t signaled.

analyze_mode

Replace audio with a solid tone and adjust the amplitude to signal some specific aspect of the decoding process. The output file can be loaded in an audio editor alongside the original to aid analysis.

analyze_mode=pe:force_pe=true can be used to see all samples above the PE level.

Modes are:

‘0, off’

Disabled

‘1, lle’

Gain adjustment level at each sample

‘2, pe’

Samples where peak extend occurs

‘3, cdt’

Samples where the code detect timer is active

‘4, tgm’

Samples where the target gain does not match between channels

### 36.93 headphone# TOC

Apply head-related transfer functions (HRTFs) to create virtual loudspeakers around the user for binaural listening via headphones. The HRIRs are provided via additional streams, for each channel one stereo input stream is needed.

The filter accepts the following options:

map

Set mapping of input streams for convolution. The argument is a ’|’-separated list of channel names in order as they are given as additional stream inputs for filter. This also specify number of input streams. Number of input streams must be not less than number of channels in first stream plus one.

gain

Set gain applied to audio. Value is in dB. Default is 0.

type

Set processing type. Can be time or freq. time is processing audio in time domain which is slow. freq is processing audio in frequency domain which is fast. Default is freq.

lfe

Set custom gain for LFE channels. Value is in dB. Default is 0.

size

Set size of frame in number of samples which will be processed at once. Default value is 1024. Allowed range is from 1024 to 96000.

hrir

Set format of hrir stream. Default value is stereo. Alternative value is multich. If value is set to stereo, number of additional streams should be greater or equal to number of input channels in first input stream. Also each additional stream should have stereo number of channels. If value is set to multich, number of additional streams should be exactly one. Also number of input channels of additional stream should be equal or greater than twice number of channels of first input stream.

#### 36.93.1 Examples# TOC

- Full example using wav files as coefficients with amovie filters for 7.1 downmix, each amovie filter use stereo file with IR coefficients as input. The files give coefficients for each position of virtual loudspeaker:

```
ffmpeg -i input.wav
-filter_complex "amovie=azi_270_ele_0_DFC.wav[sr];amovie=azi_90_ele_0_DFC.wav[sl];amovie=azi_225_ele_0_DFC.wav[br];amovie=azi_135_ele_0_DFC.wav[bl];amovie=azi_0_ele_0_DFC.wav,asplit[fc][lfe];amovie=azi_35_ele_0_DFC.wav[fl];amovie=azi_325_ele_0_DFC.wav[fr];[0:a][fl][fr][fc][lfe][bl][br][sl][sr]headphone=FL|FR|FC|LFE|BL|BR|SL|SR"
output.wav

```

- Full example using wav files as coefficients with amovie filters for 7.1 downmix, but now in multich hrir format.

```
ffmpeg -i input.wav -filter_complex "amovie=minp.wav[hrirs];[0:a][hrirs]headphone=map=FL|FR|FC|LFE|BL|BR|SL|SR:hrir=multich"
output.wav

```

### 36.94 highpass# TOC

Apply a high-pass filter with 3dB point frequency. The filter can be either single-pole, or double-pole (the default). The filter roll off at 6dB per pole per octave (20dB per pole per decade).

The filter accepts the following options:

frequency, f

Set frequency in Hz. Default is 3000.

poles, p

Set number of poles. Default is 2.

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

Specify the band-width of a filter in width_type units. Applies only to double-pole filter. The default is 0.707q and gives a Butterworth response.

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

#### 36.94.1 Commands# TOC

This filter supports the following commands:

frequency, f

Change highpass frequency. Syntax for the command is : "frequency"

width_type, t

Change highpass width_type. Syntax for the command is : "width_type"

width, w

Change highpass width. Syntax for the command is : "width"

mix, m

Change highpass mix. Syntax for the command is : "mix"

### 36.95 join# TOC

Join multiple input streams into one multi-channel stream.

It accepts the following parameters:

inputs

The number of input streams. It defaults to 2.

channel_layout

The desired output channel layout. It defaults to stereo.

map

Map channels from inputs to output. The argument is a ’|’-separated list of mappings, each in the input_idx.in_channel-out_channel form. input_idx is the 0-based index of the input stream. in_channel can be either the name of the input channel (e.g. FL for front left) or its index in the specified input stream. out_channel is the name of the output channel.

The filter will attempt to guess the mappings when they are not specified explicitly. It does so by first trying to find an unused matching input channel and if that fails it picks the first unused input channel.

Join 3 inputs (with properly set channel layouts):

```
ffmpeg -i INPUT1 -i INPUT2 -i INPUT3 -filter_complex join=inputs=3 OUTPUT

```

Build a 5.1 output from 6 single-channel streams:

```
ffmpeg -i fl -i fr -i fc -i sl -i sr -i lfe -filter_complex
'join=inputs=6:channel_layout=5.1:map=0.0-FL|1.0-FR|2.0-FC|3.0-SL|4.0-SR|5.0-LFE'
out

```

### 36.96 ladspa# TOC

Load a LADSPA (Linux Audio Developer’s Simple Plugin API) plugin.

To enable compilation of this filter you need to configure FFmpeg with --enable-ladspa.

file, f

Specifies the name of LADSPA plugin library to load. If the environment variable LADSPA_PATH is defined, the LADSPA plugin is searched in each one of the directories specified by the colon separated list in LADSPA_PATH, otherwise in the standard LADSPA paths, which are in this order: HOME/.ladspa/lib/, /usr/local/lib/ladspa/, /usr/lib/ladspa/.

plugin, p

Specifies the plugin within the library. Some libraries contain only one plugin, but others contain many of them. If this is not set filter will list all available plugins within the specified library.

controls, c

Set the ’|’ separated list of controls which are zero or more floating point values that determine the behavior of the loaded plugin (for example delay, threshold or gain). Controls need to be defined using the following syntax: c0=value0|c1=value1|c2=value2|..., where valuei is the value set on the i-th control. Alternatively they can be also defined using the following syntax: value0|value1|value2|..., where valuei is the value set on the i-th control. If controls is set to help, all available controls and their valid ranges are printed.

sample_rate, s

Specify the sample rate, default to 44100. Only used if plugin have zero inputs.

nb_samples, n

Set the number of samples per channel per each output frame, default is 1024. Only used if plugin have zero inputs.

duration, d

Set the minimum duration of the sourced audio. See the Time duration section in the ffmpeg-utils(1) manual for the accepted syntax. Note that the resulting duration may be greater than the specified duration, as the generated audio is always cut at the end of a complete frame. If not specified, or the expressed duration is negative, the audio is supposed to be generated forever. Only used if plugin have zero inputs.

latency, l

Enable latency compensation, by default is disabled. Only used if plugin have inputs.

#### 36.96.1 Examples# TOC

- List all available plugins within amp (LADSPA example plugin) library:

```
ladspa=file=amp

```

- List all available controls and their valid ranges for vcf_notch plugin from VCF library:

```
ladspa=f=vcf:p=vcf_notch:c=help

```

- Simulate low quality audio equipment using Computer Music Toolkit (CMT) plugin library:

```
ladspa=file=cmt:plugin=lofi:controls=c0=22|c1=12|c2=12

```

- Add reverberation to the audio using TAP-plugins (Tom’s Audio Processing plugins):

```
ladspa=file=tap_reverb:tap_reverb

```

- Generate white noise, with 0.2 amplitude:

```
ladspa=file=cmt:noise_source_white:c=c0=.2

```

- Generate 20 bpm clicks using plugin C* Click - Metronome from the C* Audio Plugin Suite (CAPS) library:

```
ladspa=file=caps:Click:c=c1=20'

```

- Apply C* Eq10X2 - Stereo 10-band equaliser effect:

```
ladspa=caps:Eq10X2:c=c0=-48|c9=-24|c3=12|c4=2

```

- Increase volume by 20dB using fast lookahead limiter from Steve Harris SWH Plugins collection:

```
ladspa=fast_lookahead_limiter_1913:fastLookaheadLimiter:20|0|2

```

- Attenuate low frequencies using Multiband EQ from Steve Harris SWH Plugins collection:

```
ladspa=mbeq_1197:mbeq:-24|-24|-24|0|0|0|0|0|0|0|0|0|0|0|0

```

- Reduce stereo image using Narrower from the C* Audio Plugin Suite (CAPS) library:

```
ladspa=caps:Narrower

```

- Another white noise, now using C* Audio Plugin Suite (CAPS) library:

```
ladspa=caps:White:.2

```

- Some fractal noise, using C* Audio Plugin Suite (CAPS) library:

```
ladspa=caps:Fractal:c=c1=1

```

- Dynamic volume normalization using VLevel plugin:

```
ladspa=vlevel-ladspa:vlevel_mono

```

#### 36.96.2 Commands# TOC

This filter supports the following commands:

cN

Modify the N-th control value.

If the specified value is not valid, it is ignored and prior one is kept.

### 36.97 loudnorm# TOC

EBU R128 loudness normalization. Includes both dynamic and linear normalization modes. Support for both single pass (livestreams, files) and double pass (files) modes. This algorithm can target IL, LRA, and maximum true peak. In dynamic mode, to accurately detect true peaks, the audio stream will be upsampled to 192 kHz. Use the -ar option or aresample filter to explicitly set an output sample rate.

The filter accepts the following options:

I, i

Set integrated loudness target. Range is -70.0 - -5.0. Default value is -24.0.

LRA, lra

Set loudness range target. Range is 1.0 - 50.0. Default value is 7.0.

TP, tp

Set maximum true peak. Range is -9.0 - +0.0. Default value is -2.0.

measured_I, measured_i

Measured IL of input file. Range is -99.0 - +0.0.

measured_LRA, measured_lra

Measured LRA of input file. Range is 0.0 - 99.0.

measured_TP, measured_tp

Measured true peak of input file. Range is -99.0 - +99.0.

measured_thresh

Measured threshold of input file. Range is -99.0 - +0.0.

offset

Set offset gain. Gain is applied before the true-peak limiter. Range is -99.0 - +99.0. Default is +0.0.

linear

Normalize by linearly scaling the source audio. measured_I, measured_LRA, measured_TP, and measured_thresh must all be specified. Target LRA shouldn’t be lower than source LRA and the change in integrated loudness shouldn’t result in a true peak which exceeds the target TP. If any of these conditions aren’t met, normalization mode will revert to dynamic. Options are true or false. Default is true.

dual_mono

Treat mono input files as "dual-mono". If a mono file is intended for playback on a stereo system, its EBU R128 measurement will be perceptually incorrect. If set to true, this option will compensate for this effect. Multi-channel input files are not affected by this option. Options are true or false. Default is false.

print_format

Set print format for stats. Options are summary, json, or none. Default value is none.

stats_file

Write stats to specified file. Format is controlled by print_format, which must be set. Specify - to write to standard output. Default is unset.

### 36.98 lowpass# TOC

Apply a low-pass filter with 3dB point frequency. The filter can be either single-pole or double-pole (the default). The filter roll off at 6dB per pole per octave (20dB per pole per decade).

The filter accepts the following options:

frequency, f

Set frequency in Hz. Default is 500.

poles, p

Set number of poles. Default is 2.

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

Specify the band-width of a filter in width_type units. Applies only to double-pole filter. The default is 0.707q and gives a Butterworth response.

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

#### 36.98.1 Examples# TOC

- Lowpass only LFE channel, it LFE is not present it does nothing:

```
lowpass=c=LFE

```

#### 36.98.2 Commands# TOC

This filter supports the following commands:

frequency, f

Change lowpass frequency. Syntax for the command is : "frequency"

width_type, t

Change lowpass width_type. Syntax for the command is : "width_type"

width, w

Change lowpass width. Syntax for the command is : "width"

mix, m

Change lowpass mix. Syntax for the command is : "mix"

### 36.99 lv2# TOC

Load a LV2 (LADSPA Version 2) plugin.

To enable compilation of this filter you need to configure FFmpeg with --enable-lv2.

plugin, p

Specifies the plugin URI. You may need to escape ’:’.

controls, c

Set the ’|’ separated list of controls which are zero or more floating point values that determine the behavior of the loaded plugin (for example delay, threshold or gain). If controls is set to help, all available controls and their valid ranges are printed.

sample_rate, s

Specify the sample rate, default to 44100. Only used if plugin have zero inputs.

nb_samples, n

Set the number of samples per channel per each output frame, default is 1024. Only used if plugin have zero inputs.

duration, d

Set the minimum duration of the sourced audio. See the Time duration section in the ffmpeg-utils(1) manual for the accepted syntax. Note that the resulting duration may be greater than the specified duration, as the generated audio is always cut at the end of a complete frame. If not specified, or the expressed duration is negative, the audio is supposed to be generated forever. Only used if plugin have zero inputs.

#### 36.99.1 Examples# TOC

- Apply bass enhancer plugin from Calf:

```
lv2=p=http\\\\://calf.sourceforge.net/plugins/BassEnhancer:c=amount=2

```

- Apply vinyl plugin from Calf:

```
lv2=p=http\\\\://calf.sourceforge.net/plugins/Vinyl:c=drone=0.2|aging=0.5

```

- Apply bit crusher plugin from ArtyFX:

```
lv2=p=http\\\\://www.openavproductions.com/artyfx#bitta:c=crush=0.3

```

#### 36.99.2 Commands# TOC

This filter supports all options that are exported by plugin as commands.

### 36.100 mcompand# TOC

Multiband Compress or expand the audio’s dynamic range.

The input audio is divided into bands using 4th order Linkwitz-Riley IIRs. This is akin to the crossover of a loudspeaker, and results in flat frequency response when absent compander action.

It accepts the following parameters:

args

This option syntax is: attack,decay,[attack,decay..] soft-knee points crossover_frequency [delay [initial_volume [gain]]] | attack,decay ... For explanation of each item refer to compand filter documentation.

### 36.101 pan# TOC

Mix channels with specific gain levels. The filter accepts the output channel layout followed by a set of channels definitions.

This filter is also designed to efficiently remap the channels of an audio stream.

The filter accepts parameters of the form: "l|outdef|outdef|..."

l

output channel layout or number of channels

outdef

output channel specification, of the form: "out_name=[gain*]in_name[(+-)[gain*]in_name...]"

out_name

output channel to define, either a channel name (FL, FR, etc.) or a channel number (c0, c1, etc.)

gain

multiplicative coefficient for the channel, 1 leaving the volume unchanged

in_name

input channel to use, see out_name for details; it is not possible to mix named and numbered input channels

If the ‘=’ in a channel specification is replaced by ‘<’, then the gains for that specification will be renormalized so that the total is 1, thus avoiding clipping noise.

#### 36.101.1 Mixing examples# TOC

For example, if you want to down-mix from stereo to mono, but with a bigger factor for the left channel:

```
pan=1c|c0=0.9*c0+0.1*c1

```

A customized down-mix to stereo that works automatically for 3-, 4-, 5- and 7-channels surround:

```
pan=stereo| FL < FL + 0.5*FC + 0.6*BL + 0.6*SL | FR < FR + 0.5*FC + 0.6*BR + 0.6*SR

```

Note that ffmpeg integrates a default down-mix (and up-mix) system that should be preferred (see "-ac" option) unless you have very specific needs.

#### 36.101.2 Remapping examples# TOC

The channel remapping will be effective if, and only if:

- gain coefficients are zeroes or ones,

- only one input per channel output,

If all these conditions are satisfied, the filter will notify the user ("Pure channel mapping detected"), and use an optimized and lossless method to do the remapping.

For example, if you have a 5.1 source and want a stereo audio stream by dropping the extra channels:

```
pan="stereo| c0=FL | c1=FR"

```

Given the same source, you can also switch front left and front right channels and keep the input channel layout:

```
pan="5.1| c0=c1 | c1=c0 | c2=c2 | c3=c3 | c4=c4 | c5=c5"

```

If the input is a stereo audio stream, you can mute the front left channel (and still keep the stereo channel layout) with:

```
pan="stereo|c1=c1"

```

Still with a stereo audio stream input, you can copy the right channel in both front left and right:

```
pan="stereo| c0=FR | c1=FR"

```

### 36.102 replaygain# TOC

ReplayGain scanner filter. This filter takes an audio stream as an input and outputs it unchanged. At end of filtering it displays track_gain and track_peak.

The filter accepts the following exported read-only options:

track_gain

Exported track gain in dB at end of stream.

track_peak

Exported track peak at end of stream.

### 36.103 resample# TOC

Convert the audio sample format, sample rate and channel layout. It is not meant to be used directly.

### 36.104 rubberband# TOC

Apply time-stretching and pitch-shifting with librubberband.

To enable compilation of this filter, you need to configure FFmpeg with --enable-librubberband.

The filter accepts the following options:

tempo

Set tempo scale factor.

pitch

Set pitch scale factor.

transients

Set transients detector. Possible values are:

crisp

mixed

smooth

detector

Set detector. Possible values are:

compound

percussive

soft

phase

Set phase. Possible values are:

laminar

independent

window

Set processing window size. Possible values are:

standard

short

long

smoothing

Set smoothing. Possible values are:

off

on

formant

Enable formant preservation when shift pitching. Possible values are:

shifted

preserved

pitchq

Set pitch quality. Possible values are:

quality

speed

consistency

channels

Set channels. Possible values are:

apart

together

#### 36.104.1 Commands# TOC

This filter supports the following commands:

tempo

Change filter tempo scale factor. Syntax for the command is : "tempo"

pitch

Change filter pitch scale factor. Syntax for the command is : "pitch"

### 36.105 sidechaincompress# TOC

This filter acts like normal compressor but has the ability to compress detected signal using second input signal. It needs two input streams and returns one output stream. First input stream will be processed depending on second stream signal. The filtered signal then can be filtered with other filters in later stages of processing. See pan and amerge filter.

The filter accepts the following options:

level_in

Set input gain. Default is 1. Range is between 0.015625 and 64.

mode

Set mode of compressor operation. Can be upward or downward. Default is downward.

threshold

If a signal of second stream raises above this level it will affect the gain reduction of first stream. By default is 0.125. Range is between 0.00097563 and 1.

ratio

Set a ratio about which the signal is reduced. 1:2 means that if the level raised 4dB above the threshold, it will be only 2dB above after the reduction. Default is 2. Range is between 1 and 20.

attack

Amount of milliseconds the signal has to rise above the threshold before gain reduction starts. Default is 20. Range is between 0.01 and 2000.

release

Amount of milliseconds the signal has to fall below the threshold before reduction is decreased again. Default is 250. Range is between 0.01 and 9000.

makeup

Set the amount by how much signal will be amplified after processing. Default is 1. Range is from 1 to 64.

knee

Curve the sharp knee around the threshold to enter gain reduction more softly. Default is 2.82843. Range is between 1 and 8.

link

Choose if the average level between all channels of side-chain stream or the louder(maximum) channel of side-chain stream affects the reduction. Default is average.

detection

Should the exact signal be taken in case of peak or an RMS one in case of rms. Default is rms which is mainly smoother.

level_sc

Set sidechain gain. Default is 1. Range is between 0.015625 and 64.

mix

How much to use compressed signal in output. Default is 1. Range is between 0 and 1.

#### 36.105.1 Commands# TOC

This filter supports the all above options as commands.

#### 36.105.2 Examples# TOC

- Full ffmpeg example taking 2 audio inputs, 1st input to be compressed depending on the signal of 2nd input and later compressed signal to be merged with 2nd input:

```
ffmpeg -i main.flac -i sidechain.flac -filter_complex "[1:a]asplit=2[sc][mix];[0:a][sc]sidechaincompress[compr];[compr][mix]amerge"

```

### 36.106 sidechaingate# TOC

A sidechain gate acts like a normal (wideband) gate but has the ability to filter the detected signal before sending it to the gain reduction stage. Normally a gate uses the full range signal to detect a level above the threshold. For example: If you cut all lower frequencies from your sidechain signal the gate will decrease the volume of your track only if not enough highs appear. With this technique you are able to reduce the resonation of a natural drum or remove "rumbling" of muted strokes from a heavily distorted guitar. It needs two input streams and returns one output stream. First input stream will be processed depending on second stream signal.

The filter accepts the following options:

level_in

Set input level before filtering. Default is 1. Allowed range is from 0.015625 to 64.

mode

Set the mode of operation. Can be upward or downward. Default is downward. If set to upward mode, higher parts of signal will be amplified, expanding dynamic range in upward direction. Otherwise, in case of downward lower parts of signal will be reduced.

range

Set the level of gain reduction when the signal is below the threshold. Default is 0.06125. Allowed range is from 0 to 1. Setting this to 0 disables reduction and then filter behaves like expander.

threshold

If a signal rises above this level the gain reduction is released. Default is 0.125. Allowed range is from 0 to 1.

ratio

Set a ratio about which the signal is reduced. Default is 2. Allowed range is from 1 to 9000.

attack

Amount of milliseconds the signal has to rise above the threshold before gain reduction stops. Default is 20 milliseconds. Allowed range is from 0.01 to 9000.

release

Amount of milliseconds the signal has to fall below the threshold before the reduction is increased again. Default is 250 milliseconds. Allowed range is from 0.01 to 9000.

makeup

Set amount of amplification of signal after processing. Default is 1. Allowed range is from 1 to 64.

knee

Curve the sharp knee around the threshold to enter gain reduction more softly. Default is 2.828427125. Allowed range is from 1 to 8.

detection

Choose if exact signal should be taken for detection or an RMS like one. Default is rms. Can be peak or rms.

link

Choose if the average level between all channels or the louder channel affects the reduction. Default is average. Can be average or maximum.

level_sc

Set sidechain gain. Default is 1. Range is from 0.015625 to 64.

#### 36.106.1 Commands# TOC

This filter supports the all above options as commands.

### 36.107 silencedetect# TOC

Detect silence in an audio stream.

This filter logs a message when it detects that the input audio volume is less or equal to a noise tolerance value for a duration greater or equal to the minimum detected noise duration.

The printed times and duration are expressed in seconds. The lavfi.silence_start or lavfi.silence_start.X metadata key is set on the first frame whose timestamp equals or exceeds the detection duration and it contains the timestamp of the first frame of the silence.

The lavfi.silence_duration or lavfi.silence_duration.X and lavfi.silence_end or lavfi.silence_end.X metadata keys are set on the first frame after the silence. If mono is enabled, and each channel is evaluated separately, the .X suffixed keys are used, and X corresponds to the channel number.

The filter accepts the following options:

noise, n

Set noise tolerance. Can be specified in dB (in case "dB" is appended to the specified value) or amplitude ratio. Default is -60dB, or 0.001.

duration, d

Set silence duration until notification (default is 2 seconds). See the Time duration section in the ffmpeg-utils(1) manual for the accepted syntax.

mono, m

Process each channel separately, instead of combined. By default is disabled.

#### 36.107.1 Examples# TOC

- Detect 5 seconds of silence with -50dB noise tolerance:

```
silencedetect=n=-50dB:d=5

```

- Complete example with ffmpeg to detect silence with 0.0001 noise tolerance in silence.mp3:

```
ffmpeg -i silence.mp3 -af silencedetect=noise=0.0001 -f null -

```

### 36.108 silenceremove# TOC

Remove silence from the beginning, middle or end of the audio.

The filter accepts the following options:

start_periods

This value is used to indicate if audio should be trimmed at beginning of the audio. A value of zero indicates no silence should be trimmed from the beginning. When specifying a non-zero value, it trims audio up until it finds non-silence. Normally, when trimming silence from beginning of audio the start_periods will be 1 but it can be increased to higher values to trim all audio up to specific count of non-silence periods. Default value is 0.

start_duration

Specify the amount of time that non-silence must be detected before it stops trimming audio. By increasing the duration, bursts of noises can be treated as silence and trimmed off. Default value is 0.

start_threshold

This indicates what sample value should be treated as silence. For digital audio, a value of 0 may be fine but for audio recorded from analog, you may wish to increase the value to account for background noise. Can be specified in dB (in case "dB" is appended to the specified value) or amplitude ratio. Default value is 0.

start_silence

Specify max duration of silence at beginning that will be kept after trimming. Default is 0, which is equal to trimming all samples detected as silence.

start_mode

Specify mode of detection of silence end at start of multi-channel audio. Can be any or all. Default is any. With any, any sample from any channel that is detected as non-silence will trigger end of silence trimming at start of audio stream. With all, only if every sample from every channel is detected as non-silence will trigger end of silence trimming at start of audio stream, limited usage.

stop_periods

Set the count for trimming silence from the end of audio. When specifying a positive value, it trims audio after it finds specified silence period. To remove silence from the middle of a file, specify a stop_periods that is negative. This value is then treated as a positive value and is used to indicate the effect should restart processing as specified by stop_periods, making it suitable for removing periods of silence in the middle of the audio. Default value is 0.

stop_duration

Specify a duration of silence that must exist before audio is not copied any more. By specifying a higher duration, silence that is wanted can be left in the audio. Default value is 0.

stop_threshold

This is the same as start_threshold but for trimming silence from the end of audio. Can be specified in dB (in case "dB" is appended to the specified value) or amplitude ratio. Default value is 0.

stop_silence

Specify max duration of silence at end that will be kept after trimming. Default is 0, which is equal to trimming all samples detected as silence.

stop_mode

Specify mode of detection of silence start after start of multi-channel audio. Can be any or all. Default is all. With any, any sample from any channel that is detected as silence will trigger start of silence trimming after start of audio stream, limited usage. With all, only if every sample from every channel is detected as silence will trigger start of silence trimming after start of audio stream.

detection

Set how is silence detected.

avg

Mean of absolute values of samples in moving window.

rms

Root squared mean of absolute values of samples in moving window.

peak

Maximum of absolute values of samples in moving window.

median

Median of absolute values of samples in moving window.

ptp

Absolute of max peak to min peak difference of samples in moving window.

dev

Standard deviation of values of samples in moving window.

Default value is rms.

window

Set duration in number of seconds used to calculate size of window in number of samples for detecting silence. Using 0 will effectively disable any windowing and use only single sample per channel for silence detection. In that case it may be needed to also set start_silence and/or stop_silence to nonzero values with also start_duration and/or stop_duration to nonzero values. Default value is 0.02. Allowed range is from 0 to 10.

timestamp

Set processing mode of every audio frame output timestamp.

write

Full timestamps rewrite, keep only the start time for the first output frame.

copy

Non-dropped frames are left with same timestamp as input audio frame.

Defaults value is write.

#### 36.108.1 Examples# TOC

- The following example shows how this filter can be used to start a recording that does not contain the delay at the start which usually occurs between pressing the record button and the start of the performance:

```
silenceremove=start_periods=1:start_duration=5:start_threshold=0.02

```

- Trim all silence encountered from beginning to end where there is more than 1 second of silence in audio:

```
silenceremove=stop_periods=-1:stop_duration=1:stop_threshold=-90dB

```

- Trim all digital silence samples, using peak detection, from beginning to end where there is more than 0 samples of digital silence in audio and digital silence is detected in all channels at same positions in stream:

```
silenceremove=window=0:detection=peak:stop_mode=all:start_mode=all:stop_periods=-1:stop_threshold=0

```

- Trim every 2nd encountered silence period from beginning to end where there is more than 1 second of silence per silence period in audio:

```
silenceremove=stop_periods=-2:stop_duration=1:stop_threshold=-90dB

```

- Similar as above, but keep maximum of 0.5 seconds of silence from each trimmed period:

```
silenceremove=stop_periods=-2:stop_duration=1:stop_threshold=-90dB:stop_silence=0.5

```

- Similar as above, but keep maximum of 1.5 seconds of silence from start of audio:

```
silenceremove=stop_periods=-2:stop_duration=1:stop_threshold=-90dB:stop_silence=0.5:start_periods=1:start_duration=1:start_silence=1.5:stop_threshold=-90dB

```

#### 36.108.2 Commands# TOC

This filter supports some above options as commands.

### 36.109 sofalizer# TOC

SOFAlizer uses head-related transfer functions (HRTFs) to create virtual loudspeakers around the user for binaural listening via headphones (audio formats up to 9 channels supported). The HRTFs are stored in SOFA files (see http://www.sofacoustics.org/ for a database). SOFAlizer is developed at the Acoustics Research Institute (ARI) of the Austrian Academy of Sciences.

To enable compilation of this filter you need to configure FFmpeg with --enable-libmysofa.

The filter accepts the following options:

sofa

Set the SOFA file used for rendering.

gain

Set gain applied to audio. Value is in dB. Default is 0.

rotation

Set rotation of virtual loudspeakers in deg. Default is 0.

elevation

Set elevation of virtual speakers in deg. Default is 0.

radius

Set distance in meters between loudspeakers and the listener with near-field HRTFs. Default is 1.

type

Set processing type. Can be time or freq. time is processing audio in time domain which is slow. freq is processing audio in frequency domain which is fast. Default is freq.

speakers

Set custom positions of virtual loudspeakers. Syntax for this option is: <CH> <AZIM> <ELEV>[|<CH> <AZIM> <ELEV>|...]. Each virtual loudspeaker is described with short channel name following with azimuth and elevation in degrees. Each virtual loudspeaker description is separated by ’|’. For example to override front left and front right channel positions use: ’speakers=FL 45 15|FR 345 15’. Descriptions with unrecognised channel names are ignored.

lfegain

Set custom gain for LFE channels. Value is in dB. Default is 0.

framesize

Set custom frame size in number of samples. Default is 1024. Allowed range is from 1024 to 96000. Only used if option ‘type’ is set to freq.

normalize

Should all IRs be normalized upon importing SOFA file. By default is enabled.

interpolate

Should nearest IRs be interpolated with neighbor IRs if exact position does not match. By default is disabled.

minphase

Minphase all IRs upon loading of SOFA file. By default is disabled.

anglestep

Set neighbor search angle step. Only used if option interpolate is enabled.

radstep

Set neighbor search radius step. Only used if option interpolate is enabled.

#### 36.109.1 Examples# TOC

- Using ClubFritz6 sofa file:

```
sofalizer=sofa=/path/to/ClubFritz6.sofa:type=freq:radius=1

```

- Using ClubFritz12 sofa file and bigger radius with small rotation:

```
sofalizer=sofa=/path/to/ClubFritz12.sofa:type=freq:radius=2:rotation=5

```

- Similar as above but with custom speaker positions for front left, front right, back left and back right and also with custom gain:

```
"sofalizer=sofa=/path/to/ClubFritz6.sofa:type=freq:radius=2:speakers=FL 45|FR 315|BL 135|BR 225:gain=28"

```

### 36.110 speechnorm# TOC

Speech Normalizer.

This filter expands or compresses each half-cycle of audio samples (local set of samples all above or all below zero and between two nearest zero crossings) depending on threshold value, so audio reaches target peak value under conditions controlled by below options.

The filter accepts the following options:

peak, p

Set the expansion target peak value. This specifies the highest allowed absolute amplitude level for the normalized audio input. Default value is 0.95. Allowed range is from 0.0 to 1.0.

expansion, e

Set the maximum expansion factor. Allowed range is from 1.0 to 50.0. Default value is 2.0. This option controls maximum local half-cycle of samples expansion. The maximum expansion would be such that local peak value reaches target peak value but never to surpass it and that ratio between new and previous peak value does not surpass this option value.

compression, c

Set the maximum compression factor. Allowed range is from 1.0 to 50.0. Default value is 2.0. This option controls maximum local half-cycle of samples compression. This option is used only if threshold option is set to value greater than 0.0, then in such cases when local peak is lower or same as value set by threshold all samples belonging to that peak’s half-cycle will be compressed by current compression factor.

threshold, t

Set the threshold value. Default value is 0.0. Allowed range is from 0.0 to 1.0. This option specifies which half-cycles of samples will be compressed and which will be expanded. Any half-cycle samples with their local peak value below or same as this option value will be compressed by current compression factor, otherwise, if greater than threshold value they will be expanded with expansion factor so that it could reach peak target value but never surpass it.

raise, r

Set the expansion raising amount per each half-cycle of samples. Default value is 0.001. Allowed range is from 0.0 to 1.0. This controls how fast expansion factor is raised per each new half-cycle until it reaches expansion value. Setting this options too high may lead to distortions.

fall, f

Set the compression raising amount per each half-cycle of samples. Default value is 0.001. Allowed range is from 0.0 to 1.0. This controls how fast compression factor is raised per each new half-cycle until it reaches compression value.

channels, h

Specify which channels to filter, by default all available channels are filtered.

invert, i

Enable inverted filtering, by default is disabled. This inverts interpretation of threshold option. When enabled any half-cycle of samples with their local peak value below or same as threshold option will be expanded otherwise it will be compressed.

link, l

Link channels when calculating gain applied to each filtered channel sample, by default is disabled. When disabled each filtered channel gain calculation is independent, otherwise when this option is enabled the minimum of all possible gains for each filtered channel is used.

rms, m

Set the expansion target RMS value. This specifies the highest allowed RMS level for the normalized audio input. Default value is 0.0, thus disabled. Allowed range is from 0.0 to 1.0.

#### 36.110.1 Commands# TOC

This filter supports the all above options as commands.

#### 36.110.2 Examples# TOC

- Weak and slow amplification:

```
speechnorm=e=3:r=0.00001:l=1

```

- Moderate and slow amplification:

```
speechnorm=e=6.25:r=0.00001:l=1

```

- Strong and fast amplification:

```
speechnorm=e=12.5:r=0.0001:l=1

```

- Very strong and fast amplification:

```
speechnorm=e=25:r=0.0001:l=1

```

- Extreme and fast amplification:

```
speechnorm=e=50:r=0.0001:l=1

```

### 36.111 stereotools# TOC

This filter has some handy utilities to manage stereo signals, for converting M/S stereo recordings to L/R signal while having control over the parameters or spreading the stereo image of master track.

The filter accepts the following options:

level_in

Set input level before filtering for both channels. Defaults is 1. Allowed range is from 0.015625 to 64.

level_out

Set output level after filtering for both channels. Defaults is 1. Allowed range is from 0.015625 to 64.

balance_in

Set input balance between both channels. Default is 0. Allowed range is from -1 to 1.

balance_out

Set output balance between both channels. Default is 0. Allowed range is from -1 to 1.

softclip

Enable softclipping. Results in analog distortion instead of harsh digital 0dB clipping. Disabled by default.

mutel

Mute the left channel. Disabled by default.

muter

Mute the right channel. Disabled by default.

phasel

Change the phase of the left channel. Disabled by default.

phaser

Change the phase of the right channel. Disabled by default.

mode

Set stereo mode. Available values are:

‘lr>lr’

Left/Right to Left/Right, this is default.

‘lr>ms’

Left/Right to Mid/Side.

‘ms>lr’

Mid/Side to Left/Right.

‘lr>ll’

Left/Right to Left/Left.

‘lr>rr’

Left/Right to Right/Right.

‘lr>l+r’

Left/Right to Left + Right.

‘lr>rl’

Left/Right to Right/Left.

‘ms>ll’

Mid/Side to Left/Left.

‘ms>rr’

Mid/Side to Right/Right.

‘ms>rl’

Mid/Side to Right/Left.

‘lr>l-r’

Left/Right to Left - Right.

slev

Set level of side signal. Default is 1. Allowed range is from 0.015625 to 64.

sbal

Set balance of side signal. Default is 0. Allowed range is from -1 to 1.

mlev

Set level of the middle signal. Default is 1. Allowed range is from 0.015625 to 64.

mpan

Set middle signal pan. Default is 0. Allowed range is from -1 to 1.

base

Set stereo base between mono and inversed channels. Default is 0. Allowed range is from -1 to 1.

delay

Set delay in milliseconds how much to delay left from right channel and vice versa. Default is 0. Allowed range is from -20 to 20.

sclevel

Set S/C level. Default is 1. Allowed range is from 1 to 100.

phase

Set the stereo phase in degrees. Default is 0. Allowed range is from 0 to 360.

bmode_in, bmode_out

Set balance mode for balance_in/balance_out option.

Can be one of the following:

‘balance’

Classic balance mode. Attenuate one channel at time. Gain is raised up to 1.

‘amplitude’

Similar as classic mode above but gain is raised up to 2.

‘power’

Equal power distribution, from -6dB to +6dB range.

#### 36.111.1 Commands# TOC

This filter supports the all above options as commands.

#### 36.111.2 Examples# TOC

- Apply karaoke like effect:

```
stereotools=mlev=0.015625

```

- Convert M/S signal to L/R:

```
"stereotools=mode=ms>lr"

```

### 36.112 stereowiden# TOC

This filter enhance the stereo effect by suppressing signal common to both channels and by delaying the signal of left into right and vice versa, thereby widening the stereo effect.

The filter accepts the following options:

delay

Time in milliseconds of the delay of left signal into right and vice versa. Default is 20 milliseconds.

feedback

Amount of gain in delayed signal into right and vice versa. Gives a delay effect of left signal in right output and vice versa which gives widening effect. Default is 0.3.

crossfeed

