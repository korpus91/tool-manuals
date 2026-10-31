# How it works | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

SkellyLogs source re-checked line-by-line (configure_logging.py, logger_builder.py, log_levels.py, package_log_quieters.py, handlers/, filters/, formatters/, log_format_string.py)

2026-08-24

SkellyLogs source and README read directly; consumer usage verified in FreeMoCap and SkellyCam clones

More about how these docs are written

# How it works

configure_logging() is the single entry point. In order, it:

- Applies the package-suppression map (suppress_noisy_package_logs) so chatty third-party loggers (matplotlib, httpx, uvicorn, asyncio, and more) are quieted to sane levels. Defaults come from DEFAULT_NOISY_PACKAGES; pass your own dict or {} to change this.

- Registers four custom levels and their logger.<name>() methods on logging.Logger.

- Resolves the websocket queue (auto-created in the main process; see below).

- Delegates to LoggerBuilder, which wipes any pre-existing root-logger handlers ("last writer wins") and attaches the full handler set.

The resulting root logger looks like this:

ComponentClassLevelPurpose

FilterStringifyTracebackFiltern/aFormats live exc_info tracebacks to strings before any handler sees the record, then clears exc_info, traceback objects can't be deep-copied or pickled, which would break the color formatter's record copy and the queue transport

HandlerColoredConsoleHandlerconfigured levelANSI-colored stdout output; per-level colors plus hash-stable PID/TID colors

Handlerlogging.FileHandleralways TRACEPlain-text log file using LOG_FORMAT_STRING

HandlerWebSocketQueueHandlerconfigured levelSerializes each record into a LogRecordModel dict and put_nowait()s it onto the queue

FilterDeltaTimeFilter (on all three handlers)n/aAdds record.delta_t, milliseconds since that handler's previous record, useful for spotting slow sections

Each handler owns its own DeltaTimeFilter instance, so the three outputs track deltas independently per destination.
