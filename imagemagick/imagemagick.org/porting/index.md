# ImageMagick | Porting to ImageMagick Version 7

v7.1.2-34 Latest Stable Release

# Porting to ImageMagick Version 7

Learn how ImageMagick version 7 differs from previous versions, including enhanced multi-channel pixel support, default HDRI, major command-line interface updates, and migration guides for MagickCore and MagickWand APIs.

   Get ImageMagick    Documentation

 quickstart.sh

# Install via your favorite Package Manager

$ brew install imagemagick

# Convert PNG to WebP with compression

$ magick input.png -quality 85 output.webp

# Resize image maintaining aspect ratio

$ magick input.jpg -resize 800x600^ output.jpg

 Version 7 HDRI Channels Alpha Grayscale Masks MagickCore API Headers Deprecations CLI Performance Summary

  Migration Guide

# Porting to ImageMagick Version 7

 The design of ImageMagick is an evolutionary process, with the design and implementation efforts serving to influence and guide further progress in the other. With ImageMagick version 7, we improved the design based on lessons learned from the version 6 implementation. ImageMagick was originally designed to display RGB images to an X Windows server. Over time we extended support to RGBA images and then to the CMYK and CMYKA image format. With ImageMagick version 7, we extend support to arbitrary colorspaces with an arbitrary number of pixel channels. In addition, ImageMagick 7 stores pixel channels as floats permitting out of band values (e.g. negative) and reduces rounding error. There are numerous other design enhancements described within.

##### API Changes

 To support variable pixel channels in the MagickCore API, pixel handling has changed when getting or setting channels. You can access channels as an array, pixel[i], or use accessor methods. Magick++ and PerlMagick APIs remain unchanged from version 6.

##### Shell API Overhaul

 The command-line interface has undergone a major overhaul, emphasizing options reading from scripts, file streams, co-processing, daemon/server backends, and multi-machine distributed processing.

##### Releases & Support

 ImageMagick version 7 is available now as a production release. Version 6 continues to be supported for a minimum of 10 years for bug fixes and security patches.

## High Dynamic Range Imaging

 ImageMagick version 7 enables high dynamic range imaging (HDRI) by default. HDRI accurately represents the wide range of intensity levels found in real scenes ranging from the brightest direct sunlight to the deepest darkest shadows. In addition, image processing results are more accurate. The disadvantage is it requires more memory and may result in slower processing times. If you see differences in the results of your version 6 command-line with version 7, it is likely due to HDRI. You may need to add -clamp to your command-line to constrain pixels to the 0 .. QuantumRange range, or disable HDRI when you build ImageMagick version 7. To disable HDRI (recommended for smart phone builds such as iOS or production sites where performance is a premium), simply add --disable-hdri to the configure script command line when building ImageMagick.

## Pixel Channels

 A pixel is comprised of one or more color values, or channels (e.g. red pixel channel).

 Prior versions of ImageMagick (4-6), support 4 to 5 pixel channels (RGBA or CMYKA). The first 4 channels are accessed with the PixelPacket data structure. The structure includes 4 members of type Quantum (typically 16-bits) of red, green, blue, and opacity. The black channel or colormap indexes are supported by a separate method and structure, IndexPacket. As an example, here is a code snippet from ImageMagick version 6 that negates the color components (but not the alpha component) of the image pixels:

 im6-pixel-loop.c

```
for (y=0; y < (ssize_t) image->rows; y++)
{
  IndexPacket
    *indexes;

  PixelPacket
    *q;

  q=GetCacheViewAuthenticPixels(image_view,0,y,image->columns,1,exception);
  if (q == (PixelPacket *) NULL)
    {
      status=MagickFalse;
      continue;
    }
  indexes=GetCacheViewAuthenticIndexQueue(image_view);
  for (x=0; x < (ssize_t) image->columns; x++)
  {
    if ((channel & RedChannel) != 0)
      q->red=(Quantum) QuantumRange-q->red;
    if ((channel & GreenChannel) != 0)
      q->green=(Quantum) QuantumRange-q->green;
    if ((channel & BlueChannel) != 0)
      q->blue=(Quantum) QuantumRange-q->blue;
    if (((channel & IndexChannel) != 0) &&
        (image->colorspace == CMYKColorspace))
      indexes[x]=(IndexPacket) QuantumRange-indexes[x];
    q++;
  }
  if (SyncCacheViewAuthenticPixels(image_view,exception) == MagickFalse)
    status=MagickFalse;
}
```

 ImageMagick version 7 supports any number of channels from 1 to 64 (and beyond) and simplifies access with a single method that returns an array of pixel channels of type Quantum. Source code that compiles against prior versions of ImageMagick requires refactoring to work with ImageMagick version 7. We illustrate with an example. Let's naively refactor the version 6 code snippet from above so it works with the ImageMagick version 7 API:

 im7-naive-loop.c

```
for (y=0; y < (ssize_t) image->rows; y++)
{
  Quantum
    *q;

  q=GetCacheViewAuthenticPixels(image_view,0,y,image->columns,1,exception);
  if (q == (Quantum *) NULL)
    {
      status=MagickFalse;
      continue;
    }
  for (x=0; x < (ssize_t) image->columns; x++)
  {
    if ((GetPixelRedTraits(image) & UpdatePixelTrait) != 0)
      SetPixelRed(image,QuantumRange-GetPixelRed(image,q),q);
    if ((GetPixelGreenTraits(image) & UpdatePixelTrait) != 0)
      SetPixelGreen(image,QuantumRange-GetPixelGreen(image,q),q);
    if ((GetPixelBlueTraits(image) & UpdatePixelTrait) != 0)
      SetPixelBlue(image,QuantumRange-GetPixelBlue(image,q),q);
    if ((GetPixelBlackTraits(image) & UpdatePixelTrait) != 0)
      SetPixelBlack(image,QuantumRange-GetPixelBlack(image,q),q);
    if ((GetPixelAlphaTraits(image) & UpdatePixelTrait) != 0)
      SetPixelAlpha(image,QuantumRange-GetPixelAlpha(image,q),q);
    q+=GetPixelChannels(image);
  }
  if (SyncCacheViewAuthenticPixels(image_view,exception) == MagickFalse)
    status=MagickFalse;
}
```

Let's do that again but take full advantage of the new variable pixel channel support:

 im7-optimized-loop.c

```
for (y=0; y < (ssize_t) image->rows; y++)

{
  Quantum
    *q;

  q=GetCacheViewAuthenticPixels(image_view,0,y,image->columns,1,exception);
  if (q == (Quantum *) NULL)
    {
      status=MagickFalse;
      continue;
    }
  for (x = 0; x < (ssize_t) image->columns; x++)
  {
    ssize_t
      i;

    if (GetPixelWriteMask(image,q) <= (QuantumRange/2))
      {
        q+=GetPixelChannels(image);
        continue;
      }
    for (i=0; i < (ssize_t) GetPixelChannels(image); i++)
    {
      PixelChannel channel = GetPixelChannelChannel(image,i);
      PixelTrait traits = GetPixelChannelTraits(image,channel);
      if ((traits & UpdatePixelTrait) == 0)
        continue;
      q[i]=QuantumRange-q[i];
    }
    q+=GetPixelChannels(image);
  }
  if (SyncCacheViewAuthenticPixels(image_view,exception) == MagickFalse)
    status=MagickFalse;
}
```

Note, how we use GetPixelChannels() to advance to the next set of pixel channels.

 The colormap indexes and black pixel channel (for the CMYK colorspace) are no longer stored in the index channel, previously accessed with GetAuthenticIndexQueue() and GetCacheViewAuthenticIndexQueue(). Instead they are now a first class pixel channel and accessed as a member of the pixel array (e.g. pixel[4]) or with the convenience pixel accessor methods GetPixelIndex(), SetPixelIndex(), GetPixelBlack(), and SetPixelBlack().

As a consequence of using an array structure for variable pixel channels, auto-vectorization compilers have additional opportunities to speed up pixel loops.

The `sync` channel in IMv6 was really a flag instead of a channel. In IMv7, we instead use a flag: -define compose:sync=false.

#### Pixel Accessors

You can access pixel channel as array elements (e.g. pixel[1]) or use convenience accessors to get or set pixel channels:

 GetPixela() SetPixela()
 GetPixelAlpha() SetPixelAlpha()
 GetPixelb() SetPixelb()
 GetPixelBlack() SetPixelBlack()
 GetPixelBlue() SetPixelBlue()
 GetPixelCb() SetPixelCb()
 GetPixelCr() SetPixelCr()
 GetPixelCyan() SetPixelCyan()
 GetPixelGray() SetPixelGray()
 GetPixelGreen() SetPixelGreen()
 GetPixelIndex() SetPixelIndex()
 GetPixelL() SetPixelL()
 GetPixelMagenta() SetPixelMagenta()
 GetPixelReadMask() SetPixelReadMask()
 GetPixelWriteMask() SetPixelWriteMask()
 GetPixelMetacontentExtent() SetPixelMetacontentExtent()
 GetPixelOpacity() SetPixelOpacity()
 GetPixelRed() SetPixelRed()
 GetPixelYellow() SetPixelYellow()
 GetPixelY() SetPixelY()

You can find these accessors defined in the header file, MagickCore/pixel-accessor.h

#### Pixel Traits

Each pixel channel includes one or more of these traits:

Undefined

no traits associated with this pixel channel

Copy

do not update this pixel channel, just copy it

Update

update this pixel channel

Blend

blend this pixel channel with the alpha mask if it's enabled

We provide these methods to set and get pixel traits:

 GetPixelAlphaTraits() SetPixelAlphaTraits()
 GetPixelBlackTraits() SetPixelBlackTraits()
 GetPixelBlueTraits() SetPixelBlueTraits()
 GetPixelCbTraits() SetPixelCbTraits()
 GetPixelChannelTraits() SetPixelChannelTraits()
 GetPixelCrTraits() SetPixelCrTraits()
 GetPixelGrayTraits() SetPixelGrayTraits()
 GetPixelGreenTraits() SetPixelGreenTraits()
 GetPixelIndexTraits() SetPixelIndexTraits()
 GetPixelMagentaTraits() SetPixelMagentaTraits()
 GetPixelRedTraits() SetPixelRedTraits()
 GetPixelYellowTraits() SetPixelYellowTraits()
 GetPixelYTraits() SetPixelYTraits()

For convenience you can set the active trait for a set of pixel channels with a channel mask and this method:

SetImageChannelMask()

Previously MagickCore methods had channel analogs, for example, NegateImage() and NegateImageChannels(). The channel analog methods are no longer necessary because the pixel channel traits specify whether to act on a particular pixel channel or whether to blend with the alpha mask. For example, instead of

NegateImageChannel(image,channel);

we use:

 channel_mask=SetImageChannelMask(image,channel);
 NegateImage(image,exception);
 (void) SetImageChannelMask(image,channel_mask);

#### Pixel User Channels

 In version 7, we introduce pixel user channels. Traditionally we utilize 4 channels, red, green, blue, and alpha. For CMYK we also have a black channel. User channels are designed to contain whatever additional channel information that makes sense for your application. Some examples include extra channels in TIFF or PSD images or perhaps you require a channel with infrared information for the pixel. You can associate traits with the user channels so that when they are acted upon by an image processing algorithm (e.g. blur) the pixels are copied, acted upon by the algorithm, or even blended with the alpha channel if that makes sense.

#### Pixel Metacontent

 In version 7, we introduce pixel metacontent. Metacontent is content about content. So rather than being the content itself, it's something that describes or is associated with the content. Here the content is a pixel. The pixel metacontent is for your exclusive use (internally the data is just copied, it is not modified) and is accessed with these MagickCore API methods:

 SetImageMetacontentExtent()
 GetImageMetacontentExtent()
 GetVirtualMetacontent()
 GetAuthenticMetacontent()
 GetCacheViewAuthenticMetacontent()
 GetCacheViewVirtualMetacontent()

##### Alpha

 We support alpha now, previously opacity. With alpha, a value of 0 means transparent and QuantumRange means opaque. The PixelInfo structure member alpha replaces opacity, and hexadecimal sRGB alpha notation is reversed (e.g., #0000 is fully transparent).

##### Colorspace

 Rec601Luma and Rec709Luma colorspaces are no longer supported. Specify the gray colorspace and choose from intensity options like Rec601Luminance or Rec709Luminance.

##### Grayscale

 Previously, grayscale images consumed 4 channels (red, green, blue, alpha). With version 7, grayscale consumes only 1 channel, requiring far fewer resources.

## Masks

 Version 7 supports masks for most image operators. White pixels in a read mask ignore corresponding pixels in an image, whereas white pixels in a write mask protect corresponding pixels. From the command-line, associate a mask using -read-mask and -write-mask options. The -mask option is also supported for backwards compatibility.

In this example, we compute the distortion of a masked reconstructed image:

 $ compare -metric rmse -read-mask hat_mask.png hat.png wizard.png difference.png

Here we protect certain pixels from change:

 $ magick rose: -write-mask rose_bg_mask.png -modulate 110,100,33.3 +write-mask rose_blue.png

 A mask associated with an image persists until modified or removed, which may produce unexpected results for complex command-lines. Here we only want to clip when applying the alpha option, not the resize:

 $ magick -density 300 -colorspace srgb image.eps -alpha transparent -clip -alpha opaque +clip -resize 1000x1000 -strip image.png

#### MagickCore API Changes

-  Almost all image processing algorithms are now channel aware.

-  Adds an ExceptionInfo argument to methods lacking it in v6 (e.g., NegateImage(image,MagickTrue,exception)).

-  All method channel analogs removed (use pixel traits instead).

-  Public/private API calls declared with GCC visibility attribute.

-  InterpolatePixelMethod enum is now PixelInterpolateMethod.

-  IntegerPixel removed (use LongPixel), LongLongPixel added.

-  Image signatures updated for variable pixel channels.

-  PixelPacket, LongPacket, and DoublePacket consolidated to PixelInfo.

-  ChannelMoments member I renamed to invariant to avoid conflict with complex.h.

-  Added length parameter to FormatMagickSize().

#### MagickWand & Magick++ APIs

###### MagickWand API:

-  Almost all image processing algorithms are channel aware.

-  DrawMatte() method is now called DrawAlpha().

-  MagickSetImageBias() and MagickSetImageClipMask() no longer supported.

###### Magick++ API:

-  Channel-aware algorithms.

-  Example construct to avoid operating on alpha channel:
image.negateChannel(Magick::ChannelType(Magick::CompositeChannels ^ Magick::AlphaChannel));

#### Header Files

 Prior versions of ImageMagick reference header files as magick/ and wand/. ImageMagick 7 uses MagickCore/ and MagickWand/ respectively. For example:

 #include <MagickCore/MagickCore.h>
 #include <MagickWand/MagickWand.h>

#### Deprecated Features Removed

All deprecated features from v6 are removed, including Magick-config and Wand-config. Use instead:

 MagickCore-config
 MagickWand-config

 The FilterImage() method is removed (use ConvolveImage()). The Bessel filter is removed as an alias for Jinc (use -filter Jinc).

## Shell API or Command-line Interface

 The primary focus of changes to the Shell API/CLI is abstraction so options can be read from command line arguments, files (scripts), or file streams (interactive commands/co-processing).

 The CLI parser was rewritten to perform options strictly in a do-it-as-you-see-it order. You can no longer give operations before providing an image. Error reporting now pinpoints exact options causing exceptions.

 Parentheses (( and )) push/pull image lists, while curly braces ({ and }) push/pull image settings. Command-line character limits increased from 4096 to 131072 characters.

#### Command Changes

magick

IMPORTANT: The magick command is the new primary command of the Shell API, replacing convert. Enables magick scripts or piping options.

magick-script

Same as magick with an implicit -script option, allowing she-bang scripts (e.g., #!/usr/bin/env magick-script).

Other Utilities

animate, compare, composite, conjure, convert, display, identify, import, mogrify, montage, stream are symbolic links to magick. On Windows, use magick compare, magick identify, etc. Do not use magick convert.

#### Behavioral Changes

Image settings apply to each image on the command line. Use parentheses to associate settings with particular images:

 $ magick \( -page +10+20 first.png \) \( -page +100+200 second.png \) ...

 Default channel updates include RGBA (previously RGB). Use -channel RGB if legacy results differ. +combine requires a colorspace argument. -gamma no longer accepts multiple arguments.

#### New Options

{ ... }

Save/restore current image settings.

-alpha activate/deactivate

Enables/disables alpha channel with persistence.

-alpha discrete

Treat alpha channel independently without blending.

-channel-fx expression

Exchange, extract, or copy one or more image channels.

-exit

Stop processing immediately.

-read {image}

Explicit read of an image.

-script {file}

Read further options from a given file or pipeline.

## Performance Improvements

Operating on grayscale images is significantly improved as only one channel is required (previously three).

The performance of -fx option has increased by one to two orders of magnitude.

## Version 7 Change Summary

##### High Dynamic Range Imaging

HDRI enabled by default for accurate results; can be disabled via --disable-hdri.

##### Pixels & Alpha

Addressed as an array of channels (e.g., pixel[PixelRedChannel]) with convenience accessors. Alpha replaces opacity (0 transparent, QuantumRange opaque).

##### Grayscale & Masks

Grayscale consumes one channel. Version 7 fully supports both read and write masks.

##### MagickCore API & Deprecations

Channel-aware algorithms, ExceptionInfo arguments added, and all v6 deprecated channel analogs removed.
