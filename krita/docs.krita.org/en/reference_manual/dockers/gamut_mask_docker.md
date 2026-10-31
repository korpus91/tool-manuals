# Gamut Masks Docker — Krita Manual 5.3.0 documentation

- Docs »

- Reference Manual »

- Dockers »

- Gamut Masks Docker

-

# Gamut Masks Docker¶

Added in version 4.2: Docker for gamut masks selection and management.

## Usage¶

 an icon (1) to apply a mask to color selectors.

Gamut Masks can be imported and exported in Managing Resources.

### Management Toolbar¶

Create new mask (2)

Opens the mask editor with an empty template.

Edit mask (3)

Opens the currently selected mask in the editor.

Duplicate mask (4)

Creates a copy of the currently selected mask and opens the copy in the editor.

Delete mask (5)

Deletes the currently selected mask.

Gamut Masks are a type of resource. As such, they can be saved, tagged, reordered and added to bundles. They are stored inside *.kgm files, which are ZIP files consisting of a mimetype (application/x-krita-gamutmask), a preview.png and an SVG file describing the mask.

## Editing¶

If you choose to create a new mask, edit, or duplicate selected mask, the mask template document will be opened as a new view (1).

There you can create new shapes and modify the mask with standard vector tools (Vector Graphics).

Fill in the fields at (2).

Title (Mandatory)

The name of the gamut mask.

Description

A description.

Preview the mask in the artistic color selector (4), save the mask (5), or cancel editing (3).

Warning

-
The shapes need to be added to the layer named maskShapesLayer (which is selected by default).

-
The shapes need have solid background to show correctly in the editor.

-
A template with no shapes cannot be saved.

Note

The mask is intended to be composed of basic vector shapes. Although interesting results might arise from using advanced vector drawing techniques, not all features are guaranteed to work properly (e.g. grouping, vector text, etc.).

## External Info¶

-
Color Wheel Masking, Part 1 by James Gurney.

-
The Shapes of Color Schemes by James Gurney.

-
Gamut Masking Demonstration by James Gourney (YouTube).
