# Directional Blur node — Material Maker documentation

-

- Nodes library

- Filter nodes

- Directional Blur node

-

# Directional Blur node

The Directional Blur node applies a Gaussian blur algorithm to its input in a given direction.

## Inputs

The Directional Blur node accepts an RGBA input to be blurred and an optional blur mask that defines the intensity of the blur effect.

## Outputs

The Directional Blur node outputs the result of the blur operation.

## Parameters

The Directional Blur node has four parameters:

-
The grid size defines the size of the output image.

-
The mode spcifies whether the blur will move in one direction or both.

-
The sigma parameter defines how smooth the output will be.

-
The angle specifies the angle of the blur algorithm.

-

Whether 32 Bit buffer(s) are used to sample the input.

Reduces banding artifacts but could result in higher video memory usage.

## Notes

This node outputs an image that has a fixed size.

## Example images
