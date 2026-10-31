# Brush Preset — Krita Manual 5.3.0 documentation

- Docs »

- Reference Manual »

- Resource Management »

- Brush Preset

-

# Brush Preset¶

Brush Presets, known within Krita as paintoppresets, store the preview thumbnail, brush-engine, the parameters, the brush tip, and, if possible, the texture. They are saved as .kpp files, except for MyPaint brushes, which are saved as .myb files.

For information regarding the brush system, see Brushes.

## The Docker¶

The docker for Paint-op presets is the Preset Docker. Here you can tag, add, remove and search brush presets.

## Editing the preview thumbnail¶

You can edit the preview thumbnail in the brush-scratchpad, but you can also open the \*.kpp file in Krita to get a 200x200 file to edit to your wishes. For MyPaint brushes, there is a separate PNG file which is the same name as the .myb file, except with _prev attached.

## Structure¶

MyPaint brushes are stored as JSON files with an accompanying preview image, while .kpp files are PNGs which contain an annotation with the XML data for the brush engine. You can view this data when having the .kpp file open, via image ‣ properties ‣ annotations, or by using the ImageMagick command identify -verbose {FILENAME} on the .kpp.
