# Configuration options | FreeMoCap

Skip to main content

Version: 2.0 (alpha)

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-10-14

freemocap main at v2.0.0-alpha.25 (75c8acc2): skellylogs default_paths.py (logs fixed at ~/skellylogs_data/logs, no environment override), freemocap default_paths.py (get_log_file_path unused). Fixed the log location; rest unchanged and not re-checked.

2026-08-25

FreeMoCap source v2.0.0-alpha.21 re-checked (system/default_paths.py, system/telemetry/telemetry_config.py, system/telemetry/telemetry.py, build_info.py, api/server_constants.py, __init__.py, app/app.py, __main__.py) plus Electron main/base-folder.ts, main/api.ts, main/ipc.ts, services/python-server.ts and the SkellyPings client/server

2026-08-24

FreeMoCap source v2.0.0-alpha.21 (system/default_paths.py, system/telemetry/telemetry_config.py, system/telemetry/telemetry.py, build_info.py, server_constants.py, __init__.py) plus the Electron frontend's main/base-folder.ts and services/python-server.ts

More about how these docs are written

# Configuration options

FreeMoCap V2 has deliberately little configuration surface. There is no settings framework (no pydantic BaseSettings, no .env loading, no app-level TOML/YAML). Runtime configuration consists of one environment variable and two small JSON files, described below. Everything else, ports, hostnames, log levels, is hard-coded in source.

## Environment variable: FREEMOCAP_BASE_FOLDER​

The single environment variable the Python backend reads is defined in freemocap/system/default_paths.py:

NamePurposeDefault when unset

FREEMOCAP_BASE_FOLDERRoot folder for FreeMoCap data (recordings, calibrations, telemetry config)~/freemocap_data

This variable is the single point where the base folder is resolved; every other data path derives from it (recordings go in <base>/recordings, calibrations in <base>/calibrations). Logs are the exception. SkellyLogs always writes them to ~/skellylogs_data/logs, whatever the base folder.

Who sets it: the Electron shell passes the user-chosen data folder to the Python server through this variable whenever it spawns the server as a subprocess. Who reads it: get_default_freemocap_base_folder_path(), at call time. When the server runs standalone (from source, in tests), the variable is unset and the home-directory default applies.

## Configuration files​

Two JSON files hold user preferences. They are normally managed through the desktop UI's Settings page rather than edited by hand, but their schemas are simple and stable.

FileLocationRead/written byContents

telemetry_config.json<base folder>/telemetry_config.jsonPython backend reads; Electron UI writes{ "telemetry_enabled": true }

freemocap-config.jsonElectron per-app config directory (see below)Electron only{ "baseDataFolder": "/chosen/path" }

Note the division of labor: the pointer to the base folder cannot be stored inside the base folder (the folder is movable), so it lives in Electron's OS-standard config directory, the only piece of FreeMoCap state kept outside the data folder. The telemetry opt-out lives inside the data folder so both processes agree on its location.

### telemetry_config.json​

Managed by freemocap/system/telemetry/telemetry_config.py:

```

{ "telemetry_enabled": true }

```

Resolution rules:

- If the file does not exist (first launch), the backend treats telemetry as enabled and immediately writes the file so the UI can read the value back.

- If the file exists, the telemetry_enabled boolean is honored.

- If the file exists but is unreadable or malformed JSON, the backend logs a warning and defaults to enabled.

The telemetry initializer (initialize_telemetry(), called during FastAPI app startup) checks this file before sending anything; opting out makes it a no-op. An anonymous installation identifier is stored alongside it as <base folder>/telemetry_uid, written by the SkellyPings client.

### freemocap-config.json​

Managed by the Electron main process (electron/main/base-folder.ts), stored in the platform-standard per-app location:

PlatformPath

Windows%APPDATA%/freemocap/freemocap-config.json

macOS~/Library/Application Support/freemocap/freemocap-config.json

Linux~/.config/freemocap/freemocap-config.json

Its schema:

```

{ "baseDataFolder": "/Users/me/Documents/mocap-data" }

```

Setting the key relocates the data folder via FREEMOCAP_BASE_FOLDER. Electron persists it, then restarts the Python server it owns so the change takes effect immediately (when the server is running standalone and Electron does not own it, the change applies at its next start instead). Removing the key reverts to ~/freemocap_data. An unreadable file falls back to the default with a logged error rather than failing startup.

## Build-time constants (not user-configurable)​

freemocap/build_info.py holds metadata injected at CI build time, just before PyInstaller packaging:

- Build metadata: git SHA, build number, timestamp, tag.

- Telemetry endpoint: the SkellyPings server URL and HMAC secret.

In a from-source/dev build these keep placeholder defaults, and telemetry events are sent unverified (the server accepts but segregates them). These values cannot be changed at runtime; rebuilding with different CI inputs is the only way to alter them.

## Values that are hard-coded​

For completeness, the things people most often look for a setting for, and where they actually live in source:

SettingValueDefined in

Server protocol / hostnamehttp / localhostfreemocap/api/server_constants.py

Preferred port53117freemocap/api/server_constants.py

Port scan rangepreferred port, +49 morefreemocap/api/server_constants.py

Log levelTRACE (via SkellyLogs configure_logging)freemocap/__init__.py

## Not configuration​

Per-recording calibration TOML files (for example {recording_name}_camera_calibration.toml) are pipeline artifacts, not app settings, they capture camera intrinsics/extrinsics for a given recording session. See recording folder structure.

- Environment variable: FREEMOCAP_BASE_FOLDER

- Configuration files

- telemetry_config.json

- freemocap-config.json

- Build-time constants (not user-configurable)

- Values that are hard-coded

- Not configuration
