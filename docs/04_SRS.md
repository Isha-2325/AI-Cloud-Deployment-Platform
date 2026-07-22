# 04. Software Requirements Specification

## 1. Introduction

This document defines the software requirements for the AI DevOps Assistant – Intelligent Cloud Deployment Platform, a web-based system designed to assist users in analyzing software projects and preparing them for deployment. The system is intended as a final-year engineering major project and focuses on a practical, semester-appropriate implementation of core features such as project upload, AI-based analysis, Dockerfile generation, deployment readiness evaluation, and cloud platform recommendation.

The platform targets students, beginner developers, and small project teams who need a guided and simplified approach to deployment without requiring extensive DevOps expertise.

## 2. Purpose

The purpose of this system is to reduce the manual effort involved in preparing an application for deployment. The platform allows users to upload a software project and receive structured guidance on its technology stack, deployment readiness, and suitable deployment targets. The system also generates initial deployment artifacts, such as a Dockerfile, to accelerate the deployment process.

## 3. Scope

### 3.1 In Scope

- User registration and authentication
- Project upload through ZIP file or GitHub repository URL
- Basic project analysis using AI
- Detection of programming language, framework, and dependencies
- Deployment readiness scoring
- Automatic generation of a Dockerfile draft
- Cloud platform recommendation
- Deployment checklist generation
- Deployment history tracking

### 3.2 Out of Scope

- Full CI/CD pipeline automation
- Multi-container orchestration
- Production-scale autoscaling and monitoring
- Real deployment to cloud providers within the semester project scope
- Advanced security scanning and compliance auditing

## 4. Definitions

- User: A registered person using the platform.
- Project: A software application uploaded by a user for analysis.
- Analysis Report: The AI-generated result describing language, framework, dependencies, and project structure.
- Deployment Readiness Score: A numeric score indicating how prepared a project is for deployment.
- Dockerfile: A configuration file used to containerize the application.
- Recommendation: An AI-generated suggestion for a suitable cloud deployment target.

## 5. Overall Description

The proposed system is a web application with a React-based frontend, a FastAPI backend, a PostgreSQL database, and integration with the Google Gemini API for intelligent analysis. The system is expected to operate as a guided assistant that helps users progress from project upload to deployment preparation.

The application will use a modular architecture to separate user management, project handling, AI analysis, deployment artifact generation, and history tracking. The system is expected to provide a user-friendly experience while maintaining reliability and security during normal usage.

## 6. Product Perspective

The platform is a standalone web application and is not intended to replace full DevOps platforms such as GitHub Actions, Docker Hub, or cloud-native deployment services. Instead, it provides an intelligent front-end workflow for users who need a simplified starting point for deployment preparation.

The system will interact with external services, including:

- Google Gemini API for AI-based analysis
- GitHub repository access for repository-based uploads
- Cloud service providers for recommendations only, not full automated deployment in the initial version

## 7. Product Functions

The system shall provide the following core functions:

1. Allow users to create an account and authenticate securely.
2. Allow users to upload a project archive or provide a GitHub repository URL.
3. Analyze the uploaded project to identify the technology stack.
4. Generate a deployment readiness score and checklist.
5. Create a Dockerfile draft based on the detected stack.
6. Recommend a suitable deployment platform.
7. Maintain a history of uploaded projects and generated outputs.

## 8. User Classes

### 8.1 Registered User

A registered user can upload projects, view analysis results, generate Dockerfiles, and access deployment recommendations.

### 8.2 Guest User

A guest user may browse the platform interface but will be restricted from uploading and analyzing projects until registration is completed.

### 8.3 Administrator

An administrator may manage user accounts, review system activity, and monitor platform usage in a future extended version.

## 9. Functional Requirements

| ID | Requirement | Priority |
|---|---|---|
| FR-01 | The system shall allow users to register with a valid email address and password. | High |
| FR-02 | The system shall authenticate users using secure login credentials. | High |
| FR-03 | The system shall allow users to upload a ZIP file containing a software project. | High |
| FR-04 | The system shall allow users to submit a GitHub repository URL for analysis. | Medium |
| FR-05 | The system shall analyze the uploaded project structure and identify the programming language and framework. | High |
| FR-06 | The system shall extract dependency-related information from available project files. | High |
| FR-07 | The system shall generate a deployment readiness score based on detected configuration quality. | High |
| FR-08 | The system shall generate a Dockerfile draft for supported project types. | High |
| FR-09 | The system shall generate a deployment checklist based on the analysis result. | High |
| FR-10 | The system shall provide a cloud platform recommendation based on the detected stack. | High |
| FR-11 | The system shall store project analysis results and deployment history for each user. | High |
| FR-12 | The system shall display the analysis report in a readable format to the user. | High |
| FR-13 | The system shall allow users to view previous projects and generated outputs. | Medium |
| FR-14 | The system shall provide error feedback when upload or analysis fails. | Medium |

## 10. Non-Functional Requirements

| Category | Requirement |
|---|---|
| Performance | The system should respond to common requests within 3 to 8 seconds under normal load. |
| Security | User passwords must be stored securely using hashing and the application must use HTTPS in deployment. |
| Usability | The interface should be easy to understand for beginner developers and should provide clear guidance. |
| Reliability | The system should handle invalid uploads and AI API failures gracefully. |
| Maintainability | The application should be modular and well-documented for future extension. |
| Compatibility | The web application should work on modern desktop and mobile browsers. |

## 11. External Interface Requirements

### 11.1 User Interface

The system shall provide a responsive web interface for authentication, project upload, analysis viewing, deployment recommendation, and history access.

### 11.2 Software Interfaces

The backend shall communicate with:

- Google Gemini API for AI-based analysis and content generation
- PostgreSQL for persistent storage
- GitHub API or repository access endpoints for repository-based uploads

### 11.3 Communication Interfaces

The system shall exchange data using REST-based HTTP requests in JSON format.

## 12. System Requirements

### 12.1 Frontend Requirements

- React.js with Vite
- Tailwind CSS for styling
- Support for responsive layouts

### 12.2 Backend Requirements

- FastAPI server
- Python-based business logic
- REST API endpoints for all major features

### 12.3 Database Requirements

- PostgreSQL server
- Structured storage for users, projects, analysis reports, deployment artifacts, and deployment history

### 12.4 AI Requirements

- Access to Google Gemini API for analysis and content generation
- Basic prompt design for project classification and deployment suggestion

## 13. Assumptions

- Users have access to a valid email address for registration.
- The system is deployed in a development or staging environment during the project period.
- Uploaded projects are limited to small to medium-sized applications for the semester implementation.
- Internet connectivity is available for AI service access and GitHub repository retrieval.

## 14. Constraints

- The project will be implemented within academic timelines and resource limits.
- The system may not support every programming language or framework equally well.
- AI responses may vary and should be interpreted as guidance rather than absolute truth.
- Cloud deployment will be simulated or partially implemented rather than fully automated in the initial version.
