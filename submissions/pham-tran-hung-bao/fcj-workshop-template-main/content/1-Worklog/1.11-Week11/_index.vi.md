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

**Công việc đã thực hiện:** Tôi tham gia buổi họp khởi động dự án IRMS cùng các thành viên trong nhóm để thống nhất mục tiêu, phạm vi và chức năng của hệ thống quản lý sự cố an toàn thông tin. Sau khi trao đổi, nhóm phân công nhiệm vụ và tôi đảm nhận phần Backend, chịu trách nhiệm thiết kế REST API, xây dựng các chức năng xử lý dữ liệu và chuẩn bị môi trường phát triển trên AWS.

**Kiến thức đã học:** Một dự án nhóm cần xác định rõ phạm vi công việc và trách nhiệm của từng thành viên ngay từ đầu để quá trình phát triển diễn ra đồng bộ và hiệu quả.

**Kết quả đạt được:** Tôi xác định được phần công việc của mình trong nhóm và chuẩn bị đầy đủ môi trường để bắt đầu phát triển hệ thống.

**Khó khăn và bài học:** Cần trao đổi kỹ giữa các thành viên để tránh chồng chéo chức năng và đảm bảo các API được thiết kế thống nhất.

## Ngày 2 - 30/6:  Thiết kế REST API

**Công việc đã thực hiện:** Tôi tiến hành phân tích yêu cầu nghiệp vụ và thiết kế các REST API phục vụ hệ thống IRMS. Các API được xây dựng theo chuẩn RESTful, bao gồm các phương thức tạo, xem, cập nhật và xóa dữ liệu. Đồng thời tôi thống nhất với nhóm về cấu trúc request, response và mã trạng thái HTTP để thuận tiện cho việc tích hợp với Frontend.

**Kiến thức đã học:** Việc thiết kế API ngay từ đầu giúp giảm thời gian chỉnh sửa khi các thành viên bắt đầu tích hợp hệ thống.

**Kết quả đạt được:** Hoàn thành bản thiết kế REST API và thống nhất cấu trúc dữ liệu sử dụng giữa Backend và Frontend.

**Khó khăn và bài học:** Một số yêu cầu cần được làm rõ trước khi triển khai để tránh thay đổi cấu trúc API nhiều lần.

## Ngày 3 - 1/7: Xây dựng Incident CRUD API

**Công việc đã thực hiện:** Tôi bắt đầu xây dựng các API quản lý Incident theo mô hình CRUD, bao gồm tạo mới, cập nhật, xem danh sách, xem chi tiết và xóa dữ liệu. Đồng thời bổ sung các bước kiểm tra dữ liệu đầu vào nhằm đảm bảo tính hợp lệ trước khi xử lý và lưu trữ.

**Kiến thức đã học:** Validation dữ liệu là bước quan trọng giúp hạn chế lỗi phát sinh và đảm bảo dữ liệu được lưu trữ chính xác.

**Kết quả đạt được:**  Hoàn thành các API CRUD cơ bản cho chức năng quản lý Incident và kiểm tra hoạt động thông qua Postman.

**Khó khăn và bài học:** Cần chuẩn hóa cấu trúc dữ liệu ngay từ đầu để thuận tiện cho việc mở rộng các chức năng sau này.

## Ngày 4 - 2/7: Xây dựng Timeline API và Error Handling

**Công việc đã thực hiện:** Tôi tiếp tục phát triển Timeline API để lưu lại lịch sử xử lý của từng Incident. Đồng thời bổ sung cơ chế Validation và Error Handling nhằm kiểm tra dữ liệu đầu vào, xử lý ngoại lệ và trả về thông báo lỗi phù hợp theo từng trường hợp.

**Kiến thức đã học:** Error Handling giúp hệ thống hoạt động ổn định hơn, đồng thời hỗ trợ người dùng và lập trình viên dễ dàng xác định nguyên nhân khi xảy ra lỗi.

**Kết quả đạt được:** Hoàn thiện các API Timeline và xây dựng cơ chế xử lý lỗi thống nhất cho các API Backend.

**Khó khăn và bài học:** Việc chuẩn hóa thông báo lỗi ngay từ đầu giúp giảm đáng kể thời gian kiểm thử và bảo trì hệ thống.

## Ngày 5 - 3/7: Kiểm thử và tổng kết tuần

**Công việc đã thực hiện:** Tôi kiểm thử các API đã xây dựng bằng Postman, rà soát lại cấu trúc mã nguồn, cập nhật tài liệu API và trao đổi với các thành viên để chuẩn bị tích hợp với Frontend trong giai đoạn tiếp theo. Đồng thời ghi lại các vấn đề còn tồn tại và kế hoạch hoàn thiện trong tuần sau.

**Kiến thức đã học:** Kiểm thử thường xuyên trong quá trình phát triển giúp phát hiện lỗi sớm và đảm bảo chất lượng của hệ thống.

**Kết quả đạt được:** Các API Backend cơ bản hoạt động đúng yêu cầu và sẵn sàng cho quá trình tích hợp với các thành phần khác của hệ thống.

**Khó khăn và bài học:** Cần duy trì trao đổi thường xuyên giữa Backend và Frontend để việc tích hợp diễn ra thuận lợi và hạn chế phát sinh lỗi.
