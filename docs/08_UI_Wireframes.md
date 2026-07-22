# 08. UI Wireframes

## 1. Overview

The user interface for the AI DevOps Assistant is designed to guide users through a simple workflow: authenticate, upload a project, analyze it, review the results, and prepare deployment. The UI is expected to be responsive and easy for beginners to follow.

## 2. Login Page

### Components

- Email input field
- Password input field
- Login button
- "Create account" link
- Forgot password link

### Buttons

- Login
- Register

### Navigation

- The page routes users to the dashboard after successful authentication.
- It provides a link to the registration page for new users.

### User Flow

1. User enters credentials.
2. System validates the input.
3. On success, the user is redirected to the dashboard.

### ASCII Wireframe

```text
+------------------------------+
| AI DevOps Assistant          |
|------------------------------|
| Email: ....................  |
| Password: .................. |
| [Login]                      |
| Create account               |
+------------------------------+
```

## 3. Register Page

### Components

- Full name input
- Email input
- Password input
- Confirm password input
- Register button
- Back to login link

### Buttons

- Register
- Back to Login

### Navigation

- Redirects to login after successful registration.

### User Flow

1. User fills the form.
2. System validates fields.
3. Account is created and user is redirected to login.

### ASCII Wireframe

```text
+-----------------------------------+
| Create Account                    |
|-----------------------------------|
| Full Name: ..................... |
| Email: .......................... |
| Password: ....................... |
| Confirm Password: ............... |
| [Register]                       |
| Already have an account? Login   |
+-----------------------------------+
```

## 4. Dashboard Page

### Components

- Welcome header
- Summary cards for projects analyzed and deployment readiness
- Recent projects list
- Quick action button for new upload
- Navigation sidebar

### Buttons

- Upload New Project
- View History
- View Profile

### Navigation

- Sidebar links to Dashboard, Upload, History, and Profile.

### User Flow

1. User views recent activity.
2. User selects a project or starts a new upload.

### ASCII Wireframe

```text
+-----------------------------------------------+
| Dashboard | Upload | History | Profile        |
|-----------------------------------------------|
| Welcome, Aman                                  |
| [Upload New Project]                           |
| Projects Analyzed: 4    Readiness Avg: 76%     |
| Recent Projects:                               |
| - Sample App        [View]                      |
| - ECommerce UI     [View]                      |
+-----------------------------------------------+
```

## 5. Upload Project Page

### Components

- Upload area for ZIP files
- GitHub repository URL input
- Browse button
- Upload button
- Validation messages

### Buttons

- Upload Project
- Cancel

### Navigation

- Leads to the analysis report page after successful upload.

### User Flow

1. User selects a file or enters a repository URL.
2. System validates the input.
3. The project is uploaded and analysis is started.

### ASCII Wireframe

```text
+--------------------------------------------------+
| Upload Project                                   |
|--------------------------------------------------|
| Drag and drop ZIP here or                        |
| [Browse Files]                                   |
| Or enter GitHub URL:                            |
| https://github.com/user/repo                    |
| [Analyze Project]                                |
+--------------------------------------------------+
```

## 6. Analysis Report Page

### Components

- Project summary card
- Detected language and framework section
- Dependency list
- Deployment readiness score
- AI-generated insights
- Generated Dockerfile preview
- Checklist section

### Buttons

- Generate Dockerfile
- View Recommendation
- Download Report

### Navigation

- Links to deployment recommendation and history pages.

### User Flow

1. User reviews the analysis report.
2. User chooses to generate deployment assets or continue to recommendations.

### ASCII Wireframe

```text
+---------------------------------------------------+
| Analysis Report                                   |
|---------------------------------------------------|
| Project: Sample App                               |
| Language: Python                                 |
| Framework: FastAPI                               |
| Readiness Score: 78/100                          |
| [Generate Dockerfile] [View Recommendation]      |
|---------------------------------------------------|
| Insights:                                        |
| - Dependency file found                          |
| - Dockerfile missing                             |
+---------------------------------------------------+
```

## 7. Deployment Recommendation Page

### Components

- Recommended cloud provider card
- Alternative providers list
- Reasoning text
- Cost estimate section
- Recommended deployment checklist
- Deploy button

### Buttons

- Deploy
- Back to Report

### Navigation

- Connects the report page with the history page.

### User Flow

1. User reviews provider recommendations.
2. User selects a provider and proceeds to deployment preparation.

### ASCII Wireframe

```text
+---------------------------------------------------+
| Deployment Recommendation                        |
|---------------------------------------------------|
| Recommended: Render                              |
| Why: Good fit for Python/FastAPI apps           |
| Confidence: 82%                                  |
| [Deploy] [Back]                                  |
| Alternatives: Railway, AWS, Azure               |
+---------------------------------------------------+
```

## 8. History Page

### Components

- Search/filter controls
- Project cards or table listing previous uploads
- Status badges for analysis and deployment
- View details button

### Buttons

- View Details
- Delete Entry

### Navigation

- Accessible from the dashboard sidebar.

### User Flow

1. User reviews prior project activity.
2. User opens details for one previous project.

### ASCII Wireframe

```text
+---------------------------------------------------+
| History                                          |
|---------------------------------------------------|
| Search: ...................                      |
| Project        Status        Date                  |
| Sample App     Analyzed      2026-07-22           |
| Shop UI        Deployed      2026-07-15           |
+---------------------------------------------------+
```

## 9. Profile Page

### Components

- Profile details card
- Edit profile button
- Password change section
- Account activity summary

### Buttons

- Save Changes
- Change Password

### Navigation

- Accessible from sidebar.

### User Flow

1. User reviews account information.
2. User updates profile or password details.

### ASCII Wireframe

```text
+---------------------------------------------------+
| Profile                                          |
|---------------------------------------------------|
| Name: Aman Sharma                                |
| Email: aman@example.com                          |
| [Edit Profile] [Change Password]                 |
| Account created: 2026-07-22                      |
+---------------------------------------------------+
```
