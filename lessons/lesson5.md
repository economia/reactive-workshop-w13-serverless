#Persistent storage

Eventually we do want to build a persistent storage for our api.
This isn't something sls can no natively - we will use aws cloudformation instead.
IMPORTANT - use --stage param from now on!
```yaml
Resources:
  StatusTable:
    Type: AWS::DynamoDB::Table
    Properties:
      TableName: ${self:custom.articlesTableName}
      AttributeDefinitions:
        - AttributeName: id
          AttributeType: S
        - AttributeName: publishDate
          AttributeType: N
      BillingMode: PAY_PER_REQUEST
      KeySchema:
        - AttributeName: id
          KeyType: HASH
        - AttributeName: publishDate
          KeyType: RANGE
```
Notice the variable in TableName - in sls we can define variables for more managable referencing.
In this example sls will expect `articlesTableName` in `custom` root node in serverless.yml
Tasks:
* add articlesTableName  with ${stage} suffix
* create your own DynamoDB
* explore Dynamo in aws console (try inserting an item)
