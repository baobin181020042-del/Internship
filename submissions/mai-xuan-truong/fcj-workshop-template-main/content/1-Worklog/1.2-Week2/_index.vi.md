---
title: "Worklog Tuần 2"
date: 2026-04-26
weight: 1
chapter: false
pre: " <b> 1.2. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

### Mục tiêu tuần 2 (26/04/2026 - 30/04/2026):

* Củng cố nền tảng AWS về IAM, EC2, VPC, RDS, Monitoring, CLI và Backup.
* Làm workshop theo hướng thực hành end-to-end, vừa triển khai vừa tự kiểm soát chi phí.
* Tăng khả năng vận hành thực tế: bảo mật quyền truy cập, phân tích logs, cảnh báo và backup/restore.

### Nhật ký công việc theo ngày:

| Ngày | Nội dung thực hiện | Kết quả |
| --- | --- | --- |
| **26/04/2026** | Học **Lab 02 IAM**: IAM User, Group, Policy, Role; best practices. Đồng thời học chi tiết **EC2**: Instance, AMI, Key Pair, Security Group, Elastic IP, quy trình launch và bảo mật. Thực hành thêm workshop **VPC + Site-to-Site VPN** (VPC, subnet, route table, IGW, NAT, SG/NACL, flow logs, tunnel VPN). | Nắm rõ kiến trúc truy cập IAM và nền tảng hạ tầng EC2/VPC/VPN. |
| **27/04/2026** | Workshop **Amazon RDS**: tạo DB subnet group, cấu hình security group tách biệt EC2/RDS, tạo MySQL RDS, kết nối app qua endpoint, thực hành snapshot/restore. Làm workshop **AWS Budgets**: Cost Budget, Usage Budget, tìm hiểu RI/Savings Plans Budget và cơ chế cảnh báo. | Kết nối thành công ứng dụng với RDS, hiểu rõ cách kiểm soát chi phí bằng budgets nhiều ngưỡng. |
| **28/04/2026** | Workshop **Amazon CloudWatch**: Metrics, Logs, Logs Insights, Metric Filter, Alarms qua SNS, Dashboard theo dõi tập trung. Thực hành thêm workshop **Hybrid DNS với Route 53 Resolver**: Outbound/Inbound Endpoint, Resolver Rules, tích hợp DNS giữa môi trường “on-prem” mô phỏng và AWS. | Thiết lập được luồng giám sát đầy đủ metric-log-alarm-dashboard và hiểu mô hình DNS hybrid doanh nghiệp. |
| **29/04/2026** | Workshop **AWS CLI**: cài đặt, profile, thao tác EC2/S3/SNS/IAM/VPC bằng lệnh, tạo EC2 bằng CLI và dọn tài nguyên. Làm thêm workshop **AWS Backup**: backup plan, vault, tag-based assignment, SNS notifications, kiểm thử restore tự động bằng Lambda và kiểm tra CloudWatch Logs. | Tăng tốc thao tác AWS bằng CLI, hiểu tư duy vận hành backup chuyên nghiệp có kiểm thử restore. |
| **30/04/2026** | Workshop **VM Import/Export**: tạo VM Ubuntu local, export VMDK, upload S3, tạo role `vmimport`, import thành AMI, launch EC2 từ AMI; chiều ngược lại export instance/image về lại môi trường on-prem. Thực hành thêm workshop **Deploy Application on Docker**: build image, network, docker run, docker compose, push image lên ECR/Docker Hub. | Hiểu quy trình migration VM hai chiều và nền tảng container hóa ứng dụng trên AWS. |

### Khó khăn gặp phải trong tuần 2:

* Ban đầu khó phân biệt rõ **IAM Role** và **IAM User** trong ngữ cảnh cấp quyền thực tế.
* Chưa quen đọc/viết **IAM Policy JSON**, dễ nhầm scope quyền.
* Workshop mạng (VPC/VPN/Hybrid DNS) có nhiều thành phần nên dễ sai thứ tự cấu hình.
* Khi làm RDS/Aurora và nhiều workshop liên tiếp, dễ sót tài nguyên ở region khác gây phát sinh chi phí.
* Với AWS CLI, lúc đầu khó nhớ đầy đủ tham số lệnh và ARN khi thao tác dịch vụ phức tạp.

### Cách xử lý:

* Tách từng workshop thành checklist nhỏ theo đúng thứ tự thao tác.
* Dùng CloudWatch Logs/Reachability Analyzer để debug thay vì đoán lỗi.
* Áp dụng quy tắc “xong bài nào dọn bài đó” + kiểm tra tài nguyên theo từng region.
* Đặt ngưỡng cảnh báo AWS Budgets nhiều mức (50/80/100%) để phát hiện sớm.
* Dùng profile CLI riêng và lưu các lệnh mẫu quan trọng để tái sử dụng.

### Kết quả đạt được tuần 2:

* Hoàn thành chuỗi workshop thực hành trọng tâm của tuần.
* Cải thiện rõ khả năng triển khai hạ tầng, giám sát, backup và automation trên AWS.
* Nâng cao ý thức bảo mật quyền truy cập IAM và kiểm soát chi phí cloud.
* Tự tin hơn khi chuyển từ thao tác console sang thao tác CLI/script.

### Bài học rút ra:

* IAM là nền tảng phải nắm chắc trước khi đi sâu dịch vụ khác.
* Monitoring và Backup chỉ có ý nghĩa khi có kiểm thử khôi phục và cảnh báo chủ động.
* Kiểm soát chi phí cần làm song song với kỹ thuật ngay từ đầu, không để đến cuối tháng.
* Quy trình chuẩn (triển khai -> kiểm thử -> dọn tài nguyên) giúp giảm rủi ro vận hành thực tế.

