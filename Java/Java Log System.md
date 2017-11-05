# Java Log System

Example using Global Logger:
```java
LogManager logManager = LogManager.getLogManager();

Logger logger = logManager.getLogger(Logger.GLOBAL_LOGGER_NAME);

logger.log(Level.FINE, "This log entry so fine.");
```

or for simpler use
```java
static Logger logger = LogManager.getLogManager().getLogger(Logger.GLOBAL_LOGGER_NAME);
```

## LogManager
- Managed as a Singleton object per app
- Manages objects that do the actual logging

## Logger
- Does the actual logging
- Global logger available - access using the `Logger.GLOBAL_LOGGER_NAME`

## Logging Levels
- 7 Levels
  - Severe
  - Warning
  - Config
  - Info
  - Fine
  - Finer
  - Finest
- Call `setLevel(Level logLevel);` on a Logger instance to set the logging level - all loggings below the setLevel will not be registered
  - `Level.ALL` and `Level.OFF` available for setting logLevel


## Types of Log Methods
- Level Convenience methods:
```java
logger.severe("This will be logged as severe.");
logger.warning("This will be logged at the warning level.");
// and so on..
```
- Precise Log - Standard log gets the calling info wrong sometimes.. therefore:
```java
logger.logp(Level level, String className, String methodName, String message);
```

- Entering and Exiting
Logged at **Level.FINER** level. The messages will be **ENTRY** and **RETURN** respectively.

```java
logger.entering(String className, String methodName);
logger.exiting(String className, String methodName);
```

TODO: More log methods