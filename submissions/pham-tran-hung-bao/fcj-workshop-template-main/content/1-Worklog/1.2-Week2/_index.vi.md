---
title: "Tuần 2"
date: 2026-04-27
weight: 2
chapter: false
pre: " <b> 1.2. </b> "
---

**Mốc thời gian:** 27/4 → 1/5 (5 ngày làm việc)

## Ngày 1 - 27/4: Tìm hiểu Amazon VPC

**Công việc đã thực hiện:** Trong ngày đầu của tuần thứ hai, tôi nghiên cứu dịch vụ Amazon Virtual Private Cloud (VPC), tìm hiểu khái niệm mạng riêng ảo trên nền tảng AWS. Tôi làm quen với các thành phần như VPC, Public Subnet, Private Subnet, Route Table, Internet Gateway và Elastic IP, đồng thời tìm hiểu cách các thành phần này phối hợp với nhau để xây dựng một hệ thống mạng an toàn trên môi trường điện toán đám mây. Ngoài phần lý thuyết, tôi thực hành tạo một VPC mới, thiết lập dải địa chỉ IP (CIDR Block) và tìm hiểu cách phân chia Subnet cho từng khu vực mạng.

**Kết quả và bài học:** Sau buổi học, tôi hiểu được vai trò của Amazon VPC trong việc xây dựng hạ tầng mạng trên AWS. Tôi nắm được chức năng của từng thành phần trong hệ thống mạng và hiểu vì sao việc thiết kế mạng ngay từ đầu sẽ ảnh hưởng trực tiếp đến khả năng mở rộng và bảo mật của hệ thống.

## Ngày 2 - 28/4: Thực hành cấu hình VPC và Security Group

**Công việc đã thực hiện:** Tôi thực hành cấu hình Security Group cho EC2 bằng cách thiết lập các quy tắc Inbound và Outbound, cho phép truy cập SSH và HTTP theo yêu cầu. Ngoài ra, tôi kiểm tra một số trường hợp kết nối thất bại để xác định nguyên nhân và điều chỉnh lại cấu hình mạng phù hợp.

**Kết quả và bài học:** Tôi hiểu cách Security Group hoạt động như tường lửa của EC2 và biết cách cấu hình quyền truy cập nhằm đảm bảo tính bảo mật cho hệ thống.

## Ngày 3 - 29/4: Tìm hiểu Amazon RDS

**Công việc đã thực hiện:** Tôi nghiên cứu Amazon Relational Database Service (RDS), thực hành tạo cơ sở dữ liệu mới, lựa chọn hệ quản trị cơ sở dữ liệu, cấu hình dung lượng lưu trữ và thiết lập thông tin quản trị. Đồng thời tìm hiểu cơ chế sao lưu tự động và các lợi ích của dịch vụ cơ sở dữ liệu được quản lý.

**Kết quả và bài học:** Tôi nắm được quy trình triển khai Amazon RDS và hiểu được ưu điểm của dịch vụ này trong việc giảm thời gian quản trị cơ sở dữ liệu.

## Ngày 4 - 30/4: Kết nối EC2 với RDS

**Công việc đã thực hiện:** Tôi thực hành kết nối EC2 với Amazon RDS thông qua cùng một VPC, cấu hình Security Group để cho phép hai dịch vụ giao tiếp và kiểm tra khả năng kết nối. Trong quá trình thực hành, tôi cũng tìm hiểu một số lỗi phổ biến liên quan đến cấu hình mạng và quyền truy cập.

**Kết quả và bài học:** Tôi hiểu được mối liên hệ giữa EC2, VPC và RDS trong một hệ thống thực tế, đồng thời biết cách xử lý các lỗi kết nối cơ bản.

## Ngày 5 - 1/5: Tổng kết kiến thức tuần 2

**Công việc đã thực hiện:** Tôi tổng hợp lại toàn bộ kiến thức đã học về Amazon VPC, Security Group và Amazon RDS, rà soát các tài nguyên đã tạo trong quá trình thực hành, dọn dẹp môi trường AWS và hoàn thiện ghi chú để phục vụ cho báo cáo thực tập.

**Kết quả và bài học:** Kết thúc tuần thứ hai, tôi đã nắm được cách xây dựng mạng cơ bản trên AWS, cấu hình bảo mật và triển khai cơ sở dữ liệu trong môi trường đám mây.
