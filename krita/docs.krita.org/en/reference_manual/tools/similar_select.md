# Similar Color Selection Tool — Krita Manual 5.3.0 documentation

- Docs »

- Reference Manual »

- Tools »

- Similar Color Selection Tool

-

# Similar Color Selection Tool¶

This tool, represented by a dropper over an area with a dashed border, allows you to make Selections by selecting a point of color. It will select any areas of a similar color to the one you selected. You can adjust the “fuzziness” of the tool in the tool options dock. A lower number will select colors closer to the color that you chose in the first place.

Important

Most of the behavior of the Similar Color Selection Tool is common to all other selection tools, please make sure to read Selections to learn more about this tool.

## Hotkeys and Sticky keys¶

-
Shift +  sets the subsequent selection to ‘add’. You can release the Shift key while dragging, but it will still be set to ‘add’. Same for the others.

-
Alt +  sets the subsequent selection to ‘subtract’.

-
Ctrl +  sets the subsequent selection to ‘replace’.

-
Shift + Alt +  sets the subsequent selection to ‘intersect’.

Added in version 4.2:

-
Hovering your cursor over the dashed line of the selection, or marching ants as it is commonly called, turns the cursor into the move tool icon, which you  and drag to move the selection.

-
 will open up a selection quick menu with amongst others the ability to edit the selection.

Tip

You can switch the behavior of the Alt key to use Ctrl instead by toggling the switch in Tool Settings in the General Settings

Tip

This tool is not bound to any Hotkey, if you want to define one, go to Settings ‣ Configure Krita ‣ Keyboard Shortcuts and search for ‘Similar Color Selection Tool’, there you can select the shortcut you want. Check Shortcut Settings for more info.

## Tool Options¶

Action

This option is explained in the Pixel and Vector Selection Types section.

Selection Extent

Threshold

This controls the range of the color hue used to create the selection. A lower number will select colors closer to the color that you chose in the first place. And a higher number will expand the hue range and select colors even if they are not so similar to the original color.

Adjustments

Added in version 5.1:

Anti-alias

This will smooth the jagged edges present in the region. It differs from feathering in that this will smooth in the direction of the edge instead of all directions, and only if the edge is jagged (high contrast).

Grow Selection

This value extends (positive values) or contracts (negative values) the region.

Feathering Radius

This value will add a soft border to the region.

Reference

Added in version 5.0.

Select which layers to use as a reference for the contiguous select tool. The options are:

Current Layer

Only use the currently selected layer.

All layers

Use all visible layers.

Color Labeled Layers

Use only the layers specified with a certain color label. This is useful for complex images, where you might have multiple lineart layers. Label them with the appropriate color label and use these labels to mark which layers to use as a reference.

Labels Used

Select the color labels of the layers that should be used as reference.
