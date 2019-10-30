#Wiring resources with lambda in sls

In the previous example we successfully connected lambda to database.
There are some issues though - hardcoded table name for one.
We can use Resource names in serverless.yml to reference those
in lambda function configuration. Let's add env variable with
dynamo table name.
```yaml
functions:
  myFn:
  ...
  environment:
    ARTICLESTABLE: ${self:custom.articlesTableName}
```
We can read it in javascript from `process.env`.
Trouble is, there will be more than one config value usually (a lot more).
It isn't convenient to pass all of them as env variables.
We can use `config` library to help us out.

Tasks:
* create `config/default.json` with some config values
* install `config` package
* add reading of config value to our lambda
* generate config env override using `cev` command in `config-cev-generator` package.
You can add following script to package.json: `"cev": "cev --prefix reactive > config/custom-environment-variables.json"`
