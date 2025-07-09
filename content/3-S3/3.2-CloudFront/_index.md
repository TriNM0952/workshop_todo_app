---
title : "Distribute UI via CloudFront"
date: 2025-07-09 
weight : 2 
chapter : false
pre : " <b> 3.2. </b> "
---
## Introduction to Amazon CloudFront

- **Amazon CloudFront** is a **Content Delivery Network (CDN)** provided by AWS, optimized for performance and security.
  - Distributes content through hundreds of **Edge Locations** worldwide.
  - Reduces latency and increases delivery speed by serving content from locations close to end users.

- **Content Support**
  - Static content: HTML, CSS, JS, images, video.
  - Dynamic content: uses conditional caching and supports:
    - HTTP/2
    - TLS 1.3
    - WebSocket

- **Integration with AWS services**
  - Amazon S3
  - Elastic Load Balancing
  - Amazon EC2
  - AWS Lambda@Edge
    - Process logic at the edge such as:
      - User authentication
      - URL redirection
      - Customizing responses based on conditions

- **Security features**
  - Geo-restriction and Signed URLs/Cookies to control access.
  - Integration with AWS WAF to filter malicious traffic.
  - DDoS protection with AWS Shield Standard.

- **Scalability and customization**
  - Supports custom headers.
  - Automatically scales with traffic.
  - Suitable for applications with high requirements for:
    - Performance
    - Availability
    - Security