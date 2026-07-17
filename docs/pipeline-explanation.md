Jenkins Pipeline Explanation

What is Jenkins Pipeline?
-> A Jenkins Pipeline is a collection of automated steps that define the complete CI/CD process.


Pipeline Stages:

Stage 1: Checkout Code
Purpose:
Download source code from GitHub.
Example:
git checkout main

Stage 2: Build Docker Image
Purpose:
Create a Docker image from application files.
Command:
docker build -t jenkins-demo .

Stage 3: Stop Existing Container.
Purpose:
Remove old application container before deployment.
Example:
docker stop jenkins-demo-container

Stage 4: Deploy Application
Purpose:
Run the new Docker container.
Command:
docker run -d -p 8080:80 jenkins-demo

CI/CD Benefits:

Continuous Integration:

- Automatically builds code
- Detects errors early
- Improves development speed

Continuous Deployment:

- Automatically releases new changes
- Reduces manual work
- Provides faster delivery


Jenkinsfile:
The Jenkinsfile contains pipeline instructions that Jenkins executes automatically.


Pipeline
|
|-- Checkout
|
|-- Build
|
|-- Deploy
