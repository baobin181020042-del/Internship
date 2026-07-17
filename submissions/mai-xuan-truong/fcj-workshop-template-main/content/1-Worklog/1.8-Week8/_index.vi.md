---
title: "Tuần 8"
date: 2024-01-01
weight: 8
chapter: false
pre: " <b> 1.8. </b> "
---

**Mốc thời gian:** 31/5 → 5/6 (6 ngày)

> Dự án IRMS được thực hiện bởi nhóm 5 thành viên. Các ghi chú dưới đây tập trung vào phần đóng góp cá nhân của tôi trong quá trình phối hợp với nhóm.

## Ngày 1 - 31/5: Phụ trách AWS SAM template

**Công việc đã thực hiện:** Tôi phụ trách đưa các tài nguyên chính như API Gateway, Lambda, DynamoDB permission và environment variable vào SAM template. Nhóm review để đảm bảo khớp với kiến trúc.

Tôi đưa các phần hạ tầng đã làm thủ công vào template để có thể deploy lặp lại. Tôi kiểm tra parameter, output, policy và environment variable để template không chỉ chạy được mà còn dễ đọc cho người khác.

**Kiến thức đã học:** SAM giúp quản lý serverless infrastructure bằng code và dễ deploy lặp lại.

**Kết quả đạt được:** Có template nền cho các function và resource chính.

**Khó khăn và bài học:** Cần đặt logical ID, parameter và output rõ ràng.

## Ngày 2 - 1/6: Chạy sam validate

**Công việc đã thực hiện:** Tôi chạy `sam validate` để kiểm tra template trước khi build và sửa các lỗi tham chiếu resource.

Tôi chạy validate nhiều lần sau mỗi thay đổi template. Khi gặp lỗi, tôi đọc vị trí resource bị báo, sửa logical ID hoặc reference rồi chạy lại đến khi template hợp lệ.

```bash
sam validate
```

**Kiến thức đã học:** Validate sớm giúp tránh lỗi CloudFormation khi deploy.

**Kết quả đạt được:** Template giảm lỗi cú pháp và reference.

**Khó khăn và bài học:** Lỗi indentation hoặc logical ID rất nhỏ cũng làm deploy thất bại.

## Ngày 3 - 2/6: Chạy sam build

**Công việc đã thực hiện:** Tôi chạy `sam build` để đóng gói các Lambda function và kiểm tra dependency/runtime.

Tôi kiểm tra cấu trúc thư mục Lambda, runtime và dependency trước khi build. Sau khi build, tôi xem artifact được tạo ra để chắc function sẽ được đóng gói đúng khi deploy.

```bash
sam build
```

**Kiến thức đã học:** Build step cho biết source Lambda đã sẵn sàng để deploy hay chưa.

**Kết quả đạt được:** Các build artifact chính được tạo thành công.

**Khó khăn và bài học:** Cần kiểm tra đúng runtime và cấu trúc thư mục function.

## Ngày 4 - 3/6: Thực hiện sam deploy

**Công việc đã thực hiện:** Tôi thực hiện `sam deploy` và theo dõi CloudFormation events. Khi có lỗi, tôi ghi lại nguyên nhân để nhóm cùng xử lý.

Tôi theo dõi CloudFormation events trong lúc deploy và ghi lại các lỗi rollback. Khi stack tạo thành công, tôi lấy output như API endpoint để chuyển sang bước kiểm thử thật.

```bash
sam deploy
```

**Kiến thức đã học:** Deploy bằng SAM cần hiểu cả template lẫn lỗi từ CloudFormation.

**Kết quả đạt được:** Stack deploy được các tài nguyên chính cho môi trường test.

**Khó khăn và bài học:** Rollback làm mất thời gian, nên cần đọc lỗi cẩn thận trước khi chạy lại.

## Ngày 5 - 4/6: Kiểm thử sau deploy

**Công việc đã thực hiện:** Tôi lấy endpoint thật từ API Gateway và test các luồng chính sau khi deploy. Các lỗi môi trường được phân loại cho từng thành viên xử lý.

Tôi gọi lại các endpoint trên môi trường AWS thay vì chỉ dựa vào local. Tôi kiểm tra CloudWatch Logs song song để phân biệt lỗi do code, cấu hình API Gateway hay permission của Lambda.

**Kiến thức đã học:** Môi trường thật có thể phát sinh lỗi khác local, nhất là permission và environment variable.

**Kết quả đạt được:** Xác nhận nhiều endpoint chạy được trên AWS.

**Khó khăn và bài học:** Cần kiểm tra log CloudWatch song song khi test API.

## Ngày 6 - 5/6: Ghi tài liệu deployment

**Công việc đã thực hiện:** Tôi ghi lại quy trình SAM gồm validate, build, deploy, cách lấy output và cách kiểm tra stack. Nội dung này dùng lại cho workshop.

Tôi viết lại quy trình theo đúng thứ tự thao tác, gồm chuẩn bị cấu hình, validate, build, deploy và kiểm tra output. Các lệnh quan trọng được đưa vào code block để người đọc copy và chạy dễ hơn.

**Kiến thức đã học:** Tài liệu deploy phải đủ rõ để người khác làm lại được.

**Kết quả đạt được:** Có phần ghi chú Build & Deploy cho tài liệu nhóm.

**Khó khăn và bài học:** Cần đưa lệnh vào code block và tránh ghi chú rời rạc.
