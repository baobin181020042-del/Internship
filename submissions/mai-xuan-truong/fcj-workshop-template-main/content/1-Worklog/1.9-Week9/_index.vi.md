---
title: "Tuần 9"
date: 2026-06-15
weight: 9
chapter: false
pre: " <b> 1.9. </b> "
---

**Mốc thời gian:** 15/6 → 19/6 (5 ngày làm việc)

> Dự án IRMS được thực hiện bởi nhóm 5 thành viên. Các ghi chú dưới đây tập trung vào phần đóng góp cá nhân của tôi trong quá trình phối hợp với nhóm.

## Ngày 1 - 6/6: Test Incident CRUD

**Công việc đã thực hiện:** Tôi phụ trách test CRUD qua API Gateway với dữ liệu incident mẫu, sau đó báo lại các lỗi field/response cho nhóm backend.

Tôi test các trường hợp tạo incident mới, xem danh sách, cập nhật trạng thái và xóa dữ liệu thử. Tôi ghi rõ request body, expected response và lỗi thực tế để nhóm backend sửa nhanh hơn.

**Kiến thức đã học:** Test CRUD cần kiểm tra cả success case và error case.

**Kết quả đạt được:** CRUD ổn định hơn và dữ liệu lưu đúng bảng.

**Khó khăn và bài học:** Thiếu field hoặc sai status code cần được xử lý nhất quán.

## Ngày 2 - 7/6: Test Timeline

**Công việc đã thực hiện:** Tôi test việc thêm timeline khi incident thay đổi trạng thái hoặc có ghi chú mới. Kết quả được đối chiếu với dữ liệu DynamoDB.

Tôi tạo một incident mẫu rồi thêm nhiều timeline event để kiểm tra thứ tự hiển thị. Tôi cũng đối chiếu dữ liệu trong DynamoDB để chắc timeline gắn đúng incident.

**Kiến thức đã học:** Timeline là phần quan trọng để truy vết quá trình xử lý.

**Kết quả đạt được:** Timeline hiển thị dữ liệu hợp lý hơn cho frontend.

**Khó khăn và bài học:** Cần thống nhất thứ tự sắp xếp và định dạng thời gian.

## Ngày 3 - 8/6: Test Evidence Upload

**Công việc đã thực hiện:** Tôi test presigned URL, upload file mẫu lên S3 và kiểm tra metadata trong DynamoDB. Đây là phần tôi tham gia khá nhiều vì liên quan S3 và API.

Tôi test từ bước lấy presigned URL đến upload file và kiểm tra metadata. Khi gặp lỗi CORS hoặc content type, tôi chụp lại lỗi và ghi chú cấu hình cần sửa.

**Kiến thức đã học:** Evidence upload cần phối hợp chặt giữa S3, Lambda, DynamoDB và frontend.

**Kết quả đạt được:** Flow upload hoạt động với file thử nghiệm.

**Khó khăn và bài học:** CORS và content type là lỗi dễ gặp nhất.

## Ngày 4 - 9/6: Sửa CORS cùng nhóm

**Công việc đã thực hiện:** Tôi hỗ trợ cấu hình CORS cho API Gateway/S3 để frontend có thể gọi API và upload file. Sau mỗi thay đổi, tôi test lại từ trình duyệt.

Tôi kiểm tra lỗi trên browser console và network tab, sau đó đối chiếu với cấu hình API Gateway/S3. Việc sửa CORS được test lại trực tiếp từ frontend để chắc người dùng cuối gọi API được.

**Kiến thức đã học:** CORS là vấn đề tích hợp frontend-backend, không chỉ là lỗi backend.

**Kết quả đạt được:** Giảm lỗi blocked by CORS trong quá trình test.

**Khó khăn và bài học:** Cần khai báo đúng origin, method và header.

## Ngày 5 - 10/6: Test Report API

**Công việc đã thực hiện:** Tôi test API tạo report từ incident có timeline và evidence metadata. Phần nội dung report được nhóm cùng kiểm tra.

Tôi chuẩn bị incident có đủ timeline và evidence rồi gọi report API. Tôi kiểm tra xem report có thiếu phần nào không và ghi chú các field cần frontend hiển thị.

**Kiến thức đã học:** Report cần lấy dữ liệu từ nhiều nguồn nhưng vẫn trả về cấu trúc dễ dùng.

**Kết quả đạt được:** Report API trả về đủ thông tin cho demo.

**Khó khăn và bài học:** Không nên đưa dữ liệu không cần thiết vào report.

## Ngày 6 - 11/6: Test Alert Handler

**Công việc đã thực hiện:** Tôi gửi event mẫu để kiểm tra Alert Handler, EventBridge và SNS notification. Kết quả được ghi lại trong checklist test.

Tôi gửi event mẫu qua luồng alert để xem incident có được tạo đúng không. Tôi cũng kiểm tra SNS notification và log để đảm bảo khi demo có thể giải thích luồng tự động hóa.

**Kiến thức đã học:** Event-driven workflow cần test bằng event mẫu trước khi demo.

**Kết quả đạt được:** Luồng tự động tạo incident từ alert chạy được ở mức demo.

**Khó khăn và bài học:** Cần log event id và timestamp để truy vết lỗi.
