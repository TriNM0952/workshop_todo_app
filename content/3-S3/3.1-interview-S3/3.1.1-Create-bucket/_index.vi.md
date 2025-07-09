---
title : "Tạo S3 bucket"
date: 2025-07-09 
weight : 1
chapter : false
pre : " <b> 3.1.1 </b> "
---
## Tạo bucket
1. Tạo S3 bucket  
- Truy cập _AWS Management Console_.
- Tìm _S3_ trên giao diện hoặc thanh tìm kiếm 
- Chọn S3
![S3](/images/3.S3/01-S3.png)
2. Trong giao diện _S3_, chọn _create bucket_
![S3](/images/3.S3/02-S3.png)
3. Trong giao diện _Create bucket_
- _Bucket name_: nhập ```todo-web-frontend-ws```
![S3](/images/3.S3/03-S3.png)
- **Lưu ý**: Vì _Bucket name_ là duy nhất trên mức độ toàn cầu, nếu sử dụng tên giống như trên sẽ xuất hiện thông báo: “Bucket with the same name already exists”. Do đó, cần thêm vài số phía sau để _Bucket name_ của bạn phù hợp với policy.
![S3](/images/3.S3/06-S3.png)
4. Trong phần _Block Public Access settings for this bucket_ chúng ta tắt nó đi và tích vào ô _I acknowledge that the current settings might result in this bucket and the objects within becoming public._
![S3](/images/3.S3/04-S3.png)
5. Giữ nguyên các phần còn lại và chọn _creater bucket_
![S3](/images/3.S3/05-S3.png)
6. Hoàn thành việc tạo _S3 bucket_ để lưu trữ source code.
![S3](/images/3.S3/07-S3.png)