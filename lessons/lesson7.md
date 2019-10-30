#Connect lambda to Dynamo

DynamoDb has its own client implementation in node.js (and other languages..)
```javascript
import { DynamoDB } from 'aws-sdk';
const params = {
    TableName: 'TABLENAME',
    Item: {
      id: '...',
      publishDate: '...',
      title: '...',
      content: '...'
    },
  };
await dynamoDb.put(params)
       .promise()
```
Tasks:
* try to insert item to dynamo from your lambda
* add proper try catch statement to handle errors
* add permissions for lambda to access dynamo
```yaml
iamRoleStatements:
      - Effect: Allow
        Action:
          - dynamodb:PutItem
        Resource: arn:aws:dynamodb:${self:provider.region}:*:table/${self:custom.articlesTableName}
```
