---
title: "Tuần 11"
date: 2026-06-29
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

**Mốc thời gian:** 29/6 → 3/7 (5 ngày làm việc)

> Dự án IRMS được thực hiện bởi nhóm 5 thành viên. Các ghi chú dưới đây tập trung vào phần đóng góp cá nhân của tôi trong quá trình phối hợp với nhóm.

## Ngày 1 - 29/6: Bắt đầu dự án IRMS

**Công việc đã thực hiện:** Tôi tham gia buổi thảo luận nhóm để chính thức bắt tay vào dự án IRMS. Cả nhóm thống nhất phạm vi hệ thống quản lý sự cố an toàn thông tin, còn phần tôi tập trung là hạ tầng AWS, luồng triển khai và cách tài liệu hóa thành workshop.

Tôi rà lại các yêu cầu chính như quản lý incident, timeline, evidence upload, report generation và alert handling. Sau đó tôi ghi lại các dịch vụ AWS cần dùng gồm Cognito, API Gateway, Lambda, DynamoDB, S3 Evidence Store, EventBridge, SNS, Secrets Manager, CloudWatch và CloudFront. Tôi cũng xác định phần nào bản thân chịu trách nhiệm chính, phần nào cần phối hợp với frontend/backend teammate.

**Kiến thức đã học:** Một dự án nhóm cần chốt phạm vi và ranh giới trách nhiệm sớm, nếu không tài liệu và triển khai sẽ rất dễ lệch nhau.

**Kết quả đạt được:** Nhóm có hướng triển khai rõ hơn, còn tôi có checklist AWS infrastructure và documentation để theo dõi trong các ngày tiếp theo.

**Khó khăn và bài học:** Ban đầu có nhiều ý tưởng mở rộng, nhưng cần ưu tiên phần cốt lõi để kịp tiến độ thực tập.

## Ngày 2 - 30/6: Phân tích yêu cầu và phân công kỹ thuật

**Công việc đã thực hiện:** Tôi cùng nhóm phân tích các use case chính của IRMS và tách thành các luồng nhỏ để triển khai. Phần tôi tham gia sâu gồm xác thực người dùng bằng Cognito, route API qua API Gateway, xử lý nghiệp vụ bằng Lambda và lưu dữ liệu vào DynamoDB.

Tôi hỗ trợ mô tả luồng dữ liệu cho Incident CRUD, Timeline, Evidence Upload và Report Generation. Với từng luồng, tôi ghi lại input, output, dịch vụ AWS liên quan và các điểm cần kiểm thử. Tôi cũng trao đổi với teammate phụ trách frontend để thống nhất các endpoint cần expose, format response và cách frontend gửi JWT trong Authorization header.

**Kiến thức đã học:** Khi làm serverless, API contract rất quan trọng vì frontend, Lambda và DynamoDB đều phụ thuộc vào cùng một cấu trúc dữ liệu.

**Kết quả đạt được:** Các nhóm việc được tách rõ hơn, giúp tôi chuẩn bị template SAM và tài liệu workshop sát với luồng triển khai thật.

**Khó khăn và bài học:** Một số yêu cầu ban đầu còn chung chung, nên cần hỏi lại và ghi thành checklist cụ thể thay vì hiểu theo cảm tính.

## Ngày 3 - 1/7: Chốt kiến trúc tổng thể

**Công việc đã thực hiện:** Tôi tập trung vào sơ đồ kiến trúc và luồng request từ React frontend đến các dịch vụ backend. Cả nhóm thống nhất hướng serverless: frontend dùng React + Vite, hosting qua S3/CloudFront; backend dùng API Gateway, Cognito Authorizer, Lambda và DynamoDB; evidence lưu trên S3 bằng presigned URL.

Tôi kiểm tra các điểm kết nối giữa GuardDuty, EventBridge, Lambda Alert Handler và SNS để đảm bảo phần cảnh báo được mô tả đúng. Với AI Assistant, tôi ghi rõ việc Lambda đọc secret từ Secrets Manager rồi gọi Groq API, tránh đưa API key ra frontend hoặc tài liệu công khai. Tôi cũng cập nhật ghi chú để phân biệt phần đã triển khai và phần future enhancement.

**Kiến thức đã học:** Kiến trúc không chỉ là sơ đồ, mà phải khớp với cách request, credential, log và dữ liệu thật di chuyển trong hệ thống.

**Kết quả đạt được:** Kiến trúc IRMS được chốt để dùng thống nhất trong Proposal, Workshop và Worklog.

**Khó khăn và bài học:** Nếu không thống nhất tên dịch vụ và hướng mũi tên từ đầu, các trang tài liệu sau đó rất dễ bị mâu thuẫn.

## Ngày 4 - 2/7: Chuẩn bị AWS SAM và hạ tầng

**Công việc đã thực hiện:** Tôi bắt đầu chuẩn bị cấu trúc AWS SAM cho phần hạ tầng backend. Các tài nguyên được rà theo nhóm: Cognito cho authentication, API Gateway cho REST API, Lambda cho nghiệp vụ, DynamoDB cho incident/timeline/user/evidence metadata, S3 cho evidence và EventBridge/SNS cho alert.

Tôi chạy kiểm tra template bằng `sam validate`, xem lại IAM role của Lambda và đối chiếu environment variables như table name, bucket name, secret name và AI provider. Tôi cũng ghi lại các bước cần đưa vào workshop, gồm cài AWS CLI/SAM CLI, cấu hình profile, build, validate và deploy.

```bash
sam validate
sam build
sam deploy --guided
```

**Kiến thức đã học:** SAM giúp gom hạ tầng thành code, nhưng cần đặt tên biến và quyền IAM rõ ràng để tránh lỗi khi deploy.

**Kết quả đạt được:** Có nền tảng hạ tầng ban đầu để nhóm tiếp tục triển khai Lambda và kiểm thử API.

**Khó khăn và bài học:** Lỗi nhỏ trong template hoặc quyền IAM có thể làm deploy thất bại, nên cần validate sớm thay vì chờ đến cuối.

## Ngày 5 - 3/7: Đồng bộ tài liệu ban đầu

**Công việc đã thực hiện:** Tôi bắt đầu đồng bộ Proposal và Workshop với kiến trúc IRMS đã thống nhất. Trọng tâm là giữ cho phần tiếng Việt và tiếng Anh có cùng nội dung, chỉ khác ngôn ngữ trình bày. Tôi rà lại mục Introduction, Environment Setup và Infrastructure Configuration để tránh tình trạng nội dung song ngữ bị lệch.

Tôi cũng ghi lại các điểm cần tiếp tục kiểm tra ở tuần sau như Cognito JWT, API Gateway CORS, Lambda log, DynamoDB key design, S3 presigned URL và CloudFront deployment. Những phần chưa kiểm thử xong được đánh dấu là cần xác nhận, tránh viết như đã hoàn thành hoàn toàn.

**Kiến thức đã học:** Tài liệu kỹ thuật nên được cập nhật song song với quá trình làm dự án, vì nếu để dồn cuối kỳ sẽ rất khó nhớ đúng lỗi và cách xử lý.

**Kết quả đạt được:** Worklog, Proposal và Workshop bắt đầu đi theo cùng một timeline dự án từ tuần có ngày 01/07.

**Khó khăn và bài học:** Cần viết theo đóng góp cá nhân trong nhóm 5 người, không trình bày như một mình hoàn thành toàn bộ hệ thống.
