# Logging

BasicConfig [list of options](https://docs.python.org/3/library/logging.html#logging.basicConfig)

logging [attributes](https://docs.python.org/3/library/logging.html#logrecord-attributes)

[setLoggerClass](https://docs.python.org/3/library/logging.html#logging.setLoggerClass) can be used to swap in a
new logging class for use in all modules.

Loggers are in a hierarchy, defined by dot separated names.  

 * `foo` is the parent of `foo.bar`
 * `foo.bar` is the parent of `foo.bar.baz`

Using `__name__` names loggers in the same hierarchy as the module.  This is a good default.

Each logger is created with level `NOTSET`, except for the root logger which
is `WARN`.  Loggers who's level is not set delegated to the first parent up the chain that has a level set.  

the default python logging format is:

    %(levelname)s:%(name)s:%(message)s

# File Configuration

See [logging.config](https://docs.python.org/3/library/logging.config.html#logging-config-fileformat)

There are may gotch-ya

 * `root` must be in the logger list
 * `root_logger` must have a `handlers` key

Further, the resulting file is overly complex.  

# Dictionary Configuration

See [logging.dictConfig](https://docs.python.org/3/library/logging.config.html#logging.config.dictConfig) and [schema](https://docs.python.org/3/library/logging.config.html#logging-config-dictschema].

Dictionaries could be loaded directly from YAML or JSON files.

    version: 1
    disable_existing_loggers: false

set `disable_existing_loggers` to `true` to disable all loggers
not explicitly configured in the dictionary.  Set to `false` to
retain existing loggers.  

    formatters:
      formatConsole:
        format: '%(levelname)s:%(name)s:%(message)s'
      formatFile:
        format: '%(asctime)s:%(threadName)s:%(name)s:%(levelname)s:  %(message)s'

    handlers:
      consoleHandler:
        class: logging.StreamHandler
        level: INFO
        formatter: formatConsole
        stream: ext://sys.stdout
      fileHandler:
        class : logging.FileHandler
        level: DEBUG
        formatter: formatFile
        mode: 'w'
        filename: logging/local-log.txt

`mode` `w` will overwrite the file, `a` will append to the file.


    loggers:

      root:
        level: WARN
        handlers: [consoleHandler, fileHandler]
      mod_two: 
        level: DEBUG

# Level

Level is determined by

 * Logger:  
   * The current logger
   * Parent loggers (by name and the root)
 * Handlers
   * Handlers only handle their set or higher.

(Note:  `WARN` is higher than `INFO`)


# Logging exceptions

Capture stack trace with `exc_info=True`:

    logger.error("Error message", exc_info=True)    

Or, call `logger.exception`:

    logger.exception("Error message")

which loggs as `ERROR` and includes the stack trace.

# Logging to elasticsearch

For regular logging

    formatters:
      # Create a formatter based on the ecs_logger std lib formatter
      ecsFmt:
        class:  ecs_logging.StdlibFormatter

    handlers:
      # Create a handler that uses the elastic search formatter
      ecsHnd:
        class : logging.FileHandler
        level: DEBUG
        formatter: ecsFmt
        mode: 'w'
        filename: logging/local-log.json

Alternately, log directly to elastic search using [python-elasticsearch-ecs-logger](https://github.com/iminterne/python-elasticsearch-ecs-logger)
