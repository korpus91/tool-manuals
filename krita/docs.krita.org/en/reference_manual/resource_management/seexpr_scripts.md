# SeExpr Scripts — Krita Manual 5.3.0 documentation

- Docs »

- Reference Manual »

- Resource Management »

- SeExpr Scripts

-

# SeExpr Scripts¶

SeExpr scripts allow you to render dynamically generated textures. They are saved as .se files. They can be used as fill for generated layers.

See also

-
Introduction to SeExpr

-
SeExpr Quick Reference

-
SeExpr

-
“Procedural texture generator (example and wishes)” on Krita Artists

-
Inigo Quilez’s articles

-
The Book of Shaders

## Adding new scripts¶

Like with Patterns, there is a similar UI with which you can manage SeExpr presets. This panel is available by opening the Fill Layer dialog, and selecting SeExpr:

At the bottom of the tab, beneath the resource-filter input field, there are the Import resource and Delete resource buttons. Select the former to add presets to the list.

Similarly, removing presets can be done by pressing the Delete resource button. Krita will not delete the actual file then, but rather deactivate it, and thus not load it.

## Temporary scripts¶

Layers keep a copy of the textual script that was used to generate them. You can access it by going to the Options tab and copying the text. You can then paste it into a new SeExpr Fill Layer.
