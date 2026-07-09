---
title: "Khởi tạo VPC & Subnets"
date: 2024-01-01
weight: 1
chapter: false
pre: "<b>5.3.1. </b>"
---



Trong bước này, chúng ta sẽ tạo một VPC mới và phân chia thành các subnet cụ thể cho từng lớp ứng dụng.

---

## 1. Tạo VPC

1. Đăng nhập **AWS Console** → Tìm kiếm **VPC** → Chọn **VPC**

2. Chọn **Create VPC**

<img width="1919" height="269" alt="5 3 1 1" src="https://github.com/user-attachments/assets/12806a7a-4892-493d-885d-cd574e87647b" />



1. Cấu hình VPC:

| Trường                  | Giá trị            |
| ----------------------- | ------------------ |
| **Resources to create** | VPC only           |
| **Name tag**            | `flashlearn-vpc`   |
| **IPv4 CIDR block**     | `10.0.0.0/16`      |
| **IPv6 CIDR block**     | No IPv6 CIDR block |
| **Tenancy**             | Default            |

4. Nhấn **Create VPC**

<img width="1919" height="850" alt="5 3 1 2" src="https://github.com/user-attachments/assets/cd752d69-4f48-4b13-8dda-df3761c9562c" />


---

## 2. Tạo Public Subnet

Public Subnet sẽ chứa EC2 instance chạy ứng dụng FlashLearn.

1. Trong VPC Console → **Subnets** → **Create subnet**

2. Cấu hình:

| Trường                | Giá trị                    |
| --------------------- | -------------------------- |
| **VPC ID**            | Chọn `flashlearn-vpc`      |
| **Subnet name**       | `flashlearn-public-subnet` |
| **Availability Zone** | `ap-southeast-1a`          |
| **IPv4 CIDR block**   | `10.0.1.0/24`              |

3. Nhấn **Create subnet**

<img width="1919" height="853" alt="5 3 1 3" src="https://github.com/user-attachments/assets/7982dc75-1b3f-498c-9382-042e52aa32a8" />



1. Sau khi tạo xong, **bật tính năng Auto-assign public IP**:
   - Chọn subnet `flashlearn-public-subnet`
   - **Actions** → **Edit subnet settings**
   - Tích chọn **Enable auto-assign public IPv4 address**
   - Nhấn **Save**

---

## 3. Tạo Private Subnet

Private Subnet sẽ chứa RDS database, không có kết nối Internet trực tiếp.

1. **Subnets** → **Create subnet**

2. Cấu hình subnet thứ nhất:

| Trường                | Giá trị                       |
| --------------------- | ----------------------------- |
| **VPC ID**            | Chọn `flashlearn-vpc`         |
| **Subnet name**       | `flashlearn-private-subnet-1` |
| **Availability Zone** | `ap-southeast-1a`             |
| **IPv4 CIDR block**   | `10.0.2.0/24`                 |

3. Nhấn **Add new subnet** để thêm subnet thứ 2 (RDS yêu cầu tối thiểu 2 AZ):

| Trường                | Giá trị                       |
| --------------------- | ----------------------------- |
| **Subnet name**       | `flashlearn-private-subnet-2` |
| **Availability Zone** | `ap-southeast-1b`             |
| **IPv4 CIDR block**   | `10.0.3.0/24`                 |

4. Nhấn **Create subnet**

<img width="1919" height="898" alt="5 3 1 4" src="https://github.com/user-attachments/assets/23e6c097-226b-475a-8262-4519c24ec511" />

<img width="1909" height="764" alt="5 3 1-vpc-created" src="https://github.com/user-attachments/assets/00f80f14-0611-464f-9ded-e31836dad71f" />


---

## Kết quả

Sau bước này, bạn đã có:
-  VPC `flashlearn-vpc` với CIDR `10.0.0.0/16`
-  Public Subnet `10.0.1.0/24` tại `ap-southeast-1a`
-  Private Subnet 1 `10.0.2.0/24` tại `ap-southeast-1a`
-  Private Subnet 2 `10.0.3.0/24` tại `ap-southeast-1b`
