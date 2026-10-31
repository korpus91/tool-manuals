# Normal Blend node — Material Maker documentation

-

- Nodes library

- Filter nodes

- Normal Blend node

-

# Normal Blend node

The Normal Blend node blends two normal map inputs using an optional opacity. The second input is the base and the first input gets applied on top of it using the Reorient method described in this article, using the opacity (defined by the opacity parameter, or the optional grayscale input).

## Inputs

The Normal Blend node accepts three inputs:

-
The first input is the top layer.

-
The second input is the bottom layer.

-
The third input is an optional mask that will be multiplied with the opacity parameter.

## Outputs

The Normal Blend node outputs the result of the blend operation.

## Parameters

The Normal Blend node has a single parameter:

-
The opacity used when mixing the result of the blend operation with the bottom input when the corresponding input is not connected. When connected, the opacity channel is multiplied with that parameter.

## Notes

The opacity input will be considered (and implicitly converted to) grayscale if it is a color texture.

## Example images
