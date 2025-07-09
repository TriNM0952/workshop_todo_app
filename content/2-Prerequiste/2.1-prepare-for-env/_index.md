---
title : "Prepare Server Development Environment"
date: 2025-07-09
weight : 1
chapter : false
pre : " <b> 2.1. </b> "
---
In this step, we will prepare the environment to develop and deploy the To-Do List web application using a serverless architecture on AWS. This includes installing tools, creating the project structure, and writing the initial source code.

## 🗂 Architecture Overview

After completing this step, the system will be designed with a serverless architecture, including main components such as Lambda, API Gateway, and DynamoDB.
- System Architecture Diagram
![Build](/images/2.Build/aws-architecture-drawio.drawio.png)
---

## 📦 Preparation Content

### 1. Install required tools
- AWS CLI
- Node.js & npm
- Serverless Framework
- Python and necessary libraries

### 2. Create project structure with Serverless Framework
- Create `serverless.yaml` file
- Configure Serverless Framework
- Create initial source code files
- Create `serverless.yaml` to configure required resources

### 3. Write code to grant Lambda permission to access the DynamoDB TodosTable for CRUD operations
- IAM configuration:
```bash
  iam:
    role:
      statements:
        - Effect: Allow
          Action:
            - dynamodb:PutItem
            - dynamodb:GetItem
            - dynamodb:UpdateItem
            - dynamodb:DeleteItem
            - dynamodb:Scan
            - dynamodb:Query
          Resource:
            - arn:aws:dynamodb:ap-southeast-1:your-aws-id:table/TodosTable
```

{{% notice warning %}}
Replace `your-aws-id` with your AWS account ID
{{% /notice %}}

### 4. Write Lambda source code and configure API
- Define Lambda functions in Python
- Configure API Gateway to connect with Lambda
- Configure API protection with API Key:
```bash
  apiGateway:
    apiKeySourceType: HEADER
    apiKeys:
      - name: TodoApiKey-${sls:stage}
        description: "API Key for Todo App"
        enabled: true
    usagePlan:
      throttle:
        rateLimit: 100
        burstLimit: 50
      quota:
        limit: 1000
        period: MONTH
```
### 5. Configure DynamoDB
- Create a DynamoDB table to store application data
- Create a DynamoDB table `TodosTable` with primary key `id` (string type), using PAY_PER_REQUEST billing mode.
```bash
resources:
  Resources:
    TodosTable:
      Type: AWS::DynamoDB::Table
      Properties:
        TableName: TodosTable
        AttributeDefinitions:
          - AttributeName: id
            AttributeType: S
        KeySchema:
          - AttributeName: id
            KeyType: HASH
        BillingMode: PAY_PER_REQUEST
```
- Result:
![Build](/images/2.Build/01-Build-BE.png)
### 6. Configure API KEY on AWS Console
- Go to _AWS Management Console_.
- Search for _API Gateway_ from the interface or search bar
- Access _API Gateway_
![Build](/images/2.Build/02-Build-BE.png)
- In the interface, select the _APIs_ you created from the backend
![Build](/images/2.Build/03-Build-BE.png)
- Continue to select _API key_
![Build](/images/2.Build/04-Build-BE.png)
- In the _API key_ interface, select _Create API key_
![Build](/images/2.Build/05-Build-BE.png)
- In the API key creation interface, enter _Name_ and _Description_ for your _API key_
- Then select _Save_
![Build](/images/2.Build/06-Build-BE.png)
- Result:
![Build](/images/2.Build/07-Build-BE.png)
### 7. Deploy to AWS
- Use CloudFormation or Serverless CLI to deploy the entire system
```bash
serverless deploy
```
- After you deploy the project, in the command prompt in your backend you will receive the server endpoint and API key.
- The returned endpoint and API key will look like:
  functions:
  api: todo-serverless-dev-api  
  api keys:
  TodoApiKey-dev: IZxMUcA7Vq4YoIsZGB1tp9Tgve86hc1CNlo15fj9
- You need to use the endpoint and API key to send requests to the server
---

## 🔗 References

- [Introduction to Lambda](https://000022.awsstudygroup.com/)
- [Introduction to API Gateway](https://000135.awsstudygroup.com/)
- [Introduction to DynamoDB](https://000039.awsstudygroup.com/)
- [Introduction to CloudFront](https://000137.awsstudygroup.com/)
- [Introduction to CloudFormation](https://000037.awsstudygroup.com/vi/)
- [Introduction to S3](https://000057.awsstudygroup.com/vi/)
- You can also refer to the project on Github (https://github.com/TriNM0952/Workshop.git)
---

After completing this step, you will have a ready serverless backend system with Lambda, API Gateway, and DynamoDB to continue building the frontend and complete the application.