---
title: "Bản đề xuất"
date: 2026-07-03
weight: 2
chapter: false
pre: " <b> 2. </b> "
---

{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

# IRMS — Incident Response Management System

## Project Proposal

### 1. Executive Summary

IRMS (Incident Response Management System) là hệ thống quản lý và xử lý sự cố an ninh mạng dạng SaaS, được xây dựng hoàn toàn trên kiến trúc Serverless AWS. Dự án được thực hiện bởi nhóm 5 thành viên trong chương trình thực tập AWS tại FCAJ, với mục tiêu xây dựng một sản phẩm thực tế có thể áp dụng vào môi trường doanh nghiệp.

Hệ thống cho phép đội ngũ Security chuẩn hóa toàn bộ quy trình xử lý sự cố: từ phát hiện, phân loại, phân công, điều tra, lưu trữ bằng chứng đến xuất báo cáo, thay thế cách làm thủ công qua Email, Excel, Zalo hiện tại. Ngoài ra, IRMS tích hợp khả năng tự động phát hiện mối đe dọa qua Amazon GuardDuty và hỗ trợ gợi ý xử lý bằng AI (Google Gemini API).

### 2. Problem Statement

Trong các doanh nghiệp vừa và nhỏ tại Việt Nam, khi xảy ra sự cố bảo mật như S3 bucket bị public, server bị brute force SSH, hay nhân viên nhận email phishing, đội Security thường xử lý qua các kênh không chính thức: Email, Excel, Zalo, Telegram.

Hậu quả thực tế là không có lịch sử tập trung để tra cứu, không theo dõi được tiến độ xử lý, bằng chứng điều tra dễ bị thất lạc, và không có báo cáo thống kê định kỳ để đánh giá rủi ro.

IRMS giải quyết vấn đề này bằng cách chuẩn hóa toàn bộ quy trình thành một web application duy nhất, vận hành trên AWS với chi phí gần bằng 0 trong giai đoạn demo.

### 3. Solution Architecture

Hệ thống được xây dựng theo mô hình Serverless-first, không sử dụng EC2, RDS hay VPC để tối ưu chi phí và giảm độ phức tạp vận hành.

![IRMS Solution Architecture](/images/2-Proposal/IRMS_architecture_v10.drawio.png)

#### Lớp Global/Edge (ngoài Region)

- **Amazon Route 53**: Phân giải DNS.
- **Amazon CloudFront**: CDN phân phối frontend, cổng vào duy nhất cho toàn bộ traffic.
- **AWS WAF**: Gắn vào CloudFront, kiểm tra và chặn request độc hại trước khi vào hệ thống.
- **Amazon S3 (Web Hosting)**: Lưu React SPA tĩnh, chỉ truy cập qua CloudFront.

#### Lớp Regional — Xác thực & Entry

- **Amazon API Gateway**: REST API, nhận toàn bộ request từ CloudFront (`/api/*`).
- **Amazon Cognito**: Quản lý đăng nhập, phát hành JWT token, RBAC theo 4 vai trò (Admin, Security Manager, Security Analyst, Auditor).

#### Lớp Regional — Compute (5 Lambda function)

- **Lambda Incident CRUD**: Tạo, đọc, cập nhật, phân công Incident.
- **Lambda Upload Evidence**: Xử lý upload file bằng chứng lên S3.
- **Lambda Generate Report**: Tổng hợp dữ liệu từ DynamoDB, xuất PDF/CSV.
- **Lambda Alert Handler**: Nhận finding từ GuardDuty, tạo Incident tự động, gửi thông báo.
- **Lambda AI Assistant**: Gọi Google Gemini API, gợi ý severity và hành động xử lý.

#### Lớp Regional — Data

- **Amazon DynamoDB**: Lưu Incidents, Timeline, Users, EvidenceMetadata.
- **Amazon S3 (Evidence Store)**: Lưu file bằng chứng như screenshot, log, PCAP, PDF report.

#### Lớp Regional — Security & Automation

- **Amazon GuardDuty**: Tự động phát hiện mối đe dọa.
- **Amazon EventBridge**: Bắt finding từ GuardDuty theo rule, kích hoạt Lambda Alert Handler; đồng thời chạy scheduler sinh báo cáo hàng tháng.
- **Amazon SNS**: Gửi thông báo email cho Security Analyst khi có Incident mới.
- **AWS Secrets Manager**: Lưu trữ Gemini API Key an toàn.

#### Lớp External

- **Google Gemini API**: AI phân tích mô tả sự cố, trả về severity và suggested actions. Dịch vụ này được dùng thay Bedrock do giới hạn account intern.

### 4. Technical Implementation

**Frontend:** React 18 + TypeScript + Vite + TailwindCSS. Gồm Dashboard, Incident List/Detail, Timeline, Evidence Upload, Report View. Build tĩnh, deploy lên S3, phân phối qua CloudFront.

**Backend:** Hoàn toàn Serverless. 5 Lambda function viết bằng Python 3.12, mỗi function độc lập, có IAM Role riêng với quyền tối thiểu (least-privilege). Giao tiếp với frontend qua API Gateway REST với JWT Authorizer.

**Infrastructure as Code:** AWS SAM (Serverless Application Model). Toàn bộ resource được định nghĩa trong template YAML, có thể deploy lại hoàn toàn bằng một lệnh `sam deploy`.

**Source Control:** GitHub monorepo, phân nhánh theo quy tắc `main` → `develop` → `feature/<tên>-<task>`. PR cần review trước khi merge vào `develop`.

**Phân công nhóm:**

- **Thành viên 1:** Frontend (React, Dashboard, UI).
- **Thành viên 2:** Authentication (Cognito, API Gateway, RBAC).
- **Thành viên 3:** Incident Core (Lambda CRUD, DynamoDB schema, Report).
- **Thành viên 4:** Evidence & Storage (S3, Upload Lambda, Secrets Manager).
- **Thành viên 5:** Security Automation & AI (GuardDuty, EventBridge, SNS, Alert Lambda, AI Assistant).

### 5. Timeline & Milestones

- **Tuần 1:** Setup AWS account chung, IAM users cho từng thành viên, Budget Alert, SAM CLI, cấu trúc GitHub repo. Thành viên 2 setup Cognito + API Gateway + 1 Lambda test, xác nhận JWT Authorizer hoạt động. Thành viên 3 thiết kế DynamoDB schema và API spec.
- **Tuần 2:** Thành viên 3 hoàn thiện Lambda CRUD Incident. Thành viên 1 build Frontend kết nối API thật. Demo nội bộ: login → tạo incident → list incident chạy end-to-end.
- **Tuần 3:** Thành viên 4 hoàn thiện Upload Evidence. Thành viên 5 setup GuardDuty + EventBridge + Lambda Alert Handler. Thành viên 3 làm Generate Report.
- **Tuần 4:** Thành viên 5 integrate AI Assistant (Gemini). Thành viên 1 hoàn thiện UI toàn bộ. Setup CloudFront + WAF. Test end-to-end toàn hệ thống.
- **Tuần 5+:** Viết báo cáo, workshop, blog. Fix bug phát sinh. Chuẩn bị demo cho mentor.

### 6. Budget Estimation

Kiến trúc Serverless không có server chạy liên tục, toàn bộ chỉ tính theo lượt sử dụng thực tế.

| Dịch vụ | Chi phí ước tính/tháng |
| --- | --- |
| AWS Lambda | ~$0 (Free Tier: 1M request/tháng) |
| API Gateway | ~$0-1 |
| DynamoDB | ~$0 (Free Tier: 25GB) |
| S3 (2 bucket) | ~$0-1 |
| CloudFront | ~$0-1 |
| Cognito | ~$0 (Free Tier: 50,000 MAU) |
| GuardDuty | ~$0 (30 ngày free trial) |
| EventBridge | ~$0 |
| SNS | ~$0 (Free Tier: 1M notification) |
| Secrets Manager | ~$0.40/secret/tháng |
| **Tổng** | **~$0-5/tháng** |

Đã setup AWS Budget Alert ngưỡng $5 để cảnh báo trước khi vượt chi phí.

### 7. Risk Assessment

**Rủi ro 1: Amazon Bedrock không available ở account intern**
Đã giải quyết: thay bằng Google Gemini API (free tier 1,500 request/ngày, đủ cho demo). API key lưu an toàn trong Secrets Manager, kiến trúc AWS không thay đổi.

**Rủi ro 2: Chi phí AWS vượt ngân sách**
Đã giải quyết: setup Budget Alert $5, dùng Free Tier tối đa, không deploy EC2/RDS/NAT Gateway. Chủ động xóa resource sau mỗi buổi test nếu cần.

**Rủi ro 3: Conflict code khi 5 người cùng làm**
Đã giải quyết: GitHub branching strategy rõ ràng (feature branch → develop → main), API spec thống nhất từ tuần 1, mỗi Lambda function hoàn toàn độc lập không phụ thuộc code của người khác.

**Rủi ro 4: Thành viên bị block vì phụ thuộc nhau**
Đã giải quyết: Thành viên 2 ưu tiên xong Cognito + API Gateway + JWT Authorizer trong tuần 1 vì mọi Lambda đều phụ thuộc vào đây. Frontend dùng mock data trong giai đoạn đầu để không bị block.

**Rủi ro 5: Account AWS cá nhân bị lẫn với account chung**
Đã giải quyết: mỗi người cấu hình 2 AWS CLI profile riêng (`irms-sandbox` cho account cá nhân, `irms-shared` cho account chung), luôn chỉ định `--profile` khi chạy lệnh.

### 8. Expected Outcomes

Kết thúc dự án, nhóm sẽ có một hệ thống IRMS chạy thật trên AWS với đầy đủ các chức năng:

- Đăng nhập, phân quyền theo 4 role (Admin, Manager, Analyst, Auditor).
- Tạo, xem, cập nhật, phân công Incident.
- Ghi lại Timeline điều tra từng bước.
- Upload và quản lý Evidence (file bằng chứng).
- Tự động phát hiện sự cố từ GuardDuty và gửi thông báo qua email.
- AI gợi ý mức độ nghiêm trọng và hành động xử lý.
- Xuất báo cáo PDF/CSV định kỳ.
