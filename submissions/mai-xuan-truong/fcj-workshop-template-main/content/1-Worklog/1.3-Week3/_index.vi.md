---
title: "Tuần 3"
date: 2026-05-04
weight: 3
chapter: false
pre: " <b> 1.3. </b> "
---

**Mốc thời gian:** 4/5 → 8/5 (5 ngày làm việc)

## Ngày 1 - 1/5: Workshop ECS

**Công việc đã thực hiện:** Làm workshop Deploy Applications on Amazon ECS để hiểu cách triển khai ứng dụng container trên AWS.

**Kiến thức đã học:** Học về cluster, task definition, service, Fargate và cách ECS tự duy trì số lượng task đang chạy.

**Kết quả đạt được:** Hiểu sự khác nhau giữa chạy Docker thủ công và để AWS quản lý vòng đời container.

**Khó khăn và bài học:** Nhiều khái niệm ECS liên kết với nhau. Bài học là cần đọc task definition trước rồi mới phân tích service/deployment.

## Ngày 2 - 2/5: Tìm hiểu Fargate và ALB

**Công việc đã thực hiện:** Tiếp tục phần ECS với Fargate, Application Load Balancer và chiến lược rolling deployment.

**Kiến thức đã học:** Hiểu Fargate giúp không phải quản lý EC2 bên dưới, còn ALB phân phối traffic đến các task khỏe mạnh.

**Kết quả đạt được:** Nắm được cách triển khai ứng dụng container theo hướng ít vận hành hơn.

**Khó khăn và bài học:** Khó khăn là cấu hình network/security group cho ALB và task. Bài học là cần kiểm tra subnet, listener và target group cùng lúc.

## Ngày 3 - 3/5: So sánh container và serverless

**Công việc đã thực hiện:** So sánh hướng triển khai bằng ECS/Fargate với hướng serverless dùng Lambda, API Gateway và DynamoDB.

**Kiến thức đã học:** Hiểu container phù hợp khi cần kiểm soát runtime, còn serverless phù hợp cho API/event-driven workload ít vận hành.

**Kết quả đạt được:** Có cơ sở để cân nhắc kiến trúc cho đề tài internship sau này.

**Khó khăn và bài học:** Khó khăn là mỗi mô hình có ưu/nhược điểm riêng. Bài học là chọn kiến trúc theo yêu cầu, không chọn theo cảm tính.

## Ngày 4 - 4/5: Ôn API Gateway và Lambda

**Công việc đã thực hiện:** Ôn lại cách API Gateway nhận request và gọi Lambda để xử lý nghiệp vụ. Đây là phần nền tảng cho dự án IRMS.

**Kiến thức đã học:** Hiểu request/response flow, status code, integration và vai trò của Lambda environment variables.

**Kết quả đạt được:** Chuẩn bị được nền kiến thức để thiết kế API CRUD cho incident.

**Khó khăn và bài học:** Khó khăn là dễ nhầm giữa route, method và integration. Bài học là nên lập bảng endpoint trước khi cấu hình.

## Ngày 5 - 5/5: Rà soát chi phí sau lab

**Công việc đã thực hiện:** Kiểm tra lại các tài nguyên đã tạo trong quá trình lab ECS, EC2 và các dịch vụ liên quan để tránh để sót tài nguyên chạy nền.

**Kiến thức đã học:** Học cách kiểm tra region, CloudWatch log, load balancer, NAT Gateway và các tài nguyên có thể phát sinh chi phí.

**Kết quả đạt được:** Dọn dẹp các tài nguyên không cần dùng và ghi chú lại checklist cleanup.

**Khó khăn và bài học:** Một số dịch vụ tạo tài nguyên phụ. Bài học là sau khi deploy phải kiểm tra cả tài nguyên được tạo gián tiếp.

## Ngày 6 - 6/5: Chuẩn bị chọn đề tài

**Công việc đã thực hiện:** Tổng hợp kiến thức ba tuần đầu và bắt đầu suy nghĩ về đề tài có thể triển khai trên AWS, vừa đủ thực tế vừa phù hợp thời gian thực tập.

**Kiến thức đã học:** Nhận ra đề tài cần có kiến trúc rõ, nhiều dịch vụ AWS liên kết và có thể trình bày thành workshop từng bước.

**Kết quả đạt được:** Hình thành hướng đi ban đầu cho hệ thống quản lý sự cố an ninh mạng.

**Khó khăn và bài học:** Khó khăn là phạm vi đề tài dễ quá rộng. Bài học là cần giới hạn chức năng MVP trước.
