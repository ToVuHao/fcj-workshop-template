---
title: "Blog 2"
date: 2026-07-10
weight: 1
chapter: false
pre: " <b> 3.2. </b> "
---


# Event-Driven Architecture on AWS
EventBridge, SNS, and SQS in Serverless Systems
Event-Driven Architecture (EDA) is a system design pattern in which components communicate with one another through events instead of making direct REST API calls. On AWS, this architecture can be effectively implemented using services such as Amazon API Gateway, AWS Lambda, Amazon EventBridge, Amazon SNS, and Amazon SQS. This approach reduces dependencies between services, improves scalability, and enhances system reliability when handling asynchronous workloads.

Key Points to Know:
-Producers only generate events: After completing a business operation, an AWS Lambda function publishes an event to Amazon EventBridge instead of directly invoking another service. This reduces coupling between system components and allows services to operate more independently.
-Amazon EventBridge is responsible for event routing: EventBridge receives events, filters them according to configured rules, and forwards them to the appropriate targets. It also supports event routing across multiple AWS accounts.
-Amazon SNS provides a publish/subscribe mechanism: A single event can be distributed simultaneously to multiple subscribers, such as AWS Lambda, Amazon SQS, HTTP endpoints, or email recipients, without requiring any changes to the producer.
-Amazon SQS enables reliable asynchronous processing: Amazon SQS functions as a message queue that temporarily stores events, absorbs sudden traffic spikes, and supports retry mechanisms and Dead Letter Queues (DLQs) to reduce the risk of data loss when consumers encounter failures.
-The architecture is highly extensible: When new capabilities such as email notifications, audit logging, data lake integration, or machine learning workflows are required, additional consumers can simply subscribe to existing events without affecting the current components of the system.
-Optimized cost and scalability: By leveraging serverless services such as Amazon API Gateway, AWS Lambda, Amazon EventBridge, Amazon SNS, and Amazon SQS, the system automatically scales based on incoming traffic and incurs costs only when requests are processed.

This architecture is particularly well suited for microservices-based applications, asynchronous processing, multi-system integrations, and multi-account AWS environments, where high scalability, loose coupling between services, and strong fault tolerance are essential requirements.

<img width="696" height="583" alt="image" src="https://github.com/user-attachments/assets/4ce431a6-61d4-43d3-b465-cfd79232da3e" />


[...Link...](https://www.facebook.com/share/p/19BpYphs7p/)

...Guide...
