---
title: "Week 12"
date: 2026-07-06
weight: 12
chapter: false
pre: " <b> 1.12. </b> "
---

**Timeline:** July 6, 2026 - July 21, 2026

> IRMS was completed by a five-member team. The notes below focus on my individual contribution while collaborating with the team.

## Day 1 - 6/7: Completing APIs and Optimizing the Backend

**Work completed:** I continued improving the IRMS backend by completing the Incident CRUD, Timeline, Report Generation, and Evidence Upload APIs. I reviewed the backend source code, added input validation and error handling, and optimized AWS Lambda functions to improve response time. I also verified IAM permissions and environment variable configurations to ensure that AWS services worked correctly.

**Knowledge learned:** Optimizing Lambda functions and implementing proper error handling improve application stability and reduce API response time.

**Result achieved:** The backend APIs were completed, operated reliably, and were ready for testing and frontend integration.

**Difficulty and lesson learned:**  During optimization, it was important to verify IAM role permissions and environment variables carefully to avoid deployment issues.

## Day 2 - 8/7: API Testing with Postman

**Work completed:** I used Postman to test all system APIs, including authentication, Incident Management, Timeline, Evidence Upload, and Report Generation. Besides verifying successful responses, I tested various invalid input scenarios to evaluate the validation and error-handling mechanisms before integrating the APIs with the frontend.

**Knowledge learned:** Testing APIs with different scenarios helps identify issues early and ensures system reliability before deployment.

**Result achieved:** The APIs functioned as designed, and identified issues were resolved before the integration phase.

**Difficulty and lesson learned:** Some issues were caused by invalid input formats, highlighting the importance of defining validation rules early in development.

## Day 3 - 10/7:  Frontend and Backend Integration

**Work completed:** I collaborated with the frontend developer to integrate the backend APIs into the user interface. During the integration process, I helped verify Amazon Cognito JWT tokens, configured API Gateway, resolved CORS issues, and confirmed that data was correctly synchronized between the frontend and backend.

**Knowledge learned:** Maintaining consistent API structures and data formats between the frontend and backend greatly simplifies the integration process.

**Result achieved:** The main system features successfully exchanged data through the APIs and operated reliably in the testing environment.

**Difficulty and lesson learned:** When integrating multiple components, both the frontend, backend, and AWS services must be checked to accurately identify the root cause of any issues.

## Day 4 - 14/7:  Updating the Workshop and Worklog

**Work completed:** I updated the Workshop, Worklog, and other technical documents to match the actual implementation progress of the IRMS project. I also reviewed the system architecture diagrams, AWS deployment procedures, screenshots, and bilingual documentation to ensure they accurately reflected my individual contributions.

**Knowledge learned:** Technical documentation should be updated alongside development to maintain accuracy and simplify the reporting process.

**Result achieved:** The project documentation was synchronized with the implementation progress and was ready for the internship report.

**Difficulty and lesson learned:** Updating multiple documents simultaneously requires careful review to maintain consistency in both content and formatting.

## Day 5 - 21/7: Project Review and Knowledge Sharing

**Work completed:** I reviewed all development tasks completed during the project, verified the source code, documentation, and AWS services used throughout the implementation. I also helped prepare the presentation for the IRMS project and participated in the knowledge-sharing session titled **"Study Group VN Shift-left Security with Amazon Bedrock: Automating Threat Modeling Using Generative AI."** Finally, I completed the internship report and finalized all required project documentation.

**Knowledge learned:** Reviewing and sharing project experience helps reinforce technical knowledge while improving teamwork and presentation skills.

**Result achieved:** All internship objectives were completed successfully, and both the project and its documentation were finalized for presentation and evaluation.

**Difficulty and lesson learned:** Continuously updating project progress and documentation throughout development helps reduce workload at the end of the internship and ensures consistency across all deliverables.
