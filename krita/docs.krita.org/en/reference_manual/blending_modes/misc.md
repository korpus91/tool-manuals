# Misc — Krita Manual 5.3.0 documentation

- Docs »

- Reference Manual »

- Blending Modes »

- Misc

-

# Misc¶

## Bumpmap¶

This filter seems to both multiply and respect the alpha of the input.

## Combine Normal Map¶

Mathematically robust blending mode for normal maps, using Reoriented Normal Map Blending.

## Copy¶

Copies the previous layer exactly. Useful for when using filters and filter-masks.

Left: Normal. Right: Copy.¶

## Copy Red, Green, Blue¶

This is a blending mode that will just copy/blend a source channel to a destination channel. Specifically, it will take the specific channel from the upper layer and copy that over to the lower layers.

So, if you want the brush to only affect the red channel, set the blending mode to ‘Copy Red’.

The copy red, green and blue blending modes also work on filter-layers.¶

This can also be done with filter layers. So if you quickly want to flip a layer’s green channel, make an Invert filter layer with ‘Copy Green’ above it.

Left: Normal. Right: Copy Red.¶

Left: Normal. Right: Copy Green.¶

Left: Normal. Right: Copy Blue.¶

## Dissolve¶

Instead of using transparency, this blending mode will use a random dithering pattern to make the transparent areas look sort of transparent.

Left: Normal. Right: Dissolve.¶
