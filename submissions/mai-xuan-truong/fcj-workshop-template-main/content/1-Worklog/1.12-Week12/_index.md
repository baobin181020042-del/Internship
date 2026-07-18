---
title: "Week 12"
date: 2026-06-24
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

**Timeline:** June 24, 2026 - July 30, 2026

> IRMS was completed by a five-member team. The notes below focus on my individual contribution while collaborating with the team.

## Day 1 - 24/6: Deploying the frontend to S3

**Work completed:** Built the React production bundle with `npm run build`, checked the generated `dist/` folder, and synced the assets to the S3 frontend bucket. I verified object paths, `index.html`, and browser console errors after upload. The first issue was stale local build output, so I rebuilt the project before syncing again. The lesson was to validate the build artifact before blaming AWS hosting.


## Day 2 - 25/6: Configuring CloudFront for frontend access

**Work completed:** Reviewed the CloudFront distribution, origin settings, default root object, compression, and HTTPS behavior. I coordinated with teammates to confirm that API calls still used API Gateway and that static assets were served from S3 through CloudFront. The main issue was waiting for distribution propagation. I learned to separate deployment delay from configuration error.


## Day 3 - 26/6: Running CloudFront invalidation

**Work completed:** After frontend updates, I created a CloudFront invalidation for `/*` and compared the behavior before and after cache clearing. The issue was that the browser still showed an old JavaScript bundle, so I used both CloudFront invalidation and hard refresh during verification. This became a documented deployment step in the workshop.


## Day 4 - 27/6: End-to-end testing with the team

**Work completed:** Joined the team test session for login, incident CRUD, timeline, evidence upload, report generation, and AI Assistant flows. My focus was AWS integration: Cognito tokens, API Gateway routes, Lambda logs, S3 evidence upload, and CloudFront access. A CORS issue appeared during browser testing and was solved by checking API Gateway headers and redeploying the API stage.


## Day 5 - 28/6: Cost and resource review

**Work completed:** Checked AWS Billing, Cost Explorer, CloudWatch Logs, S3 buckets, Lambda functions, API Gateway, CloudFront, DynamoDB, Secrets Manager, SNS, and EventBridge. I noted which services could create cost after the demo. The issue was distinguishing active project resources from earlier lab resources. I learned to tag and name resources consistently.


## Day 6 - 29/6: Preparing the cleanup checklist

**Work completed:** Prepared a cleanup order for CloudFront, S3 buckets, CloudFormation/SAM stack, DynamoDB tables, log groups, EventBridge rules, SNS topic, and Secrets Manager secret. The main issue was dependency order, especially buckets with objects and CloudFront distributions that cannot be removed instantly. I documented the cleanup sequence for the workshop.


## Day 7 - 30/6: Refining infrastructure workshop sections

**Work completed:** Edited the workshop sections for architecture, prerequisites, Cognito, API Gateway, DynamoDB, S3, Lambda, EventBridge, SNS, and Secrets Manager. I checked that headings and sidebar numbering matched the seven-section workshop structure. The issue was inconsistent bilingual numbering, which I corrected by aligning the English and Vietnamese files.


## Day 8 - 1/7: Reviewing backend AWS documentation

**Work completed:** Reviewed Lambda responsibility tables, DynamoDB integration, EventBridge flow, and CloudWatch logging guidance. I checked command examples such as `sam validate`, `sam build`, and AWS CLI verification commands. Some code blocks rendered as large headings because of broken Markdown fences, so I corrected the fenced block formatting.


## Day 9 - 2/7: Documenting frontend deployment

**Work completed:** Updated the frontend integration documentation for React + Vite build, S3 sync, CloudFront deployment, and invalidation. I verified that screenshots and image paths still existed in `static/images`. The issue was stale architecture wording, so I changed the text to match S3 + CloudFront deployment instead of direct S3 website access.


## Day 10 - 3/7: Synchronizing bilingual documentation

**Work completed:** Compared `_index.md` and `_index.vi.md` files for Worklog, Proposal, Workshop, Self-Assessment, and Feedback. I focused on content consistency instead of translating word by word. The issue was that some English pages had Vietnamese phrases and some Vietnamese pages had old wording. I aligned the meaning and kept the language-specific wording natural.


## Day 11 - 4/7: Reviewing the IRMS proposal

**Work completed:** Reviewed the proposal against the final IRMS architecture and team responsibilities. I checked AWS services, AI provider, budget, risks, and expected outcomes. The issue was that older proposal text still described a different AI provider. I marked Bedrock as a future enhancement and kept Groq as the implemented provider.


## Day 12 - 5/7: Editing the personal worklog

**Work completed:** Reworked the worklog so it reflected my individual role inside a five-member team instead of claiming full ownership of every feature. I described my AWS infrastructure, deployment, testing, and documentation contributions. The issue was repeated wording, so I rewrote entries with concrete tasks, tools, issues, and lessons.


## Day 13 - 6/7: Running Hugo build checks

**Work completed:** Ran Hugo build locally to catch Markdown, shortcode, front matter, and image reference issues. I checked both English and Vietnamese pages after the build. The issue was that some pages built successfully but still looked broken because of malformed code fences. I learned that build success must be paired with visual inspection.


## Day 14 - 7/7: Final functional validation

**Work completed:** Compared the workshop steps with the actual demo flows: Cognito login, API Gateway calls, Incident CRUD, Timeline, Evidence Upload, Report, Alert Handler, and AI Assistant. I used CloudWatch Logs and browser developer tools to confirm the request path. The issue was inconsistent API examples, which I updated to match the final endpoints.


## Day 15 - 8/7: Cleaning up test resources

**Work completed:** Reviewed test resources and documented what should be removed after validation. I checked S3 objects, CloudFront distribution status, Lambda functions, log groups, DynamoDB tables, EventBridge rules, SNS topic, and Secrets Manager secret. The lesson was that cleanup should be planned before the final demo, not after costs appear.


## Day 16 - 9/7: Finalizing the report layout

**Work completed:** Reviewed report pages for formatting, broken paragraphs, bilingual mismatch, image placement, and sidebar numbering. I ran local Hugo server to inspect pages in the browser. The issue was several old section names and copied text blocks, which I corrected while preserving the site structure.


## Day 17 - 10/7: Preparing the first final submission build

**Work completed:** Built the Hugo site and prepared the first final submission state. I checked the seven major report sections and verified that the workshop was navigable. The issue was that the report still needed updated final implementation details, especially AI provider consistency. I recorded those gaps for the extended period.


## Day 18 - 11/7: Investigating Bedrock as a future provider

**Work completed:** Reviewed how Amazon Bedrock could fit behind the AI provider abstraction. I did not document it as deployed; instead, I treated it as a future enhancement. The issue was avoiding contradiction between proposal and workshop. I learned to separate implemented architecture from migration options.


## Day 19 - 12/7: Planning the Groq migration documentation

**Work completed:** Mapped the AI Assistant flow from frontend to API Gateway, Lambda, Groq, structured JSON response, and fallback. I checked that `/ai/analyze`, `/ai/explain`, and `/ai/chat` were described consistently. The issue was old provider wording in multiple pages, so I prepared a cleanup list.


## Day 20 - 13/7: Updating Secrets Manager guidance

**Work completed:** Reviewed the AI secret handling documentation. I replaced provider-specific secret examples with Groq-focused placeholders and emphasized that the frontend has no API key. The issue was avoiding publication of real secrets or passwords. I learned to use placeholders even in demo documentation.


## Day 21 - 14/7: Testing AI endpoint examples

**Work completed:** Reviewed API examples for analysis, severity explanation, and chat. I checked request bodies, response fields, provider name, model name, and fallback flag. The issue was mismatched JSON field names between sections. I standardized the examples around structured AI responses.


## Day 22 - 15/7: Reviewing Cognito and API Gateway security

**Work completed:** Checked the workshop text for Cognito JWT authorizer, Authorization header examples, and protected API routes. I replaced demo passwords with placeholders such as `YOUR_PASSWORD` and `YOUR_TEMP_PASSWORD`. The lesson was that documentation should never publish reusable credentials.


## Day 23 - 16/7: Updating architecture diagrams and captions

**Work completed:** Replaced the architecture diagram used in Proposal and Workshop with the final IRMS diagram that includes Groq. I verified the image path and hash after copying. The issue was browser caching, so I used hard refresh during visual validation.


## Day 24 - 17/7: Publishing the report to GitHub Pages

**Work completed:** Configured the report repository for GitHub Pages, added a Live Demo link, built Hugo with the production baseURL, pushed the branch, and verified the deployed URL returned HTTP 200. The issue was that the workflow had to be placed at the repository root, not only inside the Hugo subfolder.


## Day 25 - 18/7: Final consistency review

**Work completed:** Started a final documentation quality pass across Proposal, Worklog, Workshop, Results, and configuration. I focused on Groq consistency, extended internship dates, metadata cleanup, credentials, and professional wording. The lesson was to review the report as one connected deliverable instead of isolated pages.


## Day 26 - 19/7: Refining cost analysis wording

**Work completed:** Reviewed the cost section to avoid unsupported claims about credits or exact offsets. I described cost drivers for Lambda, API Gateway, CloudFront, S3, DynamoDB, Secrets Manager, and CloudWatch, and kept Groq as development/demo usage. The issue was making cost text accurate without overclaiming.


## Day 27 - 20/7: Checking environment variable consistency

**Work completed:** Reviewed AI-related environment variable names in the workshop: `AIProvider`, `GroqSecretName`, `GroqModel`, and `GroqTimeoutSeconds`. I aligned the table, Python example, and deployment text. The issue was avoiding mixed naming styles across sections.


## Day 28 - 21/7: Proofreading English pages

**Work completed:** Read the English report pages for grammar and technical clarity. I fixed phrasing such as incomplete objectives, awkward instructions, and mixed Vietnamese/English wording. The issue was preserving technical detail while making the text sound like professional documentation.


## Day 29 - 22/7: Reviewing Vietnamese synchronization

**Work completed:** Compared the Vietnamese pages with the updated English content and synchronized the meaning where the final implementation changed. I did not redesign the layout or rename sections. The issue was keeping bilingual support while avoiding two different versions of the same project story.


## Day 30 - 23/7: Validating image references

**Work completed:** Checked image references in Proposal and Workshop after the architecture update. I verified that the referenced files existed under `static/images` and that Hugo included them during build. The issue was that Proposal and Workshop used separate image paths, so both files had to be updated.


## Day 31 - 24/7: Reviewing API examples

**Work completed:** Reviewed API Gateway documentation for `/incidents`, `/evidence`, `/reports`, `/ai/analyze`, `/ai/explain`, and `/ai/chat`. I checked JSON examples and authentication notes. The issue was that older examples only documented one AI endpoint, so I expanded the final AI API documentation.


## Day 32 - 25/7: Mentor feedback adjustments

**Work completed:** Reviewed feedback items related to clarity, professional tone, and final architecture accuracy. I clarified Future Enhancement items such as Route 53, WAF, and Bedrock. The lesson was to be explicit about what was deployed and what remains optional.


## Day 33 - 26/7: Running final Hugo validation

**Work completed:** Ran `hugo --minify --baseURL https://mxt2003.github.io/Internship/` and checked for build errors, front matter issues, missing images, and broken Markdown. The issue was catching problems that only appear after production baseURL is used. The build process became part of the final checklist.


## Day 34 - 27/7: Reviewing GitHub Pages output

**Work completed:** Checked the live demo after deployment and compared it with the local Hugo build. I verified navigation, language switching, image loading, and the main report sections. The issue was cached browser assets, which I handled with hard refresh and by verifying the deployed static files.


## Day 35 - 28/7: Final report polishing

**Work completed:** Polished transitions between Proposal, Workshop, Results, Self-Assessment, and Feedback. I reduced repeated phrases and made the writing more direct. The lesson was that a technical report should read consistently from start to finish, not like separate copied notes.


## Day 36 - 29/7: Preparing final verification notes

**Work completed:** Prepared the final verification checklist: AI provider references aligned to Groq, credentials replaced, dates updated, build successful, and GitHub Pages live. The issue was keeping the checklist evidence-based, so I used search results and build output instead of memory.


## Day 37 - 30/7: Completing the internship report

**Work completed:** Completed the final internship documentation review and confirmed the report covered my personal contribution within the five-member IRMS team. I verified the final live demo, source branch, and Hugo build. The final lesson was to keep implementation, documentation, and deployment aligned until the last submission day.

