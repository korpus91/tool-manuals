# Log files | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

skellylogs/system/default_paths.py: get_log_file_path(), SKELLYLOGS_LOG_DIR_ENV_VAR, and the ~/skellylogs_data/logs/ default all confirmed to match exactly

2026-08-24

SkellyLogs source and README read directly; consumer usage verified in FreeMoCap and SkellyCam clones

More about how these docs are written

# Log files

By default, get_log_file_path() (in default_paths.py) creates ~/skellylogs_data/logs/ if needed and returns a per-run filename of the form log_<iso8601>_gmt±N.log (: replaced with _ so it is filesystem-friendly, milliseconds marked with ms). The base directory can be redirected wholesale via the SKELLYLOGS_LOG_DIR environment variable, used by tests and CI, or overridden per-call with log_file_path.
