---
title : "Preparation Steps"
date: 2025-07-09
weight : 2
chapter : false
pre : " <b> 2. </b> "
---
## 1. System Requirements

- Python 3.10 or 3.11
- Node.js >= 16
- AWS CLI
- AWS Account with permissions to create Lambda, API Gateway, DynamoDB, S3 services
- Diagram design tool (suggested: draw.io, Lucidchart)
- IDE: Visual Studio Code (or your preferred editor)

## 2. Install Required Tools

### Install AWS CLI

#### macOS
```bash
brew install awscli
sudo apt install awscli
```
#### Windows
Download from AWS CLI
Configure AWS CLI
```bash
aws configure
```
Enter:
Access key, secret key
Region: ap-southeast-1
Format: json
Install Node.js & npm
macOS
```bash
brew install node
```
Ubuntu
```bash
sudo apt install nodejs npm
```
Install Serverless Framework
```bash
npm install -g serverless
```
Create Python virtual environment
```bash
python -m venv .venv
source .venv/bin/activate   # macOS/Linux
.venv\Scripts\activate      # Windows
```
## 3. Create Initial Project Structure
```bash
mkdir todo-serverless
cd todo-serverless
sls create --template aws-python --path .
```
## 4. Install Python Libraries
fastapi  
mangum  
boto3  
pydantic  
pytz  

Install:
```bash
pip install -r requirements.txt
```