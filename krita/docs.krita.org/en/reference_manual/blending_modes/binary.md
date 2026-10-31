# Binary — Krita Manual 5.3.0 documentation

- Docs »

- Reference Manual »

- Blending Modes »

- Binary

-

# Binary¶

Binary modes are a special class of blending modes which utilize binary operators for calculations. Binary modes are unlike every other blending modes as these modes have a fractal attribute with falloff similar to other blending modes. Binary modes can be used for generation of abstract art using layers with very smooth surfaces. All binary modes have capitalized letters to distinguish themselves from other blending modes.

To clarify on how binary modes work, convert decimal values to binary values, then treat 1 or 0 as T or F respectively, and use binary operation to get the end result, and then convert the result back to decimal.

Warning

Binary blending modes do not work on float images or negative numbers! So, don’t report bugs about using binary modes on unsupported color spaces.

## AND¶

Performs the AND operation for the base and blend layer. Similar to multiply blending mode.

Left: Base Layer. Middle: Blend Layer. Right: AND.¶

Left: Base Layer. Middle: Blend Layer. Right: AND.¶

## CONVERSE¶

Performs the inverse of IMPLICATION operation for the base and blend layer. Similar to screen mode with blend layer and base layer inverted.

Left: Base Layer. Middle: Blend Layer. Right: CONVERSE.¶

Left: Base Layer. Middle: Blend Layer. Right: CONVERSE.¶

## IMPLICATION¶

Performs the IMPLICATION operation for the base and blend layer. Similar to screen mode with base layer inverted.

Left: Base Layer. Middle: Blend Layer. Right: IMPLICATION.¶

Left: Base Layer. Middle: Blend Layer. Right: IMPLICATION.¶

## NAND¶

Performs the inverse of AND operation for base and blend layer. Similar to the inverted multiply mode.

Left: Base Layer. Middle: Blend Layer. Right: NAND.¶

Left: Base Layer. Middle: Blend Layer. Right: NAND.¶

## NOR¶

Performs the inverse of OR operation for base and blend layer. Similar to the inverted screen mode.

Left: Base Layer. Middle: Blend Layer. Right: NOR.¶

Left: Base Layer. Middle: Blend Layer. Right: NOR.¶

## NOT CONVERSE¶

Performs the inverse of CONVERSE operation for base and blend layer. Similar to the multiply mode with base layer and blend layer inverted.

Left: Base Layer. Middle: Blend Layer. Right: NOT CONVERSE.¶

Left: Base Layer. Middle: Blend Layer. Right: NOT CONVERSE.¶

## NOT IMPLICATION¶

Performs the inverse of IMPLICATION operation for base and blend layer. Similar to the multiply mode with the blend layer inverted.

Left: Base Layer. Middle: Blend Layer. Right: NOT IMPLICATION.¶

Left: Base Layer. Middle: Blend Layer. Right: NOT IMPLICATION.¶

## OR¶

Performs the OR operation for base and blend layer. Similar to screen mode.

Left: Base Layer. Middle: Blend Layer. Right: OR.¶

Left: Base Layer. Middle: Blend Layer. Right: XOR.¶

## XOR¶

Performs the XOR operation for base and blend layer. This mode has a special property that if you duplicate the blend layer twice, you get the base layer.

Left: Base Layer. Middle: Blend Layer. Right: XOR.¶

Left: Base Layer. Middle: Blend Layer. Right: XOR.¶

## XNOR¶

Performs the XNOR operation for base and blend layer. This mode has a special property that if you duplicate the blend layer twice, you get the base layer.

Left: Base Layer. Middle: Blend Layer. Right: XNOR.¶

Left: Base Layer. Middle: Blend Layer. Right: XNOR.¶
