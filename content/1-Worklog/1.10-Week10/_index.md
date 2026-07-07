---
title: "Week 10 Worklog"
date: 2026-06-21
weight: 2
chapter: false
pre: " <b> 1.10. </b> "
---

### Objectives for Week 10:

* Build the FlashLearn system – a web application to support English learning through flashcards, quizzes, battles, and a learning community.
* Deploy a modern system architecture on the AWS platform (Singapore Region) with a VPC structure across two Availability Zones to ensure high availability.
* Optimize application performance by combining the Serverless model and managed services such as Amazon CloudFront, Lambda, and EventBridge.

### Tasks for Week 10:

| Day | Task | Start Date | Completion Date | References |
| :---: | :--- | :---: | :---: | :--- |
| 2 | Team meeting: Finalize the PostgreSQL database Schema design and collect learning data. | 21/06/2026 | 22/06/2026 | [AWS Study Material](https://cloudjourney.awsstudygroup.com/) |
| 3 | Deploy VPC across 2 Availability Zones; configure security with IAM and set up access permissions for the EC2 instance. | 22/06/2026 | 23/06/2026 | [AWS Study Material](https://cloudjourney.awsstudygroup.com/) |
| 4 | Configure ALB to load balance for EC2 instances; deploy static content to S3 and CloudFront. | 23/06/2026 | 24/06/2026 | [AWS Study Material](https://cloudjourney.awsstudygroup.com/) |
| 5 | Team Meeting: Review UI design on Figma; optimize the user experience flow based on feedback. | 24/06/2026 | 26/06/2026 | [AWS Study Material](https://cloudjourney.awsstudygroup.com/) |
| 6 | Set up EventBridge to trigger Lambda for automated notification processing; integrate Amazon Polly for the pronunciation feature. | 26/06/2026 | 28/06/2026 | [AWS Study Material](https://cloudjourney.awsstudygroup.com/) |

### Week 10 Achievements:

* Perfected the network architecture including VPC, Public/Private Subnet, Application Load Balancer (ALB), and established a synchronous data replication mechanism for RDS PostgreSQL across availability zones.
* Used Amazon S3 and CloudFront to distribute static content.
* Integrated Amazon Polly to provide text-to-speech (TTS) features via internal API calls.
* Configured Amazon EventBridge in combination with AWS Lambda to handle scheduled tasks such as sending deadline reminder notifications.
* Conducted team meetings to finalize the PostgreSQL database Schema design and improved the UI interface on Figma.
* Mastered security and identity management services including IAM, AWS WAF, and NAT Gateway to ensure system safety.
