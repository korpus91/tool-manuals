# SeExpr — Krita Manual 5.3.0 documentation

- Docs »

- Reference Manual »

- Layers and Masks »

- Fill Layers »

- SeExpr

-

# SeExpr¶

Added in version 4.4.

Fills the layer with a pattern specified through Disney Animation’s SeExpr expression language.

See also

-
Introduction to SeExpr

-
SeExpr Quick Reference

-
SeExpr Scripts

-
“Procedural texture generator (example and wishes)” on Krita Artists

-
Inigo Quilez’s articles

-
The Book of Shaders

SeExpr is an embeddable, arithmetic expression language that enables you to write shader-like scripts. Through this language, Krita can add dynamically generated textures like lava (example above), force fields, wood, marble, etc. to your layers.

As with Patterns, you can create your own and use those as well. For some examples, please check out the thread “Procedural texture generator (example and wishes)” on Krita Artists. You can download them as a bundle through Amyspark’s blog.

Script

Select the desired preset out of any existing bundled presets. This tab is identical to the Pattern preset selector.

Options

This tab allows you to edit the selected preset, and apply its script to the layer.

There are three sections. The first bar allows you to edit and save the selected preset:

If your script is syntactically correct, the middle box lets you adjust its variables through widgets.

The lower box contains the script text, and shows the detected syntax errors, if any.

You can adjust how much space the latter two boxes have through their splitter.
