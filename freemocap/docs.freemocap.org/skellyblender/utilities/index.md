# Utilities | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

Re-checked against polyrepo-clones/freemocap_blender_addon (main, package v2026.04.1041): read utilities/git_source_manager.py, install_dependencies.py, and recording_framerate.py in full, plus utilities/get_fcurves_from_object_action.py and its caller foot_locking/methods/foot_group_movement.py (that module had been omitted from the list); confirmed resolve_git_sources is imported without ever being called in the package __init__.py and that OPTIONAL_DEPENDENCIES is empty

2026-08-24

freemocap_blender_addon source read directly (package v2026.04.1041); integration verified against the FreeMoCap clone (the core Blender export module)

More about how these docs are written

# Utilities

Four small modules under utilities/ are generally useful for anyone embedding Python tooling in Blender:

- get_fcurves_from_object_action.py: get_fcurves_from_object_action(obj) returns the fcurves of an object's active action, handling legacy actions (reading action.fcurves directly, the pre-5.0 behavior) and Blender 5.0+ slotted actions (via bpy_extras.anim_utils.action_get_channelbag_for_slot() on the active action slot); it returns None when the object has no animated action or the lookup fails. The foot-group-movement foot locking method calls it.

- git_source_manager.py: resolve_git_sources() clones or fast-forward-updates git repositories into ~/.cache/freemocap/git_sources/ (override with FREEMOCAP_GIT_SOURCES_DIR or XDG_CACHE_HOME), records last-seen commits in .source_lock.json, stashes local changes before pulling, and degrades gracefully to the cached copy when offline. It's stdlib-only, so it works in Blender's bundled Python. The addon imports it at startup but does not currently call it for anything.

- install_dependencies.py: ensures pip exists in Blender's interpreter, checks imports locally with zero subprocesses, and installs anything missing from pip, git URL, or local-path specs. Presently a no-op beyond the pip check, given the empty dependency list.

- recording_framerate.py: the timestamps-based framerate derivation described preceding.
