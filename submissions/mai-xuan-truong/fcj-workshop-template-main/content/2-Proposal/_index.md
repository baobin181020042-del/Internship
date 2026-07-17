---
title: "Proposal"
date: 2026-07-03
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

{{% notice warning %}}
⚠️ **Note:** The following information is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}

# IRMS — Incident Response Management System

## Project Proposal

### 1. Executive Summary

IRMS (Incident Response Management System) is a SaaS platform for managing and handling cybersecurity incidents, built entirely on AWS Serverless architecture. The project is implemented by a team of 5 members in the AWS internship program at FCAJ, with the goal of building a practical product that can be applied in enterprise environments.

The system helps Security teams standardize the full incident response workflow: detection, classification, assignment, investigation, evidence storage, and reporting. It replaces the current manual workflow using Email, Excel, Zalo, or informal chat channels. IRMS also integrates automated threat detection through Amazon GuardDuty and AI-assisted recommendations using Google Gemini API.

### 2. Problem Statement

In small and medium-sized businesses in Vietnam, when security incidents occur, such as a public S3 bucket, brute-force SSH attack, or phishing email, Security teams often handle them through informal channels like Email, Excel, Zalo, or Telegram.

This creates several practical issues: there is no centralized history for lookup, no clear way to track response progress, investigation evidence can be lost, and periodic reports are difficult to produce for risk assessment.

IRMS solves this problem by standardizing the whole process into a single web application, running on AWS with near-zero cost during the demo phase.

### 3. Solution Architecture

The system follows a Serverless-first model and does not use EC2, RDS, or VPC in order to optimize cost and reduce operational complexity.

![IRMS Solution Architecture](/images/2-Proposal/IRMS_architecture_v10.drawio.png)

#### Global/Edge Layer (outside Region)

- **Amazon Route 53**: DNS resolution.
- **Amazon CloudFront**: CDN for frontend distribution and the single entry point for all traffic.
- **AWS WAF**: Attached to CloudFront to inspect and block malicious requests before they reach the system.
- **Amazon S3 (Web Hosting)**: Stores the static React SPA, accessible only through CloudFront.

#### Regional — Authentication & Entry Layer

- **Amazon API Gateway**: REST API that receives all requests from CloudFront (`/api/*`).
- **Amazon Cognito**: Handles login, issues JWT tokens, and supports RBAC with 4 roles (Admin, Security Manager, Security Analyst, Auditor).

#### Regional — Compute Layer (5 Lambda functions)

- **Lambda Incident CRUD**: Creates, reads, updates, and assigns incidents.
- **Lambda Upload Evidence**: Handles evidence file uploads to S3.
- **Lambda Generate Report**: Aggregates data from DynamoDB and exports PDF/CSV reports.
- **Lambda Alert Handler**: Receives GuardDuty findings, auto-creates incidents, and sends notifications.
- **Lambda AI Assistant**: Calls Google Gemini API to suggest severity and response actions.

#### Regional — Data Layer

- **Amazon DynamoDB**: Stores Incidents, Timeline, Users, and EvidenceMetadata.
- **Amazon S3 (Evidence Store)**: Stores evidence files such as screenshots, logs, PCAP files, and PDF reports.

#### Regional — Security & Automation Layer

- **Amazon GuardDuty**: Automatically detects threats.
- **Amazon EventBridge**: Captures GuardDuty findings through rules and triggers Lambda Alert Handler; also runs the monthly report scheduler.
- **Amazon SNS**: Sends email notifications to Security Analysts when a new incident is created.
- **AWS Secrets Manager**: Stores the Gemini API key securely.

#### External Layer

- **Google Gemini API**: Analyzes incident descriptions and returns severity plus suggested actions. It is used instead of Bedrock due to intern account limitations.

### 4. Technical Implementation

**Frontend:** React 18 + TypeScript + Vite + TailwindCSS. Main screens include Dashboard, Incident List/Detail, Timeline, Evidence Upload, and Report View. The app is built as static assets, deployed to S3, and distributed through CloudFront.

**Backend:** Fully Serverless. The 5 Lambda functions are written in Python 3.12. Each function is independent and uses its own IAM Role with least-privilege permissions. The frontend communicates with the backend through API Gateway REST with JWT Authorizer.

**Infrastructure as Code:** AWS SAM (Serverless Application Model). All resources are defined in a YAML template and can be redeployed with a single `sam deploy` command.

**Source Control:** GitHub monorepo with the branching rule `main` → `develop` → `feature/<name>-<task>`. Pull requests must be reviewed before merging into `develop`.

**Team assignment:**

- **Member 1:** Frontend (React, Dashboard, UI).
- **Member 2:** Authentication (Cognito, API Gateway, RBAC).
- **Member 3:** Incident Core (Lambda CRUD, DynamoDB schema, Report).
- **Member 4:** Evidence & Storage (S3, Upload Lambda, Secrets Manager).
- **Member 5:** Security Automation & AI (GuardDuty, EventBridge, SNS, Alert Lambda, AI Assistant).

### 5. Timeline & Milestones

- **Week 1:** Set up shared AWS account, IAM users for each member, Budget Alert, SAM CLI, and GitHub repo structure. Member 2 sets up Cognito + API Gateway + 1 test Lambda and verifies JWT Authorizer. Member 3 designs DynamoDB schema and API spec.
- **Week 2:** Member 3 completes Incident CRUD Lambda. Member 1 builds the frontend and connects it to the real API. Internal demo: login → create incident → list incident end-to-end.
- **Week 3:** Member 4 completes Evidence Upload. Member 5 sets up GuardDuty + EventBridge + Lambda Alert Handler. Member 3 builds Generate Report.
- **Week 4:** Member 5 integrates AI Assistant (Gemini). Member 1 completes the full UI. Set up CloudFront + WAF. Run full end-to-end system testing.
- **Week 5+:** Write report, workshop, and blog. Fix bugs. Prepare mentor demo.

### 6. Budget Estimation

The Serverless architecture has no continuously running servers. All services are charged based on actual usage.

| Service | Estimated monthly cost |
| --- | --- |
| AWS Lambda | ~$0 (Free Tier: 1M requests/month) |
| API Gateway | ~$0-1 |
| DynamoDB | ~$0 (Free Tier: 25GB) |
| S3 (2 buckets) | ~$0-1 |
| CloudFront | ~$0-1 |
| Cognito | ~$0 (Free Tier: 50,000 MAU) |
| GuardDuty | ~$0 (30-day free trial) |
| EventBridge | ~$0 |
| SNS | ~$0 (Free Tier: 1M notifications) |
| Secrets Manager | ~$0.40/secret/month |
| **Total** | **~$0-5/month** |

An AWS Budget Alert has been configured at the $5 threshold to warn the team before costs exceed the expected budget.

### 7. Risk Assessment

**Risk 1: Amazon Bedrock is not available in the intern account**
Resolution: Use Google Gemini API instead (free tier: 1,500 requests/day, enough for demo). The API key is stored securely in Secrets Manager, and the AWS architecture remains unchanged.

**Risk 2: AWS cost exceeds budget**
Resolution: Configure a $5 Budget Alert, maximize Free Tier usage, and avoid EC2/RDS/NAT Gateway. Resources can be deleted after each test session when needed.

**Risk 3: Code conflicts when 5 members work together**
Resolution: Use a clear GitHub branching strategy (feature branch → develop → main), standardize the API spec from week 1, and keep each Lambda function independent.

**Risk 4: Team members are blocked by dependencies**
Resolution: Member 2 prioritizes Cognito + API Gateway + JWT Authorizer in week 1 because all Lambda functions depend on authentication. The frontend uses mock data early to avoid blocking.

**Risk 5: Personal AWS account and shared AWS account are mixed up**
Resolution: Each member configures 2 separate AWS CLI profiles (`irms-sandbox` for personal account and `irms-shared` for shared account), and always uses `--profile` when running commands.

### 8. Expected Outcomes

By the end of the project, the team will have a working IRMS system running on AWS with the following features:

- Login and RBAC authorization with 4 roles (Admin, Manager, Analyst, Auditor).
- Create, view, update, and assign incidents.
- Record investigation timeline step by step.
- Upload and manage evidence files.
- Automatically detect incidents from GuardDuty and send email notifications.
- AI-assisted severity and response action suggestions.
- Export periodic PDF/CSV reports.
