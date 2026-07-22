---
title: "Bản đề xuất"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---


Tại phần này, bạn cần tóm tắt các nội dung trong workshop mà bạn **dự tính** sẽ làm.

# Hệ thống học tập FlashLearn trên nền tảng AWS 
## Giải pháp kiến trúc ứng dụng Web có tính sẵn sàng cao (High Availability Architecture)  

### 1. Tóm tắt điều hành
Hệ thống FlashLearn là ứng dụng web toàn diện được thiết kế nhằm hỗ trợ người dùng học tiếng Anh thông qua flashcard, quiz, battle và cộng đồng học tập. Dự án tập trung xây dựng kiến trúc hạ tầng hiện đại trên AWS tại khu vực Singapore, chú trọng vào tính phân tán, tự động hóa và tích hợp AI. Nền tảng hướng tới mục tiêu tối ưu hóa trải nghiệm người dùng, đảm bảo tính sẵn sàng cao thông qua cấu trúc mạng Multi-AZ và áp dụng mô hình điện toán Serverless để vận hành thông minh, tiết kiệm chi phí.

### 2. Tuyên bố vấn đề  
Vấn đề hiện tại
Các ứng dụng học ngoại ngữ truyền thống thường gặp khó khăn khi quản lý tài nguyên đa phương tiện (ảnh, âm thanh) và xử lý luồng logic phức tạp. Việc lưu trữ trực tiếp trên máy chủ gây nghẽn băng thông khi lượng người dùng lớn, thiếu cơ chế sao lưu dữ liệu đồng bộ khiến thông tin học tập của người dùng dễ bị mất mát khi máy chủ gặp sự cố.

Giải pháp
Kiến trúc phân tán được đề xuất nhằm tách biệt các luồng xử lý: Sử dụng CDN để phân phối nội dung tĩnh, cơ sở dữ liệu quan hệ với cơ chế đồng bộ hóa (Synchronous replication) giữa các vùng sẵn sàng, và kiến trúc phi máy chủ (Serverless) để tự động hóa các tác vụ nền như nén ảnh, xử lý thông báo và chuyển đổi văn bản thành giọng nói (TTS).

Lợi ích và hoàn vốn đầu tư (ROI)
Giải pháp tạo nền tảng vững chắc, có khả năng mở rộng quy mô người dùng từ quy mô nhỏ đến cộng đồng học tập lớn. Việc tự động hóa giúp giảm thiểu tối đa các tác vụ thủ công trong quản lý nội dung và giám sát hệ thống. Tổng chi phí duy trì hàng tháng ước tính khoảng 152,78 USD (dựa trên cấu hình Multi-AZ và NAT Gateway), mang lại giá trị vận hành ổn định và lâu dài.

### 3. Kiến trúc giải pháp  
Nền tảng áp dụng kiến trúc phân tán với các dịch vụ chuyên biệt của AWS, đặt bên trong VPC có phân chia Subnet rõ ràng trên 2 Availability Zones.

<img width="823" height="492" alt="image" src="https://github.com/user-attachments/assets/489efd4b-60bb-4bab-8706-89a3b5c9c01b" />



Dịch vụ AWS sử dụng

AWS VPC: Mạng nội bộ với Public/Private Subnet trên 2 AZ.

Amazon EC2 (ARM64): Xử lý logic Backend.

Application Load Balancer (ALB): Cân bằng tải cho các EC2 instances.

Amazon RDS (PostgreSQL): Cơ sở dữ liệu Multi-AZ.

Amazon S3 & CloudFront: Phân phối tài nguyên tĩnh an toàn.

AWS Lambda & EventBridge: Xử lý tác vụ tự động, theo lịch trình.

Amazon Polly: Tích hợp tính năng AI chuyển đổi văn bản sang giọng nói.

CloudWatch & X-Ray: Giám sát hiệu năng và phân tích luồng API.

Thiết kế thành phần

Lớp biên: Route 53 và WAF bảo vệ ứng dụng khỏi các truy cập độc hại.

Lớp xử lý: EC2 instances đặt trong Private Subnet, đảm bảo an toàn tuyệt đối.

Lớp dữ liệu: RDS PostgreSQL với cơ chế sao lưu đồng bộ đảm bảo tính nhất quán dữ liệu.

Lớp AI/Tự động hóa: Lambda kích hoạt bởi EventBridge xử lý các tác vụ nhắc nhở và cập nhật hệ thống.
### 4. Triển khai kỹ thuật  
Các giai đoạn triển khai

Nghiên cứu & Thiết kế: Thiết kế Schema DB, sơ đồ ERD, tối ưu luồng UI trên Figma.

Thiết lập hạ tầng mạng: Cấu hình VPC, Subnets, Internet Gateway và NAT Gateway.

Triển khai tài nguyên: Cấu hình EC2, ALB, S3 và CloudFront.

Phát triển tính năng: Xây dựng các API (Flashcard, Quiz), tích hợp Polly, Lambda và EventBridge.

Kiểm thử & Giám sát: Thiết lập CloudWatch, X-Ray để giám sát hệ thống và bàn giao.

Yêu cầu kỹ thuật

Sử dụng kiến trúc ARM64 cho EC2 để tối ưu chi phí/hiệu năng.

Tuân thủ nguyên tắc Security Group: EC2 chỉ nhận traffic từ ALB; RDS chỉ nhận traffic từ EC2.

Áp dụng cơ chế OAC cho S3 để chỉ chấp nhận truy cập từ CloudFront.
### 5. Lộ trình & Mốc triển khai  
Tuần 1–3: Xây dựng nền tảng mạng và hạ tầng dữ liệu.

Tuần 4–8: Phát triển các service Backend, AI/ML và phân tích dữ liệu.

Tuần 9–10: Hoàn thiện các tính năng cốt lõi, tích hợp giám sát và AI TTS.

Tuần 11–12: Triển khai tính năng tương tác cộng đồng, tối ưu hóa toàn hệ thống và bàn giao.

### 6. Ước tính ngân sách  
Chi phí vận hành hàng tháng ước tính tại khu vực Singapore (ap-southeast-1):

RDS Multi-AZ: ~$46.40

NAT Gateway (x2): ~$65.70

ALB: ~$16.42

EC2 (x2), S3, CloudFront, WAF, Lambda, Polly: ~$23.66

Tổng cộng: ~$152.18 / tháng.

### 7. Đánh giá rủi ro  
Ma trận rủi ro

Chi phí NAT Gateway cao: Ảnh hưởng cao, xác suất trung bình.

Lỗi kết nối Security Group: Ảnh hưởng trung bình, xác suất thấp.

Băng thông CloudFront vượt hạn mức: Ảnh hưởng trung bình, xác suất thấp.

Chiến lược giảm thiểu

Tối ưu hóa cấu hình NAT Gateway trong môi trường phát triển.

Kiểm tra nghiêm ngặt quy tắc Security Group trước khi triển khai.

Cấu hình phân chia cache rõ ràng trong CloudFront để tránh lãng phí băng thông.

### 8. Kết quả kỳ vọng  
Cải tiến kỹ thuật: Hệ thống vận hành ổn định, sẵn sàng cao với kiến trúc Multi-AZ, đáp ứng tốt nhu cầu học tập tương tác của người dùng.
Giá trị dài hạn: Nền tảng dữ liệu được cấu trúc chặt chẽ, dễ dàng mở rộng và tích hợp thêm các dịch vụ AI nâng cao trong tương lai.
