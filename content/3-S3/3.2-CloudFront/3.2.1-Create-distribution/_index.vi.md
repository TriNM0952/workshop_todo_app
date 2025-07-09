---
title : "Tạo CloudFront Distribution"
date: 2025-07-09 
weight : 1 
chapter : false
pre : " <b> 3.2.1 </b> "
---
## Tạo CloudFront Distribution và cấu hình _Distribution
1. Tạo CloudFront Distribution
- Truy cập vào _AWS Console_
- Tìm _CloudFront_ trên giao diện hoặc thanh tìm kiếm 
- Chọn _CloudFront_
![CloudFront](/images/3.CloudFront/01-CloudFront.png)
2. Trong giao diện _CloudFront_, chọn _Create distribution_
![CloudFront](/images/3.CloudFront/02-CloudFront.png)
-  Trong giao diện _Create distribution_
- _Distribution name_: nhập ```todo-web-frontend-ws```
- Sau đó chọn _Next_
![CloudFront](/images/3.CloudFront/03-CloudFront.png)
![CloudFront](/images/3.CloudFront/04-CloudFront.png)
- Ở bước này, chọn _Other_ 
![CloudFront](/images/3.CloudFront/05-CloudFront.png)
- Lướt xuống phần _Origin_
- Nhập _Custom origin_: cần nhập đường dẫn đến _S3 website hosting_ của bạn và bỏ tiền tố _http://_
- Hãy sử dụng setting khuyến nghị 
![CloudFront](/images/3.CloudFront/06-CloudFront.png)
- Sau đó chọn _Next_
![CloudFront](/images/3.CloudFront/07-CloudFront.png)
- Ở bước tiếp theo, bạn có thể chọn giữa _Enable security protections_(tốn phí) hoặc _Do not enable security protections_ (miễn phí). Sau đó chọn _Next_
![CloudFront](/images/3.CloudFront/08-CloudFront.png)
- Sau đó chọn _Create distribution_ để tạo _distribution
![CloudFront](/images/3.CloudFront/09-CloudFront.png)
- Sau khi tạo _distribution_, bạn cần đợi từ 5-20 phút đợi _Amazon CloudFront_ deploy
- Sau khi deploy xong, bạn xem được thời gian deploy và đường dẫn mới đến giao diện của bạn
