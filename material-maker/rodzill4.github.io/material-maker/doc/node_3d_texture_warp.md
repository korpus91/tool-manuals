# Warp node — Material Maker documentation

-

- Nodes library

- 3D nodes

- 3D textures

- Warp node

-

# Warp node

The Warp node is variadic and deform one or more 3D textures according to the derivative of a grayscale 3D texture.

## Inputs

The Warp node accepts three inputs:

-
The Source input is the image to be deformed.

-
The Height map input is a grayscale 3D texture whose derivative will be used to deform the source.

-
Optional Strength map which multiplies the strength parameter by the map value.

## Outputs

The Warp node outputs the deformed 3D texture.

## Parameters

The Warp node has three parameters:

-
mode, that defines how the warp node calculates the offset it applies. Slope offsets by a distance calculated from the slope, and Distance to top offsets by a distance calculated from the slope and the distance to the top (this mode makes it posible to make all points of a slope get their value from the top, hence generating mosaic-like patterns).

-
strength to scale the warp effect.

-
epsilon is used to evaluate the second input’s derivative.

## Example images
