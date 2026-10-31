# tool-manuals

Text conversion of the offline documentation for the tools the studio uses. Read-only manual source for the gamedev MCP server. Images, scripts and styles are dropped; each HTML page is turned into Markdown with the page's main content only (navigation, footers and scripts removed). Converter: html_to_md.py in the studio job folder, standard library only. Pages over 480 KB are split into _p1, _p2 parts.

Built 2026-10-31 from the library copies in Dropbox GameDev-KB\library on PANZERV. Rebuilt only when a pin in gamedev-kb 00_START_HERE.md changes, as a new snapshot commit that states the new source version.

| Folder | Tool | Library source folder |
|---|---|---|
| blender-python-api-5.2/ | Blender Python API 5.2 (the pin in 00_START_HERE.md) | blender-python-api-5.2-html |
| krita/ | Krita manual | krita-manual |
| material-maker/ | Material Maker docs | material-maker-doc |
| mpfb/ | MPFB docs | mpfb-docs |
| imagemagick/ | ImageMagick usage | imagemagick-usage |
| ffmpeg/ | FFmpeg docs (ffmpeg-all, split in 4 parts) | ffmpeg-docs |
| freemocap/ | FreeMoCap docs | freemocap-docs |
| ink/ | ink docs | ink-docs |
| choicescript/ | ChoiceScript docs | choicescript-docs |
| trenchbroom/ | TrenchBroom manual | trenchbroom-manual |

Licences are those of each upstream project's documentation; this repo only reformats the text for search. The paid or licensed docs (Auto-Rig Pro, Godot MCP Pro) are not here: they live in the private gamedev-kb repo under library-text/.

Rule from the studio law: a manual at another version is a wrong source. If a page here disagrees with the pinned version, the pin wins and this snapshot is rebuilt.
