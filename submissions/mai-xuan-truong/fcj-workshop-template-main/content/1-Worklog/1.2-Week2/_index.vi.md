---
title: "Tuần 2"
date: 2026-04-27
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

**Mốc thời gian:** 27/4 → 1/5 (5 ngày làm việc)

## Ngày 1 - 26/4: Học IAM

**Công việc đã thực hiện:** Thực hiện lab IAM để hiểu cách AWS quản lý danh tính và phân quyền. Nội dung chính gồm IAM User, Group, Policy và Role.

**Kiến thức đã học:** Hiểu user đại diện cho người dùng, group giúp gom quyền, policy định nghĩa quyền bằng JSON và role dùng cho quyền tạm thời.

**Kết quả đạt được:** Nắm được nền tảng bảo mật quan trọng trước khi học các dịch vụ khác trong AWS.

**Khó khăn và bài học:** Ban đầu dễ nhầm giữa User và Role. Bài học là không dùng root account cho công việc hằng ngày và nên cấp quyền theo nguyên tắc least privilege.

## Ngày 2 - 27/4: Thực hành EC2

**Công việc đã thực hiện:** Học cách tạo EC2 instance, chọn AMI, instance type, key pair và security group. Sau đó tìm hiểu cách kết nối server qua SSH.

**Kiến thức đã học:** Hiểu EC2 là máy chủ ảo trên cloud, có thể start, stop, reboot và cấu hình tương tự server thật nhưng linh hoạt hơn.

**Kết quả đạt được:** Tạo được instance thử nghiệm và biết các điểm cần kiểm tra khi mở port truy cập.

**Khó khăn và bài học:** Khó khăn là quản lý file `.pem` và rule inbound. Bài học là không mở SSH rộng cho Internet nếu không cần thiết.

## Ngày 3 - 28/4: Học VPC và Site-to-Site VPN

**Công việc đã thực hiện:** Làm workshop về Amazon VPC và Site-to-Site VPN. Nội dung gồm VPC, subnet, route table, Internet Gateway, NAT Gateway và các lớp bảo mật mạng.

**Kiến thức đã học:** Hiểu VPC giống một mạng riêng trên AWS; public subnet cho tài nguyên cần Internet, private subnet dùng cho tài nguyên nội bộ.

**Kết quả đạt được:** Có cái nhìn rõ hơn về nền tảng network cần thiết khi thiết kế hệ thống cloud.

**Khó khăn và bài học:** Các khái niệm route và gateway khá nhiều. Bài học là nên vẽ luồng traffic để tránh cấu hình sai.

## Ngày 4 - 29/4: Học S3 và lưu trữ

**Công việc đã thực hiện:** Tìm hiểu Amazon S3, bucket, object, storage class, versioning và chính sách truy cập. Liên hệ kiến thức này với nhu cầu lưu evidence của dự án IRMS sau này.

**Kiến thức đã học:** Hiểu S3 phù hợp để lưu file tĩnh, log, bằng chứng điều tra và cũng có thể dùng cho static web hosting.

**Kết quả đạt được:** Nắm được cách tạo bucket, upload object và cấu hình quyền truy cập cơ bản.

**Khó khăn và bài học:** Khó khăn là phân biệt public access block, bucket policy và IAM policy. Bài học là quyền S3 cần được thiết kế cẩn thận.

## Ngày 5 - 30/4: Tổng hợp kiến thức tuần 2

**Công việc đã thực hiện:** Tổng hợp lại các lab IAM, EC2, VPC và S3. Sắp xếp ghi chú thành các nhóm kiến thức để dễ dùng lại khi bắt đầu dự án chính.

**Kiến thức đã học:** Nhận ra các dịch vụ AWS không tách rời: IAM kiểm soát quyền, VPC kiểm soát mạng, EC2 chạy compute và S3 lưu dữ liệu.

**Kết quả đạt được:** Có nền tảng tốt hơn để đọc tài liệu kiến trúc serverless và chuẩn bị chọn đề tài.

**Khó khăn và bài học:** Một số ghi chú còn dài. Bài học là khi viết worklog cần tóm tắt ý chính thay vì chép toàn bộ nội dung lab.
