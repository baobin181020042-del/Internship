---
title: "Week 2 Worklog"
date: 2026-04-26
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---
{{% notice warning %}}
⚠️ **Note:** The following information is for reference only. Please **do not copy verbatim** for your own report, including this warning.
{{% /notice %}}

### Week 2 Objectives (26/04/2026 - 30/04/2026):

* Strengthen AWS fundamentals across IAM, EC2, VPC, RDS, CloudWatch, CLI, Backup, and migration.
* Practice end-to-end implementation with security and cost awareness.
* Build operational mindset: monitoring, alerting, backup/restore, and cleanup discipline.

### Daily Worklog:

| Day | Activities | Outcome |
| --- | --- | --- |
| **26/04/2026** | IAM lab (User, Group, Policy, Role), detailed EC2 learning, plus VPC & Site-to-Site VPN workshop. | Built strong base on access control and cloud network architecture. |
| **27/04/2026** | RDS workshop (deploy app with RDS endpoint, snapshot/restore) and AWS Budgets workshop. | Connected app to managed DB and improved cost governance skills. |
| **28/04/2026** | CloudWatch workshop (Metrics, Logs, Insights, Alarms, Dashboard) and Hybrid DNS with Route 53 Resolver. | Completed full monitoring flow and understood enterprise DNS integration model. |
| **29/04/2026** | AWS CLI workshop (EC2/S3/SNS/IAM/VPC via commands) and AWS Backup workshop (backup plan, vault notifications, restore test with Lambda). | Improved CLI productivity and learned practical backup/restore validation workflow. |
| **30/04/2026** | VM Import/Export workshop and Docker application deployment workshop (image build, compose, ECR/Docker Hub). | Understood two-way VM migration and containerized deployment pattern on AWS. |

### Key Difficulties:

* Initially confused between IAM Role and IAM User usage contexts.
* Not fully comfortable with IAM Policy JSON design at first.
* Networking workshops (VPC/VPN/Hybrid DNS) had many dependent steps and were easy to misconfigure.
* Risk of leftover resources in non-default regions causing unexpected charges.
* CLI parameter/ARN usage was error-prone in early attempts.

### How I Addressed Them:

* Broke each workshop into strict step-by-step checklists.
* Used CloudWatch logs and Reachability Analyzer for structured troubleshooting.
* Applied immediate cleanup after each lab and cross-region resource checks.
* Configured multi-threshold AWS Budgets alerts (50/80/100).
* Kept reusable CLI command notes and profile-based configuration.

### Week 2 Achievements:

* Completed major practical workshops scheduled for the week.
* Improved hands-on capability in infrastructure, monitoring, backup, and automation.
* Strengthened IAM security mindset and cloud cost control habits.
* Increased confidence moving from console-based workflows to CLI-driven operations.

### Lessons Learned:

* IAM understanding is foundational before scaling to advanced AWS services.
* Monitoring and backup are only meaningful when restore is regularly tested.
* Cost control must run in parallel with technical implementation from day one.
* A standard workflow (deploy -> validate -> cleanup) reduces operational risk significantly.
