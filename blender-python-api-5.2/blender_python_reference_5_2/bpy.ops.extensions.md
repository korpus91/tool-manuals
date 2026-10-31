# Extensions Operators - Blender Python APIContentsMenuExpandLight modeDark modeAuto light/dark, in light modeAuto light/dark, in dark mode

Skip to content

Blender Python API

   Back to top

# Extensions Operators¶

 bpy.ops.extensions.package_disable()¶

Turn off this extension

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3588

 bpy.ops.extensions.package_install(*, repo_directory='', repo_index=-1, pkg_id='', enable_on_install=True, url='', do_legacy_replace=False)¶

Download and install the extension

Parameters:

-
repo_directory (str) – Repo Directory, (optional, never None)

-
repo_index (int) – Repo Index, (in [-inf, inf], optional)

-
pkg_id (str) – Package ID, (optional, never None)

-
enable_on_install (bool) – Enable on Install, Enable after installing (optional)

-
url (str) – URL, (optional, never None)

-
do_legacy_replace (bool) – Do Legacy Replace, (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:1511

 bpy.ops.extensions.package_install_files(*, filter_glob='*.zip;*.py', directory='', files=None, filepath='', repo='', enable_on_install=True, target='', overwrite=True, url='')¶

Install extensions from files into a locally managed repository

Parameters:

-
filter_glob (str) – filter_glob, (optional, never None)

-
directory (str) – Directory, (optional, never None)

-
files (bpy_prop_collection[OperatorFileListElement] | None) – files, (optional)

-
filepath (str) – filepath, (optional, never None)

-
repo (str) – User Repository, The user repository to install extensions into (optional)

-
enable_on_install (bool) – Enable on Install, Enable after installing (optional)

-
target (str) – Legacy Target Path, Path to install legacy add-on packages to (optional)

-
overwrite (bool) – Legacy Overwrite, Remove existing add-ons with the same ID (optional)

-
url (str) – URL, (optional, never None)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:1511

 bpy.ops.extensions.package_install_marked(*, enable_on_install=True)¶

Undocumented, consider contributing.

Parameters:

enable_on_install (bool) – Enable on Install, Enable after installing (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:1511

 bpy.ops.extensions.package_mark_clear(*, pkg_id='', repo_index=-1)¶

Undocumented, consider contributing.

Parameters:

-
pkg_id (str) – Package ID, (optional, never None)

-
repo_index (int) – Repo Index, (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3675

 bpy.ops.extensions.package_mark_clear_all()¶

Undocumented, consider contributing.

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3722

 bpy.ops.extensions.package_mark_set(*, pkg_id='', repo_index=-1)¶

Undocumented, consider contributing.

Parameters:

-
pkg_id (str) – Package ID, (optional, never None)

-
repo_index (int) – Repo Index, (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3661

 bpy.ops.extensions.package_mark_set_all()¶

Undocumented, consider contributing.

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3686

 bpy.ops.extensions.package_obsolete_marked()¶

Zeroes package versions, useful for development - to test upgrading

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3779

 bpy.ops.extensions.package_show_clear(*, pkg_id='', repo_index=-1)¶

Undocumented, consider contributing.

Parameters:

-
pkg_id (str) – Package ID, (optional, never None)

-
repo_index (int) – Repo Index, (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3748

 bpy.ops.extensions.package_show_set(*, pkg_id='', repo_index=-1)¶

Undocumented, consider contributing.

Parameters:

-
pkg_id (str) – Package ID, (optional, never None)

-
repo_index (int) – Repo Index, (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3734

 bpy.ops.extensions.package_show_settings(*, pkg_id='', repo_index=-1)¶

Undocumented, consider contributing.

Parameters:

-
pkg_id (str) – Package ID, (optional, never None)

-
repo_index (int) – Repo Index, (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3762

 bpy.ops.extensions.package_theme_disable(*, pkg_id='', repo_index=-1)¶

Reset to the default theme if this theme is active

Parameters:

-
pkg_id (str) – Package ID, (optional, never None)

-
repo_index (int) – Repo Index, (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3616

 bpy.ops.extensions.package_theme_enable(*, pkg_id='', repo_index=-1)¶

Turn on this theme

Parameters:

-
pkg_id (str) – Package ID, (optional, never None)

-
repo_index (int) – Repo Index, (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3602

 bpy.ops.extensions.package_uninstall(*, repo_directory='', repo_index=-1, pkg_id='')¶

Disable and uninstall the extension

Parameters:

-
repo_directory (str) – Repo Directory, (optional, never None)

-
repo_index (int) – Repo Index, (in [-inf, inf], optional)

-
pkg_id (str) – Package ID, (optional, never None)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:1511

 bpy.ops.extensions.package_uninstall_marked()¶

Undocumented, consider contributing.

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:1511

 bpy.ops.extensions.package_uninstall_system()¶

Undocumented, consider contributing.

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3579

 bpy.ops.extensions.package_upgrade_all(*, use_active_only=False)¶

Upgrade installed extensions to their latest version from remote repositories

Parameters:

use_active_only (bool) – Active Only, Only upgrade the active repository (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:1511

 bpy.ops.extensions.repo_enable_from_drop(*, repo_index=-1)¶

Undocumented, consider contributing.

Parameters:

repo_index (int) – Repo Index, (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:1844

 bpy.ops.extensions.repo_lock_all()¶

Lock repositories - to test locking

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3848

 bpy.ops.extensions.repo_refresh_all(*, use_active_only=False)¶

Refresh extension & legacy add-ons, reloading modules & meta-data (similar to restarting)

Parameters:

use_active_only (bool) – Active Only, Only refresh the active repository (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:1753

 bpy.ops.extensions.repo_sync(*, repo_directory='', repo_index=-1)¶

Undocumented, consider contributing.

Parameters:

-
repo_directory (str) – Repo Directory, (optional, never None)

-
repo_index (int) – Repo Index, (in [-inf, inf], optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:1511

 bpy.ops.extensions.repo_sync_all(*, use_active_only=False)¶

Refresh the list of extensions for all the remote repositories

Parameters:

use_active_only (bool) – Active Only, Only sync the active repository (optional)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:1511

 bpy.ops.extensions.repo_unlock()¶

Remove the repository file-system lock

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:1931

 bpy.ops.extensions.repo_unlock_all()¶

Unlock repositories - to test unlocking

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3874

 bpy.ops.extensions.status_clear()¶

Undocumented, consider contributing.

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3647

 bpy.ops.extensions.status_clear_errors()¶

Undocumented, consider contributing.

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3636

 bpy.ops.extensions.userpref_allow_online()¶

Allow Blender to access the internet. Add-ons that follow this setting will only connect to the internet if enabled. However, Blender cannot prevent third-party add-ons from violating this rule.

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:4000

 bpy.ops.extensions.userpref_allow_online_popup()¶

Allow Blender to access the internet. Add-ons that follow this setting will only connect to the internet if enabled. However, Blender cannot prevent third-party add-ons from violating this rule.

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:4015

 bpy.ops.extensions.userpref_show_for_update()¶

Open extensions preferences

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3939

 bpy.ops.extensions.userpref_show_online()¶

Show system preferences “Network” panel to allow online access

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3979

 bpy.ops.extensions.userpref_tags_set(*, value=False, data_path='')¶

Set the value of all tags

Parameters:

-
value (bool) – Value, Enable or disable all tags (optional)

-
data_path (str) – Data Path, (optional, never None)

Returns:

Result of the operator call.

Return type:

set[Literal[Operator Return Items]]

File:

addons_core/bl_pkg/bl_extension_ops.py:3908
