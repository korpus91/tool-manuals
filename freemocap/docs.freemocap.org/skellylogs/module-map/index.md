# Module map | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

Line-by-line check of every table row against polyrepo-clones/skellylogs on main: public API exports in __init__.py, module/class/function names, configure_logging level registration and child-process guard and atexit cleanup, LoggerBuilder dictConfig(version=1, disable_existing_loggers=False), LOG_FORMAT_STRING/COLOR_LOG_FORMAT_STRING/LOG_POINTER_STRING, SKELLYLOGS_LOG_DIR env var, DEFAULT_NOISY_PACKAGES, hashed PID/TID colors, CustomFormatter millisecond timestamps, ColoredConsoleHandler stdout stream, WebSocketQueueHandler/LogRecordModel/MIN_LOG_LEVEL_FOR_WEBSOCKET placement, tests layout, shared conftest reset fixture, and pyproject.toml pytest-as-dependency-group-only setup

2026-08-24

SkellyLogs source and README read directly; consumer usage verified in FreeMoCap and SkellyCam clones

More about how these docs are written

# Module map

PathContents

skellylogs/__init__.pyPublic API: configure_logging, LogLevels, LogRecordModel, get_websocket_log_queue, create_websocket_log_queue

configure_logging.pyEntry point; level registration; child-process guard; atexit cleanup

logger_builder.pyLoggerBuilder, attaches/clears root handlers, applies dictConfig(version=1, disable_existing_loggers=False)

log_levels.pyLogLevels enum

log_format_string.pyLOG_FORMAT_STRING, COLOR_LOG_FORMAT_STRING, the └>> pointer

default_paths.pyDefault log directory/filename, SKELLYLOGS_LOG_DIR env var

package_log_quieters.pyDEFAULT_NOISY_PACKAGES map and suppress_noisy_package_logs()

logging_color_helpers.pyHashed-color generation for PIDs/TIDs

log_test_messages.pyDemo emitter covering every level

filters/delta_time.pyDeltaTimeFilter

filters/stringify_traceback.pyStringifyTracebackFilter

formatters/custom_formatter.pyCustomFormatter (base, ms timestamps)

formatters/color_formatter.pyColorFormatter (level/PID/TID/message coloring)

handlers/colored_console.pyColoredConsoleHandler (stdout)

handlers/websocket_log_queue_handler.pyWebSocketQueueHandler, LogRecordModel, queue creation/access, MIN_LOG_LEVEL_FOR_WEBSOCKET

Tests live under tests/ (pytest, no test runner configured in pyproject.toml beyond the test dependency group); a shared fixture resets root-logger state and the queue singleton between tests.
