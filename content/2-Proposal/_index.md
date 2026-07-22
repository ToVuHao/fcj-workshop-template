---
title: "Proposal"
date: 2024-01-01
weight: 2
chapter: false
pre: " <b> 2. </b> "
---


In this section, you need to summarize the contents of the workshop that you **plan** to conduct.

# FlashLearn Learning System on AWS
## A Proposal for a High Availability Web Application Architecture

### 1.Executive Summary
FlashLearn is a comprehensive web application designed to support English language learning through features such as flashcards, quizzes, battles, and a learning community. This project focuses on building a modern infrastructure on AWS in the Singapore region, emphasizing decentralization, automation, and AI integration. The platform aims to optimize user experience, ensure high availability through a Multi-AZ network structure, and apply a Serverless computing model for intelligent and cost-effective operations.

### 2. Problem Statement
Current Challenges
Traditional language learning applications often struggle with managing multimedia resources (images, audio) and processing complex logic. Storing these directly on web servers leads to bandwidth congestion during peak traffic, while the lack of synchronized backup mechanisms makes user learning data (quiz results, favorited flashcards) vulnerable to loss during server failures.

Proposed Solution
A distributed architecture is proposed to decouple processing flows: utilizing a CDN for static content distribution, relational databases with synchronous replication between Availability Zones, and a Serverless architecture to automate background tasks such as image compression, notification processing, and Text-to-Speech (TTS) conversion.

Benefits and ROI
The solution establishes a robust foundation capable of scaling from small groups to a large learning community. Automation significantly reduces manual overhead in content management and system monitoring. The estimated monthly operational cost is approximately $152.78 (based on Multi-AZ and NAT Gateway configurations), ensuring long-term operational stability and efficiency.
### The Solution
The platform uses AWS IoT Core to ingest MQTT data, AWS Lambda and API Gateway for processing, Amazon S3 for storage (including a data lake), and AWS Glue Crawlers and ETL jobs to extract, transform, and load data from the S3 data lake to another S3 bucket for analysis. AWS Amplify with Next.js provides the web interface, and Amazon Cognito ensures secure access. Similar to Thingsboard and CoreIoT, users can register new devices and manage connections, though this platform operates on a smaller scale and is designed for private use. Key features include real-time dashboards, trend analysis, and low operational costs.

### Benefits and Return on Investment
The solution establishes a foundational resource for lab members to develop a larger IoT platform, serving as a study resource, and provides a data foundation for AI enthusiasts for model training or analysis. It reduces manual reporting for each station via a centralized platform, simplifying management and maintenance, and improves data reliability. Monthly costs are $0.66 USD per the AWS Pricing Calculator, with a 12-month total of $7.92 USD. All IoT equipment costs are covered by the existing weather station setup, eliminating additional development expenses. The break-even period of 6-12 months is achieved through significant time savings from reduced manual work.

### 3. Solution Architecture
The platform utilizes a distributed architecture with specialized AWS services, housed within a Virtual Private Cloud (VPC) with clear subnet segmentation across two Availability Zones.
<img width="823" height="492" alt="image" src="https://github.com/user-attachments/assets/73faf9a0-5844-4241-9027-e0b8daf2c3e4" />



AWS Services Used

AWS VPC: Virtual network with Public/Private Subnets across 2 AZs.

Amazon EC2 (ARM64): Handles Backend logic.

Application Load Balancer (ALB): Balances traffic for EC2 instances.

Amazon RDS (PostgreSQL): Multi-AZ relational database.

Amazon S3 & CloudFront: Secure static asset distribution.

AWS Lambda & EventBridge: Automated task processing and scheduling.

Amazon Polly: AI-integrated Text-to-Speech feature.

CloudWatch & X-Ray: Performance monitoring and API trace analysis.

Component Design

Edge Layer: Route 53 and WAF protect the application from malicious access.

Processing Layer: EC2 instances reside in Private Subnets for maximum security, receiving traffic only from the ALB.

Data Layer: RDS PostgreSQL with synchronous replication ensures data consistency.

AI/Automation Layer: Lambda, triggered by EventBridge, handles notifications and system updates.

### 4. Technical Implementation
Implementation Phases

Research & Design: Database Schema design, ERD mapping, and UI/UX optimization on Figma.

Network Infrastructure: Configuration of VPC, Subnets, Internet Gateway, and NAT Gateway.

Resource Deployment: Configuration of EC2, ALB, S3, and CloudFront.

Feature Development: Building APIs (Flashcard, Quiz), integrating Polly, Lambda, and EventBridge.

Testing & Monitoring: Setting up CloudWatch, X-Ray, and conducting end-to-end testing before handover.

Technical Requirements

Use ARM64 architecture for EC2 to optimize cost-to-performance ratio.

Strictly adhere to Security Group principles: EC2 accepts inbound traffic only from the ALB; RDS accepts inbound traffic only from EC2.

Implement OAC (Origin Access Control) for S3 to restrict access solely to CloudFront.
**Technical Requirements**
- Weather Edge Station: Sensors (temperature, humidity, rainfall, wind speed), a microcontroller (ESP32), and a Raspberry Pi as the edge device. Raspberry Pi runs Raspbian, handles Docker for filtering, and sends 1 MB/day per station via MQTT over Wi-Fi.
- Weather Platform: Practical knowledge of AWS Amplify (hosting Next.js), Lambda (minimal use due to Next.js), AWS Glue (ETL), S3 (two buckets), IoT Core (gateway and rules), and Cognito (5 users). Use AWS CDK/SDK to code interactions (e.g., IoT Core rules to S3). Next.js reduces Lambda workload for the fullstack web app.

### 5. Timeline & Milestones
Weeks 1–3: Build network foundation and data infrastructure.

Weeks 4–8: Develop Backend services, AI/ML features, and data analytics.

Weeks 9–10: Finalize core features, integrate monitoring, and AI TTS.

Weeks 11–12: Deploy community interaction features, system optimization, and project handover.

### 6. Budget Estimation
Estimated monthly operational costs in the Singapore region (ap-southeast-1) based on On-Demand pricing:

RDS Multi-AZ: ~$46.40

NAT Gateway (x2): ~$65.70

ALB: ~$16.42

EC2 (x2), S3, CloudFront, WAF, Lambda, Polly: ~$23.66

Total: ~$152.18 / month.

### 7. Risk Assessment
Risk Matrix

High NAT Gateway costs: Medium probability, High impact.

Security Group connectivity errors: Low probability, Medium impact.

CloudFront bandwidth overage: Low probability, Medium impact.

Mitigation Strategies

Optimize NAT Gateway configurations during the development phase.

Rigorously verify Security Group rules prior to deployment.

Configure precise cache behavior in CloudFront to prevent unnecessary bandwidth consumption.
### 8. Expected Outcomes
Technical Improvements: A highly available, stable system with Multi-AZ architecture, well-suited for interactive user learning.
Long-term Value: A structured data platform that is easily scalable and ready to integrate advanced AI services in the future.
#### Long-term Value
1-year data foundation for AI research.  
Reusable for future projects.
