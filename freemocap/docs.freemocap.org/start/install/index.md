# Install FreeMoCap | FreeMoCap

Skip to main content

Version: 2.0 (alpha)

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-10-14

freemocap main at v2.0.0-alpha.25 (75c8acc2): GitHub release v2.0.0-alpha.25 asset list; PyPI freemocap JSON (latest 1.8.2, no 2.x); build-installers-pyinstaller.yml matrix, code-signing steps, and CUDA routing to Cloudflare R2 (alpha.25 CUDA assets confirmed live there); freemocap-docs src/components/download/downloads.ts; freemocap.org/download; freemocap-ui electron-builder.json (NSIS, dmg/zip arm64, notarize), update-handler.ts, AutoUpdateContext.tsx and menu-builder.ts (Help > Check for Updates, manual only); skellytracker model_registry.py (models downloaded on first use); README.md development-branch install steps; .python-version (3.12). Rewritten from the alpha.21 page, which still described a conda + pip install that only reaches v1.

2026-08-25

freemocap clone pinned at v2.0.0-alpha.21: pyproject.toml (requires-python >=3.11, cuda/cpu extras, [project.scripts], uv git sources), README.md quickstart/install-from-source, .python-version, build-installers-pyinstaller.yml build matrix and R2 routing, freemocap-ui/electron-builder.json targets, freemocap-docs src/components/download/downloads.ts asset names

2026-08-19

v1 (ported, not yet re-checked against v2)

More about how these docs are written

# Install FreeMoCap

## Download​

Go to the FreeMoCap download page and get the file for your computer:

Your computerFile

Mac with Apple Silicon (M1 or newer).dmg

Windows PC.exe: the CUDA version if you have an NVIDIA graphics card, otherwise the CPU version

Linux PC.deb for Ubuntu, Debian, Mint, and similar, otherwise .AppImage. CUDA version if you have an NVIDIA graphics card.

If you're not sure whether you have an NVIDIA graphics card, get the CPU version.

## Install and open FreeMoCap​

- Mac

- Windows

- Linux

- Open the .dmg.

- Drag FreeMoCap into your Applications folder.

- Open FreeMoCap from Applications.

If macOS blocks it, open System Settings > Privacy & Security and click Open Anyway.

- Double-click the .exe and follow the installer.

- Open FreeMoCap from the Start menu.

If you see a Windows protected your PC message, click More info, then Run anyway.

For the .deb, run:

```

sudo apt install ./freemocap_*.deb

```

Then open FreeMoCap from your app launcher.

For the .AppImage, run:

```

chmod +x freemocap_*.AppImage

./freemocap_*.AppImage

```

The first launch can take a minute. Stay online for your first recording, because FreeMoCap downloads its tracking model then.

## Update​

Choose Help > Check for Updates…. If there's a new version, FreeMoCap offers to install it.

## Uninstall​

Uninstall FreeMoCap the way you'd uninstall any app. Your recordings stay in the freemocap_data folder in your home folder.

## Run from source (for developers)​

Install uv, Node.js, and git, then run:

```

git clone https://github.com/freemocap/freemocap.git

cd freemocap

uv sync

uv run python freemocap/__main__.py

```

On Windows or Linux without an NVIDIA graphics card, use uv sync --no-default-groups --group cpu instead of uv sync.

In a second terminal, start the interface:

```

cd freemocap-ui

npm install

npm run dev

```

## Next​

Make your first recording. Stuck? See fix an installation problem or ask in #help-requests on Discord.

- Download

- Install and open FreeMoCap

- Update

- Uninstall

- Run from source (for developers)

- Next
