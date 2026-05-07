---
title: "Worklog Tuần 1"
date: 2026-04-20
weight: 1
chapter: false
pre: " <b> 1.1. </b> "
---
{{% notice warning %}}
⚠️ **Lưu ý:** Các thông tin dưới đây chỉ nhằm mục đích tham khảo, vui lòng **không sao chép nguyên văn** cho bài báo cáo của bạn kể cả warning này.
{{% /notice %}}

### Mục tiêu tuần 1 (20/04/2026 - 25/04/2026):

* Tạo và kích hoạt tài khoản AWS để bắt đầu thực hành.
* Hoàn thành các nhiệm vụ nền tảng trong chương trình nhận credit.
* Làm quen cách kiểm soát chi phí và kiểm tra tài nguyên theo từng region.
* Bắt đầu viết worklog và đưa nội dung lên GitHub.

### Nhật ký công việc theo ngày:

| Ngày | Nội dung thực hiện | Kết quả |
| --- | --- | --- |
| Ngày 1 (20/04/2026) | Tạo tài khoản AWS lần đầu. Gặp lỗi tài khoản bị **suspend** nên chưa thể tiếp tục các nhiệm vụ thực hành. | Chưa tạo thành công, xác định được vấn đề chính là bước xác minh tài khoản. |
| Ngày 2 (21/04/2026) | Tiếp tục xử lý vấn đề tạo tài khoản. Sau nhiều lần thử, áp dụng giải pháp thuê số điện thoại để xác minh, sau đó tài khoản hoạt động bình thường. Bắt đầu làm chương trình 5 nhiệm vụ để nhận 100$ credit và hoàn thành được: **EC2**, **AWS Budgets**, **AWS Lambda**. | Tạo tài khoản thành công và hoàn thành 3/5 nhiệm vụ. |
| Ngày 3 (22/04/2026) | Làm tiếp các nhiệm vụ còn lại: **RDS Database** và **Amazon Bedrock**. | Hoàn thành đủ 5 nhiệm vụ theo kế hoạch tuần. |
| Ngày 4 (23/04/2026) | Nghiên cứu cách viết worklog: cấu trúc nội dung, cách mô tả tiến độ theo ngày, cách ghi vấn đề và bài học rút ra. | Nắm được format worklog để bắt đầu viết bài bản. |
| Ngày 5 (24/04/2026) | Kiểm tra billing và phát hiện bị tính phí **Relational Database Service: 8.78$** dù đã xóa tài nguyên chính. Rà soát lại toàn bộ dịch vụ, phát hiện khi làm Aurora/RDS có thử qua region **N. California** và quên tắt tài nguyên ở đó. Đăng nhập đúng region và xóa ngay. | Dừng phát sinh phí sai, rút kinh nghiệm kiểm tra tài nguyên đa region sau mỗi bài lab. |
| Ngày 6 (25/04/2026) | Tập viết worklog tuần 1 và đưa nội dung lên GitHub. | Hoàn thành bản worklog tuần đầu và sẵn sàng chuyển sang tuần 2. |

### Kết quả đạt được tuần 1:

* Đã tạo được tài khoản AWS sau khi xử lý sự cố suspend ban đầu.
* Hoàn thành 5 nhiệm vụ nhận credit (EC2, AWS Budgets, AWS Lambda, RDS Database, Amazon Bedrock).
* Bắt đầu có thói quen theo dõi billing và kiểm tra tài nguyên theo từng region.
* Hoàn thành bản worklog tuần 1 và làm quen quy trình cập nhật GitHub.

### Bài học rút ra:

* Luôn kiểm tra kỹ trạng thái tài khoản ngay từ bước đăng ký để tránh mất thời gian ở các ngày đầu.
* Sau mỗi lab liên quan đến RDS/Aurora, cần rà soát tài nguyên ở **tất cả region đã truy cập**, không chỉ region mặc định.
* Nên bật và theo dõi AWS Budgets sớm để phát hiện chi phí bất thường ngay trong ngày.
* Worklog càng ghi chi tiết theo ngày thì càng dễ tổng hợp tiến độ và báo cáo với mentor.

