---
title: "Week 12"
date: 2026-07-06
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

**Timeline:** July 6, 2026 - July 21, 2026

> IRMS was completed by a five-member team. The notes below focus on my individual contribution while collaborating with the team.

## Day 1 - 6/7: Backend and AWS infrastructure testing

**Work completed:** I checked the backend and infrastructure parts implemented by the team, focusing on Cognito, API Gateway, Lambda, DynamoDB, S3 Evidence Store, EventBridge, SNS, and CloudWatch Logs. My main responsibility was to ensure the AWS services connected correctly with the flow described in the workshop.

I tested Cognito login, retrieved a JWT, and called protected APIs. When I encountered 401 or CORS issues, I reviewed the authorizer, routes, stage deployment, and response headers. For Lambda, I checked logs to confirm that requests reached the correct functions, data was written to the right DynamoDB tables, and errors were returned clearly. I also tested evidence upload through presigned URLs to ensure files went directly to S3 while metadata was stored separately.

**Knowledge learned:** Serverless testing needs to trace the flow from browser to API Gateway, Lambda, database, and logs because errors can happen at any layer.

**Result achieved:** The main flows, including authentication, Incident CRUD, Timeline, and Evidence Upload, became more stable for end-to-end testing.

**Difficulty and lesson learned:** CORS and JWT errors can look similar at first, so authentication errors, routing errors, and backend errors should be debugged separately.

## Day 2 - 8/7: Deployment, CloudFront, and end-to-end testing

**Work completed:** I collaborated with the team to test the React + Vite frontend after build and deployment. My focus was API base URL configuration, S3 hosting, CloudFront distribution, cache behavior, and invalidation after frontend updates.

I checked `npm run build`, the `dist/` folder, asset paths, and browser console errors. After uploading the frontend to S3 and accessing it through CloudFront, I tested login, incident creation, status update, evidence upload, timeline viewing, and report generation. When the browser still loaded an old bundle, I created a CloudFront invalidation for `/*` and used hard refresh to compare the result.

```bash
npm run build
aws s3 sync dist/ s3://<frontend-bucket> --delete
aws cloudfront create-invalidation --distribution-id <distribution-id> --paths "/*"
```

**Knowledge learned:** Frontend deployment is not only uploading files; it also requires checking cache, base URLs, HTTPS behavior, and real backend calls.

**Result achieved:** The frontend could run more reliably through CloudFront and call the main APIs.

**Difficulty and lesson learned:** Without cache invalidation, viewers may still see old UI or JavaScript even after the source has been updated.

## Day 3 - 10/7: Completing the Workshop according to the implementation flow

**Work completed:** I updated Workshop sections to match the final IRMS flow: Introduction, Environment Setup, Infrastructure Configuration, Application Development, Deployment and Testing, Frontend Integration and Web Deployment, and Results/Cost/Cleanup. The goal was to summarize sections without losing important technical content.

I reviewed places that previously had joined paragraphs or Vietnamese text without accents in the English version. Long technical flows such as Lambda, S3 presigned URLs, EventBridge, Secrets Manager, and AI Assistant were split into bullets, tables, or code blocks for readability. I also checked the numbering for 5.1, 5.2, 5.3, and their child sections so the sidebar displayed correctly. Sensitive information such as passwords, access keys, secret keys, tokens, and API keys was replaced with placeholders.

**Knowledge learned:** A good workshop must follow the order a reader actually performs the work while also keeping examples secure.

**Result achieved:** Workshop content became easier to read, more synchronized between Vietnamese and English, and closer to the AWS work I contributed to.

**Difficulty and lesson learned:** Documentation copied from working notes often has broken formatting or missing context, so each page needs to be checked carefully.

## Day 4 - 14/7: Synchronizing the report, Proposal, and Worklog

**Work completed:** I reviewed the Proposal, Worklog, Events, Self-Assessment, Sharing and Feedback, and README so the content stayed consistent with IRMS. I checked the architecture diagram, AWS service names, AI provider, internship dates, student information, and internal links.

I replaced the architecture diagram in both Proposal and Workshop, then checked image paths under `static/images`. For the English version, I fixed sentences that still contained Vietnamese or sounded unnatural. For the Vietnamese version, I corrected spelling, paragraph breaks, and tone so it read more like a personal internship report. I also reviewed the Worklog to make sure it did not claim that I completed the whole project alone.

**Knowledge learned:** An internship report needs consistency across sections because a mentor can compare the Proposal, Workshop, Worklog, and final result.

**Result achieved:** The report became more consistent in timeline, architecture, personal contribution, and AWS terminology.

**Difficulty and lesson learned:** When editing bilingual files, both meaning and formatting must be checked, not only sentence-by-sentence translation.

## Day 5 - 21/7: Completing the project report

**Work completed:** I completed the final review according to the actual progress up to July 21, 2026. The work included checking Hugo build, GitHub Pages live demo, main page rendering, internal links, architecture images, sidebar numbering, and bilingual content.

I ran a production build with the GitHub Pages base URL, reviewed Hugo warnings, and confirmed there were no Markdown or front matter errors breaking the site. I also checked for sensitive information one last time to avoid publishing login emails, passwords, access keys, secret keys, tokens, or API keys. The final adjustment was updating the Worklog timeline so the early weeks represent AWS learning and labs, while the IRMS project starts from the week that includes July 1.

```bash
hugo --minify --baseURL https://mxt2003.github.io/Internship/
```

**Knowledge learned:** Completing the report is not only writing content; it also requires checking build output, links, images, sensitive data, and consistency across the whole website.

**Result achieved:** The report reflected the actual timeline, my personal role in the team, and the completed project status up to July 21, 2026.

**Difficulty and lesson learned:** Near the end, fixing one section can easily affect another, so a checklist-based review is safer than relying only on visual inspection.
