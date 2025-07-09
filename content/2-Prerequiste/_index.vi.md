---
title : "Các bước chuẩn bị"
date: 2025-07-09 
weight : 2 
chapter : false
pre : " <b> 2. </b> "
---
## 1. Yêu cầu hệ thống

- Python 3.10 hoặc 3.11
- Node.js >= 16
- AWS CLI
- AWS Account với quyền tạo dịch vụ Lambda, API Gateway, DynamoDB, S3
- Công cụ thiết kế sơ đồ (gợi ý: draw.io, Lucidchart)
- IDE: Visual Studio Code (hoặc editor bạn thích)

## 2. Cài đặt công cụ cần thiết

### Cài AWS CLI

#### macOS
```bash
brew install awscli
sudo apt install awscli
```
#### Windows
Tải từ AWS CLI
Cấu hình AWS CLI
```bash
aws configure
```
Nhập:
Access key, secret key
Region: ap-southeast-1
Format: json
Cài Node.js & npm
macOS
```bash
brew install node
```
Ubuntu
```bash
sudo apt install nodejs npm
```
Cài Serverless Framework
```bash
npm install -g serverless
```
Tạo virtual environment Python
```bash
python -m venv .venv
source .venv/bin/activate   # macOS/Linux
.venv\Scripts\activate      # Windows
```
## 3. Tạo cấu trúc dự án ban đầu
```bash
mkdir todo-serverless
cd todo-serverless
sls create --template aws-python --path .
```
## 4. Cài đặt thư viện Pythonfastapi
mangum  
boto3  
pydantic  
pytz  

Cài đặt:  
```bash
pip install -r requirements.txt
```