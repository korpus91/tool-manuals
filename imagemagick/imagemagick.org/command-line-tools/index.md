# ImageMagick | Command-line Tools

v7.1.2-34 Latest Stable Release

# Command-line Tools

Explore ImageMagick’s powerful command-line tools to create, edit, compose, and convert images across dynamic workflows and batch processing.

   Get ImageMagick    Documentation

 quickstart.sh

# Install via your favorite Package Manager

$ brew install imagemagick

# Convert PNG to WebP with compression

$ magick input.png -quality 85 output.webp

# Resize image maintaining aspect ratio

$ magick input.jpg -resize 800x600^ output.jpg

 ImageMagick is a collection of command-line tools for modifying and manipulating images. While graphical interfaces (GUIs) like Gimp or Photoshop are useful for individual edits, command-line utilities are far more efficient for web script automation, batch processing multiple files, or repeating complex tasks.

## Core Tools

 If you are just getting acquainted with ImageMagick, start with the magick program.

 magick Primary Tool

 Convert between image formats as well as resize, blur, crop, despeckle, dither, draw on, flip, join, re-sample, and much more.

 magick-script Interpreter

 Use this scripting language interpreter to convert, resize, blur, crop, despeckle, dither, draw on, flip, join, re-sample, and more.

## Version 6 Compatibility Sub-commands

 ImageMagick supports legacy compatibility sub-commands for seamless workflow transitions from version 6.

 magick animate Animation

Animate an image sequence on any X server.

 magick compare Analysis

Mathematically and visually annotate the difference between an image and its reconstruction.

 magick composite Composition

Overlap one image over another.

 magick conjure Scripting

Interpret and execute scripts written in the Magick Scripting Language (MSL).

 magick display Viewer

Display an image or image sequence on any X server.

 magick identify Inspection

Describe the format and characteristics of one or more image files.

 magick import Capture

Save any visible window or rectangular screen portion on an X server as an image file.

 magick mogrify Batch Edit

Resize, blur, crop, etc. Overwrites original source files directly (unlike magick).

 magick montage Grid Layout

Create a composite image by combining tiled separate images with optional frames and borders.

 magick stream Streaming

Lightweight tool to stream raw pixel components row-by-row, ideal for large or tera-pixel images.

######  Direct Command Execution

 If your installation includes direct v6 compatibility symlinks, you can reference tools directly from your terminal:

 $ magick identify -verbose myImage.png
