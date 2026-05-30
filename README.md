# AWS CI/CD Pipeline using CodePipeline, CodeBuild and Amazon S3

## Overview

This project demonstrates an end-to-end Continuous Integration and Continuous Deployment (CI/CD) pipeline built on AWS.

The objective of this lab was to automate the deployment process of a simple web application by integrating GitHub with AWS CodePipeline, AWS CodeBuild, and Amazon S3.

Instead of manually uploading files to S3 after every code change, the deployment process is automated through a CI/CD workflow.

---

## Architecture

```text
Developer (VS Code)
        │
        ▼
GitHub Repository
        │
        ▼
AWS CodePipeline
        │
        ▼
AWS CodeBuild
        │
        ▼
Amazon S3
        │
        ▼
Static Website Endpoint
```

---

## Workflow

### Step 1 - Develop Application

The application is developed locally using Visual Studio Code.

Example:

```html
<h1>Hello AWS DevOps Build</h1>
```

---

### Step 2 - Push Code to GitHub

Changes are committed and pushed to GitHub.

```bash
git add .
git commit -m "Version 2.0"
git push origin main
```

GitHub acts as the source repository for the pipeline.

---

### Step 3 - Source Stage (CodePipeline)

AWS CodePipeline retrieves the latest version of the application from GitHub.

This becomes the Source Artifact that moves through the pipeline.

---

### Step 4 - Build Stage (CodeBuild)

AWS CodeBuild uses the buildspec.yml file to execute build instructions.

Example:

```yaml
version: 0.2

phases:
  build:
    commands:
      - echo "Build Started"
```

The build output is packaged as a Build Artifact.

---

### Step 5 - Deploy Stage (Amazon S3)

The build artifact is deployed to an Amazon S3 bucket configured for Static Website Hosting.

The deployed files become accessible through the S3 Website Endpoint.

---

### Step 6 - Validate Deployment

After deployment, the application is accessed through the website endpoint.

Example Output:

```html
Hello AWS DevOps Build Version 2.0
```

---

## AWS Services Used

| Service          | Purpose                                    |
| ---------------- | ------------------------------------------ |
| GitHub           | Source Code Repository                     |
| AWS CodePipeline | CI/CD Orchestration                        |
| AWS CodeBuild    | Build Automation                           |
| Amazon S3        | Deployment Target & Static Website Hosting |
| IAM              | Service Permissions                        |

---

## Challenges Faced

During implementation, the following issues were identified and resolved:

* GitHub repository visibility issue in CodeBuild
* S3 AccessDenied error
* Bucket policy configuration
* Static Website Hosting configuration
* Pipeline trigger configuration
* Manual pipeline execution using Release Change

---

## Key Learnings

* Creating and configuring AWS CodeBuild projects
* Building CI/CD pipelines using AWS CodePipeline
* Deploying static websites using Amazon S3
* Managing IAM service roles
* Troubleshooting deployment failures
* Understanding Source → Build → Deploy workflows

---

## Result

Successfully implemented and tested a complete CI/CD pipeline that deploys application changes from GitHub to an Amazon S3 hosted website using AWS CodePipeline and AWS CodeBuild.
