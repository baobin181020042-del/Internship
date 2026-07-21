---
title: "Blog 5"
date: 2026-06-03
weight: 5
chapter: false
pre: " <b> 3.5. </b> "
---

{{% notice warning %}}
?? **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}

# Securing Serverless Applications with IAM and Secrets Manager

## Translation Summary

This translated blog covered common security practices for serverless applications, especially least privilege IAM permissions and safe secret handling.

## Main Technical Points

- Lambda execution roles should grant only the actions required by each function.
- API keys and provider credentials should be stored in AWS Secrets Manager, not in frontend code or Markdown files.
- Logs should help debugging without exposing tokens, passwords, presigned URLs, or full exception payloads containing sensitive values.

## How I Applied It

This was useful for the AI Assistant part of IRMS. I documented Groq API key storage in Secrets Manager, replaced active demo credentials with placeholders, and checked that workshop examples do not publish reusable secrets.
