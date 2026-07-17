CI/CD Pipeline Architecture

Overview:
This document explains the architecture of the Jenkins CI/CD pipeline.

Architecture Flow:
------------------------------------
Developer
|
| git push
v
GitHub Repository
|
v
Jenkins Server
|
|-----------------
|
| Checkout Code
|
| Build Docker Image
|
| Deploy Container
|
|
v
Running Application
------------------------------------



Components Explanation:

1.GitHub:
  GitHub stores the application source code and maintains version history.

  Responsibilities:
  - Store code
  - Manage branches
  - Track changes


2.Jenkins:
  Jenkins is responsible for automation.

  Responsibilities:
  - Pull latest code
  - Execute pipeline
  - Build Docker image
  - Deploy application


3.Docker:
  Docker packages the application and its dependencies into containers.

  Responsibilities:
  - Create images
  - Run containers
  - Provide consistent environments


Deployment Flow:

1. Developer modifies application code.
2. Changes are pushed to GitHub.
3. Jenkins starts pipeline execution.
4. Docker image is generated.
5. Container is deployed.
6. Updated application is available.
