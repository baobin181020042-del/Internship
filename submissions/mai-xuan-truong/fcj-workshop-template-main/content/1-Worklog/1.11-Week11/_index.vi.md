---
title: "Tuần 11"
date: 2024-01-01
weight: 11
chapter: false
pre: " <b> 1.11. </b> "
---

**Mốc thời gian:** 18/6 → 23/6 (6 ngày)

> Dự án IRMS được thực hiện bởi nhóm 5 thành viên. Các ghi chú dưới đây tập trung vào phần đóng góp cá nhân của tôi trong quá trình phối hợp với nhóm.

## Ngày 1 - 18/6: Kiểm tra Cognito trên frontend

**Công việc đã thực hiện:** Tôi kiểm tra luồng đăng nhập Cognito và cách frontend gửi JWT khi gọi API bảo vệ. Nhóm cùng xử lý các lỗi giao diện đăng nhập.

Tôi test đăng nhập, lấy JWT và gọi API được bảo vệ bởi Cognito Authorizer. Khi gặp lỗi 401, tôi kiểm tra lại group, app client và header request.

**Kiến thức đã học:** Authentication cần được test từ trình duyệt đến API authorizer.

**Kết quả đạt được:** Luồng đăng nhập/gọi API bảo vệ hoạt động ổn hơn.

**Khó khăn và bài học:** Cần xử lý lỗi 401 rõ ràng cho người dùng.

## Ngày 2 - 19/6: Tích hợp Evidence UI

**Công việc đã thực hiện:** Tôi hỗ trợ kiểm tra evidence upload từ UI đến S3 và metadata trong DynamoDB. Phần giao diện upload do teammate phụ trách chính.

Tôi test giao diện upload evidence với file mẫu, theo dõi progress và kiểm tra sau upload file có vào S3 hay không. Tôi cũng xem metadata có hiển thị lại trong incident detail không.

**Kiến thức đã học:** Upload UI cần phản hồi rõ khi upload thành công hoặc thất bại.

**Kết quả đạt được:** Evidence hiển thị tốt hơn trong trang incident detail.

**Khó khăn và bài học:** Cần giới hạn loại file và thông báo lỗi dễ hiểu.

## Ngày 3 - 20/6: Tích hợp Report UI

**Công việc đã thực hiện:** Tôi test luồng gọi report API từ frontend và kiểm tra dữ liệu report hiển thị đúng với incident hiện tại.

Tôi gọi report API từ giao diện và so sánh nội dung trả về với dữ liệu incident thật. Tôi góp ý tách các phần summary, timeline và evidence để report dễ đọc hơn.

**Kiến thức đã học:** Report UI cần bám đúng cấu trúc response từ backend.

**Kết quả đạt được:** Report phục vụ demo rõ hơn.

**Khó khăn và bài học:** Cần tách timeline và evidence trong report để người xem dễ theo dõi.

## Ngày 4 - 21/6: Hỗ trợ AI Assistant UI

**Công việc đã thực hiện:** Tôi hỗ trợ kết nối màn hình AI Assistant với API backend và kiểm tra trạng thái loading/error khi gọi AI.

Tôi kiểm tra lúc UI gửi incident context sang backend AI Assistant và nhận phản hồi. Tôi cũng test trạng thái loading, lỗi timeout và cách hiển thị kết quả AI cho người dùng.

**Kiến thức đã học:** AI output nên được xem là gợi ý hỗ trợ, không phải quyết định cuối cùng.

**Kết quả đạt được:** AI Assistant có thể chạy demo với incident context mẫu.

**Khó khăn và bài học:** Cần kiểm soát dữ liệu gửi đi và hiển thị thông báo phù hợp.

## Ngày 5 - 22/6: Rà soát bảo mật frontend

**Công việc đã thực hiện:** Tôi rà soát source frontend để không hard-code giá trị nhạy cảm, đồng thời kiểm tra cách cấu hình endpoint và biến môi trường.

Tôi rà lại source để tránh hard-code cấu hình nhạy cảm và kiểm tra các biến môi trường dùng khi build. Tôi cũng đảm bảo tài liệu chỉ mô tả cách cấu hình, không chứa giá trị thật.

**Kiến thức đã học:** Frontend security hygiene rất quan trọng trước khi deploy.

**Kết quả đạt được:** Source sạch hơn và phù hợp để đưa vào báo cáo/workshop.

**Khó khăn và bài học:** Không đưa giá trị nhạy cảm hoặc cấu hình riêng tư vào repository.

## Ngày 6 - 23/6: Chuẩn bị deploy frontend

**Công việc đã thực hiện:** Tôi chuẩn bị build production, kiểm tra API base URL và phối hợp với nhóm để chốt bản frontend trước khi upload S3.

Tôi kiểm tra lệnh build, base URL, API endpoint và các file output trước khi upload lên S3. Nhóm cùng review bản cuối để tránh deploy thiếu asset hoặc gọi nhầm endpoint.

**Kiến thức đã học:** Deploy frontend cần chuẩn bị cấu hình môi trường chính xác.

**Kết quả đạt được:** Frontend sẵn sàng cho bước hosting trên S3/CloudFront.

**Khó khăn và bài học:** Sai endpoint khi build sẽ khiến bản deploy gọi nhầm API.
