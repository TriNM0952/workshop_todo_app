---
title : "Tải dữ liệu và cấu hình "
date: 2025-07-09 
weight : 2 
chapter : false
pre : " <b> 3.1.2. </b> "
---
## Tải dữ liệu  



- Hiện tại chúng ta chưa có _object_ nào
![S3](/images/3.S3/08-S3.png)
- Chúng ta cần ta cần tải source giao diện lên S3
- Vào VS Code, mở source giao diện, mở terminal và chạy lệnh ```aws s3 sync build/ s3://todo-web-frontend-ws --delete```
- *Lưu ý*: hãy sửa lại đường dẫn tùy theo đường vị trí dẫn đến folder giao diện của bạn
- Sau khi chạy, soucre của bạn sẽ được tải lên S3
![S3](/images/3.S3/014-S3-Load-data.png)
![S3](/images/3.S3/015-S3-Load-data.png)
## Cấu hình  
- Chọn _permission_ trong _bucket_, lướt xuống phần _bucket policy_ chọn _edit_. 
![S3](/images/3.S3/017-S3-Load-data.png)
- Sau đó cấu hình cho S3
```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "AllowPublicRead",
      "Effect": "Allow",
      "Principal": "*",
      "Action": ["s3:GetObject"],
      "Resource": ["arn:aws:s3:::todo-web-frontend-ws/*"]
    }
  ]
}
```
- Sau đó chọn _save changes_
![S3](/images/3.S3/018-S3-Load-data.png)
- Tiếp theo, bạn chọn vào _Properties_, lướt xuống phần _Static website hosting_ chọn edit
![S3](/images/3.S3/019-S3-Load-data.png)
- Chọn _enable_
![S3](/images/3.S3/S20-S3-Load-data.png)
- _Index document_ nhập index.html
- _Error document_ nhập index.html
- Sau đó nhấn _Save change_
![S3](/images/3.S3/021-S3-Load-data.png)
- Trong phần _Static website hosting_ có phần _Bucket website endpoint_, bạn sẽ nhận được đường dẫn đến giao diện tĩnh của bạn
![S3](/images/3.S3/022-S3-Load-data.png)
- Bạn có thể truy cập đường dẫn đến giao diện tĩnh của bạn trên S3