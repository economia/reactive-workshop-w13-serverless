#debug
For additional insight to our program, it is important to learn how to
properly handle logging.

In AWS all lambdas run in parallel, and logs are aggregated in a single stream.
Usually we need to pair all log messages from a single lambda invocation.

The idea is to add some unique identificator to all our log messages per lambda execution.
We don't have to invent our own identificator - aws provides one for us `context.awsRequestId`.

Tasks:
* print `context` and `event` in your console.log statement
* try filtering for specific awsRequestId `sls logs --filter`

Other interesting challenge is to provide id to all log calls - even those buried
deep down in modules and services you might be using..
Passing context to all methods and classes is very uncomfortable, so what we try instead
is to use a proper logging library. We use pino, which amongst other things, provides a mechanism
to bind logged data to instance of logger (method child). In other words in we pass any data into child method,
these data will be serialized to each following log message.

Tasks:
* install pino package
* create logger with bound context to it
`const logger = pino().child({context})`
* use our new logger instead of console.log calls - notice how context
appears in all messages `logger.info('my log message')`
* filter out all messages with given awsRequestId `sls logs --filter "{$.context.awsRequestId = xxx}"`
