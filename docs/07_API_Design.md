# 07. API Design

## 1. Overview

The backend of the AI DevOps Assistant exposes a RESTful API for all major functionalities. The API is designed to support authentication, project management, AI-based analysis, Dockerfile generation, deployment recommendation, and deployment history retrieval. All communication is expected to use JSON payloads.

## 2. Authentication APIs

### 2.1 Register User

| Field | Value |
|---|---|
| URL | /api/auth/register |
| Method | POST |
| Description | Creates a new user account. |
| Request Body | { "name": "Aman", "email": "aman@example.com", "password": "SecurePass123" } |
| Response Body | { "message": "User registered successfully", "user_id": 1 } |
| Status Codes | 201 Created, 400 Bad Request, 409 Conflict |

### 2.2 Login User

| Field | Value |
|---|---|
| URL | /api/auth/login |
| Method | POST |
| Description | Authenticates a user and returns a token. |
| Request Body | { "email": "aman@example.com", "password": "SecurePass123" } |
| Response Body | { "access_token": "token", "token_type": "bearer" } |
| Status Codes | 200 OK, 401 Unauthorized |

### 2.3 Get Current User

| Field | Value |
|---|---|
| URL | /api/auth/me |
| Method | GET |
| Description | Returns profile details for the authenticated user. |
| Request Body | None |
| Response Body | { "id": 1, "name": "Aman", "email": "aman@example.com" } |
| Status Codes | 200 OK, 401 Unauthorized |

## 3. User APIs

### 3.1 Get User Profile

| Field | Value |
|---|---|
| URL | /api/users/me |
| Method | GET |
| Description | Retrieves the authenticated user profile. |
| Request Body | None |
| Response Body | { "id": 1, "name": "Aman", "email": "aman@example.com", "created_at": "2026-07-22T10:00:00Z" } |
| Status Codes | 200 OK, 401 Unauthorized |

### 3.2 Update User Profile

| Field | Value |
|---|---|
| URL | /api/users/me |
| Method | PUT |
| Description | Updates profile information such as the user name. |
| Request Body | { "name": "Aman Sharma" } |
| Response Body | { "message": "Profile updated successfully" } |
| Status Codes | 200 OK, 400 Bad Request |

## 4. Project APIs

### 4.1 Upload Project

| Field | Value |
|---|---|
| URL | /api/projects/upload |
| Method | POST |
| Description | Uploads a ZIP file or accepts a GitHub repository URL. |
| Request Body | { "source_type": "zip", "file": "binary" } or { "source_type": "github", "source_url": "https://github.com/user/repo" } |
| Response Body | { "project_id": 10, "status": "uploaded" } |
| Status Codes | 201 Created, 400 Bad Request, 413 Payload Too Large |

### 4.2 List Projects

| Field | Value |
|---|---|
| URL | /api/projects |
| Method | GET |
| Description | Returns all projects for the authenticated user. |
| Request Body | None |
| Response Body | [ { "id": 10, "title": "Sample App", "status": "analyzed" } ] |
| Status Codes | 200 OK |

### 4.3 Get Project Details

| Field | Value |
|---|---|
| URL | /api/projects/{project_id} |
| Method | GET |
| Description | Returns details of a specific project. |
| Request Body | None |
| Response Body | { "id": 10, "title": "Sample App", "source_type": "zip", "status": "analyzed" } |
| Status Codes | 200 OK, 404 Not Found |

### 4.4 Delete Project

| Field | Value |
|---|---|
| URL | /api/projects/{project_id} |
| Method | DELETE |
| Description | Removes a project and its related records. |
| Request Body | None |
| Response Body | { "message": "Project deleted successfully" } |
| Status Codes | 200 OK, 404 Not Found |

## 5. AI Analysis APIs

### 5.1 Start Analysis

| Field | Value |
|---|---|
| URL | /api/projects/{project_id}/analyze |
| Method | POST |
| Description | Starts AI-based analysis for a project. |
| Request Body | { "analysis_type": "full" } |
| Response Body | { "message": "Analysis started", "analysis_id": 5 } |
| Status Codes | 202 Accepted, 400 Bad Request |

### 5.2 Get Analysis Report

| Field | Value |
|---|---|---|
| URL | /api/projects/{project_id}/analysis |
| Method | GET |
| Description | Returns the stored analysis report. |
| Request Body | None |
| Response Body | { "language": "Python", "framework": "FastAPI", "readiness_score": 78, "ai_summary": "The project appears well-structured..." } |
| Status Codes | 200 OK, 404 Not Found |

## 6. Docker APIs

### 6.1 Generate Dockerfile

| Field | Value |
|---|---|
| URL | /api/projects/{project_id}/dockerfile |
| Method | POST |
| Description | Generates a Dockerfile draft for the project. |
| Request Body | { "base_image": "python:3.11-slim" } |
| Response Body | { "dockerfile_id": 3, "file_name": "Dockerfile", "content": "FROM python:3.11-slim\n..." } |
| Status Codes | 201 Created, 400 Bad Request |

### 6.2 Get Dockerfile

| Field | Value |
|---|---|
| URL | /api/projects/{project_id}/dockerfile |
| Method | GET |
| Description | Retrieves the generated Dockerfile content. |
| Request Body | None |
| Response Body | { "file_name": "Dockerfile", "content": "FROM python:3.11-slim\n..." } |
| Status Codes | 200 OK, 404 Not Found |

## 7. Deployment Guide APIs

### 7.1 Get Recommendation

| Field | Value |
|---|---|
| URL | /api/projects/{project_id}/recommendation |
| Method | GET |
| Description | Returns the cloud recommendation for the project. |
| Request Body | None |
| Response Body | { "provider": "Render", "reason": "Suitable for Python and FastAPI applications", "confidence_score": 0.82 } |
| Status Codes | 200 OK, 404 Not Found |

### 7.2 Generate Deployment Guide

| Field | Value |
|---|---|
| URL | /api/projects/{id}/guide |
| Method | POST |
| Description | Generates an AI-assisted deployment guide for the project. |
| Request Body | { "sections": ["prerequisites","steps","env"] } (optional) |
| Response Body | { "deployment_guide": { "title": "Deployment Guide", "prerequisites": [], "steps": [], "recommended_provider": "Render", "docker_commands": [], "environment_variables": {} } } |
| Status Codes | 201 Created, 400 Bad Request |

### 7.3 Get Readiness Summary

| Field | Value |
|---|---|
| URL | /api/projects/{id}/readiness |
| Method | GET |
| Description | Returns readiness score, detected issues, and strengths for the project. |
| Request Body | None |
| Response Body | { "score": 84, "issues": [], "strengths": [] } |
| Status Codes | 200 OK, 404 Not Found |

## 8. History APIs

### 8.1 Get Analysis History

| Field | Value |
|---|---|
| URL | /api/history |
| Method | GET |
| Description | Returns analysis history for the authenticated user. |
| Request Body | None |
| Response Body | [ { "project_id": 10, "readiness_score": 84, "recommended_provider": "Render", "generated_at": "2026-07-22T11:00:00Z" } ] |
| Status Codes | 200 OK |

### 8.2 Get Project History

| Field | Value |
|---|---|
| URL | /api/projects/{project_id}/history |
| Method | GET |
| Description | Returns all historical events for a single project (analysis and generated artifacts). |
| Request Body | None |
| Response Body | { "project_id": 10, "events": ["uploaded", "analyzed", "dockerfile generated", "deployment guide generated"] } |
| Status Codes | 200 OK, 404 Not Found |
