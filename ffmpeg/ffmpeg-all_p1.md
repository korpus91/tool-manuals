# ffmpeg Documentation

#   ffmpeg Documentation

## Table of Contents

- 1 Synopsis

- 2 Description

- 3 Detailed description

- 3.1 Streamcopy

- 3.2 Transcoding

- 3.3 Filtering

- 3.3.1 Simple filtergraphs

- 3.3.2 Complex filtergraphs

- 3.4 Loopback decoders

- 4 Stream selection

- 4.1 Description

- 4.1.1 Automatic stream selection

- 4.1.2 Manual stream selection

- 4.1.3 Complex filtergraphs

- 4.1.4 Stream handling

- 4.2 Examples

- 5 Options

- 5.1 Stream specifiers

- 5.2 Generic options

- 5.3 AVOptions

- 5.4 Main options

- 5.5 Video Options

- 5.6 Advanced Video options

- 5.7 Audio Options

- 5.8 Advanced Audio options

- 5.9 Subtitle options

- 5.10 Advanced Subtitle options

- 5.11 Advanced options

- 5.12 Preset files

- 5.12.1 ffpreset files

- 5.12.2 avpreset files

- 5.13 vstats file format

- 6 Examples

- 6.1 Video and Audio grabbing

- 6.2 X11 grabbing

- 6.3 Video and Audio file format conversion

- 7 Syntax

- 7.1 Quoting and escaping

- 7.1.1 Examples

- 7.2 Date

- 7.3 Time duration

- 7.3.1 Examples

- 7.4 Video size

- 7.5 Video rate

- 7.6 Ratio

- 7.7 Color

- 7.8 Channel Layout

- 8 Expression Evaluation

- 9 Codec Options

- 10 Decoders

- 11 Video Decoders

- 11.1 av1

- 11.1.1 Options

- 11.2 hevc

- 11.2.1 Options

- 11.3 rawvideo

- 11.3.1 Options

- 11.4 libastcenc

- 11.4.1 Options

- 11.5 libdav1d

- 11.5.1 Options

- 11.6 libdavs2

- 11.7 libuavs3d

- 11.7.1 Options

- 11.8 libxevd

- 11.8.1 Options

- 11.9 QSV Decoders

- 11.9.1 Common Options

- 11.9.2 HEVC Options

- 11.10 v210

- 11.10.1 Options

- 12 Audio Decoders

- 12.1 ac3

- 12.1.1 AC-3 Decoder Options

- 12.2 dca

- 12.2.1 DCA Decoder Options

- 12.3 flac

- 12.3.1 FLAC Decoder options

- 12.4 ffwavesynth

- 12.5 libgsm

- 12.6 libilbc

- 12.6.1 Options

- 12.7 libmpeghdec

- 12.8 libopencore-amrnb

- 12.9 libopencore-amrwb

- 12.10 libopus

- 12.11 pcm_dvda

- 13 Subtitles Decoders

- 13.1 libaribb24

- 13.1.1 libaribb24 Decoder Options

- 13.2 libaribcaption

- 13.2.1 libaribcaption Decoder Options

- 13.2.2 libaribcaption decoder usage examples

- 13.3 dvbsub

- 13.3.1 Options

- 13.4 dvdsub

- 13.4.1 Options

- 13.5 libzvbi-teletext

- 13.5.1 Options

- 14 Encoders

- 15 Audio Encoders

- 15.1 aac

- 15.1.1 Options

- 15.2 ac3 and ac3_fixed

- 15.2.1 AC-3 Metadata

- 15.2.1.1 Metadata Control Options

- 15.2.1.2 Downmix Levels

- 15.2.1.3 Audio Production Information

- 15.2.1.4 Other Metadata Options

- 15.2.2 Extended Bitstream Information

- 15.2.2.1 Extended Bitstream Information - Part 1

- 15.2.2.2 Extended Bitstream Information - Part 2

- 15.2.3 Other AC-3 Encoding Options

- 15.2.4 Floating-Point-Only AC-3 Encoding Options

- 15.3 flac

- 15.3.1 Options

- 15.4 opus

- 15.4.1 Options

- 15.5 libfdk_aac

- 15.5.1 Options

- 15.5.2 Examples

- 15.6 libfdk-xhe-aac

- 15.6.1 Options

- 15.7 liblc3

- 15.7.1 Options

- 15.8 libmp3lame

- 15.8.1 Options

- 15.9 libopencore-amrnb

- 15.9.1 Options

- 15.10 libopus

- 15.10.1 Option Mapping

- 15.11 libshine

- 15.11.1 Options

- 15.12 libtwolame

- 15.12.1 Options

- 15.13 libvo-amrwbenc

- 15.13.1 Options

- 15.14 libvorbis

- 15.14.1 Options

- 15.15 mjpeg

- 15.15.1 Options

- 15.16 wavpack

- 15.16.1 Options

- 15.16.1.1 Shared options

- 15.16.1.2 Private options

- 16 Video Encoders

- 16.1 a64_multi, a64_multi5

- 16.2 Cinepak

- 16.2.1 Options

- 16.3 ffv1

- 16.3.1 Options

- 16.4 GIF

- 16.4.1 Options

- 16.5 Hap

- 16.5.1 Options

- 16.6 jpeg2000

- 16.6.1 Options

- 16.7 librav1e

- 16.7.1 Options

- 16.8 libaom-av1

- 16.8.1 Options

- 16.9 liboapv

- 16.9.1 Options

- 16.10 libsvtav1

- 16.10.1 Options

- 16.11 libsvtjpegxs

- 16.11.1 Options

- 16.12 libjxl

- 16.12.1 Options

- 16.13 libkvazaar

- 16.13.1 Options

- 16.14 libopenh264

- 16.14.1 Options

- 16.15 libtheora

- 16.15.1 Options

- 16.15.2 Examples

- 16.16 libvpx

- 16.16.1 Options

- 16.17 libvvenc

- 16.17.1 Supported Pixel Formats

- 16.17.2 Options

- 16.18 libwebp

- 16.18.1 Pixel Format

- 16.18.2 Options

- 16.19 libastcenc

- 16.19.1 Pixel Format

- 16.19.2 Options

- 16.20 libx264, libx264rgb

- 16.20.1 Supported Pixel Formats

- 16.20.2 Options

- 16.21 libx265

- 16.21.1 Options

- 16.22 libxavs2

- 16.22.1 Options

- 16.23 libxeve

- 16.23.1 Options

- 16.24 libxvid

- 16.24.1 Options

- 16.25 MediaCodec

- 16.26 MediaFoundation

- 16.26.1 Options

- 16.26.2 Examples

- 16.27 Microsoft RLE

- 16.27.1 Options

- 16.28 mpeg2

- 16.28.1 Options

- 16.29 NVENC encoders

- 16.29.1 Hardware input and devices

- 16.29.2 Generic options

- 16.29.3 Common options

- 16.29.3.1 Presets and tuning

- 16.29.3.2 Rate control

- 16.29.3.3 Lookahead, adaptive quantization and B-frames

- 16.29.3.4 SEI and side data

- 16.29.3.5 Other common options

- 16.29.4 H.264 and HEVC options

- 16.29.5 HEVC and AV1 options

- 16.29.6 H.264 options

- 16.29.7 HEVC options

- 16.29.8 AV1 options

- 16.30 png

- 16.30.1 Options

- 16.30.2 Private options

- 16.31 ProRes

- 16.31.1 Private Options for prores-ks

- 16.31.2 Speed considerations

- 16.32 QSV Encoders

- 16.32.1 Ratecontrol Method

- 16.32.2 Global Options -> MSDK Options

- 16.32.3 Common Options

- 16.32.4 Runtime Options

- 16.32.5 H264 options

- 16.32.6 HEVC Options

- 16.32.7 MPEG2 Options

- 16.32.8 VP9 Options

- 16.32.9 AV1 Options

- 16.33 snow

- 16.33.1 Options

- 16.34 VAAPI encoders

- 16.35 vbn

- 16.35.1 Options

- 16.36 vc2

- 16.36.1 Options

- 17 Subtitles Encoders

- 17.1 dvbsub

- 17.1.1 Options

- 17.2 dvdsub

- 17.2.1 Options

- 17.3 lrc

- 17.3.1 Options

- 18 Bitstream Filters

- 18.1 aac_adtstoasc

- 18.2 av1_metadata

- 18.3 chomp

- 18.4 dca_core

- 18.5 dovi_rpu

- 18.6 dovi_split

- 18.7 dump_extra

- 18.8 dv_error_marker

- 18.9 eac3_core

- 18.10 eia608_to_smpte436m

- 18.11 extract_extradata

- 18.12 filter_units

- 18.13 hapqa_extract

- 18.14 h264_metadata

- 18.15 h264_mp4toannexb

- 18.16 h264_redundant_pps

- 18.17 hevc_metadata

- 18.18 hevc_mp4toannexb

- 18.19 imxdump

- 18.20 jpegapp

- 18.21 mjpeg2jpeg

- 18.22 mjpegadump

- 18.23 mov2textsub

- 18.24 mpeg2_metadata

- 18.25 mpeg4_unpack_bframes

- 18.26 noise

- 18.26.1 Examples

- 18.27 null

- 18.28 pcm_rechunk

- 18.29 pgs_frame_merge

- 18.30 prores_metadata

- 18.31 remove_extra

- 18.32 setts

- 18.33 showinfo

- 18.34 side_data

- 18.35 smpte436m_to_eia608

- 18.36 text2movsub

- 18.37 trace_headers

- 18.38 trim

- 18.39 truehd_core

- 18.40 vp9_metadata

- 18.41 vp9_superframe

- 18.42 vp9_superframe_split

- 18.43 vp9_raw_reorder

- 19 Format Options

- 19.1 Format stream specifiers

- 20 Demuxers

- 20.1 aa

- 20.2 aac

- 20.3 apng

- 20.4 asf

- 20.5 astc

- 20.6 concat

- 20.6.1 Syntax

- 20.6.2 Options

- 20.6.3 Examples

- 20.7 dash

- 20.7.1 Options

- 20.8 dvdvideo

- 20.8.1 Background

- 20.8.2 Options

- 20.8.3 Examples

- 20.9 ea

- 20.9.1 Options

- 20.10 imf

- 20.11 flv, live_flv, kux

- 20.12 gif

- 20.13 hls

- 20.14 image2

- 20.14.1 Examples

- 20.15 jpeg_mpf

- 20.16 ktx

- 20.17 libgme

- 20.18 libmodplug

- 20.19 libopenmpt

- 20.20 mcc

- 20.20.1 Examples

- 20.21 mov/mp4/3gp

- 20.21.1 Options

- 20.21.2 Audible AAX

- 20.22 mpegts

- 20.23 mpjpeg

- 20.24 rawvideo

- 20.25 rcwt

- 20.25.1 Examples

- 20.26 sbg

- 20.27 tedcaptions

- 20.28 vapoursynth

- 20.29 w64

- 20.30 wav

- 20.31 webp

- 21 Muxers

- 21.1 Raw muxers

- 21.1.1 Examples

- 21.2 Raw PCM muxers

- 21.3 MPEG-1/MPEG-2 program stream muxers

- 21.3.1 Options

- 21.4 MOV/MPEG-4/ISOMBFF muxers

- 21.4.1 Stereoscopic 3D

- 21.4.2 Fragmentation

- 21.4.3 Options

- 21.4.4 Examples

- 21.5 a64

- 21.6 ac4

- 21.6.1 Options

- 21.7 adts

- 21.7.1 Options

- 21.8 aea

- 21.9 aiff

- 21.9.1 Options

- 21.10 alp

- 21.10.1 Options

- 21.11 amr

- 21.12 amv

- 21.13 apm

- 21.14 apng

- 21.14.1 Options

- 21.14.2 Examples

- 21.15 argo_asf

- 21.15.1 Options

- 21.16 argo_cvg

- 21.16.1 Options

- 21.17 asf, asf_stream

- 21.17.1 Options

- 21.18 ass

- 21.18.1 Options

- 21.19 ast

- 21.19.1 Options

- 21.20 astc

- 21.21 au

- 21.22 avi

- 21.22.1 Options

- 21.23 avif

- 21.23.1 Options

- 21.24 avm2

- 21.25 bit

- 21.26 caf

- 21.27 codec2

- 21.28 chromaprint

- 21.28.1 Options

- 21.29 crc

- 21.29.1 Examples

- 21.30 dash

- 21.30.1 Options

- 21.30.2 Example

- 21.31 daud

- 21.31.1 Example

- 21.32 dv

- 21.32.1 Example

- 21.33 ffmetadata

- 21.33.1 Example

- 21.34 fifo

- 21.34.1 Options

- 21.34.2 Example

- 21.35 film_cpk

- 21.36 filmstrip

- 21.37 fits

- 21.38 flac

- 21.38.1 Options

- 21.38.2 Example

- 21.39 flv

- 21.39.1 Options

- 21.40 framecrc

- 21.40.1 Examples

- 21.41 framehash

- 21.41.1 Examples

- 21.42 framemd5

- 21.42.1 Examples

- 21.43 gif

- 21.43.1 Options

- 21.43.2 Example

- 21.44 gxf

- 21.45 hash

- 21.45.1 Examples

- 21.46 hds

- 21.46.1 Options

- 21.46.2 Example

- 21.47 hls

- 21.47.1 Options

- 21.48 iamf

- 21.49 ico

- 21.50 ilbc

- 21.51 image2, image2pipe

- 21.51.1 Options

- 21.51.2 Examples

- 21.52 ircam

- 21.53 iterm2

- 21.53.1 Options

- 21.53.2 Examples

- 21.54 jpeg_mpf

- 21.54.1 Examples

- 21.55 ivf

- 21.56 jacosub

- 21.57 ktx

- 21.57.1 Options

- 21.58 kvag

- 21.59 lc3

- 21.60 lrc

- 21.60.1 Options

- 21.60.2 Metadata

- 21.61 matroska

- 21.61.1 Metadata

- 21.61.2 Options

- 21.62 md5

- 21.62.1 Examples

- 21.63 mcc

- 21.63.1 Options

- 21.63.2 Examples

- 21.64 microdvd

- 21.65 mmf

- 21.66 mp3

- 21.67 mpegts

- 21.67.1 Options

- 21.67.2 Example

- 21.68 mxf, mxf_d10, mxf_opatom

- 21.68.1 Options

- 21.69 null

- 21.70 nut

- 21.71 ogg

- 21.72 pdv

- 21.73 rcwt

- 21.73.1 Examples

- 21.74 segment, stream_segment, ssegment

- 21.74.1 Options

- 21.74.2 Examples

- 21.75 smoothstreaming

- 21.76 streamhash

- 21.76.1 Examples

- 21.77 tee

- 21.77.1 Options

- 21.77.2 Examples

- 21.78 wav

- 21.78.1 Options

- 21.79 webm_chunk

- 21.79.1 Options

- 21.79.2 Example

- 21.80 webm_dash_manifest

- 21.80.1 Options

- 21.80.2 Example

- 21.81 whip

- 21.81.1 Options

- 22 Metadata

- 23 Protocol Options

- 24 Protocols

- 24.1 amqp

- 24.2 async

- 24.3 bluray

- 24.4 cache

- 24.5 concat

- 24.6 concatf

- 24.7 crypto

- 24.8 data

- 24.9 fd

- 24.10 file

- 24.11 ftp

- 24.12 gopher

- 24.13 gophers

- 24.14 handle

- 24.15 http

- 24.15.1 HTTP Cookies

- 24.16 Icecast

- 24.17 ipfs

- 24.18 mmst

- 24.19 mmsh

- 24.20 md5

- 24.21 pipe

- 24.22 prompeg

- 24.23 rist

- 24.24 rtmp

- 24.25 rtmpe

- 24.26 rtmps

- 24.27 rtmpt

- 24.28 rtmpte

- 24.29 rtmpts

- 24.30 libcurl

- 24.31 libsmbclient

- 24.32 libssh

- 24.33 librtmp rtmp, rtmpe, rtmps, rtmpt, rtmpte

- 24.34 rtp

- 24.35 rtsp

- 24.35.1 Muxer

- 24.35.2 Demuxer

- 24.35.3 Examples

- 24.36 sap

- 24.36.1 Muxer

- 24.36.2 Demuxer

- 24.37 sctp

- 24.38 shared

- 24.39 srt

- 24.40 srtp

- 24.41 subfile

- 24.42 tee

- 24.43 tcp

- 24.44 tls

- 24.45 dtls

- 24.46 udp

- 24.46.1 Examples

- 24.47 unix

- 24.48 zmq

- 25 Device Options

- 26 Input Devices

- 26.1 alsa

- 26.1.1 Options

- 26.2 android_camera

- 26.2.1 Options

- 26.3 avfoundation

- 26.3.1 Options

- 26.3.2 Examples

- 26.4 decklink

- 26.4.1 Options

- 26.4.2 Examples

- 26.5 dshow

- 26.5.1 Options

- 26.5.2 Examples

- 26.6 fbdev

- 26.6.1 Options

- 26.7 gdigrab

- 26.7.1 Options

- 26.8 iec61883

- 26.8.1 Options

- 26.8.2 Examples

- 26.9 jack

- 26.9.1 Options

- 26.10 kmsgrab

- 26.10.1 Options

- 26.10.2 Examples

- 26.11 lavfi

- 26.11.1 Options

- 26.11.2 Examples

- 26.12 libcdio

- 26.12.1 Options

- 26.13 libdc1394

- 26.13.1 Options

- 26.14 openal

- 26.14.1 Options

- 26.14.2 Examples

- 26.15 oss

- 26.15.1 Options

- 26.16 pulse

- 26.16.1 Options

- 26.16.2 Examples

- 26.17 sndio

- 26.17.1 Options

- 26.18 video4linux2, v4l2

- 26.18.1 Options

- 26.19 vfwcap

- 26.19.1 Options

- 26.20 x11grab

- 26.20.1 Options

- 27 Output Devices

- 27.1 alsa

- 27.1.1 Examples

- 27.2 AudioToolbox

- 27.2.1 Options

- 27.2.2 Examples

- 27.3 caca

- 27.3.1 Options

- 27.3.2 Examples

- 27.4 decklink

- 27.4.1 Options

- 27.4.2 Examples

- 27.5 fbdev

- 27.5.1 Options

- 27.5.2 Examples

- 27.6 oss

- 27.7 pulse

- 27.7.1 Options

- 27.7.2 Examples

- 27.8 sndio

- 27.9 v4l2

- 27.10 xv

- 27.10.1 Options

- 27.10.2 Examples

- 28 Resampler Options

- 29 Scaler Options

- 30 Filtering Introduction

- 31 graph2dot

- 32 Filtergraph description

- 32.1 Filtergraph syntax

- 32.2 Notes on filtergraph escaping

- 33 Timeline editing

- 34 Changing options at runtime with a command

- 35 Options for filters with several inputs (framesync)

- 36 Audio Filters

- 36.1 aap

- 36.2 acompressor

- 36.2.1 Commands

- 36.3 acontrast

- 36.4 acopy

- 36.5 acrossfade

- 36.5.1 Examples

- 36.6 acrossover

- 36.6.1 Examples

- 36.7 acrusher

- 36.7.1 Commands

- 36.8 acue

- 36.9 adeclick

- 36.10 adeclip

- 36.11 adecorrelate

- 36.12 adelay

- 36.12.1 Examples

- 36.13 adenorm

- 36.13.1 Commands

- 36.14 aderivative, aintegral

- 36.15 adrc

- 36.15.1 Commands

- 36.15.2 Examples

- 36.16 adynamicequalizer

- 36.16.1 Commands

- 36.17 adynamicsmooth

- 36.17.1 Commands

- 36.18 aecho

- 36.18.1 Examples

- 36.19 aemphasis

- 36.19.1 Commands

- 36.20 aeval

- 36.20.1 Examples

- 36.21 aexciter

- 36.21.1 Commands

- 36.22 afade

- 36.22.1 Commands

- 36.22.2 Examples

- 36.23 afftdn

- 36.23.1 Commands

- 36.23.2 Examples

- 36.24 afftfilt

- 36.24.1 Examples

- 36.25 afir

- 36.25.1 Examples

- 36.26 aformat

- 36.27 afreqshift

- 36.27.1 Commands

- 36.28 afwtdn

- 36.28.1 Commands

- 36.29 agate

- 36.29.1 Commands

- 36.30 aiir

- 36.30.1 Examples

- 36.31 alimiter

- 36.32 allpass

- 36.32.1 Commands

- 36.33 aloop

- 36.34 amerge

- 36.34.1 Examples

- 36.35 amix

- 36.35.1 Examples

- 36.35.2 Commands

- 36.36 amultiply

- 36.37 anequalizer

- 36.37.1 Examples

- 36.37.2 Commands

- 36.38 anlmdn

- 36.38.1 Commands

- 36.39 anlmf, anlms

- 36.39.1 Examples

- 36.39.2 Commands

- 36.40 anull

- 36.41 apad

- 36.41.1 Examples

- 36.42 aphaser

- 36.43 aphaseshift

- 36.43.1 Commands

- 36.44 apsnr

- 36.45 apsyclip

- 36.45.1 Commands

- 36.46 apulsator

- 36.47 aresample

- 36.47.1 Examples

- 36.48 areverse

- 36.48.1 Examples

- 36.49 arls

- 36.50 arnndn

- 36.50.1 Commands

- 36.51 asdr

- 36.52 asetnsamples

- 36.53 asetrate

- 36.54 ashowinfo

- 36.55 asisdr

- 36.56 asoftclip

- 36.56.1 Commands

- 36.57 aspectralstats

- 36.58 asr

- 36.59 astats

- 36.60 asubboost

- 36.60.1 Commands

- 36.61 asubcut

- 36.61.1 Commands

- 36.62 asupercut

- 36.62.1 Commands

- 36.63 asuperpass

- 36.63.1 Commands

- 36.64 asuperstop

- 36.64.1 Commands

- 36.65 atempo

- 36.65.1 Examples

- 36.65.2 Commands

- 36.66 atilt

- 36.66.1 Commands

- 36.67 atrim

- 36.68 axcorrelate

- 36.68.1 Examples

- 36.69 bandpass

- 36.69.1 Commands

- 36.70 bandreject

- 36.70.1 Commands

- 36.71 bass, lowshelf

- 36.71.1 Commands

- 36.72 biquad

- 36.72.1 Commands

- 36.73 bs2b

- 36.74 channelmap

- 36.74.1 Examples

- 36.75 channelsplit

- 36.75.1 Examples

- 36.76 chorus

- 36.76.1 Examples

- 36.77 compand

- 36.77.1 Examples

- 36.78 compensationdelay

- 36.78.1 Commands

- 36.79 crossfeed

- 36.79.1 Commands

- 36.80 crystalizer

- 36.80.1 Commands

- 36.81 dcshift

- 36.82 deesser

- 36.83 dialoguenhance

- 36.83.1 Commands

- 36.84 drmeter

- 36.85 dynaudnorm

- 36.85.1 Commands

- 36.86 earwax

- 36.87 equalizer

- 36.87.1 Examples

- 36.87.2 Commands

- 36.88 extrastereo

- 36.88.1 Commands

- 36.89 firequalizer

- 36.89.1 Examples

- 36.90 flanger

- 36.91 haas

- 36.92 hdcd

- 36.93 headphone

- 36.93.1 Examples

- 36.94 highpass

- 36.94.1 Commands

- 36.95 join

- 36.96 ladspa

- 36.96.1 Examples

- 36.96.2 Commands

- 36.97 loudnorm

- 36.98 lowpass

- 36.98.1 Examples

- 36.98.2 Commands

- 36.99 lv2

- 36.99.1 Examples

- 36.99.2 Commands

- 36.100 mcompand

- 36.101 pan

- 36.101.1 Mixing examples

- 36.101.2 Remapping examples

- 36.102 replaygain

- 36.103 resample

- 36.104 rubberband

- 36.104.1 Commands

- 36.105 sidechaincompress

- 36.105.1 Commands

- 36.105.2 Examples

- 36.106 sidechaingate

- 36.106.1 Commands

- 36.107 silencedetect

- 36.107.1 Examples

- 36.108 silenceremove

- 36.108.1 Examples

- 36.108.2 Commands

- 36.109 sofalizer

- 36.109.1 Examples

- 36.110 speechnorm

- 36.110.1 Commands

- 36.110.2 Examples

- 36.111 stereotools

- 36.111.1 Commands

- 36.111.2 Examples

- 36.112 stereowiden

- 36.112.1 Commands

- 36.113 superequalizer

- 36.114 surround

- 36.115 tiltshelf

- 36.115.1 Commands

- 36.116 treble, highshelf

- 36.116.1 Commands

- 36.117 tremolo

- 36.118 vibrato

- 36.119 virtualbass

- 36.120 volume

- 36.120.1 Commands

- 36.120.2 Examples

- 36.121 volumedetect

- 36.121.1 Examples

- 36.122 whisper

- 36.122.1 Examples

- 37 Audio Sources

- 37.1 abuffer

- 37.1.1 Examples

- 37.2 aevalsrc

- 37.2.1 Examples

- 37.3 afdelaysrc

- 37.4 afireqsrc

- 37.5 afirsrc

- 37.6 anullsrc

- 37.6.1 Examples

- 37.7 flite

- 37.7.1 Examples

- 37.8 anoisesrc

- 37.8.1 Examples

- 37.9 hilbert

- 37.10 sinc

- 37.11 sine

- 37.11.1 Examples

- 38 Audio Sinks

- 38.1 abuffersink

- 38.2 anullsink

- 39 Video Filters

- 39.1 addroi

- 39.1.1 Examples

- 39.2 alphaextract

- 39.3 alphamerge

- 39.4 amplify

- 39.4.1 Commands

- 39.5 ass

- 39.5.1 Commands

- 39.6 atadenoise

- 39.6.1 Commands

- 39.7 avgblur

- 39.7.1 Commands

- 39.8 backgroundkey

- 39.8.1 Commands

- 39.9 bbox

- 39.9.1 Commands

- 39.10 bilateral

- 39.10.1 Commands

- 39.11 bitplanenoise

- 39.12 blackdetect, blackdetect_vulkan

- 39.13 blackframe

- 39.14 blend

- 39.14.1 Examples

- 39.14.2 Commands

- 39.15 blockdetect

- 39.15.1 Examples

- 39.16 blurdetect

- 39.16.1 Examples

- 39.17 bm3d

- 39.17.1 Examples

- 39.18 boxblur

- 39.18.1 Examples

- 39.19 bwdif

- 39.20 ccrepack

- 39.21 cas

- 39.21.1 Commands

- 39.22 chromahold

- 39.22.1 Commands

- 39.23 chromakey

- 39.23.1 Commands

- 39.23.2 Examples

- 39.24 chromanr

- 39.24.1 Commands

- 39.25 chromashift

- 39.25.1 Commands

- 39.26 ciescope

- 39.27 codecview

- 39.27.1 Examples

- 39.28 colorbalance

- 39.28.1 Examples

- 39.28.2 Commands

- 39.29 colorcontrast

- 39.29.1 Commands

- 39.30 colorcorrect

- 39.30.1 Commands

- 39.31 colorchannelmixer

- 39.31.1 Examples

- 39.31.2 Commands

- 39.32 colordetect

- 39.33 colorize

- 39.33.1 Commands

- 39.34 colorkey

- 39.34.1 Examples

- 39.34.2 Commands

- 39.35 colorhold

- 39.35.1 Commands

- 39.36 colorlevels

- 39.36.1 Examples

- 39.36.2 Commands

- 39.37 colormap

- 39.38 colormatrix

- 39.39 colorspace

- 39.40 colortemperature

- 39.40.1 Commands

- 39.41 convolution

- 39.41.1 Commands

- 39.41.2 Examples

- 39.42 convolve

- 39.43 copy

- 39.44 coreimage

- 39.44.1 Examples

- 39.45 corr

- 39.46 cover_rect

- 39.46.1 Examples

- 39.47 crop

- 39.47.1 Examples

- 39.47.2 Commands

- 39.48 cropdetect

- 39.48.1 Examples

- 39.48.2 Commands

- 39.49 cue

- 39.50 curves

- 39.50.1 Commands

- 39.50.2 Examples

- 39.51 datascope

- 39.51.1 Commands

- 39.52 dblur

- 39.52.1 Commands

- 39.53 dctdnoiz

- 39.53.1 Examples

- 39.54 deband

- 39.54.1 Commands

- 39.55 deblock

- 39.55.1 Examples

- 39.55.2 Commands

- 39.56 decimate

- 39.57 deconvolve

- 39.58 dedot

- 39.59 deflate

- 39.59.1 Commands

- 39.60 deflicker

- 39.61 deinterlace_d3d12

- 39.61.1 Examples

- 39.62 dejudder

- 39.63 delogo

- 39.63.1 Examples

- 39.64 derain

- 39.65 deshake

- 39.66 despill

- 39.66.1 Commands

- 39.67 detelecine

- 39.68 dilation

- 39.68.1 Commands

- 39.69 displace

- 39.69.1 Examples

- 39.70 dnn_classify

- 39.71 dnn_detect

- 39.71.1 Examples

- 39.72 dnn_processing

- 39.72.1 Examples

- 39.73 drawbox

- 39.73.1 Examples

- 39.73.2 Commands

- 39.74 drawgraph

- 39.75 drawgrid

- 39.75.1 Examples

- 39.75.2 Commands

- 39.76 drawtext

- 39.76.1 Syntax

- 39.76.2 Text expansion

- 39.76.3 Commands

- 39.76.4 Examples

- 39.77 drawvg

- 39.77.1 Parameters

- 39.77.2 Pixel Formats

- 39.77.3 Examples

- 39.78 edgedetect

- 39.78.1 Examples

- 39.79 elbg

- 39.80 entropy

- 39.81 epx

- 39.82 eq

- 39.82.1 Commands

- 39.83 erosion

- 39.83.1 Commands

- 39.84 estdif

- 39.84.1 Commands

- 39.85 exposure

- 39.85.1 Commands

- 39.86 extractplanes

- 39.86.1 Examples

- 39.87 fade

- 39.87.1 Examples

- 39.88 feedback

- 39.88.1 Examples

- 39.89 fftdnoiz

- 39.90 fftfilt

- 39.90.1 Examples

- 39.91 field

- 39.92 fieldhint

- 39.93 fieldmatch

- 39.93.1 p/c/n/u/b meaning

- 39.93.1.1 p/c/n

- 39.93.1.2 u/b

- 39.93.2 Examples

- 39.94 fieldorder

- 39.95 fillborders

- 39.95.1 Commands

- 39.96 find_rect

- 39.96.1 Examples

- 39.97 floodfill

- 39.98 format

- 39.98.1 Examples

- 39.99 fps

- 39.99.1 Examples

- 39.100 framepack

- 39.101 framerate

- 39.102 frc_amf

- 39.103 vqe_amf

- 39.104 framestep

- 39.105 freezedetect

- 39.106 freezeframes

- 39.107 frei0r

- 39.107.1 Examples

- 39.107.2 Commands

- 39.108 fspp

- 39.109 fsync

- 39.110 gainmap

- 39.110.1 Examples

- 39.111 gblur

- 39.111.1 Commands

- 39.112 geq

- 39.112.1 Examples

- 39.113 gradfun

- 39.113.1 Examples

- 39.114 graphmonitor

- 39.115 grayworld

- 39.116 greyedge

- 39.116.1 Examples

- 39.117 guided

- 39.117.1 Commands

- 39.117.2 Examples

- 39.118 haldclut

- 39.118.1 Commands

- 39.118.2 Workflow examples

- 39.118.2.1 Hald CLUT video stream

- 39.118.2.2 Hald CLUT with preview

- 39.119 hflip

- 39.120 histeq

- 39.121 histogram

- 39.121.1 Examples

- 39.122 hqdn3d

- 39.122.1 Commands

- 39.123 hwdownload

- 39.124 hwmap

- 39.125 hwupload

- 39.126 hwupload_cuda

- 39.127 hqx

- 39.128 hstack

- 39.129 hsvhold

- 39.130 hsvkey

- 39.131 hue

- 39.131.1 Examples

- 39.131.2 Commands

- 39.132 huesaturation

- 39.133 hysteresis

- 39.134 iccdetect

- 39.135 iccgen

- 39.136 identity

- 39.137 idet

- 39.137.1 Examples

- 39.138 il

- 39.138.1 Commands

- 39.139 inflate

- 39.139.1 Commands

- 39.140 interlace, interlace_vulkan

- 39.141 kerndeint

- 39.141.1 Examples

- 39.142 kirsch

- 39.142.1 Commands

- 39.143 lagfun

- 39.143.1 Commands

- 39.144 latticepal

- 39.145 lenscorrection

- 39.145.1 Options

- 39.145.2 Commands

- 39.146 lensfun

- 39.146.1 Examples

- 39.147 lcevc

- 39.148 libplacebo

- 39.148.1 Options

- 39.148.1.1 Output mode

- 39.148.1.2 Scaling

- 39.148.1.3 Deinterlacing

- 39.148.1.4 Debanding

- 39.148.1.5 Color adjustment

- 39.148.1.6 Peak detection

- 39.148.1.7 Tone mapping

- 39.148.1.8 Dithering

- 39.148.1.9 Custom shaders

- 39.148.1.10 Debugging / performance

- 39.148.2 Commands

- 39.148.3 Examples

- 39.149 libvmaf

- 39.149.1 Examples

- 39.150 libvmaf_cuda

- 39.150.1 Examples

- 39.151 limitdiff

- 39.151.1 Commands

- 39.152 limiter

- 39.152.1 Commands

- 39.153 loop

- 39.153.1 Examples

- 39.154 lut1d

- 39.154.1 Commands

- 39.155 lut3d

- 39.155.1 Commands

- 39.156 lumakey

- 39.156.1 Commands

- 39.157 lut, lutrgb, lutyuv

- 39.157.1 Commands

- 39.157.2 Examples

- 39.158 lut2, tlut2

- 39.158.1 Commands

- 39.158.2 Examples

- 39.159 maskedclamp

- 39.159.1 Commands

- 39.160 maskedmax

- 39.160.1 Commands

- 39.161 maskedmerge

- 39.161.1 Commands

- 39.162 maskedmin

- 39.162.1 Commands

- 39.163 maskedthreshold

- 39.163.1 Commands

- 39.164 maskfun

- 39.164.1 Commands

- 39.165 mcdeint

- 39.166 median

- 39.166.1 Commands

- 39.167 mergeplanes

- 39.167.1 Examples

- 39.168 mestimate

- 39.169 mestimate_d3d12

- 39.169.1 Examples

- 39.170 midequalizer

- 39.171 minterpolate

- 39.172 mix

- 39.172.1 Commands

- 39.173 monochrome

- 39.173.1 Commands

- 39.174 morpho

- 39.174.1 Commands

- 39.175 mpdecimate

- 39.176 msad

- 39.177 multiply

- 39.177.1 Commands

- 39.178 negate

- 39.178.1 Commands

- 39.179 nlmeans

- 39.180 nnedi

- 39.180.1 Commands

- 39.181 noformat

- 39.181.1 Examples

- 39.182 noise

- 39.182.1 Examples

- 39.183 normalize

- 39.183.1 Commands

- 39.183.2 Examples

- 39.184 null

- 39.185 ocio

- 39.185.1 Examples

- 39.186 ocr

- 39.187 ocv

- 39.187.1 dilate

- 39.187.2 erode

- 39.187.3 smooth

- 39.188 oscilloscope

- 39.188.1 Commands

- 39.188.2 Examples

- 39.189 overlay

- 39.189.1 Commands

- 39.189.2 Examples

- 39.190 owdenoise

- 39.191 pad

- 39.191.1 Examples

- 39.192 palettegen

- 39.192.1 Examples

- 39.193 paletteuse

- 39.193.1 Examples

- 39.194 perspective

- 39.195 phase

- 39.195.1 Commands

- 39.196 photosensitivity

- 39.197 pixdesctest

- 39.198 pixelize

- 39.198.1 Commands

- 39.199 pixscope

- 39.199.1 Commands

- 39.200 pp7

- 39.201 premultiply

- 39.202 premultiply_dynamic

- 39.203 prewitt

- 39.203.1 Commands

- 39.204 pseudocolor

- 39.204.1 Commands

- 39.204.2 Examples

- 39.205 psnr

- 39.205.1 Examples

- 39.206 pullup

- 39.207 qp

- 39.207.1 Examples

- 39.208 qrencode

- 39.208.1 qrencode Expressions

- 39.208.2 qrencode Text expansion

- 39.208.3 Examples

- 39.209 quirc

- 39.210 random

- 39.211 readeia608

- 39.211.1 Commands

- 39.211.2 Examples

- 39.212 readvitc

- 39.212.1 Examples

- 39.213 remap

- 39.214 removegrain

- 39.215 removelogo

- 39.216 repeatfields

- 39.217 reverse

- 39.217.1 Examples

- 39.218 rgbashift

- 39.218.1 Commands

- 39.219 roberts

- 39.219.1 Commands

- 39.220 rotate

- 39.220.1 Examples

- 39.220.2 Commands

- 39.221 sab

- 39.222 scale

- 39.222.1 Options

- 39.222.2 Examples

- 39.222.3 Commands

- 39.223 scharr

- 39.223.1 Commands

- 39.224 scroll

- 39.224.1 Commands

- 39.225 scdet

- 39.226 selectivecolor

- 39.226.1 Examples

- 39.227 separatefields

- 39.228 setdar, setsar

- 39.228.1 Examples

- 39.229 setfield

- 39.230 setparams

- 39.231 shear

- 39.231.1 Commands

- 39.232 showinfo

- 39.233 showpalette

- 39.234 shuffleframes

- 39.234.1 Examples

- 39.235 shufflepixels

- 39.236 shuffleplanes

- 39.236.1 Examples

- 39.237 signalstats

- 39.237.1 Examples

- 39.238 signature

- 39.238.1 Examples

- 39.239 siti

- 39.239.1 Examples

- 39.240 smartblur

- 39.241 sobel

- 39.241.1 Commands

- 39.242 spp

- 39.242.1 Commands

- 39.243 sr

- 39.244 sr_amf

- 39.244.1 Examples

- 39.245 ssim

- 39.245.1 Examples

- 39.246 stereo3d

- 39.246.1 Examples

- 39.247 streamselect, astreamselect

- 39.247.1 Commands

- 39.247.2 Examples

- 39.248 subtitles

- 39.249 super2xsai

- 39.250 swaprect

- 39.250.1 Commands

- 39.251 swapuv

- 39.252 tblend

- 39.253 telecine

- 39.254 thistogram

- 39.255 threshold

- 39.255.1 Commands

- 39.255.2 Examples

- 39.256 thumbnail

- 39.256.1 Examples

- 39.257 tile

- 39.257.1 Examples

- 39.258 tiltandshift

- 39.259 tinterlace

- 39.260 tmedian

- 39.260.1 Commands

- 39.261 tmidequalizer

- 39.262 tmix

- 39.262.1 Examples

- 39.262.2 Commands

- 39.263 tonemap

- 39.263.1 Options

- 39.264 tpad

- 39.265 transpose

- 39.266 trim

- 39.267 unpremultiply

- 39.268 unsharp

- 39.268.1 Examples

- 39.269 untile

- 39.269.1 Examples

- 39.270 uspp

- 39.271 v360

- 39.271.1 Examples

- 39.271.2 Commands

- 39.272 vaguedenoiser

- 39.273 varblur

- 39.273.1 Commands

- 39.274 vectorscope

- 39.275 vidstabdetect

- 39.275.1 Examples

- 39.276 vidstabtransform

- 39.276.1 Options

- 39.276.2 Examples

- 39.277 vflip

- 39.278 vfrdet

- 39.279 vibrance

- 39.279.1 Commands

- 39.280 vif

- 39.281 vignette

- 39.281.1 Expressions

- 39.281.2 Examples

- 39.282 vmafmotion

- 39.283 vpp_amf

- 39.283.1 Examples

- 39.284 vstack

- 39.285 w3fdif

- 39.285.1 Commands

- 39.286 waveform

- 39.287 weave, doubleweave

- 39.287.1 Examples

- 39.288 xbr

- 39.289 xcorrelate

- 39.290 xfade

- 39.290.1 Examples

- 39.291 xmedian

- 39.291.1 Commands

- 39.292 xpsnr

- 39.292.1 Examples

- 39.293 xstack

- 39.293.1 Examples

- 39.294 yadif

- 39.295 yaepblur

- 39.295.1 Commands

- 39.296 zoompan

- 39.296.1 Examples

- 39.297 zscale

- 39.297.1 Options

- 39.297.2 Commands

- 40 CUDA Video Filters

- 40.1 bilateral_cuda

- 40.1.1 Examples

- 40.2 bwdif_cuda

- 40.3 chromakey_cuda

- 40.3.1 Examples

- 40.4 colorspace_cuda

- 40.5 overlay_cuda

- 40.6 pad_cuda

- 40.6.1 Examples

- 40.7 scale_cuda

- 40.7.1 Examples

- 40.8 thumbnail_cuda

- 40.8.1 Example

- 40.9 transpose_cuda

- 40.10 yadif_cuda

- 41 OpenCL Video Filters

- 41.1 avgblur_opencl

- 41.1.1 Example

- 41.2 boxblur_opencl

- 41.2.1 Examples

- 41.3 colorkey_opencl

- 41.3.1 Examples

- 41.4 convolution_opencl

- 41.4.1 Examples

- 41.5 erosion_opencl

- 41.5.1 Example

- 41.6 deshake_opencl

- 41.6.1 Examples

- 41.7 dilation_opencl

- 41.7.1 Example

- 41.8 nlmeans_opencl

- 41.9 overlay_opencl

- 41.9.1 Examples

- 41.10 pad_opencl

- 41.11 prewitt_opencl

- 41.11.1 Example

- 41.12 program_opencl

- 41.13 remap_opencl

- 41.14 roberts_opencl

- 41.14.1 Example

- 41.15 sobel_opencl

- 41.15.1 Example

- 41.16 tonemap_opencl

- 41.16.1 Example

- 41.17 unsharp_opencl

- 41.17.1 Examples

- 41.18 xfade_opencl

- 42 VAAPI Video Filters

- 42.1 overlay_vaapi

- 42.1.1 Examples

- 42.2 tonemap_vaapi

- 42.2.1 Example

- 42.3 hstack_vaapi

- 42.4 vstack_vaapi

- 42.5 xstack_vaapi

- 42.6 pad_vaapi

- 42.7 drawbox_vaapi

- 42.7.1 Examples

- 43 VideoToolbox Video Filters

- 43.1 scale_vt

- 43.1.1 Examples

- 43.2 transpose_vt

- 44 Vulkan Video Filters

- 44.1 avgblur_vulkan

- 44.2 blend_vulkan

- 44.3 bwdif_vulkan

- 44.4 chromaber_vulkan

- 44.5 color_vulkan

- 44.6 vflip_vulkan

- 44.7 hflip_vulkan

- 44.8 flip_vulkan

- 44.9 fruc_vulkan

- 44.10 gblur_vulkan

- 44.11 nlmeans_vulkan

- 44.12 overlay_vulkan

- 44.13 transpose_vulkan

- 44.14 v360_vulkan

- 44.14.1 Examples

- 45 QSV Video Filters

- 45.1 hstack_qsv

- 45.2 vstack_qsv

- 45.3 xstack_qsv

- 46 Video Sources

- 46.1 buffer

- 46.2 cellauto

- 46.2.1 Examples

- 46.3 coreimagesrc

- 46.3.1 Examples

- 46.4 ddagrab

- 46.4.1 Examples

- 46.5 gfxcapture

- 46.5.1 Examples

- 46.6 gradients

- 46.6.1 Commands

- 46.7 mandelbrot

- 46.8 mptestsrc

- 46.9 frei0r_src

- 46.10 life

- 46.10.1 Examples

- 46.11 perlin

- 46.11.1 Options

- 46.11.2 Examples

- 46.12 qrencodesrc

- 46.12.1 Examples

- 46.13 allrgb, allyuv, color, colorchart, colorspectrum, haldclutsrc, nullsrc, pal75bars, pal100bars, rgbtestsrc, smptebars, smptehdbars, testsrc, testsrc2, yuvtestsrc

- 46.13.1 Examples

- 46.13.2 Commands

- 46.14 openclsrc

- 46.15 sierpinski

- 46.16 zoneplate

- 46.16.1 Commands

- 46.16.2 Examples

- 47 Video Sinks

- 47.1 buffersink

- 47.2 nullsink

- 48 Multimedia Filters

- 48.1 a3dscope

- 48.1.1 Commands

- 48.2 abitscope

- 48.3 adrawgraph

- 48.4 agraphmonitor

- 48.5 ahistogram

- 48.6 aphasemeter

- 48.6.1 phasing detection

- 48.6.2 Examples

- 48.7 avectorscope

- 48.7.1 Examples

- 48.7.2 Commands

- 48.8 bench, abench

- 48.8.1 Examples

- 48.9 concat

- 48.9.1 Examples

- 48.9.2 Commands

- 48.10 ebur128

- 48.10.1 Examples

- 48.11 interleave, ainterleave

- 48.11.1 Examples

- 48.12 latency, alatency

- 48.13 metadata, ametadata

- 48.13.1 Examples

- 48.14 perms, aperms

- 48.15 realtime, arealtime

- 48.15.1 Commands

- 48.16 segment, asegment

- 48.16.1 Examples

- 48.17 select, aselect

- 48.17.1 Examples

- 48.18 sendcmd, asendcmd

- 48.18.1 Commands syntax

- 48.18.2 Examples

- 48.19 setpts, asetpts

- 48.19.1 Examples

- 48.19.2 Commands

- 48.20 setrange

- 48.21 settb, asettb

- 48.21.1 Examples

- 48.22 showcqt

- 48.22.1 Examples

- 48.23 showcwt

- 48.24 showfreqs

- 48.25 showspatial

- 48.26 showspectrum

- 48.26.1 Examples

- 48.27 showspectrumpic

- 48.27.1 Examples

- 48.28 showvolume

- 48.29 showwaves

- 48.29.1 Examples

- 48.30 showwavespic

- 48.30.1 Examples

- 48.31 sidedata, asidedata

- 48.32 spectrumsynth

- 48.32.1 Examples

- 48.33 split, asplit

- 48.33.1 Examples

- 48.34 zmq, azmq

- 48.34.1 Examples

- 49 Multimedia Sources

- 49.1 amovie

- 49.2 avsynctest

- 49.2.1 Commands

- 49.3 movie

- 49.3.1 Examples

- 49.3.2 Commands

- 50 External libraries

- 50.1 Alliance for Open Media (AOM)

- 50.2 ARM ASTC Encoder

- 50.3 AMD AMF/VCE

- 50.4 AviSynth

- 50.5 Chromaprint

- 50.6 codec2

- 50.7 dav1d

- 50.8 davs2

- 50.9 uavs3d

- 50.10 Game Music Emu

- 50.11 Intel QuickSync Video

- 50.12 Kvazaar

- 50.13 LAME

- 50.14 LCEVCdec

- 50.15 libilbc

- 50.16 libjxl

- 50.17 libvpx

- 50.18 ModPlug

- 50.19 ONNX Runtime

- 50.20 OpenCORE, VisualOn, and Fraunhofer libraries

- 50.20.1 OpenCORE AMR

- 50.20.2 VisualOn AMR-WB encoder library

- 50.20.3 Fraunhofer AAC library

- 50.20.4 Fraunhofer xHE-AAC library

- 50.20.5 Fraunhofer MPEG-H 3D Audio decoder library

- 50.20.6 LC3 library

- 50.21 OpenH264

- 50.22 OpenJPEG

- 50.23 rav1e

- 50.24 SVT-AV1

- 50.25 SVT-JPEG-XS

- 50.26 TwoLAME

- 50.27 VapourSynth

- 50.28 x264

- 50.29 x265

- 50.30 xavs

- 50.31 xavs2

- 50.32 eXtra-fast Essential Video Encoder (XEVE)

- 50.33 eXtra-fast Essential Video Decoder (XEVD)

- 50.34 ZVBI

- 51 Supported File Formats, Codecs or Features

- 51.1 File Formats

- 51.2 Image Formats

- 51.3 Video Codecs

- 51.4 Audio Codecs

- 51.5 Subtitle Formats

- 51.6 Network Protocols

- 51.7 Input/Output Devices

- 51.8 Timecode

- 52 See Also

- 53 Authors

## 1 Synopsis# TOC

ffmpeg [global_options] {[input_file_options] -i input_url} ... {[output_file_options] output_url} ...

## 2 Description# TOC

ffmpeg is a universal media converter. It can read a wide variety of inputs - including live grabbing/recording devices - filter, and transcode them into a plethora of output formats.

ffmpeg reads from an arbitrary number of inputs (which can be regular files, pipes, network streams, grabbing devices, etc.), specified by the -i option, and writes to an arbitrary number of outputs, which are specified by a plain output url. Anything found on the command line which cannot be interpreted as an option is considered to be an output url.

Each input or output can, in principle, contain any number of elementary streams of different types (video/audio/subtitle/attachment/data), though the allowed stream counts and/or types may be limited by the container format. Selecting which streams from which inputs will go into which output is either done automatically or with the -map option (see the Stream selection chapter).

To refer to inputs/outputs in options, you must use their indices (0-based). E.g. the first input is 0, the second is 1, etc. Similarly, streams within an input/output are referred to by their indices. E.g. 2:3 refers to the fourth stream in the third input or output. Also see the Stream specifiers chapter.

As a general rule, options are applied to the next specified file. Therefore, order is important, and you can have the same option on the command line multiple times. Each occurrence is then applied to the next input or output file. Exceptions from this rule are the global options (e.g. verbosity level), which should be specified first.

Do not mix input and output files – first specify all input files, then all output files. Also do not mix options which belong to different files. All options apply ONLY to the next input or output file and are reset between files.

Some simple examples follow.

- Convert an input media file to a different format, by re-encoding media streams:

```
ffmpeg -i input.avi output.mp4

```

- Set the video bitrate of the output file to 64 kbit/s:

```
ffmpeg -i input.avi -b:v 64k -bufsize 64k output.mp4

```

- Force the frame rate of the output file to 24 fps:

```
ffmpeg -i input.avi -r 24 output.mp4

```

- Force the frame rate of the input file (valid for raw formats only) to 1 fps and the frame rate of the output file to 24 fps:

```
ffmpeg -r 1 -i input.m2v -r 24 output.mp4

```

The format option may be needed for raw input files.

## 3 Detailed description# TOC

ffmpeg builds a transcoding pipeline out of the components listed below. The program’s operation then consists of input data chunks flowing from the sources down the pipes towards the sinks, while being transformed by the components they encounter along the way.

The following kinds of components are available:

- Demuxers (short for "demultiplexers") read an input source in order to extract

- global properties such as metadata or chapters;

- list of input elementary streams and their properties

One demuxer instance is created for each -i option, and sends encoded packets to decoders or muxers.

In other literature, demuxers are sometimes called splitters, because their main function is splitting a file into elementary streams (though some files only contain one elementary stream).

A schematic representation of a demuxer looks like this:

```
┌──────────┬───────────────────────┐
│ demuxer  │                       │ packets for stream 0
╞══════════╡ elementary stream 0   ├──────────────────────►
│          │                       │
│  global  ├───────────────────────┤
│properties│                       │ packets for stream 1
│   and    │ elementary stream 1   ├──────────────────────►
│ metadata │                       │
│          ├───────────────────────┤
│          │                       │
│          │     ...........       │
│          │                       │
│          ├───────────────────────┤
│          │                       │ packets for stream N
│          │ elementary stream N   ├──────────────────────►
│          │                       │
└──────────┴───────────────────────┘
     ▲
     │
     │ read from file, network stream,
     │     grabbing device, etc.
     │

```

- Decoders receive encoded (compressed) packets for an audio, video, or subtitle elementary stream, and decode them into raw frames (arrays of pixels for video, PCM for audio). A decoder is typically associated with (and receives its input from) an elementary stream in a demuxer, but sometimes may also exist on its own (see Loopback decoders).
A schematic representation of a decoder looks like this:

```
          ┌─────────┐
 packets  │         │ raw frames
─────────►│ decoder ├────────────►
          │         │
          └─────────┘

```

- Filtergraphs process and transform raw audio or video frames. A filtergraph consists of one or more individual filters linked into a graph. Filtergraphs come in two flavors - simple and complex, configured with the -filter and -filter_complex options, respectively.
A simple filtergraph is associated with an output elementary stream; it receives the input to be filtered from a decoder and sends filtered output to that output stream’s encoder.

A simple video filtergraph that performs deinterlacing (using the yadif deinterlacer) followed by resizing (using the scale filter) can look like this:

```

             ┌────────────────────────┐
             │  simple filtergraph    │
 frames from ╞════════════════════════╡ frames for
 a decoder   │  ┌───────┐  ┌───────┐  │ an encoder
────────────►├─►│ yadif ├─►│ scale ├─►│────────────►
             │  └───────┘  └───────┘  │
             └────────────────────────┘

```

A complex filtergraph is standalone and not associated with any specific stream. It may have multiple (or zero) inputs, potentially of different types (audio or video), each of which receiving data either from a decoder or another complex filtergraph’s output. It also has one or more outputs that feed either an encoder or another complex filtergraph’s input.

The following example diagram represents a complex filtergraph with 3 inputs and 2 outputs (all video):

```
          ┌─────────────────────────────────────────────────┐
          │               complex filtergraph               │
          ╞═════════════════════════════════════════════════╡
 frames   ├───────┐  ┌─────────┐      ┌─────────┐  ┌────────┤ frames
─────────►│input 0├─►│ overlay ├─────►│ overlay ├─►│output 0├────────►
          ├───────┘  │         │      │         │  └────────┤
 frames   ├───────┐╭►│         │    ╭►│         │           │
─────────►│input 1├╯ └─────────┘    │ └─────────┘           │
          ├───────┘                 │                       │
 frames   ├───────┐ ┌─────┐ ┌─────┬─╯              ┌────────┤ frames
─────────►│input 2├►│scale├►│split├───────────────►│output 1├────────►
          ├───────┘ └─────┘ └─────┘                └────────┤
          └─────────────────────────────────────────────────┘

```

Frames from second input are overlaid over those from the first. Frames from the third input are rescaled, then the duplicated into two identical streams. One of them is overlaid over the combined first two inputs, with the result exposed as the filtergraph’s first output. The other duplicate ends up being the filtergraph’s second output.

- Encoders receive raw audio, video, or subtitle frames and encode them into encoded packets. The encoding (compression) process is typically lossy - it degrades stream quality to make the output smaller; some encoders are lossless, but at the cost of much higher output size. A video or audio encoder receives its input from some filtergraph’s output, subtitle encoders receive input from a decoder (since subtitle filtering is not supported yet). Every encoder is associated with some muxer’s output elementary stream and sends its output to that muxer.
A schematic representation of an encoder looks like this:

```
             ┌─────────┐
 raw frames  │         │ packets
────────────►│ encoder ├─────────►
             │         │
             └─────────┘

```

- Muxers (short for "multiplexers") receive encoded packets for their elementary streams from encoders (the transcoding path) or directly from demuxers (the streamcopy path), interleave them (when there is more than one elementary stream), and write the resulting bytes into the output file (or pipe, network stream, etc.).
A schematic representation of a muxer looks like this:

```
                       ┌──────────────────────┬───────────┐
 packets for stream 0  │                      │   muxer   │
──────────────────────►│  elementary stream 0 ╞═══════════╡
                       │                      │           │
                       ├──────────────────────┤  global   │
 packets for stream 1  │                      │properties │
──────────────────────►│  elementary stream 1 │   and     │
                       │                      │ metadata  │
                       ├──────────────────────┤           │
                       │                      │           │
                       │     ...........      │           │
                       │                      │           │
                       ├──────────────────────┤           │
 packets for stream N  │                      │           │
──────────────────────►│  elementary stream N │           │
                       │                      │           │
                       └──────────────────────┴─────┬─────┘
                                                    │
                     write to file, network stream, │
                         grabbing device, etc.      │
                                                    │
                                                    ▼

```

### 3.1 Streamcopy# TOC

The simplest pipeline in ffmpeg is single-stream streamcopy, that is copying one input elementary stream’s packets without decoding, filtering, or encoding them. As an example, consider an input file called INPUT.mkv with 3 elementary streams, from which we take the second and write it to file OUTPUT.mp4. A schematic representation of such a pipeline looks like this:

```
┌──────────┬─────────────────────┐
│ demuxer  │                     │ unused
╞══════════╡ elementary stream 0 ├────────╳
│          │                     │
│INPUT.mkv ├─────────────────────┤          ┌──────────────────────┬───────────┐
│          │                     │ packets  │                      │   muxer   │
│          │ elementary stream 1 ├─────────►│  elementary stream 0 ╞═══════════╡
│          │                     │          │                      │OUTPUT.mp4 │
│          ├─────────────────────┤          └──────────────────────┴───────────┘
│          │                     │ unused
│          │ elementary stream 2 ├────────╳
│          │                     │
└──────────┴─────────────────────┘

```

The above pipeline can be constructed with the following commandline:

```
ffmpeg -i INPUT.mkv -map 0:1 -c copy OUTPUT.mp4

```

In this commandline

- there is a single input INPUT.mkv;

- there are no input options for this input;

- there is a single output OUTPUT.mp4;

- there are two output options for this output:

- -map 0:1 selects the input stream to be used - from input with index 0 (i.e. the first one) the stream with index 1 (i.e. the second one);

- -c copy selects the copy encoder, i.e. streamcopy with no decoding or encoding.

Streamcopy is useful for changing the elementary stream count, container format, or modifying container-level metadata. Since there is no decoding or encoding, it is very fast and there is no quality loss. However, it might not work in some cases because of a variety of factors (e.g. certain information required by the target container is not available in the source). Applying filters is obviously also impossible, since filters work on decoded frames.

More complex streamcopy scenarios can be constructed - e.g. combining streams from two input files into a single output:

```
┌──────────┬────────────────────┐         ┌────────────────────┬───────────┐
│ demuxer 0│                    │ packets │                    │   muxer   │
╞══════════╡elementary stream 0 ├────────►│elementary stream 0 ╞═══════════╡
│INPUT0.mkv│                    │         │                    │OUTPUT.mp4 │
└──────────┴────────────────────┘         ├────────────────────┤           │
┌──────────┬────────────────────┐         │                    │           │
│ demuxer 1│                    │ packets │elementary stream 1 │           │
╞══════════╡elementary stream 0 ├────────►│                    │           │
│INPUT1.aac│                    │         └────────────────────┴───────────┘
└──────────┴────────────────────┘

```

that can be built by the commandline

```
ffmpeg -i INPUT0.mkv -i INPUT1.aac -map 0:0 -map 1:0 -c copy OUTPUT.mp4

```

The output -map option is used twice here, creating two streams in the output file - one fed by the first input and one by the second. The single instance of the -c option selects streamcopy for both of those streams. You could also use multiple instances of this option together with Stream specifiers to apply different values to each stream, as will be demonstrated in following sections.

A converse scenario is splitting multiple streams from a single input into multiple outputs:

```
┌──────────┬─────────────────────┐          ┌───────────────────┬───────────┐
│ demuxer  │                     │ packets  │                   │ muxer 0   │
╞══════════╡ elementary stream 0 ├─────────►│elementary stream 0╞═══════════╡
│          │                     │          │                   │OUTPUT0.mp4│
│INPUT.mkv ├─────────────────────┤          └───────────────────┴───────────┘
│          │                     │ packets  ┌───────────────────┬───────────┐
│          │ elementary stream 1 ├─────────►│                   │ muxer 1   │
│          │                     │          │elementary stream 0╞═══════════╡
└──────────┴─────────────────────┘          │                   │OUTPUT1.mp4│
                                            └───────────────────┴───────────┘

```

built with

```
ffmpeg -i INPUT.mkv -map 0:0 -c copy OUTPUT0.mp4 -map 0:1 -c copy OUTPUT1.mp4

```

Note how a separate instance of the -c option is needed for every output file even though their values are the same. This is because non-global options (which is most of them) only apply in the context of the file before which they are placed.

These examples can of course be further generalized into arbitrary remappings of any number of inputs into any number of outputs.

### 3.2 Transcoding# TOC

Transcoding is the process of decoding a stream and then encoding it again. Since encoding tends to be computationally expensive and in most cases degrades the stream quality (i.e. it is lossy), you should only transcode when you need to and perform streamcopy otherwise. Typical reasons to transcode are:

- applying filters - e.g. resizing, deinterlacing, or overlaying video; resampling or mixing audio;

- you want to feed the stream to something that cannot decode the original codec.

Note that ffmpeg will transcode all audio, video, and subtitle streams unless you specify -c copy for them.

Consider an example pipeline that reads an input file with one audio and one video stream, transcodes the video and copies the audio into a single output file. This can be schematically represented as follows

```
┌──────────┬─────────────────────┐
│ demuxer  │                     │       audio packets
╞══════════╡ stream 0 (audio)    ├─────────────────────────────────────╮
│          │                     │                                     │
│INPUT.mkv ├─────────────────────┤ video    ┌─────────┐     raw        │
│          │                     │ packets  │  video  │ video frames   │
│          │ stream 1 (video)    ├─────────►│ decoder ├──────────────╮ │
│          │                     │          │         │              │ │
└──────────┴─────────────────────┘          └─────────┘              │ │
                                                                     ▼ ▼
                                                                     │ │
┌──────────┬─────────────────────┐ video    ┌─────────┐              │ │
│ muxer    │                     │ packets  │  video  │              │ │
╞══════════╡ stream 0 (video)    │◄─────────┤ encoder ├──────────────╯ │
│          │                     │          │(libx264)│                │
│OUTPUT.mp4├─────────────────────┤          └─────────┘                │
│          │                     │                                     │
│          │ stream 1 (audio)    │◄────────────────────────────────────╯
│          │                     │
└──────────┴─────────────────────┘

```

and implemented with the following commandline:

```
ffmpeg -i INPUT.mkv -map 0:v -map 0:a -c:v libx264 -c:a copy OUTPUT.mp4

```

Note how it uses stream specifiers :v and :a to select input streams and apply different values of the -c option to them; see the Stream specifiers section for more details.

### 3.3 Filtering# TOC

When transcoding, audio and video streams can be filtered before encoding, with either a simple or complex filtergraph.

#### 3.3.1 Simple filtergraphs# TOC

Simple filtergraphs are those that have exactly one input and output, both of the same type (audio or video). They are configured with the per-stream -filter option (with -vf and -af aliases for -filter:v (video) and -filter:a (audio) respectively). Note that simple filtergraphs are tied to their output stream, so e.g. if you have multiple audio streams, -af will create a separate filtergraph for each one.

Taking the transcoding example from above, adding filtering (and omitting audio, for clarity) makes it look like this:

```
┌──────────┬───────────────┐
│ demuxer  │               │          ┌─────────┐
╞══════════╡ video stream  │ packets  │  video  │ frames
│INPUT.mkv │               ├─────────►│ decoder ├─────►───╮
│          │               │          └─────────┘         │
└──────────┴───────────────┘                              │
                                  ╭───────────◄───────────╯
                                  │   ┌────────────────────────┐
                                  │   │  simple filtergraph    │
                                  │   ╞════════════════════════╡
                                  │   │  ┌───────┐  ┌───────┐  │
                                  ╰──►├─►│ yadif ├─►│ scale ├─►├╮
                                      │  └───────┘  └───────┘  ││
                                      └────────────────────────┘│
                                                                │
                                                                │
┌──────────┬───────────────┐ video    ┌─────────┐               │
│ muxer    │               │ packets  │  video  │               │
╞══════════╡ video stream  │◄─────────┤ encoder ├───────◄───────╯
│OUTPUT.mp4│               │          │         │
│          │               │          └─────────┘
└──────────┴───────────────┘

```

#### 3.3.2 Complex filtergraphs# TOC

Complex filtergraphs are those which cannot be described as simply a linear processing chain applied to one stream. This is the case, for example, when the graph has more than one input and/or output, or when output stream type is different from input. Complex filtergraphs are configured with the -filter_complex option. Note that this option is global, since a complex filtergraph, by its nature, cannot be unambiguously associated with a single stream or file. Each instance of -filter_complex creates a new complex filtergraph, and there can be any number of them.

A trivial example of a complex filtergraph is the overlay filter, which has two video inputs and one video output, containing one video overlaid on top of the other. Its audio counterpart is the amix filter.

### 3.4 Loopback decoders# TOC

While decoders are normally associated with demuxer streams, it is also possible to create "loopback" decoders that decode the output from some encoder and allow it to be fed back to complex filtergraphs. This is done with the -dec directive, which takes as a parameter output_file_index:stream_index to select the output stream that should be decoded. Both indices are zero-based integers: the first identifies the output file and the second identifies the stream within that file. Stream specifiers such as v:0 are not supported. Every such directive creates a new loopback decoder, indexed with successive integers starting at zero. These indices should then be used to refer to loopback decoders in complex filtergraph link labels, as described in the documentation for -filter_complex.

Decoding AVOptions can be passed to loopback decoders by placing them before -dec, analogously to input/output options.

E.g. the following example:

```
ffmpeg -i INPUT                                        \
  -map 0:v:0 -c:v libx264 -crf 45 -f null -            \
  -threads 3 -dec 0:0                                  \
  -filter_complex '[0:v][dec:0]hstack[stack]'          \
  -map '[stack]' -c:v ffv1 OUTPUT

```

reads an input video and

- (line 2) encodes it with libx264 at low quality;

- (line 3) decodes this encoded stream using 3 threads;

- (line 4) places decoded video side by side with the original input video;

- (line 5) combined video is then losslessly encoded and written into OUTPUT.

Such a transcoding pipeline can be represented with the following diagram:

```
┌──────────┬───────────────┐
│ demuxer  │               │   ┌─────────┐            ┌─────────┐    ┌────────────────────┐
╞══════════╡ video stream  │   │  video  │            │  video  │    │ null muxer         │
│   INPUT  │               ├──►│ decoder ├──┬────────►│ encoder ├─┬─►│(discards its input)│
│          │               │   └─────────┘  │         │(libx264)│ │  └────────────────────┘
└──────────┴───────────────┘                │         └─────────┘ │
                                 ╭───────◄──╯   ┌─────────┐       │
                                 │              │loopback │       │
                                 │ ╭─────◄──────┤ decoder ├────◄──╯
                                 │ │            └─────────┘
                                 │ │
                                 │ │
                                 │ │  ┌───────────────────┐
                                 │ │  │complex filtergraph│
                                 │ │  ╞═══════════════════╡
                                 │ │  │  ┌─────────────┐  │
                                 ╰─╫─►├─►│   hstack    ├─►├╮
                                   ╰─►├─►│             │  ││
                                      │  └─────────────┘  ││
                                      └───────────────────┘│
                                                           │
┌──────────┬───────────────┐  ┌─────────┐                  │
│ muxer    │               │  │  video  │                  │
╞══════════╡ video stream  │◄─┤ encoder ├───────◄──────────╯
│  OUTPUT  │               │  │ (ffv1)  │
│          │               │  └─────────┘
└──────────┴───────────────┘

```

## 4 Stream selection# TOC

ffmpeg provides the -map option for manual control of stream selection in each output file. Users can skip -map and let ffmpeg perform automatic stream selection as described below. The -vn / -an / -sn / -dn options can be used to skip inclusion of video, audio, subtitle and data streams respectively, whether manually mapped or automatically selected, except for those streams which are outputs of complex filtergraphs.

### 4.1 Description# TOC

The sub-sections that follow describe the various rules that are involved in stream selection. The examples that follow next show how these rules are applied in practice.

While every effort is made to accurately reflect the behavior of the program, FFmpeg is under continuous development and the code may have changed since the time of this writing.

#### 4.1.1 Automatic stream selection# TOC

In the absence of any map options for a particular output file, ffmpeg inspects the output format to check which type of streams can be included in it, viz. video, audio and/or subtitles. For each acceptable stream type, ffmpeg will pick one stream, when available, from among all the inputs.

It will select that stream based upon the following criteria:

- for video, it is the stream with the highest resolution,

- for audio, it is the stream with the most channels,

- for subtitles, it is the first subtitle stream found but there’s a caveat. The output format’s default subtitle encoder can be either text-based or image-based, and only a subtitle stream of the same type will be chosen.

In the case where several streams of the same type rate equally, the stream with the lowest index is chosen.

Data or attachment streams are not automatically selected and can only be included using -map.

#### 4.1.2 Manual stream selection# TOC

When -map is used, only user-mapped streams are included in that output file, with one possible exception for filtergraph outputs described below.

#### 4.1.3 Complex filtergraphs# TOC

If there are any complex filtergraph output streams with unlabeled pads, they will be added to the first output file. This will lead to a fatal error if the stream type is not supported by the output format. In the absence of the map option, the inclusion of these streams leads to the automatic stream selection of their types being skipped. If map options are present, these filtergraph streams are included in addition to the mapped streams.

Complex filtergraph output streams with labeled pads must be mapped once and exactly once.

#### 4.1.4 Stream handling# TOC

Stream handling is independent of stream selection, with an exception for subtitles described below. Stream handling is set via the -codec option addressed to streams within a specific output file. In particular, codec options are applied by ffmpeg after the stream selection process and thus do not influence the latter. If no -codec option is specified for a stream type, ffmpeg will select the default encoder registered by the output file muxer.

An exception exists for subtitles. If a subtitle encoder is specified for an output file, the first subtitle stream found of any type, text or image, will be included. ffmpeg does not validate if the specified encoder can convert the selected stream or if the converted stream is acceptable within the output format. This applies generally as well: when the user sets an encoder manually, the stream selection process cannot check if the encoded stream can be muxed into the output file. If it cannot, ffmpeg will abort and all output files will fail to be processed.

### 4.2 Examples# TOC

The following examples illustrate the behavior, quirks and limitations of ffmpeg’s stream selection methods.

They assume the following three input files.

```

input file 'A.avi'
      stream 0: video 640x360
      stream 1: audio 2 channels

input file 'B.mp4'
      stream 0: video 1920x1080
      stream 1: audio 2 channels
      stream 2: subtitles (text)
      stream 3: audio 5.1 channels
      stream 4: subtitles (text)

input file 'C.mkv'
      stream 0: video 1280x720
      stream 1: audio 2 channels
      stream 2: subtitles (image)

```

```
ffmpeg -i A.avi -i B.mp4 out1.mkv out2.wav -map 1:a -c:a copy out3.mov

```

There are three output files specified, and for the first two, no -map options are set, so ffmpeg will select streams for these two files automatically.

out1.mkv is a Matroska container file and accepts video, audio and subtitle streams, so ffmpeg will try to select one of each type.
 For video, it will select stream 0 from B.mp4, which has the highest resolution among all the input video streams.
 For audio, it will select stream 3 from B.mp4, since it has the greatest number of channels.
 For subtitles, it will select stream 2 from B.mp4, which is the first subtitle stream from among A.avi and B.mp4.

out2.wav accepts only audio streams, so only stream 3 from B.mp4 is selected.

For out3.mov, since a -map option is set, no automatic stream selection will occur. The -map 1:a option will select all audio streams from the second input B.mp4. No other streams will be included in this output file.

For the first two outputs, all included streams will be transcoded. The encoders chosen will be the default ones registered by each output format, which may not match the codec of the selected input streams.

For the third output, codec option for audio streams has been set to copy, so no decoding-filtering-encoding operations will occur, or can occur. Packets of selected streams shall be conveyed from the input file and muxed within the output file.

```
ffmpeg -i C.mkv out1.mkv -c:s dvdsub -an out2.mkv

```

Although out1.mkv is a Matroska container file which accepts subtitle streams, only a video and audio stream shall be selected. The subtitle stream of C.mkv is image-based and the default subtitle encoder of the Matroska muxer is text-based, so a transcode operation for the subtitles is expected to fail and hence the stream isn’t selected. However, in out2.mkv, a subtitle encoder is specified in the command and so, the subtitle stream is selected, in addition to the video stream. The presence of -an disables audio stream selection for out2.mkv.

```
ffmpeg -i A.avi -i C.mkv -i B.mp4 -filter_complex "overlay" out1.mp4 out2.srt

```

A filtergraph is setup here using the -filter_complex option and consists of a single video filter. The overlay filter requires exactly two video inputs, but none are specified, so the first two available video streams are used, those of A.avi and C.mkv. The output pad of the filter has no label and so is sent to the first output file out1.mp4. Due to this, automatic selection of the video stream is skipped, which would have selected the stream in B.mp4. The audio stream with most channels viz. stream 3 in B.mp4, is chosen automatically. No subtitle stream is chosen however, since the MP4 format has no default subtitle encoder registered, and the user hasn’t specified a subtitle encoder.

The 2nd output file, out2.srt, only accepts text-based subtitle streams. So, even though the first subtitle stream available belongs to C.mkv, it is image-based and hence skipped. The selected stream, stream 2 in B.mp4, is the first text-based subtitle stream.

```
ffmpeg -i A.avi -i B.mp4 -i C.mkv -filter_complex "[1:v]hue=s=0[outv];overlay;aresample" \
       -map '[outv]' -an        out1.mp4 \
                                out2.mkv \
       -map '[outv]' -map 1:a:0 out3.mkv

```

The above command will fail, as the output pad labelled [outv] has been mapped twice. None of the output files shall be processed.

```
ffmpeg -i A.avi -i B.mp4 -i C.mkv -filter_complex "[1:v]hue=s=0[outv];overlay;aresample" \
       -an        out1.mp4 \
                  out2.mkv \
       -map 1:a:0 out3.mkv

```

This command above will also fail as the hue filter output has a label, [outv], and hasn’t been mapped anywhere.

The command should be modified as follows,

```
ffmpeg -i A.avi -i B.mp4 -i C.mkv -filter_complex "[1:v]hue=s=0,split=2[outv1][outv2];overlay;aresample" \
        -map '[outv1]' -an        out1.mp4 \
                                  out2.mkv \
        -map '[outv2]' -map 1:a:0 out3.mkv

```

The video stream from B.mp4 is sent to the hue filter, whose output is cloned once using the split filter, and both outputs labelled. Then a copy each is mapped to the first and third output files.

The overlay filter, requiring two video inputs, uses the first two unused video streams. Those are the streams from A.avi and C.mkv. The overlay output isn’t labelled, so it is sent to the first output file out1.mp4, regardless of the presence of the -map option.

The aresample filter is sent the first unused audio stream, that of A.avi. Since this filter output is also unlabelled, it too is mapped to the first output file. The presence of -an only suppresses automatic or manual stream selection of audio streams, not outputs sent from filtergraphs. Both these mapped streams shall be ordered before the mapped stream in out1.mp4.

The video, audio and subtitle streams mapped to out2.mkv are entirely determined by automatic stream selection.

out3.mkv consists of the cloned video output from the hue filter and the first audio stream from B.mp4.

## 5 Options# TOC

All the numerical options, if not specified otherwise, accept a string representing a number as input, which may be followed by one of the SI unit prefixes, for example: ’K’, ’M’, or ’G’.

If ’i’ is appended to the SI unit prefix, the complete prefix will be interpreted as a unit prefix for binary multiples, which are based on powers of 1024 instead of powers of 1000. Appending ’B’ to the SI unit prefix multiplies the value by 8. This allows using, for example: ’KB’, ’MiB’, ’G’ and ’B’ as number suffixes.

Options which do not take arguments are boolean options, and set the corresponding value to true. They can be set to false by prefixing the option name with "no". For example using "-nofoo" will set the boolean option with name "foo" to false.

Options that take arguments support a special syntax where the argument given on the command line is interpreted as a path to the file from which the actual argument value is loaded. To use this feature, add a forward slash ’/’ immediately before the option name (after the leading dash). E.g.

```
ffmpeg -i INPUT -/filter:v filter.script OUTPUT

```

will load a filtergraph description from the file named filter.script.

### 5.1 Stream specifiers# TOC

Some options are applied per-stream, e.g. bitrate or codec. Stream specifiers are used to precisely specify which stream(s) a given option belongs to.

A stream specifier is a string generally appended to the option name and separated from it by a colon. E.g. -codec:a:1 ac3 contains the a:1 stream specifier, which matches the second audio stream. Therefore, it would select the ac3 codec for the second audio stream.

A stream specifier can match several streams, so that the option is applied to all of them. E.g. the stream specifier in -b:a 128k matches all audio streams.

An empty stream specifier matches all streams. For example, -codec copy or -codec: copy would copy all the streams without reencoding.

Possible forms of stream specifiers are:

stream_index

Matches the stream with this index. E.g. -threads:1 4 would set the thread count for the second stream to 4. If stream_index is used as an additional stream specifier (see below), then it selects stream number stream_index from the matching streams. Stream numbering is based on the order of the streams as detected by libavformat except when a stream group specifier or program ID is also specified. In this case it is based on the ordering of the streams in the group or program.

stream_type[:additional_stream_specifier]

stream_type is one of following: ’v’ or ’V’ for video, ’a’ for audio, ’s’ for subtitle, ’d’ for data, and ’t’ for attachments. ’v’ matches all video streams, ’V’ only matches video streams which are not attached pictures, video thumbnails or cover arts. If additional_stream_specifier is used, then it matches streams which both have this type and match the additional_stream_specifier. Otherwise, it matches all streams of the specified type.

g:group_specifier[:additional_stream_specifier]

Matches streams which are in the group with the specifier group_specifier. if additional_stream_specifier is used, then it matches streams which both are part of the group and match the additional_stream_specifier. group_specifier may be one of the following:

group_index

Match the stream with this group index.

#group_id or i:group_id

Match the stream with this group id.

p:program_id[:additional_stream_specifier]

Matches streams which are in the program with the id program_id. If additional_stream_specifier is used, then it matches streams which both are part of the program and match the additional_stream_specifier.

#stream_id or i:stream_id

Match the stream by stream id (e.g. PID in MPEG-TS container).

m:key[:value]

Matches streams with the metadata tag key having the specified value. If value is not given, matches streams that contain the given tag with any value. The colon character ’:’ in key or value needs to be backslash-escaped.

disp:dispositions[:additional_stream_specifier]

Matches streams with the given disposition(s). dispositions is a list of one or more dispositions (as printed by the -dispositions option) joined with ’+’.

u

Matches streams with usable configuration, the codec must be defined and the essential information such as video dimension or audio sample rate must be present.

Note that in ffmpeg, matching by metadata will only work properly for input files.

### 5.2 Generic options# TOC

These options are shared amongst the ff* tools.

-L, -license

Show license.

-h, -?, -help, --help [arg]

Show help. An optional parameter may be specified to print help about a specific item. If no argument is specified, only basic (non advanced) tool options are shown.

Possible values of arg are:

long

Print advanced tool options in addition to the basic tool options.

full

Print complete list of options, including shared and private options for encoders, decoders, demuxers, muxers, filters, etc.

decoder=decoder_name

Print detailed information about the decoder named decoder_name. Use the -decoders option to get a list of all decoders.

encoder=encoder_name

Print detailed information about the encoder named encoder_name. Use the -encoders option to get a list of all encoders.

demuxer=demuxer_name

Print detailed information about the demuxer named demuxer_name. Use the -formats option to get a list of all demuxers and muxers.

muxer=muxer_name

Print detailed information about the muxer named muxer_name. Use the -formats option to get a list of all muxers and demuxers.

filter=filter_name

Print detailed information about the filter named filter_name. Use the -filters option to get a list of all filters.

bsf=bitstream_filter_name

Print detailed information about the bitstream filter named bitstream_filter_name. Use the -bsfs option to get a list of all bitstream filters.

protocol=protocol_name

Print detailed information about the protocol named protocol_name. Use the -protocols option to get a list of all protocols.

-version

Show version.

-buildconf

Show the build configuration, one option per line.

-formats

Show available formats (including devices).

-demuxers

Show available demuxers.

-muxers

Show available muxers.

-devices

Show available devices.

-codecs

Show all codecs known to libavcodec.

Note that the term ’codec’ is used throughout this documentation as a shortcut for what is more correctly called a media bitstream format.

-decoders

Show available decoders.

-encoders

Show all available encoders.

-bsfs

Show available bitstream filters.

-protocols

Show available protocols.

-filters

Show available libavfilter filters.

-pix_fmts

Show available pixel formats.

-sample_fmts

Show available sample formats.

-layouts

Show channel names and standard channel layouts.

-dispositions

Show stream dispositions.

-colors

Show recognized color names.

-sources device[,opt1=val1[,opt2=val2]...]

Show autodetected sources of the input device. Some devices may provide system-dependent source names that cannot be autodetected. The returned list cannot be assumed to be always complete.

```
ffmpeg -sources pulse,server=192.168.0.4

```

-sinks device[,opt1=val1[,opt2=val2]...]

Show autodetected sinks of the output device. Some devices may provide system-dependent sink names that cannot be autodetected. The returned list cannot be assumed to be always complete.

```
ffmpeg -sinks pulse,server=192.168.0.4

```

-loglevel [flags+]loglevel | -v [flags+]loglevel

Set logging level and flags used by the library.

The optional flags prefix can consist of the following values:

‘repeat’

Indicates that repeated log output should not be compressed to the first line and the "Last message repeated n times" line will be omitted.

‘level’

Indicates that log output should add a [level] prefix to each message line. This can be used as an alternative to log coloring, e.g. when dumping the log to file.

‘time’

Indicates that log lines should be prefixed with time information.

‘datetime’

Indicates that log lines should be prefixed with date and time information.

Flags can also be used alone by adding a ’+’/’-’ prefix to set/reset a single flag without affecting other flags or changing loglevel. When setting both flags and loglevel, a ’+’ separator is expected between the last flags value and before loglevel.

loglevel is a string or a number containing one of the following values:

‘quiet, -8’

Show nothing at all; be silent.

‘panic, 0’

Only show fatal errors which could lead the process to crash, such as an assertion failure. This is not currently used for anything.

‘fatal, 8’

Only show fatal errors. These are errors after which the process absolutely cannot continue.

‘error, 16’

Show all errors, including ones which can be recovered from.

‘warning, 24’

Show all warnings and errors. Any message related to possibly incorrect or unexpected events will be shown.

‘info, 32’

Show informative messages during processing. This is in addition to warnings and errors. This is the default value.

‘verbose, 40’

Same as info, except more verbose.

‘debug, 48’

Show everything, including debugging information.

‘trace, 56’

For example to enable repeated log output, add the level prefix, and set loglevel to verbose:

```
ffmpeg -loglevel repeat+level+verbose -i input output

```

Another example that enables repeated log output without affecting current state of level prefix flag or loglevel:

```
ffmpeg [...] -loglevel +repeat

```

By default the program logs to stderr. If coloring is supported by the terminal, colors are used to mark errors and warnings. Log coloring can be disabled setting the environment variable AV_LOG_FORCE_NOCOLOR, or can be forced setting the environment variable AV_LOG_FORCE_COLOR.

-report

Dump full command line and log output to a file named program-YYYYMMDD-HHMMSS.log in the current directory. This file can be useful for bug reports. It also implies -loglevel debug.

Setting the environment variable FFREPORT to any value has the same effect. If the value is a ’:’-separated key=value sequence, these options will affect the report; option values must be escaped if they contain special characters or the options delimiter ’:’ (see the “Quoting and escaping” section in the ffmpeg-utils manual).

The following options are recognized:

file

set the file name to use for the report; %p is expanded to the name of the program, %t is expanded to a timestamp, %% is expanded to a plain %

level

set the log verbosity level using a numerical value (see -loglevel).

For example, to output a report to a file named ffreport.log using a log level of 32 (alias for log level info):

```
FFREPORT=file=ffreport.log:level=32 ffmpeg -i input output

```

Errors in parsing the environment variable are not fatal, and will not appear in the report.

-hide_banner

Suppress printing banner.

All FFmpeg tools will normally show a copyright notice, build options and library versions. This option can be used to suppress printing this information.

-cpuflags flags (global)

Allows setting and clearing cpu flags. This option is intended for testing. Do not use it unless you know what you’re doing.

```
ffmpeg -cpuflags -sse+mmx ...
ffmpeg -cpuflags mmx ...
ffmpeg -cpuflags 0 ...

```

Possible flags for this option are:

‘x86’

‘mmx’

‘mmxext’

‘sse’

‘sse2’

‘sse2slow’

‘sse3’

‘sse3slow’

‘ssse3’

‘atom’

‘sse4.1’

‘sse4.2’

‘avx’

‘avx2’

‘xop’

‘fma3’

‘fma4’

‘3dnow’

‘3dnowext’

‘bmi1’

‘bmi2’

‘cmov’

‘ARM’

‘armv5te’

‘armv6’

‘armv6t2’

‘vfp’

‘vfpv3’

‘neon’

‘setend’

‘AArch64’

‘armv8’

‘vfp’

‘neon’

‘PowerPC’

‘altivec’

‘Specific Processors’

‘pentium2’

‘pentium3’

‘pentium4’

‘k6’

‘k62’

‘athlon’

‘athlonxp’

‘k8’

-cpucount count (global)

Override detection of CPU count. This option is intended for testing. Do not use it unless you know what you’re doing.

```
ffmpeg -cpucount 2

```

-max_alloc bytes

Set the maximum size limit for allocating a block on the heap by ffmpeg’s family of malloc functions. Exercise extreme caution when using this option. Don’t use if you do not understand the full consequence of doing so. Default is INT_MAX.

### 5.3 AVOptions# TOC

These options are provided directly by the libavformat, libavdevice and libavcodec libraries. To see the list of available AVOptions, use the -help option. They are separated into two categories:

generic

These options can be set for any container, codec or device. Generic options are listed under AVFormatContext options for containers/devices and under AVCodecContext options for codecs.

private

These options are specific to the given container, device or codec. Private options are listed under their corresponding containers/devices/codecs.

For example to write an ID3v2.3 header instead of a default ID3v2.4 to an MP3 file, use the id3v2_version private option of the MP3 muxer:

```
ffmpeg -i input.flac -id3v2_version 3 out.mp3

```

All codec AVOptions are per-stream, and thus a stream specifier should be attached to them:

```
ffmpeg -i multichannel.mxf -map 0:v:0 -map 0:a:0 -map 0:a:0 -c:a:0 ac3 -b:a:0 640k -ac:a:1 2 -c:a:1 aac -b:2 128k out.mp4

```

In the above example, a multichannel audio stream is mapped twice for output. The first instance is encoded with codec ac3 and bitrate 640k. The second instance is downmixed to 2 channels and encoded with codec aac. A bitrate of 128k is specified for it using absolute index of the output stream.

Note: the -nooption syntax cannot be used for boolean AVOptions, use -option 0/-option 1.

Note: the old undocumented way of specifying per-stream AVOptions by prepending v/a/s to the options name is now obsolete and will be removed soon.

### 5.4 Main options# TOC

-f fmt (input/output)

Force input or output file format. The format is normally auto detected for input files and guessed from the file extension for output files, so this option is not needed in most cases.

-i url (input)

input file url

-y (global)

Overwrite output files without asking.

-n (global)

Do not overwrite output files, and exit immediately if a specified output file already exists.

-stream_loop number (input)

Set number of times input stream shall be looped. Loop 0 means no loop, loop -1 means infinite loop.

-recast_media (global)

Allow forcing a decoder of a different media type than the one detected or designated by the demuxer. Useful for decoding media data muxed as data streams.

-c[:stream_specifier] codec (input/output,per-stream)

-codec[:stream_specifier] codec (input/output,per-stream)

Select an encoder (when used before an output file) or a decoder (when used before an input file) for one or more streams. codec is the name of a decoder/encoder or a special value copy (output only) to indicate that the stream is not to be re-encoded.

For example

```
ffmpeg -i INPUT -map 0 -c:v libx264 -c:a copy OUTPUT

```

encodes all video streams with libx264 and copies all audio streams.

For each stream, the last matching c option is applied, so

```
ffmpeg -i INPUT -map 0 -c copy -c:v:1 libx264 -c:a:137 libvorbis OUTPUT

```

will copy all the streams except the second video, which will be encoded with libx264, and the 138th audio, which will be encoded with libvorbis.

-t duration (input/output)

When used as an input option (before -i), limit the duration of data read from the input file.

When used as an output option (before an output url), stop writing the output after its duration reaches duration.

duration must be a time duration specification, see the Time duration section in the ffmpeg-utils(1) manual.

-to and -t are mutually exclusive and -t has priority.

-to position (input/output)

Stop writing the output or reading the input at position. position must be a time duration specification, see the Time duration section in the ffmpeg-utils(1) manual.

-to and -t are mutually exclusive and -t has priority.

-fs limit_size (output)

Set the file size limit, expressed in bytes. No further chunk of bytes is written after the limit is exceeded. The size of the output file is slightly more than the requested file size.

-ss position (input/output)

When used as an input option (before -i), seeks in this input file to position. Note that in most formats it is not possible to seek exactly, so ffmpeg will seek to the closest seek point before position. When transcoding and -accurate_seek is enabled (the default), this extra segment between the seek point and position will be decoded and discarded. When doing stream copy or when -noaccurate_seek is used, it will be preserved.

When used as an output option (before an output url), decodes but discards input until the timestamps reach position.

position must be a time duration specification, see the Time duration section in the ffmpeg-utils(1) manual.

-sseof position (input)

Like the -ss option but relative to the "end of file". That is negative values are earlier in the file, 0 is at EOF.

-isync input_index (input)

Assign an input as a sync source.

This will take the difference between the start times of the target and reference inputs and offset the timestamps of the target file by that difference. The source timestamps of the two inputs should derive from the same clock source for expected results. If copyts is set then start_at_zero must also be set. If either of the inputs has no starting timestamp then no sync adjustment is made.

Acceptable values are those that refer to a valid ffmpeg input index. If the sync reference is the target index itself or -1, then no adjustment is made to target timestamps. A sync reference may not itself be synced to any other input.

Default value is -1.

-itsoffset offset (input)

Set the input time offset.

offset must be a time duration specification, see the Time duration section in the ffmpeg-utils(1) manual.

The offset is added to the timestamps of the input files. Specifying a positive offset means that the corresponding streams are delayed by the time duration specified in offset.

-itsscale scale (input,per-stream)

Rescale input timestamps. scale should be a floating point number.

-timestamp date (output)

Set the recording timestamp in the container.

date must be a date specification, see the Date section in the ffmpeg-utils(1) manual.

-metadata[:metadata_specifier] key=value (output,per-metadata)

Set a metadata key/value pair.

An optional metadata_specifier may be given to set metadata on streams, chapters or programs. See -map_metadata documentation for details.

This option overrides metadata set with -map_metadata. It is also possible to delete metadata by using an empty value.

For example, for setting the title in the output file:

```
ffmpeg -i in.avi -metadata title="my title" out.flv

```

To set the language of the first audio stream:

```
ffmpeg -i INPUT -metadata:s:a:0 language=eng OUTPUT

```

-keep_metadata[:metadata_specifier] key (output,per-metadata)

When re-encoding a stream, certain metadata keys that are likely to become stale (such as iTunSMPB or encoded_by) are automatically discarded. This option prevents a specific key from being discarded, preserving its original value from the input.

Without a specifier, the key is preserved in all metadata contexts (format and streams). Use g to restrict to format (global) metadata, or s with an optional stream specifier to restrict to matching streams only.

For example, to keep iTunSMPB in format metadata only when re-encoding:

```
ffmpeg -i in.mp3 -keep_metadata:g iTunSMPB out.mp3

```

To keep NUMBER_OF_BYTES only for the video stream:

```
ffmpeg -i in.mkv -keep_metadata:s:v NUMBER_OF_BYTES out.mkv

```

Some keys are stored in the metadata with a suffix (e.g. NUMBER_OF_BYTES-eng). Specifying the unsuffixed family name (e.g. NUMBER_OF_BYTES) keeps all variants. To keep only a specific one, specify the full key explicitly:

```
ffmpeg -i in.mkv -keep_metadata:s:v NUMBER_OF_BYTES-eng out.mkv

```

Some (such as major_brand, minor_version, and compatible_brands) are always removed regardless of re-encoding, because they describe the source container and are meaningless in the output. -keep_metadata applies to those keys even when stream-copying.

Re-encoding-only keys (such as encoder tags and Matroska stream statistics) are removed from a stream’s metadata only when that stream is being re-encoded, and from format metadata only when at least one audio or video stream is re-encoded.

Only format and stream metadata are filtered. Chapter and program metadata are never modified by this mechanism.

-disposition[:stream_specifier] value (output,per-stream)

Sets the disposition flags for a stream.

Default value: by default, all disposition flags are copied from the input stream, unless the output stream this option applies to is fed by a complex filtergraph - in that case no disposition flags are set by default.

value is a sequence of disposition flags separated by ’+’ or ’-’. A ’+’ prefix adds the given disposition, ’-’ removes it. If the first flag is also prefixed with ’+’ or ’-’, the resulting disposition is the default value updated by value. If the first flag is not prefixed, the resulting disposition is value. It is also possible to clear the disposition by setting it to 0.

If no -disposition options were specified for an output file, ffmpeg will automatically set the ’default’ disposition flag on the first stream of each type, when there are multiple streams of this type in the output file and no stream of that type is already marked as default.

The -dispositions option lists the known disposition flags.

For example, to make the second audio stream the default stream:

```
ffmpeg -i in.mkv -c copy -disposition:a:1 default out.mkv

```

To make the second subtitle stream the default stream and remove the default disposition from the first subtitle stream:

```
ffmpeg -i in.mkv -c copy -disposition:s:0 0 -disposition:s:1 default out.mkv

```

To add an embedded cover/thumbnail:

```
ffmpeg -i in.mp4 -i IMAGE -map 0 -map 1 -c copy -c:v:1 png -disposition:v:1 attached_pic out.mp4

```

To add the ’original’ and remove the ’comment’ disposition flag from the first audio stream without removing its other disposition flags:

```
ffmpeg -i in.mkv -c copy -disposition:a:0 +original-comment out.mkv

```

To remove the ’original’ and add the ’comment’ disposition flag to the first audio stream without removing its other disposition flags:

```
ffmpeg -i in.mkv -c copy -disposition:a:0 -original+comment out.mkv

```

To set only the ’original’ and ’comment’ disposition flags on the first audio stream (and remove its other disposition flags):

```
ffmpeg -i in.mkv -c copy -disposition:a:0 original+comment out.mkv

```

To remove all disposition flags from the first audio stream:

```
ffmpeg -i in.mkv -c copy -disposition:a:0 0 out.mkv

```

Not all muxers support embedded thumbnails, and those who do, only support a few formats, like JPEG or PNG.

-program [title=title:][program_num=program_num:]st=stream[:st=stream...] (output)

Creates a program with the specified title, program_num and adds the specified stream(s) to it.

-stream_group [map=input_file_id=stream_group][type=type:]st=stream[:st=stream][:stg=stream_group][:id=stream_group_id...] (output)

Creates a stream group of the specified type and stream_group_id, or by mapping an input group, adding the specified stream(s) and/or previously defined stream_group(s) to it.

type can be one of the following:

iamf_audio_element

Groups streams that belong to the same IAMF Audio Element

For this group type, the following options are available

audio_element_type

The Audio Element type. The following values are supported:

channel

Scalable channel audio representation

scene

Ambisonics representation

demixing

Demixing information used to reconstruct a scalable channel audio representation. This option must be separated from the rest with a ’,’, and takes the following key=value options

parameter_id

An identifier parameters blocks in frames may refer to

dmixp_mode

A pre-defined combination of demixing parameters

recon_gain

Recon gain information used to reconstruct a scalable channel audio representation. This option must be separated from the rest with a ’,’, and takes the following key=value options

parameter_id

An identifier parameters blocks in frames may refer to

layer

A layer defining a Channel Layout in the Audio Element. This option must be separated from the rest with a ’,’. Several ’,’ separated entries can be defined, and at least one must be set.

It takes the following ":"-separated key=value options

ch_layout

The layer’s channel layout

flags

The following flags are available:

recon_gain

Whether to signal if recon_gain is present as metadata in parameter blocks within frames

output_gain

output_gain_flags

Which channels output_gain applies to. The following flags are available:

FL

FR

BL

BR

TFL

TFR

ambisonics_mode

The ambisonics mode. This has no effect if audio_element_type is set to channel.

The following values are supported:

mono

Each ambisonics channel is coded as an individual mono stream in the group

default_w

Default weight value

iamf_mix_presentation

Groups streams that belong to all IAMF Audio Element the same IAMF Mix Presentation references

For this group type, the following options are available

submix

A sub-mix within the Mix Presentation. This option must be separated from the rest with a ’,’. Several ’,’ separated entries can be defined, and at least one must be set.

It takes the following ":"-separated key=value options

parameter_id

An identifier parameters blocks in frames may refer to, for post-processing the mixed audio signal to generate the audio signal for playback

parameter_rate

The sample rate duration fields in parameters blocks in frames that refer to this parameter_id are expressed as

default_mix_gain

Default mix gain value to apply when there are no parameter blocks sharing the same parameter_id for a given frame

element

References an Audio Element used in this Mix Presentation to generate the final output audio signal for playback. This option must be separated from the rest with a ’|’. Several ’|’ separated entries can be defined, and at least one must be set.

It takes the following ":"-separated key=value options:

stg

The stream_group_id for an Audio Element which this sub-mix refers to

parameter_id

An identifier parameters blocks in frames may refer to, for applying any processing to the referenced and rendered Audio Element before being summed with other processed Audio Elements

parameter_rate

The sample rate duration fields in parameters blocks in frames that refer to this parameter_id are expressed as

default_mix_gain

Default mix gain value to apply when there are no parameter blocks sharing the same parameter_id for a given frame

annotations

A key=value string describing the sub-mix element where "key" is a string conforming to BCP-47 that specifies the language for the "value" string. "key" must be the same as the one in the mix’s annotations

headphones_rendering_mode

Indicates whether the input channel-based Audio Element is rendered to stereo loudspeakers or spatialized with a binaural renderer when played back on headphones. This has no effect if the referenced Audio Element’s audio_element_type is set to channel.

The following values are supported:

stereo

binaural

layout

Specifies the layouts for this sub-mix on which the loudness information was measured. This option must be separated from the rest with a ’|’. Several ’|’ separated entries can be defined, and at least one must be set.

It takes the following ":"-separated key=value options:

layout_type

loudspeakers

The layout follows the loudspeaker sound system convention of ITU-2051-3.

binaural

The layout is binaural.

sound_system

Channel layout matching one of Sound Systems A to J of ITU-2051-3, plus 7.1.2 and 3.1.2 This has no effect if layout_type is set to binaural.

integrated_loudness

The program integrated loudness information, as defined in ITU-1770-4.

digital_peak

The digital (sampled) peak value of the audio signal, as defined in ITU-1770-4.

true_peak

The true peak of the audio signal, as defined in ITU-1770-4.

dialog_anchored_loudness

The Dialogue loudness information, as defined in ITU-1770-4.

album_anchored_loudness

The Album loudness information, as defined in ITU-1770-4.

annotations

A key=value string string describing the mix where "key" is a string conforming to BCP-47 that specifies the language for the "value" string. "key" must be the same as the ones in all sub-mix element’s annotationss

gain_map

Groups together a base stream with a gain map, which together form a pair of renditions (e.g. HDR and SDR) as per ISO 21496-1.

For this group type, the following options are available

el_index

Index of the gain map stream within the group. Defaults to 0.

video_size

Size of the final image for presentation.

E.g. to create an scalable 5.1 IAMF file from several WAV input files

```
ffmpeg -i front.wav -i back.wav -i center.wav -i lfe.wav
-map 0:0 -map 1:0 -map 2:0 -map 3:0 -c:a opus
-stream_group type=iamf_audio_element:id=1:st=0:st=1:st=2:st=3,
demixing=parameter_id=998,
recon_gain=parameter_id=101,
layer=ch_layout=stereo,
layer=ch_layout=5.1(side),
-stream_group type=iamf_mix_presentation:id=2:stg=0:annotations=en-us=Mix_Presentation,
submix=parameter_id=100:parameter_rate=48000|element=stg=0:parameter_id=100:annotations=en-us=Scalable_Submix|layout=sound_system=stereo|layout=sound_system=5.1(side)
-streamid 0:0 -streamid 1:1 -streamid 2:2 -streamid 3:3 output.iamf

```

To copy the two stream groups (Audio Element and Mix Presentation) from an input IAMF file with four streams into an mp4 output

```
ffmpeg -i input.iamf -c:a copy -stream_group map=0=0:st=0:st=1:st=2:st=3 -stream_group map=0=1:stg=0
-streamid 0:0 -streamid 1:1 -streamid 2:2 -streamid 3:3 output.mp4

```

-reinit_opts[:stream_specifier] pts=pts|key=value[:force_reinit=1][:key=value,pts=pts...] (output,per-stream)

Creates a "," separated group of options to reconfigure an encoder at the specified output pts in AV_TIME_BASE units. The pseudo-option force_reinit ensures the encoder is fully reinitialized instead of simply reconfigured.

-target type (output)

Specify target file type (vcd, svcd, dvd, dv, dv50). type may be prefixed with pal-, ntsc- or film- to use the corresponding standard. All the format options (bitrate, codecs, buffer sizes) are then set automatically. You can just type:

```
ffmpeg -i myfile.avi -target vcd /tmp/vcd.mpg

```

Nevertheless you can specify additional options as long as you know they do not conflict with the standard, as in:

```
ffmpeg -i myfile.avi -target vcd -bf 2 /tmp/vcd.mpg

```

The parameters set for each target are as follows.

VCD

```
pal:
-f vcd -muxrate 1411200 -muxpreload 0.44 -packetsize 2324
-s 352x288 -r 25
-codec:v mpeg1video -g 15 -b:v 1150k -maxrate:v 1150k -minrate:v 1150k -bufsize:v 327680
-ar 44100 -ac 2
-codec:a mp2 -b:a 224k

ntsc:
-f vcd -muxrate 1411200 -muxpreload 0.44 -packetsize 2324
-s 352x240 -r 30000/1001
-codec:v mpeg1video -g 18 -b:v 1150k -maxrate:v 1150k -minrate:v 1150k -bufsize:v 327680
-ar 44100 -ac 2
-codec:a mp2 -b:a 224k

film:
-f vcd -muxrate 1411200 -muxpreload 0.44 -packetsize 2324
-s 352x240 -r 24000/1001
-codec:v mpeg1video -g 18 -b:v 1150k -maxrate:v 1150k -minrate:v 1150k -bufsize:v 327680
-ar 44100 -ac 2
-codec:a mp2 -b:a 224k

```

SVCD

```
pal:
-f svcd -packetsize 2324
-s 480x576 -pix_fmt yuv420p -r 25
-codec:v mpeg2video -g 15 -b:v 2040k -maxrate:v 2516k -minrate:v 0 -bufsize:v 1835008 -scan_offset 1
-ar 44100
-codec:a mp2 -b:a 224k

ntsc:
-f svcd -packetsize 2324
-s 480x480 -pix_fmt yuv420p -r 30000/1001
-codec:v mpeg2video -g 18 -b:v 2040k -maxrate:v 2516k -minrate:v 0 -bufsize:v 1835008 -scan_offset 1
-ar 44100
-codec:a mp2 -b:a 224k

film:
-f svcd -packetsize 2324
-s 480x480 -pix_fmt yuv420p -r 24000/1001
-codec:v mpeg2video -g 18 -b:v 2040k -maxrate:v 2516k -minrate:v 0 -bufsize:v 1835008 -scan_offset 1
-ar 44100
-codec:a mp2 -b:a 224k

```

DVD

```
pal:
-f dvd -muxrate 10080k -packetsize 2048
-s 720x576 -pix_fmt yuv420p -r 25
-codec:v mpeg2video -g 15 -b:v 6000k -maxrate:v 9000k -minrate:v 0 -bufsize:v 1835008
-ar 48000
-codec:a ac3 -b:a 448k

ntsc:
-f dvd -muxrate 10080k -packetsize 2048
-s 720x480 -pix_fmt yuv420p -r 30000/1001
-codec:v mpeg2video -g 18 -b:v 6000k -maxrate:v 9000k -minrate:v 0 -bufsize:v 1835008
-ar 48000
-codec:a ac3 -b:a 448k

film:
-f dvd -muxrate 10080k -packetsize 2048
-s 720x480 -pix_fmt yuv420p -r 24000/1001
-codec:v mpeg2video -g 18 -b:v 6000k -maxrate:v 9000k -minrate:v 0 -bufsize:v 1835008
-ar 48000
-codec:a ac3 -b:a 448k

```

DV

```
pal:
-f dv
-s 720x576 -pix_fmt yuv420p -r 25
-ar 48000 -ac 2

ntsc:
-f dv
-s 720x480 -pix_fmt yuv411p -r 30000/1001
-ar 48000 -ac 2

film:
-f dv
-s 720x480 -pix_fmt yuv411p -r 24000/1001
-ar 48000 -ac 2

```

The dv50 target is identical to the dv target except that the pixel format set is yuv422p for all three standards.

Any user-set value for a parameter above will override the target preset value. In that case, the output may not comply with the target standard.

-dn (input/output)

As an input option, blocks all data streams of a file from being filtered or being automatically selected or mapped for any output. See -discard option to disable streams individually.

As an output option, disables data recording i.e. automatic selection or mapping of any data stream. For full manual control see the -map option.

-dframes number (output)

Set the number of data frames to output. This is an obsolete alias for -frames:d, which you should use instead.

-frames[:stream_specifier] framecount (output,per-stream)

Stop writing to the stream after framecount frames.

-q[:stream_specifier] q (output,per-stream)

-qscale[:stream_specifier] q (output,per-stream)

Use fixed quality scale (VBR). The meaning of q/qscale is codec-dependent. If qscale is used without a stream_specifier then it applies only to the video stream, this is to maintain compatibility with previous behavior and as specifying the same codec specific value to 2 different codecs that is audio and video generally is not what is intended when no stream_specifier is used.

-filter[:stream_specifier] filtergraph (output,per-stream)

Create the filtergraph specified by filtergraph and use it to filter the stream.

filtergraph is a description of the filtergraph to apply to the stream, and must have a single input and a single output of the same type of the stream. In the filtergraph, the input is associated to the label in, and the output to the label out. See the ffmpeg-filters manual for more information about the filtergraph syntax.

See the -filter_complex option if you want to create filtergraphs with multiple inputs and/or outputs.

-reinit_filter[:stream_specifier] integer (input,per-stream)

This boolean option determines if the filtergraph(s) to which this stream is fed gets reinitialized when input frame parameters change mid-stream. This option is enabled by default as most video and all audio filters cannot handle deviation in input frame properties. Upon reinitialization, existing filter state is lost, like e.g. the frame count n reference available in some filters. Any frames buffered at time of reinitialization are lost. The properties where a change triggers reinitialization are, for video, frame resolution or pixel format; for audio, sample format, sample rate, channel count or channel layout.

-drop_changed[:stream_specifier] integer (input,per-stream)

This boolean option determines whether a frame with differing frame parameters mid-stream gets dropped instead of leading to filtergraph reinitialization, as that would lead to loss of filter state. Generally useful to avoid corrupted yet decodable packets in live streaming inputs. Default is false.

-filter_threads nb_threads (global)

Defines how many threads are used to process a filter pipeline. Each pipeline will produce a thread pool with this many threads available for parallel processing. The default is the number of available CPUs.

-filter_buffered_frames[:media_type] nb_frames (global)

Defines the maximum number of buffered frames allowed in a filtergraph. Under normal circumstances, a filtergraph should not buffer more than a few frames, especially if frames are being fed to it and read from it in a balanced way (which is the intended behavior in ffmpeg). That said, this option allows you to limit the total number of frames buffered across all links in a filtergraph. If more frames are generated, filtering is aborted and an error is returned. The default value is 0, which means no limit.

The optional suffix media_type may be used to set a different limit for audio and video frames, using the suffixes a and v, respectively. If the suffix is omitted, the limit applies to both audio and video frames, separately.

-pre[:stream_specifier] preset_name (output,per-stream)

Specify the preset for matching stream(s).

-stats (global)

Log encoding progress/statistics as "info"-level log (see -loglevel). It is on by default, to explicitly disable it you need to specify -nostats.

-stats_period time (global)

Set period at which encoding progress/statistics are updated. Default is 0.5 seconds.

-print_graphs (global)

Prints execution graph details to stderr in the format set via -print_graphs_format.

-print_graphs_file filename (global)

Writes execution graph details to the specified file in the format set via -print_graphs_format.

-print_graphs_format format (global)

Sets the output format (available formats are: default, compact, csv, flat, ini, json, xml, mermaid, mermaidhtml) The default format is json.

-progress url (global)

Send program-friendly progress information to url.

Progress information is written periodically and at the end of the encoding process. It is made of "key=value" lines. key consists of only alphanumeric characters. The last key of a sequence of progress information is always "progress" with the value "continue" or "end".

The update period is set using -stats_period.

For example, log progress information to stdout:

```
ffmpeg -progress pipe:1 -i in.mkv out.mkv

```

-stdin

Enable interaction on standard input. On by default unless standard input is used as an input. To explicitly disable interaction you need to specify -nostdin.

Disabling interaction on standard input is useful, for example, if ffmpeg is in the background process group. Roughly the same result can be achieved with ffmpeg ... < /dev/null but it requires a shell.

-debug_ts (global)

Print timestamp/latency information. It is off by default. This option is mostly useful for testing and debugging purposes, and the output format may change from one version to another, so it should not be employed by portable scripts.

See also the option -fdebug ts.

-attach filename (output)

Add an attachment to the output file. This is supported by a few formats like Matroska for e.g. fonts used in rendering subtitles. Attachments are implemented as a specific type of stream, so this option will add a new stream to the file. It is then possible to use per-stream options on this stream in the usual way. Attachment streams created with this option will be created after all the other streams (i.e. those created with -map or automatic mappings).

Note that for Matroska you also have to set the mimetype metadata tag:

```
ffmpeg -i INPUT -attach DejaVuSans.ttf -metadata:s:2 mimetype=application/x-truetype-font out.mkv

```

(assuming that the attachment stream will be third in the output file).

-dump_attachment[:stream_specifier] filename (input,per-stream)

Extract the matching attachment stream into a file named filename. If filename is empty, then the value of the filename metadata tag will be used.

E.g. to extract the first attachment to a file named ’out.ttf’:

```
ffmpeg -dump_attachment:t:0 out.ttf -i INPUT

```

To extract all attachments to files determined by the filename tag:

```
ffmpeg -dump_attachment:t "" -i INPUT

```

Technical note – attachments are implemented as codec extradata, so this option can actually be used to extract extradata from any stream, not just attachments.

### 5.5 Video Options# TOC

-vframes number (output)

Set the number of video frames to output. This is an obsolete alias for -frames:v, which you should use instead.

-r[:stream_specifier] fps (input/output,per-stream)

Set frame rate (Hz value, fraction or abbreviation).

As an input option, ignore any timestamps stored in the file and instead generate timestamps assuming constant frame rate fps. This is not the same as the -framerate option used for some input formats like image2 or v4l2 (it used to be the same in older versions of FFmpeg). If in doubt use -framerate instead of the input option -r.

As an output option:

video encoding

Duplicate or drop frames right before encoding them to achieve constant output frame rate fps.

video streamcopy

Indicate to the muxer that fps is the stream frame rate. No data is dropped or duplicated in this case. This may produce invalid files if fps does not match the actual stream frame rate as determined by packet timestamps. See also the setts bitstream filter.

-fpsmax[:stream_specifier] fps (output,per-stream)

Set maximum frame rate (Hz value, fraction or abbreviation).

Clamps output frame rate when output framerate is auto-set and is higher than this value. Useful in batch processing or when input framerate is wrongly detected as very high. It cannot be set together with -r. It is ignored during streamcopy.

-s[:stream_specifier] size (input/output,per-stream)

Set frame size.

As an input option, this is a shortcut for the video_size private option, recognized by some demuxers for which the frame size is either not stored in the file or is configurable – e.g. raw video or video grabbers.

As an output option, this inserts the scale video filter to the end of the corresponding filtergraph. Please use the scale filter directly to insert it at the beginning or some other place.

The format is ‘wxh’ (default - same as source).

-aspect[:stream_specifier] aspect (output,per-stream)

Set the video display aspect ratio specified by aspect.

aspect can be a floating point number string, or a string of the form num:den, where num and den are the numerator and denominator of the aspect ratio. For example "4:3", "16:9", "1.3333", and "1.7777" are valid argument values.

If used together with -vcodec copy, it will affect the aspect ratio stored at container level, but not the aspect ratio stored in encoded frames, if it exists.

-stereo3d[:stream_specifier] layout (output,per-stream)

Set stereoscopic 3D layout metadata on the output stream. This does not rearrange pixels; use -vf stereo3d for that.

The metadata is stored as AV_PKT_DATA_STEREO3D side data on the output stream. Muxers that already consume that side data will write the corresponding container boxes or elements, including:

- MP4 Google spatial-media st3d (requires -strict unofficial)

- QuickTime MOV Apple vexu eyes (no st3d)

- Matroska StereoMode; -stereo3d overrides the stereo_mode metadata tag, including a value inherited from the input

layout is case-insensitive. The following values are accepted:

‘2d’

‘mono’

Monoscopic video.

‘sbs’

‘sbsl’

‘side by side’

Side-by-side, left eye on the left.

‘tb’

‘tbl’

‘top and bottom’

Top-and-bottom, left eye on top.

Inverted layouts such as ‘sbsr’ are not supported. An empty stream specifier applies to video streams only and is ignored for audio and other types. An explicit specifier on a non-video stream (for example -stereo3d:a) is an error.

Recommended form: -stereo3d:v sbsl.

-display_rotation[:stream_specifier] rotation (input,per-stream)

Set video rotation metadata.

rotation is a decimal number specifying the amount in degree by which the video should be rotated counter-clockwise before being displayed.

This option overrides the rotation/display transform metadata stored in the file, if any. When the video is being transcoded (rather than copied) and -autorotate is enabled, the video will be rotated at the filtering stage. Otherwise, the metadata will be written into the output file if the muxer supports it.

If the -display_hflip and/or -display_vflip options are given, they are applied after the rotation specified by this option.

-display_hflip[:stream_specifier] (input,per-stream)

Set whether on display the image should be horizontally flipped.

See the -display_rotation option for more details.

-display_vflip[:stream_specifier] (input,per-stream)

Set whether on display the image should be vertically flipped.

See the -display_rotation option for more details.

-mastering_display[:stream_specifier] G(%u,%u)B(%u,%u)R(%u,%u)WP(%u,%u)L(%u,%u) (input,per-stream)

Set video mastering display metadata.

G(%u,%u)B(%u,%u)R(%u,%u)WP(%u,%u)L(%u,%u) is a string specifying X,Y display primaries for GBR channels and white point (WP) in units of 0.00002, and max-min luminance (L) values in units of 0.0001 candela per meter square. The values are unsigned integers representing the numerator of a rational with an implicit denominator of 50000 for GBR and (WP), and implicit denominator 10000 for (L).

This option overrides the mastering display metadata stored in the file, if any.

-content_light[:stream_specifier] %u,%u (input,per-stream)

Set video content light metadata.

%u,%u is a string specifying max content light level and maximum picture average light level.

This option overrides the content light metadata stored in the file, if any.

-vn (input/output)

As an input option, blocks all video streams of a file from being filtered or being automatically selected or mapped for any output. See -discard option to disable streams individually.

As an output option, disables video recording i.e. automatic selection or mapping of any video stream. For full manual control see the -map option.

-vcodec codec (output)

Set the video codec. This is an alias for -codec:v.

-pass[:stream_specifier] n (output,per-stream)

Select the pass number (1 or 2). It is used to do two-pass video encoding. The statistics of the video are recorded in the first pass into a log file (see also the option -passlogfile), and in the second pass that log file is used to generate the video at the exact requested bitrate. On pass 1, you may just deactivate audio and set output to null, examples for Windows and Unix:

```
ffmpeg -i foo.mov -c:v libxvid -pass 1 -an -f rawvideo -y NUL
ffmpeg -i foo.mov -c:v libxvid -pass 1 -an -f rawvideo -y /dev/null

```

-passlogfile[:stream_specifier] prefix (output,per-stream)

Set two-pass log file name prefix to prefix, the default file name prefix is “ffmpeg2pass”. The complete file name will be PREFIX-N.log, where N is a number specific to the output stream

-vf filtergraph (output)

Create the filtergraph specified by filtergraph and use it to filter the stream.

This is an alias for -filter:v, see the -filter option.

-autorotate

Automatically rotate the video according to file metadata. Enabled by default, use -noautorotate to disable it.

-autoscale

Automatically scale the video according to the resolution of first frame. Enabled by default, use -noautoscale to disable it. When autoscale is disabled, all output frames of filter graph might not be in the same resolution and may be inadequate for some encoder/muxer. Therefore, it is not recommended to disable it unless you really know what you are doing. Disable autoscale at your own risk.

### 5.6 Advanced Video options# TOC

-pix_fmt[:stream_specifier] format (input/output,per-stream)

Set pixel format. Use -pix_fmts to show all the supported pixel formats. If the selected pixel format can not be selected, ffmpeg will print a warning and select the best pixel format supported by the encoder. If pix_fmt is prefixed by a +, ffmpeg will exit with an error if the requested pixel format can not be selected, and automatic conversions inside filtergraphs are disabled. If pix_fmt is a single +, ffmpeg selects the same pixel format as the input (or graph output) and automatic conversions are disabled.

-sws_flags flags (input/output)

Set default flags for the libswscale library. These flags are used by automatically inserted scale filters and those within simple filtergraphs, if not overridden within the filtergraph definition.

See the ffmpeg-scaler manual for a list of scaler options.

-rc_override[:stream_specifier] override (output,per-stream)

Rate control override for specific intervals, formatted as "int,int,int" list separated with slashes. Two first values are the beginning and end frame numbers, last one is quantizer to use if positive, or quality factor if negative.

-vstats

Dump video coding statistics to vstats_HHMMSS.log. See the vstats file format section for the format description.

-vstats_file file

Dump video coding statistics to file. See the vstats file format section for the format description.

-vstats_version file

Specify which version of the vstats format to use. Default is 2. See the vstats file format section for the format description.

-vtag fourcc/tag (output)

Force video tag/fourcc. This is an alias for -tag:v.

-force_key_frames[:stream_specifier] time[,time...] (output,per-stream)

-force_key_frames[:stream_specifier] expr:expr (output,per-stream)

-force_key_frames[:stream_specifier] source (output,per-stream)

-force_key_frames[:stream_specifier] scd_metadata (output,per-stream)

force_key_frames can take arguments of the following form:

time[,time...]

If the argument consists of timestamps, ffmpeg will round the specified times to the nearest output timestamp as per the encoder time base and force a keyframe at the first frame having timestamp equal or greater than the computed timestamp. Note that if the encoder time base is too coarse, then the keyframes may be forced on frames with timestamps lower than the specified time. The default encoder time base is the inverse of the output framerate but may be set otherwise via -enc_time_base.

If one of the times is "chapters[delta]", it is expanded into the time of the beginning of all chapters in the file, shifted by delta, expressed as a time in seconds. This option can be useful to ensure that a seek point is present at a chapter mark or any other designated place in the output file.

For example, to insert a key frame at 5 minutes, plus key frames 0.1 second before the beginning of every chapter:

```
-force_key_frames 0:05:00,chapters-0.1

```

expr:expr

If the argument is prefixed with expr:, the string expr is interpreted like an expression and is evaluated for each frame. A key frame is forced in case the evaluation is non-zero.

The expression in expr can contain the following constants:

n

the number of current processed frame, starting from 0

n_forced

the number of forced frames

prev_forced_n

the number of the previous forced frame, it is NAN when no keyframe was forced yet

prev_forced_t

the time of the previous forced frame, it is NAN when no keyframe was forced yet

t

the time of the current processed frame

For example to force a key frame every 5 seconds, you can specify:

```
-force_key_frames expr:gte(t,n_forced*5)

```

To force a key frame 5 seconds after the time of the last forced one, starting from second 13:

```
-force_key_frames expr:if(isnan(prev_forced_t),gte(t,13),gte(t,prev_forced_t+5))

```

source

If the argument is source, ffmpeg will force a key frame if the current frame being encoded is marked as a key frame in its source. In cases where this particular source frame has to be dropped, enforce the next available frame to become a key frame instead.

scd_metadata

If the argument is scd_metadata, ffmpeg will force a key frame if the current frame contains a metadata entry with the key lavfi.scd.time. The metadata can be added by filters like scdet and scdet_vulkan. Avoid inserting filters that duplicate frames after scdet, as this can cause duplicate metadata for multiple frames and repeated insertion of key frames.

Note that forcing too many keyframes is very harmful for the lookahead algorithms of certain encoders: using fixed-GOP options or similar would be more efficient.

-apply_cropping[:stream_specifier] source (input,per-stream)

Automatically crop the video after decoding according to file metadata. Default is all.

none (0)

Don’t apply any cropping metadata.

all (1)

Apply both codec and container level croppping. This is the default mode.

codec (2)

Apply codec level croppping.

container (3)

Apply container level croppping.

-copyinkf[:stream_specifier] (output,per-stream)

When doing stream copy, copy also non-key frames found at the beginning.

-init_hw_device type[=name][:device[,key=value...]]

Initialise a new hardware device of type type called name, using the given device parameters. If no name is specified it will receive a default name of the form "type%d".

The meaning of device and the following arguments depends on the device type:

cuda

device is the number of the CUDA device.

The following options are recognized:

primary_ctx

If set to 1, uses the primary device context instead of creating a new one.

Examples:

-init_hw_device cuda:1

Choose the second device on the system.

-init_hw_device cuda:0,primary_ctx=1

Choose the first device and use the primary device context.

dxva2

device is the number of the Direct3D 9 display adapter.

d3d11va

device is the number of the Direct3D 11 display adapter. If not specified, it will attempt to use the default Direct3D 11 display adapter or the first Direct3D 11 display adapter whose hardware VendorId is specified by ‘vendor_id’.

Examples:

-init_hw_device d3d11va

Create a d3d11va device on the default Direct3D 11 display adapter.

-init_hw_device d3d11va:1

Create a d3d11va device on the Direct3D 11 display adapter specified by index 1.

-init_hw_device d3d11va:,vendor_id=0x8086

Create a d3d11va device on the first Direct3D 11 display adapter whose hardware VendorId is 0x8086.

vaapi

device is either an X11 display name, a DRM render node or a DirectX adapter index. If not specified, it will attempt to open the default X11 display ($DISPLAY) and then the first DRM render node (/dev/dri/renderD128), or the default DirectX adapter on Windows.

The following options are recognized:

kernel_driver

When device is not specified, use this option to specify the name of the kernel driver associated with the desired device. This option is available only when the hardware acceleration method drm and vaapi are enabled.

vendor_id

When device and kernel_driver are not specified, use this option to specify the vendor id associated with the desired device. This option is available only when the hardware acceleration method drm and vaapi are enabled and kernel_driver is not specified.

Examples:

-init_hw_device vaapi

Create a vaapi device on the default device.

-init_hw_device vaapi:/dev/dri/renderD129

Create a vaapi device on DRM render node /dev/dri/renderD129.

-init_hw_device vaapi:1

Create a vaapi device on DirectX adapter 1.

-init_hw_device vaapi:,kernel_driver=i915

Create a vaapi device on a device associated with kernel driver ‘i915’.

-init_hw_device vaapi:,vendor_id=0x8086

Create a vaapi device on a device associated with vendor id ‘0x8086’.

vdpau

device is an X11 display name. If not specified, it will attempt to open the default X11 display ($DISPLAY).

qsv

device selects a value in ‘MFX_IMPL_*’. Allowed values are:

auto

sw

hw

auto_any

hw_any

hw2

hw3

hw4

If not specified, ‘auto_any’ is used. (Note that it may be easier to achieve the desired result for QSV by creating the platform-appropriate subdevice (‘dxva2’ or ‘d3d11va’ or ‘vaapi’) and then deriving a QSV device from that.)

The following options are recognized:

child_device

Specify a DRM render node on Linux or DirectX adapter on Windows.

child_device_type

Choose platform-appropriate subdevice type. On Windows ‘d3d11va’ is used as default subdevice type when --enable-libvpl is specified at configuration time, ‘dxva2’ is used as default subdevice type when --enable-libmfx is specified at configuration time. On Linux user can use ‘vaapi’ only as subdevice type.

Examples:

-init_hw_device qsv:hw,child_device=/dev/dri/renderD129

Create a QSV device with ‘MFX_IMPL_HARDWARE’ on DRM render node /dev/dri/renderD129.

-init_hw_device qsv:hw,child_device=1

Create a QSV device with ‘MFX_IMPL_HARDWARE’ on DirectX adapter 1.

-init_hw_device qsv:hw,child_device_type=d3d11va

Choose the GPU subdevice with type ‘d3d11va’ and create QSV device with ‘MFX_IMPL_HARDWARE’.

-init_hw_device qsv:hw,child_device_type=dxva2

Choose the GPU subdevice with type ‘dxva2’ and create QSV device with ‘MFX_IMPL_HARDWARE’.

-init_hw_device qsv:hw,child_device=1,child_device_type=d3d11va

Create a QSV device with ‘MFX_IMPL_HARDWARE’ on DirectX adapter 1 with subdevice type ‘d3d11va’.

-init_hw_device vaapi=va:/dev/dri/renderD129 -init_hw_device qsv=hw1@va

Create a VAAPI device called ‘va’ on /dev/dri/renderD129, then derive a QSV device called ‘hw1’ from device ‘va’.

opencl

device selects the platform and device as platform_index.device_index.

The set of devices can also be filtered using the key-value pairs to find only devices matching particular platform or device strings.

The strings usable as filters are:

platform_profile

platform_version

platform_name

platform_vendor

platform_extensions

device_name

device_vendor

driver_version

device_version

device_profile

device_extensions

device_type

The indices and filters must together uniquely select a device.

Examples:

-init_hw_device opencl:0.1

Choose the second device on the first platform.

-init_hw_device opencl:,device_name=Foo9000

Choose the device with a name containing the string Foo9000.

-init_hw_device opencl:1,device_type=gpu,device_extensions=cl_khr_fp16

Choose the GPU device on the second platform supporting the cl_khr_fp16 extension.

vulkan

If device is an integer, it selects the device by its index in a system-dependent list of devices. If device is any other string, it selects the first device with a name containing that string as a substring.

The following options are recognized:

debug

If set to 1, enables the validation layer, if installed.

linear_images

If set to 1, images allocated by the hwcontext will be linear and locally mappable.

instance_extensions

A plus separated list of additional instance extensions to enable.

device_extensions

A plus separated list of additional device extensions to enable.

Examples:

-init_hw_device vulkan:1

Choose the second device on the system.

-init_hw_device vulkan:RADV

Choose the first device with a name containing the string RADV.

-init_hw_device vulkan:0,instance_extensions=VK_KHR_wayland_surface+VK_KHR_xcb_surface

Choose the first device and enable the Wayland and XCB instance extensions.

-init_hw_device type[=name]@source

Initialise a new hardware device of type type called name, deriving it from the existing device with the name source.

-init_hw_device list

List all hardware device types supported in this build of ffmpeg.

-filter_hw_device name

Pass the hardware device called name to all filters in any filter graph. This can be used to set the device to upload to with the hwupload filter, or the device to map to with the hwmap filter. Other filters may also make use of this parameter when they require a hardware device. Note that this is typically only required when the input is not already in hardware frames - when it is, filters will derive the device they require from the context of the frames they receive as input.

This is a global setting, so all filters will receive the same device.

-hwaccel[:stream_specifier] hwaccel (input,per-stream)

Use hardware acceleration to decode the matching stream(s). The allowed values of hwaccel are:

none

Do not use any hardware acceleration (the default).

auto

Automatically select the hardware acceleration method.

vdpau

Use VDPAU (Video Decode and Presentation API for Unix) hardware acceleration.

dxva2

Use DXVA2 (DirectX Video Acceleration) hardware acceleration.

d3d11va

Use D3D11VA (DirectX Video Acceleration) hardware acceleration.

vaapi

Use VAAPI (Video Acceleration API) hardware acceleration.

qsv

Use the Intel QuickSync Video acceleration for video transcoding.

Unlike most other values, this option does not enable accelerated decoding (that is used automatically whenever a qsv decoder is selected), but accelerated transcoding, without copying the frames into the system memory.

For it to work, both the decoder and the encoder must support QSV acceleration and no filters must be used.

videotoolbox

Use Video Toolbox hardware acceleration.

This option has no effect if the selected hwaccel is not available or not supported by the chosen decoder.

Note that most acceleration methods are intended for playback and will not be faster than software decoding on modern CPUs. Additionally, ffmpeg will usually need to copy the decoded frames from the GPU memory into the system memory, resulting in further performance loss. This option is thus mainly useful for testing.

-hwaccel_device[:stream_specifier] hwaccel_device (input,per-stream)

Select a device to use for hardware acceleration.

This option only makes sense when the -hwaccel option is also specified. It can either refer to an existing device created with -init_hw_device by name, or it can create a new device as if ‘-init_hw_device’ type:hwaccel_device were called immediately before.

-hwaccels

List all hardware acceleration components enabled in this build of ffmpeg. Actual runtime availability depends on the hardware and its suitable driver being installed.

-fix_sub_duration_heartbeat[:stream_specifier]

Set a specific output video stream as the heartbeat stream according to which to split and push through currently in-progress subtitle upon receipt of a random access packet.

This lowers the latency of subtitles for which the end packet or the following subtitle has not yet been received. As a drawback, this will most likely lead to duplication of subtitle events in order to cover the full duration, so when dealing with use cases where latency of when the subtitle event is passed on to output is not relevant this option should not be utilized.

Requires -fix_sub_duration to be set for the relevant input subtitle stream for this to have any effect, as well as for the input subtitle stream having to be directly mapped to the same output in which the heartbeat stream resides.

### 5.7 Audio Options# TOC

-aframes number (output)

Set the number of audio frames to output. This is an obsolete alias for -frames:a, which you should use instead.

-ar[:stream_specifier] freq (input/output,per-stream)

Set the audio sampling frequency. For output streams it is set by default to the frequency of the corresponding input stream. For input streams this option only makes sense for audio grabbing devices and raw demuxers and is mapped to the corresponding demuxer options.

-aq q (output)

Set the audio quality (codec-specific, VBR). This is an alias for -q:a.

-ac[:stream_specifier] channels (input/output,per-stream)

Set the number of audio channels. For output streams it is set by default to the number of input audio channels. For input streams this option only makes sense for audio grabbing devices and raw demuxers and is mapped to the corresponding demuxer options.

-an (input/output)

As an input option, blocks all audio streams of a file from being filtered or being automatically selected or mapped for any output. See -discard option to disable streams individually.

As an output option, disables audio recording i.e. automatic selection or mapping of any audio stream. For full manual control see the -map option.

-acodec codec (input/output)

Set the audio codec. This is an alias for -codec:a.

-sample_fmt[:stream_specifier] sample_fmt (output,per-stream)

Set the audio sample format. Use -sample_fmts to get a list of supported sample formats.

-af filtergraph (output)

Create the filtergraph specified by filtergraph and use it to filter the stream.

This is an alias for -filter:a, see the -filter option.

### 5.8 Advanced Audio options# TOC

-atag fourcc/tag (output)

Force audio tag/fourcc. This is an alias for -tag:a.

-ch_layout[:stream_specifier] layout (input/output,per-stream)

Alias for -channel_layout.

-channel_layout[:stream_specifier] layout (input/output,per-stream)

Set the audio channel layout. For output streams it is set by default to the input channel layout. For input streams it overrides the channel layout of the input. Not all decoders respect the overridden channel layout. This option also sets the channel layout for audio grabbing devices and raw demuxers and is mapped to the corresponding demuxer option.

-guess_layout_max channels (input,per-stream)

If some input channel layout is not known, try to guess only if it corresponds to at most the specified number of channels. For example, 2 tells to ffmpeg to recognize 1 channel as mono and 2 channels as stereo but not 6 channels as 5.1. The default is to always try to guess. Use 0 to disable all guessing. Using the -channel_layout option to explicitly specify an input layout also disables guessing.

### 5.9 Subtitle options# TOC

-scodec codec (input/output)

Set the subtitle codec. This is an alias for -codec:s.

-sn (input/output)

As an input option, blocks all subtitle streams of a file from being filtered or being automatically selected or mapped for any output. See -discard option to disable streams individually.

As an output option, disables subtitle recording i.e. automatic selection or mapping of any subtitle stream. For full manual control see the -map option.

### 5.10 Advanced Subtitle options# TOC

-fix_sub_duration

Fix subtitles durations. For each subtitle, wait for the next packet in the same stream and adjust the duration of the first to avoid overlap. This is necessary with some subtitles codecs, especially DVB subtitles, because the duration in the original packet is only a rough estimate and the end is actually marked by an empty subtitle frame. Failing to use this option when necessary can result in exaggerated durations or muxing failures due to non-monotonic timestamps.

Note that this option will delay the output of all data until the next subtitle packet is decoded: it may increase memory consumption and latency a lot.

-canvas_size size

Set the size of the canvas used to render subtitles.

### 5.11 Advanced options# TOC

-map [-]input_file_id[:stream_specifier][:view_specifier][:?] | [linklabel] (output)

Create one or more streams in the output file. This option has two forms for specifying the data source(s): the first selects one or more streams from some input file (specified with -i), the second takes an output from some complex filtergraph (specified with -filter_complex).

In the first form, an output stream is created for every stream from the input file with the index input_file_id. If stream_specifier is given, only those streams that match the specifier are used (see the Stream specifiers section for the stream_specifier syntax).

A - character before the stream identifier creates a "negative" mapping. It disables matching streams from already created mappings.

An optional view_specifier may be given after the stream specifier, which for multiview video specifies the view to be used. The view specifier may have one of the following formats:

view:view_id

select a view by its ID; view_id may be set to ’all’ to use all the views interleaved into one stream;

vidx:view_idx

select a view by its index; i.e. 0 is the base view, 1 is the first non-base view, etc.

vpos:position

select a view by its display position; position may be left or right

The default for transcoding is to only use the base view, i.e. the equivalent of vidx:0. For streamcopy, view specifiers are not supported and all views are always copied.

A trailing ? after the stream index will allow the map to be optional: if the map matches no streams the map will be ignored instead of failing. Note the map will still fail if an invalid input file index is used; such as if the map refers to a non-existent input.

An alternative [linklabel] form will map outputs from complex filter graphs (see the -filter_complex option) to the output file. linklabel must correspond to a defined output link label in the graph.

This option may be specified multiple times, each adding more streams to the output file. Any given input stream may also be mapped any number of times as a source for different output streams, e.g. in order to use different encoding options and/or filters. The streams are created in the output in the same order in which the -map options are given on the commandline.

Using this option disables the default mappings for this output file.

Examples:

map everything

To map ALL streams from the first input file to output

```
ffmpeg -i INPUT -map 0 output

```

select specific stream

If you have two audio streams in the first input file, these streams are identified by 0:0 and 0:1. You can use -map to select which streams to place in an output file. For example:

```
ffmpeg -i INPUT -map 0:1 out.wav

```

will map the second input stream in INPUT to the (single) output stream in out.wav.

create multiple streams

To select the stream with index 2 from input file a.mov (specified by the identifier 0:2), and stream with index 6 from input b.mov (specified by the identifier 1:6), and copy them to the output file out.mov:

```
ffmpeg -i a.mov -i b.mov -c copy -map 0:2 -map 1:6 out.mov

```

create multiple streams 2

To select all video and the third audio stream from an input file:

```
ffmpeg -i INPUT -map 0:v -map 0:a:2 OUTPUT

```

negative map

To map all the streams except the second audio, use negative mappings

```
ffmpeg -i INPUT -map 0 -map -0:a:1 OUTPUT

```

optional map

To map the video and audio streams from the first input, and using the trailing ?, ignore the audio mapping if no audio streams exist in the first input:

```
ffmpeg -i INPUT -map 0:v -map 0:a? OUTPUT

```

map by language

To pick the English audio stream:

```
ffmpeg -i INPUT -map 0:m:language:eng OUTPUT

```

-ignore_unknown

Ignore input streams with unknown type instead of failing if copying such streams is attempted.

-copy_unknown

Allow input streams with unknown type to be copied instead of failing if copying such streams is attempted.

-map_metadata[:metadata_spec_out] infile[:metadata_spec_in] (output,per-metadata)

Set metadata information of the next output file from infile. Note that those are file indices (zero-based), not filenames. Optional metadata_spec_in/out parameters specify, which metadata to copy. A metadata specifier can have the following forms:

g

global metadata, i.e. metadata that applies to the whole file

s[:stream_spec]

per-stream metadata. stream_spec is a stream specifier as described in the Stream specifiers chapter. In an input metadata specifier, the first matching stream is copied from. In an output metadata specifier, all matching streams are copied to.

c:chapter_index

per-chapter metadata. chapter_index is the zero-based chapter index.

p:program_index

per-program metadata. program_index is the zero-based program index.

If metadata specifier is omitted, it defaults to global.

By default, global metadata is copied from the first input file, per-stream and per-chapter metadata is copied along with streams/chapters. These default mappings are disabled by creating any mapping of the relevant type. A negative file index can be used to create a dummy mapping that just disables automatic copying.

For example to copy metadata from the first stream of the input file to global metadata of the output file:

```
ffmpeg -i in.ogg -map_metadata 0:s:0 out.mp3

```

To do the reverse, i.e. copy global metadata to all audio streams:

```
ffmpeg -i in.mkv -map_metadata:s:a 0:g out.mkv

```

Note that simple 0 would work as well in this example, since global metadata is assumed by default.

-map_chapters input_file_index (output)

Copy chapters from input file with index input_file_index to the next output file. If no chapter mapping is specified, then chapters are copied from the first input file with at least one chapter. Use a negative file index to disable any chapter copying.

-benchmark (global)

Show benchmarking information at the end of an encode. Shows real, system and user time used and maximum memory consumption. Maximum memory consumption is not supported on all systems, it will usually display as 0 if not supported.

-benchmark_all (global)

Show benchmarking information during the encode. Shows real, system and user time used in various steps (audio/video encode/decode).

-timelimit duration (global)

Exit after ffmpeg has been running for duration seconds in CPU user time.

-dump (global)

Dump each input packet to stderr.

-hex (global)

When dumping packets, also dump the payload.

-readrate speed (input)

Limit input read speed.

Its value is a floating-point positive number which represents the maximum duration of media, in seconds, that should be ingested in one second of wallclock time. Default value is zero and represents no imposed limitation on speed of ingestion. Value 1 represents real-time speed and is equivalent to -re.

Mainly used to simulate a capture device or live input stream (e.g. when reading from a file). Should not be used with a low value when input is an actual capture device or live stream as it may cause packet loss.

It is useful for when flow speed of output packets is important, such as live streaming.

-re (input)

Read input at native frame rate. This is equivalent to setting -readrate 1.

-readrate_initial_burst seconds

Set an initial read burst time, in seconds, after which -re/-readrate will be enforced.

-readrate_catchup speed (input)

If either the input or output is blocked leading to actual read speed falling behind the specified readrate, then this rate takes effect till the input catches up with the specified readrate. Must not be lower than the primary readrate.

-fps_mode[:stream_specifier] parameter (output,per-stream)

Set video sync method / framerate mode.

passthrough

Each frame is passed with its timestamp from the demuxer to the muxer.

cfr

Frames will be duplicated and dropped to achieve exactly the requested constant frame rate.

vfr

Frames are passed through with their timestamp or dropped so as to prevent 2 frames from having the same timestamp.

auto

Chooses between cfr and vfr depending on muxer capabilities. This is the default method.

Note that the timestamps may be further modified by the muxer, after this. For example, in the case that the format option avoid_negative_ts is enabled.

With -map you can select from which stream the timestamps should be taken. You can leave either video or audio unchanged and sync the remaining stream(s) to the unchanged one.

-frame_drop_threshold parameter

Frame drop threshold, which specifies how much behind video frames can be before they are dropped. In frame rate units, so 1.0 is one frame. The default is -1.1. One possible usecase is to avoid framedrops in case of noisy timestamps or to increase frame drop precision in case of exact timestamps.

-apad parameters (output,per-stream)

Pad the output audio stream(s). This is the same as applying -af apad. Argument is a string of filter parameters composed the same as with the apad filter. -shortest must be set for this output for the option to take effect.

-copyts

Do not process input timestamps, but keep their values without trying to sanitize them. In particular, do not remove the initial start time offset value.

Note that, depending on the fps_mode option or on specific muxer processing (e.g. in case the format option avoid_negative_ts is enabled) the output timestamps may mismatch with the input timestamps even when this option is selected.

-start_at_zero

When used with copyts, shift input timestamps so they start at zero.

This means that using e.g. -ss 50 will make output timestamps start at 50 seconds, regardless of what timestamp the input file started at.

-copytb mode

Specify how to set the encoder timebase when stream copying. mode is an integer numeric value, and can assume one of the following values:

1

Use the demuxer timebase.

The time base is copied to the output encoder from the corresponding input demuxer. This is sometimes required to avoid non monotonically increasing timestamps when copying video streams with variable frame rate.

0

Use the decoder timebase.

The time base is copied to the output encoder from the corresponding input decoder.

-1

Try to make the choice automatically, in order to generate a sane output.

Default value is -1.

-enc_time_base[:stream_specifier] timebase (output,per-stream)

Set the encoder timebase. timebase can assume one of the following values:

0

Assign a default value according to the media type.

For video - use 1/framerate, for audio - use 1/samplerate.

demux

Use the timebase from the demuxer.

filter

Use the timebase from the filtergraph.

a positive number

Use the provided number as the timebase.

This field can be provided as a ratio of two integers (e.g. 1:24, 1:48000) or as a decimal number (e.g. 0.04166, 2.0833e-5)

Default value is 0.

-bitexact (input/output)

Enable bitexact mode for (de)muxer and (de/en)coder

-shortest (output)

Finish encoding when the shortest output stream ends.

Note that this option may require buffering frames, which introduces extra latency. The maximum amount of this latency may be controlled with the -shortest_buf_duration option.

-shortest_buf_duration duration (output)

The -shortest option may require buffering potentially large amounts of data when at least one of the streams is "sparse" (i.e. has large gaps between frames – this is typically the case for subtitles).

This option controls the maximum duration of buffered frames in seconds. Larger values may allow the -shortest option to produce more accurate results, but increase memory use and latency.

The default value is 10 seconds.

-dts_delta_threshold threshold

Timestamp discontinuity delta threshold, expressed as a decimal number of seconds.

The timestamp discontinuity correction enabled by this option is only applied to input formats accepting timestamp discontinuity (for which the AVFMT_TS_DISCONT flag is enabled), e.g. MPEG-TS and HLS, and is automatically disabled when employing the -copyts option (unless wrapping is detected).

If a timestamp discontinuity is detected whose absolute value is greater than threshold, ffmpeg will remove the discontinuity by decreasing/increasing the current DTS and PTS by the corresponding delta value.

The default value is 10.

-dts_error_threshold threshold

Timestamp error delta threshold, expressed as a decimal number of seconds.

The timestamp correction enabled by this option is only applied to input formats not accepting timestamp discontinuity (for which the AVFMT_TS_DISCONT flag is not enabled).

If a timestamp discontinuity is detected whose absolute value is greater than threshold, ffmpeg will drop the PTS/DTS timestamp value.

The default value is 3600*30 (30 hours), which is arbitrarily picked and quite conservative.

-muxdelay seconds (output)

Set the maximum demux-decode delay.

-muxpreload seconds (output)

Set the initial demux-decode delay.

-streamid output-stream-index:new-value (output)

Assign a new stream-id value to an output stream. This option should be specified prior to the output filename to which it applies. For the situation where multiple output files exist, a streamid may be reassigned to a different value.

For example, to set the stream 0 PID to 33 and the stream 1 PID to 36 for an output mpegts file:

```
ffmpeg -i inurl -streamid 0:33 -streamid 1:36 out.ts

```

-bsf[:stream_specifier] bitstream_filters (input/output,per-stream)

Apply bitstream filters to matching streams. The filters are applied to each packet as it is received from the demuxer (when used as an input option) or before it is sent to the muxer (when used as an output option).

bitstream_filters is a comma-separated list of bitstream filter specifications, each of the form

```
filter[=optname0=optval0:optname1=optval1:...]

```

Any of the ’,=:’ characters that are to be a part of an option value need to be escaped with a backslash.

Use the -bsfs option to get the list of bitstream filters.

E.g.

```
ffmpeg -bsf:v h264_mp4toannexb -i h264.mp4 -c:v copy -an out.h264

```

applies the h264_mp4toannexb bitstream filter (which converts MP4-encapsulated H.264 stream to Annex B) to the input video stream.

On the other hand,

```
ffmpeg -i file.mov -an -vn -bsf:s mov2textsub -c:s copy -f rawvideo sub.txt

```

applies the mov2textsub bitstream filter (which extracts text from MOV subtitles) to the output subtitle stream. Note, however, that since both examples use -c copy, it matters little whether the filters are applied on input or output - that would change if transcoding was happening.

-tag[:stream_specifier] codec_tag (input/output,per-stream)

Force a tag/fourcc for matching streams.

-timecode hh:mm:ssSEPff

Specify Timecode for writing. SEP is ’:’ for non drop timecode and ’;’ (or ’.’) for drop.

```
ffmpeg -i input.mpg -timecode 01:02:03.04 -r 30000/1001 -s ntsc output.mpg

```

-filter_complex filtergraph (global)

Define a complex filtergraph, i.e. one with arbitrary number of inputs and/or outputs. For simple graphs – those with one input and one output of the same type – see the -filter options. filtergraph is a description of the filtergraph, as described in the “Filtergraph syntax” section of the ffmpeg-filters manual. This option may be specified multiple times - each use creates a new complex filtergraph.

Inputs to a complex filtergraph may come from different source types, distinguished by the format of the corresponding link label:

- To connect an input stream, use [file_index:stream_specifier] (i.e. the same syntax as -map). If stream_specifier matches multiple streams, the first one will be used. For multiview video, the stream specifier may be followed by the view specifier, see documentation for the -map option for its syntax.

- To connect a loopback decoder use [dec:dec_idx], where dec_idx is the index of the loopback decoder to be connected to given input. For multiview video, the decoder index may be followed by the view specifier, see documentation for the -map option for its syntax.

- To connect an output from another complex filtergraph, use its link label. E.g the following example:

```
ffmpeg -i input.mkv \
  -filter_complex '[0:v]scale=size=hd1080,split=outputs=2[for_enc][orig_scaled]' \
  -c:v libx264 -map '[for_enc]' output.mkv \
  -dec 0:0 \
  -filter_complex '[dec:0][orig_scaled]hstack[stacked]' \
  -map '[stacked]' -c:v ffv1 comparison.mkv

```

reads an input video and

- (line 2) uses a complex filtergraph with one input and two outputs to scale the video to 1920x1080 and duplicate the result to both outputs;

- (line 3) encodes one scaled output with libx264 and writes the result to output.mkv;

- (line 4) decodes this encoded stream with a loopback decoder;

- (line 5) places the output of the loopback decoder (i.e. the libx264-encoded video) side by side with the scaled original input;

- (line 6) combined video is then losslessly encoded and written into comparison.mkv.

Note that the two filtergraphs cannot be combined into one, because then there would be a cycle in the transcoding pipeline (filtergraph output goes to encoding, from there to decoding, then back to the same graph), and such cycles are not allowed.

An unlabeled input will be connected to the first unused input stream of the matching type.

Output link labels are referred to with -map. Unlabeled outputs are added to the first output file.

Note that with this option it is possible to use only lavfi sources without normal input files.

For example, to overlay an image over video

```
ffmpeg -i video.mkv -i image.png -filter_complex '[0:v][1:v]overlay[out]' -map
'[out]' out.mkv

```

Here [0:v] refers to the first video stream in the first input file, which is linked to the first (main) input of the overlay filter. Similarly the first video stream in the second input is linked to the second (overlay) input of overlay.

Assuming there is only one video stream in each input file, we can omit input labels, so the above is equivalent to

```
ffmpeg -i video.mkv -i image.png -filter_complex 'overlay[out]' -map
'[out]' out.mkv

```

Furthermore we can omit the output label and the single output from the filter graph will be added to the output file automatically, so we can simply write

```
ffmpeg -i video.mkv -i image.png -filter_complex 'overlay' out.mkv

```

As a special exception, you can use a bitmap subtitle stream as input: it will be converted into a video with the same size as the largest video in the file, or 720x576 if no video is present. Note that this is an experimental and temporary solution. It will be removed once libavfilter has proper support for subtitles.

For example, to hardcode subtitles on top of a DVB-T recording stored in MPEG-TS format, delaying the subtitles by 1 second:

```
ffmpeg -i input.ts -filter_complex \
  '[#0x2ef] setpts=PTS+1/TB [sub] ; [#0x2d0] [sub] overlay' \
  -sn -map '#0x2dc' output.mkv

```

(0x2d0, 0x2dc and 0x2ef are the MPEG-TS PIDs of respectively the video, audio and subtitles streams; 0:0, 0:3 and 0:7 would have worked too)

To generate 5 seconds of pure red video using lavfi color source:

```
ffmpeg -filter_complex 'color=c=red' -t 5 out.mkv

```

-filter_complex_threads nb_threads (global)

Defines how many threads are used to process a filter_complex graph. Similar to filter_threads but used for -filter_complex graphs only. The default is the number of available CPUs.

-lavfi filtergraph (global)

Define a complex filtergraph, i.e. one with arbitrary number of inputs and/or outputs. Equivalent to -filter_complex.

-accurate_seek (input)

This option enables or disables accurate seeking in input files with the -ss option. It is enabled by default, so seeking is accurate when transcoding. Use -noaccurate_seek to disable it, which may be useful e.g. when copying some streams and transcoding the others.

-seek_timestamp (input)

This option enables or disables seeking by timestamp in input files with the -ss option. It is disabled by default. If enabled, the argument to the -ss option is considered an actual timestamp, and is not offset by the start time of the file. This matters only for files which do not start from timestamp 0, such as transport streams.

-thread_queue_size size (output)

This option specifies the maximum number of packets per stream that may be queued to each muxing thread.

-sdp_file file (global)

Print sdp information for an output stream to file. This allows dumping sdp information when at least one output isn’t an rtp stream. (Requires at least one of the output formats to be rtp).

-discard (input)

Allows discarding specific streams or frames from streams. Any input stream can be fully discarded, using value all whereas selective discarding of frames from a stream occurs at the demuxer and is not supported by all demuxers.

none

Discard no frame.

default

Default, which discards no frames.

noref

Discard all non-reference frames.

bidir

Discard all bidirectional frames.

nokey

Discard all frames excepts keyframes.

all

Discard all frames.

-abort_on flags (global)

Stop and abort on various conditions. The following flags are available:

empty_output

No packets were passed to the muxer, the output is empty.

empty_output_stream

No packets were passed to the muxer in some of the output streams.

-max_error_rate (global)

Set fraction of decoding frame failures across all inputs which when crossed ffmpeg will return exit code 69. Crossing this threshold does not terminate processing. Range is a floating-point number between 0 to 1. Default is 2/3.

-xerror (global)

Stop and exit on error

-max_muxing_queue_size packets (output,per-stream)

When transcoding audio and/or video streams, ffmpeg will not begin writing into the output until it has one packet for each such stream. While waiting for that to happen, packets for other streams are buffered. This option sets the size of this buffer, in packets, for the matching output stream.

The default value of this option should be high enough for most uses, so only touch this option if you are sure that you need it.

-muxing_queue_data_threshold bytes (output,per-stream)

This is a minimum threshold until which the muxing queue size is not taken into account. Defaults to 50 megabytes per stream, and is based on the overall size of packets passed to the muxer.

-auto_conversion_filters (global)

Enable automatically inserting format conversion filters in all filter graphs, including those defined by -vf, -af, -filter_complex and -lavfi. If filter format negotiation requires a conversion, the initialization of the filters will fail. Conversions can still be performed by inserting the relevant conversion filter (scale, aresample) in the graph. On by default, to explicitly disable it you need to specify -noauto_conversion_filters.

-bits_per_raw_sample[:stream_specifier] value (output,per-stream)

Declare the number of bits per raw sample in the given output stream to be value. Note that this option sets the information provided to the encoder/muxer, it does not change the stream to conform to this value. Setting values that do not match the stream properties may result in encoding failures or invalid output files.

-stats_enc_pre[:stream_specifier] path (output,per-stream)

-stats_enc_post[:stream_specifier] path (output,per-stream)

-stats_mux_pre[:stream_specifier] path (output,per-stream)

Write per-frame encoding information about the matching streams into the file given by path.

-stats_enc_pre writes information about raw video or audio frames right before they are sent for encoding, while -stats_enc_post writes information about encoded packets as they are received from the encoder. -stats_mux_pre writes information about packets just as they are about to be sent to the muxer. Every frame or packet produces one line in the specified file. The format of this line is controlled by -stats_enc_pre_fmt / -stats_enc_post_fmt / -stats_mux_pre_fmt.

When stats for multiple streams are written into a single file, the lines corresponding to different streams will be interleaved. The precise order of this interleaving is not specified and not guaranteed to remain stable between different invocations of the program, even with the same options.

-stats_enc_pre_fmt[:stream_specifier] format_spec (output,per-stream)

-stats_enc_post_fmt[:stream_specifier] format_spec (output,per-stream)

-stats_mux_pre_fmt[:stream_specifier] format_spec (output,per-stream)

Specify the format for the lines written with -stats_enc_pre / -stats_enc_post / -stats_mux_pre.

format_spec is a string that may contain directives of the form {fmt}. format_spec is backslash-escaped — use \{, \}, and \\ to write a literal {, }, or \, respectively, into the output.

The directives given with fmt may be one of the following:

fidx

Index of the output file.

sidx

Index of the output stream in the file.

n

Frame number. Pre-encoding: number of frames sent to the encoder so far. Post-encoding: number of packets received from the encoder so far. Muxing: number of packets submitted to the muxer for this stream so far.

ni

Input frame number. Index of the input frame (i.e. output by a decoder) that corresponds to this output frame or packet. -1 if unavailable.

tb

Timebase in which this frame/packet’s timestamps are expressed, as a rational number num/den. Note that encoder and muxer may use different timebases.

tbi

Timebase for ptsi, as a rational number num/den. Available when ptsi is available, 0/1 otherwise.

pts

Presentation timestamp of the frame or packet, as an integer. Should be multiplied by the timebase to compute presentation time.

ptsi

Presentation timestamp of the input frame (see ni), as an integer. Should be multiplied by tbi to compute presentation time. Printed as (2^63 - 1 = 9223372036854775807) when not available.

t

Presentation time of the frame or packet, as a decimal number. Equal to pts multiplied by tb.

ti

Presentation time of the input frame (see ni), as a decimal number. Equal to ptsi multiplied by tbi. Printed as inf when not available.

dts (packet)

Decoding timestamp of the packet, as an integer. Should be multiplied by the timebase to compute presentation time.

dt (packet)

Decoding time of the frame or packet, as a decimal number. Equal to dts multiplied by tb.

sn (frame,audio)

Number of audio samples sent to the encoder so far.

samp (frame,audio)

Number of audio samples in the frame.

size (packet)

Size of the encoded packet in bytes.

br (packet)

Current bitrate in bits per second.

abr (packet)

Average bitrate for the whole stream so far, in bits per second, -1 if it cannot be determined at this point.

key (packet)

Character ’K’ if the packet contains a keyframe, character ’N’ otherwise.

Directives tagged with packet may only be used with -stats_enc_post_fmt and -stats_mux_pre_fmt.

Directives tagged with frame may only be used with -stats_enc_pre_fmt.

Directives tagged with audio may only be used with audio streams.

The default format strings are:

pre-encoding

{fidx} {sidx} {n} {t}

post-encoding

{fidx} {sidx} {n} {t}

In the future, new items may be added to the end of the default formatting strings. Users who depend on the format staying exactly the same, should prescribe it manually.

Note that stats for different streams written into the same file may have different formats.

### 5.12 Preset files# TOC

A preset file contains a sequence of option=value pairs, one for each line, specifying a sequence of options which would be awkward to specify on the command line. Lines starting with the hash (’#’) character are ignored and are used to provide comments. Check the presets directory in the FFmpeg source tree for examples.

There are two types of preset files: ffpreset and avpreset files.

#### 5.12.1 ffpreset files# TOC

ffpreset files are specified with the vpre, apre, spre, and fpre options. The fpre option takes the filename of the preset instead of a preset name as input and can be used for any kind of codec. For the vpre, apre, and spre options, the options specified in a preset file are applied to the currently selected codec of the same type as the preset option.

The argument passed to the vpre, apre, and spre preset options identifies the preset file to use according to the following rules:

First ffmpeg searches for a file named arg.ffpreset in the directories $FFMPEG_DATADIR (if set), and $HOME/.ffmpeg, and in the datadir defined at configuration time (usually PREFIX/share/ffmpeg) or in a ffpresets folder along the executable on win32, in that order. For example, if the argument is libvpx-1080p, it will search for the file libvpx-1080p.ffpreset.

If no such file is found, then ffmpeg will search for a file named codec_name-arg.ffpreset in the above-mentioned directories, where codec_name is the name of the codec to which the preset file options will be applied. For example, if you select the video codec with -vcodec libvpx and use -vpre 1080p, then it will search for the file libvpx-1080p.ffpreset.

#### 5.12.2 avpreset files# TOC

avpreset files are specified with the pre option. They work similar to ffpreset files, but they only allow encoder- specific options. Therefore, an option=value pair specifying an encoder cannot be used.

When the pre option is specified, ffmpeg will look for files with the suffix .avpreset in the directories $AVCONV_DATADIR (if set), and $HOME/.avconv, and in the datadir defined at configuration time (usually PREFIX/share/ffmpeg), in that order.

First ffmpeg searches for a file named codec_name-arg.avpreset in the above-mentioned directories, where codec_name is the name of the codec to which the preset file options will be applied. For example, if you select the video codec with -vcodec libvpx and use -pre 1080p, then it will search for the file libvpx-1080p.avpreset.

If no such file is found, then ffmpeg will search for a file named arg.avpreset in the same directories.

### 5.13 vstats file format# TOC

The -vstats and -vstats_file options enable generation of a file containing statistics about the generated video outputs.

The -vstats_version option controls the format version of the generated file.

With version 1 the format is:

```
frame= FRAME q= FRAME_QUALITY PSNR= PSNR f_size= FRAME_SIZE s_size= STREAM_SIZEkB time= TIMESTAMP br= BITRATEkbits/s avg_br= AVERAGE_BITRATEkbits/s

```

With version 2 the format is:

```
out= OUT_FILE_INDEX st= OUT_FILE_STREAM_INDEX frame= FRAME_NUMBER q= FRAME_QUALITYf PSNR= PSNR f_size= FRAME_SIZE s_size= STREAM_SIZEkB time= TIMESTAMP br= BITRATEkbits/s avg_br= AVERAGE_BITRATEkbits/s

```

The value corresponding to each key is described below:

avg_br

average bitrate expressed in Kbits/s

br

bitrate expressed in Kbits/s

frame

number of encoded frame

out

out file index

PSNR

Peak Signal to Noise Ratio

q

quality of the frame

f_size

encoded packet size expressed as number of bytes

s_size

stream size expressed in KiB

st

out file stream index

time

time of the packet

type

picture type

See also the -stats_enc options for an alternative way to show encoding statistics.

## 6 Examples# TOC

### 6.1 Video and Audio grabbing# TOC

If you specify the input format and device then ffmpeg can grab video and audio directly.

```
ffmpeg -f oss -i /dev/dsp -f video4linux2 -i /dev/video0 /tmp/out.mpg

```

Or with an ALSA audio source (mono input, card id 1) instead of OSS:

```
ffmpeg -f alsa -ac 1 -i hw:1 -f video4linux2 -i /dev/video0 /tmp/out.mpg

```

Note that you must activate the right video source and channel before launching ffmpeg with any TV viewer such as xawtv by Gerd Knorr. You also have to set the audio recording levels correctly with a standard mixer.

### 6.2 X11 grabbing# TOC

Grab the X11 display with ffmpeg via

```
ffmpeg -f x11grab -video_size cif -framerate 25 -i :0.0 /tmp/out.mpg

```

0.0 is display.screen number of your X11 server, same as the DISPLAY environment variable.

```
ffmpeg -f x11grab -video_size cif -framerate 25 -i :0.0+10,20 /tmp/out.mpg

```

0.0 is display.screen number of your X11 server, same as the DISPLAY environment variable. 10 is the x-offset and 20 the y-offset for the grabbing.

### 6.3 Video and Audio file format conversion# TOC

Any supported file format and protocol can serve as input to ffmpeg:

Examples:

- You can use YUV files as input:

```
ffmpeg -i /tmp/test%d.Y /tmp/out.mpg

```

It will use the files:

```
/tmp/test0.Y, /tmp/test0.U, /tmp/test0.V,
/tmp/test1.Y, /tmp/test1.U, /tmp/test1.V, etc...

```

The Y files use twice the resolution of the U and V files. They are raw files, without header. They can be generated by all decent video decoders. You must specify the size of the image with the -s option if ffmpeg cannot guess it.

- You can input from a raw YUV420P file:

```
ffmpeg -i /tmp/test.yuv /tmp/out.avi

```

test.yuv is a file containing raw YUV planar data. Each frame is composed of the Y plane followed by the U and V planes at half vertical and horizontal resolution.

- You can output to a raw YUV420P file:

```
ffmpeg -i mydivx.avi hugefile.yuv

```

- You can set several input files and output files:

```
ffmpeg -i /tmp/a.wav -s 640x480 -i /tmp/a.yuv /tmp/a.mpg

```

Converts the audio file a.wav and the raw YUV video file a.yuv to MPEG file a.mpg.

- You can also do audio and video conversions at the same time:

```
ffmpeg -i /tmp/a.wav -ar 22050 /tmp/a.mp2

```

Converts a.wav to MPEG audio at 22050 Hz sample rate.

- You can encode to several formats at the same time and define a mapping from input stream to output streams:

```
ffmpeg -i /tmp/a.wav -map 0:a -b:a 64k /tmp/a.mp2 -map 0:a -b:a 128k /tmp/b.mp2

```

Converts a.wav to a.mp2 at 64 kbits and to b.mp2 at 128 kbits. ’-map file:index’ specifies which input stream is used for each output stream, in the order of the definition of output streams.

- You can transcode decrypted VOBs:

```
ffmpeg -i snatch_1.vob -f avi -c:v mpeg4 -b:v 800k -g 300 -bf 2 -c:a libmp3lame -b:a 128k snatch.avi

```

This is a typical DVD ripping example; the input is a VOB file, the output an AVI file with MPEG-4 video and MP3 audio. Note that in this command we use B-frames so the MPEG-4 stream is DivX5 compatible, and GOP size is 300 which means one intra frame every 10 seconds for 29.97fps input video. Furthermore, the audio stream is MP3-encoded so you need to enable LAME support by passing --enable-libmp3lame to configure. The mapping is particularly useful for DVD transcoding to get the desired audio language.

NOTE: To see the supported input formats, use ffmpeg -demuxers.

- You can extract images from a video, or create a video from many images:
For extracting images from a video:

```
ffmpeg -i foo.avi -r 1 -s WxH -f image2 foo-%03d.jpeg

```

This will extract one video frame per second from the video and will output them in files named foo-001.jpeg, foo-002.jpeg, etc. Images will be rescaled to fit the new WxH values.

If you want to extract just a limited number of frames, you can use the above command in combination with the -frames:v or -t option, or in combination with -ss to start extracting from a certain point in time.

For creating a video from many images:

```
ffmpeg -f image2 -framerate 12 -i foo-%03d.jpeg -s WxH foo.avi

```

The syntax foo-%03d.jpeg specifies to use a decimal number composed of three digits padded with zeroes to express the sequence number. It is the same syntax supported by the C printf function, but only formats accepting a normal integer are suitable.

When importing an image sequence, -i also supports expanding shell-like wildcard patterns (globbing) internally, by selecting the image2-specific -pattern_type glob option.

For example, for creating a video from filenames matching the glob pattern foo-*.jpeg:

```
ffmpeg -f image2 -pattern_type glob -framerate 12 -i 'foo-*.jpeg' -s WxH foo.avi

```

- You can put many streams of the same type in the output:

```
ffmpeg -i test1.avi -i test2.avi -map 1:1 -map 1:0 -map 0:1 -map 0:0 -c copy -y test12.nut

```

The resulting output file test12.nut will contain the first four streams from the input files in reverse order.

- To force CBR video output:

```
ffmpeg -i myfile.avi -b 4000k -minrate 4000k -maxrate 4000k -bufsize 1835k out.m2v

```

- The four options lmin, lmax, mblmin and mblmax use ’lambda’ units, but you may use the QP2LAMBDA constant to easily convert from ’q’ units:

```
ffmpeg -i src.ext -lmax 21*QP2LAMBDA dst.ext

```

## 7 Syntax# TOC

This section documents the syntax and formats employed by the FFmpeg libraries and tools.

### 7.1 Quoting and escaping# TOC

FFmpeg adopts the following quoting and escaping mechanism, unless explicitly specified. The following rules are applied:

- ‘'’ and ‘\’ are special characters (respectively used for quoting and escaping). In addition to them, there might be other special characters depending on the specific syntax where the escaping and quoting are employed.

- A special character is escaped by prefixing it with a ‘\’.

- All characters enclosed between ‘''’ are included literally in the parsed string. The quote character ‘'’ itself cannot be quoted, so you may need to close the quote and escape it.

- Leading and trailing whitespaces, unless escaped or quoted, are removed from the parsed string.

Note that you may need to add a second level of escaping when using the command line or a script, which depends on the syntax of the adopted shell language.

The function av_get_token defined in libavutil/avstring.h can be used to parse a token quoted or escaped according to the rules defined above.

The tool tools/ffescape in the FFmpeg source tree can be used to automatically quote or escape a string in a script.

#### 7.1.1 Examples# TOC

- Escape the string Crime d'Amour containing the ' special character:

```
Crime d\'Amour

```

- The string above contains a quote, so the ' needs to be escaped when quoting it:

```
'Crime d'\''Amour'

```

- Include leading or trailing whitespaces using quoting:

```
'  this string starts and ends with whitespaces  '

```

- Escaping and quoting can be mixed together:

```
' The string '\'string\'' is a string '

```

- To include a literal ‘\’ you can use either escaping or quoting:

```
'c:\foo' can be written as c:\\foo

```

### 7.2 Date# TOC

The accepted syntax is:

```
[(YYYY-MM-DD|YYYYMMDD)[T|t| ]]((HH:MM:SS[.m...]]])|(HHMMSS[.m...]]]))[Z]
now

```

If the value is "now" it takes the current time.

Time is local time unless Z is appended, in which case it is interpreted as UTC. If the year-month-day part is not specified it takes the current year-month-day.

### 7.3 Time duration# TOC

There are two accepted syntaxes for expressing time duration.

```
[-][HH:]MM:SS[.m...]

```

HH expresses the number of hours, MM the number of minutes for a maximum of 2 digits, and SS the number of seconds for a maximum of 2 digits. The m at the end expresses decimal value for SS.

or

```
[-]S+[.m...][s|ms|us]

```

S expresses the number of seconds, with the optional decimal part m. The optional literal suffixes ‘s’, ‘ms’ or ‘us’ indicate to interpret the value as seconds, milliseconds or microseconds, respectively.

In both expressions, the optional ‘-’ indicates negative duration.

#### 7.3.1 Examples# TOC

The following examples are all valid time duration:

‘55’

55 seconds

‘0.2’

0.2 seconds

‘200ms’

200 milliseconds, that’s 0.2s

‘200000us’

200000 microseconds, that’s 0.2s

‘12:03:45’

12 hours, 03 minutes and 45 seconds

‘23.189’

23.189 seconds

### 7.4 Video size# TOC

Specify the size of the sourced video, it may be a string of the form widthxheight, or the name of a size abbreviation.

The following abbreviations are recognized:

‘ntsc’

720x480

‘pal’

720x576

‘qntsc’

352x240

‘qpal’

352x288

‘sntsc’

640x480

‘spal’

768x576

‘film’

352x240

‘ntsc-film’

352x240

‘sqcif’

128x96

‘qcif’

176x144

‘cif’

352x288

‘4cif’

704x576

‘16cif’

1408x1152

‘qqvga’

160x120

‘qvga’

320x240

‘vga’

640x480

‘svga’

800x600

‘xga’

1024x768

‘uxga’

1600x1200

‘qxga’

2048x1536

‘sxga’

1280x1024

‘qsxga’

2560x2048

‘hsxga’

5120x4096

‘wvga’

852x480

‘wxga’

1366x768

‘wsxga’

1600x1024

‘wuxga’

1920x1200

‘woxga’

2560x1600

‘wqsxga’

3200x2048

‘wquxga’

3840x2400

‘whsxga’

6400x4096

‘whuxga’

7680x4800

‘cga’

320x200

‘ega’

640x350

‘hd480’

852x480

‘hd720’

1280x720

‘hd1080’

1920x1080

‘2k’

2048x1080

‘2kflat’

1998x1080

‘2kscope’

2048x858

‘4k’

4096x2160

‘4kflat’

3996x2160

‘4kscope’

4096x1716

‘nhd’

640x360

‘hqvga’

240x160

‘wqvga’

400x240

‘fwqvga’

432x240

‘hvga’

480x320

‘qhd’

960x540

‘2kdci’

2048x1080

‘4kdci’

4096x2160

‘uhd2160’

3840x2160

‘uhd4320’

7680x4320

### 7.5 Video rate# TOC

Specify the frame rate of a video, expressed as the number of frames generated per second. It has to be a string in the format frame_rate_num/frame_rate_den, an integer number, a float number or a valid video frame rate abbreviation.

The following abbreviations are recognized:

‘ntsc’

30000/1001

‘pal’

25/1

‘qntsc’

30000/1001

‘qpal’

25/1

‘sntsc’

30000/1001

‘spal’

25/1

‘film’

24/1

‘ntsc-film’

24000/1001

### 7.6 Ratio# TOC

A ratio can be expressed as an expression, or in the form numerator:denominator.

Note that a ratio with infinite (1/0) or negative value is considered valid, so you should check on the returned value if you want to exclude those values.

The undefined value can be expressed using the "0:0" string.

### 7.7 Color# TOC

It can be the name of a color as defined below (case insensitive match) or a [0x|#]RRGGBB[AA] sequence, possibly followed by @ and a string representing the alpha component.

The alpha component may be a string composed by "0x" followed by an hexadecimal number or a decimal number between 0.0 and 1.0, which represents the opacity value (‘0x00’ or ‘0.0’ means completely transparent, ‘0xff’ or ‘1.0’ completely opaque). If the alpha component is not specified then ‘0xff’ is assumed.

The string ‘random’ will result in a random color.

The following names of colors are recognized:

‘AliceBlue’

0xF0F8FF

‘AntiqueWhite’

0xFAEBD7

‘Aqua’

0x00FFFF

‘Aquamarine’

0x7FFFD4

‘Azure’

0xF0FFFF

‘Beige’

0xF5F5DC

‘Bisque’

0xFFE4C4

‘Black’

0x000000

‘BlanchedAlmond’

0xFFEBCD

‘Blue’

0x0000FF

‘BlueViolet’

0x8A2BE2

‘Brown’

0xA52A2A

‘BurlyWood’

0xDEB887

‘CadetBlue’

0x5F9EA0

‘Chartreuse’

0x7FFF00

‘Chocolate’

0xD2691E

‘Coral’

0xFF7F50

‘CornflowerBlue’

0x6495ED

‘Cornsilk’

0xFFF8DC

‘Crimson’

0xDC143C

‘Cyan’

0x00FFFF

‘DarkBlue’

0x00008B

‘DarkCyan’

0x008B8B

‘DarkGoldenRod’

0xB8860B

‘DarkGray’

0xA9A9A9

‘DarkGreen’

0x006400

‘DarkKhaki’

0xBDB76B

‘DarkMagenta’

0x8B008B

‘DarkOliveGreen’

0x556B2F

‘Darkorange’

0xFF8C00

‘DarkOrchid’

0x9932CC

‘DarkRed’

0x8B0000

‘DarkSalmon’

0xE9967A

‘DarkSeaGreen’

0x8FBC8F

‘DarkSlateBlue’

0x483D8B

‘DarkSlateGray’

0x2F4F4F

‘DarkTurquoise’

0x00CED1

‘DarkViolet’

0x9400D3

‘DeepPink’

0xFF1493

‘DeepSkyBlue’

0x00BFFF

‘DimGray’

0x696969

‘DodgerBlue’

0x1E90FF

‘FireBrick’

0xB22222

‘FloralWhite’

0xFFFAF0

‘ForestGreen’

0x228B22

‘Fuchsia’

0xFF00FF

‘Gainsboro’

0xDCDCDC

‘GhostWhite’

0xF8F8FF

‘Gold’

0xFFD700

‘GoldenRod’

0xDAA520

‘Gray’

0x808080

‘Green’

0x008000

‘GreenYellow’

0xADFF2F

‘HoneyDew’

0xF0FFF0

‘HotPink’

0xFF69B4

‘IndianRed’

0xCD5C5C

‘Indigo’

0x4B0082

‘Ivory’

0xFFFFF0

‘Khaki’

0xF0E68C

‘Lavender’

0xE6E6FA

‘LavenderBlush’

0xFFF0F5

‘LawnGreen’

0x7CFC00

‘LemonChiffon’

0xFFFACD

‘LightBlue’

0xADD8E6

‘LightCoral’

0xF08080

‘LightCyan’

0xE0FFFF

‘LightGoldenRodYellow’

0xFAFAD2

‘LightGreen’

0x90EE90

‘LightGrey’

0xD3D3D3

‘LightPink’

0xFFB6C1

‘LightSalmon’

0xFFA07A

‘LightSeaGreen’

0x20B2AA

‘LightSkyBlue’

0x87CEFA

‘LightSlateGray’

0x778899

‘LightSteelBlue’

0xB0C4DE

‘LightYellow’

0xFFFFE0

‘Lime’

0x00FF00

‘LimeGreen’

0x32CD32

‘Linen’

0xFAF0E6

‘Magenta’

0xFF00FF

‘Maroon’

0x800000

‘MediumAquaMarine’

0x66CDAA

‘MediumBlue’

0x0000CD

‘MediumOrchid’

0xBA55D3

‘MediumPurple’

0x9370D8

‘MediumSeaGreen’

0x3CB371

‘MediumSlateBlue’

0x7B68EE

‘MediumSpringGreen’

0x00FA9A

‘MediumTurquoise’

0x48D1CC

‘MediumVioletRed’

0xC71585

‘MidnightBlue’

0x191970

‘MintCream’

0xF5FFFA

‘MistyRose’

0xFFE4E1

‘Moccasin’

0xFFE4B5

‘NavajoWhite’

0xFFDEAD

‘Navy’

0x000080

‘OldLace’

0xFDF5E6

‘Olive’

0x808000

‘OliveDrab’

0x6B8E23

‘Orange’

0xFFA500

‘OrangeRed’

0xFF4500

‘Orchid’

0xDA70D6

‘PaleGoldenRod’

0xEEE8AA

‘PaleGreen’

0x98FB98

‘PaleTurquoise’

0xAFEEEE

‘PaleVioletRed’

0xD87093

‘PapayaWhip’

0xFFEFD5

‘PeachPuff’

0xFFDAB9

‘Peru’

0xCD853F

‘Pink’

0xFFC0CB

‘Plum’

0xDDA0DD

‘PowderBlue’

0xB0E0E6

‘Purple’

0x800080

‘Red’

0xFF0000

‘RosyBrown’

0xBC8F8F

‘RoyalBlue’

0x4169E1

‘SaddleBrown’

0x8B4513

‘Salmon’

0xFA8072

‘SandyBrown’

0xF4A460

‘SeaGreen’

0x2E8B57

‘SeaShell’

0xFFF5EE

‘Sienna’

0xA0522D

‘Silver’

0xC0C0C0

‘SkyBlue’

0x87CEEB

‘SlateBlue’

0x6A5ACD

‘SlateGray’

0x708090

‘Snow’

0xFFFAFA

‘SpringGreen’

0x00FF7F

‘SteelBlue’

0x4682B4

‘Tan’

0xD2B48C

‘Teal’

0x008080

‘Thistle’

0xD8BFD8

‘Tomato’

0xFF6347

‘Turquoise’

0x40E0D0

‘Violet’

0xEE82EE

‘Wheat’

0xF5DEB3

‘White’

0xFFFFFF

‘WhiteSmoke’

0xF5F5F5

‘Yellow’

0xFFFF00

‘YellowGreen’

0x9ACD32

### 7.8 Channel Layout# TOC

A channel layout specifies the spatial disposition of the channels in a multi-channel audio stream. To specify a channel layout, FFmpeg makes use of a special syntax.

Individual channels are identified by an id, as given by the table below:

‘FL’

front left

‘FR’

front right

‘FC’

front center

‘LFE’

low frequency

‘BL’

back left

‘BR’

back right

‘FLC’

front left-of-center

‘FRC’

front right-of-center

‘BC’

back center

‘SL’

side left

‘SR’

side right

‘TC’

top center

‘TFL’

top front left

‘TFC’

top front center

‘TFR’

top front right

‘TBL’

top back left

‘TBC’

top back center

‘TBR’

top back right

‘DL’

downmix left

‘DR’

downmix right

‘WL’

wide left

‘WR’

wide right

‘SDL’

surround direct left

‘SDR’

surround direct right

‘LFE2’

low frequency 2

Standard channel layout compositions can be specified by using the following identifiers:

‘mono’

FC

‘stereo’

FL+FR

‘2.1’

FL+FR+LFE

‘3.0’

FL+FR+FC

‘3.0(back)’

FL+FR+BC

‘4.0’

FL+FR+FC+BC

‘quad’

FL+FR+BL+BR

‘quad(side)’

FL+FR+SL+SR

‘3.1’

FL+FR+FC+LFE

‘5.0’

FL+FR+FC+BL+BR

‘5.0(side)’

FL+FR+FC+SL+SR

‘4.1’

FL+FR+FC+LFE+BC

‘5.1’

FL+FR+FC+LFE+BL+BR

‘5.1(side)’

FL+FR+FC+LFE+SL+SR

‘6.0’

FL+FR+FC+BC+SL+SR

‘6.0(front)’

FL+FR+FLC+FRC+SL+SR

‘3.1.2’

FL+FR+FC+LFE+TFL+TFR

‘hexagonal’

FL+FR+FC+BL+BR+BC

‘6.1’

FL+FR+FC+LFE+BC+SL+SR

‘6.1’

FL+FR+FC+LFE+BL+BR+BC

‘6.1(front)’

FL+FR+LFE+FLC+FRC+SL+SR

‘7.0’

FL+FR+FC+BL+BR+SL+SR

‘7.0(front)’

FL+FR+FC+FLC+FRC+SL+SR

‘7.1’

FL+FR+FC+LFE+BL+BR+SL+SR

‘7.1(wide)’

FL+FR+FC+LFE+BL+BR+FLC+FRC

‘7.1(wide-side)’

FL+FR+FC+LFE+FLC+FRC+SL+SR

‘5.1.2’

FL+FR+FC+LFE+BL+BR+TFL+TFR

‘octagonal’

FL+FR+FC+BL+BR+BC+SL+SR

‘cube’

FL+FR+BL+BR+TFL+TFR+TBL+TBR

‘5.1.4’

FL+FR+FC+LFE+BL+BR+TFL+TFR+TBL+TBR

‘7.1.2’

FL+FR+FC+LFE+BL+BR+SL+SR+TFL+TFR

‘7.1.4’

FL+FR+FC+LFE+BL+BR+SL+SR+TFL+TFR+TBL+TBR

‘7.2.3’

FL+FR+FC+LFE+BL+BR+SL+SR+TFL+TFR+TBC+LFE2

‘9.1.4’

FL+FR+FC+LFE+BL+BR+FLC+FRC+SL+SR+TFL+TFR+TBL+TBR

‘9.1.6’

FL+FR+FC+LFE+BL+BR+FLC+FRC+SL+SR+TFL+TFR+TBL+TBR+TSL+TSR

‘hexadecagonal’

FL+FR+FC+BL+BR+BC+SL+SR+WL+WR+TBL+TBR+TBC+TFC+TFL+TFR

‘binaural’

BIL+BIR

‘downmix’

DL+DR

‘22.2’

FL+FR+FC+LFE+BL+BR+FLC+FRC+BC+SL+SR+TC+TFL+TFC+TFR+TBL+TBC+TBR+LFE2+TSL+TSR+BFC+BFL+BFR

A custom channel layout can be specified as a sequence of terms, separated by ’+’. Each term can be:

- the name of a single channel (e.g. ‘FL’, ‘FR’, ‘FC’, ‘LFE’, etc.), each optionally containing a custom name after a ’@’, (e.g. ‘FL@Left’, ‘FR@Right’, ‘FC@Center’, ‘LFE@Low_Frequency’, etc.)

A standard channel layout can be specified by the following:

- the name of a single channel (e.g. ‘FL’, ‘FR’, ‘FC’, ‘LFE’, etc.)

- the name of a standard channel layout (e.g. ‘mono’, ‘stereo’, ‘4.0’, ‘quad’, ‘5.0’, etc.)

- a number of channels, in decimal, followed by ’c’, yielding the default channel layout for that number of channels (see the function av_channel_layout_default). Note that not all channel counts have a default layout.

- a number of channels, in decimal, followed by ’C’, yielding an unknown channel layout with the specified number of channels. Note that not all channel layout specification strings support unknown channel layouts.

- a channel layout mask, in hexadecimal starting with "0x" (see the AV_CH_* macros in libavutil/channel_layout.h.

Before libavutil version 53 the trailing character "c" to specify a number of channels was optional, but now it is required, while a channel layout mask can also be specified as a decimal number (if and only if not followed by "c" or "C").

See also the function av_channel_layout_from_string defined in libavutil/channel_layout.h.

## 8 Expression Evaluation# TOC

When evaluating an arithmetic expression, FFmpeg uses an internal formula evaluator, implemented through the libavutil/eval.h interface.

An expression may contain unary, binary operators, constants, and functions.

Two expressions expr1 and expr2 can be combined to form another expression "expr1;expr2". expr1 and expr2 are evaluated in turn, and the new expression evaluates to the value of expr2.

The following binary operators are available: +, -, *, /, ^.

The following unary operators are available: +, -.

Some internal variables can be used to store and load intermediary results. They can be accessed using the ld and st functions with an index argument varying from 0 to 9 to specify which internal variable to access.

The following functions are available:

abs(x)

Compute absolute value of x.

acos(x)

Compute arccosine of x.

asin(x)

Compute arcsine of x.

atan(x)

Compute arctangent of x.

atan2(y, x)

Compute principal value of the arc tangent of y/x.

between(x, min, max)

Return 1 if x is greater than or equal to min and lesser than or equal to max, 0 otherwise.

bitand(x, y)

bitor(x, y)

Compute bitwise and/or operation on x and y.

The results of the evaluation of x and y are converted to integers before executing the bitwise operation.

Note that both the conversion to integer and the conversion back to floating point can lose precision. Beware of unexpected results for large numbers (usually 2^53 and larger).

ceil(expr)

Round the value of expression expr upwards to the nearest integer. For example, "ceil(1.5)" is "2.0".

clip(x, min, max)

Return the value of x clipped between min and max.

cos(x)

Compute cosine of x.

cosh(x)

Compute hyperbolic cosine of x.

eq(x, y)

Return 1 if x and y are equivalent, 0 otherwise.

exp(x)

Compute exponential of x (with base e, the Euler’s number).

floor(expr)

Round the value of expression expr downwards to the nearest integer. For example, "floor(-1.5)" is "-2.0".

gauss(x)

Compute Gauss function of x, corresponding to exp(-x*x/2) / sqrt(2*PI).

gcd(x, y)

Return the greatest common divisor of x and y. If both x and y are 0 or either or both are less than zero then behavior is undefined.

gt(x, y)

Return 1 if x is greater than y, 0 otherwise.

gte(x, y)

Return 1 if x is greater than or equal to y, 0 otherwise.

hypot(x, y)

This function is similar to the C function with the same name; it returns "sqrt(x*x + y*y)", the length of the hypotenuse of a right triangle with sides of length x and y, or the distance of the point (x, y) from the origin.

if(x, y)

Evaluate x, and if the result is non-zero return the result of the evaluation of y, return 0 otherwise.

if(x, y, z)

Evaluate x, and if the result is non-zero return the evaluation result of y, otherwise the evaluation result of z.

ifnot(x, y)

Evaluate x, and if the result is zero return the result of the evaluation of y, return 0 otherwise.

ifnot(x, y, z)

Evaluate x, and if the result is zero return the evaluation result of y, otherwise the evaluation result of z.

isinf(x)

Return 1.0 if x is +/-INFINITY, 0.0 otherwise.

isnan(x)

Return 1.0 if x is NAN, 0.0 otherwise.

ld(idx)

Load the value of the internal variable with index idx, which was previously stored with st(idx, expr). The function returns the loaded value.

lerp(x, y, z)

Return linear interpolation between x and y by amount of z.

log(x)

Compute natural logarithm of x.

lt(x, y)

Return 1 if x is lesser than y, 0 otherwise.

lte(x, y)

Return 1 if x is lesser than or equal to y, 0 otherwise.

max(x, y)

Return the maximum between x and y.

min(x, y)

Return the minimum between x and y.

mod(x, y)

Compute the remainder of division of x by y.

not(expr)

Return 1.0 if expr is zero, 0.0 otherwise.

pow(x, y)

Compute the power of x elevated y, it is equivalent to "(x)^(y)".

print(t)

print(t, l)

Print the value of expression t with loglevel l. If l is not specified then a default log level is used. Return the value of the expression printed.

random(idx)

Return a pseudo random value between 0.0 and 1.0. idx is the index of the internal variable used to save the seed/state, which can be previously stored with st(idx).

To initialize the seed, you need to store the seed value as a 64-bit unsigned integer in the internal variable with index idx.

For example, to store the seed with value 42 in the internal variable with index 0 and print a few random values:

```
st(0,42); print(random(0)); print(random(0)); print(random(0))

```

randomi(idx, min, max)

Return a pseudo random value in the interval between min and max. idx is the index of the internal variable which will be used to save the seed/state, which can be previously stored with st(idx).

To initialize the seed, you need to store the seed value as a 64-bit unsigned integer in the internal variable with index idx.

root(expr, max)

Find an input value for which the function represented by expr with argument ld(0) is 0 in the interval 0..max.

The expression in expr must denote a continuous function or the result is undefined.

ld(0) is used to represent the function input value, which means that the given expression will be evaluated multiple times with various input values that the expression can access through ld(0). When the expression evaluates to 0 then the corresponding input value will be returned.

round(expr)

Round the value of expression expr to the nearest integer. For example, "round(1.5)" is "2.0".

sgn(x)

Compute sign of x.

sin(x)

Compute sine of x.

sinh(x)

Compute hyperbolic sine of x.

sqrt(expr)

Compute the square root of expr. This is equivalent to "(expr)^.5".

squish(x)

Compute expression 1/(1 + exp(4*x)).

st(idx, expr)

Store the value of the expression expr in an internal variable. idx specifies the index of the variable where to store the value, and it is a value ranging from 0 to 9. The function returns the value stored in the internal variable.

The stored value can be retrieved with ld(var).

Note: variables are currently not shared between expressions.

tan(x)

Compute tangent of x.

tanh(x)

Compute hyperbolic tangent of x.

taylor(expr, x)

taylor(expr, x, idx)

Evaluate a Taylor series at x, given an expression representing the ld(idx)-th derivative of a function at 0.

When the series does not converge the result is undefined.

ld(idx) is used to represent the derivative order in expr, which means that the given expression will be evaluated multiple times with various input values that the expression can access through ld(idx). If idx is not specified then 0 is assumed.

Note, when you have the derivatives at y instead of 0, taylor(expr, x-y) can be used.

time(0)

Return the current (wallclock) time in seconds.

trunc(expr)

Round the value of expression expr towards zero to the nearest integer. For example, "trunc(-1.5)" is "-1.0".

while(cond, expr)

Evaluate expression expr while the expression cond is non-zero, and returns the value of the last expr evaluation, or NAN if cond was always false.

The following constants are available:

PI

area of the unit disc, approximately 3.14

E

exp(1) (Euler’s number), approximately 2.718

PHI

golden ratio (1+sqrt(5))/2, approximately 1.618

Assuming that an expression is considered "true" if it has a non-zero value, note that:

* works like AND

+ works like OR

For example the construct:

```
if (A AND B) then C

```

is equivalent to:

```
if(A*B, C)

```

In your C code, you can extend the list of unary and binary functions, and define recognized constants, so that they are available for your expressions.

The evaluator also recognizes the International System unit prefixes. If ’i’ is appended after the prefix, binary prefixes are used, which are based on powers of 1024 instead of powers of 1000. The ’B’ postfix multiplies the value by 8, and can be appended after a unit prefix or used alone. This allows using for example ’KB’, ’MiB’, ’G’ and ’B’ as number postfix.

The list of available International System prefixes follows, with indication of the corresponding powers of 10 and of 2.

y

10^-24 / 2^-80

z

10^-21 / 2^-70

a

10^-18 / 2^-60

f

10^-15 / 2^-50

p

10^-12 / 2^-40

n

10^-9 / 2^-30

u

10^-6 / 2^-20

m

10^-3 / 2^-10

c

10^-2

d

10^-1

h

10^2

k

10^3 / 2^10

K

10^3 / 2^10

M

10^6 / 2^20

G

10^9 / 2^30

T

10^12 / 2^40

P

10^15 / 2^50

E

10^18 / 2^60

Z

10^21 / 2^70

Y

10^24 / 2^80

## 9 Codec Options# TOC

libavcodec provides some generic global options, which can be set on all the encoders and decoders. In addition, each codec may support so-called private options, which are specific for a given codec.

Sometimes, a global option may only affect a specific kind of codec, and may be nonsensical or ignored by another, so you need to be aware of the meaning of the specified options. Also some options are meant only for decoding or encoding.

Options may be set by specifying -option value in the FFmpeg tools, or by setting the value explicitly in the AVCodecContext options or using the libavutil/opt.h API for programmatic use.

The list of supported options follow:

b integer (encoding,audio,video)

Set bitrate in bits/s. Default value is 200K.

ab integer (encoding,audio)

Set audio bitrate (in bits/s). Default value is 128K.

bt integer (encoding,video)

Set video bitrate tolerance (in bits/s). In 1-pass mode, bitrate tolerance specifies how far ratecontrol is willing to deviate from the target average bitrate value. This is not related to min/max bitrate. Lowering tolerance too much has an adverse effect on quality.

flags flags (decoding/encoding,audio,video,subtitles)

Set generic flags.

Possible values:

‘mv4’

Use four motion vector by macroblock (mpeg4).

‘qpel’

Use 1/4 pel motion compensation.

‘loop’

Use loop filter.

‘qscale’

Use fixed qscale.

‘pass1’

Use internal 2pass ratecontrol in first pass mode.

‘pass2’

Use internal 2pass ratecontrol in second pass mode.

‘gray’

Only decode/encode grayscale.

‘psnr’

Set error[?] variables during encoding.

‘truncated’

Input bitstream might be randomly truncated.

‘drop_changed’

Don’t output frames whose parameters differ from first decoded frame in stream. Error AVERROR_INPUT_CHANGED is returned when a frame is dropped.

‘ildct’

Use interlaced DCT.

‘low_delay’

Force low delay.

‘global_header’

Place global headers in extradata instead of every keyframe.

‘bitexact’

Only write platform-, build- and time-independent data. (except (I)DCT). This ensures that file and data checksums are reproducible and match between platforms. Its primary use is for regression testing.

‘aic’

Apply H263 advanced intra coding / mpeg4 ac prediction.

‘ilme’

Apply interlaced motion estimation.

‘cgop’

Use closed gop.

‘output_corrupt’

Output even potentially corrupted frames.

time_base rational number

Set codec time base.

It is the fundamental unit of time (in seconds) in terms of which frame timestamps are represented. For fixed-fps content, timebase should be 1 / frame_rate and timestamp increments should be identically 1.

g integer (encoding,video)

Set the group of picture (GOP) size. Default value is 12.

ar integer (decoding/encoding,audio)

Set audio sampling rate (in Hz).

ac integer (decoding/encoding,audio)

Set number of audio channels.

cutoff integer (encoding,audio)

Set cutoff bandwidth. (Supported only by selected encoders, see their respective documentation sections.)

frame_size integer (encoding,audio)

Set audio frame size.

Each submitted frame except the last must contain exactly frame_size samples per channel. May be 0 when the codec has CODEC_CAP_VARIABLE_FRAME_SIZE set, in that case the frame size is not restricted. It is set by some decoders to indicate constant frame size.

frame_number integer

Set the frame number.

delay integer

qcomp float (encoding,video)

Set video quantizer scale compression (VBR). It is used as a constant in the ratecontrol equation. Recommended range for default rc_eq: 0.0-1.0.

qblur float (encoding,video)

Set video quantizer scale blur (VBR).

qmin integer (encoding,video)

Set min video quantizer scale (VBR). Must be included between -1 and 69, default value is 2.

qmax integer (encoding,video)

Set max video quantizer scale (VBR). Must be included between -1 and 1024, default value is 31.

qdiff integer (encoding,video)

Set max difference between the quantizer scale (VBR).

bf integer (encoding,video)

Set max number of B frames between non-B-frames.

Must be an integer between -1 and 16. 0 means that B-frames are disabled. If a value of -1 is used, it will choose an automatic value depending on the encoder.

Default value is 0.

b_qfactor float (encoding,video)

Set qp factor between P and B frames.

codec_tag integer

bug flags (decoding,video)

Workaround not auto detected encoder bugs.

Possible values:

‘autodetect’

‘xvid_ilace’

Xvid interlacing bug (autodetected if fourcc==XVIX)

‘ump4’

(autodetected if fourcc==UMP4)

‘no_padding’

padding bug (autodetected)

‘amv’

‘qpel_chroma’

‘std_qpel’

old standard qpel (autodetected per fourcc/version)

‘qpel_chroma2’

‘direct_blocksize’

direct-qpel-blocksize bug (autodetected per fourcc/version)

‘edge’

edge padding bug (autodetected per fourcc/version)

‘hpel_chroma’

‘dc_clip’

‘ms’

Workaround various bugs in microsoft broken decoders.

‘trunc’

trancated frames

‘h264_dp_nnz’

H.264 nC derivation for partitioned slices, as done by JM rather than by 9.2.1 (autodetected)

strict integer (decoding/encoding,audio,video)

Specify how strictly to follow the standards.

Possible values:

‘very’

strictly conform to an older more strict version of the spec or reference software

‘strict’

strictly conform to all the things in the spec no matter what consequences

‘normal’

‘unofficial’

allow unofficial extensions

‘experimental’

allow non standardized experimental things, experimental (unfinished/work in progress/not well tested) decoders and encoders. Note: experimental decoders can pose a security risk, do not use this for decoding untrusted input.

b_qoffset float (encoding,video)

Set QP offset between P and B frames.

err_detect flags (decoding,audio,video)

Set error detection flags.

Possible values:

‘crccheck’

verify embedded CRCs

‘bitstream’

detect bitstream specification deviations

‘buffer’

detect improper bitstream length

‘explode’

abort decoding on minor error detection

‘ignore_err’

ignore decoding errors, and continue decoding. This is useful if you want to analyze the content of a video and thus want everything to be decoded no matter what. This option will not result in a video that is pleasing to watch in case of errors.

‘careful’

consider things that violate the spec and have not been seen in the wild as errors

‘compliant’

consider all spec non compliancies as errors

‘aggressive’

consider things that a sane encoder should not do as an error

has_b_frames integer

block_align integer

rc_override_count integer

maxrate integer (encoding,audio,video)

Set max bitrate tolerance (in bits/s). Requires bufsize to be set.

minrate integer (encoding,audio,video)

Set min bitrate tolerance (in bits/s). Most useful in setting up a CBR encode. It is of little use elsewise.

bufsize integer (encoding,audio,video)

Set ratecontrol buffer size (in bits).

i_qfactor float (encoding,video)

Set QP factor between P and I frames.

i_qoffset float (encoding,video)

Set QP offset between P and I frames.

dct integer (encoding,video)

Set DCT algorithm.

Possible values:

‘auto’

autoselect a good one (default)

‘fastint’

fast integer

‘int’

accurate integer

‘mmx’

‘altivec’

‘faan’

floating point AAN DCT

lumi_mask float (encoding,video)

Compress bright areas stronger than medium ones.

tcplx_mask float (encoding,video)

Set temporal complexity masking.

scplx_mask float (encoding,video)

Set spatial complexity masking.

p_mask float (encoding,video)

Set inter masking.

dark_mask float (encoding,video)

Compress dark areas stronger than medium ones.

idct integer (decoding/encoding,video)

Select IDCT implementation.

Possible values:

‘auto’

‘int’

‘simple’

‘simplemmx’

‘simpleauto’

Automatically pick a IDCT compatible with the simple one

‘arm’

‘altivec’

‘sh4’

‘simplearm’

‘simplearmv5te’

‘simplearmv6’

‘simpleneon’

‘xvid’

‘faani’

floating point AAN IDCT

slice_count integer

ec flags (decoding,video)

Set error concealment strategy.

Possible values:

‘guess_mvs’

iterative motion vector (MV) search (slow)

‘deblock’

use strong deblock filter for damaged MBs

‘favor_inter’

favor predicting from the previous frame instead of the current

bits_per_coded_sample integer

aspect rational number (encoding,video)

Set sample aspect ratio.

sar rational number (encoding,video)

Set sample aspect ratio. Alias to aspect.

debug flags (decoding/encoding,audio,video,subtitles)

Print specific debug info.

Possible values:

‘pict’

picture info

‘rc’

rate control

‘bitstream’

‘mb_type’

macroblock (MB) type

‘qp’

per-block quantization parameter (QP)

‘dct_coeff’

‘green_metadata’

display complexity metadata for the upcoming frame, GoP or for a given duration.

‘skip’

‘startcode’

‘er’

error recognition

‘mmco’

memory management control operations (H.264)

‘bugs’

‘buffers’

picture buffer allocations

‘thread_ops’

threading operations

‘nomc’

skip motion compensation

cmp integer (encoding,video)

Set full pel me compare function.

Possible values:

‘sad’

sum of absolute differences, fast (default)

‘sse’

sum of squared errors

‘satd’

sum of absolute Hadamard transformed differences

‘dct’

sum of absolute DCT transformed differences

‘psnr’

sum of squared quantization errors (avoid, low quality)

‘bit’

number of bits needed for the block

‘rd’

rate distortion optimal, slow

‘zero’

0

‘vsad’

sum of absolute vertical differences

‘vsse’

sum of squared vertical differences

‘nsse’

noise preserving sum of squared differences

‘w53’

5/3 wavelet, only used in snow

‘w97’

9/7 wavelet, only used in snow

‘dctmax’

‘chroma’

subcmp integer (encoding,video)

Set sub pel me compare function.

Possible values:

‘sad’

sum of absolute differences, fast (default)

‘sse’

sum of squared errors

‘satd’

sum of absolute Hadamard transformed differences

‘dct’

sum of absolute DCT transformed differences

‘psnr’

sum of squared quantization errors (avoid, low quality)

‘bit’

number of bits needed for the block

‘rd’

rate distortion optimal, slow

‘zero’

0

‘vsad’

sum of absolute vertical differences

‘vsse’

sum of squared vertical differences

‘nsse’

noise preserving sum of squared differences

‘w53’

5/3 wavelet, only used in snow

‘w97’

9/7 wavelet, only used in snow

‘dctmax’

‘chroma’

mbcmp integer (encoding,video)

Set macroblock compare function.

Possible values:

‘sad’

sum of absolute differences, fast (default)

‘sse’

sum of squared errors

‘satd’

sum of absolute Hadamard transformed differences

‘dct’

sum of absolute DCT transformed differences

‘psnr’

sum of squared quantization errors (avoid, low quality)

‘bit’

number of bits needed for the block

‘rd’

rate distortion optimal, slow

‘zero’

0

‘vsad’

sum of absolute vertical differences

‘vsse’

sum of squared vertical differences

‘nsse’

noise preserving sum of squared differences

‘w53’

5/3 wavelet, only used in snow

‘w97’

9/7 wavelet, only used in snow

‘dctmax’

‘chroma’

ildctcmp integer (encoding,video)

Set interlaced dct compare function.

Possible values:

‘sad’

sum of absolute differences, fast (default)

‘sse’

sum of squared errors

‘satd’

sum of absolute Hadamard transformed differences

‘dct’

sum of absolute DCT transformed differences

‘psnr’

sum of squared quantization errors (avoid, low quality)

‘bit’

number of bits needed for the block

‘rd’

rate distortion optimal, slow

‘zero’

0

‘vsad’

sum of absolute vertical differences

‘vsse’

sum of squared vertical differences

‘nsse’

noise preserving sum of squared differences

‘w53’

5/3 wavelet, only used in snow

‘w97’

9/7 wavelet, only used in snow

‘dctmax’

‘chroma’

dia_size integer (encoding,video)

Set diamond type & size for motion estimation.

‘(1024, INT_MAX)’

full motion estimation(slowest)

‘(768, 1024]’

umh motion estimation

‘(512, 768]’

hex motion estimation

‘(256, 512]’

l2s diamond motion estimation

‘[2,256]’

var diamond motion estimation

‘(-1, 2)’

small diamond motion estimation

‘-1’

funny diamond motion estimation

‘(INT_MIN, -1)’

sab diamond motion estimation

last_pred integer (encoding,video)

Set amount of motion predictors from the previous frame.

precmp integer (encoding,video)

Set pre motion estimation compare function.

Possible values:

‘sad’

sum of absolute differences, fast (default)

‘sse’

sum of squared errors

‘satd’

sum of absolute Hadamard transformed differences

‘dct’

sum of absolute DCT transformed differences

‘psnr’

sum of squared quantization errors (avoid, low quality)

‘bit’

number of bits needed for the block

‘rd’

rate distortion optimal, slow

‘zero’

0

‘vsad’

sum of absolute vertical differences

‘vsse’

sum of squared vertical differences

‘nsse’

noise preserving sum of squared differences

‘w53’

5/3 wavelet, only used in snow

‘w97’

9/7 wavelet, only used in snow

‘dctmax’

‘chroma’

pre_dia_size integer (encoding,video)

Set diamond type & size for motion estimation pre-pass.

subq integer (encoding,video)

Set sub pel motion estimation quality.

me_range integer (encoding,video)

Set limit motion vectors range (1023 for DivX player).

global_quality integer (encoding,audio,video)

slice_flags integer

mbd integer (encoding,video)

Set macroblock decision algorithm (high quality mode).

Possible values:

‘simple’

use mbcmp (default)

‘bits’

use fewest bits

‘rd’

use best rate distortion

rc_init_occupancy integer (encoding,video)

Set number of bits which should be loaded into the rc buffer before decoding starts.

flags2 flags (decoding/encoding,audio,video,subtitles)

Possible values:

‘fast’

Allow non spec compliant speedup tricks.

‘noout’

Skip bitstream encoding.

‘ignorecrop’

Ignore cropping information from sps.

‘local_header’

Place global headers at every keyframe instead of in extradata.

‘chunks’

Frame data might be split into multiple chunks.

‘showall’

Show all frames before the first keyframe.

‘export_mvs’

Export motion vectors into frame side-data (see AV_FRAME_DATA_MOTION_VECTORS) for codecs that support it. See also doc/examples/export_mvs.c.

‘skip_manual’

Do not skip samples and export skip information as frame side data.

‘ass_ro_flush_noop’

Do not reset ASS ReadOrder field on flush.

‘icc_profiles’

Generate/parse embedded ICC profiles from/to colorimetry tags.

‘fixed_frame_size’

Force audio encoders to use a fixed frame size.

export_side_data flags (decoding/encoding,audio,video,subtitles)

Possible values:

‘mvs’

Export motion vectors into frame side-data (see AV_FRAME_DATA_MOTION_VECTORS) for codecs that support it. See also doc/examples/export_mvs.c.

‘prft’

Export encoder Producer Reference Time into packet side-data (see AV_PKT_DATA_PRFT) for codecs that support it.

‘venc_params’

Export video encoding parameters through frame side data (see AV_FRAME_DATA_VIDEO_ENC_PARAMS) for codecs that support it. At present, those are H.264 and VP9.

‘film_grain’

Export film grain parameters through frame side data (see AV_FRAME_DATA_FILM_GRAIN_PARAMS). Supported at present by AV1 decoders.

‘enhancements’

Export picture enhancement metadata through frame side data, e.g. LCEVC (see AV_FRAME_DATA_LCEVC).

threads integer (decoding/encoding,video)

Set the number of threads to be used, in case the selected codec implementation supports multi-threading.

Possible values:

‘auto, 0’

automatically select the number of threads to set

Default value is ‘auto’.

dc integer (encoding,video)

Set intra_dc_precision.

nssew integer (encoding,video)

Set nsse weight.

skip_top integer (decoding,video)

Set number of macroblock rows at the top which are skipped.

skip_bottom integer (decoding,video)

Set number of macroblock rows at the bottom which are skipped.

profile integer (encoding,audio,video)

Set encoder codec profile. Default value is ‘unknown’. Encoder specific profiles are documented in the relevant encoder documentation.

level integer (encoding,audio,video)

Set the encoder level. This level depends on the specific codec, and might correspond to the profile level. It is set by default to ‘unknown’.

Possible values:

‘unknown’

lowres integer (decoding,audio,video)

Decode at 1= 1/2, 2=1/4, 3=1/8 resolutions.

mblmin integer (encoding,video)

Set min macroblock lagrange factor (VBR).

mblmax integer (encoding,video)

Set max macroblock lagrange factor (VBR).

skip_loop_filter integer (decoding,video)

skip_idct integer (decoding,video)

skip_pred integer (decoding,video)

skip_frame integer (decoding,video)

Make decoder discard processing depending on the frame type selected by the option value.

skip_loop_filter skips frame loop filtering, skip_idct skips frame IDCT/dequantization, skip_pred skips prediction (intra prediction and motion compensation), skip_frame skips decoding.

With both skip_pred and skip_idct set to ‘all’ the decoder may skip all pixel operations and output frames with undefined pixels but valid metadata, such as timestamps and frame types.

Possible values:

‘none’

Discard no frame.

‘default’

Discard useless frames like 0-sized frames.

‘noref’

Discard all non-reference frames.

‘bidir’

Discard all bidirectional frames.

‘nokey’

Discard all frames excepts keyframes.

‘nointra’

Discard all frames except I frames.

‘all’

Discard all frames.

Default value is ‘default’.

bidir_refine integer (encoding,video)

Refine the two motion vectors used in bidirectional macroblocks.

keyint_min integer (encoding,video)

Set minimum interval between IDR-frames.

refs integer (encoding,video)

Set reference frames to consider for motion compensation.

trellis integer (encoding,audio,video)

Set rate-distortion optimal quantization.

mv0_threshold integer (encoding,video)

compression_level integer (encoding,audio,video)

bits_per_raw_sample integer

channel_layout integer (decoding/encoding,audio)

See the Channel Layout section in the ffmpeg-utils(1) manual for the required syntax.

rc_max_vbv_use float (encoding,video)

rc_min_vbv_use float (encoding,video)

color_primaries integer (decoding/encoding,video)

Possible values:

‘bt709’

BT.709

‘bt470m’

BT.470 M

‘bt470bg’

BT.470 BG

‘smpte170m’

SMPTE 170 M

‘smpte240m’

SMPTE 240 M

‘film’

Film

‘bt2020’

BT.2020

‘smpte428’

‘smpte428_1’

SMPTE ST 428-1

‘smpte431’

SMPTE 431-2

‘smpte432’

SMPTE 432-1

‘jedec-p22’

JEDEC P22

color_trc integer (decoding/encoding,video)

Possible values:

‘bt709’

BT.709

‘gamma22’

BT.470 M

‘gamma28’

BT.470 BG

‘smpte170m’

SMPTE 170 M

‘smpte240m’

SMPTE 240 M

‘linear’

Linear

‘log’

‘log100’

Log

‘log_sqrt’

‘log316’

Log square root

‘iec61966_2_4’

‘iec61966-2-4’

IEC 61966-2-4

‘bt1361’

‘bt1361e’

BT.1361

‘iec61966_2_1’

‘iec61966-2-1’

IEC 61966-2-1

‘bt2020_10’

‘bt2020_10bit’

BT.2020 - 10 bit

‘bt2020_12’

‘bt2020_12bit’

BT.2020 - 12 bit

‘smpte2084’

SMPTE ST 2084

‘smpte428’

‘smpte428_1’

SMPTE ST 428-1

‘arib-std-b67’

ARIB STD-B67

colorspace integer (decoding/encoding,video)

Possible values:

‘rgb’

RGB

‘bt709’

BT.709

‘fcc’

FCC

‘bt470bg’

BT.470 BG

‘smpte170m’

SMPTE 170 M

‘smpte240m’

SMPTE 240 M

‘ycocg’

YCOCG

‘bt2020nc’

‘bt2020_ncl’

BT.2020 NCL

‘bt2020c’

‘bt2020_cl’

BT.2020 CL

‘smpte2085’

SMPTE 2085

‘chroma-derived-nc’

Chroma-derived NCL

‘chroma-derived-c’

Chroma-derived CL

‘ictcp’

ICtCp

color_range integer (decoding/encoding,video)

If used as input parameter, it serves as a hint to the decoder, which color_range the input has. Possible values:

‘tv’

‘mpeg’

‘limited’

MPEG (219*2^(n-8))

‘pc’

‘jpeg’

‘full’

JPEG (2^n-1)

chroma_sample_location integer (decoding/encoding,video)

Possible values:

‘left’

‘center’

‘topleft’

‘top’

‘bottomleft’

‘bottom’

alpha_mode integer (decoding/encoding,video)

Possible values:

‘premultiplied’

‘straight’

log_level_offset integer

Set the log level offset.

slices integer (encoding,video)

Number of slices, used in parallelized encoding.

thread_type flags (decoding/encoding,video)

Select which multithreading methods to use.

Use of ‘frame’ will increase decoding delay by one frame per thread, so clients which cannot provide future frames should not use it.

Possible values:

‘slice’

Decode more than one part of a single frame at once.

Multithreading using slices works only when the video was encoded with slices.

‘frame’

Decode more than one frame at once.

Default value is ‘slice+frame’.

audio_service_type integer (encoding,audio)

Set audio service type.

Possible values:

‘ma’

Main Audio Service

‘ef’

Effects

‘vi’

Visually Impaired

‘hi’

Hearing Impaired

‘di’

Dialogue

‘co’

Commentary

‘em’

Emergency

‘vo’

Voice Over

‘ka’

Karaoke

request_sample_fmt sample_fmt (decoding,audio)

Set sample format audio decoders should prefer. Default value is none.

pkt_timebase rational number

sub_charenc encoding (decoding,subtitles)

Set the input subtitles character encoding.

field_order field_order (video)

Set/override the field order of the video. Possible values:

‘progressive’

Progressive video

‘tt’

Interlaced video, top field coded and displayed first

‘bb’

Interlaced video, bottom field coded and displayed first

‘tb’

Interlaced video, top coded first, bottom displayed first

‘bt’

Interlaced video, bottom coded first, top displayed first

skip_alpha bool (decoding,video)

Set to 1 to disable processing alpha (transparency). This works like the ‘gray’ flag in the flags option which skips chroma information instead of alpha. Default is 0.

codec_whitelist list (input)

"," separated list of allowed decoders. By default all are allowed.

dump_separator string (input)

Separator used to separate the fields printed on the command line about the Stream parameters. For example, to separate the fields with newlines and indentation:

```
ffprobe -dump_separator "
                          "  -i ~/videos/matrixbench_mpeg2.mpg

```

max_pixels integer (decoding/encoding,video)

Maximum number of pixels per image. This value can be used to avoid out of memory failures due to large images.

apply_cropping bool (decoding,video)

Enable cropping if cropping parameters are multiples of the required alignment for the left and top parameters. If the alignment is not met the cropping will be partially applied to maintain alignment. Default is 1 (enabled). Note: The required alignment depends on if AV_CODEC_FLAG_UNALIGNED is set and the CPU. AV_CODEC_FLAG_UNALIGNED cannot be changed from the command line. Also hardware decoders will not apply left/top Cropping.

lcevc-dec-params string (decoding,video)

A :-separated list of key=value parameters passed to liblcevc-dec to initialize it.

## 10 Decoders# TOC

Decoders are configured elements in FFmpeg which allow the decoding of multimedia streams.

When you configure your FFmpeg build, all the supported native decoders are enabled by default. Decoders requiring an external library must be enabled manually via the corresponding --enable-lib option. You can list all available decoders using the configure option --list-decoders.

You can disable all the decoders with the configure option --disable-decoders and selectively enable / disable single decoders with the options --enable-decoder=DECODER / --disable-decoder=DECODER.

The option -decoders of the ff* tools will display the list of enabled decoders.

## 11 Video Decoders# TOC

A description of some of the currently available video decoders follows.

### 11.1 av1# TOC

AOMedia Video 1 (AV1) decoder.

#### 11.1.1 Options# TOC

operating_point

Select an operating point of a scalable AV1 bitstream (0 - 31). Default is 0.

### 11.2 hevc# TOC

HEVC (AKA ITU-T H.265 or ISO/IEC 23008-2) decoder.

The decoder supports MV-HEVC multiview streams with at most two views. Views to be output are selected by supplying a list of view IDs to the decoder (the view_ids option). This option may be set either statically before decoder init, or from the get_format() callback - useful for the case when the view count or IDs change dynamically during decoding.

Only the base layer is decoded by default.

Note that if you are using the ffmpeg CLI tool, you should be using view specifiers as documented in its manual, rather than the options documented here.

#### 11.2.1 Options# TOC

view_ids (MV-HEVC)

Specify a list of view IDs that should be output. This option can also be set to a single ’-1’, which will cause all views defined in the VPS to be decoded and output.

view_ids_available (MV-HEVC)

This option may be read by the caller to retrieve an array of view IDs available in the active VPS. The array is empty for single-layer video.

The value of this option is guaranteed to be accurate when read from the get_format() callback. It may also be set at other times (e.g. after opening the decoder), but the value is informational only and may be incorrect (e.g. when the stream contains multiple distinct VPS NALUs).

view_pos_available (MV-HEVC)

This option may be read by the caller to retrieve an array of view positions (left, right, or unspecified) available in the active VPS, as AVStereo3DView values. When the array is available, its elements apply to the corresponding elements of view_ids_available, i.e. view_pos_available[i] contains the position of view with ID view_ids_available[i].

Same validity restrictions as for view_ids_available apply to this option.

### 11.3 rawvideo# TOC

Raw video decoder.

This decoder decodes rawvideo streams.

#### 11.3.1 Options# TOC

top top_field_first

Specify the assumed field type of the input video.

-1

the video is assumed to be progressive (default)

0

bottom-field-first is assumed

1

top-field-first is assumed

### 11.4 libastcenc# TOC

ARM ASTC Encoder wrapper for decoding ASTC textures.

This decoder requires the Arm ASTC Encoder (astc-encoder) library version 5.4 or newer, installed as astcenc/astcenc.h next to a library that -lastcenc finds. Pass --enable-version3 together with --enable-libastcenc to configure.

The .astc header does not record the intended decoding profile. Individual blocks identify their endpoint encodings, but this does not establish the sRGB versus linear interpretation. The decoder therefore uses the container metadata or dec_profile: a KTX sRGB texture is decoded as ldr-srgb, while a KTX texture in the linear format is sampled with HDR precision (hdr-ldr-a, half-float output) because the linear GL internal format says nothing about LDR. A raw .astc file carries no profile at all, so it falls back to ldr-srgb; use dec_profile for a raw HDR image:

```
ffmpeg -dec_profile hdr-ldr-a -i input.astc output.png

```

#### 11.4.1 Options# TOC

dec_profile int

Color profile to decode with, overriding the container metadata. It must match the profile the texture was encoded with: astcenc substitutes a fixed magenta error color for blocks whose endpoints do not fit the selected profile. The values are ldr, ldr-srgb, hdr-ldr-a and hdr. Without this option the profile published by the container is used; a raw .astc stream, which publishes none, falls back to ldr-srgb.

### 11.5 libdav1d# TOC

dav1d AV1 decoder.

libdav1d allows libavcodec to decode the AOMedia Video 1 (AV1) codec. Requires the presence of the libdav1d headers and library during configuration. You need to explicitly configure the build with --enable-libdav1d.

#### 11.5.1 Options# TOC

The following options are supported by the libdav1d wrapper.

max_frame_delay

Set max amount of frames the decoder may buffer internally. The default value is 0 (autodetect).

filmgrain

Apply film grain to the decoded video if present in the bitstream. Defaults to the internal default of the library. This option is deprecated and will be removed in the future. See the global option export_side_data to export Film Grain parameters instead of applying it.

oppoint

Select an operating point of a scalable AV1 bitstream (0 - 31). Defaults to the internal default of the library.

alllayers

Output all spatial layers of a scalable AV1 bitstream. The default value is false.

### 11.6 libdavs2# TOC

AVS2-P2/IEEE1857.4 video decoder wrapper.

This decoder allows libavcodec to decode AVS2 streams with davs2 library.

### 11.7 libuavs3d# TOC

AVS3-P2/IEEE1857.10 video decoder.

libuavs3d allows libavcodec to decode AVS3 streams. Requires the presence of the libuavs3d headers and library during configuration. You need to explicitly configure the build with --enable-libuavs3d.

#### 11.7.1 Options# TOC

The following option is supported by the libuavs3d wrapper.

frame_threads

Set amount of frame threads to use during decoding. The default value is 0 (autodetect).

### 11.8 libxevd# TOC

eXtra-fast Essential Video Decoder (XEVD) MPEG-5 EVC decoder wrapper.

This decoder requires the presence of the libxevd headers and library during configuration. You need to explicitly configure the build with --enable-libxevd.

The xevd project website is at https://github.com/mpeg5/xevd.

#### 11.8.1 Options# TOC

The following options are supported by the libxevd wrapper. The xevd-equivalent options or values are listed in parentheses for easy migration.

To get a more accurate and extensive documentation of the libxevd options, invoke the command xevd_app --help or consult the libxevd documentation.

threads (threads)

Force to use a specific number of threads

### 11.9 QSV Decoders# TOC

The family of Intel QuickSync Video decoders (VC1, MPEG-2, H.264, HEVC, JPEG/MJPEG, VP8, VP9, AV1, VVC).

#### 11.9.1 Common Options# TOC

The following options are supported by all qsv decoders.

async_depth

Internal parallelization depth, the higher the value the higher the latency.

gpu_copy

A GPU-accelerated copy between video and system memory

‘default’

‘on’

‘off’

#### 11.9.2 HEVC Options# TOC

Extra options for hevc_qsv.

load_plugin

A user plugin to load in an internal session

‘none’

‘hevc_sw’

‘hevc_hw’

load_plugins

A :-separate list of hexadecimal plugin UIDs to load in an internal session

### 11.10 v210# TOC

Uncompressed 4:2:2 10-bit decoder.

#### 11.10.1 Options# TOC

custom_stride

Set the line size of the v210 data in bytes. The default value is 0 (autodetect). You can use the special -1 value for a strideless v210 as seen in BOXX files.

## 12 Audio Decoders# TOC

A description of some of the currently available audio decoders follows.

### 12.1 ac3# TOC

AC-3 audio decoder.

This decoder implements part of ATSC A/52:2010 and ETSI TS 102 366, as well as the undocumented RealAudio 3 (a.k.a. dnet).

#### 12.1.1 AC-3 Decoder Options# TOC

-drc_scale value

Dynamic Range Scale Factor. The factor to apply to dynamic range values from the AC-3 stream. This factor is applied exponentially. The default value is 1. There are 3 notable scale factor ranges:

drc_scale == 0

DRC disabled. Produces full range audio.

0 < drc_scale <= 1

DRC enabled. Applies a fraction of the stream DRC value. Audio reproduction is between full range and full compression.

drc_scale > 1

DRC enabled. Applies drc_scale asymmetrically. Loud sounds are fully compressed. Soft sounds are enhanced.

### 12.2 dca# TOC

DCA (DTS Coherent Acoustics) audio decoder, including the DTS-HD extensions.

#### 12.2.1 DCA Decoder Options# TOC

-downmix channel_layout

Request a smaller channel layout from the decoder: ‘stereo’, ‘5.0(side)’, ‘5.1(side)’ or ‘7.1’.

A DTS:X stream in the standard presentation decodes to 7.1.4 by default. Its four height channels are carried in an extension at the end of each lossless (XLL) frame, and the encoder also folds them into the 7.1 bed, so the decoder removes them from the bed when it outputs them. Requesting ‘7.1’ outputs the bed as coded instead, with the heights folded in, and so does every smaller layout. A ‘7.1’ request has no effect on other streams.

### 12.3 flac# TOC

FLAC audio decoder.

This decoder aims to implement the complete FLAC specification from Xiph.

#### 12.3.1 FLAC Decoder options# TOC

-use_buggy_lpc

The lavc FLAC encoder used to produce buggy streams with high lpc values (like the default value). This option makes it possible to decode such streams correctly by using lavc’s old buggy lpc logic for decoding.

### 12.4 ffwavesynth# TOC

Internal wave synthesizer.

This decoder generates wave patterns according to predefined sequences. Its use is purely internal and the format of the data it accepts is not publicly documented.

### 12.5 libgsm# TOC

libgsm decoder wrapper.

libgsm allows libavcodec to decode the GSM full rate audio codec. Requires the presence of the libgsm headers and library during configuration. You need to explicitly configure the build with --enable-libgsm.

This decoder supports both the ordinary GSM and the Microsoft variant.

### 12.6 libilbc# TOC

libilbc decoder wrapper.

libilbc allows libavcodec to decode the Internet Low Bitrate Codec (iLBC) audio codec. Requires the presence of the libilbc headers and library during configuration. You need to explicitly configure the build with --enable-libilbc.

#### 12.6.1 Options# TOC

The following option is supported by the libilbc wrapper.

enhance

Enable the enhancement of the decoded audio when set to 1. The default value is 0 (disabled).

### 12.7 libmpeghdec# TOC

libmpeghdec decoder wrapper.

libmpeghdec allows libmpeghdec to decode the MPEG-H 3D audio codec. Requires the presence of the libmpeghdec headers and library during configuration. You need to explicitly configure the build with --enable-libmpeghdec --enable-nonfree.

### 12.8 libopencore-amrnb# TOC

libopencore-amrnb decoder wrapper.

libopencore-amrnb allows libavcodec to decode the Adaptive Multi-Rate Narrowband audio codec. Using it requires the presence of the libopencore-amrnb headers and library during configuration. You need to explicitly configure the build with --enable-libopencore-amrnb.

An FFmpeg native decoder for AMR-NB exists, so users can decode AMR-NB without this library.

### 12.9 libopencore-amrwb# TOC

libopencore-amrwb decoder wrapper.

libopencore-amrwb allows libavcodec to decode the Adaptive Multi-Rate Wideband audio codec. Using it requires the presence of the libopencore-amrwb headers and library during configuration. You need to explicitly configure the build with --enable-libopencore-amrwb.

An FFmpeg native decoder for AMR-WB exists, so users can decode AMR-WB without this library.

### 12.10 libopus# TOC

libopus decoder wrapper.

libopus allows libavcodec to decode the Opus Interactive Audio Codec. Requires the presence of the libopus headers and library during configuration. You need to explicitly configure the build with --enable-libopus.

An FFmpeg native decoder for Opus exists, so users can decode Opus without this library.

### 12.11 pcm_dvda# TOC

PCM DVD-Audio decoder.

Decodes the LPCM variant stored in DVD-Audio AOB files. Unlike DVD-Video LPCM it supports sample rates up to 192 kHz and allows splitting the channels into two groups with different quantization.

## 13 Subtitles Decoders# TOC

### 13.1 libaribb24# TOC

ARIB STD-B24 caption decoder.

Implements profiles A and C of the ARIB STD-B24 standard.

#### 13.1.1 libaribb24 Decoder Options# TOC

-aribb24-base-path path

Sets the base path for the libaribb24 library. This is utilized for reading of configuration files (for custom unicode conversions), and for dumping of non-text symbols as images under that location.

Unset by default.

-aribb24-skip-ruby-text boolean

Tells the decoder wrapper to skip text blocks that contain half-height ruby text.

Enabled by default.

### 13.2 libaribcaption# TOC

Yet another ARIB STD-B24 caption decoder using external libaribcaption library.

Implements profiles A and C of the Japanese ARIB STD-B24 standard, Brazilian ABNT NBR 15606-1, and Philippines version of ISDB-T.

Requires the presence of the libaribcaption headers and library (https://github.com/xqq/libaribcaption) during configuration. You need to explicitly configure the build with --enable-libaribcaption. If both libaribb24 and libaribcaption are enabled, libaribcaption decoder precedes.

#### 13.2.1 libaribcaption Decoder Options# TOC

-sub_type subtitle_type

Specifies the format of the decoded subtitles.

‘bitmap’

Graphical image.

‘ass’

ASS formatted text.

‘text’

Simple text based output without formatting.

The default is ass as same as libaribb24 decoder. Some present players (e.g., mpv) expect ASS format for ARIB caption.

-caption_encoding encoding_scheme

Specifies the encoding scheme of input subtitle text.

‘auto’

Automatically detect text encoding (default).

‘jis’

8bit-char JIS encoding defined in ARIB STD B24. This encoding used in Japan for ISDB captions.

‘utf8’

UTF-8 encoding defined in ARIB STD B24. This encoding is used in Philippines for ISDB-T captions.

‘latin’

Latin character encoding defined in ABNT NBR 15606-1. This encoding is used in South America for SBTVD / ISDB-Tb captions.

-font font_name[,font_name2,...]

Specify comma-separated list of font family names to be used for bitmap or ass type subtitle rendering. Only first font name is used for ass type subtitle.

If not specified, use internally defined default font family.

-ass_single_rect boolean

ARIB STD-B24 specifies that some captions may be displayed at different positions at a time (multi-rectangle subtitle). Since some players (e.g., old mpv) can’t handle multiple ASS rectangles in a single AVSubtitle, or multiple ASS rectangles of indeterminate duration with the same start timestamp, this option can change the behavior so that all the texts are displayed in a single ASS rectangle.

The default is false.

If your player cannot handle AVSubtitles with multiple ASS rectangles properly, set this option to true or define ASS_SINGLE_RECT=1 to change default behavior at compilation.

-force_outline_text boolean

Specify whether always render outline text for all characters regardless of the indication by character style.

The default is false.

-outline_width number (0.0 - 3.0)

Specify width for outline text, in dots (relative).

The default is 1.5.

-ignore_background boolean

Specify whether to ignore background color rendering.

The default is false.

-ignore_ruby boolean

Specify whether to ignore rendering for ruby-like (furigana) characters.

The default is false.

-replace_drcs boolean

Specify whether to render replaced DRCS characters as Unicode characters.

The default is true.

-replace_msz_ascii boolean

Specify whether to replace MSZ (Middle Size; half width) fullwidth alphanumerics with halfwidth alphanumerics.

The default is true.

-replace_msz_japanese boolean

Specify whether to replace some MSZ (Middle Size; half width) fullwidth japanese special characters with halfwidth ones.

The default is true.

-replace_msz_glyph boolean

Specify whether to replace MSZ (Middle Size; half width) characters with halfwidth glyphs if the fonts supports it. This option works under FreeType or DirectWrite renderer with Adobe-Japan1 compliant fonts. e.g., IBM Plex Sans JP, Morisawa BIZ UDGothic, Morisawa BIZ UDMincho, Yu Gothic, Yu Mincho, and Meiryo.

The default is true.

-canvas_size image_size

Specify the resolution of the canvas to render subtitles to; usually, this should be frame size of input video. This only applies when -subtitle_type is set to bitmap.

The libaribcaption decoder assumes input frame size for bitmap rendering as below:

-  PROFILE_A : 1440 x 1080 with SAR (PAR) 4:3

-  PROFILE_C : 320 x 180 with SAR (PAR) 1:1

If actual frame size of input video does not match above assumption, the rendered captions may be distorted. To make the captions undistorted, add -canvas_size option to specify actual input video size.

Note that the -canvas_size option is not required for video with different size but same aspect ratio. In such cases, the caption will be stretched or shrunk to actual video size if -canvas_size option is not specified. If -canvas_size option is specified with different size, the caption will be stretched or shrunk as specified size with calculated SAR.

#### 13.2.2 libaribcaption decoder usage examples# TOC

Display MPEG-TS file with ARIB subtitle by ffplay tool:

```
ffplay -sub_type bitmap MPEG.TS

```

Display MPEG-TS file with input frame size 1920x1080 by ffplay tool:

```
ffplay -sub_type bitmap -canvas_size 1920x1080 MPEG.TS

```

Embed ARIB subtitle in transcoded video:

```
ffmpeg -sub_type bitmap -i src.m2t -filter_complex "[0:v][0:s]overlay" -vcodec h264 dest.mp4

```

### 13.3 dvbsub# TOC

#### 13.3.1 Options# TOC

compute_clut

-2

Compute clut once if no matching CLUT is in the stream.

-1

Compute clut if no matching CLUT is in the stream.

0

Never compute CLUT

1

Always compute CLUT and override the one provided in the stream.

dvb_substream

Selects the dvb substream, or all substreams if -1 which is default.

### 13.4 dvdsub# TOC

This codec decodes the bitmap subtitles used in DVDs; the same subtitles can also be found in VobSub file pairs and in some Matroska files.

#### 13.4.1 Options# TOC

palette

Specify the global palette used by the bitmaps. When stored in VobSub, the palette is normally specified in the index file; in Matroska, the palette is stored in the codec extra-data in the same format as in VobSub. In DVDs, the palette is stored in the IFO file, and therefore not available when reading from dumped VOB files.

The format for this option is a string containing 16 24-bits hexadecimal numbers (without 0x prefix) separated by commas, for example 0d00ee, ee450d, 101010, eaeaea, 0ce60b, ec14ed, ebff0b, 0d617a, 7b7b7b, d1d1d1, 7b2a0e, 0d950c, 0f007b, cf0dec, cfa80c, 7c127b.

ifo_palette

Specify the IFO file from which the global palette is obtained. (experimental)

forced_subs_only

Only decode subtitle entries marked as forced. Some titles have forced and non-forced subtitles in the same track. Setting this flag to 1 will only keep the forced subtitles. Default value is 0.

### 13.5 libzvbi-teletext# TOC

Libzvbi allows libavcodec to decode DVB teletext pages and DVB teletext subtitles. Requires the presence of the libzvbi headers and library during configuration. You need to explicitly configure the build with --enable-libzvbi.

#### 13.5.1 Options# TOC

txt_page

List of teletext page numbers to decode. Pages that do not match the specified list are dropped. You may use the special * string to match all pages, or subtitle to match all subtitle pages. Default value is *.

txt_default_region

Set default character set used for decoding, a value between 0 and 87 (see ETS 300 706, Section 15, Table 32). Default value is -1, which does not override the libzvbi default. This option is needed for some legacy level 1.0 transmissions which cannot signal the proper charset.

txt_chop_top

Discards the top teletext line. Default value is 1.

txt_format

Specifies the format of the decoded subtitles.

bitmap

The default format, you should use this for teletext pages, because certain graphics and colors cannot be expressed in simple text or even ASS.

text

Simple text based output without formatting.

ass

Formatted ASS output, subtitle pages and teletext pages are returned in different styles, subtitle pages are stripped down to text, but an effort is made to keep the text alignment and the formatting.

txt_left

X offset of generated bitmaps, default is 0.

txt_top

Y offset of generated bitmaps, default is 0.

txt_chop_spaces

Chops leading and trailing spaces and removes empty lines from the generated text. This option is useful for teletext based subtitles where empty spaces may be present at the start or at the end of the lines or empty lines may be present between the subtitle lines because of double-sized teletext characters. Default value is 1.

txt_duration

Sets the display duration of the decoded teletext pages or subtitles in milliseconds. Default value is -1 which means infinity or until the next subtitle event comes.

txt_transparent

Force transparent background of the generated teletext bitmaps. Default value is 0 which means an opaque background.

txt_opacity

Sets the opacity (0-255) of the teletext background. If txt_transparent is not set, it only affects characters between a start box and an end box, typically subtitles. Default value is 0 if txt_transparent is set, 255 otherwise.

## 14 Encoders# TOC

Encoders are configured elements in FFmpeg which allow the encoding of multimedia streams.

When you configure your FFmpeg build, all the supported native encoders are enabled by default. Encoders requiring an external library must be enabled manually via the corresponding --enable-lib option. You can list all available encoders using the configure option --list-encoders.

You can disable all the encoders with the configure option --disable-encoders and selectively enable / disable single encoders with the options --enable-encoder=ENCODER / --disable-encoder=ENCODER.

The option -encoders of the ff* tools will display the list of enabled encoders.

## 15 Audio Encoders# TOC

A description of some of the currently available audio encoders follows.

### 15.1 aac# TOC

Advanced Audio Coding (AAC) encoder.

This encoder is the default AAC encoder, natively implemented into FFmpeg.

#### 15.1.1 Options# TOC

b

Set bit rate in bits/s. Setting this automatically activates constant bit rate (CBR) mode. If this option is unspecified it is set to 128kbps.

q

Set quality for variable bit rate (VBR) mode. This option is valid only using the ffmpeg command-line tool. For library interface users, use global_quality.

With the default ‘nmr’ coder, VBR holds a constant noise-to-mask target and lets the bitrate follow the content. Higher values are finer: 1 lands near 128 kbps for typical stereo music, and each doubling of the value raises the rate by roughly a third; values above about 6 make no further difference. A quality setting takes precedence over b and aac_rc.

cutoff

Set cutoff frequency. If unspecified will allow the encoder to dynamically adjust the cutoff to improve clarity on low bitrates.

aac_coder

Set AAC encoder coding method. Possible values:

‘twoloop’

Two loop searching (TLS) method. This is the default method.

This method first sets quantizers depending on band thresholds and then tries to find an optimal combination by adding or subtracting a specific value from all quantizers and adjusting some individual quantizer a little. Will tune itself based on whether aac_is, aac_ms and aac_pns are enabled.

‘anmr’

Average noise to mask ratio (ANMR) trellis-based solution.

This is an experimental coder which currently produces a lower quality, is more unstable and is slower than the default twoloop coder but has potential. Currently has no support for the aac_is or aac_pns options. Not currently recommended.

‘fast’

Constant quantizer method.

Uses a cheaper version of twoloop algorithm that doesn’t try to do as many clever adjustments. Worse with low bitrates (less than 64kbps), but is better and much faster at higher bitrates.

aac_rc

Rate-control mode of the ‘nmr’ coder when a bitrate is set with b (other coders ignore it; q takes precedence). Possible values:

‘cbr’

Constant bitrate within the decoder’s bit reservoir. This is the default.

‘abr’

Average bitrate: a constant-quality target, as in VBR, whose set-point a slow servo moves to meet b over the length of the stream. Local quality stays constant, so short files and individual passages can deviate from the requested rate; the average converges over minutes rather than seconds. Below roughly 56 kbps stereo the rate lands above the request; use ‘cbr’ there.

aac_ms

Sets mid/side coding mode. The default value of "auto" will automatically use M/S with bands which will benefit from such coding. Can be forced for all bands using the value "enable", which is mainly useful for debugging or disabled using "disable".

aac_is

Sets intensity stereo coding tool usage. By default, it’s enabled and will automatically toggle IS for similar pairs of stereo bands if it’s beneficial. Can be disabled for debugging by setting the value to "disable".

aac_pns

Uses perceptual noise substitution to replace low entropy high frequency bands with imperceptible white noise during the decoding process. By default, it’s enabled, but can be disabled for debugging purposes by using "disable".

aac_tns

Enables the use of a multitap FIR filter which spans through the high frequency bands to hide quantization noise during the encoding process and is reverted by the decoder. As well as decreasing unpleasant artifacts in the high range this also reduces the entropy in the high bands and allows for more bits to be used by the mid-low bands. By default it’s enabled but can be disabled for debugging by setting the option to "disable".

aac_ltp

Enables the use of the long term prediction extension which increases coding efficiency in very low bandwidth situations such as encoding of voice or solo piano music by extending constant harmonic peaks in bands throughout frames. This option is implied by profile:a aac_low. Use in conjunction with -ar to decrease the samplerate.

profile

Sets the encoding profile, possible values:

‘aac_low’

The default, AAC "Low-complexity" profile. Is the most compatible and produces decent quality.

‘mpeg2_aac_low’

Equivalent to -profile:a aac_low -aac_pns 0. PNS was introduced with the MPEG4 specifications.

‘aac_ltp’

Long term prediction profile, is enabled by and will enable the aac_ltp option. Introduced in MPEG4.

If this option is unspecified it is set to ‘aac_low’.

### 15.2 ac3 and ac3_fixed# TOC

AC-3 audio encoders.

These encoders implement part of ATSC A/52:2010 and ETSI TS 102 366.

The ac3 encoder uses floating-point math, while the ac3_fixed encoder only uses fixed-point integer math. This does not mean that one is always faster, just that one or the other may be better suited to a particular system. The ac3_fixed encoder is not the default codec for any of the output formats, so it must be specified explicitly using the option -acodec ac3_fixed in order to use it.

#### 15.2.1 AC-3 Metadata# TOC

The AC-3 metadata options are used to set parameters that describe the audio, but in most cases do not affect the audio encoding itself. Some of the options do directly affect or influence the decoding and playback of the resulting bitstream, while others are just for informational purposes. A few of the options will add bits to the output stream that could otherwise be used for audio data, and will thus affect the quality of the output. Those will be indicated accordingly with a note in the option list below.

These parameters are described in detail in several publicly-available documents.

- A/52:2010 - Digital Audio Compression (AC-3) (E-AC-3) Standard

- A/54 - Guide to the Use of the ATSC Digital Television Standard

- Dolby Metadata Guide

- Dolby Digital Professional Encoding Guidelines

#### 15.2.1.1 Metadata Control Options# TOC

-per_frame_metadata boolean

Allow Per-Frame Metadata. Specifies if the encoder should check for changing metadata for each frame.

0

The metadata values set at initialization will be used for every frame in the stream. (default)

1

Metadata values can be changed before encoding each frame.

#### 15.2.1.2 Downmix Levels# TOC

-center_mixlev level

Center Mix Level. The amount of gain the decoder should apply to the center channel when downmixing to stereo. This field will only be written to the bitstream if a center channel is present. The value is specified as a scale factor. There are 3 valid values:

0.707

Apply -3dB gain

0.595

Apply -4.5dB gain (default)

0.500

Apply -6dB gain

-surround_mixlev level

Surround Mix Level. The amount of gain the decoder should apply to the surround channel(s) when downmixing to stereo. This field will only be written to the bitstream if one or more surround channels are present. The value is specified as a scale factor. There are 3 valid values:

0.707

Apply -3dB gain

0.500

Apply -6dB gain (default)

0.000

Silence Surround Channel(s)

#### 15.2.1.3 Audio Production Information# TOC

Audio Production Information is optional information describing the mixing environment. Either none or both of the fields are written to the bitstream.

-mixing_level number

Mixing Level. Specifies peak sound pressure level (SPL) in the production environment when the mix was mastered. Valid values are 80 to 111, or -1 for unknown or not indicated. The default value is -1, but that value cannot be used if the Audio Production Information is written to the bitstream. Therefore, if the room_type option is not the default value, the mixing_level option must not be -1.

-room_type type

Room Type. Describes the equalization used during the final mixing session at the studio or on the dubbing stage. A large room is a dubbing stage with the industry standard X-curve equalization; a small room has flat equalization. This field will not be written to the bitstream if both the mixing_level option and the room_type option have the default values.

0

notindicated

Not Indicated (default)

1

large

Large Room

2

small

Small Room

#### 15.2.1.4 Other Metadata Options# TOC

-copyright boolean

Copyright Indicator. Specifies whether a copyright exists for this audio.

0

off

No Copyright Exists (default)

1

on

Copyright Exists

-dialnorm value

Dialogue Normalization. Indicates how far the average dialogue level of the program is below digital 100% full scale (0 dBFS). This parameter determines a level shift during audio reproduction that sets the average volume of the dialogue to a preset level. The goal is to match volume level between program sources. A value of -31dB will result in no volume level change, relative to the source volume, during audio reproduction. Valid values are whole numbers in the range -31 to -1, with -31 being the default.

-dsur_mode mode

Dolby Surround Mode. Specifies whether the stereo signal uses Dolby Surround (Pro Logic). This field will only be written to the bitstream if the audio stream is stereo. Using this option does NOT mean the encoder will actually apply Dolby Surround processing.

0

notindicated

Not Indicated (default)

1

off

Not Dolby Surround Encoded

2

on

Dolby Surround Encoded

-original boolean

Original Bit Stream Indicator. Specifies whether this audio is from the original source and not a copy.

0

off

Not Original Source

1

on

Original Source (default)

#### 15.2.2 Extended Bitstream Information# TOC

The extended bitstream options are part of the Alternate Bit Stream Syntax as specified in Annex D of the A/52:2010 standard. It is grouped into 2 parts. If any one parameter in a group is specified, all values in that group will be written to the bitstream. Default values are used for those that are written but have not been specified. If the mixing levels are written, the decoder will use these values instead of the ones specified in the center_mixlev and surround_mixlev options if it supports the Alternate Bit Stream Syntax.

#### 15.2.2.1 Extended Bitstream Information - Part 1# TOC

-dmix_mode mode

Preferred Stereo Downmix Mode. Allows the user to select either Lt/Rt (Dolby Surround) or Lo/Ro (normal stereo) as the preferred stereo downmix mode.

0

notindicated

Not Indicated (default)

1

ltrt

Lt/Rt Downmix Preferred

2

loro

Lo/Ro Downmix Preferred

-ltrt_cmixlev level

Lt/Rt Center Mix Level. The amount of gain the decoder should apply to the center channel when downmixing to stereo in Lt/Rt mode.

1.414

Apply +3dB gain

1.189

Apply +1.5dB gain

1.000

Apply 0dB gain

0.841

Apply -1.5dB gain

0.707

Apply -3.0dB gain

0.595

Apply -4.5dB gain (default)

0.500

Apply -6.0dB gain

0.000

Silence Center Channel

-ltrt_surmixlev level

Lt/Rt Surround Mix Level. The amount of gain the decoder should apply to the surround channel(s) when downmixing to stereo in Lt/Rt mode.

0.841

Apply -1.5dB gain

0.707

Apply -3.0dB gain

0.595

Apply -4.5dB gain

0.500

Apply -6.0dB gain (default)

0.000

Silence Surround Channel(s)

-loro_cmixlev level

Lo/Ro Center Mix Level. The amount of gain the decoder should apply to the center channel when downmixing to stereo in Lo/Ro mode.

1.414

Apply +3dB gain

1.189

Apply +1.5dB gain

1.000

Apply 0dB gain

0.841

Apply -1.5dB gain

0.707

Apply -3.0dB gain

0.595

Apply -4.5dB gain (default)

0.500

Apply -6.0dB gain

0.000

Silence Center Channel

-loro_surmixlev level

Lo/Ro Surround Mix Level. The amount of gain the decoder should apply to the surround channel(s) when downmixing to stereo in Lo/Ro mode.

0.841

Apply -1.5dB gain

0.707

Apply -3.0dB gain

0.595

Apply -4.5dB gain

0.500

Apply -6.0dB gain (default)

0.000

Silence Surround Channel(s)

#### 15.2.2.2 Extended Bitstream Information - Part 2# TOC

-dsurex_mode mode

Dolby Surround EX Mode. Indicates whether the stream uses Dolby Surround EX (7.1 matrixed to 5.1). Using this option does NOT mean the encoder will actually apply Dolby Surround EX processing.

0

notindicated

Not Indicated (default)

1

on

Dolby Surround EX Off

2

off

Dolby Surround EX On

-dheadphone_mode mode

Dolby Headphone Mode. Indicates whether the stream uses Dolby Headphone encoding (multi-channel matrixed to 2.0 for use with headphones). Using this option does NOT mean the encoder will actually apply Dolby Headphone processing.

0

notindicated

Not Indicated (default)

1

on

Dolby Headphone Off

2

off

Dolby Headphone On

-ad_conv_type type

A/D Converter Type. Indicates whether the audio has passed through HDCD A/D conversion.

0

standard

Standard A/D Converter (default)

1

hdcd

HDCD A/D Converter

#### 15.2.3 Other AC-3 Encoding Options# TOC

-stereo_rematrixing boolean

Stereo Rematrixing. Enables/Disables use of rematrixing for stereo input. This is an optional AC-3 feature that increases quality by selectively encoding the left/right channels as mid/side. This option is enabled by default, and it is highly recommended that it be left as enabled except for testing purposes.

cutoff frequency

Set lowpass cutoff frequency. If unspecified, the encoder selects a default determined by various other encoding parameters.

#### 15.2.4 Floating-Point-Only AC-3 Encoding Options# TOC

These options are only valid for the floating-point encoder and do not exist for the fixed-point encoder due to the corresponding features not being implemented in fixed-point.

-channel_coupling boolean

Enables/Disables use of channel coupling, which is an optional AC-3 feature that increases quality by combining high frequency information from multiple channels into a single channel. The per-channel high frequency information is sent with less accuracy in both the frequency and time domains. This allows more bits to be used for lower frequencies while preserving enough information to reconstruct the high frequencies. This option is enabled by default for the floating-point encoder and should generally be left as enabled except for testing purposes or to increase encoding speed.

-1

auto

Selected by Encoder (default)

0

off

Disable Channel Coupling

1

on

Enable Channel Coupling

-cpl_start_band number

Coupling Start Band. Sets the channel coupling start band, from 1 to 15. If a value higher than the bandwidth is used, it will be reduced to 1 less than the coupling end band. If auto is used, the start band will be determined by the encoder based on the bit rate, sample rate, and channel layout. This option has no effect if channel coupling is disabled.

-1

auto

Selected by Encoder (default)

### 15.3 flac# TOC

FLAC (Free Lossless Audio Codec) Encoder

#### 15.3.1 Options# TOC

The following options are supported by FFmpeg’s flac encoder.

compression_level

Sets the compression level, which chooses defaults for many other options if they are not set explicitly. Valid values are from 0 to 12, 5 is the default.

frame_size

Sets the size of the frames in samples per channel.

lpc_coeff_precision

Sets the LPC coefficient precision, valid values are from 1 to 15, 15 is the default.

lpc_type

Sets the first stage LPC algorithm

‘none’

LPC is not used

‘fixed’

fixed LPC coefficients

‘levinson’

‘cholesky’

lpc_passes

Number of passes to use for Cholesky factorization during LPC analysis

min_partition_order

The minimum partition order

max_partition_order

The maximum partition order

prediction_order_method

‘estimation’

‘2level’

‘4level’

‘8level’

‘search’

Bruteforce search

‘log’

ch_mode

Channel mode

‘auto’

The mode is chosen automatically for each frame

‘indep’

Channels are independently coded

‘left_side’

‘right_side’

‘mid_side’

exact_rice_parameters

Chooses if rice parameters are calculated exactly or approximately. if set to 1 then they are chosen exactly, which slows the code down slightly and improves compression slightly.

multi_dim_quant

Multi Dimensional Quantization. If set to 1 then a 2nd stage LPC algorithm is applied after the first stage to finetune the coefficients. This is quite slow and slightly improves compression.

### 15.4 opus# TOC

Opus encoder.

This is a native FFmpeg encoder for the Opus format. Currently, it’s in development and only implements the CELT part of the codec. Its quality is usually worse and at best is equal to the libopus encoder.

#### 15.4.1 Options# TOC

b

Set bit rate in bits/s. If unspecified it uses the number of channels and the layout to make a good guess.

opus_delay

Sets the maximum delay in milliseconds. Lower delays than 20ms will very quickly decrease quality.

### 15.5 libfdk_aac# TOC

libfdk-aac AAC (Advanced Audio Coding) encoder wrapper.

The libfdk-aac library is based on the Fraunhofer FDK AAC code from the Android project.

Requires the presence of the libfdk-aac headers and library during configuration. You need to explicitly configure the build with --enable-libfdk-aac. The library is also incompatible with GPL, so if you allow the use of GPL, you should configure with --enable-gpl --enable-nonfree --enable-libfdk-aac.

This encoder has support for the AAC-HE profiles.

VBR encoding, enabled through the vbr or flags +qscale options, is experimental and only works with some combinations of parameters.

Support for encoding 7.1 audio is only available with libfdk-aac 0.1.3 or higher.

For more information see the fdk-aac project at http://sourceforge.net/p/opencore-amr/fdk-aac/.

#### 15.5.1 Options# TOC

The following options are mapped on the shared FFmpeg codec options.

b

Set bit rate in bits/s. If the bitrate is not explicitly specified, it is automatically set to a suitable value depending on the selected profile.

In case VBR mode is enabled the option is ignored.

ar

Set audio sampling rate (in Hz).

channels

Set the number of audio channels.

flags +qscale

Enable fixed quality, VBR (Variable Bit Rate) mode. Note that VBR is implicitly enabled when the vbr value is positive.

cutoff

Set cutoff frequency. If not specified (or explicitly set to 0) it will use a value automatically computed by the library. Default value is 0.

profile

Set audio profile.

The following profiles are recognized:

‘aac_low’

Low Complexity AAC (LC)

‘aac_he’

High Efficiency AAC (HE-AAC)

‘aac_he_v2’

High Efficiency AAC version 2 (HE-AACv2)

‘aac_ld’

Low Delay AAC (LD)

‘aac_eld’

Enhanced Low Delay AAC (ELD)

If not specified it is set to ‘aac_low’.

The following are private options of the libfdk_aac encoder.

afterburner

Enable afterburner feature if set to 1, disabled if set to 0. This improves the quality but also the required processing power.

Default value is 1.

eld_sbr

Enable SBR (Spectral Band Replication) for ELD if set to 1, disabled if set to 0.

Default value is 0.

eld_v2

Enable ELDv2 (LD-MPS extension for ELD stereo signals) for ELDv2 if set to 1, disabled if set to 0.

Note that option is available when fdk-aac version (AACENCODER_LIB_VL0.AACENCODER_LIB_VL1.AACENCODER_LIB_VL2) > (4.0.0).

Default value is 0.

signaling

Set SBR/PS signaling style.

It can assume one of the following values:

‘default’

choose signaling implicitly (explicit hierarchical by default, implicit if global header is disabled)

‘implicit’

implicit backwards compatible signaling

‘explicit_sbr’

explicit SBR, implicit PS signaling

‘explicit_hierarchical’

explicit hierarchical signaling

Default value is ‘default’.

latm

Output LATM/LOAS encapsulated data if set to 1, disabled if set to 0.

Default value is 0.

header_period

Set StreamMuxConfig and PCE repetition period (in frames) for sending in-band configuration buffers within LATM/LOAS transport layer.

Must be a 16-bits non-negative integer.

Default value is 0.

vbr

Set VBR mode, from 1 to 5. 1 is lowest quality (though still pretty good) and 5 is highest quality. A value of 0 will disable VBR, and CBR (Constant Bit Rate) is enabled.

Currently only the ‘aac_low’ profile supports VBR encoding.

VBR modes 1-5 correspond to roughly the following average bit rates:

‘1’

32 kbps/channel

‘2’

40 kbps/channel

‘3’

48-56 kbps/channel

‘4’

64 kbps/channel

‘5’

about 80-96 kbps/channel

Default value is 0.

frame_length

Set the audio frame length in samples. Default value is the internal default of the library. Refer to the library’s documentation for information about supported values.

#### 15.5.2 Examples# TOC

- Use ffmpeg to convert an audio file to VBR AAC in an M4A (MP4) container:

```
ffmpeg -i input.wav -codec:a libfdk_aac -vbr 3 output.m4a

```

- Use ffmpeg to convert an audio file to CBR 64k kbps AAC, using the High-Efficiency AAC profile:

```
ffmpeg -i input.wav -c:a libfdk_aac -profile:a aac_he -b:a 64k output.m4a

```

### 15.6 libfdk-xhe-aac# TOC

libfdk-xhe-aac (Extended High-Efficiency Advanced Audio Coding) encoder wrapper.

The libfdk-xhe-aac library is based on the Fraunhofer FDK Extended High Efficiency AAC Encoder Software code from the Android project.

Requires the presence of the libfdk-xhe-aac headers and library during configuration. You need to explicitly configure the build with --enable-libfdk-xhe-aac. The library is also incompatible with GPL, so if you allow the use of GPL, you should configure with --enable-gpl --enable-nonfree --enable-libfdk-xhe-aac.

#### 15.6.1 Options# TOC

The following are private options of the libfdk_xhe_aac encoder.

vbr

Set VBR mode, from 0 to 6. 0 is lowest quality and 6 is highest quality. A value of -1 will disable VBR, and CBR (Constant Bit Rate) is enabled.

If not set, the default is CBR.

live_loudness_level

Set the expected loudness level of the stream, between -31 and -10 dB LUFS. Defaults to -24 dB LUFS if not set.

rap_length

The duration between encoded Random Access Points in the bitstream.

stream_id

A unique ID of the encoded stream within an adaptation set. The ID is embedded into the encoded bitstream.

If not set, the encoder tries to generate a hopefully unique ID for the stream.

In order to do two pass encoding (where the first pass measures the loudness of the stream, and the second pass uses that information for accurately preserving the dynamics of the stream), invoke ffmpeg e.g. like this:

```
ffmpeg -i input.wav -c:a libfdk_xhe_aac -pass 1 -f null -
ffmpeg -i input.wav -c:a libfdk_xhe_aac -pass 2 out.m4a

```

Doing two pass encoding is the recommended way to use the libfdk_xhe_aac encoder.

### 15.7 liblc3# TOC

liblc3 LC3 (Low Complexity Communication Codec) encoder wrapper.

Requires the presence of the liblc3 headers and library during configuration. You need to explicitly configure the build with --enable-liblc3.

This encoder has support for the Bluetooth SIG LC3 codec for the LE Audio protocol, and the following features of LC3plus:

- Frame duration of 2.5 and 5ms.

- High-Resolution mode, 48 KHz, and 96 kHz sampling rates.

For more information see the liblc3 project at https://github.com/google/liblc3.

#### 15.7.1 Options# TOC

The following options are mapped on the shared FFmpeg codec options.

b bitrate

Set the bit rate in bits/s. This will determine the fixed size of the encoded frames, for a selected frame duration.

ar frequency

Set the audio sampling rate (in Hz).

channels

Set the number of audio channels.

frame_duration

Set the audio frame duration in milliseconds. Default value is 10ms. Allowed frame durations are 2.5ms, 5ms, 7.5ms and 10ms. LC3 (Bluetooth LE Audio), allows 7.5ms and 10ms; and LC3plus 2.5ms, 5ms and 10ms.

The 10ms frame duration is available in LC3 and LC3 plus standard. In this mode, the produced bitstream can be referenced either as LC3 or LC3plus.

high_resolution boolean

Enable the high-resolution mode if set to 1. The high-resolution mode is available with all LC3plus frame durations and for a sampling rate of 48 KHz, and 96 KHz.

The encoder automatically turns off this mode at lower sampling rates and activates it at 96 KHz.

This mode should be preferred at high bitrates. In this mode, the audio bandwidth is always up to the Nyquist frequency, compared to LC3 at 48 KHz, which limits the bandwidth to 20 KHz.

### 15.8 libmp3lame# TOC

LAME (Lame Ain’t an MP3 Encoder) MP3 encoder wrapper.

Requires the presence of the libmp3lame headers and library during configuration. You need to explicitly configure the build with --enable-libmp3lame.

See libshine for a fixed-point MP3 encoder, although with a lower quality.

#### 15.8.1 Options# TOC

The following options are supported by the libmp3lame wrapper. The lame-equivalent of the options are listed in parentheses.

b (-b)

Set bitrate expressed in bits/s for CBR or ABR. LAME bitrate is expressed in kilobits/s.

q (-V)

Set constant quality setting for VBR. This option is valid only using the ffmpeg command-line tool. For library interface users, use global_quality.

compression_level (-q)

Set algorithm quality. Valid arguments are integers in the 0-9 range, with 0 meaning highest quality but slowest, and 9 meaning fastest while producing the worst quality.

cutoff (--lowpass)

Set lowpass cutoff frequency. If unspecified, the encoder dynamically adjusts the cutoff.

strict (--strictly-enforce-ISO)

Enable LAME’s strict ISO buffer constraints when set to ‘strict’ or ‘very’. Other values leave LAME’s default buffer constraints unchanged. This can improve compatibility with some decoders, at the cost of reduced bit reservoir usage.

reservoir

Enable use of bit reservoir when set to 1. Default value is 1. LAME has this enabled by default, but can be overridden by use --nores option.

joint_stereo (-m j)

Enable the encoder to use (on a frame by frame basis) either L/R stereo or mid/side stereo. Default value is 1.

abr (--abr)

Enable the encoder to use ABR when set to 1. The lame --abr sets the target bitrate, while this options only tells FFmpeg to use ABR still relies on b to set bitrate.

copyright (-c)

Set MPEG audio copyright flag when set to 1. The default value is 0 (disabled).

original (-o)

Set MPEG audio original flag when set to 1. The default value is 1 (enabled).

### 15.9 libopencore-amrnb# TOC

OpenCORE Adaptive Multi-Rate Narrowband encoder.

Requires the presence of the libopencore-amrnb headers and library during configuration. You need to explicitly configure the build with --enable-libopencore-amrnb --enable-version3.

This is a mono-only encoder. Officially it only supports 8000Hz sample rate, but you can override it by setting strict to ‘unofficial’ or lower.

#### 15.9.1 Options# TOC

b

Set bitrate in bits per second. Only the following bitrates are supported, otherwise libavcodec will round to the nearest valid bitrate.

4750

5150

5900

6700

7400

7950

10200

12200

dtx

Allow discontinuous transmission (generate comfort noise) when set to 1. The default value is 0 (disabled).

### 15.10 libopus# TOC

libopus Opus Interactive Audio Codec encoder wrapper.

Requires the presence of the libopus headers and library during configuration. You need to explicitly configure the build with --enable-libopus.

#### 15.10.1 Option Mapping# TOC

Most libopus options are modelled after the opusenc utility from opus-tools. The following is an option mapping chart describing options supported by the libopus wrapper, and their opusenc-equivalent in parentheses.

b (bitrate)

Set the bit rate in bits/s. FFmpeg’s b option is expressed in bits/s, while opusenc’s bitrate in kilobits/s.

vbr (vbr, hard-cbr, and cvbr)

Set VBR mode. The FFmpeg vbr option has the following valid arguments, with the opusenc equivalent options in parentheses:

‘off (hard-cbr)’

Use constant bit rate encoding.

‘on (vbr)’

Use variable bit rate encoding (the default).

‘constrained (cvbr)’

Use constrained variable bit rate encoding.

compression_level (comp)

Set encoding algorithm complexity. Valid options are integers in the 0-10 range. 0 gives the fastest encodes but lower quality, while 10 gives the highest quality but slowest encoding. The default is 10.

frame_duration (framesize)

Set maximum frame size, or duration of a frame in milliseconds. The argument must be exactly the following: 2.5, 5, 10, 20, 40, 60. Smaller frame sizes achieve lower latency but less quality at a given bitrate. Sizes greater than 20ms are only interesting at fairly low bitrates. The default is 20ms.

packet_loss (expect-loss)

Set expected packet loss percentage. The default is 0.

fec (n/a)

Enable inband forward error correction. packet_loss must be non-zero to take advantage - frequency of FEC ’side-data’ is proportional to expected packet loss. Default is disabled.

application (N.A.)

Set intended application type. Valid options are listed below:

‘voip’

Favor improved speech intelligibility.

‘audio’

Favor faithfulness to the input (the default).

‘lowdelay’

Restrict to only the lowest delay modes by disabling voice-optimized modes.

cutoff (N.A.)

Set cutoff bandwidth in Hz. The argument must be exactly one of the following: 4000, 6000, 8000, 12000, or 20000, corresponding to narrowband, mediumband, wideband, super wideband, and fullband respectively. The default is 0 (cutoff disabled). Note that libopus forces a wideband cutoff for bitrates < 15 kbps, unless CELT-only (application set to ‘lowdelay’) mode is used.

mapping_family (mapping_family)

Set channel mapping family to be used by the encoder. The default value of -1 uses mapping family 0 for mono and stereo inputs, and mapping family 1 otherwise. The default also disables the surround masking and LFE bandwidth optimizations in libopus, and requires that the input contains 8 channels or fewer.

Other values include 0 for mono and stereo, 1 for surround sound with masking and LFE bandwidth optimizations, and 255 for independent streams with an unspecified channel layout.

dtx (N.A.)

Allow discontinuous transmission when set to 1. The default value is 0 (disabled).

apply_phase_inv (N.A.) (requires libopus >= 1.2)

If set to 0, disables the use of phase inversion for intensity stereo, improving the quality of mono downmixes, but slightly reducing normal stereo quality. The default is 1 (phase inversion enabled).

### 15.11 libshine# TOC

Shine Fixed-Point MP3 encoder wrapper.

Shine is a fixed-point MP3 encoder. It has a far better performance on platforms without an FPU, e.g. armel CPUs, and some phones and tablets. However, as it is more targeted on performance than quality, it is not on par with LAME and other production-grade encoders quality-wise. Also, according to the project’s homepage, this encoder may not be free of bugs as the code was written a long time ago and the project was dead for at least 5 years.

This encoder only supports stereo and mono input. This is also CBR-only.

The original project (last updated in early 2007) is at http://sourceforge.net/projects/libshine-fxp/. We only support the updated fork by the Savonet/Liquidsoap project at https://github.com/savonet/shine.

Requires the presence of the libshine headers and library during configuration. You need to explicitly configure the build with --enable-libshine.

See also libmp3lame.

#### 15.11.1 Options# TOC

The following options are supported by the libshine wrapper. The shineenc-equivalent of the options are listed in parentheses.

b (-b)

Set bitrate expressed in bits/s for CBR. shineenc -b option is expressed in kilobits/s.

### 15.12 libtwolame# TOC

TwoLAME MP2 encoder wrapper.

Requires the presence of the libtwolame headers and library during configuration. You need to explicitly configure the build with --enable-libtwolame.

#### 15.12.1 Options# TOC

The following options are supported by the libtwolame wrapper. The twolame-equivalent options follow the FFmpeg ones and are in parentheses.

b (-b)

Set bitrate expressed in bits/s for CBR. twolame b option is expressed in kilobits/s. Default value is 128k.

q (-V)

Set quality for experimental VBR support. Maximum value range is from -50 to 50, useful range is from -10 to 10. The higher the value, the better the quality. This option is valid only using the ffmpeg command-line tool. For library interface users, use global_quality.

mode (--mode)

Set the mode of the resulting audio. Possible values:

‘auto’

Choose mode automatically based on the input. This is the default.

‘stereo’

Stereo

‘joint_stereo’

Joint stereo

‘dual_channel’

Dual channel

‘mono’

Mono

psymodel (--psyc-mode)

Set psychoacoustic model to use in encoding. The argument must be an integer between -1 and 4, inclusive. The higher the value, the better the quality. The default value is 3.

energy_levels (--energy)

Enable energy levels extensions when set to 1. The default value is 0 (disabled).

error_protection (--protect)

Enable CRC error protection when set to 1. The default value is 0 (disabled).

copyright (--copyright)

Set MPEG audio copyright flag when set to 1. The default value is 0 (disabled).

original (--original)

Set MPEG audio original flag when set to 1. The default value is 0 (disabled).

### 15.13 libvo-amrwbenc# TOC

VisualOn Adaptive Multi-Rate Wideband encoder.

Requires the presence of the libvo-amrwbenc headers and library during configuration. You need to explicitly configure the build with --enable-libvo-amrwbenc --enable-version3.

This is a mono-only encoder. Officially it only supports 16000Hz sample rate, but you can override it by setting strict to ‘unofficial’ or lower.

#### 15.13.1 Options# TOC

b

Set bitrate in bits/s. Only the following bitrates are supported, otherwise libavcodec will round to the nearest valid bitrate.

‘6600’

‘8850’

‘12650’

‘14250’

‘15850’

‘18250’

‘19850’

‘23050’

‘23850’

dtx

Allow discontinuous transmission (generate comfort noise) when set to 1. The default value is 0 (disabled).

### 15.14 libvorbis# TOC

libvorbis encoder wrapper.

Requires the presence of the libvorbisenc headers and library during configuration. You need to explicitly configure the build with --enable-libvorbis.

#### 15.14.1 Options# TOC

The following options are supported by the libvorbis wrapper. The oggenc-equivalent of the options are listed in parentheses.

To get a more accurate and extensive documentation of the libvorbis options, consult the libvorbisenc’s and oggenc’s documentations. See http://xiph.org/vorbis/, http://wiki.xiph.org/Vorbis-tools, and oggenc(1).

b (-b)

Set bitrate expressed in bits/s for ABR. oggenc -b is expressed in kilobits/s.

q (-q)

Set constant quality setting for VBR. The value should be a float number in the range of -1.0 to 10.0. The higher the value, the better the quality. The default value is ‘3.0’.

This option is valid only using the ffmpeg command-line tool. For library interface users, use global_quality.

cutoff (--advanced-encode-option lowpass_frequency=N)

Set cutoff bandwidth in Hz, a value of 0 disables cutoff. oggenc’s related option is expressed in kHz. The default value is ‘0’ (cutoff disabled).

minrate (-m)

Set minimum bitrate expressed in bits/s. oggenc -m is expressed in kilobits/s.

maxrate (-M)

Set maximum bitrate expressed in bits/s. oggenc -M is expressed in kilobits/s. This only has effect on ABR mode.

iblock (--advanced-encode-option impulse_noisetune=N)

Set noise floor bias for impulse blocks. The value is a float number from -15.0 to 0.0. A negative bias instructs the encoder to pay special attention to the crispness of transients in the encoded audio. The tradeoff for better transient response is a higher bitrate.

### 15.15 mjpeg# TOC

Motion JPEG encoder.

#### 15.15.1 Options# TOC

huffman

Set the huffman encoding strategy. Possible values:

‘default’

Use the default huffman tables. This is the default strategy.

‘optimal’

Compute and use optimal huffman tables.

intra_dc_precision integer

Set the precision of the DC coefficient minus 8. Valid range is 0 to 3. Higher values quantize DC more finely as the DC entry of the written quantization table is 8 >> intra_dc_precision so 3 gives a DC quantizer of 1. Default is 0 which keeps the previous fixed DC quantizer of 8.

Combined with -q:v 1 and an intra_matrix of all 8s, a value of 3 produces a quantization table of all ones.

### 15.16 wavpack# TOC

WavPack lossless audio encoder.

#### 15.16.1 Options# TOC

The equivalent options for wavpack command line utility are listed in parentheses.

#### 15.16.1.1 Shared options# TOC

The following shared options are effective for this encoder. Only special notes about this particular encoder will be documented here. For the general meaning of the options, see the Codec Options chapter.

frame_size (--blocksize)

For this encoder, the range for this option is between 128 and 131072. Default is automatically decided based on sample rate and number of channel.

For the complete formula of calculating default, see libavcodec/wavpackenc.c.

compression_level (-f, -h, -hh, and -x)

#### 15.16.1.2 Private options# TOC

joint_stereo (-j)

Set whether to enable joint stereo. Valid values are:

‘on (1)’

Force mid/side audio encoding.

‘off (0)’

Force left/right audio encoding.

‘auto’

Let the encoder decide automatically.

optimize_mono

Set whether to enable optimization for mono. This option is only effective for non-mono streams. Available values:

‘on’

enabled

‘off’

disabled

## 16 Video Encoders# TOC

A description of some of the currently available video encoders follows.

### 16.1 a64_multi, a64_multi5# TOC

A64 / Commodore 64 multicolor charset encoder. a64_multi5 is extended with 5th color (colram).

### 16.2 Cinepak# TOC

Cinepak aka CVID encoder. Compatible with Windows 3.1 and vintage MacOS.

#### 16.2.1 Options# TOC

g integer

Keyframe interval. A keyframe is inserted at least every -g frames, sometimes sooner.

q:v integer

Quality factor. Lower is better. Higher gives lower bitrate. The following table lists bitrates when encoding akiyo_cif.y4m for various values of -q:v with -g 100:

-q:v 1 1918 kb/s

-q:v 2 1735 kb/s

-q:v 4 1500 kb/s

-q:v 10 1041 kb/s

-q:v 20 826 kb/s

-q:v 40 553 kb/s

-q:v 100 394 kb/s

-q:v 200 312 kb/s

-q:v 400 266 kb/s

-q:v 1000 237 kb/s

max_extra_cb_iterations integer

Max extra codebook recalculation passes, more is better and slower.

skip_empty_cb boolean

Avoid wasting bytes, ignore vintage MacOS decoder.

max_strips integer

min_strips integer

The minimum and maximum number of strips to use. Wider range sometimes improves quality. More strips is generally better quality but costs more bits. Fewer strips tend to yield more keyframes. Vintage compatible is 1..3.

strip_number_adaptivity integer

How much number of strips is allowed to change between frames. Higher is better but slower.

### 16.3 ffv1# TOC

FFv1 Encoder

#### 16.3.1 Options# TOC

The following options are supported by FFmpeg’s FFv1 encoder.

context

Sets the context size, 0 (default) is small, 1 is big, 2 is minimal. The minimal context set compresses better when coding many slices, as each slice has too little data for larger context sets to adapt to.

coder

Set the coder,

‘rice’

Golomb rice coder

‘range_def’

Range coder with default table

‘range_tab’

Range coder with custom table

slicecrc

-1 (default, automatic), 1 use crc with zero initial and final state, 2 use crc with non zero initial and final state

qtable

‘default’

default, automatic

‘8bit’

use 8bit default

‘greater8bit’

use >8bit default

remap_optimizer

0 - 5, default 3, how much effort the encoder puts into optimizing the remap table.

### 16.4 GIF# TOC

GIF image/animation encoder.

#### 16.4.1 Options# TOC

gifflags integer

Sets the flags used for GIF encoding.

offsetting

Enables picture offsetting.

Default is enabled.

transdiff

Enables transparency detection between frames.

Default is enabled.

gifimage integer

Enables encoding one full GIF image per frame, rather than an animated GIF.

Default value is 0.

global_palette integer

Writes a palette to the global GIF header where feasible.

If disabled, every frame will always have a palette written, even if there is a global palette supplied.

Default value is 1.

### 16.5 Hap# TOC

Vidvox Hap video encoder.

#### 16.5.1 Options# TOC

format integer

Specifies the Hap format to encode.

hap

hap_alpha

hap_q

Default value is hap.

chunks integer

Specifies the number of chunks to split frames into, between 1 and 64. This permits multithreaded decoding of large frames, potentially at the cost of data-rate. The encoder may modify this value to divide frames evenly.

Default value is 1.

compressor integer

Specifies the second-stage compressor to use. If set to none, chunks will be limited to 1, as chunked uncompressed frames offer no benefit.

none

snappy

Default value is snappy.

### 16.6 jpeg2000# TOC

The native jpeg 2000 encoder is lossy by default, the -q:v option can be used to set the encoding quality. Lossless encoding can be selected with -pred 1.

#### 16.6.1 Options# TOC

format integer

Can be set to either j2k or jp2 (the default) that makes it possible to store non-rgb pix_fmts.

tile_width integer

Sets tile width. Range is 1 to 1073741824. Default is 256.

tile_height integer

Sets tile height. Range is 1 to 1073741824. Default is 256.

pred integer

Allows setting the discrete wavelet transform (DWT) type

dwt97int (Lossy)

dwt53 (Lossless)

Default is dwt97int

sop boolean

Enable this to add SOP marker at the start of each packet. Disabled by default.

eph boolean

Enable this to add EPH marker at the end of each packet header. Disabled by default.

prog integer

Sets the progression order to be used by the encoder. Possible values are:

lrcp

rlcp

rpcl

pcrl

cprl

Set to lrcp by default.

layer_rates string

By default, when this option is not used, compression is done using the quality metric. This option allows for compression using compression ratio. The compression ratio for each level could be specified. The compression ratio of a layer l species the what ratio of total file size is contained in the first l layers.

Example usage:

```
ffmpeg -i input.bmp -c:v jpeg2000 -layer_rates "100,10,1" output.j2k

```

This would compress the image to contain 3 layers, where the data contained in the first layer would be compressed by 1000 times, compressed by 100 in the first two layers, and shall contain all data while using all 3 layers.

### 16.7 librav1e# TOC

rav1e AV1 encoder wrapper.

Requires the presence of the rav1e headers and library during configuration. You need to explicitly configure the build with --enable-librav1e.

#### 16.7.1 Options# TOC

qmax

Sets the maximum quantizer to use when using bitrate mode.

qmin

Sets the minimum quantizer to use when using bitrate mode.

qp

Uses quantizer mode to encode at the given quantizer (0-255).

speed

Selects the speed preset (0-10) to encode with.

tiles

Selects how many tiles to encode with.

tile-rows

Selects how many rows of tiles to encode with.

tile-columns

Selects how many columns of tiles to encode with.

rav1e-params

Set rav1e options using a list of key=value pairs separated by ":". See rav1e --help for a list of options.

For example to specify librav1e encoding options with -rav1e-params:

```
ffmpeg -i input -c:v librav1e -b:v 500K -rav1e-params speed=5:low_latency=true output.mp4

```

### 16.8 libaom-av1# TOC

libaom AV1 encoder wrapper.

Requires the presence of the libaom headers and library during configuration. You need to explicitly configure the build with --enable-libaom.

#### 16.8.1 Options# TOC

The wrapper supports the following standard libavcodec options:

b

Set bitrate target in bits/second. By default this will use variable-bitrate mode. If maxrate and minrate are also set to the same value then it will use constant-bitrate mode, otherwise if crf is set as well then it will use constrained-quality mode.

g keyint_min

Set key frame placement. The GOP size sets the maximum distance between key frames; if zero the output stream will be intra-only. The minimum distance is ignored unless it is the same as the GOP size, in which case key frames will always appear at a fixed interval. Not set by default, so without this option the library has completely free choice about where to place key frames.

qmin qmax

Set minimum/maximum quantisation values. Valid range is from 0 to 63 (warning: this does not match the quantiser values actually used by AV1 - divide by four to map real quantiser values to this range). Defaults to min/max (no constraint).

minrate maxrate bufsize rc_init_occupancy

Set rate control buffering parameters. Not used if not set - defaults to unconstrained variable bitrate.

threads

Set the number of threads to use while encoding. This may require the tiles or row-mt options to also be set to actually use the specified number of threads fully. Defaults to the number of hardware threads supported by the host machine.

profile

Set the encoding profile. Defaults to using the profile which matches the bit depth and chroma subsampling of the input.

The wrapper also has some specific options:

cpu-used

Set the quality/encoding speed tradeoff. Valid range is from 0 to 8, higher numbers indicating greater speed and lower quality. The default value is 1, which will be slow and high quality.

auto-alt-ref

Enable use of alternate reference frames. Defaults to the internal default of the library.

arnr-max-frames (frames)

Set altref noise reduction max frame count. Default is -1.

arnr-strength (strength)

Set altref noise reduction filter strength. Range is -1 to 6. Default is -1.

aq-mode (aq-mode)

Set adaptive quantization mode. Possible values:

‘none (0)’

Disabled.

‘variance (1)’

Variance-based.

‘complexity (2)’

Complexity-based.

‘cyclic (3)’

Cyclic refresh.

tune (tune)

Set the distortion metric the encoder is tuned with. Default is psnr.

‘psnr (0)’

‘ssim (1)’

lag-in-frames

Set the maximum number of frames which the encoder may keep in flight at any one time for lookahead purposes. Defaults to the internal default of the library.

error-resilience

Enable error resilience features:

default

Improve resilience against losses of whole frames.

Not enabled by default.

crf

Set the quality/size tradeoff for constant-quality (no bitrate target) and constrained-quality (with maximum bitrate target) modes. Valid range is 0 to 63, higher numbers indicating lower quality and smaller output size. Only used if set; by default only the bitrate target is used.

static-thresh

Set a change threshold on blocks below which they will be skipped by the encoder. Defined in arbitrary units as a nonnegative integer, defaulting to zero (no blocks are skipped).

drop-threshold

Set a threshold for dropping frames when close to rate control bounds. Defined as a percentage of the target buffer - when the rate control buffer falls below this percentage, frames will be dropped until it has refilled above the threshold. Defaults to zero (no frames are dropped).

denoise-noise-level (level)

Amount of noise to be removed for grain synthesis. Grain synthesis is disabled if this option is not set or set to 0.

denoise-block-size (pixels)

Block size used for denoising for grain synthesis. If not set, AV1 codec uses the default value of 32.

undershoot-pct (pct)

Set datarate undershoot (min) percentage of the target bitrate. Range is -1 to 100. Default is -1.

overshoot-pct (pct)

Set datarate overshoot (max) percentage of the target bitrate. Range is -1 to 1000. Default is -1.

minsection-pct (pct)

Minimum percentage variation of the GOP bitrate from the target bitrate. If minsection-pct is not set, the libaomenc wrapper computes it as follows: (minrate * 100 / bitrate). Range is -1 to 100. Default is -1 (unset).

maxsection-pct (pct)

Maximum percentage variation of the GOP bitrate from the target bitrate. If maxsection-pct is not set, the libaomenc wrapper computes it as follows: (maxrate * 100 / bitrate). Range is -1 to 5000. Default is -1 (unset).

frame-parallel (boolean)

Enable frame parallel decodability features. Default is true.

tiles

Set the number of tiles to encode the input video with, as columns x rows. Larger numbers allow greater parallelism in both encoding and decoding, but may decrease coding efficiency. Defaults to the minimum number of tiles required by the size of the input video (this is 1x1 (that is, a single tile) for sizes up to and including 4K).

tile-columns tile-rows

Set the number of tiles as log2 of the number of tile rows and columns. Provided for compatibility with libvpx/VP9.

row-mt (Requires libaom >= 1.0.0-759-g90a15f4f2)

Enable row based multi-threading. Disabled by default.

enable-cdef (boolean)

Enable Constrained Directional Enhancement Filter. The libaom-av1 encoder enables CDEF by default.

enable-restoration (boolean)

Enable Loop Restoration Filter. Default is true for libaom-av1.

enable-global-motion (boolean)

Enable the use of global motion for block prediction. Default is true.

enable-intrabc (boolean)

Enable block copy mode for intra block prediction. This mode is useful for screen content. Default is true.

enable-rect-partitions (boolean) (Requires libaom >= v2.0.0)

Enable rectangular partitions. Default is true.

enable-1to4-partitions (boolean) (Requires libaom >= v2.0.0)

Enable 1:4/4:1 partitions. Default is true.

enable-ab-partitions (boolean) (Requires libaom >= v2.0.0)

Enable AB shape partitions. Default is true.

enable-angle-delta (boolean) (Requires libaom >= v2.0.0)

Enable angle delta intra prediction. Default is true.

enable-cfl-intra (boolean) (Requires libaom >= v2.0.0)

Enable chroma predicted from luma intra prediction. Default is true.

enable-filter-intra (boolean) (Requires libaom >= v2.0.0)

Enable filter intra predictor. Default is true.

enable-intra-edge-filter (boolean) (Requires libaom >= v2.0.0)

Enable intra edge filter. Default is true.

enable-smooth-intra (boolean) (Requires libaom >= v2.0.0)

Enable smooth intra prediction mode. Default is true.

enable-paeth-intra (boolean) (Requires libaom >= v2.0.0)

Enable paeth predictor in intra prediction. Default is true.

enable-palette (boolean) (Requires libaom >= v2.0.0)

Enable palette prediction mode. Default is true.

enable-flip-idtx (boolean) (Requires libaom >= v2.0.0)

Enable extended transform type, including FLIPADST_DCT, DCT_FLIPADST, FLIPADST_FLIPADST, ADST_FLIPADST, FLIPADST_ADST, IDTX, V_DCT, H_DCT, V_ADST, H_ADST, V_FLIPADST, H_FLIPADST. Default is true.

enable-tx64 (boolean) (Requires libaom >= v2.0.0)

Enable 64-pt transform. Default is true.

reduced-tx-type-set (boolean) (Requires libaom >= v2.0.0)

Use reduced set of transform types. Default is false.

use-intra-dct-only (boolean) (Requires libaom >= v2.0.0)

Use DCT only for INTRA modes. Default is false.

use-inter-dct-only (boolean) (Requires libaom >= v2.0.0)

Use DCT only for INTER modes. Default is false.

use-intra-default-tx-only (boolean) (Requires libaom >= v2.0.0)

Use Default-transform only for INTRA modes. Default is false.

enable-ref-frame-mvs (boolean) (Requires libaom >= v2.0.0)

Enable temporal mv prediction. Default is true.

enable-reduced-reference-set (boolean) (Requires libaom >= v2.0.0)

Use reduced set of single and compound references. Default is false.

enable-obmc (boolean) (Requires libaom >= v2.0.0)

Enable obmc. Default is true.

enable-dual-filter (boolean) (Requires libaom >= v2.0.0)

Enable dual filter. Default is true.

enable-diff-wtd-comp (boolean) (Requires libaom >= v2.0.0)

Enable difference-weighted compound. Default is true.

enable-dist-wtd-comp (boolean) (Requires libaom >= v2.0.0)

Enable distance-weighted compound. Default is true.

enable-onesided-comp (boolean) (Requires libaom >= v2.0.0)

Enable one sided compound. Default is true.

enable-interinter-wedge (boolean) (Requires libaom >= v2.0.0)

Enable interinter wedge compound. Default is true.

enable-interintra-wedge (boolean) (Requires libaom >= v2.0.0)

Enable interintra wedge compound. Default is true.

enable-masked-comp (boolean) (Requires libaom >= v2.0.0)

Enable masked compound. Default is true.

enable-interintra-comp (boolean) (Requires libaom >= v2.0.0)

Enable interintra compound. Default is true.

enable-smooth-interintra (boolean) (Requires libaom >= v2.0.0)

Enable smooth interintra mode. Default is true.

aom-params

Set libaom options using a list of key=value pairs separated by ":". For a list of supported options, see aomenc --help under the section "AV1 Specific Options".

For example to specify libaom encoding options with -aom-params:

```
ffmpeg -i input -c:v libaom-av1 -b:v 500K -aom-params tune=psnr:enable-tpl-model=1 output.mp4

```

### 16.9 liboapv# TOC

Advanced Professional Video codec encoder wrapper.

This encoder requires the presence of the liboapv headers and library during configuration. You need to explicitly configure the build with --enable-liboapv.

Many liboapv encoder options are mapped to FFmpeg global codec options, while unique encoder options are provided through private options.

The apv project website is at https://github.com/AcademySoftwareFoundation/openapv.

#### 16.9.1 Options# TOC

The following options are supported by the liboapv wrapper.

To get a more extensive documentation of the liboapv options, consult the liboapv documentation.

preset

Set the quality-speed tradeoff [fastest, fast, medium, slow, placebo, default]

qp

Set the quantization parameter value for CQP rate control mode.

oapv-params (parse_apv_params)

Set liboapvenc options using a list of key=value pairs separated by ":". See the liboapv encoder user guide for a list of accepted parameters.

### 16.10 libsvtav1# TOC

SVT-AV1 encoder wrapper.

Requires the presence of the SVT-AV1 headers and library during configuration. You need to explicitly configure the build with --enable-libsvtav1.

#### 16.10.1 Options# TOC

profile

Set the encoding profile.

‘main’

‘high’

‘professional’

level

Set the operating point level. For example: ’4.0’

hielevel

Set the Hierarchical prediction levels.

‘3level’

‘4level’

This is the default.

tier

Set the operating point tier.

‘main’

This is the default.

‘high’

qmax

Set the maximum quantizer to use when using a bitrate mode.

qmin

Set the minimum quantizer to use when using a bitrate mode.

crf

Constant rate factor value used in crf rate control mode (0-63).

qp

Set the quantizer used in cqp rate control mode (0-63).

sc_detection

Enable scene change detection.

la_depth

Set number of frames to look ahead (0-120).

preset

Set the quality-speed tradeoff, in the range 0 to 13. Higher values are faster but lower quality.

tile_rows

Set log2 of the number of rows of tiles to use (0-6).

tile_columns

Set log2 of the number of columns of tiles to use (0-4).

svtav1-params

Set SVT-AV1 options using a list of key=value pairs separated by ":". See the SVT-AV1 encoder user guide for a list of accepted parameters.

### 16.11 libsvtjpegxs# TOC

SVT-JPEG-XS encoder wrapper.

Requires the presence of the SVT-JPEG-XS headers and library during configuration. You need to explicitly configure the build with --enable-libsvtjpegxs.

#### 16.11.1 Options# TOC

decomp_v

Set vertical decomposition level

decomp_h

Set horizontal decomposition level

quantization

Set the quantization algorithm.

‘deadzone’

‘uniform’

coding-signs

Enable Signs handling strategy

‘disable’

‘fast’

‘full’

coding-sigf

Enable Significance coding

coding-vpred

Enable Vertical Prediction coding

‘disable’

‘no_residuals’

‘no_coeffs’

### 16.12 libjxl# TOC

libjxl JPEG XL encoder wrapper.

Requires the presence of the libjxl headers and library during configuration. You need to explicitly configure the build with --enable-libjxl.

#### 16.12.1 Options# TOC

The libjxl wrapper supports the following options:

distance

Set the target Butteraugli distance. This is a quality setting: lower distance yields higher quality, with distance=1.0 roughly comparable to libjpeg Quality 90 for photographic content. Setting distance=0.0 yields true lossless encoding. Valid values range between 0.0 and 15.0, and sane values rarely exceed 5.0. Setting distance=0.1 usually attains transparency for most input. The default is 1.0.

effort

Set the encoding effort used. Higher effort values produce more consistent quality and usually produces a better quality/bpp curve, at the cost of more CPU time required. Valid values range from 1 to 9, and the default is 7.

modular

Force the encoder to use Modular mode instead of choosing automatically. The default is to use VarDCT for lossy encoding and Modular for lossless. VarDCT is generally superior to Modular for lossy encoding but does not support lossless encoding.

### 16.13 libkvazaar# TOC

Kvazaar H.265/HEVC encoder.

Requires the presence of the libkvazaar headers and library during configuration. You need to explicitly configure the build with --enable-libkvazaar.

#### 16.13.1 Options# TOC

b

Set target video bitrate in bit/s and enable rate control.

kvazaar-params

Set kvazaar parameters as a list of name=value pairs separated by commas (,). See kvazaar documentation for a list of options.

### 16.14 libopenh264# TOC

Cisco libopenh264 H.264/MPEG-4 AVC encoder wrapper.

This encoder requires the presence of the libopenh264 headers and library during configuration. You need to explicitly configure the build with --enable-libopenh264. The library is detected using pkg-config.

For more information about the library see http://www.openh264.org.

#### 16.14.1 Options# TOC

The following FFmpeg global options affect the configurations of the libopenh264 encoder.

b

Set the bitrate (as a number of bits per second).

g

Set the GOP size.

maxrate

Set the max bitrate (as a number of bits per second).

flags +global_header

Set global header in the bitstream.

slices

Set the number of slices, used in parallelized encoding. Default value is 0. This is only used when slice_mode is set to ‘fixed’.

loopfilter

Enable loop filter, if set to 1 (automatically enabled). To disable set a value of 0.

profile

Set profile restrictions. If set to the value of ‘main’ enable CABAC (set the SEncParamExt.iEntropyCodingModeFlag flag to 1).

max_nal_size

Set maximum NAL size in bytes.

allow_skip_frames

Allow skipping frames to hit the target bitrate if set to 1.

### 16.15 libtheora# TOC

libtheora Theora encoder wrapper.

Requires the presence of the libtheora headers and library during configuration. You need to explicitly configure the build with --enable-libtheora.

For more information about the libtheora project see http://www.theora.org/.

#### 16.15.1 Options# TOC

The following global options are mapped to internal libtheora options which affect the quality and the bitrate of the encoded stream.

b

Set the video bitrate in bit/s for CBR (Constant Bit Rate) mode. In case VBR (Variable Bit Rate) mode is enabled this option is ignored.

flags

Used to enable constant quality mode (VBR) encoding through the qscale flag, and to enable the pass1 and pass2 modes.

g

Set the GOP size.

global_quality

Set the global quality as an integer in lambda units.

Only relevant when VBR mode is enabled with flags +qscale. The value is converted to QP units by dividing it by FF_QP2LAMBDA, clipped in the [0 - 10] range, and then multiplied by 6.3 to get a value in the native libtheora range [0-63]. A higher value corresponds to a higher quality.

q

Enable VBR mode when set to a non-negative value, and set constant quality value as a double floating point value in QP units.

The value is clipped in the [0-10] range, and then multiplied by 6.3 to get a value in the native libtheora range [0-63].

This option is valid only using the ffmpeg command-line tool. For library interface users, use global_quality.

#### 16.15.2 Examples# TOC

- Set maximum constant quality (VBR) encoding with ffmpeg:

```
ffmpeg -i INPUT -codec:v libtheora -q:v 10 OUTPUT.ogg

```

- Use ffmpeg to convert a CBR 1000 kbps Theora video stream:

```
ffmpeg -i INPUT -codec:v libtheora -b:v 1000k OUTPUT.ogg

```

### 16.16 libvpx# TOC

VP8/VP9 format supported through libvpx.

Requires the presence of the libvpx headers and library during configuration. You need to explicitly configure the build with --enable-libvpx.

#### 16.16.1 Options# TOC

The following options are supported by the libvpx wrapper. The vpxenc-equivalent options or values are listed in parentheses for easy migration.

To reduce the duplication of documentation, only the private options and some others requiring special attention are documented here. For the documentation of the undocumented generic options, see the Codec Options chapter.

To get more documentation of the libvpx options, invoke the command ffmpeg -h encoder=libvpx, ffmpeg -h encoder=libvpx-vp9 or vpxenc --help. Further information is available in the libvpx API documentation.

b (target-bitrate)

Set bitrate in bits/s. Note that FFmpeg’s b option is expressed in bits/s, while vpxenc’s target-bitrate is in kilobits/s.

g (kf-max-dist)

keyint_min (kf-min-dist)

qmin (min-q)

Minimum (Best Quality) Quantizer.

qmax (max-q)

Maximum (Worst Quality) Quantizer. Can be changed per-frame.

bufsize (buf-sz, buf-optimal-sz)

Set ratecontrol buffer size (in bits). Note vpxenc’s options are specified in milliseconds, the libvpx wrapper converts this value as follows: buf-sz = bufsize * 1000 / bitrate, buf-optimal-sz = bufsize * 1000 / bitrate * 5 / 6.

rc_init_occupancy (buf-initial-sz)

Set number of bits which should be loaded into the rc buffer before decoding starts. Note vpxenc’s option is specified in milliseconds, the libvpx wrapper converts this value as follows: rc_init_occupancy * 1000 / bitrate.

undershoot-pct

Set datarate undershoot (min) percentage of the target bitrate.

overshoot-pct

Set datarate overshoot (max) percentage of the target bitrate.

skip_threshold (drop-frame)

qcomp (bias-pct)

maxrate (maxsection-pct)

Set GOP max bitrate in bits/s. Note vpxenc’s option is specified as a percentage of the target bitrate, the libvpx wrapper converts this value as follows: (maxrate * 100 / bitrate).

minrate (minsection-pct)

Set GOP min bitrate in bits/s. Note vpxenc’s option is specified as a percentage of the target bitrate, the libvpx wrapper converts this value as follows: (minrate * 100 / bitrate).

minrate, maxrate, b end-usage=cbr

(minrate == maxrate == bitrate).

crf (end-usage=cq, cq-level)

tune (tune)

‘psnr (psnr)’

‘ssim (ssim)’

quality, deadline (deadline)

‘best’

Use best quality deadline. Poorly named and quite slow, this option should be avoided as it may give worse quality output than good.

‘good’

Use good quality deadline. This is a good trade-off between speed and quality when used with the cpu-used option.

‘realtime’

Use realtime quality deadline.

speed, cpu-used (cpu-used)

Set quality/speed ratio modifier. Higher values speed up the encode at the cost of quality.

nr (noise-sensitivity)

static-thresh

Set a change threshold on blocks below which they will be skipped by the encoder.

slices (token-parts)

Note that FFmpeg’s slices option gives the total number of partitions, while vpxenc’s token-parts is given as log2(partitions).

max-intra-rate

Set maximum I-frame bitrate as a percentage of the target bitrate. A value of 0 means unlimited.

force_key_frames

VPX_EFLAG_FORCE_KF

Alternate reference frame related

auto-alt-ref

Enable use of alternate reference frames (2-pass only). Values greater than 1 enable multi-layer alternate reference frames (VP9 only).

arnr-maxframes

Set altref noise reduction max frame count.

arnr-type

Set altref noise reduction filter type: backward, forward, centered.

arnr-strength

Set altref noise reduction filter strength.

rc-lookahead, lag-in-frames (lag-in-frames)

Set number of frames to look ahead for frametype and ratecontrol.

min-gf-interval

Set minimum golden/alternate reference frame interval (VP9 only).

error-resilient

Enable error resiliency features.

sharpness integer

Increase sharpness at the expense of lower PSNR. The valid range is [0, 7].

ts-parameters

Sets the temporal scalability configuration using a :-separated list of key=value pairs. For example, to specify temporal scalability parameters with ffmpeg:

```
ffmpeg -i INPUT -c:v libvpx -ts-parameters ts_number_layers=3:\
ts_target_bitrate=250,500,1000:ts_rate_decimator=4,2,1:\
ts_periodicity=4:ts_layer_id=0,2,1,2:ts_layering_mode=3 OUTPUT

```

Below is a brief explanation of each of the parameters, please refer to struct vpx_codec_enc_cfg in vpx/vpx_encoder.h for more details.

ts_number_layers

Number of temporal coding layers.

ts_target_bitrate

Target bitrate for each temporal layer (in kbps). (bitrate should be inclusive of the lower temporal layer).

ts_rate_decimator

Frame rate decimation factor for each temporal layer.

ts_periodicity

Length of the sequence defining frame temporal layer membership.

ts_layer_id

Template defining the membership of frames to temporal layers.

ts_layering_mode

(optional) Selecting the temporal structure from a set of pre-defined temporal layering modes. Currently supports the following options.

0

No temporal layering flags are provided internally, relies on flags being passed in using metadata field in AVFrame with following keys.

vp8-flags

Sets the flags passed into the encoder to indicate the referencing scheme for the current frame. Refer to function vpx_codec_encode in vpx/vpx_encoder.h for more details.

temporal_id

Explicitly sets the temporal id of the current frame to encode.

2

Two temporal layers. 0-1...

3

Three temporal layers. 0-2-1-2...; with single reference frame.

4

Same as option "3", except there is a dependency between the two temporal layer 2 frames within the temporal period.

VP8-specific options

screen-content-mode

Screen content mode, one of: 0 (off), 1 (screen), 2 (screen with more aggressive rate control).

VP9-specific options

lossless

Enable lossless mode.

tile-columns

Set number of tile columns to use. Note this is given as log2(tile_columns). For example, 8 tile columns would be requested by setting the tile-columns option to 3.

tile-rows

Set number of tile rows to use. Note this is given as log2(tile_rows). For example, 4 tile rows would be requested by setting the tile-rows option to 2.

frame-parallel

Enable frame parallel decodability features.

aq-mode

Set adaptive quantization mode (0: off (default), 1: variance 2: complexity, 3: cyclic refresh, 4: equator360).

colorspace color-space

Set input color space. The VP9 bitstream supports signaling the following colorspaces:

‘rgb’ sRGB

‘bt709’ bt709

‘unspecified’ unknown

‘bt470bg’ bt601

‘smpte170m’ smpte170

‘smpte240m’ smpte240

‘bt2020_ncl’ bt2020

row-mt boolean

Enable row based multi-threading.

tune-content

Set content type: default (0), screen (1), film (2).

corpus-complexity

Corpus VBR mode is a variant of standard VBR where the complexity distribution midpoint is passed in rather than calculated for a specific clip or chunk.

The valid range is [0, 10000]. 0 (default) uses standard VBR.

enable-tpl boolean

Enable temporal dependency model.

ref-frame-config

Using per-frame metadata, set members of the structure vpx_svc_ref_frame_config_t in vpx/vp8cx.h to fine-control referencing schemes and frame buffer management.
Use a :-separated list of key=value pairs. For example,

```
av_dict_set(&av_frame->metadata, "ref-frame-config", \
"rfc_update_buffer_slot=7:rfc_lst_fb_idx=0:rfc_gld_fb_idx=1:rfc_alt_fb_idx=2:rfc_reference_last=0:rfc_reference_golden=0:rfc_reference_alt_ref=0");

```

rfc_update_buffer_slot

Indicates the buffer slot number to update

rfc_update_last

Indicates whether to update the LAST frame

rfc_update_golden

Indicates whether to update GOLDEN frame

rfc_update_alt_ref

Indicates whether to update ALT_REF frame

rfc_lst_fb_idx

LAST frame buffer index

rfc_gld_fb_idx

GOLDEN frame buffer index

rfc_alt_fb_idx

ALT_REF frame buffer index

rfc_reference_last

Indicates whether to reference LAST frame

rfc_reference_golden

Indicates whether to reference GOLDEN frame

rfc_reference_alt_ref

Indicates whether to reference ALT_REF frame

rfc_reference_duration

Indicates frame duration

For more information about libvpx see: http://www.webmproject.org/

### 16.17 libvvenc# TOC

VVenC H.266/VVC encoder wrapper.

This encoder requires the presence of the libvvenc headers and library during configuration. You need to explicitly configure the build with --enable-libvvenc.

The VVenC project website is at https://github.com/fraunhoferhhi/vvenc.

#### 16.17.1 Supported Pixel Formats# TOC

VVenC supports only 10-bit color spaces as input. But the internal (encoded) bit depth can be set to 8-bit or 10-bit at runtime.

#### 16.17.2 Options# TOC

b

Sets target video bitrate.

g

Set the GOP size. Currently support for g=1 (Intra only) or default.

preset

Set the VVenC preset.

levelidc

Set level idc.

tier

Set vvc tier.

qp

Set constant quantization parameter.

subopt boolean

Set subjective (perceptually motivated) optimization. Default is 1 (on).

bitdepth8 boolean

Set 8bit coding mode instead of using 10bit. Default is 0 (off).

period

set (intra) refresh period in seconds.

vvenc-params

Set vvenc options using a list of key=value couples separated by ":". See vvencapp --fullhelp or vvencFFapp --fullhelp for a list of options.

For example, the options might be provided as:

```
intraperiod=64:decodingrefreshtype=idr:poc0idr=1:internalbitdepth=8

```

For example the encoding options might be provided with -vvenc-params:

```
ffmpeg -i input -c:v libvvenc -b 1M -vvenc-params intraperiod=64:decodingrefreshtype=idr:poc0idr=1:internalbitdepth=8 output.mp4

```

### 16.18 libwebp# TOC

libwebp WebP Image encoder wrapper

libwebp is Google’s official encoder for WebP images. It can encode in either lossy or lossless mode. Lossy images are essentially a wrapper around a VP8 frame. Lossless images are a separate codec developed by Google.

#### 16.18.1 Pixel Format# TOC

Currently, libwebp only supports YUV420 for lossy and RGB for lossless due to limitations of the format and libwebp. Alpha is supported for either mode. Because of API limitations, if RGB is passed in when encoding lossy or YUV is passed in for encoding lossless, the pixel format will automatically be converted using functions from libwebp. This is not ideal and is done only for convenience.

#### 16.18.2 Options# TOC

-lossless boolean

Enables/Disables use of lossless mode. Default is 0.

-compression_level integer

For lossy, this is a quality/speed tradeoff. Higher values give better quality for a given size at the cost of increased encoding time. For lossless, this is a size/speed tradeoff. Higher values give smaller size at the cost of increased encoding time. More specifically, it controls the number of extra algorithms and compression tools used, and varies the combination of these tools. This maps to the method option in libwebp. The valid range is 0 to 6. Default is 4.

-quality float

For lossy encoding, this controls image quality. For lossless encoding, this controls the effort and time spent in compression. Range is 0 to 100. Default is 75.

-preset type

Configuration preset. This does some automatic settings based on the general type of the image.

none

Do not use a preset.

default

Use the encoder default.

picture

Digital picture, like portrait, inner shot

photo

Outdoor photograph, with natural lighting

drawing

Hand or line drawing, with high-contrast details

icon

Small-sized colorful images

text

Text-like

### 16.19 libastcenc# TOC

ARM ASTC Encoder wrapper.

This encoder requires the Arm ASTC Encoder (astc-encoder) library version 5.4 or newer, which provides high-quality GPU texture compression to the ASTC format, installed as astcenc/astcenc.h next to a library that -lastcenc finds. Pass --enable-version3 together with --enable-libastcenc to configure.

The encoder supports both LDR (8-bit RGBA/RGB) and HDR (float/half RGBA) input. When float or half input is detected with an LDR profile, the profile is automatically promoted to HDR RGB with LDR alpha (HDR_RGB_LDR_A); an explicitly selected HDR profile is kept.

The raw bitstream can be packaged in the .astc container (16-byte header + compressed blocks) or in the Khronos Texture 1.0 container (.ktx). This implementation writes LDR 2D textures only through the .ktx muxer: HDR ASTC and 3D block footprints are not supported by the muxer and .astc must be used for them instead. The KTX 1.0 linear ASTC GL enums do not imply LDR either, so a linear .ktx texture may still hold HDR endpoints; such a texture is decoded with HDR precision by default. The .ktx muxer records its row order in a KTXorientation key.

#### 16.19.1 Pixel Format# TOC

The encoder accepts the following pixel formats:

- rgba – 8-bit packed RGBA (LDR).

- rgb24 – 8-bit packed RGB (LDR, opaque alpha synthesized).

- rgbaf16 – 16-bit floating-point RGBA (HDR).

- rgbaf32 – 32-bit floating-point RGBA (HDR).

- gbrapf32 – planar 32-bit floating-point GBR+Alpha (HDR).

swscale cannot convert to the packed floating-point formats (rgbaf16, rgbaf32); to encode ordinary image formats as HDR, produce a planar floating-point source instead, for example with -vf format=gbrapf32. The packed formats are accepted when they are supplied directly, such as from a decoder or a custom filter graph.

#### 16.19.2 Options# TOC

block_size string

ASTC block size specified as WxH[xD]. When the third dimension is omitted it defaults to 1 (2D block). Valid 2D: 4x4, 5x4, 5x5, 6x5, 6x6, 8x5, 8x6, 8x8, 10x5, 10x6, 10x8, 10x10, 12x10, 12x12. Valid 3D: 3x3x3, 4x3x3, 4x4x3, 4x4x4, 5x4x4, 5x5x4, 5x5x5, 6x5x5, 6x6x5, 6x6x6. Default is 8x8.

quality float

Compression quality from 0 (fastest) to 100 (slowest, exhaustive search). Default is 60.

profile int

Color profile. Possible values:

‘ldr’

Linear LDR.

‘ldr-srgb’

sRGB LDR (default).

‘hdr-ldr-a’

HDR RGB channels with LDR alpha channel.

‘hdr’

Full HDR.

When float/half input is detected with an LDR profile, the profile is automatically promoted to hdr-ldr-a. Conversely, selecting an HDR profile with 8-bit input is rejected. This option overrides AVCodecContext.profile. When it is not set, the profile is taken from AVCodecContext.profile (AV_PROFILE_ASTC_*), where AV_PROFILE_UNKNOWN selects ldr-srgb as before.

perceptual boolean

Use the perceptual (PSNR-weighted) error metric instead of peak-SNR. Default is 0.

alpha_weight boolean

Enable per-texel alpha weighting. Default is 1.

### 16.20 libx264, libx264rgb# TOC

x264 H.264/MPEG-4 AVC encoder wrapper.

This encoder requires the presence of the libx264 headers and library during configuration. You need to explicitly configure the build with --enable-libx264.

libx264 supports an impressive number of features, including 8x8 and 4x4 adaptive spatial transform, adaptive B-frame placement, CAVLC/CABAC entropy coding, interlacing (MBAFF), lossless mode, psy optimizations for detail retention (adaptive quantization, psy-RD, psy-trellis).

Many libx264 encoder options are mapped to FFmpeg global codec options, while unique encoder options are provided through private options. Additionally the x264opts and x264-params private options allows one to pass a list of key=value tuples as accepted by the libx264 x264_param_parse function.

The x264 project website is at http://www.videolan.org/developers/x264.html.

The libx264rgb encoder is the same as libx264, except it accepts packed RGB pixel formats as input instead of YUV.

#### 16.20.1 Supported Pixel Formats# TOC

x264 supports 8- to 10-bit color spaces. The exact bit depth is controlled at x264’s configure time.

#### 16.20.2 Options# TOC

The following options are supported by the libx264 wrapper. The x264-equivalent options or values are listed in parentheses for easy migration.

To reduce the duplication of documentation, only the private options and some others requiring special attention are documented here. For the documentation of the undocumented generic options, see the Codec Options chapter.

To get a more accurate and extensive documentation of the libx264 options, invoke the command x264 --fullhelp or consult the libx264 documentation.

In the list below, note that the x264 option name is shown in parentheses after the libavcodec corresponding name, in case there is a direct mapping.

b (bitrate)

Set bitrate in bits/s. Note that FFmpeg’s b option is expressed in bits/s, while x264’s bitrate is in kilobits/s.

bf (bframes)

Number of B-frames between I and P-frames

g (keyint)

Maximum GOP size

qmin (qpmin)

Minimum quantizer scale

qmax (qpmax)

Maximum quantizer scale

qdiff (qpstep)

Maximum difference between quantizer scales

qblur (qblur)

Quantizer curve blur

qcomp (qcomp)

Quantizer curve compression factor

refs (ref)

Number of reference frames each P-frame can use. The range is 0-16.

level (level)

Set the x264_param_t.i_level_idc value in case the value is positive, it is ignored otherwise.

This value can be set using the AVCodecContext API (e.g. by setting the AVCodecContext value directly), and is specified as an integer mapped on a corresponding level (e.g. the value 31 maps to H.264 level IDC "3.1", as defined in the x264_levels table). It is ignored when set to a non positive value.

Alternatively it can be set as a private option, overriding the value set in AVCodecContext, and in this case must be specified as the level IDC identifier (e.g. "3.1"), as defined by H.264 Annex A.

sc_threshold (scenecut)

Sets the threshold for the scene change detection.

trellis (trellis)

Performs Trellis quantization to increase efficiency. Enabled by default.

nr (nr)

Noise reduction

me_range (merange)

Maximum range of the motion search in pixels.

me_method (me)

Set motion estimation method. Possible values in the decreasing order of speed:

‘dia (dia)’

‘epzs (dia)’

Diamond search with radius 1 (fastest). ‘epzs’ is an alias for ‘dia’.

‘hex (hex)’

Hexagonal search with radius 2.

‘umh (umh)’

Uneven multi-hexagon search.

‘esa (esa)’

Exhaustive search.

‘tesa (tesa)’

Hadamard exhaustive search (slowest).

forced-idr

Normally, when forcing a I-frame type, the encoder can select any type of I-frame. This option forces it to choose an IDR-frame.

subq (subme)

Sub-pixel motion estimation method.

b_strategy (b-adapt)

Adaptive B-frame placement decision algorithm. Use only on first-pass.

keyint_min (min-keyint)

Minimum GOP size.

coder

Set entropy encoder. Possible values:

‘ac’

Enable CABAC.

‘vlc’

Enable CAVLC and disable CABAC. It generates the same effect as x264’s --no-cabac option.

cmp

Set full pixel motion estimation comparison algorithm. Possible values:

‘chroma’

Enable chroma in motion estimation.

‘sad’

Ignore chroma in motion estimation. It generates the same effect as x264’s --no-chroma-me option.

threads (threads)

Number of encoding threads.

thread_type

Set multithreading technique. Possible values:

‘slice’

Slice-based multithreading. It generates the same effect as x264’s --sliced-threads option.

‘frame’

Frame-based multithreading.

flags

Set encoding flags. It can be used to disable closed GOP and enable open GOP by setting it to -cgop. The result is similar to the behavior of x264’s --open-gop option.

rc_init_occupancy (vbv-init)

Initial VBV buffer occupancy

preset (preset)

Set the encoding preset.

tune (tune)

Set tuning of the encoding params.

profile (profile)

Set profile restrictions.

fastfirstpass

Enable fast settings when encoding first pass, when set to 1. When set to 0, it has the same effect of x264’s --slow-firstpass option.

crf (crf)

Set the quality for constant quality mode.

crf_max (crf-max)

In CRF mode, prevents VBV from lowering quality beyond this point.

qp (qp)

Set constant quantization rate control method parameter.

aq-mode (aq-mode)

Set AQ method. Possible values:

‘none (0)’

Disabled.

‘variance (1)’

Variance AQ (complexity mask).

‘autovariance (2)’

Auto-variance AQ (experimental).

aq-strength (aq-strength)

Set AQ strength, reduce blocking and blurring in flat and textured areas.

psy

Use psychovisual optimizations when set to 1. When set to 0, it has the same effect as x264’s --no-psy option.

psy-rd (psy-rd)

Set strength of psychovisual optimization, in psy-rd:psy-trellis format.

rc-lookahead (rc-lookahead)

Set number of frames to look ahead for frametype and ratecontrol.

weightb

Enable weighted prediction for B-frames when set to 1. When set to 0, it has the same effect as x264’s --no-weightb option.

weightp (weightp)

Set weighted prediction method for P-frames. Possible values:

‘none (0)’

Disabled

‘simple (1)’

Enable only weighted refs

‘smart (2)’

Enable both weighted refs and duplicates

ssim (ssim)

Enable calculation and printing SSIM stats after the encoding.

intra-refresh (intra-refresh)

Enable the use of Periodic Intra Refresh instead of IDR frames when set to 1.

avcintra-class (class)

Configure the encoder to generate AVC-Intra. Valid values are 50, 100 and 200

bluray-compat (bluray-compat)

Configure the encoder to be compatible with the bluray standard. It is a shorthand for setting "bluray-compat=1 force-cfr=1".

b-bias (b-bias)

Set the influence on how often B-frames are used.

b-pyramid (b-pyramid)

Set method for keeping of some B-frames as references. Possible values:

‘none (none)’

Disabled.

‘strict (strict)’

Strictly hierarchical pyramid.

‘normal (normal)’

Non-strict (not Blu-ray compatible).

mixed-refs

Enable the use of one reference per partition, as opposed to one reference per macroblock when set to 1. When set to 0, it has the same effect as x264’s --no-mixed-refs option.

8x8dct

Enable adaptive spatial transform (high profile 8x8 transform) when set to 1. When set to 0, it has the same effect as x264’s --no-8x8dct option.

fast-pskip

Enable early SKIP detection on P-frames when set to 1. When set to 0, it has the same effect as x264’s --no-fast-pskip option.

aud (aud)

Enable use of access unit delimiters when set to 1.

mbtree

Enable use macroblock tree ratecontrol when set to 1. When set to 0, it has the same effect as x264’s --no-mbtree option.

deblock (deblock)

Set loop filter parameters, in alpha:beta form.

cplxblur (cplxblur)

Set fluctuations reduction in QP (before curve compression).

partitions (partitions)

Set partitions to consider as a comma-separated list of values. Possible values in the list:

‘p8x8’

8x8 P-frame partition.

‘p4x4’

4x4 P-frame partition.

‘b8x8’

4x4 B-frame partition.

‘i8x8’

8x8 I-frame partition.

‘i4x4’

4x4 I-frame partition. (Enabling ‘p4x4’ requires ‘p8x8’ to be enabled. Enabling ‘i8x8’ requires adaptive spatial transform (8x8dct option) to be enabled.)

‘none (none)’

Do not consider any partitions.

‘all (all)’

Consider every partition.

direct-pred (direct)

Set direct MV prediction mode. Possible values:

‘none (none)’

Disable MV prediction.

‘spatial (spatial)’

Enable spatial predicting.

‘temporal (temporal)’

Enable temporal predicting.

‘auto (auto)’

Automatically decided.

slice-max-size (slice-max-size)

Set the limit of the size of each slice in bytes. If not specified but RTP payload size (ps) is specified, that is used.

stats (stats)

Set the file name for multi-pass stats.

nal-hrd (nal-hrd)

Set signal HRD information (requires vbv-bufsize to be set). Possible values:

‘none (none)’

Disable HRD information signaling.

‘vbr (vbr)’

Variable bit rate.

‘cbr (cbr)’

Constant bit rate (not allowed in MP4 container).

x264opts opts

x264-params opts

Override the x264 configuration using a :-separated list of key=value options.

The argument for both options is a list of key=value couples separated by ":". With x264opts the value can be omitted, and the value 1 is assumed in that case.

For filter and psy-rd options values that use ":" as a separator themselves, use "," instead. They accept it as well since long ago but this is kept undocumented for some reason.

For example, the options might be provided as:

```
level=30:bframes=0:weightp=0:cabac=0:ref=1:vbv-maxrate=768:vbv-bufsize=2000:analyse=all:me=umh:no-fast-pskip=1:subq=6:8x8dct=0:trellis=0

```

For example to specify libx264 encoding options with ffmpeg:

```
ffmpeg -i foo.mpg -c:v libx264 -x264opts keyint=123:min-keyint=20 -an out.mkv

```

To get the complete list of the libx264 options, invoke the command x264 --fullhelp or consult the libx264 documentation.

a53cc boolean

Import closed captions (which must be ATSC compatible format) into output. Only the mpeg2 and h264 decoders provide these. Default is 1 (on).

udu_sei boolean

Import user data unregistered SEI if available into output. Default is 0 (off).

mb_info boolean

Set mb_info data through AVFrameSideData, only useful when used from the API. Default is 0 (off).

Encoding ffpresets for common usages are provided so they can be used with the general presets system (e.g. passing the pre option).

### 16.21 libx265# TOC

x265 H.265/HEVC encoder wrapper.

This encoder requires the presence of the libx265 headers and library during configuration. You need to explicitly configure the build with --enable-libx265.

#### 16.21.1 Options# TOC

b

Sets target video bitrate.

bf

g

Set the GOP size.

keyint_min

Minimum GOP size.

refs

Number of reference frames each P-frame can use. The range is from 1-16.

preset

Set the x265 preset.

tune

Set the x265 tune parameter.

profile

Set profile restrictions.

crf

Set the quality for constant quality mode.

qp

Set constant quantization rate control method parameter.

qmin

Minimum quantizer scale.

qmax

Maximum quantizer scale.

qdiff

Maximum difference between quantizer scales.

qblur

Quantizer curve blur

qcomp

Quantizer curve compression factor

i_qfactor

b_qfactor

forced-idr

Normally, when forcing a I-frame type, the encoder can select any type of I-frame. This option forces it to choose an IDR-frame.

x265-stats

Specify the file name for 2-pass stats. This is set automatically when using the -passlogfile option.

udu_sei boolean

Import user data unregistered SEI if available into output. Default is 0 (off).

x265-params

Set x265 options using a list of key=value couples separated by ":". See x265 --help for a list of options.

For example to specify libx265 encoding options with -x265-params:

```
ffmpeg -i input -c:v libx265 -x265-params crf=26:psy-rd=1 output.mp4

```

### 16.22 libxavs2# TOC

xavs2 AVS2-P2/IEEE1857.4 encoder wrapper.

This encoder requires the presence of the libxavs2 headers and library during configuration. You need to explicitly configure the build with --enable-libxavs2.

The following standard libavcodec options are used:

- b / bit_rate

- g / gop_size

- bf / max_b_frames

The encoder also has its own specific options:

#### 16.22.1 Options# TOC

lcu_row_threads

Set the number of parallel threads for rows from 1 to 8 (default 5).

initial_qp

Set the xavs2 quantization parameter from 1 to 63 (default 34). This is used to set the initial qp for the first frame.

qp

Set the xavs2 quantization parameter from 1 to 63 (default 34). This is used to set the qp value under constant-QP mode.

max_qp

Set the max qp for rate control from 1 to 63 (default 55).

min_qp

Set the min qp for rate control from 1 to 63 (default 20).

speed_level

Set the Speed level from 0 to 9 (default 0). Higher is better but slower.

log_level

Set the log level from -1 to 3 (default 0). -1: none, 0: error, 1: warning, 2: info, 3: debug.

xavs2-params

Set xavs2 options using a list of key=value couples separated by ":".

For example to specify libxavs2 encoding options with -xavs2-params:

```
ffmpeg -i input -c:v libxavs2 -xavs2-params RdoqLevel=0 output.avs2

```

### 16.23 libxeve# TOC

eXtra-fast Essential Video Encoder (XEVE) MPEG-5 EVC encoder wrapper. The xeve-equivalent options or values are listed in parentheses for easy migration.

This encoder requires the presence of the libxeve headers and library during configuration. You need to explicitly configure the build with --enable-libxeve.

Many libxeve encoder options are mapped to FFmpeg global codec options, while unique encoder options are provided through private options. Additionally the xeve-params private options allows one to pass a list of key=value tuples as accepted by the libxeve parse_xeve_params function.

The xeve project website is at https://github.com/mpeg5/xeve.

#### 16.23.1 Options# TOC

The following options are supported by the libxeve wrapper. The xeve-equivalent options or values are listed in parentheses for easy migration.

To reduce the duplication of documentation, only the private options and some others requiring special attention are documented here. For the documentation of the undocumented generic options, see the Codec Options chapter.

To get a more accurate and extensive documentation of the libxeve options, invoke the command xeve_app --help or consult the libxeve documentation.

b (bitrate)

Set target video bitrate in bits/s. Note that FFmpeg’s b option is expressed in bits/s, while xeve’s bitrate is in kilobits/s.

bf (bframes)

Set the maximum number of B frames (1,3,7,15).

g (keyint)

Set the GOP size (I-picture period).

preset (preset)

Set the xeve preset. Set the encoder preset value to determine encoding speed [fast, medium, slow, placebo]

tune (tune)

Set the encoder tune parameter [psnr, zerolatency]

profile (profile)

Set the encoder profile [0: baseline; 1: main]

crf (crf)

Set the quality for constant quality mode. Constant rate factor <10..49> [default: 32]

qp (qp)

Set constant quantization rate control method parameter. Quantization parameter qp <0..51> [default: 32]

threads (threads)

Force to use a specific number of threads

### 16.24 libxvid# TOC

Xvid MPEG-4 Part 2 encoder wrapper.

This encoder requires the presence of the libxvidcore headers and library during configuration. You need to explicitly configure the build with --enable-libxvid --enable-gpl.

The native mpeg4 encoder supports the MPEG-4 Part 2 format, so users can encode to this format without this library.

#### 16.24.1 Options# TOC

The following options are supported by the libxvid wrapper. Some of the following options are listed but are not documented, and correspond to shared codec options. See the Codec Options chapter for their documentation. The other shared options which are not listed have no effect for the libxvid encoder.

b

g

qmin

qmax

mpeg_quant

threads

bf

b_qfactor

b_qoffset

flags

Set specific encoding flags. Possible values:

‘mv4’

Use four motion vector by macroblock.

‘aic’

Enable high quality AC prediction.

‘gray’

Only encode grayscale.

‘qpel’

Enable quarter-pixel motion compensation.

‘cgop’

Enable closed GOP.

‘global_header’

Place global headers in extradata instead of every keyframe.

gmc

Enable the use of global motion compensation (GMC). Default is 0 (disabled).

me_quality

Set motion estimation quality level. Possible values in decreasing order of speed and increasing order of quality:

‘0’

Use no motion estimation (default).

‘1, 2’

Enable advanced diamond zonal search for 16x16 blocks and half-pixel refinement for 16x16 blocks.

‘3, 4’

Enable all of the things described above, plus advanced diamond zonal search for 8x8 blocks and half-pixel refinement for 8x8 blocks, also enable motion estimation on chroma planes for P and B-frames.

‘5, 6’

Enable all of the things described above, plus extended 16x16 and 8x8 blocks search.

mbd

Set macroblock decision algorithm. Possible values in the increasing order of quality:

‘simple’

Use macroblock comparing function algorithm (default).

‘bits’

Enable rate distortion-based half pixel and quarter pixel refinement for 16x16 blocks.

‘rd’

Enable all of the things described above, plus rate distortion-based half pixel and quarter pixel refinement for 8x8 blocks, and rate distortion-based search using square pattern.

lumi_aq

Enable lumi masking adaptive quantization when set to 1. Default is 0 (disabled).

variance_aq

Enable variance adaptive quantization when set to 1. Default is 0 (disabled).

When combined with lumi_aq, the resulting quality will not be better than any of the two specified individually. In other words, the resulting quality will be the worse one of the two effects.

trellis

Set rate-distortion optimal quantization.

ssim

Set structural similarity (SSIM) displaying method. Possible values:

‘off’

Disable displaying of SSIM information.

‘avg’

Output average SSIM at the end of encoding to stdout. The format of showing the average SSIM is:

```
Average SSIM: %f

```

For users who are not familiar with C, %f means a float number, or a decimal (e.g. 0.939232).

‘frame’

Output both per-frame SSIM data during encoding and average SSIM at the end of encoding to stdout. The format of per-frame information is:

```
       SSIM: avg: %1.3f min: %1.3f max: %1.3f

```

For users who are not familiar with C, %1.3f means a float number rounded to 3 digits after the dot (e.g. 0.932).

ssim_acc

Set SSIM accuracy. Valid options are integers within the range of 0-4, while 0 gives the most accurate result and 4 computes the fastest.

### 16.25 MediaCodec# TOC

MediaCodec encoder wrapper enables hardware-accelerated video encoding on Android device. It supports H.264, H.265 (HEVC), VP8, VP9, MPEG-4, and AV1 encoding (whether works or not is device dependent).

Android provides two sets of APIs: Java MediaCodec and NDK MediaCodec. The MediaCodec encoder wrapper supports both. Note that the NDK MediaCodec API operates without requiring JVM, but may fail to function outside the JVM environment due to dependencies on system framework services, particularly after Android 15.

ndk_codec boolean

Use the NDK-based MediaCodec API instead of the Java API. Enabled by default if av_jni_get_java_vm() return NULL.

ndk_async boolean

Use NDK MediaCodec in async mode. Async mode has less overhead than poll in a loop in sync mode. The drawback of async mode is AV_CODEC_FLAG_GLOBAL_HEADER doesn’t work (use extract_extradata bsf when necessary). It doesn’t work and will be disabled automatically on devices below Android 8.0.

codec_name string

A codec type can have multiple implementations on a single device, this option specify which backend to use (via MediaCodec createCodecByName API). It’s NULL by default, and encoder is created by createEncoderByType.

bitrate_mode integer

Possible values:

‘cq’

Constant quality mode

‘vbr’

Variable bitrate mode

‘cbr’

Constant bitrate mode

‘cbr_fd’

Constant bitrate mode with frame drops

pts_as_dts boolean

Use PTS as DTS. This is a workaround since MediaCodec API doesn’t provide decoding timestamp. It is enabled automatically if B frame is 0.

operating_rate integer

The desired operating rate that the codec will need to operate at, zero for unspecified. This is used for cases like high-speed/slow-motion video capture, where the video encoder format contains the target playback rate (e.g. 30fps), but the component must be able to handle the high operating capture rate (e.g. 240fps). This rate will be used by codec for resource planning and setting the operating points.

qp_i_min integer

Minimum quantization parameter for I frame.

qp_p_min integer

Minimum quantization parameter for P frame.

qp_b_min integer

Minimum quantization parameter for B frame.

qp_i_max integer

Maximum quantization parameter for I frame.

qp_p_max integer

Maximum quantization parameter for P frame.

qp_b_max integer

Maximum quantization parameter for B frame.

### 16.26 MediaFoundation# TOC

The following wrappers for encoders in the MediaFoundation framework are available:

- h264_mf

- hevc_mf

- av1_mf

These support both software and hardware encoding.

Video encoders can take input in either of nv12 or yuv420p form (some encoders support both, some support only either - in practice, nv12 is the safer choice, especially among HW encoders).

Hardware-accelerated encoding requires D3D11, including hardware scaling capabilities through the scale_d3d11 filter.

To list all available options for the MediaFoundation encoders, use: ffmpeg -h encoder=<encoder> e.g. ffmpeg -h encoder=h264_mf

#### 16.26.1 Options# TOC

rate_control

Select rate control mode. Available modes:

‘default’

Default mode

‘cbr’

CBR mode

‘pc_vbr’

Peak constrained VBR mode

‘u_vbr’

Unconstrained VBR mode

‘quality’

Quality mode

‘ld_vbr’

Low delay VBR mode (requires Windows 8+)

‘g_vbr’

Global VBR mode (requires Windows 8+)

‘gld_vbr’

Global low delay VBR mode (requires Windows 8+)

scenario

Select usage scenario. Available scenarios:

‘default’

Default scenario

‘display_remoting’

Display remoting scenario

‘video_conference’

Video conference scenario

‘archive’

Archive scenario

‘live_streaming’

Live streaming scenario

‘camera_record’

Camera record scenario

‘display_remoting_with_feature_map’

Display remoting with feature map scenario

quality

Set encoding quality (0-100). -1 means default quality.

hw_encoding

Force hardware encoding (0-1). Default is 0 (disabled).

#### 16.26.2 Examples# TOC

Hardware encoding:

```
ffmpeg -i input.mp4 -c:v h264_mf -hw_encoding 1 output.mp4

```

Hardware-accelerated decoding with hardware encoding:

```
ffmpeg -hwaccel d3d11va -i input.mp4 -c:v h264_mf -hw_encoding 1 output.mp4

```

Hardware-accelerated decoding, HW scaling and encoding with quality setting:

```
ffmpeg -hwaccel d3d11va -hwaccel_output_format d3d11 -i input.mp4 -vf scale_d3d11=1920:1080 -c:v hevc_mf -hw_encoding 1 -quality 80 output.mp4

```

### 16.27 Microsoft RLE# TOC

Microsoft RLE aka MSRLE encoder. Only 8-bit palette mode supported. Compatible with Windows 3.1 and Windows 95.

#### 16.27.1 Options# TOC

g integer

Keyframe interval. A keyframe is inserted at least every -g frames, sometimes sooner.

### 16.28 mpeg2# TOC

MPEG-2 video encoder.

#### 16.28.1 Options# TOC

profile

Select the mpeg2 profile to encode:

‘422’

‘high’

‘ss’

Spatially Scalable

‘snr’

SNR Scalable

‘main’

‘simple’

level

Select the mpeg2 level to encode:

‘high’

‘high1440’

‘main’

‘low’

seq_disp_ext integer

Specifies if the encoder should write a sequence_display_extension to the output.

-1

auto

Decide automatically to write it or not (this is the default) by checking if the data to be written is different from the default or unspecified values.

0

never

Never write it.

1

always

Always write it.

video_format integer

Specifies the video_format written into the sequence display extension indicating the source of the video pictures. The default is ‘unspecified’, can be ‘component’, ‘pal’, ‘ntsc’, ‘secam’ or ‘mac’. For maximum compatibility, use ‘component’.

a53cc boolean

Import closed captions (which must be ATSC compatible format) into output. Default is 1 (on).

### 16.29 NVENC encoders# TOC

The h264_nvenc, hevc_nvenc and av1_nvenc encoders use NVIDIA NVENC hardware to encode H.264, HEVC and AV1 video, respectively. Building them requires the ffnvcodec headers provided by nv-codec-headers. They are autodetected by configure; they can also be enabled explicitly with --enable-ffnvcodec and --enable-nvenc.

Available options and values depend on the SDK version exposed by the headers at build time. Feature checks in libavcodec/nvenc.h distinguish SDK versions 12.0, 12.1, 12.2, 13.0 and 13.1. Runtime support also depends on the GPU and driver. Use ffmpeg -h encoder=hevc_nvenc, or substitute h264_nvenc or av1_nvenc, to list the options, devices and pixel formats available in a particular build.

#### 16.29.1 Hardware input and devices# TOC

These encoders accept system-memory frames and CUDA hardware frames (AV_PIX_FMT_CUDA). Builds using SDK 13.1 or newer also accept CUDA array frames (AV_PIX_FMT_CUARRAY). Builds with d3d11va support accept D3D11 hardware frames (AV_PIX_FMT_D3D11). The input pixel format and encoding features must be supported by the selected GPU.

For CUDA decoding followed by encoding, use the input options -hwaccel cuda -hwaccel_output_format cuda to keep decoded frames on the device. A hardware device can also be created with -init_hw_device and supplied to the encoder, directly or through its hardware frames context. For system-memory input without a supplied hardware device, the encoder option gpu selects the device. See its entry under Other common options below.

#### 16.29.2 Generic options# TOC

Several generic encoding options are mapped to NVENC settings. The bitrate options b, maxrate and bufsize set the average bitrate, the maximum bitrate and the VBV buffer size; the NVENC default for b is ‘2M’. g sets the GOP length, with 0 requesting intra-only encoding. bf sets the number of B-frames between non-B-frames. refs sets the number of reference frames in each reference list. g and bf default to -1 and refs defaults to 0; these defaults leave the values of the preset unchanged.

The generic qmin and qmax options are honoured in VBR mode with a warning; API users should set the encoder options of the same names listed below instead.

Only applications calling the libavcodec API can change AVCodecContext.bit_rate, AVCodecContext.rc_max_rate and AVCodecContext.rc_buffer_size during encoding. The encoder checks these fields before encoding each frame. When dynamic bitrate changes are supported and rate control is not ‘constqp’, changed positive values trigger reconfiguration, reset the encoder and force an IDR. A change to the display aspect ratio also triggers reconfiguration.

#### 16.29.3 Common options# TOC

The following option names are shared by all three encoders. Differences in values and build requirements are noted below. Boolean options accept 0 (disabled) and 1 (enabled), unless otherwise stated.

#### 16.29.3.1 Presets and tuning# TOC

preset integer

Select the encoding preset using a named value from the table (recommended) or its integer. The range is 0 to 9; the default is ‘p4’ (6).

‘slow’

Deprecated alias for high quality with two passes (0).

‘medium’

Deprecated alias for high quality with one pass (1).

‘fast’

Deprecated alias for high performance with one pass (2).

‘p1’

Fastest, lowest quality (3).

‘p2’

Faster, lower quality (4).

‘p3’

Fast, low quality (5).

‘p4’

Medium (6); the default.

‘p5’

Slow, good quality (7).

‘p6’

Slower, better quality (8).

‘p7’

Slowest, best quality (9).

Use ‘p1’ through ‘p7’ with tune and multipass instead of the deprecated aliases.

tune integer

Select encoding tuning using a named value from the table (recommended) or its integer. The default is ‘hq’ (1).

H.264 accepts 1 to 4; HEVC and AV1 also expose ‘uhq’ when built with the required SDK.

‘hq’

High quality (1).

‘ll’

Low latency (2).

‘ull’

Ultra low latency (3).

‘lossless’

Lossless (4).

‘uhq’

Ultra high quality (5).

HEVC requires SDK 12.2 or newer; AV1 requires SDK 13.0 or newer. Not available for H.264.

#### 16.29.3.2 Rate control# TOC

rc integer

Override preset rate control using a named value from the table (recommended) or its integer. The range is -1 to INT_MAX; the default is -1 (no explicit override).

‘constqp’

Constant QP (0).

‘vbr’

Variable bitrate (1).

‘cbr’

Constant bitrate (2).

multipass integer

Select multipass encoding using a named value from the table (recommended) or its integer. The range is 0 to 2; the default is ‘disabled’ (0).

‘disabled’

Single pass (0).

‘qres’

Two passes, with the first pass at quarter resolution (1).

‘fullres’

Two passes, with the first pass at full resolution (2).

cq float

Set the target quality for constant quality mode in VBR rate control. The default is 0 (automatic).

The range is 0 to 51 for H.264 and HEVC, or 0 to 63 for AV1.

qp integer

Set the constant quantization parameter. The default is -1 (unset).

The range is -1 to 51 for H.264 and HEVC, or -1 to 255 for AV1.

init_qpP integer

init_qpB integer

init_qpI integer

Set the initial QP for P-, B- and I-frames, respectively. Each defaults to -1 (unset).

The range is -1 to 51 for H.264 and HEVC, or -1 to 255 for AV1.

qmin integer

qmax integer

Set the minimum and maximum QP used for rate control. Each defaults to -1 (unset).

The range is -1 to 51 for H.264 and HEVC, or -1 to 255 for AV1.

qp_cb_offset integer

qp_cr_offset integer

Set the chroma QP offsets for the Cb and Cr channels, respectively. Each accepts -12 to 12 and defaults to 0.

strict_gop boolean

Minimize GOP-to-GOP rate fluctuations. The default is 0.

ldkfs integer

Set the low-delay keyframe scale, which specifies the scene-change frame size increase allowed with a single-frame VBV buffer and CBR. The range is 0 to 255 and the default is 0.

cbr_padding boolean

Pad the bitstream to prevent the bitrate falling below the target in CBR mode. The default is 0.

#### 16.29.3.3 Lookahead, adaptive quantization and B-frames# TOC

rc-lookahead integer

Set the number of frames to look ahead for rate control. The range is 0 to INT_MAX and the default is 0.

lookahead_level integer

Set the lookahead level using a named value from the table (recommended) or its integer. Higher levels may improve quality at the expense of performance. Requires SDK 12.2 or newer. The range is -1 to 15; the default is -1 (no override).

‘0’

‘1’

‘2’

‘3’

Select the corresponding lookahead level.

‘auto’

Automatic selection (15).

no-scenecut boolean

Disable adaptive I-frame insertion at scene cuts when lookahead is enabled. The default is 0.

b_adapt boolean

Enable adaptive B-frame decisions when lookahead is enabled. The default is 1.

spatial-aq boolean

Enable spatial adaptive quantization. The default is 0.

temporal-aq boolean

Enable temporal adaptive quantization. The default is 0.

aq-strength integer

Set spatial adaptive quantization strength when spatial-aq is enabled, from 1 (low) to 15 (aggressive). The default is 8.

b_ref_mode integer

Select the use of B-frames as references using a named value from the table (recommended) or its integer. The default is -1 (no override).

H.264 and HEVC accept -1 to 2. AV1 accepts -1 to 4 with SDK 13.1 or newer, or -1 to 2 with older headers.

‘disabled’

Do not use B-frames as references (0).

‘each’

Use each B-frame as a reference (1).

‘middle’

For H.264 and HEVC, use only half the B-frames as references (2).

For AV1, use every other B-frame as an Altref2 reference (2), except the last in the Altref interval.

‘hierarchical’

Use B-frames as references hierarchically (4).

AV1 only; requires SDK 13.1 or newer.

weighted_pred integer

Enable weighted prediction with 1, or disable it with 0 (the default).

This is a boolean option for AV1.

tf_level integer

Set temporal filtering strength. The range is -1 to INT_MAX; the default is -1 (no override).

Requires SDK 12.2 or newer for HEVC, or SDK 13.0 or newer for H.264 and AV1.

‘0’

‘4’

Select the corresponding temporal filtering strength.

#### 16.29.3.4 SEI and side data# TOC

extra_sei boolean

Pass extra frame side data. The default is 1.

H.264 and HEVC use SEI payloads; AV1 uses metadata OBUs. This gates the payload array used for a53cc, HEVC and AV1 s12m_tc, and H.264 and HEVC udu_sei.

a53cc boolean

Use AV_FRAME_DATA_A53_CC side data for A53 closed captions when available. Requires extra_sei. The default is 1.

H.264 and HEVC carry it in ITU-T T.35 registered user-data SEI; AV1 uses an ITU-T T.35 metadata OBU.

s12m_tc boolean

Use AV_FRAME_DATA_S12M_TIMECODE side data when available. The default is 1.

H.264 uses picture timing and requires SDK 12.2 or newer; HEVC uses timecode SEI; AV1 uses timecode metadata OBUs. The HEVC and AV1 paths require extra_sei; the H.264 path is independent of it.

With SDK 13.0 or newer, HEVC and AV1 also support mastering-display and content-light-level metadata. The corresponding AV_FRAME_DATA_MASTERING_DISPLAY_METADATA and AV_FRAME_DATA_CONTENT_LIGHT_LEVEL entries in AVCodecContext.decoded_side_data enable output at initialization. Frame side data supplies per-frame values, falling back to those stream values when absent. This path is independent of extra_sei.

#### 16.29.3.5 Other common options# TOC

level integer

Set the encoding level restriction using a named value (recommended) or its integer. The tables below list the values, numeric ranges and default integers for each codec. The default is ‘auto’ (0 for H.264 and HEVC, 24 for AV1).

gpu integer

Select the NVENC-capable GPU for system-memory input without a supplied hardware device using a named value from the table (recommended) or its integer. Device indices start at 0. The range is -2 to INT_MAX and the default is ‘any’ (-1).

‘list’

List the available devices (-2).

‘any’

Use the first available device (-1).

surfaces integer

Set the number of concurrent surfaces, from 0 to 64. The default is 0 (automatic).

delay integer

Delay frame output by the specified number of frames, from 0 to INT_MAX. The default is INT_MAX; the actual delay is limited by the number of surfaces.

rgb_mode integer

Select how packed RGB input is handled using a named value from the table (recommended) or its integer. The range is 0 to INT_MAX; the default is ‘yuv420’ (1).

‘disabled’

Reject packed RGB input (0).

‘yuv420’

Convert to YUV 4:2:0 (1).

‘yuv444’

Convert to YUV 4:4:4 (2).

highbitdepth boolean

Enable 10-bit encoding for 8-bit input. The default is 0.

For H.264 this requires SDK 13.0 or newer.

forced-idr boolean

When forcing keyframes, force IDR frames. The range is -1 to 1 and the default is 0. A value of -1 leaves the picture-type decision to the encoder.

zerolatency boolean

Request zero-latency operation with no reordering delay. The default is 0.

nonref_p boolean

Enable automatic insertion of non-reference P-frames. The default is 0.

dpb_size integer

Set the decoded picture buffer size, from 0 to INT_MAX. The default is 0 (automatic).

intra-refresh boolean

Use periodic intra refresh instead of IDR frames. The default is 0.

#### 16.29.4 H.264 and HEVC options# TOC

The following options are available for h264_nvenc and hevc_nvenc only.

aud boolean

Use access unit delimiters. The default is 0.

bluray-compat boolean

Enable Blu-ray compatibility workarounds. The default is 0.

udu_sei boolean

Pass AV_FRAME_DATA_SEI_UNREGISTERED frame side data as unregistered user-data SEI. Requires extra_sei. The default is 0.

single-slice-intra-refresh boolean

Use single-slice intra refresh. This also enables intra-refresh. The default is 0.

max_slice_size integer

Set the maximum encoded slice size in bytes, from 0 to INT_MAX. The default is 0 (no override).

constrained-encoding boolean

Enable constrained-frame encoding, making each slice in a constrained picture independent of the other slices. The default is 0.

#### 16.29.5 HEVC and AV1 options# TOC

The following option is available for hevc_nvenc and av1_nvenc only.

split_encode_mode integer

Set split-frame encoding mode using a named value from the table (recommended) or its integer. Requires SDK 12.1 or newer. The range is 0 to 15 and the default is ‘auto’ (0).

‘auto’

Enable or disable it according to the preset and tuning (0).

‘forced’

Enable it with the number of horizontal strips selected by the driver (1).

‘2’

Force two horizontal strips when more than one NVENC engine is available (2).

‘3’

Force three horizontal strips when more than two NVENC engines are available (3).

‘4’

Force four horizontal strips when more than three NVENC engines are available (4). Requires SDK 13.0 or newer.

‘disabled’

Disable split encoding (15).

#### 16.29.6 H.264 options# TOC

profile integer

Set the H.264 profile using a named value from the table (recommended) or its integer. The default is ‘high’ (2).

‘baseline’

baseline profile (0).

‘main’

main profile (1).

‘high’

high profile (2).

‘high10’

high10 profile (3).

‘high422’

high422 profile (4).

‘high444p’

high444p profile (5).

The ‘high10’ and ‘high422’ values require SDK 13.0 or newer. With headers older than SDK 13.0, ‘high444p’ has integer value 3 instead of 5.

level integer

Set the H.264 level restriction using a named value from the table (recommended) or its integer. The range is 0 to 62; the default is ‘auto’ (0).

‘auto’

Automatic selection (0).

‘1b’

Level 1b (9).

‘1.0b’

Level 1.0b (9).

‘1’

Level 1 (10).

‘1.0’

Level 1.0 (10).

‘1.1’

Level 1.1 (11).

‘1.2’

Level 1.2 (12).

‘1.3’

Level 1.3 (13).

‘2’

Level 2 (20).

‘2.0’

Level 2.0 (20).

‘2.1’

Level 2.1 (21).

‘2.2’

Level 2.2 (22).

‘3’

Level 3 (30).

‘3.0’

Level 3.0 (30).

‘3.1’

Level 3.1 (31).

‘3.2’

Level 3.2 (32).

‘4’

Level 4 (40).

‘4.0’

Level 4.0 (40).

‘4.1’

Level 4.1 (41).

‘4.2’

Level 4.2 (42).

‘5’

Level 5 (50).

‘5.0’

Level 5.0 (50).

‘5.1’

Level 5.1 (51).

‘5.2’

Level 5.2 (52).

‘6.0’

Level 6.0 (60).

‘6.1’

Level 6.1 (61).

‘6.2’

Level 6.2 (62).

coder integer

Set the entropy coder using a named value from the table (recommended) or its integer. The range is -1 to 2; the default is ‘default’ (-1).

‘default’

Leave the preset entropy coding mode unchanged (-1).

‘auto’

Automatic selection (0).

‘cabac’

‘ac’

CABAC (1).

‘cavlc’

‘vlc’

CAVLC (2).

#### 16.29.7 HEVC options# TOC

profile integer

Set the HEVC profile using a named value from the table (recommended) or its integer. The default is ‘main’ (0).

‘main’

main profile (0).

‘main10’

main10 profile (1).

‘rext’

rext profile (2).

‘mv’

mv profile (3).

The ‘mv’ value requires SDK 13.0 or newer.

level integer

Set the HEVC level restriction using a named value from the table (recommended) or its integer. The range is 0 to 186; the default is ‘auto’ (0).

‘auto’

Automatic selection (0).

‘1’

Level 1 (30).

‘1.0’

Level 1.0 (30).

‘2’

Level 2 (60).

‘2.0’

Level 2.0 (60).

‘2.1’

Level 2.1 (63).

‘3’

Level 3 (90).

‘3.0’

Level 3.0 (90).

‘3.1’

Level 3.1 (93).

‘4’

Level 4 (120).

‘4.0’

Level 4.0 (120).

‘4.1’

Level 4.1 (123).

‘5’

Level 5 (150).

‘5.0’

Level 5.0 (150).

‘5.1’

Level 5.1 (153).

‘5.2’

Level 5.2 (156).

‘6’

Level 6 (180).

‘6.0’

Level 6.0 (180).

‘6.1’

Level 6.1 (183).

‘6.2’

Level 6.2 (186).

tier integer

Set the HEVC encoding tier using a named value from the table (recommended) or its integer. The range is 0 to 1; the default is ‘main’ (0).

‘main’

Main tier (0).

‘high’

High tier (1).

unidir_b boolean

Enable unidirectional B-frames. Requires SDK 12.2 or newer. The default is 0.

#### 16.29.8 AV1 options# TOC

level integer

Set the AV1 level restriction using a named value from the table (recommended) or its integer. The range is 0 to 24; the default is ‘auto’ (24).

‘2’

Level 2 (0).

‘2.0’

Level 2.0 (0).

‘2.1’

Level 2.1 (1).

‘2.2’

Level 2.2 (2).

‘2.3’

Level 2.3 (3).

‘3’

Level 3 (4).

‘3.0’

Level 3.0 (4).

‘3.1’

Level 3.1 (5).

‘3.2’

Level 3.2 (6).

‘3.3’

Level 3.3 (7).

‘4’

Level 4 (8).

‘4.0’

Level 4.0 (8).

‘4.1’

Level 4.1 (9).

‘4.2’

Level 4.2 (10).

‘4.3’

Level 4.3 (11).

‘5’

Level 5 (12).

‘5.0’

Level 5.0 (12).

‘5.1’

Level 5.1 (13).

‘5.2’

Level 5.2 (14).

‘5.3’

Level 5.3 (15).

‘6’

Level 6 (16).

‘6.0’

Level 6.0 (16).

‘6.1’

Level 6.1 (17).

‘6.2’

Level 6.2 (18).

‘6.3’

Level 6.3 (19).

‘7’

Level 7 (20).

‘7.0’

Level 7.0 (20).

‘7.1’

Level 7.1 (21).

‘7.2’

Level 7.2 (22).

‘7.3’

Level 7.3 (23).

‘auto’

Automatic selection (24).

tier integer

Set the AV1 encoding tier, from 0 to 1. The default is 0.

‘0’

Tier 0.

‘1’

Tier 1.

tile-rows integer

tile-columns integer

Set the number of tile rows and columns, respectively. Each accepts -1 to 64 and defaults to -1 (no override).

timing-info boolean

Include timing information in sequence and frame headers. The default is 0.

### 16.30 png# TOC

PNG image encoder.

#### 16.30.1 Options# TOC

compression_level

Sets the compression level, from 0 to 9(default)

#### 16.30.2 Private options# TOC

dpi integer

Set physical density of pixels, in dots per inch, unset by default

dpm integer

Set physical density of pixels, in dots per meter, unset by default

pred method

Set prediction method (none, sub, up, avg, paeth, mixed), default is paeth

### 16.31 ProRes# TOC

Apple ProRes encoder.

FFmpeg contains 2 ProRes encoders, the prores-aw and prores-ks encoder. The used encoder can be chosen with the -vcodec option.

#### 16.31.1 Private Options for prores-ks# TOC

profile integer

Select the ProRes profile to encode

‘proxy’

‘lt’

‘standard’

‘hq’

‘4444’

‘4444xq’

quant_mat integer

Select quantization matrix.

‘auto’

‘default’

‘proxy’

‘lt’

‘standard’

‘hq’

If set to auto, the matrix matching the profile will be picked. If not set, the matrix providing the highest quality, default, will be picked.

bits_per_mb integer

How many bits to allot for coding one macroblock. Different profiles use between 200 and 2400 bits per macroblock, the maximum is 8000.

mbs_per_slice integer

Number of macroblocks in each slice (1-8); the default value (8) should be good in almost all situations.

vendor string

Override the 4-byte vendor ID. A custom vendor ID like apl0 would claim the stream was produced by the Apple encoder.

alpha_bits integer

Specify number of bits for alpha component. Possible values are 0, 8 and 16. Use 0 to disable alpha plane coding.

#### 16.31.2 Speed considerations# TOC

In the default mode of operation the encoder has to honor frame constraints (i.e. not produce frames with size bigger than requested) while still making output picture as good as possible. A frame containing a lot of small details is harder to compress and the encoder would spend more time searching for appropriate quantizers for each slice.

Setting a higher bits_per_mb limit will improve the speed.

For the fastest encoding speed set the qscale parameter (4 is the recommended value) and do not set a size constraint.

### 16.32 QSV Encoders# TOC

The family of Intel QuickSync Video encoders (MPEG-2, H.264, HEVC, JPEG/MJPEG, VP9, AV1)

#### 16.32.1 Ratecontrol Method# TOC

The ratecontrol method is selected as follows:

- When global_quality is specified, a quality-based mode is used. Specifically this means either

- CQP - constant quantizer scale, when the qscale codec flag is also set (the -qscale ffmpeg option).

- LA_ICQ - intelligent constant quality with lookahead, when the look_ahead option is also set.

- ICQ – intelligent constant quality otherwise. For the ICQ modes, global quality range is 1 to 51, with 1 being the best quality.

- Otherwise when the desired average bitrate is specified with the b option, a bitrate-based mode is used.

- LA - VBR with lookahead, when the look_ahead option is specified.

- VCM - video conferencing mode, when the vcm option is set.

- CBR - constant bitrate, when maxrate is specified and equal to the average bitrate.

- VBR - variable bitrate, when maxrate is specified, but is higher than the average bitrate.

- AVBR - average VBR mode, when maxrate is not specified, both avbr_accuracy and avbr_convergence are set to non-zero. This mode is available for H264 and HEVC on Windows.

- Otherwise the default ratecontrol method CQP is used.

Note that depending on your system, a different mode than the one you specified may be selected by the encoder. Set the verbosity level to verbose or higher to see the actual settings used by the QSV runtime.

#### 16.32.2 Global Options -> MSDK Options# TOC

Additional libavcodec global options are mapped to MSDK options as follows:

- g/gop_size -> GopPicSize

- bf/max_b_frames+1 -> GopRefDist

- rc_init_occupancy/rc_initial_buffer_occupancy -> InitialDelayInKB

- slices -> NumSlice

- refs -> NumRefFrame

- b_strategy/b_frame_strategy -> BRefType

- cgop/CLOSED_GOP codec flag -> GopOptFlag

- For the CQP mode, the i_qfactor/i_qoffset and b_qfactor/b_qoffset set the difference between QPP and QPI, and QPP and QPB respectively.

- Setting the coder option to the value vlc will make the H.264 encoder use CAVLC instead of CABAC.

#### 16.32.3 Common Options# TOC

Following options are used by all qsv encoders.

async_depth

Specifies how many asynchronous operations an application performs before the application explicitly synchronizes the result. If zero, the value is not specified.

preset

This option itemizes a range of choices from veryfast (best speed) to veryslow (best quality).

‘veryfast’

‘faster’

‘fast’

‘medium’

‘slow’

‘slower’

‘veryslow’

forced_idr

Forcing I frames as IDR frames.

low_power

For encoders set this flag to ON to reduce power consumption and GPU usage.

#### 16.32.4 Runtime Options# TOC

Following options can be used during qsv encoding.

global_quality

i_quant_factor

i_quant_offset

b_quant_factor

b_quant_offset

Supported in h264_qsv and hevc_qsv. Change these value to reset qsv codec’s qp configuration.

max_frame_size

Supported in h264_qsv and hevc_qsv. Change this value to reset qsv codec’s MaxFrameSize configuration.

gop_size

Change this value to reset qsv codec’s gop configuration.

int_ref_type

int_ref_cycle_size

int_ref_qp_delta

int_ref_cycle_dist

Supported in h264_qsv and hevc_qsv. Change these value to reset qsv codec’s Intra Refresh configuration.

qmax

qmin

max_qp_i

min_qp_i

max_qp_p

min_qp_p

max_qp_b

min_qp_b

Supported in h264_qsv. Change these value to reset qsv codec’s max/min qp configuration.

low_delay_brc

Supported in h264_qsv, hevc_qsv and av1_qsv. Change this value to reset qsv codec’s low_delay_brc configuration.

framerate

Change this value to reset qsv codec’s framerate configuration.

bit_rate

rc_buffer_size

rc_initial_buffer_occupancy

rc_max_rate

Change these value to reset qsv codec’s bitrate control configuration.

pic_timing_sei

Supported in h264_qsv and hevc_qsv. Change this value to reset qsv codec’s pic_timing_sei configuration.

qsv_params

Set QSV encoder parameters as a colon-separated list of key-value pairs.

The qsv_params should be formatted as key1=value1:key2=value2:....

These parameters are passed directly to the underlying Intel Quick Sync Video (QSV) encoder using the MFXSetParameter function.

Example:

```
ffmpeg -i input.mp4 -c:v h264_qsv -qsv_params "CodingOption1=1:CodingOption2=2" output.mp4

```

This option allows fine-grained control over various encoder-specific settings provided by the QSV encoder.

#### 16.32.5 H264 options# TOC

These options are used by h264_qsv

extbrc

Extended bitrate control.

recovery_point_sei

Set this flag to insert the recovery point SEI message at the beginning of every intra refresh cycle.

rdo

Enable rate distortion optimization.

max_frame_size

Maximum encoded frame size in bytes.

max_frame_size_i

Maximum encoded frame size for I frames in bytes. If this value is set as larger than zero, then for I frames the value set by max_frame_size is ignored.

max_frame_size_p

Maximum encoded frame size for P frames in bytes. If this value is set as larger than zero, then for P frames the value set by max_frame_size is ignored.

max_slice_size

Maximum encoded slice size in bytes.

bitrate_limit

Toggle bitrate limitations. Modifies bitrate to be in the range imposed by the QSV encoder. Setting this flag off may lead to violation of HRD conformance. Mind that specifying bitrate below the QSV encoder range might significantly affect quality. If on this option takes effect in non CQP modes: if bitrate is not in the range imposed by the QSV encoder, it will be changed to be in the range.

mbbrc

Setting this flag enables macroblock level bitrate control that generally improves subjective visual quality. Enabling this flag may have negative impact on performance and objective visual quality metric.

low_delay_brc

Setting this flag turns on or off LowDelayBRC feature in qsv plugin, which provides more accurate bitrate control to minimize the variance of bitstream size frame by frame. Value: -1-default 0-off 1-on

adaptive_i

This flag controls insertion of I frames by the QSV encoder. Turn ON this flag to allow changing of frame type from P and B to I.

adaptive_b

This flag controls changing of frame type from B to P.

p_strategy

Enable P-pyramid: 0-default 1-simple 2-pyramid(bf need to be set to 0).

b_strategy

This option controls usage of B frames as reference.

dblk_idc

This option disable deblocking. It has value in range 0~2.

cavlc

If set, CAVLC is used; if unset, CABAC is used for encoding.

vcm

Video conferencing mode, please see ratecontrol method.

idr_interval

Distance (in I-frames) between IDR frames.

pic_timing_sei

Insert picture timing SEI with pic_struct_syntax element.

single_sei_nal_unit

Put all the SEI messages into one NALU.

max_dec_frame_buffering

Maximum number of frames buffered in the DPB.

look_ahead

Use VBR algorithm with look ahead.

look_ahead_depth

Depth of look ahead in number frames.

look_ahead_downsampling

Downscaling factor for the frames saved for the lookahead analysis.

‘unknown’

‘auto’

‘off’

‘2x’

‘4x’

int_ref_type

Specifies intra refresh type. The major goal of intra refresh is improvement of error resilience without significant impact on encoded bitstream size caused by I frames. The SDK encoder achieves this by encoding part of each frame in refresh cycle using intra MBs. none means no refresh. vertical means vertical refresh, by column of MBs. horizontal means horizontal refresh, by rows of MBs. slice means horizontal refresh by slices without overlapping. In case of slice, in_ref_cycle_size is ignored. To enable intra refresh, B frame should be set to 0.

int_ref_cycle_size

Specifies number of pictures within refresh cycle starting from 2. 0 and 1 are invalid values.

int_ref_qp_delta

Specifies QP difference for inserted intra MBs. This is signed value in [-51, 51] range if target encoding bit-depth for luma samples is 8 and this range is [-63, 63] for 10 bit-depth or [-75, 75] for 12 bit-depth respectively.

int_ref_cycle_dist

Distance between the beginnings of the intra-refresh cycles in frames.

profile

‘unknown’

‘baseline’

‘main’

‘high’

a53cc

Use A53 Closed Captions (if available).

aud

Insert the Access Unit Delimiter NAL.

mfmode

Multi-Frame Mode.

‘off’

‘auto’

repeat_pps

Repeat pps for every frame.

max_qp_i

Maximum video quantizer scale for I frame.

min_qp_i

Minimum video quantizer scale for I frame.

max_qp_p

Maximum video quantizer scale for P frame.

min_qp_p

Minimum video quantizer scale for P frame.

max_qp_b

Maximum video quantizer scale for B frame.

min_qp_b

Minimum video quantizer scale for B frame.

scenario

Provides a hint to encoder about the scenario for the encoding session.

‘unknown’

‘displayremoting’

‘videoconference’

‘archive’

‘livestreaming’

‘cameracapture’

‘videosurveillance’

‘gamestreaming’

‘remotegaming’

avbr_accuracy

Accuracy of the AVBR ratecontrol (unit of tenth of percent).

avbr_convergence

Convergence of the AVBR ratecontrol (unit of 100 frames)

The parameters avbr_accuracy and avbr_convergence are for the average variable bitrate control (AVBR) algorithm. The algorithm focuses on overall encoding quality while meeting the specified bitrate, target_bitrate, within the accuracy range avbr_accuracy, after a avbr_Convergence period. This method does not follow HRD and the instant bitrate is not capped or padded.

skip_frame

Use per-frame metadata "qsv_skip_frame" to skip frame when encoding. This option defines the usage of this metadata.

‘no_skip’

Frame skipping is disabled.

‘insert_dummy’

Encoder inserts into bitstream frame where all macroblocks are encoded as skipped.

‘insert_nothing’

Similar to insert_dummy, but encoder inserts nothing into bitstream. The skipped frames are still used in brc. For example, gop still include skipped frames, and the frames after skipped frames will be larger in size.

‘brc_only’

skip_frame metadata indicates the number of missed frames before the current frame.

#### 16.32.6 HEVC Options# TOC

These options are used by hevc_qsv

extbrc

Extended bitrate control.

recovery_point_sei

Set this flag to insert the recovery point SEI message at the beginning of every intra refresh cycle.

rdo

Enable rate distortion optimization.

max_frame_size

Maximum encoded frame size in bytes.

max_frame_size_i

Maximum encoded frame size for I frames in bytes. If this value is set as larger than zero, then for I frames the value set by max_frame_size is ignored.

max_frame_size_p

Maximum encoded frame size for P frames in bytes. If this value is set as larger than zero, then for P frames the value set by max_frame_size is ignored.

max_slice_size

Maximum encoded slice size in bytes.

mbbrc

Setting this flag enables macroblock level bitrate control that generally improves subjective visual quality. Enabling this flag may have negative impact on performance and objective visual quality metric.

low_delay_brc

Setting this flag turns on or off LowDelayBRC feature in qsv plugin, which provides more accurate bitrate control to minimize the variance of bitstream size frame by frame. Value: -1-default 0-off 1-on

adaptive_i

This flag controls insertion of I frames by the QSV encoder. Turn ON this flag to allow changing of frame type from P and B to I.

adaptive_b

This flag controls changing of frame type from B to P.

p_strategy

Enable P-pyramid: 0-default 1-simple 2-pyramid(bf need to be set to 0).

b_strategy

This option controls usage of B frames as reference.

dblk_idc

This option disable deblocking. It has value in range 0~2.

idr_interval

Distance (in I-frames) between IDR frames.

‘begin_only’

Output an IDR-frame only at the beginning of the stream.

load_plugin

A user plugin to load in an internal session.

‘none’

‘hevc_sw’

‘hevc_hw’

load_plugins

A :-separate list of hexadecimal plugin UIDs to load in an internal session.

look_ahead_depth

Depth of look ahead in number frames, available when extbrc option is enabled.

profile

Set the encoding profile (scc requires libmfx >= 1.32).

‘unknown’

‘main’

‘main10’

‘mainsp’

‘rext’

‘scc’

tier

Set the encoding tier (only level >= 4 can support high tier). This option only takes effect when the level option is specified.

‘main’

‘high’

gpb

1: GPB (generalized P/B frame)

0: regular P frame.

tile_cols

Number of columns for tiled encoding.

tile_rows

Number of rows for tiled encoding.

aud

Insert the Access Unit Delimiter NAL.

pic_timing_sei

Insert picture timing SEI with pic_struct_syntax element.

transform_skip

Turn this option ON to enable transformskip. It is supported on platform equal or newer than ICL.

int_ref_type

Specifies intra refresh type. The major goal of intra refresh is improvement of error resilience without significant impact on encoded bitstream size caused by I frames. The SDK encoder achieves this by encoding part of each frame in refresh cycle using intra MBs. none means no refresh. vertical means vertical refresh, by column of MBs. horizontal means horizontal refresh, by rows of MBs. slice means horizontal refresh by slices without overlapping. In case of slice, in_ref_cycle_size is ignored. To enable intra refresh, B frame should be set to 0.

int_ref_cycle_size

Specifies number of pictures within refresh cycle starting from 2. 0 and 1 are invalid values.

int_ref_qp_delta

Specifies QP difference for inserted intra MBs. This is signed value in [-51, 51] range if target encoding bit-depth for luma samples is 8 and this range is [-63, 63] for 10 bit-depth or [-75, 75] for 12 bit-depth respectively.

int_ref_cycle_dist

Distance between the beginnings of the intra-refresh cycles in frames.

max_qp_i

Maximum video quantizer scale for I frame.

min_qp_i

Minimum video quantizer scale for I frame.

max_qp_p

Maximum video quantizer scale for P frame.

min_qp_p

Minimum video quantizer scale for P frame.

max_qp_b

Maximum video quantizer scale for B frame.

min_qp_b

Minimum video quantizer scale for B frame.

scenario

Provides a hint to encoder about the scenario for the encoding session.

‘unknown’

‘displayremoting’

‘videoconference’

‘archive’

‘livestreaming’

‘cameracapture’

‘videosurveillance’

‘gamestreaming’

‘remotegaming’

avbr_accuracy

Accuracy of the AVBR ratecontrol (unit of tenth of percent).

avbr_convergence

Convergence of the AVBR ratecontrol (unit of 100 frames)

The parameters avbr_accuracy and avbr_convergence are for the average variable bitrate control (AVBR) algorithm. The algorithm focuses on overall encoding quality while meeting the specified bitrate, target_bitrate, within the accuracy range avbr_accuracy, after a avbr_Convergence period. This method does not follow HRD and the instant bitrate is not capped or padded.

skip_frame

Use per-frame metadata "qsv_skip_frame" to skip frame when encoding. This option defines the usage of this metadata.

‘no_skip’

Frame skipping is disabled.

‘insert_dummy’

Encoder inserts into bitstream frame where all macroblocks are encoded as skipped.

‘insert_nothing’

Similar to insert_dummy, but encoder inserts nothing into bitstream. The skipped frames are still used in brc. For example, gop still include skipped frames, and the frames after skipped frames will be larger in size.

‘brc_only’

skip_frame metadata indicates the number of missed frames before the current frame.

#### 16.32.7 MPEG2 Options# TOC

These options are used by mpeg2_qsv

profile

‘unknown’

‘simple’

‘main’

‘high’

#### 16.32.8 VP9 Options# TOC

These options are used by vp9_qsv

profile

‘unknown’

‘profile0’

‘profile1’

‘profile2’

‘profile3’

tile_cols

Number of columns for tiled encoding (requires libmfx >= 1.29).

tile_rows

Number of rows for tiled encoding (requires libmfx >= 1.29).

#### 16.32.9 AV1 Options# TOC

These options are used by av1_qsv (requires libvpl).

profile

‘unknown’

‘main’

tile_cols

Number of columns for tiled encoding.

tile_rows

Number of rows for tiled encoding.

adaptive_i

This flag controls insertion of I frames by the QSV encoder. Turn ON this flag to allow changing of frame type from P and B to I.

adaptive_b

This flag controls changing of frame type from B to P.

b_strategy

This option controls usage of B frames as reference.

extbrc

Extended bitrate control.

look_ahead_depth

Depth of look ahead in number frames, available when extbrc option is enabled.

low_delay_brc

Setting this flag turns on or off LowDelayBRC feature in qsv plugin, which provides more accurate bitrate control to minimize the variance of bitstream size frame by frame. Value: -1-default 0-off 1-on

max_frame_size

Set the allowed max size in bytes for each frame. If the frame size exceeds the limitation, encoder will adjust the QP value to control the frame size. Invalid in CQP rate control mode.

max_frame_size_i

Maximum encoded frame size for I frames in bytes. If this value is set as larger than zero, then for I frames the value set by max_frame_size is ignored.

max_frame_size_p

Maximum encoded frame size for P frames in bytes. If this value is set as larger than zero, then for P frames the value set by max_frame_size is ignored.

### 16.33 snow# TOC

#### 16.33.1 Options# TOC

iterative_dia_size

dia size for the iterative motion estimation

### 16.34 VAAPI encoders# TOC

Wrappers for hardware encoders accessible via VAAPI.

These encoders only accept input in VAAPI hardware surfaces. If you have input in software frames, use the hwupload filter to upload them to the GPU.

The following standard libavcodec options are used:

- g / gop_size

- bf / max_b_frames

- profile
If not set, this will be determined automatically from the format of the input frames and the profiles supported by the driver.

- level

- b / bit_rate

- maxrate / rc_max_rate

- bufsize / rc_buffer_size

- rc_init_occupancy / rc_initial_buffer_occupancy

- compression_level
Speed / quality tradeoff: higher values are faster / worse quality.

- q / global_quality
Size / quality tradeoff: higher values are smaller / worse quality.

- qmin

- qmax

- i_qfactor / i_quant_factor

- i_qoffset / i_quant_offset

- b_qfactor / b_quant_factor

- b_qoffset / b_quant_offset

- slices

All encoders support the following options:

low_power

Some drivers/platforms offer a second encoder for some codecs intended to use less power than the default encoder; setting this option will attempt to use that encoder. Note that it may support a reduced feature set, so some other options may not be available in this mode.

idr_interval

Set the number of normal intra frames between full-refresh (IDR) frames in open-GOP mode. The intra frames are still IRAPs, but will not include global headers and may have non-decodable leading pictures.

b_depth

Set the B-frame reference depth. When set to one (the default), all B-frames will refer only to P- or I-frames. When set to greater values multiple layers of B-frames will be present, frames in each layer only referring to frames in higher layers.

async_depth

Maximum processing parallelism. Increase this to improve single channel performance. This option doesn’t work if driver doesn’t implement vaSyncBuffer function. Please make sure there are enough hw_frames allocated if a large number of async_depth is used.

max_frame_size

Set the allowed max size in bytes for each frame. If the frame size exceeds the limitation, encoder will adjust the QP value to control the frame size. Invalid in CQP rate control mode.

rc_mode

Set the rate control mode to use. A given driver may only support a subset of modes.

Possible modes:

auto

Choose the mode automatically based on driver support and the other options. This is the default.

CQP

Constant-quality.

CBR

Constant-bitrate.

VBR

Variable-bitrate.

ICQ

Intelligent constant-quality.

QVBR

Quality-defined variable-bitrate.

AVBR

Average variable bitrate.

blbrc

Enable block level rate control, which assigns different bitrate block by block. Invalid for CQP mode.

Each encoder also has its own specific options:

av1_vaapi

profile sets the value of seq_profile. tier sets the value of seq_tier. level sets the value of seq_level_idx.

tiles

Set the number of tiles to encode the input video with, as columns x rows. (default is auto, which means use minimal tile column/row number).

tile_groups

Set tile groups number. All the tiles will be distributed as evenly as possible to each tile group. (default is 1).

h264_vaapi

profile sets the value of profile_idc and the constraint_set*_flags. level sets the value of level_idc.

coder

Set entropy encoder (default is cabac). Possible values:

‘ac’

‘cabac’

Use CABAC.

‘vlc’

‘cavlc’

Use CAVLC.

aud

Include access unit delimiters in the stream (not included by default).

sei

Set SEI message types to include. Some combination of the following values:

‘identifier’

Include a user_data_unregistered message containing information about the encoder.

‘timing’

Include picture timing parameters (buffering_period and pic_timing messages).

‘recovery_point’

Include recovery points where appropriate (recovery_point messages).

hevc_vaapi

profile and level set the values of general_profile_idc and general_level_idc respectively.

aud

Include access unit delimiters in the stream (not included by default).

tier

Set general_tier_flag. This may affect the level chosen for the stream if it is not explicitly specified.

sei

Set SEI message types to include. Some combination of the following values:

‘hdr’

Include HDR metadata if the input frames have it (mastering_display_colour_volume and content_light_level messages).

tiles

Set the number of tiles to encode the input video with, as columns x rows. Larger numbers allow greater parallelism in both encoding and decoding, but may decrease coding efficiency.

mjpeg_vaapi

Only baseline DCT encoding is supported. The encoder always uses the standard quantisation and huffman tables - global_quality scales the standard quantisation table (range 1-100).

For YUV, 4:2:0, 4:2:2 and 4:4:4 subsampling modes are supported. RGB is also supported, and will create an RGB JPEG.

jfif

Include JFIF header in each frame (not included by default).

huffman

Include standard huffman tables (on by default). Turning this off will save a few hundred bytes in each output frame, but may lose compatibility with some JPEG decoders which don’t fully handle MJPEG.

mpeg2_vaapi

profile and level set the value of profile_and_level_indication.

vp8_vaapi

B-frames are not supported.

global_quality sets the q_idx used for non-key frames (range 0-127).

loop_filter_level

loop_filter_sharpness

Manually set the loop filter parameters.

vp9_vaapi

global_quality sets the q_idx used for P-frames (range 0-255).

loop_filter_level

loop_filter_sharpness

Manually set the loop filter parameters.

B-frames are supported, but the output stream is always in encode order rather than display order. If B-frames are enabled, it may be necessary to use the vp9_raw_reorder bitstream filter to modify the output stream to display frames in the correct order.

Only normal frames are produced - the vp9_superframe bitstream filter may be required to produce a stream usable with all decoders.

### 16.35 vbn# TOC

Vizrt Binary Image encoder.

This format is used by the broadcast vendor Vizrt for quick texture streaming. Advanced features of the format such as LZW compression of texture data or generation of mipmaps are not supported.

#### 16.35.1 Options# TOC

format string

Sets the texture compression used by the VBN file. Can be dxt1, dxt5 or raw. Default is dxt5.

### 16.36 vc2# TOC

SMPTE VC-2 (previously BBC Dirac Pro). This codec was primarily aimed at professional broadcasting but since it supports yuv420, yuv422 and yuv444 at 8 (limited range or full range), 10 or 12 bits, this makes it suitable for other tasks which require low overhead and low compression (like screen recording).

#### 16.36.1 Options# TOC

b

Sets target video bitrate. Usually that’s around 1:6 of the uncompressed video bitrate (e.g. for 1920x1080 50fps yuv422p10 that’s around 400Mbps). Higher values (close to the uncompressed bitrate) turn on lossless compression mode.

field_order

Enables field coding when set (e.g. to tt - top field first) for interlaced inputs. Should increase compression with interlaced content as it splits the fields and encodes each separately.

wavelet_depth

Sets the total amount of wavelet transforms to apply, between 1 and 5 (default). Lower values reduce compression and quality. Less capable decoders may not be able to handle values of wavelet_depth over 3.

wavelet_type

Sets the transform type. Currently only 5_3 (LeGall) and 9_7 (Deslauriers-Dubuc) are implemented, with 9_7 being the one with better compression and thus is the default.

slice_width

slice_height

Sets the slice size for each slice. Larger values result in better compression. For compatibility with other more limited decoders use slice_width of 32 and slice_height of 8.

tolerance

Sets the undershoot tolerance of the rate control system in percent. This is to prevent an expensive search from being run.

qm

Sets the quantization matrix preset to use by default or when wavelet_depth is set to 5

- default Uses the default quantization matrix from the specifications, extended with values for the fifth level. This provides a good balance between keeping detail and omitting artifacts.

- flat Use a completely zeroed out quantization matrix. This increases PSNR but might reduce perception. Use in bogus benchmarks.

- color Reduces detail but attempts to preserve color at extremely low bitrates.

## 17 Subtitles Encoders# TOC

### 17.1 dvbsub# TOC

This codec encodes the bitmap subtitle format that is used in DVB broadcasts and recordings. The bitmaps are typically embedded in a container such as MPEG-TS as a separate stream.

#### 17.1.1 Options# TOC

min_bpp integer (2, 4, or 8)

Set a minimum bits-per-pixel value for the subtitle color lookup tables.

DVB supports 2, 4, and 8 bits-per-pixel color lookup tables. This option enables forcing a particular bits-per-pixel value regardless of the number of colors. Since not all players support or properly support 2 bits-per-pixel, this value defaults to 4.

### 17.2 dvdsub# TOC

This codec encodes the bitmap subtitle format that is used in DVDs. Typically they are stored in VOBSUB file pairs (*.idx + *.sub), and they can also be used in Matroska files.

#### 17.2.1 Options# TOC

palette

Specify the global palette used by the bitmaps.

The format for this option is a string containing 16 24-bits hexadecimal numbers (without 0x prefix) separated by commas, for example 0d00ee, ee450d, 101010, eaeaea, 0ce60b, ec14ed, ebff0b, 0d617a, 7b7b7b, d1d1d1, 7b2a0e, 0d950c, 0f007b, cf0dec, cfa80c, 7c127b.

even_rows_fix

When set to 1, enable a work-around that makes the number of pixel rows even in all subtitles. This fixes a problem with some players that cut off the bottom row if the number is odd. The work-around just adds a fully transparent row if needed. The overhead is low, typically one byte per subtitle on average.

By default, this work-around is disabled.

### 17.3 lrc# TOC

This codec encodes the LRC lyrics format.

#### 17.3.1 Options# TOC

precision

Specify the precision of the fractional part of the timestamp. Time base is determined based on this value.

Defaults to 2 for centiseconds.

## 18 Bitstream Filters# TOC

When you configure your FFmpeg build, all the supported bitstream filters are enabled by default. You can list all available ones using the configure option --list-bsfs.

You can disable all the bitstream filters using the configure option --disable-bsfs, and selectively enable any bitstream filter using the option --enable-bsf=BSF, or you can disable a particular bitstream filter using the option --disable-bsf=BSF.

The option -bsfs of the ff* tools will display the list of all the supported bitstream filters included in your build.

The ff* tools have a -bsf option applied per stream, taking a comma-separated list of filters, whose parameters follow the filter name after a ’=’.

```
ffmpeg -i INPUT -c:v copy -bsf:v filter1[=opt1=str1:opt2=str2][,filter2] OUTPUT

```

Below is a description of the currently available bitstream filters, with their parameters, if any.

### 18.1 aac_adtstoasc# TOC

Convert MPEG-2/4 AAC ADTS to an MPEG-4 Audio Specific Configuration bitstream.

This filter creates an MPEG-4 AudioSpecificConfig from an MPEG-2/4 ADTS header and removes the ADTS header.

This filter is required for example when copying an AAC stream from a raw ADTS AAC or an MPEG-TS container to MP4A-LATM, to an FLV file, or to MOV/MP4 files and related formats such as 3GP or M4A. Please note that it is auto-inserted for MP4A-LATM and MOV/MP4 and related formats.

### 18.2 av1_metadata# TOC

Modify metadata embedded in an AV1 stream.

td

Insert or remove temporal delimiter OBUs in all temporal units of the stream.

‘insert’

Insert a TD at the beginning of every TU which does not already have one.

‘remove’

Remove the TD from the beginning of every TU which has one.

color_primaries

transfer_characteristics

matrix_coefficients

Set the color description fields in the stream (see AV1 section 6.4.2).

color_range

Set the color range in the stream (see AV1 section 6.4.2; note that this cannot be set for streams using BT.709 primaries, sRGB transfer characteristic and identity (RGB) matrix coefficients).

‘tv’

Limited range.

‘pc’

Full range.

chroma_sample_position

Set the chroma sample location in the stream (see AV1 section 6.4.2). This can only be set for 4:2:0 streams.

‘vertical’

Left position (matching the default in MPEG-2 and H.264).

‘colocated’

Top-left position.

tick_rate

Set the tick rate (time_scale / num_units_in_display_tick) in the timing info in the sequence header.

num_ticks_per_picture

Set the number of ticks in each picture, to indicate that the stream has a fixed framerate. Ignored if tick_rate is not also set.

delete_padding

Deletes Padding OBUs.

### 18.3 chomp# TOC

Remove zero padding at the end of a packet.

### 18.4 dca_core# TOC

Extract the core from a DCA/DTS stream, dropping extensions such as DTS-HD.

### 18.5 dovi_rpu# TOC

Manipulate Dolby Vision metadata in a HEVC/AV1 bitstream, optionally enabling metadata compression.

strip

If enabled, strip all Dolby Vision metadata (configuration record + RPU data blocks) from the stream.

compression

Which compression level to enable.

‘none’

No metadata compression.

‘limited’

Limited metadata compression scheme. Should be compatible with most devices. This is the default.

‘extended’

Extended metadata compression. Devices are not required to support this. Note that this level currently behaves the same as ‘limited’ in libavcodec.

### 18.6 dovi_split# TOC

Split a Dolby Vision Profile 7 multi-layer HEVC bitstream. Profile 7 carries the enhancement-layer HEVC bitstream interleaved inside the base-layer access units, wrapped in user-unspecified NAL units of type 63 (UNSPEC63), and the RPU metadata as a sibling user-unspecified NAL of type 62 (UNSPEC62).

mode

Which Dolby Vision components to keep in the output bitstream.

‘bl’

Base layer only: drop every UNSPEC63 (EL) and every UNSPEC62 (RPU). The output is a plain HEVC stream with no Dolby Vision markers. This is the default.

‘bl_rpu’

Base layer with the RPU NAL kept.

‘el’

Enhancement layer only: for every UNSPEC63 NAL, strip the two-byte outer NAL header and emit the inner payload. The result is a standalone HEVC bitstream. UNSPEC62 (RPU) is dropped.

‘el_rpu’

Enhancement layer with the RPU NAL kept verbatim. Same as ‘el’, but the UNSPEC62 RPU NALs are also emitted alongside the unwrapped EL NALs.

### 18.7 dump_extra# TOC

Add extradata to the beginning of the filtered packets except when said packets already exactly begin with the extradata that is intended to be added.

freq

The additional argument specifies which packets should be filtered. It accepts the values:

‘k’

‘keyframe’

add extradata to all key packets

‘e’

‘all’

add extradata to all packets

If not specified it is assumed ‘k’.

For example the following ffmpeg command forces a global header (thus disabling individual packet headers) in the H.264 packets generated by the libx264 encoder, but corrects them by adding the header stored in extradata to the key packets:

```
ffmpeg -i INPUT -map 0 -flags:v +global_header -c:v libx264 -bsf:v dump_extra out.ts

```

### 18.8 dv_error_marker# TOC

Blocks in DV which are marked as damaged are replaced by blocks of the specified color.

color

The color to replace damaged blocks by

sta

A 16 bit mask which specifies which of the 16 possible error status values are to be replaced by colored blocks. 0xFFFE is the default which replaces all non 0 error status values.

‘ok’

No error, no concealment

‘err’

Error, No concealment

‘res’

Reserved

‘notok’

Error or concealment

‘notres’

Not reserved

‘Aa, Ba, Ca, Ab, Bb, Cb, A, B, C, a, b, erri, erru’

The specific error status code

see page 44-46 or section 5.5 of http://web.archive.org/web/20060927044735/http://www.smpte.org/smpte_store/standards/pdf/s314m.pdf

### 18.9 eac3_core# TOC

Extract the core from a E-AC-3 stream, dropping extra channels.

### 18.10 eia608_to_smpte436m# TOC

Convert from a EIA_608 stream to a SMPTE_436M_ANC data stream, wrapping the closed captions in CTA-708 CDP VANC packets.

line_number

Choose which line number the generated VANC packets should go on. You generally want either line 9 (the default) or 11.

wrapping_type

Choose the SMPTE 436M wrapping type, defaults to ‘vanc_frame’. It accepts the values:

‘vanc_frame’

VANC frame (interlaced or segmented progressive frame)

‘vanc_field_1’

‘vanc_field_2’

‘vanc_progressive_frame’

sample_coding

Choose the SMPTE 436M sample coding, defaults to ‘8bit_luma’. It accepts the values:

‘8bit_luma’

8-bit component luma samples

‘8bit_color_diff’

8-bit component color difference samples

‘8bit_luma_and_color_diff’

8-bit component luma and color difference samples

‘10bit_luma’

10-bit component luma samples

‘10bit_color_diff’

10-bit component color difference samples

‘10bit_luma_and_color_diff’

10-bit component luma and color difference samples

‘8bit_luma_parity_error’

8-bit component luma samples with parity error

‘8bit_color_diff_parity_error’

8-bit component color difference samples with parity error

‘8bit_luma_and_color_diff_parity_error’

8-bit component luma and color difference samples with parity error

initial_cdp_sequence_cntr

The initial value of the CDP’s 16-bit unsigned integer cdp_hdr_sequence_cntr and cdp_ftr_sequence_cntr fields. Defaults to 0.

cdp_frame_rate

Set the CDP’s cdp_frame_rate field. This doesn’t actually change the timing of the data stream, it just changes the values inserted in that field in the generated CDP packets. Defaults to ‘30000/1001’.

### 18.11 extract_extradata# TOC

Extract the in-band extradata.

Certain codecs allow the long-term headers (e.g. MPEG-2 sequence headers, or H.264/HEVC (VPS/)SPS/PPS) to be transmitted either "in-band" (i.e. as a part of the bitstream containing the coded frames) or "out of band" (e.g. on the container level). This latter form is called "extradata" in FFmpeg terminology.

This bitstream filter detects the in-band headers and makes them available as extradata.

remove

When this option is enabled, the long-term headers are removed from the bitstream after extraction.

### 18.12 filter_units# TOC

Remove units with types in or not in a given set from the stream.

pass_types

List of unit types or ranges of unit types to pass through while removing all others. This is specified as a ’|’-separated list of unit type values or ranges of values with ’-’.

remove_types

Identical to pass_types, except the units in the given set removed and all others passed through.

The types used by pass_types and remove_types correspond to NAL unit types (nal_unit_type) in H.264, HEVC and H.266 (see Table 7-1 in the H.264 and HEVC specifications or Table 5 in the H.266 specification), to marker values for JPEG (without 0xFF prefix) and to start codes without start code prefix (i.e. the byte following the 0x000001) for MPEG-2. For VP8 and VP9, every unit has type zero.

Extradata is unchanged by this transformation, but note that if the stream contains inline parameter sets then the output may be unusable if they are removed.

For example, to remove all non-VCL NAL units from an H.264 stream:

```
ffmpeg -i INPUT -c:v copy -bsf:v 'filter_units=pass_types=1-5' OUTPUT

```

To remove all AUDs, SEI and filler from an H.265 stream:

```
ffmpeg -i INPUT -c:v copy -bsf:v 'filter_units=remove_types=35|38-40' OUTPUT

```

To remove all user data from a MPEG-2 stream, including Closed Captions:

```
ffmpeg -i INPUT -c:v copy -bsf:v 'filter_units=remove_types=178' OUTPUT

```

To remove all SEI from a H264 stream, including Closed Captions:

```
ffmpeg -i INPUT -c:v copy -bsf:v 'filter_units=remove_types=6' OUTPUT

```

To remove all prefix and suffix SEI from a HEVC stream, including Closed Captions and dynamic HDR:

```
ffmpeg -i INPUT -c:v copy -bsf:v 'filter_units=remove_types=39|40' OUTPUT

```

### 18.13 hapqa_extract# TOC

Extract Rgb or Alpha part of an HAPQA file, without recompression, in order to create an HAPQ or an HAPAlphaOnly file.

texture

Specifies the texture to keep.

color

alpha

Convert HAPQA to HAPQ

```
ffmpeg -i hapqa_inputfile.mov -c copy -bsf:v hapqa_extract=texture=color -tag:v HapY -metadata:s:v:0 encoder="HAPQ" hapq_file.mov

```

Convert HAPQA to HAPAlphaOnly

```
ffmpeg -i hapqa_inputfile.mov -c copy -bsf:v hapqa_extract=texture=alpha -tag:v HapA -metadata:s:v:0 encoder="HAPAlpha Only" hapalphaonly_file.mov

```

### 18.14 h264_metadata# TOC

Modify metadata embedded in an H.264 stream.

aud

Insert or remove AUD NAL units in all access units of the stream.

‘pass’

‘insert’

‘remove’

Default is pass.

sample_aspect_ratio

Set the sample aspect ratio of the stream in the VUI parameters. See H.264 table E-1.

overscan_appropriate_flag

Set whether the stream is suitable for display using overscan or not (see H.264 section E.2.1).

video_format

video_full_range_flag

Set the video format in the stream (see H.264 section E.2.1 and table E-2).

colour_primaries

transfer_characteristics

matrix_coefficients

Set the colour description in the stream (see H.264 section E.2.1 and tables E-3, E-4 and E-5).

chroma_sample_loc_type

Set the chroma sample location in the stream (see H.264 section E.2.1 and figure E-1).

tick_rate

Set the tick rate (time_scale / num_units_in_tick) in the VUI parameters. This is the smallest time unit representable in the stream, and in many cases represents the field rate of the stream (double the frame rate).

fixed_frame_rate_flag

Set whether the stream has fixed framerate - typically this indicates that the framerate is exactly half the tick rate, but the exact meaning is dependent on interlacing and the picture structure (see H.264 section E.2.1 and table E-6).

zero_new_constraint_set_flags

Zero constraint_set4_flag and constraint_set5_flag in the SPS. These bits were reserved in a previous version of the H.264 spec, and thus some hardware decoders require these to be zero. The result of zeroing this is still a valid bitstream.

crop_left

crop_right

crop_top

crop_bottom

Set the frame cropping offsets in the SPS. These values will replace the current ones if the stream is already cropped.

These fields are set in pixels. Note that some sizes may not be representable if the chroma is subsampled or the stream is interlaced (see H.264 section 7.4.2.1.1).

sei_user_data

Insert a string as SEI unregistered user data. The argument must be of the form UUID+string, where the UUID is as hex digits possibly separated by hyphens, and the string can be anything.

For example, ‘086f3693-b7b3-4f2c-9653-21492feee5b8+hello’ will insert the string “hello” associated with the given UUID.

delete_filler

Deletes both filler NAL units and filler SEI messages.

display_orientation

Insert, extract or remove Display orientation SEI messages. See H.264 section D.1.27 and D.2.27 for syntax and semantics.

‘pass’

‘insert’

‘remove’

‘extract’

Default is pass.

Insert mode works in conjunction with rotate and flip options. Any pre-existing Display orientation messages will be removed in insert or remove mode. Extract mode attaches the display matrix to the packet as side data.

rotate

Set rotation in display orientation SEI (anticlockwise angle in degrees). Range is -360 to +360. Default is NaN.

flip

Set flip in display orientation SEI.

‘horizontal’

‘vertical’

Default is unset.

level

Set the level in the SPS. Refer to H.264 section A.3 and tables A-1 to A-5.

The argument must be the name of a level (for example, ‘4.2’), a level_idc value (for example, ‘42’), or the special name ‘auto’ indicating that the filter should attempt to guess the level from the input stream properties.

### 18.15 h264_mp4toannexb# TOC

Convert an H.264 bitstream from length prefixed mode to start code prefixed mode (as defined in the Annex B of the ITU-T H.264 specification).

This is required by some streaming formats, typically the MPEG-2 transport stream format (muxer mpegts).

For example to remux an MP4 file containing an H.264 stream to mpegts format with ffmpeg, you can use the command:

```
ffmpeg -i INPUT.mp4 -codec copy -bsf:v h264_mp4toannexb OUTPUT.ts

```

Please note that this filter is auto-inserted for MPEG-TS (muxer mpegts) and raw H.264 (muxer h264) output formats.

### 18.16 h264_redundant_pps# TOC

This applies a specific fixup to some Blu-ray BDMV H264 streams which contain redundant PPSs. The PPSs modify irrelevant parameters of the stream, confusing other transformations which require the correct extradata.

The encoder used on these impacted streams adds extra PPSs throughout the stream, varying the initial QP and whether weighted prediction was enabled. This causes issues after copying the stream into a global header container, as the starting PPS is not suitable for the rest of the stream. One side effect, for example, is seeking will return garbled output until a new PPS appears.

This BSF removes the extra PPSs and rewrites the slice headers such that the stream uses a single leading PPS in the global header, which resolves the issue.

### 18.17 hevc_metadata# TOC

Modify metadata embedded in an HEVC stream.

aud

Insert or remove AUD NAL units in all access units of the stream.

‘insert’

‘remove’

sample_aspect_ratio

Set the sample aspect ratio in the stream in the VUI parameters.

video_format

video_full_range_flag

Set the video format in the stream (see H.265 section E.3.1 and table E.2).

colour_primaries

transfer_characteristics

matrix_coefficients

Set the colour description in the stream (see H.265 section E.3.1 and tables E.3, E.4 and E.5).

chroma_sample_loc_type

Set the chroma sample location in the stream (see H.265 section E.3.1 and figure E.1).

tick_rate

Set the tick rate in the VPS and VUI parameters (time_scale / num_units_in_tick). Combined with num_ticks_poc_diff_one, this can set a constant framerate in the stream. Note that it is likely to be overridden by container parameters when the stream is in a container.

num_ticks_poc_diff_one

Set poc_proportional_to_timing_flag in VPS and VUI and use this value to set num_ticks_poc_diff_one_minus1 (see H.265 sections 7.4.3.1 and E.3.1). Ignored if tick_rate is not also set.

crop_left

crop_right

crop_top

crop_bottom

Set the conformance window cropping offsets in the SPS. These values will replace the current ones if the stream is already cropped.

These fields are set in pixels. Note that some sizes may not be representable if the chroma is subsampled (H.265 section 7.4.3.2.1).

width

height

Set width and height after crop.

level

Set the level in the VPS and SPS. See H.265 section A.4 and tables A.6 and A.7.

The argument must be the name of a level (for example, ‘5.1’), a general_level_idc value (for example, ‘153’ for level 5.1), or the special name ‘auto’ indicating that the filter should attempt to guess the level from the input stream properties.

### 18.18 hevc_mp4toannexb# TOC

Convert an HEVC/H.265 bitstream from length prefixed mode to start code prefixed mode (as defined in the Annex B of the ITU-T H.265 specification).

This is required by some streaming formats, typically the MPEG-2 transport stream format (muxer mpegts).

For example to remux an MP4 file containing an HEVC stream to mpegts format with ffmpeg, you can use the command:

```
ffmpeg -i INPUT.mp4 -codec copy -bsf:v hevc_mp4toannexb OUTPUT.ts

```

Please note that this filter is auto-inserted for MPEG-TS (muxer mpegts) and raw HEVC/H.265 (muxer h265 or hevc) output formats.

### 18.19 imxdump# TOC

Modifies the bitstream to fit in MOV and to be usable by the Final Cut Pro decoder. This filter only applies to the mpeg2video codec, and is likely not needed for Final Cut Pro 7 and newer with the appropriate -tag:v.

For example, to remux 30 MB/sec NTSC IMX to MOV:

```
ffmpeg -i input.mxf -c copy -bsf:v imxdump -tag:v mx3n output.mov

```

### 18.20 jpegapp# TOC

Inject JPEG APP0..APP15 segments from a length-prefixed sidecar into each MJPEG packet, after SOI.

The sidecar is a sequence of records, one per encoded JPEG, in encode order:

```
u32be length
u8    payload[length]

```

length does not include the 4-byte prefix and must not exceed 16 MiB. A zero length leaves that packet unchanged. A non-empty payload must be a concatenation of complete APP segments (FF En plus the 16-bit length that includes those two length bytes).

If the payload starts with APP0 and the packet has an APP0 marker in the two bytes immediately following SOI, that APP0 segment is dropped. APP0 segments preceded by fill bytes or another segment are retained. An APP1-only payload keeps the encoder APP0: SOI, APP1, APP0, DQT, ...

The filter requires sidecar. Extra unused sidecar bytes are ignored; a packet without a matching record is an error. Records follow packets in arrival order. Flushing the filter does not rewind the sidecar, so a reused context needs a sidecar positioned for the packets it will see next. A sidecar read or validation error prevents further record consumption by that filter context. To resume, create a new context with a sidecar matching the remaining packets. Flushing does not clear this error.

```
ffmpeg -i in.mp4 -c:v mjpeg -bsf:v jpegapp=sidecar=00000004DEADBEEF frame_%d.jpg

```

### 18.21 mjpeg2jpeg# TOC

Convert MJPEG/AVI1 packets to full JPEG/JFIF packets.

MJPEG is a video codec wherein each video frame is essentially a JPEG image. The individual frames can be extracted without loss, e.g. by

```
ffmpeg -i ../some_mjpeg.avi -c:v copy frames_%d.jpg

```

Unfortunately, these chunks are incomplete JPEG images, because they lack the DHT segment required for decoding. Quoting from http://www.digitalpreservation.gov/formats/fdd/fdd000063.shtml:

Avery Lee, writing in the rec.video.desktop newsgroup in 2001, commented that "MJPEG, or at least the MJPEG in AVIs having the MJPG fourcc, is restricted JPEG with a fixed – and *omitted* – Huffman table. The JPEG must be YCbCr colorspace, it must be 4:2:2, and it must use basic Huffman encoding, not arithmetic or progressive. . . . You can indeed extract the MJPEG frames and decode them with a regular JPEG decoder, but you have to prepend the DHT segment to them, or else the decoder won’t have any idea how to decompress the data. The exact table necessary is given in the OpenDML spec."

This bitstream filter patches the header of frames extracted from an MJPEG stream (carrying the AVI1 header ID and lacking a DHT segment) to produce fully qualified JPEG images.

```
ffmpeg -i mjpeg-movie.avi -c:v copy -bsf:v mjpeg2jpeg frame_%d.jpg
exiftran -i -9 frame*.jpg
ffmpeg -i frame_%d.jpg -c:v copy rotated.avi

```

### 18.22 mjpegadump# TOC

Add an MJPEG A header to the bitstream, to enable decoding by Quicktime.

### 18.23 mov2textsub# TOC

Extract a representable text file from MOV subtitles, stripping the metadata header from each subtitle packet.

See also the text2movsub filter.

### 18.24 mpeg2_metadata# TOC

Modify metadata embedded in an MPEG-2 stream.

display_aspect_ratio

Set the display aspect ratio in the stream.

The following fixed values are supported:

4/3

16/9

221/100

Any other value will result in square pixels being signalled instead (see H.262 section 6.3.3 and table 6-3).

frame_rate

Set the frame rate in the stream. This is constructed from a table of known values combined with a small multiplier and divisor - if the supplied value is not exactly representable, the nearest representable value will be used instead (see H.262 section 6.3.3 and table 6-4).

video_format

Set the video format in the stream (see H.262 section 6.3.6 and table 6-6).

colour_primaries

transfer_characteristics

matrix_coefficients

Set the colour description in the stream (see H.262 section 6.3.6 and tables 6-7, 6-8 and 6-9).

### 18.25 mpeg4_unpack_bframes# TOC

Unpack DivX-style packed B-frames.

DivX-style packed B-frames are not valid MPEG-4 and were only a workaround for the broken Video for Windows subsystem. They use more space, can cause minor AV sync issues, require more CPU power to decode (unless the player has some decoded picture queue to compensate the 2,0,2,0 frame per packet style) and cause trouble if copied into a standard container like mp4 or mpeg-ps/ts, because MPEG-4 decoders may not be able to decode them, since they are not valid MPEG-4.

For example to fix an AVI file containing an MPEG-4 stream with DivX-style packed B-frames using ffmpeg, you can use the command:

```
ffmpeg -i INPUT.avi -codec copy -bsf:v mpeg4_unpack_bframes OUTPUT.avi

```

### 18.26 noise# TOC

Damages the contents of packets or simply drops them without damaging the container. Can be used for fuzzing or testing error resilience/concealment.

Parameters:

amount

Accepts an expression whose evaluation per-packet determines how often bytes in that packet will be modified. A value below 0 will result in a variable frequency. Default is 0 which results in no modification. However, if neither amount nor drop is specified, amount will be set to -1. See below for accepted variables.

drop

Accepts an expression evaluated per-packet whose value determines whether that packet is dropped. Evaluation to a positive value results in the packet being dropped. Evaluation to a negative value results in a variable chance of it being dropped, roughly inverse in proportion to the magnitude of the value. Default is 0 which results in no drops. See below for accepted variables.

dropamount

Accepts a non-negative integer, which assigns a variable chance of it being dropped, roughly inverse in proportion to the value. Default is 0 which results in no drops. This option is kept for backwards compatibility and is equivalent to setting drop to a negative value with the same magnitude i.e. dropamount=4 is the same as drop=-4. Ignored if drop is also specified.

Both amount and drop accept expressions containing the following variables:

‘n’

The index of the packet, starting from zero.

‘tb’

The timebase for packet timestamps.

‘pts’

Packet presentation timestamp.

‘dts’

Packet decoding timestamp.

‘nopts’

Constant representing AV_NOPTS_VALUE.

‘startpts’

First non-AV_NOPTS_VALUE PTS seen in the stream.

‘startdts’

First non-AV_NOPTS_VALUE DTS seen in the stream.

‘duration’

‘d’

Packet duration, in timebase units.

‘pos’

Packet position in input; may be -1 when unknown or not set.

‘size’

Packet size, in bytes.

‘key’

Whether packet is marked as a keyframe.

‘state’

A pseudo random integer, primarily derived from the content of packet payload.

#### 18.26.1 Examples# TOC

Apply modification to every byte but don’t drop any packets.

```
ffmpeg -i INPUT -c copy -bsf noise=1 output.mkv

```

Drop every video packet not marked as a keyframe after timestamp 30s but do not modify any of the remaining packets.

```
ffmpeg -i INPUT -c copy -bsf:v noise=drop='gt(pts*tb\,30)*not(key)' output.mkv

```

Drop one second of audio every 10 seconds and add some random noise to the rest.

```
ffmpeg -i INPUT -c copy -bsf:a noise=amount=-1:drop='between(mod(pts*tb\,10)\,9\,10)' output.mkv

```

### 18.27 null# TOC

This bitstream filter passes the packets through unchanged.

### 18.28 pcm_rechunk# TOC

Repacketize PCM audio to a fixed number of samples per packet or a fixed packet rate per second. This is similar to the asetnsamples audio filter but works on audio packets instead of audio frames.

nb_out_samples, n

Set the number of samples per each output audio packet. The number is intended as the number of samples per each channel. Default value is 1024.

pad, p

If set to 1, the filter will pad the last audio packet with silence, so that it will contain the same number of samples (or roughly the same number of samples, see frame_rate) as the previous ones. Default value is 1.

frame_rate, r

This option makes the filter output a fixed number of packets per second instead of a fixed number of samples per packet. If the audio sample rate is not divisible by the frame rate then the number of samples will not be constant but will vary slightly so that each packet will start as close to the frame boundary as possible. Using this option has precedence over nb_out_samples.

You can generate the well known 1602-1601-1602-1601-1602 pattern of 48kHz audio for NTSC frame rate using the frame_rate option.

```
ffmpeg -f lavfi -i sine=r=48000:d=1 -c pcm_s16le -bsf pcm_rechunk=r=30000/1001 -f framecrc -

```

### 18.29 pgs_frame_merge# TOC

Merge a sequence of PGS Subtitle segments ending with an "end of display set" segment into a single packet.

This is required by some containers that support PGS subtitles (muxer matroska).

### 18.30 prores_metadata# TOC

Modify color property metadata embedded in prores stream.

color_primaries

Set the color primaries. Available values are:

‘auto’

Keep the same color primaries property (default).

‘unknown’

‘bt709’

‘bt470bg’

BT601 625

‘smpte170m’

BT601 525

‘bt2020’

‘smpte431’

DCI P3

‘smpte432’

P3 D65

transfer_characteristics

Set the color transfer. Available values are:

‘auto’

Keep the same transfer characteristics property (default).

‘unknown’

‘bt709’

BT 601, BT 709, BT 2020

‘smpte2084’

SMPTE ST 2084

‘arib-std-b67’

ARIB STD-B67

matrix_coefficients

Set the matrix coefficient. Available values are:

‘auto’

Keep the same colorspace property (default).

‘unknown’

‘bt709’

‘smpte170m’

BT 601

‘bt2020nc’

Set Rec709 colorspace for each frame of the file

```
ffmpeg -i INPUT -c copy -bsf:v prores_metadata=color_primaries=bt709:color_trc=bt709:colorspace=bt709 output.mov

```

Set Hybrid Log-Gamma parameters for each frame of the file

```
ffmpeg -i INPUT -c copy -bsf:v prores_metadata=color_primaries=bt2020:color_trc=arib-std-b67:colorspace=bt2020nc output.mov

```

### 18.31 remove_extra# TOC

Remove extradata from packets.

It accepts the following parameter:

freq

Set which frame types to remove extradata from.

‘k’

Remove extradata from non-keyframes only.

‘keyframe’

Remove extradata from keyframes only.

‘e, all’

Remove extradata from all frames.

### 18.32 setts# TOC

Set PTS and DTS in packets.

It accepts the following parameters:

ts

pts

dts

Set expressions for PTS, DTS or both.

duration

Set expression for duration.

time_base

Set output time base.

prescale

Set whether to convert time fields to user-set output time base before evaluation of expressions. Defaults to 0.

The expressions are evaluated through the eval API and can contain the following constants:

N

The count of the input packet. Starting from 0.

TS

The demux timestamp in input in case of ts or dts option or presentation timestamp in case of pts option.

POS

The original position in the file of the packet, or undefined if undefined for the current packet

DTS

The demux timestamp in input.

PTS

The presentation timestamp in input.

DURATION

The duration in input.

STARTDTS

The DTS of the first packet.

STARTPTS

The PTS of the first packet.

PREV_INDTS

The previous input DTS.

PREV_INPTS

The previous input PTS.

PREV_INDURATION

The previous input duration.

PREV_OUTDTS

The previous output DTS.

PREV_OUTPTS

The previous output PTS.

PREV_OUTDURATION

The previous output duration.

NEXT_DTS

The next input DTS.

NEXT_PTS

The next input PTS.

NEXT_DURATION

The next input duration.

TB

The timebase in which time fields are denominated. The user-set output timebase if prescale is enabled, else the input timebase.

TB_OUT

The output timebase.

SR

The sample rate of stream packet belongs.

NOPTS

The AV_NOPTS_VALUE constant.

For example, to set PTS equal to DTS (not recommended if B-frames are involved):

```
ffmpeg -i INPUT -c:a copy -bsf:a setts=pts=DTS out.mkv

```

### 18.33 showinfo# TOC

Log basic packet information. Mainly useful for testing, debugging, and development.

### 18.34 side_data# TOC

Remove side data from packets and from the stream, or select packets by their side data.

It accepts the following parameters:

remove

Set the side data types to remove, joined with ‘+’, from the packets and from the side data of the stream. Each type is given by its handle; ffmpeg -h bsf=side_data lists them.

select

Set the side data types of the packets to keep, joined with ‘+’. A packet is kept if it carries any of them, and dropped otherwise. The selection looks at the side data before remove applies. Dropping a packet breaks the decoding of the packets that depend on it, so this is meant for analysis or for streams where each packet decodes on its own.

For example, to drop the display matrix and the replay gain of a stream:

```
ffmpeg -i INPUT -c copy -bsf:v side_data=remove=displaymatrix+replaygain output.mkv

```

### 18.35 smpte436m_to_eia608# TOC

Convert from a SMPTE_436M_ANC data stream to a EIA_608 stream, extracting the closed captions from CTA-708 CDP VANC packets, and ignoring all other data.

### 18.36 text2movsub# TOC

Convert text subtitles to MOV subtitles (as used by the mov_text codec) with metadata headers.

See also the mov2textsub filter.

### 18.37 trace_headers# TOC

Log trace output containing all syntax elements in the coded stream headers (everything above the level of individual coded blocks). This can be useful for debugging low-level stream issues.

Supports AV1, H.264, H.265, (M)JPEG, MPEG-2 and VP9, but depending on the build only a subset of these may be available.

### 18.38 trim# TOC

Drop packets outside a given range, similar to the trim and atrim filters, but operating on packets instead of decoded frames.

The range is described by a start and an end bound. At least one of them must be set. Each bound is fully described by three independent choices:

- The discriminant it is compared against: the packet’s presentation timestamp, its decoding timestamp, or its index. The two bounds need not use the same one, for instance a dts start with a pts end.

- The unit its value is given in: the stream time base, milliseconds, or packets.

- What it is counted from: zero, or its reference packet when start_rel / end_rel is set. For start the reference packet is the first packet carrying that discriminant. For end it is the first exported packet.

The start_type and end_type options name a combination of the three. The dur_ts and dur_t_msec end types are the always relative forms of pts and msec_pt. A zero duration therefore produces an empty stream.

Every packet is judged on its own discriminant, and on nothing else. A packet not carrying the discriminant its bound uses cannot be placed, and is dropped.

start_rel makes start an offset from a reference packet instead of an absolute value. The reference is the first packet carrying the discriminant that bound uses. Its value is added to the offset once, and the bound stays there for the rest of the stream.

end_rel anchors on the first exported packet instead, at the position start trimmed it to. The two bounds therefore move together.

Only a discriminant that cannot come back into the range ends the stream, namely the packet index or the decoding timestamp. End of stream is signaled once one of those passes the end bound. A presentation timestamp past the end only drops its packet, so that later packets still inside the range are not lost.

A bound given in a time unit can fall inside a packet rather than between two. Such a packet is trimmed. Set trim_packets to false to keep every packet exactly as it came in: exported whole if its own value is inside the range, dropped otherwise.

Audio is trimmed in sample space, through skip samples side data. The timestamps and duration are left untouched, and a decoder discards the signaled samples on output. This needs a sample rate and a time base. Audio missing either is rejected rather than trimmed on the timeline. Every other media type is trimmed by shifting the packet timestamps and shortening its duration.

Trimming inside an audio packet needs the number of samples it decodes to. Where the codec does not give that number, the packet is handled as though trim_packets were false.

A skip larger than the packet carrying it continues into the packets after it. Dropping such a packet carries the remainder over to the next one. A skip that packet already carries replaces the remainder, as a decoder would, and the larger of it and this filter’s own trim wins.

By default a packet outside the range is dropped, whether or not later packets depend on it. Streams of independent frames, such as ADTS or intra only video, can be cut anywhere. Cutting an inter coded stream inside a group of pictures leaves the first packets in range undecodable.

Set preroll to export the packets those first packets depend on as well. They are flagged for a decoder to decode and then drop, so the frames it outputs still begin at the start bound. Only a decoder acts on that flag. Use preroll where the stream is decoded. A muxer writes the extra packets like any other. A remux then covers more than the requested range.

preroll covers the start of the range only. On a stream with B-frames an end bound on the presentation timestamp can drop a packet the last frames in the range need. Those frames then decode incorrectly.

It accepts the following parameters:

start

Time or index marking the start of the accepted range. Packets before it are dropped. A packet straddling it is trimmed at its start, or dropped when trim_packets is false.

start_type

How to interpret start:

‘pts’

Presentation timestamp, in stream time base (default).

‘dts’

Decoding timestamp, in stream time base.

‘pkt_index’

Packet index, counting from zero.

‘msec_pt’

Milliseconds, matched against the presentation timestamp.

‘msec_dt’

Milliseconds, matched against the decoding timestamp.

start_rel

Count start from the reference packet rather than from zero. Has no effect on ‘pkt_index’, whose first packet is already zero. Default false.

end

Time or index marking the end of the accepted range. Signals end of stream when reached. A packet straddling it is trimmed at its end, or exported untouched when trim_packets is false.

end_type

How to interpret end. Same values as start_type, plus:

‘dur_ts’

Duration in stream time base. Same as ‘pts’ with end_rel set.

‘dur_t_msec’

Duration in milliseconds. Same as ‘msec_pt’ with end_rel set.

end_rel

Count end from the first exported packet rather than from zero. The reference is that packet’s value on the discriminant end_type names. On a timestamp it is taken at the position the packet is trimmed to. For audio that is the time of its first retained sample. The skip that packet carries can push it past the packet itself. With ‘pkt_index’ it exports a fixed number of packets, which can be combined with a timestamp-based start. Always set for the duration types. Default false.

trim_packets

Trim packets straddling a boundary. When false, packets are exported exactly as they came in, with no timestamp adjustment and no skip samples side data. A packet is then exported untouched if its value falls inside the range, and dropped otherwise. Default true.

preroll

Export the packets a decoder needs to decode the first packet in range, rather than dropping them for falling before the start bound. The filter holds every packet from the last keyframe on. It exports them ahead of the first packet in range, carrying AV_PKT_FLAG_DISCARD.

Video only. Default false.

preroll_size

Maximum number of packets held for preroll. A group of pictures longer than this is dropped whole, with a warning naming the count to raise it past. Default 300, which covers the keyframe intervals encoders commonly default to.

For example, to keep only the 10 first packets of an ADTS stream:

```
ffmpeg -i INPUT.aac -c copy -bsf:a trim=end=10:end_type=pkt_index OUTPUT.aac

```

To keep 5 seconds starting 1.5 seconds into the stream:

```
ffmpeg -i INPUT.aac -c copy -bsf:a trim=start=1500:start_type=msec_pt:end=5000:end_type=dur_t_msec OUTPUT.aac

```

The same, expressed relative to the first packet so it works regardless of the stream’s starting timestamp:

```
ffmpeg -i INPUT.aac -c copy -bsf:a trim=start=1500:start_type=msec_pt:start_rel=1:end=5000:end_type=dur_t_msec OUTPUT.aac

```

To start on a keyframeless point of an inter coded video stream, re-encoding it so that the preroll is decoded rather than written out. The filter must run before the decoder, so it is given before the input:

```
ffmpeg -bsf:v trim=start=17000:start_type=msec_pt:end=30000:end_type=dur_t_msec:preroll=1 -i INPUT.mp4 OUTPUT.mp4

```

### 18.39 truehd_core# TOC

Extract the core from a TrueHD stream, dropping ATMOS data.

### 18.40 vp9_metadata# TOC

Modify metadata embedded in a VP9 stream.

color_space

Set the color space value in the frame header. Note that any frame set to RGB will be implicitly set to PC range and that RGB is incompatible with profiles 0 and 2.

‘unknown’

‘bt601’

‘bt709’

‘smpte170’

‘smpte240’

‘bt2020’

‘rgb’

color_range

Set the color range value in the frame header. Note that any value imposed by the color space will take precedence over this value.

‘tv’

‘pc’

### 18.41 vp9_superframe# TOC

Merge VP9 invisible (alt-ref) frames back into VP9 superframes. This fixes merging of split/segmented VP9 streams where the alt-ref frame was split from its visible counterpart.

### 18.42 vp9_superframe_split# TOC

Split VP9 superframes into single frames.

### 18.43 vp9_raw_reorder# TOC

Given a VP9 stream with correct timestamps but possibly out of order, insert additional show-existing-frame packets to correct the ordering.

## 19 Format Options# TOC

The libavformat library provides some generic global options, which can be set on all the muxers and demuxers. In addition each muxer or demuxer may support so-called private options, which are specific for that component.

Options may be set by specifying -option value in the FFmpeg tools, or by setting the value explicitly in the AVFormatContext options or using the libavutil/opt.h API for programmatic use.

The list of supported options follows:

avioflags flags (input/output)

Possible values:

‘direct’

Reduce buffering.

probesize integer (input)

Set probing size in bytes, i.e. the size of the data to analyze to get stream information. A higher value will enable detecting more information in case it is dispersed into the stream, but will increase latency. Must be an integer not lesser than 32. It is 5000000 by default.

max_probe_packets integer (input)

Set the maximum number of buffered packets when probing a codec. Default is 2500 packets.

packetsize integer (output)

Set packet size.

fflags flags

Set format flags. Some are implemented for a limited number of formats.

Possible values for input files:

‘discardcorrupt’

Discard corrupted packets.

‘fastseek’

Enable fast, but inaccurate seeks for some formats.

‘genpts’

Generate missing PTS if DTS is present.

‘igndts’

Ignore DTS if PTS is also set. In case the PTS is set, the DTS value is set to NOPTS. This is ignored when the nofillin flag is set.

‘ignidx’

Ignore index.

‘nobuffer’

Reduce the latency introduced by buffering during initial input streams analysis.

‘nofillin’

Do not fill in missing values in packet fields that can be exactly calculated.

‘noparse’

Disable AVParsers, this needs +nofillin too.

‘sortdts’

Try to interleave output packets by DTS. At present, available only for AVIs with an index.

Possible values for output files:

‘autobsf’

Automatically apply bitstream filters as required by the output format. Enabled by default.

‘bitexact’

Only write platform-, build- and time-independent data. This ensures that file and data checksums are reproducible and match between platforms. Its primary use is for regression testing.

‘flush_packets’

Write out packets immediately.

‘shortest’

Stop muxing at the end of the shortest stream. It may be needed to increase max_interleave_delta to avoid flushing the longer streams before EOF.

seek2any integer (input)

Allow seeking to non-keyframes on demuxer level when supported if set to 1. Default is 0.

analyzeduration integer (input)

Specify how many microseconds are analyzed to probe the input. A higher value will enable detecting more accurate information, but will increase latency. It defaults to 5,000,000 microseconds = 5 seconds.

cryptokey hexadecimal string (input)

Set decryption key.

indexmem integer (input)

Set max memory used for timestamp index (per stream).

rtbufsize integer (input)

Set max memory used for buffering real-time frames.

fdebug flags (input/output)

Print specific debug info.

Possible values:

‘ts’

Print timestamp information.

‘id3v2’

Print ID3v2 frame data when demuxing files containing ID3v2 tags.

max_delay integer (input/output)

Set maximum muxing or demuxing delay in microseconds.

fpsprobesize integer (input)

Set number of frames used to probe fps.

audio_preload integer (output)

Set microseconds by which audio packets should be interleaved earlier.

chunk_duration integer (output)

Set microseconds for each chunk.

chunk_size integer (output)

Set size in bytes for each chunk.

err_detect, f_err_detect flags (input)

Set error detection flags. f_err_detect is deprecated and should be used only via the ffmpeg tool.

Possible values:

‘crccheck’

Verify embedded CRCs.

‘bitstream’

Detect bitstream specification deviations.

‘buffer’

Detect improper bitstream length.

‘explode’

Abort decoding on minor error detection.

‘careful’

Consider things that violate the spec and have not been seen in the wild as errors.

‘compliant’

Consider all spec non compliancies as errors.

‘aggressive’

Consider things that a sane encoder should not do as an error.

max_interleave_delta integer (output)

Set maximum buffering duration for interleaving. The duration is expressed in microseconds, and defaults to 10000000 (10 seconds).

To ensure all the streams are interleaved correctly, libavformat will wait until it has at least one packet for each stream before actually writing any packets to the output file. When some streams are "sparse" (i.e. there are large gaps between successive packets), this can result in excessive buffering.

This field specifies the maximum difference between the timestamps of the first and the last packet in the muxing queue, above which libavformat will output a packet regardless of whether it has queued a packet for all the streams.

If set to 0, libavformat will continue buffering packets until it has a packet for each stream, regardless of the maximum timestamp difference between the buffered packets.

use_wallclock_as_timestamps integer (input)

Use wallclock as timestamps if set to 1. Default is 0.

avoid_negative_ts integer (output)

Possible values:

‘make_non_negative’

Shift timestamps to make them non-negative. Also note that this affects only leading negative timestamps, and not non-monotonic negative timestamps.

‘make_zero’

Shift timestamps so that the first timestamp is 0.

‘auto (default)’

Enables shifting when required by the target format.

‘disabled’

Disables shifting of timestamp.

When shifting is enabled, all output timestamps are shifted by the same amount. Audio, video, and subtitles desynching and relative timestamp differences are preserved compared to how they would have been without shifting.

skip_initial_bytes integer (input)

Set number of bytes to skip before reading header and frames if set to 1. Default is 0.

correct_ts_overflow integer (input)

Correct single timestamp overflows if set to 1. Default is 1.

flush_packets integer (output)

Flush the underlying I/O stream after each packet. Default is -1 (auto), which means that the underlying protocol will decide, 1 enables it, and has the effect of reducing the latency, 0 disables it and may increase IO throughput in some cases.

output_ts_offset offset (output)

Set the output time offset.

offset must be a time duration specification, see the Time duration section in the ffmpeg-utils(1) manual.

The offset is added by the muxer to the output timestamps.

Specifying a positive offset means that the corresponding streams are delayed bt the time duration specified in offset. Default value is 0 (meaning that no offset is applied).

format_whitelist list (input)

"," separated list of allowed demuxers. By default all are allowed.

dump_separator string (input)

Separator used to separate the fields printed on the command line about the Stream parameters. For example, to separate the fields with newlines and indentation:

```
ffprobe -dump_separator "
                          "  -i ~/videos/matrixbench_mpeg2.mpg

```

max_streams integer (input)

Specifies the maximum number of streams. This can be used to reject files that would require too many resources due to a large number of streams.

skip_estimate_duration_from_pts bool (input)

Skip estimation of input duration if it requires an additional probing for PTS at end of file. At present, applicable for MPEG-PS and MPEG-TS.

duration_probesize integer (input)

Set probing size, in bytes, for input duration estimation when it actually requires an additional probing for PTS at end of file (at present: MPEG-PS and MPEG-TS). It is aimed at users interested in better durations probing for itself, or indirectly because using the concat demuxer, for example. The typical use case is an MPEG-TS CBR with a high bitrate, high video buffering and ending cleaning with similar PTS for video and audio: in such a scenario, the large physical gap between the last video packet and the last audio packet makes it necessary to read many bytes in order to get the video stream duration. Another use case is where the default probing behaviour only reaches a single video frame which is not the last one of the stream due to frame reordering, so the duration is not accurate. Setting this option has a performance impact even for small files because the probing size is fixed. Default behaviour is a general purpose trade-off, largely adaptive, but the probing size will not be extended to get streams durations at all costs. Must be an integer not lesser than 1, or 0 for default behaviour.

strict, f_strict integer (input/output)

Specify how strictly to follow the standards. f_strict is deprecated and should be used only via the ffmpeg tool.

Possible values:

‘very’

strictly conform to an older more strict version of the spec or reference software

‘strict’

strictly conform to all the things in the spec no matter what consequences

‘normal’

‘unofficial’

allow unofficial extensions

‘experimental’

allow non standardized experimental things, experimental (unfinished/work in progress/not well tested) decoders and encoders. Note: experimental decoders can pose a security risk, do not use this for decoding untrusted input.

### 19.1 Format stream specifiers# TOC

Format stream specifiers allow selection of one or more streams that match specific properties.

The exact semantics of stream specifiers is defined by the avformat_match_stream_specifier() function declared in the libavformat/avformat.h header and documented in the Stream specifiers section in the ffmpeg(1) manual.

## 20 Demuxers# TOC

Demuxers are configured elements in FFmpeg that can read the multimedia streams from a particular type of file.

When you configure your FFmpeg build, all the supported demuxers are enabled by default. You can list all available ones using the configure option --list-demuxers.

You can disable all the demuxers using the configure option --disable-demuxers, and selectively enable a single demuxer with the option --enable-demuxer=DEMUXER, or disable it with the option --disable-demuxer=DEMUXER.

The option -demuxers of the ff* tools will display the list of enabled demuxers. Use -formats to view a combined list of enabled demuxers and muxers.

The description of some of the currently available demuxers follows.

### 20.1 aa# TOC

Audible Format 2, 3, and 4 demuxer.

This demuxer is used to demux Audible Format 2, 3, and 4 (.aa) files.

### 20.2 aac# TOC

Raw Audio Data Transport Stream AAC demuxer.

This demuxer is used to demux an ADTS input containing a single AAC stream alongwith any ID3v1/2 or APE tags in it.

### 20.3 apng# TOC

Animated Portable Network Graphics demuxer.

This demuxer is used to demux APNG files. All headers, but the PNG signature, up to (but not including) the first fcTL chunk are transmitted as extradata. Frames are then split as being all the chunks between two fcTL ones, or between the last fcTL and IEND chunks.

-ignore_loop bool

Ignore the loop variable in the file if set. Default is enabled.

-max_fps int

Maximum framerate in frames per second. Default of 0 imposes no limit.

-default_fps int

Default framerate in frames per second when none is specified in the file (0 meaning as fast as possible). Default is 15.

### 20.4 asf# TOC

Advanced Systems Format demuxer.

This demuxer is used to demux ASF files and MMS network streams.

-no_resync_search bool

Do not try to resynchronize by looking for a certain optional start code.

### 20.5 astc# TOC

ASTC (Adaptive Scalable Texture Compression) demuxer.

This demuxer reads the 16-byte .astc header, hands it to the decoder as extradata, and emits the compressed image as a single packet.

### 20.6 concat# TOC

Virtual concatenation script demuxer.

This demuxer reads a list of files and other directives from a text file and demuxes them one after the other, as if all their packets had been muxed together.

The timestamps in the files are adjusted so that the first file starts at 0 and each next file starts where the previous one finishes. Note that it is done globally and may cause gaps if all streams do not have exactly the same length.

All files must have the same streams (same codecs, same time base, etc.).

The duration of each file is used to adjust the timestamps of the next file: if the duration is incorrect (because it was computed using the bit-rate or because the file is truncated, for example), it can cause artifacts. The duration directive can be used to override the duration stored in each file.

#### 20.6.1 Syntax# TOC

The script is a text file in extended-ASCII, with one directive per line. Empty lines, leading spaces and lines starting with ’#’ are ignored. The following directive is recognized:

file path

Path to a file to read; special characters and spaces must be escaped with backslash or single quotes.

All subsequent file-related directives apply to that file.

ffconcat version 1.0

Identify the script type and version.

To make FFmpeg recognize the format automatically, this directive must appear exactly as is (no extra space or byte-order-mark) on the very first line of the script.

duration dur

Duration of the file. This information can be specified from the file; specifying it here may be more efficient or help if the information from the file is not available or accurate.

If the duration is set for all files, then it is possible to seek in the whole concatenated video.

inpoint timestamp

In point of the file. When the demuxer opens the file it instantly seeks to the specified timestamp. Seeking is done so that all streams can be presented successfully at In point.

This directive works best with intra frame codecs, because for non-intra frame ones you will usually get extra packets before the actual In point and the decoded content will most likely contain frames before In point too.

For each file, packets before the file In point will have timestamps less than the calculated start timestamp of the file (negative in case of the first file), and the duration of the files (if not specified by the duration directive) will be reduced based on their specified In point.

Because of potential packets before the specified In point, packet timestamps may overlap between two concatenated files.

outpoint timestamp

Out point of the file. When the demuxer reaches the specified decoding timestamp in any of the streams, it handles it as an end of file condition and skips the current and all the remaining packets from all streams.

Out point is exclusive, which means that the demuxer will not output packets with a decoding timestamp greater or equal to Out point.

This directive works best with intra frame codecs and formats where all streams are tightly interleaved. For non-intra frame codecs you will usually get additional packets with presentation timestamp after Out point therefore the decoded content will most likely contain frames after Out point too. If your streams are not tightly interleaved you may not get all the packets from all streams before Out point and you may only will be able to decode the earliest stream until Out point.

The duration of the files (if not specified by the duration directive) will be reduced based on their specified Out point.

file_packet_metadata key=value

Metadata of the packets of the file. The specified metadata will be set for each file packet. You can specify this directive multiple times to add multiple metadata entries. This directive is deprecated, use file_packet_meta instead.

file_packet_meta key value

Metadata of the packets of the file. The specified metadata will be set for each file packet. You can specify this directive multiple times to add multiple metadata entries.

option key value

Option to access, open and probe the file. Can be present multiple times.

stream

Introduce a stream in the virtual file. All subsequent stream-related directives apply to the last introduced stream. Some streams properties must be set in order to allow identifying the matching streams in the subfiles. If no streams are defined in the script, the streams from the first file are copied.

exact_stream_id id

Set the id of the stream. If this directive is given, the string with the corresponding id in the subfiles will be used. This is especially useful for MPEG-PS (VOB) files, where the order of the streams is not reliable.

stream_meta key value

Metadata for the stream. Can be present multiple times.

stream_codec value

Codec for the stream.

stream_extradata hex_string

Extradata for the string, encoded in hexadecimal.

chapter id start end

Add a chapter. id is an unique identifier, possibly small and consecutive.

#### 20.6.2 Options# TOC

This demuxer accepts the following option:

safe

If set to 1, reject unsafe file paths and directives. A file path is considered safe if it does not contain a protocol specification and is relative and all components only contain characters from the portable character set (letters, digits, period, underscore and hyphen) and have no period at the beginning of a component.

If set to 0, any file name is accepted.

The default is 1.

auto_convert

If set to 1, try to perform automatic conversions on packet data to make the streams concatenable. The default is 1.

Currently, the only conversion is adding the h264_mp4toannexb bitstream filter to H.264 streams in MP4 format. This is necessary in particular if there are resolution changes.

segment_time_metadata

If set to 1, every packet will contain the lavf.concat.start_time and the lavf.concat.duration packet metadata values which are the start_time and the duration of the respective file segments in the concatenated output expressed in microseconds. The duration metadata is only set if it is known based on the concat file. The default is 0.

chapter_per_file

If set to 1, add a chapter for each file, named after the title metadata of the file or, failing that, its file name, and carrying the rest of the file’s metadata. The files are opened in order when the script is read to learn their durations, stopping after the first file whose duration is unknown, which gets the last chapter; when all durations are known, this also makes the total duration known and the output seekable. The default is 0.

#### 20.6.3 Examples# TOC

- Use absolute filenames and include some comments:

```
# my first filename
file /mnt/share/file-1.wav
# my second filename including whitespace
file '/mnt/share/file 2.wav'
# my third filename including whitespace plus single quote
file '/mnt/share/file 3'\''.wav'

```

- Allow for input format auto-probing, use safe filenames and set the duration of the first file:

```
ffconcat version 1.0

file file-1.wav
duration 20.0

file subdir/file-2.wav

```

### 20.7 dash# TOC

Dynamic Adaptive Streaming over HTTP demuxer.

This demuxer presents all AVStreams found in the manifest. By setting the discard flags on AVStreams the caller can decide which streams to actually receive. Each stream mirrors the id and bandwidth properties from the <Representation> as metadata keys named "id" and "variant_bitrate" respectively.

#### 20.7.1 Options# TOC

This demuxer accepts the following option:

cenc_decryption_key

Default 16-byte key, in hex, to decrypt files encrypted using ISO Common Encryption (CENC/AES-128 CTR; ISO/IEC 23001-7).

cenc_decryption_keys

Dictionary of 16-byte key ID => 16-byte key, both in hex, to decrypt files encrypted using ISO Common Encryption (CENC/AES-128 CTR; ISO/IEC 23001-7).

### 20.8 dvdvideo# TOC

DVD-Video demuxer, powered by libdvdnav and libdvdread.

Can directly ingest DVD titles, specifically sequential PGCs, into a conversion pipeline. Menu assets, such as background video or audio, can also be demuxed given the menu’s coordinates (at best effort).

Block devices (DVD drives), ISO files, and directory structures are accepted. Activate with -f dvdvideo in front of one of these inputs.

This demuxer does NOT have decryption code of any kind. You are on your own working with encrypted DVDs, and should not expect support on the matter.

Underlying playback is handled by libdvdnav, and structure parsing by libdvdread. FFmpeg must be built with GPL library support available as well as the configure switches --enable-libdvdnav and --enable-libdvdread.

You will need to provide either the desired "title number" or exact PGC/PG coordinates. Many open-source DVD players and tools can aid in providing this information. If not specified, the demuxer will default to title 1 which works for many discs. However, due to the flexibility of the format, it is recommended to check manually. There are many discs that are authored strangely or with invalid headers.

If the input is a real DVD drive, please note that there are some drives which may silently fail on reading bad sectors from the disc, returning random bits instead which is effectively corrupt data. This is especially prominent on aging or rotting discs. A second pass and integrity checks would be needed to detect the corruption. This is not an FFmpeg issue.

#### 20.8.1 Background# TOC

DVD-Video is not a directly accessible, linear container format in the traditional sense. Instead, it allows for complex and programmatic playback of carefully muxed MPEG-PS streams that are stored in headerless VOB files. To the end-user, these streams are known simply as "titles", but the actual logical playback sequence is defined by one or more "PGCs", or Program Group Chains, within the title. The PGC is in turn comprised of multiple "PGs", or Programs", which are the actual video segments (and for a typical video feature, sequentially ordered). The PGC structure, along with stream layout and metadata, are stored in IFO files that need to be parsed. PGCs can be thought of as playlists in easier terms.

An actual DVD player relies on user GUI interaction via menus and an internal VM to drive the direction of demuxing. Generally, the user would either navigate (via menus) or automatically be redirected to the PGC of their choice. During this process and the subsequent playback, the DVD player’s internal VM also maintains a state and executes instructions that can create jumps to different sectors during playback. This is why libdvdnav is involved, as a linear read of the MPEG-PS blobs on the disc (VOBs) is not enough to produce the right sequence in many cases.

There are many other DVD structures (a long subject) that will not be discussed here. NAV packets, in particular, are handled by this demuxer to build accurate timing but not emitted as a stream. For a good high-level understanding, refer to: https://code.videolan.org/videolan/libdvdnav/-/blob/master/doc/dvd_structures

#### 20.8.2 Options# TOC

This demuxer accepts the following options:

title int

The title number to play. Must be set if pgc and pg are not set. Not applicable to menus. Default is 0 (auto), which currently only selects the first available title (title 1) and notifies the user about the implications.

chapter_start int

The chapter, or PTT (part-of-title), number to start at. Not applicable to menus. Default is 1.

chapter_end int

The chapter, or PTT (part-of-title), number to end at. Not applicable to menus. Default is 0, which is a special value to signal end at the last possible chapter.

angle int

The video angle number, referring to what is essentially an additional video stream that is composed from alternate frames interleaved in the VOBs. Not applicable to menus. Default is 1.

region int

The region code to use for playback. Some discs may use this to default playback at a particular angle in different regions. This option will not affect the region code of a real DVD drive, if used as an input. Not applicable to menus. Default is 0, "world".

menu bool

Demux menu assets instead of navigating a title. Requires exact coordinates of the menu (menu_lu, menu_vts, pgc, pg). Default is false.

menu_lu int

The menu language to demux. In DVD, menus are grouped by language. Default is 1, the first language unit.

menu_vts int

The VTS where the menu lives, or 0 if it is a VMG menu (root-level). Default is 1, menu of the first VTS.

pgc int

The entry PGC to start playback, in conjunction with pg. Alternative to setting title. Chapter markers are not supported at this time. Must be explicitly set for menus. Default is 0, automatically resolve from value of title.

pg int

The entry PG to start playback, in conjunction with pgc. Alternative to setting title. Chapter markers are not supported at this time. Default is 1, the first PG of the PGC.

preindex bool

Enable this to have accurate chapter (PTT) markers and duration measurement, which requires a slow second pass read in order to index the chapter marker timestamps from NAV packets. This is non-ideal extra work for real optical drives. It is recommended and faster to use this option with a backup of the DVD structure stored on a hard drive. Not compatible with pgc and pg. Default is 0, false.

trim bool

Skip padding cells (i.e. cells shorter than 1 second) from the beginning. There exist many discs with filler segments at the beginning of the PGC, often with junk data intended for controlling a real DVD player’s buffering speed and with no other material data value. Not applicable to menus. Default is 1, true.

#### 20.8.3 Examples# TOC

- Open title 3 from a given DVD structure:

```
ffmpeg -f dvdvideo -title 3 -i <path to DVD> ...

```

- Open chapters 3-6 from title 1 from a given DVD structure:

```
ffmpeg -f dvdvideo -chapter_start 3 -chapter_end 6 -title 1 -i <path to DVD> ...

```

- Open only chapter 5 from title 1 from a given DVD structure:

```
ffmpeg -f dvdvideo -chapter_start 5 -chapter_end 5 -title 1 -i <path to DVD> ...

```

- Demux menu with language 1 from VTS 1, PGC 1, starting at PG 1:

```
ffmpeg -f dvdvideo -menu 1 -menu_lu 1 -menu_vts 1 -pgc 1 -pg 1 -i <path to DVD> ...

```

### 20.9 ea# TOC

Electronic Arts Multimedia format demuxer.

This format is used by various Electronic Arts games.

#### 20.9.1 Options# TOC

merge_alpha bool

Normally the VP6 alpha channel (if exists) is returned as a secondary video stream, by setting this option you can make the demuxer return a single video stream which contains the alpha channel in addition to the ordinary video.

### 20.10 imf# TOC

Interoperable Master Format demuxer.

This demuxer presents audio and video streams found in an IMF Composition, as specified in SMPTE ST 2067-2.

```
ffmpeg [-assetmaps <path of ASSETMAP1>,<path of ASSETMAP2>,...] -i <path of CPL> ...

```

If -assetmaps is not specified, the demuxer looks for a file called ASSETMAP.xml in the same directory as the CPL.

### 20.11 flv, live_flv, kux# TOC

Adobe Flash Video Format demuxer.

This demuxer is used to demux FLV files and RTMP network streams. In case of live network streams, if you force format, you may use live_flv option instead of flv to survive timestamp discontinuities. KUX is a flv variant used on the Youku platform.

```
ffmpeg -f flv -i myfile.flv ...
ffmpeg -f live_flv -i rtmp://<any.server>/anything/key ....

```

-flv_metadata bool

Allocate the streams according to the onMetaData array content.

-flv_ignore_prevtag bool

Ignore the size of previous tag value.

-flv_full_metadata bool

Output all context of the onMetadata.

### 20.12 gif# TOC

Animated GIF demuxer.

It accepts the following options:

min_delay

Set the minimum valid delay between frames in hundredths of seconds. Range is 0 to 6000. Default value is 2.

max_gif_delay

Set the maximum valid delay between frames in hundredth of seconds. Range is 0 to 65535. Default value is 65535 (nearly eleven minutes), the maximum value allowed by the specification.

default_delay

Set the default delay between frames in hundredths of seconds. Range is 0 to 6000. Default value is 10.

ignore_loop

GIF files can contain information to loop a certain number of times (or infinitely). If ignore_loop is set to 1, then the loop setting from the input will be ignored and looping will not occur. If set to 0, then looping will occur and will cycle the number of times according to the GIF. Default value is 1.

For example, with the overlay filter, place an infinitely looping GIF over another video:

```
ffmpeg -i input.mp4 -ignore_loop 0 -i input.gif -filter_complex overlay=shortest=1 out.mkv

```

Note that in the above example the shortest option for overlay filter is used to end the output video at the length of the shortest input file, which in this case is input.mp4 as the GIF in this example loops infinitely.

### 20.13 hls# TOC

HLS demuxer

Apple HTTP Live Streaming demuxer.

This demuxer presents all AVStreams from all variant streams. The id field is set to the bitrate variant index number. By setting the discard flags on AVStreams (by pressing ’a’ or ’v’ in ffplay), the caller can decide which variant streams to actually receive. The total bitrate of the variant that the stream belongs to is available in a metadata key named "variant_bitrate". It is unset when the stream is shared by variants with different bitrates. The value is always available in the corresponding program’s metadata.

It accepts the following options:

live_start_index

segment index to start live streams at (negative values are from the end).

prefer_x_start

prefer to use #EXT-X-START if it’s in playlist instead of live_start_index.

allowed_extensions

’,’ separated list of file extensions that hls is allowed to access.

extension_picky

This blocks disallowed extensions from probing It also requires all available segments to have matching extensions to the format except mpegts, which is always allowed. It is recommended to set the whitelists correctly instead of depending on extensions Enabled by default.

max_reload

Maximum number of times a insufficient list is attempted to be reloaded. Default value is 1000.

m3u8_hold_counters

The maximum number of times to load m3u8 when it refreshes without new segments. Default value is 1000.

http_persistent

Use persistent HTTP connections. Applicable only for HTTP streams. Enabled by default.

http_multiple

Use multiple HTTP connections for downloading HTTP segments. Enabled by default for HTTP/1.1 servers.

http_seekable

Use HTTP partial requests for downloading HTTP segments. 0 = disable, 1 = enable, -1 = auto, Default is auto.

seg_format_options

Set options for the demuxer of media segments using a list of key=value pairs separated by :.

seg_max_retry

Maximum number of times to reload a segment on error, useful when segment skip on network error is not desired. Default value is 0.

### 20.14 image2# TOC

Image file demuxer.

This demuxer reads from a list of image files specified by a pattern. The syntax and meaning of the pattern is specified by the option pattern_type.

The pattern may contain a suffix which is used to automatically determine the format of the images contained in the files.

The size, the pixel format, and the format of each image must be the same for all the files in the sequence.

This demuxer accepts the following options:

framerate

Set the frame rate for the video stream. It defaults to 25.

loop

If set to 1, loop over the input. Default value is 0.

pattern_type

Select the pattern type used to interpret the provided filename.

pattern_type accepts one of the following values.

none

Disable pattern matching, therefore the video will only contain the specified image. You should use this option if you do not want to create sequences from multiple images and your filenames may contain special pattern characters.

sequence

Select a sequence pattern type, used to specify a sequence of files indexed by sequential numbers.

A sequence pattern may contain the string "%d" or "%0Nd", which specifies the position of the characters representing a sequential number in each filename matched by the pattern. If the form "%d0Nd" is used, the string representing the number in each filename is 0-padded and N is the total number of 0-padded digits representing the number. The literal character ’%’ can be specified in the pattern with the string "%%".

If the sequence pattern contains "%d" or "%0Nd", the first filename of the file list specified by the pattern must contain a number inclusively contained between start_number and start_number+start_number_range-1, and all the following numbers must be sequential.

For example the pattern "img-%03d.bmp" will match a sequence of filenames of the form img-001.bmp, img-002.bmp, ..., img-010.bmp, etc.; the pattern "i%%m%%g-%d.jpg" will match a sequence of filenames of the form i%m%g-1.jpg, i%m%g-2.jpg, ..., i%m%g-10.jpg, etc.

Note that the pattern must not necessarily contain "%d" or "%0Nd", for example to convert a single image file img.jpeg you can employ the command:

```
ffmpeg -i img.jpeg img.png

```

glob

Select a glob wildcard pattern type.

The pattern is interpreted like a glob() pattern. This is only selectable if libavformat was compiled with globbing support.

Default value is sequence.

pixel_format

Set the pixel format of the images to read. If not specified the pixel format is guessed from the first image file in the sequence.

start_number

Set the index of the file matched by the image file pattern to start to read from. Default value is 0.

start_number_range

Set the index interval range to check when looking for the first image file in the sequence, starting from start_number. Default value is 5.

ts_from_file

If set to 1, will set frame timestamp to modification time of image file. Note that monotonity of timestamps is not provided: images go in the same order as without this option. Default value is 0. If set to 2, will set frame timestamp to the modification time of the image file in nanosecond precision.

video_size

Set the video size of the images to read. If not specified the video size is guessed from the first image file in the sequence.

export_path_metadata

If set to 1, will add two extra fields to the metadata found in input, making them also available for other filters (see drawtext filter for examples). Default value is 0. The extra fields are described below:

lavf.image2dec.source_path

Corresponds to the full path to the input file being read.

lavf.image2dec.source_basename

Corresponds to the name of the file being read.

#### 20.14.1 Examples# TOC

- Use ffmpeg for creating a video from the images in the file sequence img-001.jpeg, img-002.jpeg, ..., assuming an input frame rate of 10 frames per second:

```
ffmpeg -framerate 10 -i 'img-%03d.jpeg' out.mkv

```

- As above, but start by reading from a file with index 100 in the sequence:

```
ffmpeg -framerate 10 -start_number 100 -i 'img-%03d.jpeg' out.mkv

```

- Read images matching the "*.png" glob pattern , that is all the files terminating with the ".png" suffix:

```
ffmpeg -framerate 10 -pattern_type glob -i "*.png" out.mkv

```

### 20.15 jpeg_mpf# TOC

JPEG Multi-Picture Format demuxer.

Exposes each JPEG image stored in a CIPA DC-007 MP file as a separate stream, in the order of the MP Entries, with the First Individual Image flagged as the default stream. If the file contains an ISO 21496-1 gain map, as is the case for JPEG Ultra HDR, the primary image and the gain map are linked by a ‘gain_map’ stream group, and the gain map parameters are exported as frame side data by the decoder.

Images of any other type (e.g. large thumbnails or multi-view images) are exposed as additional streams.

This demuxer accepts the following options, which behave like the options of the same name of the ‘image2’ demuxer:

framerate

Set the frame rate of the video streams. The default is 25.

loop

If set to 1, loop over the images in the file. The default is 0. This requires seekable input.

### 20.16 ktx# TOC

Khronos Texture 1.0 demuxer for ASTC textures.

This demuxer reads the KTX 1.0 header and maps the ASTC GL internal format to the block footprint the decoder needs, so only files using the ASTC formats are accepted. A KTXorientation key is preserved as stream display metadata, and the texture is emitted as a single packet.

### 20.17 libgme# TOC

The Game Music Emu library is a collection of video game music file emulators.

See https://bitbucket.org/mpyne/game-music-emu/overview for more information.

It accepts the following options:

track_index

Set the index of which track to demux. The demuxer can only export one track. Track indexes start at 0. Default is to pick the first track. Number of tracks is exported as tracks metadata entry.

sample_rate

Set the sampling rate of the exported track. Range is 1000 to 999999. Default is 44100.

max_size (bytes)

The demuxer buffers the entire file into memory. Adjust this value to set the maximum buffer size, which in turn, acts as a ceiling for the size of files that can be read. Default is 50 MiB.

### 20.18 libmodplug# TOC

ModPlug based module demuxer

See https://github.com/Konstanty/libmodplug

It will export one 2-channel 16-bit 44.1 kHz audio stream. Optionally, a pal8 16-color video stream can be exported with or without printed metadata.

It accepts the following options:

noise_reduction

Apply a simple low-pass filter. Can be 1 (on) or 0 (off). Default is 0.

reverb_depth

Set amount of reverb. Range 0-100. Default is 0.

reverb_delay

Set delay in ms, clamped to 40-250 ms. Default is 0.

bass_amount

Apply bass expansion a.k.a. XBass or megabass. Range is 0 (quiet) to 100 (loud). Default is 0.

bass_range

Set cutoff i.e. upper-bound for bass frequencies. Range is 10-100 Hz. Default is 0.

surround_depth

Apply a Dolby Pro-Logic surround effect. Range is 0 (quiet) to 100 (heavy). Default is 0.

surround_delay

Set surround delay in ms, clamped to 5-40 ms. Default is 0.

max_size

The demuxer buffers the entire file into memory. Adjust this value to set the maximum buffer size, which in turn, acts as a ceiling for the size of files that can be read. Range is 0 to 100 MiB. 0 removes buffer size limit (not recommended). Default is 5 MiB.

video_stream_expr

String which is evaluated using the eval API to assign colors to the generated video stream. Variables which can be used are x, y, w, h, t, speed, tempo, order, pattern and row.

video_stream

Generate video stream. Can be 1 (on) or 0 (off). Default is 0.

video_stream_w

Set video frame width in ’chars’ where one char indicates 8 pixels. Range is 20-512. Default is 30.

video_stream_h

Set video frame height in ’chars’ where one char indicates 8 pixels. Range is 20-512. Default is 30.

video_stream_ptxt

Print metadata on video stream. Includes speed, tempo, order, pattern, row and ts (time in ms). Can be 1 (on) or 0 (off). Default is 1.

### 20.19 libopenmpt# TOC

libopenmpt based module demuxer

See https://lib.openmpt.org/libopenmpt/ for more information.

Some files have multiple subsongs (tracks) this can be set with the subsong option.

It accepts the following options:

subsong

Set the subsong index. This can be either ’all’, ’auto’, or the index of the subsong. Subsong indexes start at 0. The default is ’auto’.

The default value is to let libopenmpt choose.

layout

Set the channel layout. Valid values are 1, 2, and 4 channel layouts. The default value is STEREO.

sample_rate

Set the sample rate for libopenmpt to output. Range is from 1000 to INT_MAX. The value default is 48000.

### 20.20 mcc# TOC

Demuxer for MacCaption MCC files, it supports MCC versions 1.0 and 2.0. MCC files store VANC data, which can include closed captions (EIA-608 and CEA-708), ancillary time code, pan-scan data, etc. By default, for backward compatibility, the MCC demuxer extracts just the EIA-608 and CEA-708 closed captions and returns a EIA_608 stream, ignoring all other VANC data. You can change it to return all VANC data in a SMPTE_436M_ANC data stream by setting -eia608_extract 0

#### 20.20.1 Examples# TOC

- Convert a MCC file to Scenarist (SCC) format:

```
ffmpeg -i CC.mcc -c:s copy CC.scc

```

Note that the SCC format only supports EIA-608, so this will discard all other data such as CEA-708 extensions.

- Merge a MCC file into a MXF file:

```
ffmpeg -i video_and_audio.mxf -eia608_extract 0 -i CC.mcc -c copy -map 0 -map 1 out.mxf

```

This retains all VANC data and inserts it into the output MXF file as a SMPTE_436M_ANC data stream.

### 20.21 mov/mp4/3gp# TOC

Demuxer for Quicktime File Format & ISO/IEC Base Media File Format (ISO/IEC 14496-12 or MPEG-4 Part 12, ISO/IEC 15444-12 or JPEG 2000 Part 12).

Registered extensions: mov, mp4, m4a, 3gp, 3g2, mj2, psp, m4b, ism, ismv, isma, f4v

#### 20.21.1 Options# TOC

This demuxer accepts the following options:

enable_drefs

Enable loading of external tracks, disabled by default. Enabling this can theoretically leak information in some use cases.

use_absolute_path

Allows loading of external tracks via absolute paths, disabled by default. Enabling this poses a security risk. It should only be enabled if the source is known to be non-malicious.

seek_streams_individually

When seeking, identify the closest point in each stream individually and demux packets in that stream from identified point. This can lead to a different sequence of packets compared to demuxing linearly from the beginning. Default is true.

ignore_editlist

Ignore any edit list atoms. The demuxer, by default, modifies the stream index to reflect the timeline described by the edit list. Default is false.

advanced_editlist

Modify the stream index to reflect the timeline described by the edit list. ignore_editlist must be set to false for this option to be effective. If both ignore_editlist and this option are set to false, then only the start of the stream index is modified to reflect initial dwell time or starting timestamp described by the edit list. Default is true.

ignore_chapters

Don’t parse chapters. This includes GoPro ’HiLight’ tags/moments. Note that chapters are only parsed when input is seekable. Default is false.

use_mfra_for

For seekable fragmented input, set fragment’s starting timestamp from media fragment random access box, if present.

Following options are available:

‘auto’

Auto-detect whether to set mfra timestamps as PTS or DTS (default)

‘dts’

Set mfra timestamps as DTS

‘pts’

Set mfra timestamps as PTS

‘0’

Don’t use mfra box to set timestamps

use_tfdt

For fragmented input, set fragment’s starting timestamp to baseMediaDecodeTime from the tfdt box. Default is enabled, which will prefer to use the tfdt box to set DTS. Disable to use the earliest_presentation_time from the sidx box. In either case, the timestamp from the mfra box will be used if it’s available and use_mfra_for is set to pts or dts.

export_all

Export unrecognized boxes within the udta box as metadata entries. The first four characters of the box type are set as the key. Default is false.

export_xmp

Export entire contents of XMP_ box and uuid box as a string with key xmp. Note that if export_all is set and this option isn’t, the contents of XMP_ box are still exported but with key XMP_. Default is false.

activation_bytes

4-byte key required to decrypt Audible AAX and AAX+ files. See Audible AAX subsection below.

audible_fixed_key

Fixed key used for handling Audible AAX/AAX+ files. It has been pre-set so should not be necessary to specify.

decryption_key

Default 16-byte key, in hex, to decrypt files encrypted using ISO Common Encryption (CENC/AES-128 CTR; ISO/IEC 23001-7).

decryption_keys

Dictionary of 16-byte key ID => 16-byte key, both in hex, to decrypt files encrypted using ISO Common Encryption (CENC/AES-128 CTR; ISO/IEC 23001-7).

max_stts_delta

Very high sample deltas written in a trak’s stts box may occasionally be intended but usually they are written in error or used to store a negative value for dts correction when treated as signed 32-bit integers. This option lets the user set an upper limit, beyond which the delta is clamped to 1. Values greater than the limit if negative when cast to int32 are used to adjust onward dts.

Unit is the track time scale. Range is 0 to UINT_MAX. Default is UINT_MAX - 48000*10 which allows up to a 10 second dts correction for 48 kHz audio streams while accommodating 99.9% of uint32 range.

interleaved_read

Interleave packets from multiple tracks at demuxer level. For badly interleaved files, this prevents playback issues caused by large gaps between packets in different tracks, as MOV/MP4 do not have packet placement requirements. However, this can cause excessive seeking on very badly interleaved files, due to seeking between tracks, so disabling it may prevent I/O issues, at the expense of playback.

#### 20.21.2 Audible AAX# TOC

Audible AAX files are encrypted M4B files, and they can be decrypted by specifying a 4 byte activation secret.

```
ffmpeg -activation_bytes 1CEB00DA -i test.aax -vn -c:a copy output.mp4

```

### 20.22 mpegts# TOC

MPEG-2 transport stream demuxer.

This demuxer accepts the following options:

resync_size

Set size limit for looking up a new synchronization. Default value is 65536.

skip_unknown_pmt

Skip PMTs for programs not defined in the PAT. Default value is 0.

fix_teletext_pts

Override teletext packet PTS and DTS values with the timestamps calculated from the PCR of the first program which the teletext stream is part of and is not discarded. Default value is 1, set this option to 0 if you want your teletext packet PTS and DTS values untouched.

ts_packetsize

Output option carrying the raw packet size in bytes. Show the detected raw packet size, cannot be set by the user.

scan_all_pmts

Scan and combine all PMTs. The value is an integer with value from -1 to 1 (-1 means automatic setting, 1 means enabled, 0 means disabled). Default value is -1.

merge_pmt_versions

Reuse existing streams when a PMT’s version is updated and elementary streams move to different PIDs. Default value is 0.

max_packet_size

Set maximum size, in bytes, of packet emitted by the demuxer. Payloads above this size are split across multiple packets. Range is 184 to INT_MAX/2. Default is 204800 bytes.

### 20.23 mpjpeg# TOC

MJPEG encapsulated in multi-part MIME demuxer.

This demuxer allows reading of MJPEG, where each frame is represented as a part of multipart/x-mixed-replace stream.

strict_mime_boundary

Default implementation applies a relaxed standard to multi-part MIME boundary detection, to prevent regression with numerous existing endpoints not generating a proper MIME MJPEG stream. Turning this option on by setting it to 1 will result in a stricter check of the boundary value.

### 20.24 rawvideo# TOC

Raw video demuxer.

This demuxer allows one to read raw video data. Since there is no header specifying the assumed video parameters, the user must specify them in order to be able to decode the data correctly.

This demuxer accepts the following options:

framerate

Set input video frame rate. Default value is 25.

pixel_format

Set the input video pixel format. Default value is yuv420p.

stride

Set frame line size in bytes, only required if there are extra padding. For multiplane formats, stride is a list of line size for each plane.

video_size

Set the input video size. This value must be specified explicitly.

For example to read a rawvideo file input.raw with ffplay, assuming a pixel format of rgb24, a video size of 320x240, and a frame rate of 10 images per second, use the command:

```
ffplay -f rawvideo -pixel_format rgb24 -video_size 320x240 -framerate 10 input.raw

```

