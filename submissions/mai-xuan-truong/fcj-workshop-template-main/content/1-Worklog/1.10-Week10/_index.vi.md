---
title: "Tuần 10"
date: 2026-06-12
weight: 10
chapter: false
pre: " <b> 1.10. </b> "
---

**Mốc thời gian:** 12/6 → 17/6 (6 ngày)

> Dự án IRMS được thực hiện bởi nhóm 5 thành viên. Các ghi chú dưới đây tập trung vào phần đóng góp cá nhân của tôi trong quá trình phối hợp với nhóm.

## Ngày 1 - 12/6: Hỗ trợ khởi tạo React + Vite

**Công việc đã thực hiện:** Tôi hỗ trợ khởi tạo frontend React + Vite và kiểm tra cách cấu hình endpoint API cho môi trường test.

Tôi hỗ trợ phần cấu hình môi trường frontend, API base URL và cách chạy local. Việc này giúp nhóm frontend có thể gọi API thật thay vì chỉ dùng dữ liệu mẫu.

**Kiến thức đã học:** Frontend cần được cấu hình để gọi đúng API Gateway endpoint.

**Kết quả đạt được:** Project frontend chạy local và sẵn sàng tích hợp API.

**Khó khăn và bài học:** Cần tách cấu hình môi trường khỏi code cứng.

## Ngày 2 - 13/6: Tích hợp Dashboard với API

**Công việc đã thực hiện:** Tôi phối hợp với bạn làm UI để nối dashboard với dữ liệu incident từ API. Trọng tâm của tôi là kiểm tra request, response và lỗi CORS.

Tôi test request lấy dữ liệu incident cho dashboard và kiểm tra dữ liệu tổng hợp hiển thị đúng. Khi response thiếu field, tôi trao đổi lại với nhóm backend để thống nhất schema.

**Kiến thức đã học:** Dashboard chỉ hữu ích khi dữ liệu backend trả về ổn định.

**Kết quả đạt được:** Dashboard có thể hiển thị dữ liệu incident mẫu.

**Khó khăn và bài học:** Cần xử lý loading/error để tránh giao diện bị trống.

## Ngày 3 - 14/6: Tích hợp Incident List/Detail

**Công việc đã thực hiện:** Tôi hỗ trợ nối màn hình danh sách và chi tiết incident với API Gateway. Các bạn frontend xử lý layout, tôi kiểm tra mapping field.

Tôi nối thử luồng chọn incident từ danh sách sang trang chi tiết, kiểm tra ID truyền đúng và dữ liệu timeline/evidence tải được. Phần layout do teammate xử lý, còn tôi tập trung vào dữ liệu và API.

**Kiến thức đã học:** Frontend integration cần bám API contract đã thống nhất.

**Kết quả đạt được:** Incident list/detail đọc được dữ liệu backend.

**Khó khăn và bài học:** Sai tên field nhỏ cũng làm giao diện hiển thị thiếu dữ liệu.

## Ngày 4 - 15/6: Tích hợp thao tác frontend

**Công việc đã thực hiện:** Tôi test các thao tác tạo/cập nhật incident và thêm timeline từ giao diện. Khi phát hiện lỗi, tôi đối chiếu log API/Lambda.

Tôi test các thao tác tạo, cập nhật incident và thêm timeline ngay trên giao diện. Nếu giao diện báo lỗi, tôi kiểm tra network request rồi đối chiếu với CloudWatch log.

**Kiến thức đã học:** Debug end-to-end cần nhìn cả browser console, network tab và CloudWatch.

**Kết quả đạt được:** Một số lỗi mapping field được phát hiện và sửa.

**Khó khăn và bài học:** Cần ghi rõ lỗi thuộc frontend, API hay Lambda.

## Ngày 5 - 16/6: Hỗ trợ Stitch AI UI integration

**Công việc đã thực hiện:** Tôi hỗ trợ đưa ý tưởng giao diện từ Stitch AI vào các màn hình chính, đồng thời giữ cấu trúc đủ thực dụng cho dashboard vận hành.

Tôi cùng nhóm xem các màn hình do Stitch AI gợi ý rồi chọn phần phù hợp để đưa vào UI. Tôi chú ý giữ giao diện phục vụ thao tác vận hành, không chỉ đẹp về mặt trình bày.

**Kiến thức đã học:** UI đẹp cần đi cùng workflow rõ ràng, không chỉ là phần nhìn.

**Kết quả đạt được:** Giao diện nhất quán hơn và phù hợp demo IRMS.

**Khó khăn và bài học:** Cần tránh làm giao diện quá giống landing page.

## Ngày 6 - 17/6: Kiểm thử frontend local

**Công việc đã thực hiện:** Tôi chạy test local cho các luồng chính: xem dashboard, tạo incident, xem chi tiết, thêm timeline và upload evidence.

Tôi chạy lại toàn bộ luồng local sau khi tích hợp API thật: dashboard, incident detail, timeline, evidence và report. Các lỗi còn lại được ghi thành checklist để xử lý trước khi deploy.

**Kiến thức đã học:** Local testing giúp phát hiện lỗi trước khi deploy lên S3/CloudFront.

**Kết quả đạt được:** Frontend ổn định hơn để chuẩn bị deploy.

**Khó khăn và bài học:** Cần kiểm tra cả dữ liệu thật từ API, không chỉ mock data.
