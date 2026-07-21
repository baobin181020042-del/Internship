---
title: "Blog 5"
date: 2026-06-03
weight: 5
chapter: false
pre: " <b> 3.5. </b> "
---

# B?o m?t Serverless Application v?i IAM v? Secrets Manager

## T?m t?t b?i d?ch

B?i blog n?y n?i v? c?c th?c h?nh b?o m?t trong serverless application, ??c bi?t l? least privilege IAM permission v? c?ch x? l? secret an to?n.

## ? ch?nh k? thu?t

- Lambda execution role ch? n?n c? nh?ng quy?n m? function th?t s? c?n.
- API key v? provider credential c?n l?u trong AWS Secrets Manager, kh?ng ?? trong frontend code ho?c Markdown.
- Log ph?i h? tr? debugging nh?ng kh?ng ???c l? token, password, presigned URL ho?c exception payload c? th?ng tin nh?y c?m.

## C?ch t?i ?p d?ng

N?i dung n?y r?t h?u ?ch cho ph?n AI Assistant c?a IRMS. T?i ghi r? Groq API key ???c l?u trong Secrets Manager, thay credential demo b?ng placeholder v? ki?m tra workshop kh?ng publish secret d?ng ???c.
