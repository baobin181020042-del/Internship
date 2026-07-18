---
title: "Tuần 7"
date: 2026-05-25
weight: 7
chapter: false
pre: " <b> 1.7. </b> "
---

**Mốc thời gian:** 25/5 → 30/5 (6 ngày)

> Dự án IRMS được thực hiện bởi nhóm 5 thành viên. Các ghi chú dưới đây tập trung vào phần đóng góp cá nhân của tôi trong quá trình phối hợp với nhóm.

## Ngày 1 - 25/5: Cấu hình EventBridge rule

**Công việc đã thực hiện:** Tôi phụ trách thử rule EventBridge bằng event mẫu, sau đó phối hợp với bạn làm Alert Handler để kiểm tra dữ liệu truyền vào Lambda.

Tôi thử nhiều event mẫu nhỏ để kiểm tra rule có match đúng không. Sau mỗi lần test, tôi xem log Lambda để biết event truyền vào có đủ field cho Alert Handler xử lý hay không.

**Kiến thức đã học:** Event pattern quyết định event nào được chuyển sang xử lý.

**Kết quả đạt được:** Rule hoạt động với event mẫu và có thể dùng cho demo GuardDuty-like flow.

**Khó khăn và bài học:** Cần test bằng mẫu nhỏ trước khi mở rộng event source.

## Ngày 2 - 26/5: Tích hợp SNS notification

**Công việc đã thực hiện:** Tôi hỗ trợ cấu hình SNS topic và kiểm tra cách Lambda gửi thông báo khi có alert quan trọng. Nhóm cùng đánh giá mức độ thông báo phù hợp.

Tôi cấu hình topic và kiểm tra luồng Lambda gửi thông báo khi có alert. Tôi cũng trao đổi với nhóm về việc chỉ gửi thông báo cho sự kiện quan trọng để demo không bị quá nhiều message.

**Kiến thức đã học:** SNS phù hợp cho notification đơn giản trong kiến trúc serverless.

**Kết quả đạt được:** Có kênh thông báo thử nghiệm cho alert workflow.

**Khó khăn và bài học:** Không nên gửi quá nhiều thông báo gây nhiễu trong demo.

## Ngày 3 - 27/5: Rà soát Secrets Manager

**Công việc đã thực hiện:** Tôi rà soát cách lưu giá trị nhạy cảm cho phần AI integration trong Secrets Manager. Tôi không đưa giá trị thật vào source hoặc tài liệu.

Tôi kiểm tra cách Lambda đọc giá trị cấu hình từ Secrets Manager và cách mô tả bước này trong tài liệu. Tôi chỉ ghi hướng cấu hình và tên biến minh họa, không đưa giá trị thật vào Worklog hoặc Workshop.

**Kiến thức đã học:** Secrets Manager giúp tách cấu hình nhạy cảm khỏi code.

**Kết quả đạt được:** Có hướng cấu hình an toàn hơn cho Lambda gọi dịch vụ AI.

**Khó khăn và bài học:** Tài liệu chỉ nên mô tả cách cấu hình, không chứa giá trị thật.

## Ngày 4 - 28/5: Hỗ trợ tích hợp AI provider

**Công việc đã thực hiện:** Tôi hỗ trợ phần cấu hình môi trường và kiểm tra Lambda AI Assistant khi gọi dịch vụ bên ngoài. Phần prompt và nghiệp vụ AI được nhóm cùng điều chỉnh.

Tôi hỗ trợ kiểm tra phần cấu hình runtime, timeout và xử lý lỗi khi Lambda gọi dịch vụ AI. Tôi cũng test tình huống phản hồi chậm hoặc lỗi để frontend có thể hiển thị thông báo phù hợp.

**Kiến thức đã học:** Khi tích hợp AI cần giới hạn dữ liệu gửi đi và xử lý lỗi phản hồi.

**Kết quả đạt được:** AI Assistant chạy thử được với incident context mẫu.

**Khó khăn và bài học:** Không nên xem output AI là kết luận cuối cùng trong xử lý sự cố.

## Ngày 5 - 29/5: Kiểm thử API nội bộ

**Công việc đã thực hiện:** Tôi tập trung test các endpoint bằng dữ liệu mẫu: incident CRUD, timeline, evidence, report và alert. Kết quả được ghi lại để nhóm sửa theo từng phần.

Tôi chuẩn bị dữ liệu mẫu cho incident, timeline và evidence để gọi API theo thứ tự thực tế. Kết quả test được ghi lại theo endpoint để nhóm biết lỗi nằm ở API Gateway, Lambda hay DynamoDB.

**Kiến thức đã học:** Test API sớm giúp phát hiện lỗi tích hợp trước khi frontend gọi thật.

**Kết quả đạt được:** Phát hiện một số lỗi response schema và permission.

**Khó khăn và bài học:** Cần test từng endpoint riêng trước khi test cả workflow.

## Ngày 6 - 30/5: Hỗ trợ sửa lỗi backend

**Công việc đã thực hiện:** Tôi phối hợp với nhóm sửa các lỗi liên quan API Gateway integration, status code, IAM permission và dữ liệu DynamoDB.

Tôi phối hợp sửa các lỗi tích hợp sau khi test API, nhất là response thiếu header, status code chưa đúng và permission chưa đủ. Sau mỗi lần sửa, tôi chạy lại request để xác nhận lỗi đã hết.

**Kiến thức đã học:** Serverless integration thường lỗi ở ranh giới giữa các dịch vụ hơn là trong một file code riêng lẻ.

**Kết quả đạt được:** Backend ổn định hơn để chuẩn bị đưa vào SAM.

**Khó khăn và bài học:** Cần giữ response schema cố định để frontend tích hợp thuận lợi.
