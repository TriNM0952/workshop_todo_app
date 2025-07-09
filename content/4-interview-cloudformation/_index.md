---
title : "Introduction to CloudFormation"
date: 2025-05-25 
weight : 4 
chapter : false
pre : " <b> 4. </b> "
---

**Amazon CloudWatch** is AWS's centralized monitoring service, providing the ability to collect logs, metrics, and create alarms for your entire infrastructure.

In your system, CloudWatch can be used to:
- Record logs from **Lambda functions** via `console.log()`
- Monitor the number of requests, 4xx/5xx errors from **API Gateway**
- Monitor traffic to **CloudFront** and **S3**

You can:
- Access **CloudWatch Logs** to check real-time logs from Lambda
- Create **Alarms** to send notifications via email (SNS) if there is an abnormal increase in errors
- Combine **CloudWatch Dashboard** to visualize the entire system