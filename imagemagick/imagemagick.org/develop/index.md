# ImageMagick | Develop & Language APIs

v7.1.2-34 Latest Stable Release

# Develop & Language APIs

Explore ImageMagick development resources with bindings for C, C++, Python, PHP, .NET, Node.js, and more. Integrate image processing directly into your applications.

   Get ImageMagick    Documentation

 quickstart.sh

# Install via your favorite Package Manager

$ brew install imagemagick

# Convert PNG to WebP with compression

$ magick input.png -quality 85 output.webp

# Resize image maintaining aspect ratio

$ magick input.jpg -resize 800x600^ output.jpg

 The functionality of ImageMagick can be driven from the command-line or integrated natively into your favorite programming language. Choose from bindings for C, C++, Python, PHP, .NET, Node.js, Rust, and many others to manipulate or create images dynamically.

###### Jump to Language Binding

 C / C++ .NET JavaScript / WASM Node.js PHP Python Ruby Rust Go Java Perl

## Core C & C++ Libraries

Direct thread-safe native APIs for high-performance image processing applications.

##### MagickWand & MagickCore
 C Native

 Use the thread-safe MagickWand library to convert, compose, and edit images, or drop down to the low-level MagickCore API for wizard-level control.

  MagickCache API Docs

##### Magick++
 C++ OOP

 Magick++ provides a thread-safe object-oriented C++ interface to ImageMagick.

  Tutorial (PDF)  Source (ODT)

## Third-Party & Official Language Bindings

Select bindings tailored to your preferred software stack.

###### .NET / C#
 Ecosystem

 Use Magick.NET to convert, compose, and edit images from Windows .NET.

###### Node.js
 Async / Sync

 Node-magickwand offers direct native access to the full C++ library with TypedArray and TypeScript support.

###### JavaScript / TS
 WASM

 magick-wasm provides high-performance WebAssembly bindings for browser and server runtimes.

###### Python
 Data / Web

 Use Wand (ctypes-based) or PythonMagick / PythonMagickWand for object-oriented image processing.

###### PHP
 Extension

 IMagick is a native PHP extension. Explore guides at PHPImagick.com.

###### Ruby
 Wrapper

 RMagick interfaces MagickCore libraries, while MiniMagick provides a lightweight CLI wrapper.

###### Rust
 Safe

 MagickRust provides robust MagickWand bindings for high-reliability Rust systems.

###### Go (Golang)
 Concurrent

 GoImagick connects Go routines directly to ImageMagick's MagickWand and MagickCore C APIs.

###### Java
 Enterprise

 JMagick offers object-oriented Java bindings, alongside im4java.

###### Perl
 Scripting

 Use PerlMagick to convert, compose, and edit images natively from Perl scripts.

###### R Language
 Stats

 The magick package wraps Magick++ STL for vectorized statistical image processing in R.

###### Julia
 Scientific

 JuliaIO provides an object-oriented Julia interface for numerical image workflows.

#####  Additional Community Bindings

ImageMagick also supports community-maintained integrations for niche environments:

 Ch (ChMagick) Kotlin (KMagick) LabVIEW Common Lisp LuaJIT / Lua Pascal / Delphi Tcl/Tk
