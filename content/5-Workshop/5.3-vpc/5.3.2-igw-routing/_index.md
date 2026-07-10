---
title: "Configure Internet Gateway & Route Tables"
date: 2026-07-09
weight: 2
chapter: false
pre: "<b>5.3.2. </b>"
---


After creating the VPC and Subnets, we need to configure an **Internet Gateway** to allow the Public Subnet to connect to the Internet, and **Route Tables** to direct network traffic correctly.

---

## 1. Create Internet Gateway

An **Internet Gateway (IGW)** is the gateway connecting the VPC to the Internet.

1. In the VPC Console → **Internet gateways** → **Create internet gateway**

2. Configure:

| Field        | Value            |
| ------------ | ---------------- |
| **Name tag** | `flashlearn-igw` |

3. Click **Create internet gateway**

<img width="1460" height="491" alt="image" src="https://github.com/user-attachments/assets/47f2f15b-fa22-4ec7-aec9-dd935d36b9fd" />


4. After creation, **attach the IGW to the VPC**:
   - Select `flashlearn-igw` → **Actions** → **Attach to VPC**
   - Select `flashlearn-vpc`
   - Click **Attach internet gateway**

<img width="1458" height="338" alt="image" src="https://github.com/user-attachments/assets/90f259fc-3ef3-449a-bfb0-4e8430e2aab8" />


---

## 2. Create Route Table for Public Subnet

A **Route Table** defines where network traffic is directed.

1. **Route tables** → **Create route table**

2. Configure:

| Field    | Value                  |
| -------- | ---------------------- |
| **Name** | `flashlearn-public-rt` |
| **VPC**  | `flashlearn-vpc`       |

3. Click **Create route table**

4. **Add a route to the Internet**: Select `flashlearn-public-rt` → **Routes** tab → **Edit routes** → **Add route**

| Destination | Target           |
| ----------- | ---------------- |
| `0.0.0.0/0` | `flashlearn-igw` |

5. Click **Save changes**
<img width="1452" height="355" alt="image" src="https://github.com/user-attachments/assets/f07f908b-f55a-4e35-af64-4a523738a603" />


6. **Associate with Public Subnet**: **Subnet associations** tab → **Edit subnet associations** → Select `flashlearn-public-subnet` → **Save associations**

---

## 3. Create Security Group for EC2

A **Security Group** acts as a virtual firewall, controlling inbound and outbound traffic for EC2.

1. **Security Groups** → **Create security group**

2. Configure:

| Field                   | Value                               |
| ----------------------- | ----------------------------------- |
| **Security group name** | `flashlearn-ec2-sg`                 |
| **Description**         | `Security group for FlashLearn EC2` |
| **VPC**                 | `flashlearn-vpc`                    |

3. **Inbound rules** — Add the following rules:

| Type       | Protocol | Port | Source    | Description           |
| ---------- | -------- | ---- | --------- | --------------------- |
| HTTP       | TCP      | 80   | 0.0.0.0/0 | HTTP from Internet    |
| HTTPS      | TCP      | 443  | 0.0.0.0/0 | HTTPS from Internet   |
| Custom TCP | TCP      | 5000 | 0.0.0.0/0 | ASP.NET Core app port |
| SSH        | TCP      | 22   | My IP     | SSH from your machine |

4. Click **Create security group**

---

## 4. Create Security Group for RDS

1. **Create security group**

2. Configure:

| Field                   | Value                               |
| ----------------------- | ----------------------------------- |
| **Security group name** | `flashlearn-rds-sg`                 |
| **Description**         | `Security group for FlashLearn RDS` |
| **VPC**                 | `flashlearn-vpc`                    |

3. **Inbound rules**:

| Type       | Protocol | Port | Source              | Description                |
| ---------- | -------- | ---- | ------------------- | -------------------------- |
| PostgreSQL | TCP      | 5432 | `flashlearn-ec2-sg` | Allow EC2 connections only |

>  **Security Note**: The source for the PostgreSQL rule must be the **EC2 Security Group** (not an IP address), ensuring only EC2 can access the database.

4. Click **Create security group**

---

## Result

After this step, you will have:
-  Internet Gateway `flashlearn-igw` attached to the VPC
-  Route Table `flashlearn-public-rt` routing traffic to the Internet
-  Security Group `flashlearn-ec2-sg` allowing HTTP/HTTPS/SSH
-  Security Group `flashlearn-rds-sg` allowing only EC2 to connect to PostgreSQL
