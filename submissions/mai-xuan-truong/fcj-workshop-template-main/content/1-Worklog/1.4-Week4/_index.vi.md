---
title: "Tuần 4"
date: 2026-05-07
weight: 4
chapter: false
pre: " <b> 1.4. </b> "
---

**Mốc thời gian:** 7/5 → 12/5 (6 ngày)

> Dự án IRMS được thực hiện bởi nhóm 5 thành viên. Các ghi chú dưới đây tập trung vào phần đóng góp cá nhân của tôi trong quá trình phối hợp với nhóm.

## Ngày 1 - 7/5: Thảo luận chọn đề tài IRMS

**Công việc đã thực hiện:** Tham gia buổi trao đổi với nhóm 5 thành viên để thống nhất đề tài IRMS. Phần đóng góp cá nhân của tôi là phân tích hướng triển khai bằng AWS serverless, xác định các dịch vụ phù hợp như API Gateway, Lambda, DynamoDB, S3 và CloudFront.

Cụ thể, tôi chuẩn bị một số tiêu chí để so sánh đề tài như mức độ dùng được AWS, khả năng demo, chi phí dự kiến và phạm vi phù hợp với thời gian thực tập. Tôi cũng ghi lại các chức năng nên nằm trong MVP để nhóm không bị sa vào các tính năng quá lớn ngay từ đầu.

**Kiến thức đã học:** Hiểu rõ hơn cách chọn đề tài theo năng lực của nhóm, thời gian thực tập và khả năng demo thực tế trên AWS.

**Kết quả đạt được:** Nhóm thống nhất chọn IRMS, còn tôi nhận hướng phụ trách chính về hạ tầng AWS, triển khai và kiểm thử.

**Khó khăn và bài học:** Phạm vi ban đầu khá rộng. Bài học là cần chia rõ trách nhiệm để tránh một người bị hiểu là làm toàn bộ hệ thống.

## Ngày 2 - 8/5: Phân tích yêu cầu cùng nhóm

**Công việc đã thực hiện:** Cùng nhóm phân tích các vai trò trong hệ thống như Admin, Security Manager, Security Analyst và Viewer. Tôi tập trung vào phần yêu cầu liên quan đến xác thực, phân quyền và cách API cần bảo vệ bằng Cognito.

Tôi đọc lại các tình huống xử lý sự cố như incident mới, phân công người xử lý, cập nhật trạng thái và lưu bằng chứng. Sau buổi trao đổi, tôi tổng hợp các yêu cầu liên quan đến quyền truy cập để chuẩn bị cho phần Cognito và API Gateway Authorizer.

**Kiến thức đã học:** Học cách chuyển yêu cầu nghiệp vụ thành nhóm chức năng kỹ thuật, đặc biệt là RBAC và luồng gọi API an toàn.

**Kết quả đạt được:** Có danh sách yêu cầu chức năng ở mức MVP và các điểm tôi cần chuẩn bị cho hạ tầng AWS.

**Khó khăn và bài học:** Khó khăn là nhiều chức năng bảo mật dễ bị mở rộng quá mức. Tôi rút ra rằng MVP cần đủ dùng trước khi thêm tính năng nâng cao.

## Ngày 3 - 9/5: Đóng góp thiết kế kiến trúc serverless

**Công việc đã thực hiện:** Tham gia vẽ kiến trúc tổng thể của IRMS. Tôi đề xuất luồng CloudFront phân phối frontend, API Gateway làm entry point, Lambda xử lý nghiệp vụ và DynamoDB lưu dữ liệu chính.

Tôi đối chiếu từng thành phần với trách nhiệm cụ thể: CloudFront cho frontend, API Gateway cho entry point, Lambda cho xử lý nghiệp vụ và DynamoDB cho dữ liệu. Tôi cũng ghi chú các điểm cần kiểm thử sau này như CORS, permission và chi phí tài nguyên.

**Kiến thức đã học:** Hiểu rõ hơn cách các dịch vụ serverless phối hợp với nhau và vì sao mô hình này phù hợp với project thực tập có chi phí thấp.

**Kết quả đạt được:** Có bản kiến trúc ban đầu để cả nhóm dùng làm nền khi chia việc backend, frontend và tài liệu.

**Khó khăn và bài học:** Bài học là sơ đồ kiến trúc phải thể hiện đúng trách nhiệm từng dịch vụ, không chỉ liệt kê dịch vụ AWS.

## Ngày 4 - 10/5: Hỗ trợ thiết kế dữ liệu DynamoDB

**Công việc đã thực hiện:** Phối hợp với các bạn phụ trách nghiệp vụ để xác định dữ liệu cần lưu cho Incident, Timeline, Users và EvidenceMetadata. Tôi tập trung kiểm tra cách Lambda sẽ đọc/ghi DynamoDB theo access pattern.

Tôi xem các màn hình dự kiến của hệ thống để đoán các truy vấn cần dùng, ví dụ danh sách incident theo trạng thái, timeline theo incident và evidence metadata theo file. Từ đó tôi góp ý về key, GSI và cách đặt tên bảng sao cho dễ dùng trong Lambda.

**Kiến thức đã học:** Học cách thiết kế DynamoDB theo truy vấn cần dùng thay vì theo thói quen database quan hệ.

**Kết quả đạt được:** Có bản nháp data model để phục vụ thiết kế API và triển khai Lambda sau này.

**Khó khăn và bài học:** Khó khăn là phải cân bằng giữa thiết kế đơn giản và đủ truy vấn cho dashboard. Tôi ghi lại các điểm cần kiểm thử sau.

## Ngày 5 - 11/5: Góp ý thiết kế API

**Công việc đã thực hiện:** Tham gia review danh sách endpoint cho incident, timeline, evidence, report và alert. Phần cá nhân của tôi là kiểm tra method, path và cách API Gateway sẽ map request đến Lambda.

Tôi rà lại từng endpoint theo góc nhìn người tích hợp hạ tầng: path có rõ không, method có đúng nghiệp vụ không, endpoint nào cần bảo vệ bằng Cognito. Tôi cũng ghi chú các response mẫu để về sau test bằng API Gateway dễ hơn.

**Kiến thức đã học:** Hiểu rằng API contract cần ổn định để backend và frontend làm song song mà ít bị lệch.

**Kết quả đạt được:** Có bảng endpoint ban đầu và quy ước response để dùng khi test API.

**Khó khăn và bài học:** Bài học là cần thống nhất naming sớm, vì đổi path sau khi frontend đã gọi API sẽ tốn nhiều thời gian.

## Ngày 6 - 12/5: Chuẩn bị Proposal theo phần phụ trách

**Công việc đã thực hiện:** Cùng nhóm hoàn thiện proposal IRMS. Tôi viết và rà soát các phần liên quan đến AWS architecture, service mapping, triển khai serverless và luồng vận hành trên cloud.

Tôi bổ sung phần giải thích vì sao nhóm chọn kiến trúc serverless, vai trò của từng dịch vụ AWS và hướng triển khai demo. Nội dung này sau đó được dùng lại khi viết phần Proposal và phần giới thiệu Workshop.

**Kiến thức đã học:** Học cách trình bày đóng góp kỹ thuật cá nhân trong một proposal chung của nhóm.

**Kết quả đạt được:** Proposal có phần kiến trúc và dịch vụ AWS rõ hơn, làm nền cho workshop sau này.

**Khó khăn và bài học:** Cần tránh viết proposal như một người làm tất cả. Tôi điều chỉnh câu chữ theo hướng dự án nhóm có phân công.
