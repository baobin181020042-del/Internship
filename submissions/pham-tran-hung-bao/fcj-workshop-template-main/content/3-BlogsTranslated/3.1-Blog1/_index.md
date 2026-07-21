---
title: "Blog 1"
date: 2026-05-18
weight: 1
chapter: false
pre: " <b> 3.1. </b> "
---

{{% notice warning %}}
?? **Note:** The information below is for reference purposes only. Please **do not copy verbatim** for your report, including this warning.
{{% /notice %}}

# Getting Started with Healthcare Data Lakes: Using Microservices

## Translation Summary

This translated blog helped me understand why healthcare systems often split ingestion, validation, catalog, and processing logic into smaller microservices instead of putting everything into one large backend service.

## Main Technical Points

- A healthcare data lake needs clear boundaries between data ingestion, catalog management, and downstream processing.
- Amazon S3 can act as the storage layer, while DynamoDB stores metadata and Amazon SNS/EventBridge decouples communication between services.
- Microservices make the system easier to extend because a new connector can be added without changing every other service.

## How I Applied It

The most useful lesson for my IRMS project was the idea of decoupling. I later applied the same thinking when separating Incident CRUD, Evidence Upload, Report Generation, Alert Handler, and AI Assistant Lambda functions.
