Troubleshooting Guide
This document lists common issues encountered while implementing the Jenkins CI/CD Pipeline and their solutions.

Problem 1: Jenkins Cannot Access GitHub
Error:
Permission denied (public key).
fatal: Could not read from remote repository.

Possible Causes:
SSH key is not configured.
Public key is not added to GitHub.
Incorrect repository URL.
Jenkins is using the wrong credentials.

Solution:
Verify GitHub SSH connectivity:
ssh -T git@github.com

Expected output:
Hi <GitHub-Username>! You've successfully authenticated, but GitHub does not provide shell access.
--------------------------------------------------------------------------------------------------------

Problem 2: Docker Permission Denied
Error:
permission denied while trying to connect to the Docker daemon socket

Cause:
The Jenkins user does not have permission to access the Docker daemon.

Solution:
Add the Jenkins user to the Docker group:
sudo usermod -aG docker jenkins

Restart Jenkinns:
sudo systemctl restart Jenkins

Verify Docker access:
sudo -u jenkins docker ps
--------------------------------------------------------------------------------------------------------

Problem 3: Docker Container Already Exists
Error:
Conflict. The container name is already in use.

Cause:
A previous container with the same name is still running or exists in a stopped state.

Solution:
List all containers:
docker ps -a

Stop the running container:
docker stop jenkins-demo-container

Remove the old container:
docker rm jenkins-demo-container

Run the pipeline again.
--------------------------------------------------------------------------------------------------------

Problem 4: Jenkins Pipeline Build Failed

Possible Causes:
Invalid Jenkinsfile syntax
Docker service is not running
Repository configuration is incorrect
Docker image build failed

Solution:
Check the following:
Jenkins Console Output
Jenkinsfile syntax
Git repository URL
Docker service status

Useful commands:
systemctl status docker
docker images
----------------------------------------------------------------------------------------------------------

Problem 5: Application Not Accessible

Possible Causes:
Container is not running
Incorrect port mapping
Firewall blocks the port

## Solution:
Check running containers:
docker ps

Verify port mapping:
docker port jenkins-demo-container

If the container has stopped, check its logs:
docker logs jenkins-demo-container
Restart the container if required:
docker start jenkins-demo-container
---------------------------------------------------------------------------------------------------------

Problem 6: Changes Not Reflected After Deployment
Cause:
The old Docker container or image is still being used.

Solution:
Remove the existing container and rebuild the image through the Jenkins pipeline.

Verify the latest deployment:
docker images
docker ps
Then refresh the application in the browser.
---------------------------------------------------------------------------------------------------------

Best Practices:

Always verify GitHub connectivity before running the pipeline.
Check Jenkins Console Output whenever a build fails.
Ensure Docker service is running before deployment.
Keep the Jenkinsfile under version control.
Test Docker commands manually before automating them in Jenkins.

