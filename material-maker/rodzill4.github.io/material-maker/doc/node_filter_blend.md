# Blend node — Material Maker documentation

-

- Nodes library

- Filter nodes

- Blend node

-

# Blend node

The Blend node blends two or more inputs using an optional opacity. It performs a blend operation defined by the blend mode between the inputs, and mixes the result with the background input using the opacity (defined by the opacity parameter multiplied by the grayscale input).

## Inputs

The Blend node accepts three or more inputs:

-
The first input is the background layer.

-
The second input is the first layer.

-
The third input is an optional mask that will be multiplied by the opacity parameter for the first layer.

This node is variadic, and more layers and associated masks can be added.

## Outputs

The Blend node outputs the result of the blend operation.

## Parameters

The Blend node has two or more parameters:

-
The blend mode, that can be one of the following: Normal, Dissolve, Multiply, Screen, Overlay, Hard Light, Soft Light, Linear Light, Vivid Light, Pin Light, Burn, Dodge, Lighten, Darken, Difference, Additive, AddSub, Hard Mix, Exclusion, Hue, Saturation, Color, Value.

-
The opacity is used when mixing the result of the blend operation with the background input when the corresponding input is not connected. When connected, the opacity channel is multiplied with that parameter.

Both parameters are repeated for each additional layer.

## Blending modes

Blend mode

Example

Description

Normal

This is the default blend mode. It simply displays the top layer over the bottom layer without any blending

Dissolve

This blend mode randomly replaces the pixels of the top layer with the pixels of the bottom layer

Multiply

This blend mode multiplies the colors of the two layers, resulting in a darker image

Screen

This blend mode multiplies the inverse of the colors of the two layers, resulting in a lighter image

Overlay

This blend mode multiplies the darker colors and screens the lighter colors. It increases the contrast of the image

Hard Light

This blend mode is similar to Overlay, but it is more intense

Soft Light

This blend mode multiplies the darker colors and screens the lighter colors, but it is less intense than Overlay

Burn

This blend mode darkens the bottom layer to reflect the top layer. It increases the contrast between the two layers

Dodge

This blend mode lightens the bottom layer to reflect the top layer. It decreases the contrast between the two layers

Lighten

This blend mode compares the colors of the two layers and keeps the lighter of the two colors

Darken

This blend mode compares the colors of the two layers and keeps the darker of the two colors

Difference

This blend mode substracts the color of the two layers

Additive

This blend mode adds the color of the two layers

AddSub

This blend mode adds or substract the foreground layer depending on its luminosity

Linear Light

This blend mode is a combination of Linear Dodge and Linear Burn

Vivid Light

This blend mode is similar to Color Dodge and Color Burn, but it is more intense

Pin Light

This blend mode replaces colors of the bottom layer with those of the top layer depending on the luminosity of the top layer

Hard Mix

This blend mode multiplies the colors of the two layers, and maps the resulting color to the nearest primary color

Exclusion

This blend mode is similar to Difference, but it is less intense

Hue

This blend mode takes the hue of the top layer and combines them with the saturation and value of the bottom layer

Saturation

This blend mode takes the saturation of the top layer and combines them with the hue and value of the bottom layer

Color

This blend mode takes the hue and saturation of the top layer and combines them with the value of the bottom layer

Value

This blend mode takes the value of the top layer and combines them with the hue and saturation of the bottom layer

## Notes

The opacity input will be considered (and implicitly converted to) grayscale if it is a color texture.

## Example images
