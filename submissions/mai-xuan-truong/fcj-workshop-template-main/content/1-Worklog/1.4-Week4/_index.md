---
title: "Week 4"
date: 2024-01-01
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

**Timeline:** 7/5 → 12/5 (6 days)

> IRMS was completed by a five-member team. The notes below focus on my individual contribution while collaborating with the team.

## Day 1 - 7/5: Team discussion and IRMS topic selection

**Work completed:** I joined the five-member team discussion to select IRMS as the project topic. My individual contribution was evaluating the AWS serverless direction and identifying suitable services such as API Gateway, Lambda, DynamoDB, S3, and CloudFront.

I also recorded the concrete checks I performed, the integration points I verified, and the issues I needed to report back to teammates. This made the entry reflect my own internship work instead of describing the whole project as if it was completed by one person.

**Knowledge gained:** I learned how to select a topic based on team capability, internship timeline, and realistic AWS demo scope.

**Result:** The team agreed on IRMS, and I took primary responsibility for AWS infrastructure, deployment, and testing.

**Difficulty and lesson:** The initial scope was broad. The lesson was to divide responsibilities clearly so the project did not look like one person owned everything.

## Day 2 - 8/5: Collaborative requirement analysis

**Work completed:** I collaborated with the team to analyze user roles such as Admin, Security Manager, Security Analyst, and Viewer. I focused on authentication, authorization, and how APIs should be protected by Cognito.

I also recorded the concrete checks I performed, the integration points I verified, and the issues I needed to report back to teammates. This made the entry reflect my own internship work instead of describing the whole project as if it was completed by one person.

**Knowledge gained:** I learned how to convert business requirements into technical functions, especially RBAC and secure API access.

**Result:** We produced an MVP requirement list and I identified the infrastructure items I needed to prepare.

**Difficulty and lesson:** The challenge was that security features could expand quickly. I learned to keep the MVP practical before adding advanced features.

## Day 3 - 9/5: Contributing to serverless architecture design

**Work completed:** I joined the architecture design work for IRMS. I proposed using CloudFront for frontend delivery, API Gateway as the entry point, Lambda for business logic, and DynamoDB for core data.

I also recorded the concrete checks I performed, the integration points I verified, and the issues I needed to report back to teammates. This made the entry reflect my own internship work instead of describing the whole project as if it was completed by one person.

**Knowledge gained:** I learned how serverless services work together and why this model fits a low-cost internship project.

**Result:** We had an initial architecture that the team could use to divide backend, frontend, and documentation tasks.

**Difficulty and lesson:** The lesson was that an architecture diagram must show service responsibilities, not only list AWS services.

## Day 4 - 10/5: Assisting DynamoDB data design

**Work completed:** I worked with teammates responsible for business logic to identify data for Incident, Timeline, Users, and EvidenceMetadata. My focus was checking how Lambda would read and write DynamoDB based on access patterns.

I also recorded the concrete checks I performed, the integration points I verified, and the issues I needed to report back to teammates. This made the entry reflect my own internship work instead of describing the whole project as if it was completed by one person.

**Knowledge gained:** I learned to design DynamoDB around access patterns instead of relational database habits.

**Result:** We produced a draft data model for API design and later Lambda implementation.

**Difficulty and lesson:** The challenge was balancing simplicity with dashboard query needs, so I documented items to test later.

## Day 5 - 11/5: API design contribution

**Work completed:** I participated in reviewing endpoints for incident, timeline, evidence, report, and alert flows. My individual focus was checking methods, paths, and how API Gateway would map requests to Lambda.

I also recorded the concrete checks I performed, the integration points I verified, and the issues I needed to report back to teammates. This made the entry reflect my own internship work instead of describing the whole project as if it was completed by one person.

**Knowledge gained:** I learned that a stable API contract helps backend and frontend work in parallel with fewer mismatches.

**Result:** We had an initial endpoint table and response convention for later API testing.

**Difficulty and lesson:** The lesson was to agree on naming early because changing paths after frontend integration costs time.

## Day 6 - 12/5: Preparing proposal content for my scope

**Work completed:** I worked with the team on the IRMS proposal. I wrote and reviewed the parts related to AWS architecture, service mapping, serverless deployment, and cloud operation flow.

I also recorded the concrete checks I performed, the integration points I verified, and the issues I needed to report back to teammates. This made the entry reflect my own internship work instead of describing the whole project as if it was completed by one person.

**Knowledge gained:** I learned how to present my technical contribution inside a shared team proposal.

**Result:** The proposal had clearer architecture and AWS service sections, which later supported the workshop documentation.

**Difficulty and lesson:** I needed to avoid writing as if one person did everything, so I adjusted the wording to reflect a team project.
