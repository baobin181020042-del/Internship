---
title: "Blog 6"
date: 2026-06-08
weight: 6
chapter: false
pre: " <b> 3.6. </b> "
---

{{% notice warning %}}
?? **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}

# Monitoring and Cost Awareness for Serverless Projects

## Translation Summary

This translated blog focused on operating a small AWS workload responsibly by checking logs, metrics, and cost drivers during development.

## Main Technical Points

- CloudWatch Logs are important for debugging Lambda and API Gateway integration issues.
- Serverless projects can still create cost through API requests, storage, logs, CloudFront traffic, and unmanaged resources.
- Cleanup steps should be documented before the final demo so temporary resources do not remain active by mistake.

## How I Applied It

The lesson carried into the final IRMS documentation. I added cost-driver wording for Lambda, API Gateway, CloudFront, S3, DynamoDB, Secrets Manager, and CloudWatch, and treated cleanup as part of the workshop rather than an afterthought.
