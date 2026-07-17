---
title: "Tuần 12"
date: 2024-01-01
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

**Mốc thời gian:** 24/6 → 10/7 (giai đoạn tổng kết dài hơn)

> Dự án IRMS được thực hiện bởi nhóm 5 thành viên. Các ghi chú dưới đây tập trung vào phần đóng góp cá nhân của tôi trong quá trình phối hợp với nhóm.

## Ngày 1 - 24/6: Deploy frontend lên S3

**Công việc đã thực hiện:** Tôi phụ trách build production và upload static assets lên S3 hosting bucket. Nhóm cùng kiểm tra giao diện sau khi deploy.

Tôi build bản production, kiểm tra thư mục output rồi upload các static assets lên bucket hosting. Sau khi upload, tôi mở website để kiểm tra trang chính, đường dẫn asset và lỗi console.

**Kiến thức đã học:** S3 có thể dùng để hosting frontend tĩnh khi kết hợp CloudFront.

**Kết quả đạt được:** Có bản frontend deploy đầu tiên.

**Khó khăn và bài học:** Cần kiểm tra asset path và file index.html sau upload.

## Ngày 2 - 25/6: Cấu hình CloudFront

**Công việc đã thực hiện:** Tôi cấu hình/kiểm tra CloudFront distribution cho frontend và route phù hợp đến API. Đây là phần hạ tầng tôi phụ trách chính.

Tôi kiểm tra origin, cache behavior và route liên quan đến frontend/API. Sau khi distribution cập nhật, tôi test truy cập qua CloudFront thay vì chỉ mở trực tiếp S3.

**Kiến thức đã học:** CloudFront giúp có entry point ổn định và cache nội dung tĩnh.

**Kết quả đạt được:** Website truy cập ổn định hơn qua CloudFront.

**Khó khăn và bài học:** Cần chờ distribution deploy và kiểm tra cache behavior.

## Ngày 3 - 26/6: CloudFront invalidation

**Công việc đã thực hiện:** Sau khi frontend thay đổi, tôi thực hiện invalidation để bản mới hiển thị đúng. Tôi ghi lại bước này cho workshop deployment.

Tôi tạo invalidation sau khi frontend thay đổi để tránh trình duyệt nhận bản cũ. Tôi ghi lại khi nào cần invalidation và đường dẫn nên invalidate trong phần tài liệu deployment.

**Kiến thức đã học:** Cache invalidation là bước quan trọng khi cập nhật frontend tĩnh.

**Kết quả đạt được:** Các thay đổi giao diện được cập nhật đúng hơn.

**Khó khăn và bài học:** Cần dùng invalidation hợp lý, không lạm dụng.

## Ngày 4 - 27/6: End-to-end testing cùng nhóm

**Công việc đã thực hiện:** Cùng nhóm test toàn bộ luồng từ đăng nhập, tạo incident, timeline, evidence, report đến AI Assistant. Tôi tập trung phần AWS/API/deployment và ghi lỗi tích hợp.

Tôi cùng nhóm chạy demo flow đầy đủ và tập trung ghi lỗi thuộc AWS/API/deployment. Tôi test lại sau mỗi lần sửa để đảm bảo các phần tích hợp không làm hỏng luồng khác.

**Kiến thức đã học:** End-to-end test giúp phát hiện lỗi nằm giữa các phần của hệ thống.

**Kết quả đạt được:** Các luồng chính đạt mức demo được.

**Khó khăn và bài học:** Cần phân loại lỗi theo frontend, backend, hạ tầng để sửa nhanh.

## Ngày 5 - 28/6: Cost analysis

**Công việc đã thực hiện:** Tôi kiểm tra Billing/Cost Explorer và rà lại các dịch vụ AWS đang dùng trong IRMS. Kết quả được đưa vào phần phân tích chi phí.

Tôi kiểm tra Billing, Cost Explorer và các resource còn chạy. Tôi ghi chú dịch vụ nào có khả năng phát sinh phí như CloudFront, S3 storage, CloudWatch logs hoặc tài nguyên chưa dọn.

**Kiến thức đã học:** Cost awareness là kỹ năng quan trọng khi làm project trên AWS.

**Kết quả đạt được:** Có ghi chú chi phí cho tài liệu cuối.

**Khó khăn và bài học:** Cần theo dõi log, S3 storage, API request và tài nguyên còn chạy.

## Ngày 6 - 29/6: Lập checklist cleanup

**Công việc đã thực hiện:** Tôi lập checklist tài nguyên cần dọn sau demo: SAM stack, S3 bucket, CloudFront distribution, log group và resource phụ.

Tôi liệt kê thứ tự dọn tài nguyên để tránh lỗi phụ thuộc, ví dụ dọn object trong bucket trước, kiểm tra stack SAM và log group. Checklist này được đưa vào phần cleanup của workshop.

**Kiến thức đã học:** Cleanup giúp tránh phát sinh chi phí sau khi kết thúc project.

**Kết quả đạt được:** Có checklist cleanup để đưa vào workshop.

**Khó khăn và bài học:** Một số tài nguyên cần xóa theo thứ tự, ví dụ bucket còn object hoặc CloudFront còn distribution.

## Ngày 7 - 30/6: Biên tập workshop phần hạ tầng

**Công việc đã thực hiện:** Tôi biên tập các phần workshop liên quan đến kiến trúc, prerequisite và cấu hình hạ tầng AWS.

Tôi chỉnh lại nội dung về kiến trúc, điều kiện tiên quyết và các bước cấu hình hạ tầng AWS. Tôi thêm ảnh/sơ đồ khi cần để người đọc dễ hình dung hơn.

**Kiến thức đã học:** Tài liệu workshop cần phản ánh đúng phần đã triển khai thực tế.

**Kết quả đạt được:** Các mục đầu của workshop rõ hơn.

**Khó khăn và bài học:** Cần giữ numbering và sidebar nhất quán.

## Ngày 8 - 1/7: Biên tập workshop backend AWS

**Công việc đã thực hiện:** Tôi viết/rá soát các bước Cognito, API Gateway, Lambda, DynamoDB, EventBridge và SNS theo phần mình tham gia.

Tôi rà soát các bước Cognito, API Gateway, Lambda, DynamoDB, EventBridge và SNS để nội dung sát với phần tôi đã triển khai/test. Tôi cũng sửa lại numbering và format code block.

**Kiến thức đã học:** Tài liệu kỹ thuật cần đủ bước để người khác làm lại được.

**Kết quả đạt được:** Nội dung backend AWS dễ theo dõi hơn.

**Khó khăn và bài học:** Cần đưa lệnh và cấu hình vào đúng định dạng.

## Ngày 9 - 2/7: Biên tập deployment/frontend

**Công việc đã thực hiện:** Tôi bổ sung phần React integration, build frontend, deploy S3, CloudFront và invalidation trong workshop.

Tôi bổ sung bước build React, upload S3, cấu hình CloudFront và invalidation. Tôi kiểm tra link ảnh, đường dẫn nội bộ và cách trình bày để workshop không bị đứt mạch.

**Kiến thức đã học:** Frontend deployment cần được mô tả liền với hạ tầng hosting.

**Kết quả đạt được:** Workshop có phần deploy web hoàn chỉnh hơn.

**Khó khăn và bài học:** Cần kiểm tra link ảnh và đường dẫn nội bộ.

## Ngày 10 - 3/7: Đồng bộ nội dung song ngữ

**Công việc đã thực hiện:** Tôi rà soát `_index.vi.md` và `_index.md` để tránh lệch nội dung giữa tiếng Việt và tiếng Anh.

Tôi rà soát các trang tiếng Việt và tiếng Anh để tránh hai bên khác nội dung quá nhiều. Khi thấy trang nào chỉ có placeholder hoặc dịch chưa đúng, tôi ghi chú để sửa lại.

**Kiến thức đã học:** Website song ngữ cần cùng cấu trúc, chỉ khác ngôn ngữ.

**Kết quả đạt được:** Giảm tình trạng hai bản khác nhau quá nhiều.

**Khó khăn và bài học:** Không nên copy tiếng Việt sang file English hoặc ngược lại.

## Ngày 11 - 4/7: Rà soát Proposal IRMS

**Công việc đã thực hiện:** Tôi kiểm tra lại Proposal để bảo đảm đúng đề tài IRMS của nhóm, không dùng nội dung mẫu của dự án khác.

Tôi kiểm tra Proposal để đảm bảo nội dung là IRMS của nhóm, không phải dự án mẫu khác. Tôi cũng đưa ảnh kiến trúc đúng sang phần Workshop để các phần tài liệu thống nhất.

**Kiến thức đã học:** Nội dung báo cáo phải đúng ownership và đúng project.

**Kết quả đạt được:** Proposal khớp hơn với IRMS.

**Khó khăn và bài học:** Cần kiểm tra kỹ tài liệu mẫu trước khi đưa vào submission.

## Ngày 12 - 5/7: Biên tập Worklog cá nhân

**Công việc đã thực hiện:** Tôi biên tập Worklog để phản ánh đúng hoạt động cá nhân trong team 5 người, không phóng đại phạm vi đóng góp cá nhân.

Tôi chỉnh Worklog theo hướng phản ánh đúng vai trò cá nhân trong team 5 người. Nội dung được viết lại để có phần việc cụ thể của tôi, phần phối hợp nhóm và bài học rút ra.

**Kiến thức đã học:** Worklog thực tập cần trung thực về vai trò cá nhân và hợp tác nhóm.

**Kết quả đạt được:** Worklog phù hợp hơn với thực tế dự án nhóm.

**Khó khăn và bài học:** Cần dùng các từ như tham gia, hỗ trợ, phụ trách, phối hợp đúng ngữ cảnh.

## Ngày 13 - 6/7: Build và kiểm tra Hugo

**Công việc đã thực hiện:** Tôi chạy Hugo build để kiểm tra Markdown, shortcode, ảnh và link sau khi chỉnh tài liệu.

Tôi chạy Hugo build sau khi sửa tài liệu để phát hiện lỗi Markdown, shortcode, ảnh và link. Nếu build pass, tôi tiếp tục kiểm tra một số trang trên website để xem có lỗi trình bày không.

**Kiến thức đã học:** Build validation giúp phát hiện lỗi tài liệu trước khi nộp.

**Kết quả đạt được:** Website build thành công sau chỉnh sửa.

**Khó khăn và bài học:** Cần kiểm tra cả bản tiếng Việt và tiếng Anh.

## Ngày 14 - 7/7: Kiểm tra chức năng cuối

**Công việc đã thực hiện:** Cùng nhóm đối chiếu các luồng demo với nội dung workshop. Tôi tập trung phần AWS, API, deploy và testing checklist.

Tôi đối chiếu các luồng demo với nội dung workshop để đảm bảo bước hướng dẫn khớp với hệ thống thật. Những điểm không còn đúng được ghi lại để sửa trong tài liệu.

**Kiến thức đã học:** Tài liệu phải khớp với cách hệ thống chạy thực tế.

**Kết quả đạt được:** Các nội dung chính nhất quán hơn.

**Khó khăn và bài học:** Nếu tài liệu và app lệch nhau, người đọc sẽ khó làm theo.

## Ngày 15 - 8/7: Dọn dẹp tài nguyên thử nghiệm

**Công việc đã thực hiện:** Tôi kiểm tra và dọn các tài nguyên thử nghiệm không cần giữ, đồng thời ghi lại hướng cleanup cho workshop.

Tôi kiểm tra lại các tài nguyên không còn cần dùng sau demo và chuẩn bị dọn để tránh chi phí. Tôi cũng ghi lại phần cleanup để người làm workshop biết nên xóa gì.

**Kiến thức đã học:** Quản lý tài nguyên AWS là trách nhiệm quan trọng sau demo.

**Kết quả đạt được:** Giảm rủi ro phát sinh chi phí không cần thiết.

**Khó khăn và bài học:** Cần kiểm tra nhiều region và resource phụ.

## Ngày 16 - 9/7: Hoàn thiện báo cáo

**Công việc đã thực hiện:** Tôi rà soát Proposal, Worklog, Workshop và các phần liên quan đến đóng góp cá nhân để chỉnh câu chữ và định dạng.

Tôi rà lại Proposal, Worklog và Workshop để sửa câu chữ, định dạng và lỗi song ngữ. Tôi ưu tiên làm cho nội dung rõ vai trò cá nhân, không bị quá ngắn hoặc quá chung chung.

**Kiến thức đã học:** Báo cáo cuối cần rõ ràng, nhất quán và không phóng đại vai trò cá nhân.

**Kết quả đạt được:** Nội dung báo cáo gọn và đúng hơn.

**Khó khăn và bài học:** Cần đọc lại từ góc nhìn người chấm và người làm theo workshop.

## Ngày 17 - 10/7: Tổng kết cá nhân

**Công việc đã thực hiện:** Tôi tổng kết phần đóng góp cá nhân trong dự án IRMS: AWS infrastructure, SAM, Cognito, API Gateway, Lambda/DynamoDB integration, EventBridge, SNS, CloudFront, frontend integration, testing và documentation.

Tôi tổng hợp lại các phần mình tham gia nhiều nhất: hạ tầng AWS, SAM, API Gateway, Cognito, Lambda/DynamoDB integration, EventBridge/SNS, CloudFront, frontend integration, testing và documentation. Đây là phần giúp tôi nhìn lại rõ quá trình thực tập của mình.

**Kiến thức đã học:** Dự án giúp tôi hiểu cách làm việc trong một nhóm phần mềm có phân công và tích hợp nhiều dịch vụ AWS.

**Kết quả đạt được:** Hoàn thành phần worklog và tài liệu phản ánh đúng vai trò cá nhân.

**Khó khăn và bài học:** Bài học lớn nhất là cần giao tiếp rõ, kiểm thử thường xuyên và ghi tài liệu song song với triển khai.
