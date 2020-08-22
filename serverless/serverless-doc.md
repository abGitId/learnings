

###  Serverless Doc

-----------------------------------



**Configure aws profile in serverless**

```
$ serverless config credentials --provider aws --key <access_key_id> --secret <secret_access_key>
```

**Configure aws profile in serverless with profile option**

```
$ serverless config credentials --provider aws --key <access_key_id> --secret <secret_access_key> --profile default --overwrite
```

**Initializing our Project**

```
$ serverless create --template aws-python3 --name hello-world
```

**Deploy project**

```
serverless deploy -v
```

> **Output:**
> $ serverless deploy -v
> Serverless: Packaging service...
> Serverless: Excluding development dependencies...
> Serverless: Creating Stack...
> Serverless: Checking Stack create progress...
> CloudFormation - CREATE_IN_PROGRESS - AWS::CloudFormation::Stack - hello-world-dev
> CloudFormation - CREATE_IN_PROGRESS - AWS::S3::Bucket - ServerlessDeploymentBucket
> CloudFormation - CREATE_IN_PROGRESS - AWS::S3::Bucket - ServerlessDeploymentBucket
> CloudFormation - CREATE_COMPLETE - AWS::S3::Bucket - ServerlessDeploymentBucket
> CloudFormation - CREATE_IN_PROGRESS - AWS::S3::BucketPolicy - ServerlessDeploymentBucketPolicy
> CloudFormation - CREATE_IN_PROGRESS - AWS::S3::BucketPolicy - ServerlessDeploymentBucketPolicy
> CloudFormation - CREATE_COMPLETE - AWS::S3::BucketPolicy - ServerlessDeploymentBucketPolicy
> CloudFormation - CREATE_COMPLETE - AWS::CloudFormation::Stack - hello-world-dev
> Serverless: Stack create finished...
> Serverless: Uploading CloudFormation file to S3...
> Serverless: Uploading artifacts...
> Serverless: Uploading service hello-world.zip file to S3 (389 B)...
> Serverless: Validating template...
> Serverless: Updating Stack...
> Serverless: Checking Stack update progress...
> CloudFormation - UPDATE_IN_PROGRESS - AWS::CloudFormation::Stack - hello-world-dev
> CloudFormation - CREATE_IN_PROGRESS - AWS::Logs::LogGroup - HelloLogGroup
> CloudFormation - CREATE_IN_PROGRESS - AWS::IAM::Role - IamRoleLambdaExecution
> CloudFormation - CREATE_IN_PROGRESS - AWS::ApiGateway::RestApi - ApiGatewayRestApi
> CloudFormation - CREATE_IN_PROGRESS - AWS::Logs::LogGroup - HelloLogGroup
> CloudFormation - CREATE_IN_PROGRESS - AWS::ApiGateway::RestApi - ApiGatewayRestApi
> CloudFormation - CREATE_IN_PROGRESS - AWS::IAM::Role - IamRoleLambdaExecution
> CloudFormation - CREATE_COMPLETE - AWS::Logs::LogGroup - HelloLogGroup
> CloudFormation - CREATE_COMPLETE - AWS::ApiGateway::RestApi - ApiGatewayRestApi
> CloudFormation - CREATE_IN_PROGRESS - AWS::ApiGateway::Resource - ApiGatewayResourceHello
> CloudFormation - CREATE_IN_PROGRESS - AWS::ApiGateway::Resource - ApiGatewayResourceHello
> CloudFormation - CREATE_COMPLETE - AWS::ApiGateway::Resource - ApiGatewayResourceHello
> CloudFormation - CREATE_COMPLETE - AWS::IAM::Role - IamRoleLambdaExecution
> CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Function - HelloLambdaFunction
> CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Function - HelloLambdaFunction
> CloudFormation - CREATE_COMPLETE - AWS::Lambda::Function - HelloLambdaFunction
> CloudFormation - CREATE_IN_PROGRESS - AWS::ApiGateway::Method - ApiGatewayMethodHelloGet
> CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Permission - HelloLambdaPermissionApiGateway
> CloudFormation - CREATE_IN_PROGRESS - AWS::ApiGateway::Method - ApiGatewayMethodHelloGet
> CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Version - HelloLambdaVersionHk9wTkK6lQ2MmS9qk83aPyKIfvnrQQsCyOwzv54
> CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Permission - HelloLambdaPermissionApiGateway
> CloudFormation - CREATE_IN_PROGRESS - AWS::Lambda::Version - HelloLambdaVersionHk9wTkK6lQ2MmS9qk83aPyKIfvnrQQsCyOwzv54
> CloudFormation - CREATE_COMPLETE - AWS::ApiGateway::Method - ApiGatewayMethodHelloGet
> CloudFormation - CREATE_COMPLETE - AWS::Lambda::Version - HelloLambdaVersionHk9wTkK6lQ2MmS9qk83aPyKIfvnrQQsCyOwzv54
> CloudFormation - CREATE_IN_PROGRESS - AWS::ApiGateway::Deployment - ApiGatewayDeployment1590937596534
> CloudFormation - CREATE_IN_PROGRESS - AWS::ApiGateway::Deployment - ApiGatewayDeployment1590937596534
> CloudFormation - CREATE_COMPLETE - AWS::ApiGateway::Deployment - ApiGatewayDeployment1590937596534
> CloudFormation - CREATE_COMPLETE - AWS::Lambda::Permission - HelloLambdaPermissionApiGateway
> CloudFormation - UPDATE_COMPLETE_CLEANUP_IN_PROGRESS - AWS::CloudFormation::Stack - hello-world-dev
> CloudFormation - UPDATE_COMPLETE - AWS::CloudFormation::Stack - hello-world-dev
> Serverless: Stack update finished...
> Service Information
> service: hello-world
> stage: dev
> region: us-east-1
> stack: hello-world-dev
> resources: 11
> api keys:
>   None
> endpoints:
>   GET - https://xxxxxx.us-east-1.amazonaws.com/dev/hello
> functions:
>   hello: hello-world-dev-hello
> layers:
>   None
>
> Stack Outputs
> HelloLambdaFunctionQualifiedArn: arn:aws:lambda:us-east-1:xxxx:function:hello-world-dev-hello:1
> ServiceEndpoint: https://xxxxx.us-east-1.amazonaws.com/dev
> ServerlessDeploymentBucketName: hello-world-dev-serverlessdeploymentbucket-rfh2l1yieco1
>
> Serverless: Run the "serverless" command to setup monitoring, troubleshooting and testing.



**Remove deployed serverless project**

```
$ serverless remove
```



#### Invoke

--------------------------------

**Invoke Locally**

```
$ serverless invoke local --function <funcation-name>
```

**Invoke Locally with data**

```
$ serverless invoke local --function <funcation-name> --data '{"key":"val"}'
```

---------------------------------------

**References used**

> Ref url: https://www.serverless.com/framework/docs/providers/aws/cli-reference/invoke-local/

> https://medium.com/faun/aws-lambda-serverless-framework-python-part-1-a-step-by-step-hello-world-4182202aba4a
