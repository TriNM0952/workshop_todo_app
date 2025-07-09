+++
title = "Clean up resources"
date = 2025
weight = 5
chapter = false
pre = "<b>5. </b>"
+++

### Clean up AWS resources with CloudFormation, CLI, and Console

#### 1. Delete CloudFormation Stack

If you created resources using CloudFormation, delete the stack to automatically clean up:

- **Using AWS CLI:**

```bash
aws cloudformation delete-stack --stack-name <your-stack-name>
```
Example:
```bash
aws cloudformation delete-stack --stack-name todo-app-stack
```

- **Using AWS Console:**
  1. Go to the **CloudFormation** service.
  2. Select your stack (e.g., `todo-app-stack`).
  3. Click **Delete**.

➡️ This will automatically delete: S3, Lambda, API Gateway, DynamoDB, IAM roles (if defined in the template).

#### 2. Delete S3 Bucket (if not deleted by stack)
If the bucket was created manually or the stack cannot delete the bucket because it still contains files:

```bash
aws s3 rm s3://<bucket-name> --recursive
aws s3api delete-bucket --bucket <bucket-name>
```

#### 3. Delete CloudFront Distribution (if created outside the stack)
If you created the CloudFront Distribution manually:
- Go to AWS Console → **CloudFront** → Select Distribution → **Disable**.
- After disabling, select **Delete**.

#### 4. Delete DynamoDB Table (if created outside the stack)
```bash
aws dynamodb delete-table --table-name <table-name>
```
Example:
```bash
aws dynamodb delete-table --table-name Tasks
```

#### 5. Delete Lambda Functions (if created outside the stack)
```bash
aws lambda delete-function --function-name <function-name>
```
Example:
```bash
aws lambda delete-function --function-name yourFunctionName
```

#### 6. Delete API Gateway (if created outside the stack)
```bash
aws apigateway delete-rest-api --rest-api-id <api-id>
```

#### 7. Delete IAM Roles/Policies (if created manually)
- Go to AWS Console → **IAM** → Delete any unused roles/policies.

---

### 🧼 Double-check
- Go to the **Billing Dashboard** to check if there are any services still incurring charges.
- Check other **Regions** if you have created resources in multiple regions.

### ✅ Summary
Cleaning up resources helps:
- Avoid unwanted charges.
- Keep your AWS account clean and secure.
- Follow the project lifecycle process.