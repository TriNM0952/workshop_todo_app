+++
title = "Dọn dẹp tài nguyên  "
date = 2025
weight = 5
chapter = false
pre = "<b>5. </b>"
+++

Chúng ta sẽ tiến hành các bước sau để xóa các tài nguyên chúng ta đã tạo trong bài thực hành này.



### Dọn dẹp tài nguyên AWS với CloudFormation, CLI và Console

#### 1. Xóa Stack CloudFormation

Nếu bạn đã tạo tài nguyên qua CloudFormation, hãy xóa stack để tự động dọn dẹp:

- **Dùng AWS CLI:**

```bash
aws cloudformation delete-stack --stack-name <tên-stack-của-bạn>
```
Ví dụ:
```bash
aws cloudformation delete-stack --stack-name todo-app-stack
```

- **Qua giao diện AWS Console:**
  1. Vào dịch vụ **CloudFormation**.
  2. Chọn Stack của bạn (ví dụ: `todo-app-stack`).
  3. Nhấn **Delete**.

➡️ Việc này sẽ tự động xóa: S3, Lambda, API Gateway, DynamoDB, IAM roles (nếu được định nghĩa trong template).

#### 2. Xóa S3 Bucket (nếu không được xóa bởi stack)
Nếu bucket được tạo thủ công hoặc stack không xóa được bucket vì còn file:

```bash
aws s3 rm s3://<bucket-name> --recursive
aws s3api delete-bucket --bucket <bucket-name>
```

#### 3. Xóa CloudFront Distribution (nếu tạo ngoài stack)
Nếu bạn tạo CloudFront Distribution thủ công:
- Vào AWS Console → **CloudFront** → Chọn Distribution → **Disable**.
- Sau khi disable, chọn **Delete**.

#### 4. Xóa DynamoDB Table (nếu tạo ngoài stack)
```bash
aws dynamodb delete-table --table-name <tên-bảng>
```
Ví dụ:
```bash
aws dynamodb delete-table --table-name Tasks
```

#### 5. Xóa Lambda Functions (nếu tạo ngoài stack)
```bash
aws lambda delete-function --function-name <tên-hàm>
```
Ví dụ:
```bash
aws lambda delete-function --function-name yourFunctionName
```

#### 6. Xóa API Gateway (nếu tạo ngoài stack)
```bash
aws apigateway delete-rest-api --rest-api-id <api-id>
```

#### 7. Xóa IAM Roles/Policies (nếu tạo thủ công)
- Vào AWS Console → **IAM** → Xóa các role/policy không còn dùng.

---

### 🧼 Kiểm tra lại
- Vào **Billing Dashboard** để kiểm tra xem có dịch vụ nào còn tính phí.
- Kiểm tra các vùng (**Region**) khác nếu bạn đã tạo tài nguyên ở nhiều khu vực.

### ✅ Tổng kết
Việc dọn dẹp tài nguyên giúp:
- Tránh bị tính phí không mong muốn.
- Giữ tài khoản AWS sạch sẽ và an toàn.
- Tuân thủ quy trình phát triển theo vòng đời dự án.