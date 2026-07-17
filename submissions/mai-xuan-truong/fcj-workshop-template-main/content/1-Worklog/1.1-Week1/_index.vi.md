---
title: "Tuần 1"
date: 2024-01-01
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---

**Mốc thời gian:** 20/4 → 25/4 (6 ngày)

## Ngày 1 - 20/4: Tạo tài khoản AWS

**Công việc đã thực hiện:** Bắt đầu chuẩn bị tài khoản AWS để dùng cho quá trình thực tập. Khi đăng ký, tài khoản gặp trạng thái bị suspend nên chưa thể thao tác ngay trên console.

**Kiến thức đã học:** Hiểu rằng tài khoản AWS cần thông tin thanh toán, xác minh số điện thoại và cơ chế kiểm soát rủi ro khá chặt chẽ trước khi được sử dụng.

**Kết quả đạt được:** Ghi lại các bước đăng ký, các lỗi gặp phải và chuẩn bị phương án xử lý để tiếp tục trong ngày sau.

**Khó khăn và bài học:** Khó khăn chính là chưa quen quy trình xác minh tài khoản. Bài học rút ra là cần chuẩn bị thông tin hợp lệ và theo dõi email/thông báo từ AWS cẩn thận.

## Ngày 2 - 21/4: Hoàn tất tài khoản và làm nhiệm vụ AWS đầu tiên

**Công việc đã thực hiện:** Tiếp tục xử lý tài khoản AWS, sau đó bắt đầu thực hiện các nhiệm vụ học tập ban đầu để nhận credit. Các dịch vụ được thao tác gồm EC2, AWS Budgets và AWS Lambda.

**Kiến thức đã học:** Nắm được cách truy cập AWS Console, tìm dịch vụ, tạo tài nguyên cơ bản và theo dõi ngân sách để tránh phát sinh chi phí ngoài ý muốn.

**Kết quả đạt được:** Tài khoản đã có thể sử dụng cho các bài lab cơ bản. Một số thao tác tạo/xóa tài nguyên đã được thực hiện thành công.

**Khó khăn và bài học:** Một số bước xác minh mất thời gian. Bài học là phải kiểm tra kỹ vùng triển khai và xóa tài nguyên ngay sau khi thực hành.

## Ngày 3 - 22/4: Thực hành RDS và Amazon Bedrock

**Công việc đã thực hiện:** Hoàn thành thêm các nhiệm vụ liên quan đến Amazon RDS và Amazon Bedrock. Nội dung tập trung vào cách tạo database managed service và tìm hiểu dịch vụ AI sinh nội dung trên AWS.

**Kiến thức đã học:** Hiểu sự khác nhau giữa việc tự vận hành database trên server và dùng RDS. Đồng thời có cái nhìn ban đầu về model foundation trong Bedrock.

**Kết quả đạt được:** Hoàn thành các bước thực hành chính, có thêm kinh nghiệm kiểm tra cấu hình trước khi tạo tài nguyên có thể phát sinh chi phí.

**Khó khăn và bài học:** RDS có nhiều tùy chọn dễ tạo nhầm cấu hình. Bài học là cần đọc kỹ region, instance class và storage trước khi bấm tạo.

## Ngày 4 - 23/4: Nghiên cứu cách viết Worklog

**Công việc đã thực hiện:** Tìm hiểu cách viết worklog cho báo cáo thực tập và cách trình bày nội dung theo tuần/ngày trên website Hugo Workshop.

**Kiến thức đã học:** Học cách tách nội dung thành công việc đã làm, kiến thức học được, kết quả, khó khăn và bài học thay vì ghi lan man theo cảm xúc.

**Kết quả đạt được:** Xây dựng được khung trình bày thống nhất để áp dụng cho các tuần sau của quá trình thực tập.

**Khó khăn và bài học:** Ban đầu nội dung dễ bị dài và dính đoạn. Bài học là cần viết ngắn, xuống dòng rõ và dùng heading phù hợp.

## Ngày 5 - 24/4: Kiểm tra chi phí và dọn tài nguyên

**Công việc đã thực hiện:** Rà soát Billing Dashboard sau các bài lab đầu tiên. Phát hiện chi phí phát sinh từ RDS/Aurora do có tài nguyên còn chạy ở một region khác.

**Kiến thức đã học:** Hiểu rõ hơn rằng tài nguyên AWS được quản lý theo từng region; nếu chỉ kiểm tra một region thì có thể bỏ sót tài nguyên đang phát sinh phí.

**Kết quả đạt được:** Xóa các tài nguyên không cần thiết và ghi lại quy trình kiểm tra chi phí sau mỗi buổi thực hành.

**Khó khăn và bài học:** Khó khăn là chi phí không luôn xuất hiện ngay lập tức. Bài học là phải kiểm tra Cost Explorer, Billing và từng region thường xuyên.

## Ngày 6 - 25/4: Đưa Worklog lên GitHub

**Công việc đã thực hiện:** Tập đưa nội dung worklog lên GitHub và kiểm tra cách website Hugo đọc các file Markdown trong thư mục content.

**Kiến thức đã học:** Nắm được front matter, weight, title và cấu trúc thư mục ảnh hưởng đến sidebar và thứ tự hiển thị của website.

**Kết quả đạt được:** Có bản worklog đầu tiên chạy được trên website, làm nền cho việc tiếp tục cập nhật các tuần sau.

**Khó khăn và bài học:** Một số nội dung chưa đẹp vì copy trực tiếp từ ghi chú. Bài học là cần biên tập lại trước khi publish.
