#Deploy and run
We can run our code locally, but the point is to run it in scalable aws infrastructure.

You need an aws account - we have one prepared for you, for the purpose of this workshop.
But you can create your own - everything we will create should stay in free tier (aws terminology for free demo).

Url for aws console login: https://103221641077.signin.aws.amazon.com/console/
Login: firstName.LastName
Password: VacuumLabs

We have just a single account for all of you to share - we have to deal with the fact,
that many aws resources require unique names.
To minimise conflicts between our projects, we will use sls "stages".

Task:
* get your aws access keys (https://console.aws.amazon.com/iam/home#/users)
* configure sls project to use these access keys
* deploy project with specified stage `sls deploy --stage ${stagename}`
* invoke remote labda `sls invoke` (explore help page and search for required parameters --stage and -f)
* check your project in aws console
* add console.log with custom message to your lambda code
* browse through logs `sls logs` or cloudwatch console
