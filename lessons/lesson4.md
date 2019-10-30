#CRUD http api
Events can be invoked by various event sources.
We want to build http api - let's use default AWS apigateway for that.

```yaml
functions:
  helloWorld:
    handler: helloWorld.handler
    events:
      - http:
          path: hello
          method: get
```

We need to return apigateway compatible response 
```javascript
return {
       statusCode: 200,
       headers: { 'Content-Type': 'text/plain'},
       body: 'Hello World!',
     }
```

Tasks:
* add proper lambda functions for CRUD on articles resource
  * GET articles articles/<id>
  * PUT articles
  * DELETE articles
* return just dummy object or message to make sure our http api is wired properly
* log event provided by apigateway
