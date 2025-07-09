---
title : "Phân phối giao diện qua CloudFront"
date: 2025-07-09 
weight : 2 
chapter : false
pre : " <b> 3.2. </b> "
---
## Giới thiệu về Amazon CloudFront

- **Amazon CloudFront** là một **Content Delivery Network (CDN)** do AWS cung cấp, được tối ưu cho hiệu suất và bảo mật.
  - Phân phối nội dung thông qua hàng trăm **Edge Locations** toàn cầu.
  - Giảm độ trễ và tăng tốc độ truyền tải bằng cách phục vụ nội dung từ vị trí gần người dùng cuối.

- **Hỗ trợ nội dung**
  - Nội dung tĩnh: HTML, CSS, JS, hình ảnh, video.
  - Nội dung động: sử dụng caching có điều kiện và hỗ trợ:
    - HTTP/2
    - TLS 1.3
    - WebSocket

- **Tích hợp với các dịch vụ AWS**
  - Amazon S3
  - Elastic Load Balancing
  - Amazon EC2
  - AWS Lambda@Edge
    - Xử lý logic phía edge như:
      - Xác thực người dùng
      - Chuyển hướng URL
      - Tùy biến response theo điều kiện

- **Tính năng bảo mật**
  - Geo-restriction và Signed URLs/Cookies để kiểm soát truy cập.
  - Tích hợp với AWS WAF để lọc traffic độc hại.
  - Bảo vệ DDoS với AWS Shield Standard.

- **Khả năng mở rộng và tùy chỉnh**
  - Hỗ trợ header tùy biến.
  - Tự động scale theo lưu lượng truy cập.
  - Phù hợp cho ứng dụng có yêu cầu cao về:
    - Hiệu năng
    - Độ sẵn sàng
    - Bảo mật

