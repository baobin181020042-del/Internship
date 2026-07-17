---
title: "Tuần 5"
date: 2024-01-01
weight: 5
chapter: false
pre: " <b> 1.5. </b> "
---

**Mốc thời gian:** 13/5 → 18/5 (6 ngày)

> Dự án IRMS được thực hiện bởi nhóm 5 thành viên. Các ghi chú dưới đây tập trung vào phần đóng góp cá nhân của tôi trong quá trình phối hợp với nhóm.

## Ngày 1 - 13/5: Phụ trách cấu hình Cognito

**Công việc đã thực hiện:** Tôi phụ trách thử nghiệm User Pool, app client và group theo vai trò. Nhóm cùng review để đảm bảo luồng đăng nhập phù hợp với yêu cầu RBAC.

Tôi thử tạo User Pool, app client và group role, sau đó kiểm tra các thiết lập đăng nhập cơ bản. Tôi ghi lại các cấu hình cần dùng cho frontend như User Pool ID, Client ID và domain/callback ở dạng mô tả, không đưa giá trị nhạy cảm vào tài liệu.

**Kiến thức đã học:** Cognito can handle authentication for the team while API Gateway uses its authorizer to protect routes.

**Kết quả đạt được:** Có cấu hình xác thực ban đầu và ghi chú các giá trị cần dùng cho frontend/backend.

**Khó khăn và bài học:** Callback URL, logout URL và group naming cần được kiểm tra kỹ.

## Ngày 2 - 14/5: Thiết lập API Gateway skeleton

**Công việc đã thực hiện:** Tôi tạo cấu trúc API Gateway ban đầu theo API contract đã thống nhất, gồm resource, method và authorizer. Các bạn backend dùng cấu trúc này để nối Lambda sau.

Tôi tạo khung resource/method trước để cả nhóm có điểm tích hợp chung. Khi tạo API, tôi kiểm tra naming của route, chuẩn bị authorizer và ghi lại các endpoint cần nối Lambda ở các bước sau.

**Kiến thức đã học:** API Gateway cần được thiết kế nhất quán để frontend và Lambda không bị lệch path.

**Kết quả đạt được:** Có skeleton API để nhóm bắt đầu tích hợp các chức năng.

**Khó khăn và bài học:** Sai method hoặc path nhỏ cũng có thể làm test API thất bại.

## Ngày 3 - 15/5: Hỗ trợ tạo DynamoDB

**Công việc đã thực hiện:** Tôi hỗ trợ tạo các bảng DynamoDB và kiểm tra khóa chính/GSI theo access pattern. Phần nghiệp vụ do nhóm cùng thống nhất trước đó.

Tôi tạo hoặc kiểm tra các bảng theo thiết kế đã thống nhất, sau đó rà lại partition key, sort key và GSI. Tôi cũng thử đọc cấu hình table name để chuẩn bị đưa vào environment variable của Lambda.

**Kiến thức đã học:** DynamoDB cần được thiết kế theo cách dữ liệu được truy vấn trong ứng dụng.

**Kết quả đạt được:** Các bảng nền tảng sẵn sàng cho Lambda đọc/ghi thử nghiệm.

**Khó khăn và bài học:** Cần ghi lại tên bảng và index để tránh sai environment variable.

## Ngày 4 - 16/5: Chuẩn bị S3 Evidence

**Công việc đã thực hiện:** Tôi chuẩn bị bucket lưu evidence và trao đổi với nhóm về hướng dùng presigned URL để upload file. Cách này giúp Lambda không phải nhận file trực tiếp.

Tôi kiểm tra cấu hình bucket, block public access và hướng đặt object key cho evidence. Ngoài ra tôi ghi lại luồng upload bằng presigned URL để nhóm frontend biết cần gọi API nào trước khi upload file.

**Kiến thức đã học:** S3 phù hợp cho file evidence, còn metadata nên lưu trong DynamoDB để truy vấn nhanh.

**Kết quả đạt được:** Có hướng thiết kế evidence upload rõ ràng cho backend và frontend.

**Khó khăn và bài học:** Cần tránh cấu hình public access không cần thiết.

## Ngày 5 - 17/5: Rà soát IAM permission

**Công việc đã thực hiện:** Tôi rà soát permission cần thiết cho Lambda khi truy cập DynamoDB, S3, CloudWatch, SNS và Secrets Manager. Mục tiêu là đủ quyền cho demo nhưng không quá rộng.

Tôi liệt kê các quyền tối thiểu cho từng Lambda: quyền đọc/ghi DynamoDB, tạo presigned URL với S3, ghi log CloudWatch và gửi SNS khi cần. Việc này giúp SAM template rõ hơn và hạn chế cấp quyền quá rộng.

**Kiến thức đã học:** Least privilege giúp giảm rủi ro trong hệ thống serverless.

**Kết quả đạt được:** Có danh sách policy cần đưa vào SAM template.

**Khó khăn và bài học:** Nếu permission thiếu thì Lambda lỗi runtime, nhưng cấp quá rộng cũng không tốt.

## Ngày 6 - 18/5: Kiểm tra hạ tầng tuần 5

**Công việc đã thực hiện:** Tôi kiểm tra lại Cognito, API Gateway, DynamoDB và S3 cùng nhóm để đảm bảo tên tài nguyên thống nhất trước khi đi vào Lambda.

Tôi mở lại từng dịch vụ đã cấu hình để so sánh tên resource, region và dependency. Sau đó tôi ghi thành checklist nhỏ để khi deploy hoặc test API không bị nhầm giữa các tài nguyên.

**Kiến thức đã học:** Hạ tầng cần ổn định trước khi team triển khai nhiều phần song song.

**Kết quả đạt được:** Hoàn thành lớp AWS infrastructure ban đầu theo phần tôi phụ trách.

**Khó khăn và bài học:** Bài học là resource name phải được ghi lại sớm để tránh lệch tài liệu và code.
