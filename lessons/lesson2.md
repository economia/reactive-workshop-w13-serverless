#Deploy and run
We can run our code locally, but the point is to run it in scalable aws infrastructure.

You need an aws account - we have one prepared for you, for the purpose of this workshop.
But you can create your own - everything we will create should stay in free tier (aws terminology for free demo).

We have one account for 10 people to share - many aws resources require unique names.
To minimise conflicts between our projects, we will use sls "stages".

Task:
* get your aws access keys
* configure sls project to use these access keys
* deploy project with specified stage `sls deploy --stage ${stagename}`
* invoke remote labda `sls invoke`
* check your project in aws console
* add console.log with custom message to your labda code
* browse through logs `sls logs` or cloudwatch console
