# In-viewport analysis tools | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

Re-checked every claim against polyrepo-clones/freemocap_blender_addon @ main: Data View Settings panel label and scoping (blender_ui/sub_panels/visualizer_panel.py), the nine visibility toggles and their regex-driven scene graph patterns, motion path target enum and properties plus add/clear-one/clear-all operators, COM vertical projection colors, base of support z threshold/radius/color, joint angle properties, data overlay properties and SpaceView3D.draw_handler_add viewport rendering

2026-08-24

freemocap_blender_addon source read directly (package v2026.04.1041); integration verified against the FreeMoCap clone (the core Blender export module)

More about how these docs are written

# In-viewport analysis tools

The Data View Settings panel operates on the scoped recording:

- Visibility toggles for armature, Skelly mesh, tracked points, rigid bodies, center of mass, capture videos, COM vertical projection, joint angles, and base of support, driven by regular expression patterns over the scene graph.

- Motion paths along any tracked element (center of mass or a named joint), with line thickness, separate past/future colors and ranges, frame stepping, and optional frame-number and keyframe display. Add per element, or clear one/all.

- COM vertical projection coloring: neutral, inside base of support, outside base of support.

- Base of support rendering with a z threshold, contact-point radius, and color.

- Joint angle arcs with configurable angle selection, radius, arc and text colors, text size, orientation, and local offsets.

- Data overlays drawn in the viewport at a configurable position and size: a time-series plot (parameter, window size, line and background styling) and a range-of-motion gauge, plus a clear-all.
