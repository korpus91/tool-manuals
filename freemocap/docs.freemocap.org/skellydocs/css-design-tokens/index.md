# CSS design tokens | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

Re-read polyrepo-clones/skellydocs/src/css/custom.css and theme.module.css on main (package 0.3.17); all 10 --sk-* token names/defaults, Infima-level overrides, header comment, and font import re-verified

2026-08-24

SkellyDocs source read directly (package at 0.3.17, main); consumer usage verified in this site's package.json, Docusaurus config, custom.css, and fetched SkellyCam docs

More about how these docs are written

# CSS design tokens

custom.css defines the palette as --sk-* variables consumed by theme.module.css, so overriding one variable re-themes every component:

TokenDefaultPurpose

--sk-bg-deep#06050ePage background

--sk-bg-surface#0e0c1aCard/surface background

--sk-border#1a1730Borders and dividers

--sk-text#e8e6f0Primary text

--sk-text-dim#b0aec3Secondary/muted text

--sk-accent#6ee7b7Accent color

--sk-accent-dimrgba(110, 231, 183, 0.15)Accent background tint

--sk-purple#a78bfaSecondary accent

--sk-purple-dimrgba(167, 139, 250, 0.1)Secondary accent tint

--sk-monoJetBrains Mono stackMonospace font

Beyond the tokens, the style sheet also sets Infima-level values: a purple --ifm-color-primary scale, dark backgrounds (#0a0818 page, #110e20 surface), a blurred translucent navbar, footer and active-sidebar-item styling, and a JetBrains Mono import. The file's own header calls it "plumbing only." Component styles belong in theme.module.css.
