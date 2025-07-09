---
title : "Giới Thiệu Về CloudFormation"
date: 2025-05-25 
weight : 4 
chapter : false
pre : " <b> 4. </b> "
---


**Amazon CloudWatch** là dịch vụ giám sát tập trung của AWS, cung cấp khả năng thu thập log, số liệu (metrics) và tạo cảnh báo (alarms) cho toàn bộ hạ tầng.

Trong hệ thống của bạn, CloudWatch có thể được sử dụng để:
- Ghi lại log của **Lambda function** thông qua `console.log()`
- Theo dõi số lượng request, lỗi 4xx/5xx của **API Gateway**
- Giám sát lượng truy cập đến **CloudFront** và **S3**

Bạn có thể:
- Truy cập **CloudWatch Logs** để kiểm tra log theo thời gian thực từ Lambda
- Tạo **Alarm** để gửi cảnh báo qua email (SNS) nếu có lỗi tăng bất thường
- Kết hợp **CloudWatch Dashboard** để trực quan hóa toàn bộ hệ thống
