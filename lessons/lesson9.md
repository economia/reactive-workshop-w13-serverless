#Other event sources
ApiGateway is not the only source of events for lambdas.
You can create everything a normal monolith application can do.
https://docs.aws.amazon.com/lambda/latest/dg/lambda-services.html

We can try one more event source - cron
```yaml
events:
      - schedule: rate(5 minutes)
```

Task:
* Create a scheduled task to run every 5 minutes
