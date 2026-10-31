# Path Selection Tool — Krita Manual 5.3.0 documentation

- Docs »

- Reference Manual »

- Tools »

- Path Selection Tool

-

# Path Selection Tool¶

This tool, represented by an ellipse with a dashed border and a curve control, allows you to make a Selections of an area by drawing a path around it. Click where you want each point of the path to be. Click and drag to curve the line between points. Finally click on the first point you created to close your path.

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
Hovering over a selection allows you to move it.

-
When not actively making a selection,  will open up a selection quick menu with amongst others the ability to edit the selection. If you already began making a selection,  will undo the last added point.

Note

You can switch the behavior of the Alt key to use the Ctrl key instead by toggling the switch in the General Settings.

## Tool Options¶

Added in version 4.1.3:

Autosmooth Curve

Toggling this will have nodes initialize with smooth curves instead of angles. Untoggle this if you want to create sharp angles for a node. This will not affect curve sharpness from dragging after clicking.

Anti-aliasing

This toggles whether or not to give selections feathered edges. Some people prefer hard-jagged edges for their selections.

Added in version 4.2:

Autosmooth Curve

Toggling this will have nodes initialize with smooth curves instead of angles. Untoggle this if you want to create sharp angles for a node. This will not affect curve sharpness from dragging after clicking.

Angle Snapping Delta

The angle to snap to.

Activate Angle Snap

Angle snap will make it easier to have the next line be at a specific angle of the current. The angle is determined by the Angle Snapping Delta.
