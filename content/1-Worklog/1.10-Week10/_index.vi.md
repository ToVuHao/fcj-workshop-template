---
title: "Worklog Tuần 10"
date: 2026-06-21
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

### Mục tiêu cho tuần 10:

* Xây dựng hệ thống FlashLearn – ứng dụng web hỗ trợ học tiếng Anh thông qua flashcard, quiz, battle và cộng đồng học tập.
* Triển khai kiến trúc hệ thống hiện đại trên nền tảng AWS (Khu vực Singapore) với cấu trúc VPC trên hai Availability Zone để đảm bảo tính sẵn sàng cao.
* Tối ưu hóa hiệu năng ứng dụng bằng cách kết hợp mô hình Serverless và các dịch vụ quản lý như Amazon CloudFront, Lambda và EventBridge.

### Nhiệm vụ cho tuần 10:

| Ngày | Nhiệm vụ | Ngày bắt đầu | Ngày hoàn thành | Tài liệu tham khảo |
| :---: | :--- | :---: | :---: | :--- |
| 2 | Họp nhóm: Hoàn thiện thiết kế Schema cơ sở dữ liệu PostgreSQL và thu thập dữ liệu học tập. | 21/06/2026 | 22/06/2026 | [Tài liệu học tập AWS](https://cloudjourney.awsstudygroup.com/) |
| 3 | Triển khai VPC trên 2 Availability Zone; cấu hình bảo mật với IAM và thiết lập quyền truy cập cho EC2 instance. | 22/06/2026 | 23/06/2026 | [Tài liệu học tập AWS](https://cloudjourney.awsstudygroup.com/) |
| 4 | Cấu hình ALB để cân bằng tải cho các EC2 instance; triển khai nội dung tĩnh lên S3 và CloudFront. | 23/06/2026 | 24/06/2026 | [Tài liệu học tập AWS](https://cloudjourney.awsstudygroup.com/) |
| 5 | Team Meeting: Review thiết kế UI trên Figma; tối ưu luồng trải nghiệm người dùng dựa trên phản hồi. | 24/06/2026 | 26/06/2026 | [Tài liệu học tập AWS](https://cloudjourney.awsstudygroup.com/) |
| 6 | Thiết lập EventBridge để trigger Lambda xử lý thông báo tự động; tích hợp Amazon Polly cho tính năng phát âm. | 26/06/2026 | 28/06/2026 | [Tài liệu học tập AWS](https://cloudjourney.awsstudygroup.com/) |

### Thành tích tuần 10:

* Hoàn thiện kiến trúc mạng bao gồm VPC, Public/Private Subnet, Application Load Balancer (ALB) và thiết lập cơ chế đồng bộ hóa dữ liệu (Synchronous replication) cho RDS PostgreSQL giữa các vùng sẵn sàng.
* Sử dụng Amazon S3 và CloudFront để phân phối nội dung tĩnh.
* Tích hợp Amazon Polly để cung cấp tính năng chuyển đổi văn bản thành giọng nói (TTS) qua các cuộc gọi API nội bộ.
* Cấu hình Amazon EventBridge kết hợp với AWS Lambda để xử lý các tác vụ định kỳ như gửi thông báo nhắc nhở hạn chót.
* Thực hiện các phiên họp nhóm để hoàn thiện thiết kế Schema cơ sở dữ liệu PostgreSQL và cải thiện giao diện UI trên Figma.
* Nắm vững các dịch vụ bảo mật và quản lý định danh bao gồm IAM, AWS WAF và NAT Gateway để đảm bảo an toàn cho hệ thống.
