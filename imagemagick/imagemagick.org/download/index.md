# ImageMagick | Download

v7.1.2-34 Latest Stable Release

# Download

Download ImageMagick for Linux, macOS, and Windows. Access ready-to-run binaries, portable builds, or source code to convert, edit, and compose images.

   Get ImageMagick    Documentation

 quickstart.sh

# Install via your favorite Package Manager

$ brew install imagemagick

# Convert PNG to WebP with compression

$ magick input.png -quality 85 output.webp

# Resize image maintaining aspect ratio

$ magick input.jpg -resize 800x600^ output.jpg

  Linux Binary  macOS Binary  Windows Binary

 You can install ImageMagick from source, or grab a ready-to-run package below. Review recent changes or check our global mirrors.

 It is strongly recommended to establish a security policy suitable for your local environment before utilizing ImageMagick.

## Linux Binary Release

 We provide AppImage as the official portable binary format. For specialized configurations, please build from source.

 ImageMagick-7.1.2-34-gcc-x86_64.AppImage

 ImageMagick-7.1.2-34-clang-x86_64.AppImage

 Complete portable application, zero installation required. Verify using its provenance .

 $ mkdir -p ~/.config/ImageMagick && ./magick -list policy

## macOS Binary Release

 We recommend using Homebrew for macOS environments.

###### Standard Installation

 $ brew install imagemagick
 $ brew install ghostscript

###### Full Suite (Optional codecs: SVG, RAW, OpenMP)

 $ brew install imagemagick-full
 Note: imagemagick-full is keg-only and not automatically linked to your system PATH.

## Windows Binary Release

 Compatible with Windows 10/11 (x86, x64, ARM64) or Windows Server 2012+.

 Recommended for 64-Bit Windows

##### Win64 Dynamic Q16-HDRI

16 bits-per-pixel component with High Dynamic Range imaging enabled.

 ImageMagick-7.1.2-34-Q16-HDRI-x64-dll.exe

##### Alternate Windows Binaries & Portable Archives

 Distribution Variant Specifications & Details

  ImageMagick-7.1.2-34-Q16-x64-dll.exe  Win64 dynamic at 16 bits-per-pixel component

  ImageMagick-7.1.2-34-Q16-x64-static.exe  Win64 static at 16 bits-per-pixel component

  ImageMagick-7.1.2-34-Q8-x64-dll.exe  Win64 dynamic at 8 bits-per-pixel component

  ImageMagick-7.1.2-34-Q16-HDRI-x64-static.exe  Win64 static at 16 bits-per-pixel with high dynamic-range enabled

  ImageMagick-7.1.2-34-portable-Q16-x64.7z  Portable Win64 static (No installer or registry changes required)

  ImageMagick-7.1.2-34-portable-Q16-HDRI-x64.7z  Portable Win64 HDRI static archive

##### Command-Line Package Managers

Quickly install via winget, scoop, or chocolatey:

$ winget install ImageMagick.Q16-HDRI

$ scoop install main/imagemagick

$ choco install imagemagick

###### Verify Installation

 $ magick logo: logo.gif
 $ magick identify logo.gif

 Missing dependencies? You may need the Visual C++ Redistributable Package.
