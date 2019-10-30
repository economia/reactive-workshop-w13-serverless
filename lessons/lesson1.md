#Project setup
This project is very basic setup for serverless (sls) application.
We will create whole api application in several steps.

Each lesson will present you a new topic with an exercise to practice.

All dependencies are imported via npm - there will be notice when you have to install
some additional dependencies..

First we need to setup our project
`npm i`

We will deploy our project into AWS account eventually, but first, let's
try everything on local machine.

Task:
* Add a new helloWorld.js script which prints "Hello World!"
```javascript
exports.handler = async () => {
  return "Hello World!"
};
```
* register new lambda function serverless.yml
```yaml
functions:
  helloWorld:
    handler: helloWorld.handler
```
* invoke function on your local machine `sls invoke local` (`sls help`)
* Note, that we can use async/await constructs thanks to webpack and babel
