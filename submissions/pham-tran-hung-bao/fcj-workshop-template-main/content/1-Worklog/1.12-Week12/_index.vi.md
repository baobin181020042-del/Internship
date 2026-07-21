---
title: "Tuần 12"
date: 2026-07-06
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

**Mốc thời gian:** 06/07/2026 - 21/07/2026

> Dự án IRMS được thực hiện bởi nhóm 5 thành viên. Các ghi chú dưới đây tập trung vào phần đóng góp cá nhân của tôi trong quá trình phối hợp với nhóm.

## Ngày 1 - 6/7: Hoàn thiện API và tối ưu Backend

**Công việc đã thực hiện:** Tôi tiếp tục hoàn thiện các API của hệ thống IRMS, bao gồm Incident CRUD, Timeline, Report Generation và Upload Evidence. Đồng thời rà soát lại mã nguồn Backend, bổ sung Validation, Error Handling và tối ưu các hàm Lambda để giảm thời gian xử lý. Bên cạnh đó, tôi kiểm tra quyền IAM và cấu hình môi trường nhằm đảm bảo các dịch vụ AWS hoạt động ổn định.

**Kiến thức đã học:** Việc tối ưu Lambda và chuẩn hóa xử lý lỗi giúp ứng dụng hoạt động ổn định hơn, đồng thời giảm thời gian phản hồi của API.

**Kết quả đạt được:** Các API Backend được hoàn thiện, hoạt động ổn định và sẵn sàng cho quá trình kiểm thử và tích hợp với Frontend.

**Khó khăn và bài học:**  Trong quá trình tối ưu, cần kiểm tra kỹ quyền truy cập của IAM Role và các biến môi trường để tránh phát sinh lỗi khi triển khai.

## Ngày 2 - 8/7: Kiểm thử API bằng Postman

**Công việc đã thực hiện:** Tôi sử dụng Postman để kiểm thử toàn bộ các API của hệ thống như đăng nhập, quản lý Incident, Timeline, Upload Evidence và Report Generation. Ngoài việc kiểm tra kết quả trả về, tôi còn thử nhiều trường hợp dữ liệu không hợp lệ để đánh giá khả năng Validation và Error Handling của hệ thống trước khi tích hợp với giao diện người dùng.

**Kiến thức đã học:** Kiểm thử API theo nhiều trường hợp khác nhau giúp phát hiện lỗi sớm và đảm bảo hệ thống hoạt động ổn định trước khi triển khai thực tế.

**Kết quả đạt được:** Các API hoạt động đúng theo thiết kế, các lỗi được ghi nhận và khắc phục trước khi chuyển sang giai đoạn tích hợp.

**Khó khăn và bài học:** Một số lỗi phát sinh do dữ liệu đầu vào chưa đúng định dạng, vì vậy cần xây dựng quy tắc Validation rõ ràng ngay từ đầu.

## Ngày 3 - 10/7: Tích hợp Frontend với Backend

**Công việc đã thực hiện:** Tôi phối hợp với thành viên phụ trách Frontend để tích hợp các API đã xây dựng vào giao diện của hệ thống. Trong quá trình thực hiện, tôi hỗ trợ kiểm tra JWT Token từ Amazon Cognito, cấu hình API Gateway, xử lý lỗi CORS và xác nhận dữ liệu được đồng bộ chính xác giữa Frontend và Backend.

**Kiến thức đã học:**  Việc thống nhất cấu trúc API và dữ liệu giữa Frontend và Backend giúp quá trình tích hợp diễn ra thuận lợi và hạn chế phát sinh lỗi.

**Kết quả đạt được:** Các chức năng chính của hệ thống có thể trao đổi dữ liệu thông qua API và hoạt động ổn định trên môi trường thử nghiệm.

**Khó khăn và bài học:** Khi tích hợp nhiều thành phần, cần kiểm tra đồng thời cả Frontend, Backend và các dịch vụ AWS để xác định đúng nguyên nhân khi xảy ra lỗi.

## Ngày 4 - 14/7: Hoàn thiện Workshop và Worklog

**Công việc đã thực hiện:** Tôi cập nhật lại Workshop, Worklog và các tài liệu kỹ thuật theo đúng tiến độ triển khai của dự án IRMS. Đồng thời rà soát sơ đồ kiến trúc, các bước triển khai AWS, hình ảnh minh họa và nội dung song ngữ để đảm bảo tài liệu phản ánh đúng phần công việc mà tôi đã tham gia thực hiện.

**Kiến thức đã học:** Tài liệu cần được cập nhật song song với quá trình phát triển để đảm bảo tính chính xác và thuận tiện cho việc báo cáo sau này.

**Kết quả đạt được:** Các tài liệu được đồng bộ với tiến độ dự án và sẵn sàng sử dụng cho báo cáo thực tập.

**Khó khăn và bài học:** Khi chỉnh sửa nhiều tài liệu cùng lúc cần kiểm tra kỹ nội dung và định dạng để tránh sai lệch giữa các phần.

## Ngày 5 - 21/7: Tổng kết và chia sẻ kết quả

**Công việc đã thực hiện:** Tôi tổng hợp toàn bộ công việc đã thực hiện trong giai đoạn triển khai dự án, kiểm tra lại mã nguồn, tài liệu và các dịch vụ AWS đã sử dụng. Ngoài ra, tôi tham gia chuẩn bị nội dung chia sẻ về quá trình xây dựng hệ thống IRMS và chủ đề **"Study Group VN Shift-left Security Với Amazon Bedrock: Tự Động Hóa Threat Modeling Bằng Generative AI"**, đồng thời hoàn thiện báo cáo để kết thúc đợt thực tập.

**Kiến thức đã học:** Việc tổng kết và chia sẻ kinh nghiệm giúp hệ thống hóa lại kiến thức đã học cũng như nâng cao kỹ năng làm việc nhóm và trình bày dự án.

**Kết quả đạt được:** Hoàn thành các nội dung theo kế hoạch thực tập, tài liệu và dự án được hoàn thiện, sẵn sàng phục vụ cho quá trình báo cáo và đánh giá.

**Khó khăn và bài học:** Cần thường xuyên cập nhật tiến độ và tài liệu trong suốt quá trình phát triển để giảm khối lượng công việc ở giai đoạn cuối và đảm bảo tính nhất quán của toàn bộ dự án.
