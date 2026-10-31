# Custom log levels | FreeMoCap

Skip to main content

AI-generated documentationchecked against source

This page was drafted by an AI assistant from source material and may contain inaccuracies. If you spot something wrong, please open an issue or use the Edit this page link below to submit a fix.

2026-08-26

skellylogs/log_levels.py (LogLevels enum) read directly, every value in the table (LOOP 3, TRACE 5, DEBUG 10, INFO 20, SUCCESS 22, API 25, WARNING 30, ERROR 40) confirmed exact; log_test_messages.py confirmed to exist

2026-08-24

SkellyLogs source and README read directly; consumer usage verified in FreeMoCap and SkellyCam clones

More about how these docs are written

# Custom log levels

Defined in log_levels.py as the LogLevels enum and registered globally by configure_logging():

MethodValueUse case (from source comments)

logger.loop()3Logs inside hot loops; debugging only

logger.trace()5Low-level tracing for deep debugging

logger.debug()10Detailed information for devs

logger.info()20General program information

logger.success()22Something worked

logger.api()25API call/response logging

logger.warning()30Unexpected but not necessarily an error

logger.error()40Something went wrong

There is no CRITICAL entry in the enum. The ALL member maps to NOTSET (0) for third-party library noise.

A log_test_messages(logger) helper in log_test_messages.py emits one message at every level plus timed loop/trace pairs, for eyeballing the formatter output.
