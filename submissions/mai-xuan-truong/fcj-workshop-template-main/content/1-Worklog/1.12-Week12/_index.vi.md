---
title: "Tuần 12"
date: 2026-07-06
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

**Mốc thời gian:** 06/07/2026 - 30/07/2026

> Dự án IRMS được thực hiện bởi nhóm 5 thành viên. Các ghi chú dưới đây tập trung vào phần đóng góp cá nhân của tôi trong quá trình phối hợp với nhóm.

## Ngày 1 - 24/6: Deploy frontend lên S3

**Công việc đã thực hiện:** Tôi build frontend bằng `npm run build`, kiểm tra thư mục `dist/` và sync static assets lên S3 frontend bucket. Sau khi upload, tôi kiểm tra `index.html`, asset path và lỗi console trên trình duyệt. Vấn đề gặp phải là build local cũ còn sót, nên tôi build lại trước khi sync lần cuối.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 2 - 25/6: Cấu hình CloudFront

**Công việc đã thực hiện:** Tôi kiểm tra CloudFront distribution, origin, default root object, HTTPS behavior và cache behavior. Tôi phối hợp với nhóm để đảm bảo frontend vẫn gọi backend qua API Gateway. Khó khăn chính là thời gian propagation, vì vậy tôi tách lỗi cấu hình khỏi trạng thái đang deploy.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 3 - 26/6: CloudFront invalidation

**Công việc đã thực hiện:** Sau khi frontend thay đổi, tôi tạo invalidation cho `/*` và so sánh kết quả trước/sau khi clear cache. Một số trình duyệt vẫn hiển thị bundle cũ nên tôi dùng thêm hard refresh để xác minh. Bước này được đưa vào phần deployment của workshop.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 4 - 27/6: End-to-end testing cùng nhóm

**Công việc đã thực hiện:** Tôi tham gia test luồng login, Incident CRUD, Timeline, Evidence Upload, Report và AI Assistant. Phần tôi tập trung là Cognito token, API Gateway routes, Lambda logs, S3 evidence upload và CloudFront access. Lỗi CORS được xử lý bằng cách kiểm tra header API Gateway và redeploy stage.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 5 - 28/6: Rà soát chi phí và tài nguyên

**Công việc đã thực hiện:** Tôi kiểm tra Billing, Cost Explorer, CloudWatch Logs, S3, Lambda, API Gateway, CloudFront, DynamoDB, Secrets Manager, SNS và EventBridge. Khó khăn là phân biệt resource của project với resource lab cũ. Bài học là cần đặt tên và tag resource nhất quán.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 6 - 29/6: Chuẩn bị cleanup checklist

**Công việc đã thực hiện:** Tôi lập thứ tự cleanup cho CloudFront, S3 buckets, SAM stack, DynamoDB, log groups, EventBridge rules, SNS topic và Secrets Manager secret. Vấn đề là một số resource có dependency, ví dụ bucket còn object hoặc CloudFront chưa disable xong.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 7 - 30/6: Chỉnh workshop phần hạ tầng

**Công việc đã thực hiện:** Tôi chỉnh các phần architecture, prerequisites, Cognito, API Gateway, DynamoDB, S3, Lambda, EventBridge, SNS và Secrets Manager. Vấn đề là numbering giữa English/Vietnamese chưa đồng bộ, nên tôi căn lại sidebar và heading.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 8 - 1/7: Rà soát tài liệu backend AWS

**Công việc đã thực hiện:** Tôi kiểm tra bảng trách nhiệm Lambda, DynamoDB integration, EventBridge flow và CloudWatch logging. Một số code block bị render sai do thiếu fence Markdown, nên tôi sửa định dạng để nội dung không bị biến thành heading lớn.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 9 - 2/7: Cập nhật frontend deployment

**Công việc đã thực hiện:** Tôi bổ sung tài liệu build React + Vite, sync S3, deploy CloudFront và invalidation. Tôi kiểm tra ảnh trong `static/images`. Vấn đề là wording cũ còn mô tả direct S3 website, nên tôi cập nhật lại theo S3 + CloudFront.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 10 - 3/7: Đồng bộ tài liệu song ngữ

**Công việc đã thực hiện:** Tôi so sánh `_index.md` và `_index.vi.md` ở Worklog, Proposal, Workshop, Self-Assessment và Feedback. Vấn đề là một số trang English còn lẫn tiếng Việt hoặc bản Việt còn nội dung cũ. Tôi đồng bộ ý nghĩa thay vì dịch máy từng câu.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 11 - 4/7: Rà soát Proposal IRMS

**Công việc đã thực hiện:** Tôi đối chiếu Proposal với kiến trúc cuối cùng và phân công nhóm. Vấn đề là Proposal vẫn còn nhắc provider AI cũ, nên tôi cập nhật Groq là provider hiện tại và Bedrock là future enhancement.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 12 - 5/7: Chỉnh Worklog cá nhân

**Công việc đã thực hiện:** Tôi viết lại Worklog theo vai trò cá nhân trong nhóm 5 người, tập trung vào AWS infrastructure, deployment, testing và documentation. Vấn đề là nội dung cũ lặp lại nhiều, nên tôi thay bằng task, công cụ, lỗi và bài học cụ thể.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 13 - 6/7: Chạy Hugo build

**Công việc đã thực hiện:** Tôi chạy Hugo build để kiểm tra Markdown, shortcode, front matter và image references. Build pass chưa đủ, nên tôi mở thêm một số trang để kiểm tra hiển thị. Bài học là validation cần có cả build và visual check.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 14 - 7/7: Kiểm tra chức năng cuối

**Công việc đã thực hiện:** Tôi đối chiếu workshop với demo flow: Cognito, API Gateway, Incident CRUD, Timeline, Evidence Upload, Report, Alert Handler và AI Assistant. Vấn đề là API examples chưa đồng bộ, nên tôi cập nhật theo endpoint cuối cùng.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 15 - 8/7: Dọn resource test

**Công việc đã thực hiện:** Tôi kiểm tra resource test và ghi cleanup guidance. Các dịch vụ liên quan gồm S3, CloudFront, Lambda, CloudWatch, DynamoDB, EventBridge, SNS và Secrets Manager. Bài học là cần có kế hoạch cleanup trước final demo.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 16 - 9/7: Hoàn thiện layout báo cáo

**Công việc đã thực hiện:** Tôi rà soát format, paragraph, ảnh, sidebar numbering và lỗi song ngữ. Một số section name cũ và nội dung copy từ template được chỉnh lại trong khi vẫn giữ cấu trúc Hugo ban đầu.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 17 - 10/7: Chuẩn bị bản final đầu tiên

**Công việc đã thực hiện:** Tôi build Hugo và kiểm tra 7 mục lớn của report. Vấn đề còn lại là tài liệu chưa phản ánh đầy đủ final AI implementation, nên tôi ghi lại các điểm cần chỉnh trong giai đoạn gia hạn.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 18 - 11/7: Khảo sát Bedrock như provider tương lai

**Công việc đã thực hiện:** Tôi xem Bedrock có thể nằm sau provider abstraction như thế nào nhưng không ghi là đã deploy. Vấn đề là tránh mâu thuẫn giữa Proposal và Workshop, nên tôi phân biệt rõ implemented architecture và future option.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 19 - 12/7: Lập kế hoạch cập nhật Groq

**Công việc đã thực hiện:** Tôi map lại AI flow từ frontend đến API Gateway, Lambda, Groq, JSON response và fallback. Vấn đề là nhiều trang còn wording cũ, nên tôi lập danh sách cleanup cho các reference provider.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 20 - 13/7: Cập nhật Secrets Manager guidance

**Công việc đã thực hiện:** Tôi rà lại tài liệu secret handling và nhấn mạnh frontend không có API key. Vấn đề là không được publish secrets hoặc password thật, nên tôi dùng placeholder trong mọi ví dụ.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 21 - 14/7: Kiểm tra AI endpoint examples

**Công việc đã thực hiện:** Tôi rà soát `/ai/analyze`, `/ai/explain` và `/ai/chat`, gồm request body, response fields, provider name, model và fallback flag. Vấn đề là field name chưa đồng bộ, nên tôi chuẩn hóa example JSON.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 22 - 15/7: Rà soát Cognito và API Gateway security

**Công việc đã thực hiện:** Tôi kiểm tra Cognito JWT authorizer, Authorization header và protected routes. Các demo password được thay bằng `YOUR_PASSWORD` hoặc `YOUR_TEMP_PASSWORD`. Bài học là tài liệu cũng phải tuân thủ nguyên tắc bảo mật.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 23 - 16/7: Cập nhật sơ đồ kiến trúc

**Công việc đã thực hiện:** Tôi thay sơ đồ kiến trúc trong Proposal và Workshop bằng bản cuối có Groq. Tôi kiểm tra path và hash sau khi copy. Vấn đề là browser cache nên cần hard refresh để thấy ảnh mới.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 24 - 17/7: Publish report lên GitHub Pages

**Công việc đã thực hiện:** Tôi cấu hình GitHub Pages, thêm Live Demo link, build Hugo với production baseURL, push branch và kiểm tra URL trả HTTP 200. Vấn đề là workflow phải nằm ở root repo mới chạy.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 25 - 18/7: Bắt đầu final consistency review

**Công việc đã thực hiện:** Tôi rà Proposal, Worklog, Workshop, Results và config để kiểm Groq, thời gian thực tập, metadata, credentials và wording. Bài học là phải xem report như một sản phẩm thống nhất.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 26 - 19/7: Chỉnh cost analysis

**Công việc đã thực hiện:** Tôi chỉnh wording chi phí để không claim credit/free-tier offset nếu không có bằng chứng. Nội dung tập trung vào Lambda, API Gateway, CloudFront, S3, DynamoDB, Secrets Manager và Groq development usage.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 27 - 20/7: Kiểm tra environment variables

**Công việc đã thực hiện:** Tôi đồng bộ `AIProvider`, `GroqSecretName`, `GroqModel`, `GroqTimeoutSeconds` trong bảng, ví dụ Python và deployment notes. Vấn đề là không để lẫn nhiều naming style.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 28 - 21/7: Proofread English pages

**Công việc đã thực hiện:** Tôi đọc các trang English để sửa ngữ pháp và câu hướng dẫn chưa tự nhiên. Tôi giữ nguyên giải thích kỹ thuật, chỉ chỉnh cách diễn đạt cho chuyên nghiệp hơn.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 29 - 22/7: Đồng bộ bản tiếng Việt

**Công việc đã thực hiện:** Tôi đối chiếu bản Việt với nội dung English sau khi cập nhật final implementation. Tôi không đổi cấu trúc hoặc theme, chỉ đồng bộ ý nghĩa và sửa chỗ lệch nội dung.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 30 - 23/7: Kiểm tra image references

**Công việc đã thực hiện:** Tôi kiểm tra ảnh trong Proposal và Workshop sau khi thay sơ đồ. Vấn đề là hai phần dùng hai path khác nhau, nên cần cập nhật cả hai file ảnh.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 31 - 24/7: Rà soát API documentation

**Công việc đã thực hiện:** Tôi kiểm tra các endpoint `/incidents`, `/evidence`, `/reports`, `/ai/analyze`, `/ai/explain`, `/ai/chat`. Vấn đề là tài liệu cũ chỉ có một endpoint AI, nên tôi bổ sung đủ ba endpoint.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 32 - 25/7: Điều chỉnh theo feedback

**Công việc đã thực hiện:** Tôi chỉnh các phần mentor feedback liên quan đến clarity, professional tone và architecture accuracy. Route 53, WAF và Bedrock được ghi rõ là Future Enhancement nếu chưa deploy thật.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 33 - 26/7: Final Hugo validation

**Công việc đã thực hiện:** Tôi chạy `hugo --minify --baseURL https://mxt2003.github.io/Internship/` để kiểm build production. Vấn đề là lỗi chỉ xuất hiện khi dùng production baseURL, nên tôi đưa bước này vào checklist cuối.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 34 - 27/7: Kiểm tra GitHub Pages output

**Công việc đã thực hiện:** Tôi so sánh live demo với local build, kiểm navigation, language switch, ảnh và các section chính. Vấn đề là cache trình duyệt, nên tôi dùng hard refresh và kiểm deployed static files.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 35 - 28/7: Polish final report

**Công việc đã thực hiện:** Tôi chỉnh transition giữa Proposal, Workshop, Results, Self-Assessment và Feedback. Tôi giảm câu lặp và làm văn phong kỹ thuật nhất quán hơn.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 36 - 29/7: Chuẩn bị final verification notes

**Công việc đã thực hiện:** Tôi lập checklist: không còn old AI provider, Groq documented, credentials replaced, dates updated, Hugo build success và GitHub Pages live. Tôi dựa trên search/build output thay vì nhớ thủ công.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.

## Ngày 37 - 30/7: Hoàn tất báo cáo thực tập

**Công việc đã thực hiện:** Tôi hoàn tất final review, xác nhận report phản ánh đóng góp cá nhân trong nhóm 5 người, kiểm live demo, source branch và Hugo build. Bài học cuối là documentation phải đi cùng implementation đến ngày nộp.

**Công cụ và dịch vụ sử dụng:** AWS Console, AWS CLI, AWS SAM, CloudFront, S3, API Gateway, Cognito, Lambda, DynamoDB, EventBridge, SNS, Secrets Manager, CloudWatch, Groq, Hugo, GitHub Pages và browser developer tools tùy theo công việc trong ngày.
