---
title: "Week 11 Worklog"
date: 2026-06-28
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

### Objectives for Week 11:

* Design core APIs
* Build the database
* Deploy the content approval workflow
* Optimize resource management
* Finalize technical documentation

### Tasks for Week 11:

| Day | Task | Start Date | Completion Date | References |
| :---: | :--- | :---: | :---: | :--- |
| 2 | Design APIs for Flashcard (POST/Create) and Quiz features, validate input data (max characters, question format). | 28/06/2026 | 29/06/2026 | [Build a RESTful API with API Gateway](https://docs.aws.amazon.com/apigateway/latest/developerguide/getting-started.html) |
| 3 | Create flashcards and quiz_results tables with processing statuses; build an admin interface to manage flashcard content. | 29/06/2026 | 30/06/2026 | [AWS Study Material](https://cloudjourney.awsstudygroup.com/) |
| 4 | Process content statuses (pending/approved); trigger Lambda to update the search index after approval. | 01/07/2026 | 02/07/2026 | [AWS Study Material](https://cloudjourney.awsstudygroup.com/) |
| 5 | Create Presigned URL APIs for S3 to allow users to upload learning images/audio; configure CloudFront URLs for retrieval. | 02/07/2026 | 03/07/2026 | [AWS Study Material](https://cloudjourney.awsstudygroup.com/) |
| 6 | Evaluate technical documentation, complete the Entity-Relationship Diagram (ERD) for users, flashcards, and test results; prepare for week 12. | 03/07/2026 | 05/07/2026 | [Entity Relationship Diagram Tutorial](https://lucid.co/diagram/erd/tutorial) |

### Week 11 Achievements:

* Successfully designed all APIs for Flashcard and Quiz features, including the deployment of strict input validation mechanisms to ensure data integrity.
* Completed the design of flashcards and quiz_results data tables in PostgreSQL; simultaneously developed a successful admin interface for moderating learning content.
* Successfully established the content status processing workflow (pending/approved) and integrated AWS Lambda to automate search index updates immediately after content is approved.
* Deployed the Amazon S3 Presigned URL mechanism in combination with CloudFront, allowing users to safely and optimally upload and retrieve learning resources (images/audio).
* Summarized and finalized the Entity-Relationship Diagram (ERD) for key entities (users, flashcards, learning results), creating a solid foundation for deploying subsequent phases.
