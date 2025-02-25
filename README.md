﻿
# AWS-Node-http-ToDo-API

  This is a ToDo app API built with node.js and can be deployed using serverless framework. The serverless framework will store the code in S3 bucket and then it will be transfered to Lambda for execution, then a API gateway and will be attached to the Lambda function and  along with that DynamoDB will be provisioned with required table. Everything will be done with appropriate IAM roles and logging will be done by CloudWatch. Serveless framework uses CloudFormation for provision and deployment of the resources.
  
  

## Usage
Add task - 
  ``` 
POST - https://xxxxx.execute-api.us-east-1.amazonaws.com/InsertTask
```
Data in body should be like:
```
{
        "kaam": "Go for a morning walk"
}
```

Update status of completion -
```
PUT - https://xxxxx.execute-api.us-east-1.amazonaws.com/updateSTS/{id}
```
Data in body should be like:
```
# You can also keep the value as false
{ 
"completed": true
}
```

### Deployment

  First make changes in `serverless.yml` change the organization name to your **username** of serverless.com and **Account ID** of AWS in the resources section. You can also change region as per your choice.

```
$ npm install
$ serverless deploy
```

  

After deploying, you should see output similar to:

  

```bash

Deploying "project-name" to stage "dev" (us-east-1)

✔ Service deployed to stack aws-node-http-api-project-dev (44s)

endpoints:
  GET - https://xxxxx.execute-api.us-east-1.amazonaws.com/
  POST - https://xxxxx.execute-api.us-east-1.amazonaws.com/InsertTask
  GET - https://xxxxx.execute-api.us-east-1.amazonaws.com/show
  PUT - https://xxxxx.execute-api.us-east-1.amazonaws.com/updateSTS/{id}
  POST - https://xxxxx.execute-api.us-east-1.amazonaws.com/TaskDel/{id}
functions:
  hello: aws-node-http-api-project-dev-hello (14 MB)
  kaamBharo: aws-node-http-api-project-dev-kaamBharo (14 MB)
  kaamDikhao: aws-node-http-api-project-dev-kaamDikhao (14 MB)
  kaamKhatamKaro: aws-node-http-api-project-dev-kaamKhatamKaro (14 MB)
  kaamHatao: aws-node-http-api-project-dev-kaamHatao (14 MB)


```

  

_Note_: In current form, after deployment, your API is public and can be invoked by anyone. For production deployments, you might want to configure an authorizer. For details on how to do that, refer to [http event docs](https://www.serverless.com/framework/docs/providers/aws/events/apigateway/).

  

### Invocation

  

After successful deployment, you can call the created application via HTTP:

  

```bash

curl https://xxxxxxx.execute-api.us-east-1.amazonaws.com/

```
