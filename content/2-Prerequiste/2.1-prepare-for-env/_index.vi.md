---
title : "Chuẩn bị môi trường phát triển Server"
date: 2025-07-09 
weight : 1
chapter : false
pre : " <b> 2.1. </b> "
---
Trong bước này, chúng ta sẽ chuẩn bị môi trường để phát triển và triển khai ứng dụng web To-Do List theo kiến trúc serverless trên AWS. Bao gồm việc cài đặt công cụ, tạo cấu trúc dự án, và viết mã nguồn ban đầu.

## 🗂 Tổng quan kiến trúc

Sau khi hoàn tất bước này, hệ thống sẽ được thiết kế theo kiến trúc serverless, bao gồm các thành phần chính như Lambda, API Gateway, và DynamoDB.
-  Sơ đồ kiến trúc hệ thống
![Build](/images/2.Build/diagram.png)


---

## 📦 Nội dung chuẩn bị

### 1. Cài đặt công cụ cần thiết
- AWS CLI
- Node.js & npm
- Serverless Framework
- Python và các thư viện cần thiết

### 2. Tạo cấu trúc dự án với Serverless Framework
- Tạo file serverless.yalm
- Cấu hình Serverless Framework
- Tạo các file mã nguồn ban đầu
- Tạo file serverless.yalm để cấu hình các tài nguyên cần thiết
### 3. Viết mã nguồn cấp quyền cho Lambda truy cập bảng DynamoDB TodosTable để thực hiện các thao tác CRUD
- Cấu hình IAM:
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
Thay ```your-aws-id``` bằng Id tài khoản AWS của bạn
{{% /notice %}}

### 4. Viết mã nguồn Lambda và cấu hình API
- Định nghĩa cho các Lambda function bằng Python
- Cấu hình API Gateway để kết nối với Lambda
- Cấu hình bảo vệ API bằng API Key:
```bash
  apiGateway:
    apiKeySourceType: HEADER
    apiKeys:
      - name: TodoApiKey-${sls:stage}
        description: "API Key cho Todo App"
        enabled: true
    usagePlan:
      throttle:
        rateLimit: 100
        burstLimit: 50
      quota:
        limit: 1000
        period: MONTH
```
### 5. Cấu hình DynamoDB
- Tạo bảng DynamoDB để lưu trữ dữ liệu ứng dụng
- Tạo DynamoDB bảng TodosTable với khóa chính là id (kiểu chuỗi), dùng chế độ thanh toán theo lượt truy vấn (PAY_PER_REQUEST).
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
- Kết quả:
![Build](/images/2.Build/01-Build-BE.png)
### 6. Cấu hình API KEY trên AWS Console
- Truy cập vào  _AWS Management Console_.
- Tìm _API Gateway_ từ giao diện hoặc thanh tìm kiếm
- Truy cập _API Gateway_ 
![Build](/images/2.Build/02-Build-BE.png)
-Tại giao diện, chọn vào _APIs_ mà bạn đã tạo từ back end
![Build](/images/2.Build/03-Build-BE.png)
- Tiếp tục chọn _API key_
![Build](/images/2.Build/04-Build-BE.png)
- Tại giao diện _API key_ chọn _Create API key_
![Build](/images/2.Build/05-Build-BE.png)
- Tại giao diện tạo API key, điền _Name_ và _Decription_ cho _API key_ của bạn
- Sau đó chọn _Save_
![Build](/images/2.Build/06-Build-BE.png)
- Kết quả: 
![Build](/images/2.Build/07-Build-BE.png)
### 7. Triển khai lên AWS
- Sử dụng CloudFormation hoặc Serverless CLI để triển khai toàn bộ hệ thống
```bash
serverless deploy
```
- Sau khi bạn deploy dự án, trong command prompt trong back end của bạn sẽ nhận được đường dẫn đến server và api key.
- Đường dần và API key trả về có dạng:  
  functions:
  api: todo-serverless-dev-api  
  api keys:
  TodoApiKey-dev: IZxMUcA7Vq4YoIsZGB1tp9Tgve86hc1CNlo15fj9
- Bạn cần sử dụng đường dẫn và API key để gửi các yêu cầu về server
---

## 🔗 Tài liệu tham khảo

- [Giới thiệu về Lambda](https://000022.awsstudygroup.com/)
- [Giới thiệu về API Gateway](https://000135.awsstudygroup.com/)
- [Giới thiệu về DynamoDB](https://000039.awsstudygroup.com/)
- [Giới thiệu về CloudFront](https://000137.awsstudygroup.com/)
- [Giới thiệu về CloudFormation](https://000037.awsstudygroup.com/vi/)
- [Giới thiệu về S3](https://000057.awsstudygroup.com/vi/)
- Hoặc bạn có thể tham khảo dự án thêm tại Github (https://github.com/TriNM0952/Workshop.git)
---

Sau khi hoàn tất bước này, bạn đã có sẵn hệ thống backend serverless với Lambda, API Gateway và DynamoDB để tiếp tục xây dựng giao diện và hoàn thiện ứng dụng.