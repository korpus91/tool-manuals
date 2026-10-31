# Fill Layers — Krita Manual 5.3.0 documentation

- Docs »

- Reference Manual »

- Layers and Masks »

- Fill Layers

-

# Fill Layers¶

A Fill Layer is a special layer that Krita generates on-the-fly that can contain either a pattern or a solid color.

By default, the dialog selects the flat color fill. This fills the layer with a singular color. Newly created colored fill layers will be assigned to the currently active foreground color, unless they were made by drag-and-dropping a palette swatch onto the layer stack.

However, there are many more options, with more complex features:

- Gradient Fill

- Multigrid

- Pattern Fill

- Screentone

- SeExpr

- Simplex Noise

## Painting on a fill layer¶

A fill-layer is a single-channel layer, meaning it only has transparency. Therefore, you can erase and paint on fill-layers to make them semi-opaque, or for when you want to have a particular color only. Being single channel, fill-layers are also a little bit less memory-consuming than regular 4-channel paint layers.
