# 09. Module Design

## 1. Overview

The software is divided into several modules so that each functional area can be developed and tested independently. The modules correspond closely to the major system features and support future extension without major redesign.

## 2. Module Summary

| Module | Purpose |
|---|---|
| Authentication | Manage user login, registration, and session handling. |
| User Management | Maintain profile and account information. |
| Project Upload | Accept uploaded files or repository URLs and store metadata. |
| AI Analysis | Analyze project content and generate deployment insights. |
| Docker Generation | Create deployment artifact suggestions. |
| Cloud Recommendation | Suggest suitable cloud deployment targets. |
| History | Track previous projects and deployment results. |

## 3. Authentication Module

| Item | Description |
|---|---|
| Purpose | To secure access to the platform and validate user identity. |
| Responsibilities | Register users, verify login credentials, issue authentication tokens, and manage session state. |
| Inputs | Email, password, user profile data. |
| Outputs | Authenticated session, error messages, user identity. |
| Dependencies | User Management, password hashing utilities, backend security middleware. |
| Future Scope | Support for password reset, OAuth login, and refresh tokens. |

## 4. User Management Module

| Item | Description |
|---|---|
| Purpose | To manage user account details and profile information. |
| Responsibilities | Store user profile information, update profile details, and provide account-related data to other modules. |
| Inputs | User profile updates, account creation data. |
| Outputs | Profile records, account metadata. |
| Dependencies | Authentication module and database models. |
| Future Scope | Role-based access control and admin management. |

## 5. Project Upload Module

| Item | Description |
|---|---|
| Purpose | To accept and validate project input from the user. |
| Responsibilities | Receive uploaded ZIP files, accept GitHub repository URLs, validate size and format, save uploaded artifacts, and store project metadata. |
| Inputs | ZIP file or repository URL. |
| Outputs | Project record, temporary storage path, upload status. |
| Dependencies | File handling utilities, database access layer, storage service. |
| Future Scope | Support for larger archives, private repository access, and drag-and-drop enhancements. |

## 6. AI Analysis Module

| Item | Description |
|---|---|
| Purpose | To analyze the uploaded project and generate deployment-related insights. |
| Responsibilities | Parse project contents, detect language/framework, summarize dependencies, evaluate deployment readiness, and generate AI-based recommendations. |
| Inputs | Project files, repository contents, analysis prompts. |
| Outputs | Analysis report, readiness score, AI narrative summary. |
| Dependencies | Gemini API, file parser utilities, project metadata. |
| Future Scope | Improve language detection, support more frameworks, and add deeper code quality analysis. |

## 7. Docker Generation Module

| Item | Description |
|---|---|
| Purpose | To generate deployment artifacts that assist in containerizing the application. |
| Responsibilities | Create a Dockerfile draft, suggest appropriate base images, and return the resulting content for review. |
| Inputs | Analysis report, detected stack, project type. |
| Outputs | Dockerfile content, base image suggestion, generation status. |
| Dependencies | AI Analysis module, template library, backend generation service. |
| Future Scope | Support multi-stage builds and framework-specific Docker templates. |

## 8. Cloud Recommendation Module

| Item | Description |
|---|---|---|
| Purpose | To suggest suitable deployment platforms based on project characteristics. |
| Responsibilities | Evaluate project needs, match them to service providers such as Render, Railway, AWS, Azure, or Google Cloud, and generate a recommendation with reasoning. |
| Inputs | Detected framework, dependency summary, deployment readiness score. |
| Outputs | Recommended provider, explanation, confidence score, estimated cost. |
| Dependencies | AI Analysis module and recommendation rules. |
| Future Scope | Add cost comparison, provider health checks, and deployment automation. |

## 9. History Module

| Item | Description |
|---|---|
| Purpose | To provide users with visibility into their past uploads and deployment activities. |
| Responsibilities | Retrieve prior projects, display analysis and deployment activity, and support basic filtering and sorting. |
| Inputs | User ID, project ID, deployment records. |
| Outputs | History list, status summaries, deployment timeline. |
| Dependencies | Project Upload module, database layer, deployment records. |
| Future Scope | Add richer reporting, date filtering, and downloadable reports. |
