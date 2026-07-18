---
title: "Kết quả, chi phí và dọn dẹp"
date: 2026-07-17
weight: 7
chapter: false
pre: " <b> 5.7. </b> "
---

## 7. Kết quả, chi phí và dọn dẹp

#### Nội dung

- 5.7.13 Kết quả, chi phí & dọn dẹp

### 5.7.13 Results, Cost Estimation and Resource Cleanup

#### 5.7.13.1 Project Results
Sau khi hoàn thành triển khai, hệ thống đạt được các chức năng chính:
- ✅ User Authentication (Amazon Cognito)
- ✅ Incident Management
- Create
- Update
- Delete
- View
- ✅ Incident Timeline
- ✅ Evidence Upload
- ✅ AI Incident Analysis
- ✅ Report Generation
- ✅ Dashboard Monitoring
- ✅ HTTPS Deployment
- ✅ Infrastructure as Code
Toàn bộ hệ thống được triển khai theo kiến trúc Serverless trên AWS.

#### 5.7.13.2 AWS Services Used

| Service | Purpose |
| --- | --- |
| Amazon Cognito | Authentication |
| Amazon API Gateway | REST API |
| AWS Lambda | Business Logic |
| Amazon DynamoDB | Incident Database |
| Amazon S3 | Evidence + Frontend |
| Amazon CloudFront | CDN + HTTPS |
| Amazon EventBridge | Event Trigger |
| Amazon SNS | Notification |
| AWS SAM | Infrastructure as Code |
| AWS IAM | Permission Management |

#### 5.7.13.3 Cost Analysis
Trong quá trình phát triển và triển khai hệ thống, nhóm sử dụng AWS Billing & Cost Management để theo dõi mức sử dụng tài nguyên. Toàn bộ dịch vụ được triển khai trong AWS Free Tier, do đó chi phí phát sinh gần như bằng 0 USD.
Bảng dưới đây tổng hợp mức sử dụng chính của các dịch vụ.

| AWS Service | Usage | Cost (USD) |
| --- | --- | --- |
| Amazon API Gateway | 35 Requests | 0.00 |
| AWS Lambda | 33 Invocations, 6.381 GB-Seconds | 0.00 |
| Amazon DynamoDB | 36 Read Units, 25 Write Units | 0.00 |
| Amazon Cognito | 4 Monthly Active Users (MAU) | 0.00 |
| Amazon S3 | 69 PUT/LIST, 280 GET Requests | 0.00 |
| Amazon CloudWatch | Logs & Metrics | 0.00 |
| Amazon EventBridge | 2 Events | 0.00 |
| Amazon SNS | 22 Requests | 0.00 |
| AWS CloudFormation | 66 Operations | 0.00 |
| AWS X-Ray | 68 Traces | 0.00 |
| AWS KMS | 2 Requests | 0.00 |

Secrets Manager
Dự án sử dụng AWS Secrets Manager để lưu Groq API key. Frontend không chứa API key.

| Service | Usage | Cost |
| --- | --- | --- |
| AWS Secrets Manager | 1 Secret | USD 0.02 |

Giá trị này được ghi nhận như một yếu tố chi phí nhỏ ở quy mô demo. Chi phí thực tế phụ thuộc account, region, thời gian lưu và tài nguyên còn hoạt động sau khi test.

#### 5.7.13.4 AI Service Cost

Final implementation sử dụng Groq cho workload AI trong giai đoạn development/demo.

| Hạng mục | Giá trị |
| --- | --- |
| Provider hiện tại | Groq |
| Model | `llama-3.1-8b-instant` |
| Cost model | Groq Free Tier cho development/demo |
| Provider tương lai | Amazon Bedrock |

Trong phạm vi dự án:

- Chỉ gửi số lượng nhỏ request cho incident analysis, explain và chat.
- Không huấn luyện model.
- Không xử lý dữ liệu dung lượng lớn.
- Nếu Groq không khả dụng, Lambda trả về rule-based fallback response.

Chi phí AWS chủ yếu đến từ Lambda, API Gateway, CloudFront, S3, DynamoDB và Secrets Manager. Amazon Bedrock chỉ phát sinh inference charge nếu được bật trong phiên bản tương lai.

#### 5.7.13.5 Total Project Cost

| Category | Cost |
| --- | --- |
| AWS Services | USD 0.00 |
| AWS Secrets Manager | Chi phí nhỏ theo số lượng secret/tháng |
| Groq API | USD 0.00, Free Tier cho development/demo |
| Amazon Bedrock | USD 0.00, chưa bật |

```text
Primary AWS cost drivers : Lambda, API Gateway, CloudFront, S3, DynamoDB, Secrets Manager, CloudWatch
Current AI provider      : Groq cho development/demo
Future AI provider       : Amazon Bedrock nếu được bật sau này
```

Demo được giữ ở mức cost-aware bằng serverless services, kiểm tra tài nguyên đang chạy và cleanup tài nguyên không còn cần thiết.

#### 5.7.13.6 Resource Cleanup
Sau khi hoàn thành workshop hoặc quá trình đánh giá, cần dọn dẹp tài nguyên để tránh phát sinh chi phí ngoài ý muốn.
Khuyến nghị thực hiện theo thứ tự sau:
- Xóa CloudFront Distribution cũ (nếu còn).
- Xóa CloudFormation Stack:
aws cloudformation delete-stack \
--stack-name irms-serverless \
--region ap-southeast-1 \
--profile irms-shared
- Kiểm tra và xóa các tài nguyên còn sót:
- Amazon S3 Frontend Bucket (sau khi sao lưu nếu cần)
- Amazon S3 Evidence Bucket (sau khi sao lưu dữ liệu)
- Lambda Functions (nếu không bị xóa cùng stack)
- API Gateway (nếu không bị xóa cùng stack)
- DynamoDB Tables (nếu không bị xóa cùng stack)
- SNS Topic
- EventBridge Rules
- IAM Roles do dự án tạo riêng
- Secrets Manager Secret chứa Groq API key
- Chỉ giữ lại Amazon Cognito User Pool nếu có kế hoạch tiếp tục phát triển hoặc tái sử dụng cho các phiên bản sau.
