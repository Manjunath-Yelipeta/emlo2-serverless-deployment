# emlo2-serverless-deployment
# 1. Deploy CIFAR10 Model on AWS Lambda and share link to your Lambda

endpoint created: POST - https://pjdexo4gq5.execute-api.us-west-2.amazonaws.com/dev/inference

functions:  cifar: serverless-cifar-dev-cifar

ARN:  arn:aws:lambda:us-west-2:884880583184:function:serverless-cifar-dev-cifar

## 1.1. - Install the packages

```
curl -sL https://deb.nodesource.com/setup_16.x | sudo -E bash -
sudo apt install nodejs
sudo npm i -g serverless
```

## 1.2. - Get the Code for serverless from this folder.
## 1.3. - Create the docker and push the image to ECR on a private repository.

    My ECR Repository [URI:](884880583184.dkr.ecr.us-west-2.amazonaws.com/cifar-serverless-handson:latest) 

## 1.4. - Add permissions to IAM Role

![](data_serverless/IAM.png)

## 1.5. Run the command to deploy your code
```
serverless deploy
```


## 1.6. Some Errors Faced:
```
CREATE_FAILED: IamRoleLambdaExecution (AWS::IAM::Role)
API: iam:CreateRole User: arn:aws:sts::258326714772:assumed-role/TestSession5EC2S3Access/i-0a6509e740e929efd is not authorized to perform: iam:CreateRole on resource: arn:aws:iam::258326714772:role/serverless-cifar-dev-ap-south-1-lambdaRole because no identity-based policy allows the iam:CreateRole action
```
 Added IAMFullAccess to the EC2 IAM role.

```
CREATE_FAILED: CifarLambdaFunction (AWS::Lambda::Function)
Resource handler returned message: "'MemorySize' value failed to satisfy constraint: Member must have value less than or equal to 3008 (Service: Lambda, Status Code: 400, Request ID: f23c4c31-8577-41ed-b402-c11a355cf8c1)" (RequestToken: 45626d5b-a0af-54bb-22e5-89a1b08f1142, HandlerErrorCode: InvalidRequest)
```



# 2. Deploy Frontend on Vercel and share link to your deployment

Frontend code repository: https://github.com/Manjunath-Yelipeta/emlov2-session9-serverless-frontend

Deployment URL: https://emlov2-session9-serverless-frontend-iguzp2d87-yelipetamanjunath.vercel.app/

<br>

<br>

## Useful Tips
1. Check the memory of your instance
```
grep MemTotal /proc/meminfo
```
2. curl command to test serverless deployement [curl](cmd.txt)
