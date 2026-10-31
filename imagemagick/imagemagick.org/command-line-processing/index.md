# ImageMagick | Command-line Processing

v7.1.2-34 Latest Stable Release

# Command-line Processing

Learn how ImageMagick interprets and executes command-line instructions for image manipulation. Master processing order, options, and input/output workflows.

   Get ImageMagick    Documentation

 quickstart.sh

# Install via your favorite Package Manager

$ brew install imagemagick

# Convert PNG to WebP with compression

$ magick input.png -quality 85 output.webp

# Resize image maintaining aspect ratio

$ magick input.jpg -resize 800x600^ output.jpg

 Anatomy Input Filename Command Options Settings Operators Sequence Geometry Stack Output Filename

 The ImageMagick command-line tools can range from simple single-file conversions:

 $ magick image.jpg image.png

Or scale into complex multi-step processing pipelines with a plethora of options:

 $ magick label.gif -alpha Set \
 \( +clone -shade 110x90 -normalize -negate +clone -compose Plus -composite \) \
 \( -clone 0 -shade 110x50 -normalize -channel BG -fx 0 +channel -alpha Off \) \
 -delete 0 +swap -compose Multiply -composite button.gif

  Cross-Platform Note: Linux uses the backslash (\) for line continuation, whereas Windows uses a caret (^). Parentheses do not require escaping under Windows.

###### 2D Label to 3D Simulated Depth

Transform flat typography into rich, textured dimensional UI buttons using single-line execution.

###### Dynamic Shaded Progress Cylinder

Generate complex vector-like primitives, gradients, shadows, and labels programmatically.

## The Anatomy of the Command-line

An ImageMagick command string consists of the following modular building blocks:

-  One or more required input filenames.

-  Zero, one, or more persistent image settings.

-  Zero, one, or more immediate image operators.

-  Zero, one, or more image sequence operators.

-  Zero, one, or more isolated image stacks (parentheses).

-  Zero or one output image filename.

## Input Filename Extensions

ImageMagick extends input filenames far beyond simple file paths to support globbing, built-ins, and direct streams.

###### Filename Globbing

Wildcards like asterisks automatically match sets of files across all platforms (e.g., Windows and Linux):

$ magick *.jpg images.gif

###### Explicit Image Format

Force signature-less raw data streams by prefixing formats explicitly:

$ magick -size 640x480 -depth 8 rgb:image image.png

###### Built-in Images & Patterns

Generate standard procedural patterns instantly:

$ magick -size 640x480 pattern:checkerboard checkerboard.png

###### STDIN / STDOUT Pipes

Stream image pipelines seamlessly between processes using -:

$ magick logo: gif:- | magick display gif:-

## Command-line Options & Settings

Options dictate execution behavior and are categorized into persistent settings, immediate operators, sequence operators, and geometry modifiers.

#####  Image Settings (Persistent)

Persist across the command line until execution terminates or settings are overridden:

- -adjoin

- -alpha

- -background

- -colorspace

- -density

- -depth

- -font

- -format

- -quality

- -size

#####  Image Operators (Immediate)

Execute immediately against the current active image set:

- -blur

- -charcoal

- -crop

- -despeckle

- -flop

- -negate

- -resize

- -rotate

- -sharpen

- -trim

## Image Geometry Reference

Geometry arguments control target widths, heights, percentages, and coordinate offsets without spaces.

 Size / Modifier Description & Behavior

 scale% Height and width both scaled by specified percentage.

 widthxheight Maximum values of height and width given; aspect ratio preserved.

 widthxheight^ Minimum values of width and height given; aspect ratio preserved.

 widthxheight! Width and height strictly forced; original aspect ratio ignored.

 widthxheight> Shrink image only if dimensions are larger than specified bounds.

 widthxheight< Enlarge image only if dimensions are smaller than specified bounds.

 area@ Resize image to total pixel area limit while preserving aspect ratio.

 size+x+y Pixel offset coordinates adjusted by gravity rules.

## Image Stack & Output Management

Isolate operations using parenthesis blocks and export results using advanced formatting strings.

##### Isolated Stack Processing Example

Apply rotation strictly inside a parentheses stack without affecting preceding files:

 $ magick wand.gif \( wizard.gif -rotate 30 \) +append images.gif

##### Sequential Output Formatting

Extract property strings or format multi-page sequence outputs dynamically:

 $ magick rose: -set filename:area '%wx%h' 'rose-%[filename:area].png'

 $ magick *.jpg +adjoin page-%d.pdf
