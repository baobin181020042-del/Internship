---
title: "Blog 2"
date: 2026-05-21
weight: 2
chapter: false
pre: " <b> 3.2. </b> "
---

{{% notice warning %}}
?? **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}

# Using Amazon Cognito and ABAC for Healthcare Data Access

## Translation Summary

This translated blog focused on authentication and authorization for sensitive data. I used it to strengthen my understanding of Amazon Cognito, identity claims, user groups, and attribute-based access control.

## Main Technical Points

- Amazon Cognito can issue JWT tokens that backend services use to identify the current user.
- Groups and claims help keep authorization logic explicit instead of hardcoding permissions in the frontend.
- ABAC is useful when access decisions depend on attributes such as department, role, or data classification.

## How I Applied It

The blog was directly useful for IRMS because our system also required role-based access for Admin, Manager, Analyst, and Auditor users. It helped me explain why Cognito authorizer validation belongs at API Gateway and Lambda, not only in the UI.
