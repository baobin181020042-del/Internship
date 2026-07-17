---
title: "Results, Cost Analysis, and Cleanup"
date: 2024-01-01
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---

## 7. Results, Cost Analysis, and Cleanup

#### Contents

- 5.7.13 Results, Cost Analysis, and Cleanup

### 5.7.13 Results, Cost Estimation and Resource Cleanup

#### 5.7.13.1 Project Results

After deployment and testing, the IRMS system completed the main functions planned for the workshop:

- User authentication with Amazon Cognito
- Incident management: create, update, delete, and view incidents
- Incident timeline tracking
- Evidence upload to Amazon S3
- AI-assisted incident analysis
- Report generation
- Dashboard monitoring
- HTTPS access through CloudFront
- Infrastructure as Code with AWS SAM

The whole system was deployed using a serverless architecture on AWS.

#### 5.7.13.2 AWS Services Used

| Service | Purpose |
| --- | --- |
| Amazon Cognito | Authentication |
| Amazon API Gateway | REST API |
| AWS Lambda | Business logic |
| Amazon DynamoDB | Incident database |
| Amazon S3 | Evidence storage and frontend hosting |
| Amazon CloudFront | CDN and HTTPS |
| Amazon EventBridge | Event trigger |
| Amazon SNS | Notification |
| AWS SAM | Infrastructure as Code |
| AWS IAM | Permission management |

#### 5.7.13.3 Cost Analysis

During development and deployment, the team used AWS Billing & Cost Management to monitor resource usage. The workload stayed within the AWS Free Tier for the demo scale, so the actual AWS charge was almost zero.

| AWS Service | Usage | Cost (USD) |
| --- | --- | --- |
| Amazon API Gateway | 35 requests | 0.00 |
| AWS Lambda | 33 invocations, 6.381 GB-seconds | 0.00 |
| Amazon DynamoDB | 36 read units, 25 write units | 0.00 |
| Amazon Cognito | 4 monthly active users (MAU) | 0.00 |
| Amazon S3 | 69 PUT/LIST, 280 GET requests | 0.00 |
| Amazon CloudWatch | Logs and metrics | 0.00 |
| Amazon EventBridge | 2 events | 0.00 |
| Amazon SNS | 22 requests | 0.00 |
| AWS CloudFormation | 66 operations | 0.00 |
| AWS X-Ray | 68 traces | 0.00 |
| AWS KMS | 2 requests | 0.00 |

The project also used AWS Secrets Manager to store the Groq API key. No API key exists in the frontend.

| Service | Usage | Cost |
| --- | --- | --- |
| AWS Secrets Manager | 1 secret | USD 0.02 |

This cost was fully offset by AWS Free Tier credit, so the final amount paid remained USD 0.00.

#### 5.7.13.4 AI Service Cost

The final implementation uses Groq for development and demo AI workloads.

| Item | Value |
| --- | --- |
| Current provider | Groq |
| Model | `llama-3.1-8b-instant` |
| Cost model used | Groq Free Tier for development/demo |
| Future optional provider | Amazon Bedrock |

In this project:

- Only a small number of incident analysis, explain, and chat requests were sent.
- No model training was performed.
- No large-volume data processing was performed.
- If Groq is unavailable, the Lambda returns a rule-based fallback response.

AWS costs remain dominated by Lambda, API Gateway, CloudFront, S3, DynamoDB, and Secrets Manager. Amazon Bedrock would incur inference charges only if it is enabled in a future version.

#### 5.7.13.5 Total Project Cost

| Category | Cost |
| --- | --- |
| AWS Services | USD 0.00 |
| AWS Secrets Manager | USD 0.02, offset by Free Tier credit |
| Groq API | USD 0.00, Free Tier for development/demo |
| Amazon Bedrock | USD 0.00, not enabled |

```text
Actual AWS Charge     : USD 0.00
Free Tier Credit Used : USD 0.02
Final Amount Paid     : USD 0.00
```

The system was deployed and operated successfully without a final payable charge by using AWS Free Tier and the Groq Free Tier effectively.

#### 5.7.13.6 Resource Cleanup

After completing the workshop and evaluation, clean up resources to avoid unexpected cost.

Recommended cleanup order:

1. Disable and delete the old CloudFront distribution if it is no longer needed.
2. Delete the CloudFormation stack.

```bash
aws cloudformation delete-stack \
  --stack-name irms-serverless \
  --region ap-southeast-1 \
  --profile irms-shared
```

3. Check and delete any remaining resources:

- Amazon S3 frontend bucket, after backing up required files
- Amazon S3 evidence bucket, after backing up required data
- Lambda functions, if they were not removed with the stack
- API Gateway, if it was not removed with the stack
- DynamoDB tables, if they were not removed with the stack
- SNS topic
- EventBridge rules
- IAM roles created specifically for the project
- Secrets Manager secret for the Groq API key

Keep the Amazon Cognito User Pool only if there is a plan to continue development or reuse it for a later version.
