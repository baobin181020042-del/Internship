---
title: "Week 11"
date: 2026-06-29
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

**Timeline:** 29/6 → 3/7 (5 working days)

> IRMS was completed by a five-member team. The notes below focus on my individual contribution while collaborating with the team.

## Day 1 - 29/6: Starting the IRMS project

**Work completed:** I joined the team discussion to officially start the IRMS project. The team aligned on the scope of an information security incident management system, while I focused on AWS infrastructure, deployment flow, and how the project could be documented as a workshop.

I reviewed the main requirements: incident management, timeline tracking, evidence upload, report generation, and alert handling. I then listed the AWS services needed for the project, including Cognito, API Gateway, Lambda, DynamoDB, S3 Evidence Store, EventBridge, SNS, Secrets Manager, CloudWatch, and CloudFront. I also separated the areas I would handle directly from the areas that required coordination with frontend and backend teammates.

**Knowledge learned:** A team project needs clear scope and responsibility boundaries early; otherwise, implementation and documentation can drift quickly.

**Result achieved:** The team had a clearer implementation direction, and I had an AWS infrastructure and documentation checklist for the following days.

**Difficulty and lesson learned:** There were many possible extensions at first, so we had to prioritize the core features to fit the internship schedule.

## Day 2 - 30/6: Requirement analysis and technical assignment

**Work completed:** I worked with the team to break the IRMS use cases into smaller implementation flows. My deeper focus was user authentication with Cognito, REST routing through API Gateway, business logic in Lambda, and data storage in DynamoDB.

I helped describe the data flow for Incident CRUD, Timeline, Evidence Upload, and Report Generation. For each flow, I wrote down the input, output, related AWS services, and testing points. I also discussed with the frontend teammate to align the endpoints, response format, and how the frontend should send the JWT in the Authorization header.

**Knowledge learned:** In a serverless project, the API contract is important because frontend code, Lambda functions, and DynamoDB access all depend on the same data structure.

**Result achieved:** The work items became clearer, which helped me prepare the SAM template and workshop documentation closer to the actual implementation.

**Difficulty and lesson learned:** Some requirements were still broad, so I needed to turn them into concrete checklists instead of relying on assumptions.

## Day 3 - 1/7: Finalizing the overall architecture

**Work completed:** I focused on the architecture diagram and the request flow from the React frontend to backend services. The team agreed on a serverless direction: React + Vite frontend hosted with S3/CloudFront, backend through API Gateway, Cognito Authorizer, Lambda, and DynamoDB, with evidence files stored in S3 through presigned URLs.

I checked the connection points between GuardDuty, EventBridge, Lambda Alert Handler, and SNS so the alerting section would be documented correctly. For AI Assistant, I clearly noted that Lambda reads the secret from Secrets Manager and calls the Groq API, avoiding API keys in the frontend or public documentation. I also updated notes to separate implemented architecture from future enhancements.

**Knowledge learned:** Architecture is not only a diagram; it must match how requests, credentials, logs, and data actually move through the system.

**Result achieved:** The IRMS architecture was finalized for consistent use in the Proposal, Workshop, and Worklog.

**Difficulty and lesson learned:** If service names and arrows are not aligned early, later documentation pages can easily contradict each other.

## Day 4 - 2/7: Preparing AWS SAM and infrastructure

**Work completed:** I started preparing the AWS SAM structure for the backend infrastructure. I reviewed the resources by group: Cognito for authentication, API Gateway for REST APIs, Lambda for business logic, DynamoDB for incident/timeline/user/evidence metadata, S3 for evidence, and EventBridge/SNS for alerts.

I validated the template with `sam validate`, reviewed Lambda IAM roles, and checked environment variables such as table names, bucket names, secret name, and AI provider. I also recorded the steps that needed to appear in the workshop, including AWS CLI/SAM CLI installation, profile configuration, build, validation, and deployment.

```bash
sam validate
sam build
sam deploy --guided
```

**Knowledge learned:** SAM helps keep infrastructure in code, but variable names and IAM permissions must be clear to avoid deployment errors.

**Result achieved:** The backend infrastructure baseline was ready for the team to continue Lambda implementation and API testing.

**Difficulty and lesson learned:** Small template or IAM mistakes can block deployment, so validating early is better than waiting until the end.

## Day 5 - 3/7: Initial documentation synchronization

**Work completed:** I started synchronizing the Proposal and Workshop with the agreed IRMS architecture. The main goal was to keep the Vietnamese and English versions equivalent in content, with only the language being different. I reviewed the Introduction, Environment Setup, and Infrastructure Configuration sections to avoid mismatched bilingual content.

I also recorded items that needed further validation in the following week, such as Cognito JWT, API Gateway CORS, Lambda logs, DynamoDB key design, S3 presigned URLs, and CloudFront deployment. Items that were not fully tested were marked for confirmation instead of being written as completed.

**Knowledge learned:** Technical documentation should be updated alongside implementation, because leaving everything until the end makes it difficult to remember real issues and fixes accurately.

**Result achieved:** Worklog, Proposal, and Workshop started following the same project timeline from the week that includes July 1.

**Difficulty and lesson learned:** The worklog must describe my personal contribution in a five-member team, not present the whole system as work I completed alone.
