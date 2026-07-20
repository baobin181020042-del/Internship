---
title: "Tuần 6"
date: 2026-05-25
weight: 6
chapter: false
pre: " <b> 1.6. </b> "
---

**Mốc thời gian:** 25/5 → 29/5 (5 ngày làm việc)

> Dự án IRMS được thực hiện bởi nhóm 5 thành viên. Các ghi chú dưới đây tập trung vào phần đóng góp cá nhân của tôi trong quá trình phối hợp với nhóm.

## Ngày 1 - 19/5: Hỗ trợ Lambda Incident CRUD

**Công việc đã thực hiện:** Tôi hỗ trợ phần kết nối Lambda với DynamoDB cho luồng Incident CRUD, trong khi các bạn khác xử lý nghiệp vụ chi tiết. Tôi tập trung kiểm tra permission, environment variable và response format.

Tôi không phụ trách toàn bộ nghiệp vụ CRUD, nhưng hỗ trợ phần tích hợp Lambda với DynamoDB và API Gateway. Tôi kiểm tra event đầu vào, response trả ra, status code và log để đảm bảo frontend có thể gọi được về sau.

**Kiến thức đã học:** Lambda cần tương tác DynamoDB rõ ràng và trả response phù hợp cho API Gateway.

**Kết quả đạt được:** CRUD chạy thử được ở mức API/backend.

**Khó khăn và bài học:** Input validation và lỗi permission là hai điểm cần kiểm tra sớm.

## Ngày 2 - 20/5: Hỗ trợ Timeline backend

**Công việc đã thực hiện:** Tôi hỗ trợ kiểm tra cách timeline được ghi vào DynamoDB và cách API trả về lịch sử xử lý. Nhóm cùng thống nhất các field cần có cho audit trail.

Tôi test thử việc ghi timeline theo incidentId và kiểm tra dữ liệu trong DynamoDB sau mỗi thao tác. Khi thấy field chưa nhất quán, tôi ghi lại để nhóm chỉnh lại schema trước khi tích hợp frontend.

**Kiến thức đã học:** Timeline giúp theo dõi quá trình xử lý incident minh bạch hơn.

**Kết quả đạt được:** Timeline có thể ghi nhận các bước xử lý cơ bản.

**Khó khăn và bài học:** Cần sắp xếp dữ liệu theo thời gian để frontend hiển thị dễ đọc.

## Ngày 3 - 21/5: Tích hợp Evidence Upload

**Công việc đã thực hiện:** Tôi phụ trách chính việc kiểm tra luồng presigned URL và metadata evidence giữa Lambda, S3 và DynamoDB. Các bạn frontend/backend cùng phối hợp để xác nhận flow.

Tôi tập trung vào luồng kỹ thuật: gọi Lambda lấy presigned URL, upload file lên S3 và lưu metadata. Tôi test bằng file mẫu, kiểm tra object key trên S3 và đối chiếu metadata trong DynamoDB.

**Kiến thức đã học:** File storage và metadata storage nên tách riêng để hệ thống dễ mở rộng.

**Kết quả đạt được:** Evidence upload có flow kỹ thuật rõ ràng để test tiếp trên frontend.

**Khó khăn và bài học:** Content type, object key và CORS là các điểm dễ lỗi.

## Ngày 4 - 22/5: Hỗ trợ Report Generation

**Công việc đã thực hiện:** Tôi hỗ trợ kiểm tra dữ liệu đầu vào cho report API, đặc biệt là incident, timeline và evidence metadata. Phần trình bày report được nhóm cùng review.

Tôi hỗ trợ phần lấy dữ liệu từ các nguồn cần thiết cho report và kiểm tra response API có đủ thông tin hay không. Tôi cũng góp ý không nên đưa quá nhiều trường kỹ thuật vào report vì người xem cần phần tóm tắt rõ ràng.

**Kiến thức đã học:** Report nên tổng hợp đủ thông tin xử lý sự cố nhưng không đưa dữ liệu dư thừa.

**Kết quả đạt được:** API report có dữ liệu đầu vào ổn định hơn.

**Khó khăn và bài học:** Cần phân biệt dữ liệu phục vụ điều tra và dữ liệu nên hiển thị trong report.

## Ngày 5 - 23/5: Tích hợp Alert Handler với EventBridge

**Công việc đã thực hiện:** Tôi tham gia thiết kế luồng event-driven cho Alert Handler. Trọng tâm cá nhân là EventBridge rule, event mẫu và cách Lambda nhận event để tạo incident.

Tôi tạo event mẫu để mô phỏng cảnh báo và kiểm tra cách EventBridge chuyển event sang Lambda. Phần này giúp nhóm có thể demo luồng tự động tạo incident mà không phụ thuộc hoàn toàn vào nguồn event thật.

**Kiến thức đã học:** EventBridge giúp hệ thống phản ứng với security event mà không cần polling.

**Kết quả đạt được:** Có luồng alert tự động ở mức demo để nhóm tiếp tục test.

**Khó khăn và bài học:** Event pattern cần đơn giản và dễ mô phỏng trong môi trường thực tập.

## Ngày 6 - 24/5: Debug backend và CloudWatch

**Công việc đã thực hiện:** Tôi rà soát log CloudWatch cho các Lambda đã tích hợp, ghi lại lỗi thường gặp và trao đổi với nhóm để sửa response/permission.

Tôi dùng CloudWatch Logs để xem lỗi của từng Lambda sau khi gọi API. Tôi ghi lại lỗi theo nhóm như thiếu permission, sai environment variable, response format sai hoặc dữ liệu DynamoDB chưa đúng.

**Kiến thức đã học:** CloudWatch log là công cụ quan trọng khi debug serverless backend.

**Kết quả đạt được:** Một số lỗi IAM và format response được phát hiện sớm.

**Khó khăn và bài học:** Log cần đủ context để biết lỗi đến từ API, Lambda hay DynamoDB.
