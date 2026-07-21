---
title: "Tuần 12"
date: 2026-07-06
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

**Mốc thời gian:** 06/07/2026 - 21/07/2026

> Dự án IRMS được thực hiện bởi nhóm 5 thành viên. Các ghi chú dưới đây tập trung vào phần đóng góp cá nhân của tôi trong quá trình phối hợp với nhóm.

## Ngày 1 - 6/7: Kiểm thử backend và hạ tầng AWS

**Công việc đã thực hiện:** Tôi kiểm tra các phần backend và hạ tầng đã được nhóm triển khai, tập trung vào Cognito, API Gateway, Lambda, DynamoDB, S3 Evidence Store, EventBridge, SNS và CloudWatch Logs. Phần tôi chịu trách nhiệm chính là đảm bảo các dịch vụ AWS kết nối đúng với flow đã mô tả trong workshop.

Tôi test Cognito login, lấy JWT và gọi các API được bảo vệ. Khi gặp lỗi 401 hoặc CORS, tôi kiểm tra lại authorizer, route, stage deployment và response headers. Với Lambda, tôi xem log để xác định request có đi đúng hàm không, dữ liệu có ghi vào DynamoDB đúng table không và lỗi có được trả về rõ ràng không. Tôi cũng kiểm tra luồng evidence upload bằng presigned URL để đảm bảo file đi trực tiếp lên S3, còn metadata được lưu riêng.

**Kiến thức đã học:** Kiểm thử serverless cần đi từ trình duyệt đến API Gateway, Lambda, database và log, vì lỗi có thể nằm ở bất kỳ tầng nào.

**Kết quả đạt được:** Các luồng chính gồm authentication, Incident CRUD, Timeline và Evidence Upload ổn định hơn để tiếp tục test end-to-end.

**Khó khăn và bài học:** CORS và JWT là hai lỗi dễ gây nhầm lẫn, nên cần tách lỗi xác thực, lỗi route và lỗi backend khi debug.

## Ngày 2 - 8/7: Deploy, CloudFront và kiểm thử end-to-end

**Công việc đã thực hiện:** Tôi phối hợp với nhóm để kiểm tra bản frontend React + Vite sau khi build và deploy. Phần tôi tập trung là cấu hình API base URL, kiểm tra S3 hosting, CloudFront distribution, cache behavior và invalidation sau khi frontend thay đổi.

Tôi kiểm tra `npm run build`, thư mục `dist/`, asset path và lỗi console trên trình duyệt. Sau khi upload frontend lên S3 và truy cập qua CloudFront, tôi test lại login, tạo incident, cập nhật trạng thái, upload evidence, xem timeline và gọi report. Khi gặp trường hợp trình duyệt vẫn lấy bundle cũ, tôi tạo CloudFront invalidation cho `/*` và dùng hard refresh để đối chiếu.

```bash
npm run build
aws s3 sync dist/ s3://<frontend-bucket> --delete
aws cloudfront create-invalidation --distribution-id <distribution-id> --paths "/*"
```

**Kiến thức đã học:** Deploy frontend không chỉ là upload file, mà còn cần kiểm tra cache, base URL, HTTPS và khả năng gọi backend thật.

**Kết quả đạt được:** Frontend có thể chạy demo ổn định hơn qua CloudFront và gọi được các API chính.

**Khó khăn và bài học:** Nếu không invalidate cache, người xem có thể vẫn thấy giao diện hoặc JavaScript cũ dù source đã sửa.

## Ngày 3 - 10/7: Hoàn thiện Workshop theo flow triển khai

**Công việc đã thực hiện:** Tôi cập nhật các phần Workshop để khớp với flow IRMS cuối cùng: Introduction, Environment Setup, Infrastructure Configuration, Application Development, Deployment and Testing, Frontend Integration and Web Deployment, Results/Cost/Cleanup. Mục tiêu là tóm gọn mục nhưng không làm mất nội dung kỹ thuật quan trọng.

Tôi rà các đoạn từng bị dính dòng hoặc lẫn tiếng Việt không dấu trong bản English. Các đoạn flow dài như Lambda, S3 presigned URL, EventBridge, Secrets Manager và AI Assistant được tách lại thành bullet, bảng hoặc code block để dễ đọc hơn. Tôi cũng kiểm tra numbering 5.1, 5.2, 5.3 và các mục con để sidebar hiển thị đúng. Những thông tin nhạy cảm như password, access key, secret key, token và API key được thay bằng placeholder.

**Kiến thức đã học:** Workshop tốt cần đi theo đúng thứ tự người đọc thao tác, đồng thời phải bảo mật ngay cả trong ví dụ minh họa.

**Kết quả đạt được:** Nội dung Workshop dễ đọc hơn, đồng bộ hơn giữa tiếng Việt và tiếng Anh, và phản ánh đúng phần AWS mà tôi tham gia triển khai.

**Khó khăn và bài học:** Tài liệu copy từ quá trình làm việc thường bị dính câu, sai format hoặc thiếu context, nên phải kiểm tra từng trang thay vì sửa một lần chung chung.

## Ngày 4 - 14/7: Đồng bộ báo cáo, Proposal và Worklog

**Công việc đã thực hiện:** Tôi rà soát lại Proposal, Worklog, Events, Self-Assessment, Sharing and Feedback và README để nội dung thống nhất với dự án IRMS. Tôi kiểm tra lại sơ đồ kiến trúc, tên dịch vụ AWS, provider AI, thời gian thực tập, thông tin sinh viên và các link nội bộ.

Tôi thay sơ đồ kiến trúc mới vào cả Proposal và Workshop, sau đó kiểm tra đường dẫn ảnh trong `static/images`. Với phần tiếng Anh, tôi sửa các câu còn lẫn tiếng Việt hoặc dịch chưa tự nhiên. Với phần tiếng Việt, tôi chỉnh lỗi chính tả, xuống dòng và giọng văn để giống báo cáo thực tập cá nhân hơn. Tôi cũng rà Worklog để đảm bảo nội dung không viết như cả dự án do một mình tôi làm.

**Kiến thức đã học:** Một báo cáo thực tập cần thống nhất giữa nhiều phần, vì mentor có thể đối chiếu Proposal, Workshop, Worklog và kết quả triển khai.

**Kết quả đạt được:** Báo cáo nhất quán hơn về timeline, kiến trúc, vai trò cá nhân và cách gọi tên dịch vụ AWS.

**Khó khăn và bài học:** Khi sửa nhiều file song ngữ, cần kiểm tra cả ý nghĩa lẫn format, không chỉ dịch từng câu.

## Ngày 5 - 21/7: Hoàn tất báo cáo dự án

**Công việc đã thực hiện:** Tôi hoàn tất rà soát cuối theo tiến độ thực tế đến ngày 21/07/2026. Công việc gồm kiểm tra Hugo build, kiểm tra live demo trên GitHub Pages, xác nhận các trang chính hiển thị được, kiểm tra link nội bộ, ảnh kiến trúc, numbering sidebar và nội dung song ngữ.

Tôi chạy production build với base URL GitHub Pages, xem lại các warning của Hugo và xác nhận không có lỗi Markdown/front matter làm hỏng trang. Tôi cũng kiểm tra lần cuối các nội dung nhạy cảm để không publish email đăng nhập, password, access key, secret key, token hoặc API key. Phần cuối cùng là cập nhật Worklog để timeline phản ánh đúng: các tuần đầu là học AWS và làm lab, còn dự án IRMS bắt đầu từ tuần có ngày 01/07.

```bash
hugo --minify --baseURL https://mxt2003.github.io/Internship/
```

**Kiến thức đã học:** Hoàn thiện báo cáo không chỉ là viết nội dung, mà còn phải kiểm tra build, link, hình ảnh, bảo mật thông tin và sự nhất quán của toàn bộ website.

**Kết quả đạt được:** Báo cáo phản ánh đúng tiến độ thực tế, vai trò cá nhân trong nhóm và trạng thái hoàn thành dự án đến ngày 21/07/2026.

**Khó khăn và bài học:** Càng về cuối càng dễ sửa một chỗ làm lệch chỗ khác, nên cần kiểm tra theo checklist thay vì chỉ nhìn bằng mắt.
