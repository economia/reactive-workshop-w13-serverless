#Alarm notifications
We want to be notified of any errors on production
environment

AWS provides default mechanism for monitoring and alerting.
In sls there is a plugin for this `serverless-plugin-aws-alerts`.
We need to specify Topics, Definitions and provide them as alarms to uor functions.
```yaml
topics:
      ok:
        topic: ${self:service}-${self:custom.stage}-alerts-ok
        notifications:
          - protocol: email
            endpoint: your email
      alarm: ${self:service}-${self:custom.stage}-alerts-alarm
        notifications:
          - protocol: email
            endpoint: jan.stepanek@economia.cz
```
```yaml
definitions:
      criticalFunctionErrors:
        namespace: 'AWS/Lambda'
        metric: Errors
        threshold: 10
        statistic: Sum
        period: 60
        evaluationPeriods: 10
        comparisonOperator: GreaterThanOrEqualToThreshold
```
```yaml
articlesCreate:
    handler: create.handler
    events:
      - http:
          path: articles
          method: post
    iamRoleStatements:
      - Effect: Allow
        Action:
          - dynamodb:PutItem
        Resource: arn:aws:dynamodb:${self:provider.region}:*:table/${self:custom.articlesTableName}
    alarms:
      - criticalFunctionErrors
```
Tasks:
* add alarms to our lambdas - you can even create a dedicated error lambda to trigger 
an error for alarms debugging
* explore alarms in aws console
