# CI/CD Pipeline with GitHub, Jenkins & Docker

Overview

This project demonstrates a complete CI/CD pipeline for a simple Flask web application using GitHub, Jenkins, and Docker.
Every time code is pushed to GitHub, Jenkins automatically:

Checks out the code

Builds a Docker image

Deploys and runs the application in a Docker container

Architecture
Developer → GitHub → Jenkins → Docker → Running Flask App


Developer commits code to GitHub

Jenkins detects changes and runs the pipeline

Docker builds the image and runs the container

The Flask app is accessible at http://<jenkins-server-ip>:5000

1. Clone the repository
git clone https://github.com/ganesh-966/jenkins-docker-demo.git
cd jenkins-docker-demo

2. Jenkins Setup

Install Jenkins with Docker support

Add Jenkins user to Docker group:

sudo usermod -aG docker jenkins
sudo systemctl restart jenkins

![](./images/Screenshot%202026-01-17%20123707.png)

3. Create Jenkins Pipeline

Create a Pipeline job in Jenkins

Connect it to your GitHub repository

Use the provided Jenkinsfile

![](./images/Screenshot%202026-01-17%20123814.png)

4. Run Pipeline

Trigger a build

Jenkins will:

Checkout code from main branch

Build Docker image flask-ci-cd-app

Run container flask-app on port 5000

![](./images/Screenshot%202026-01-17%20123942.png)


container will create into jenkins server

![](./images/Screenshot%202026-01-17%20124757.png)
5. Access App

Open your browser and go to:

http://<JENKINS_SERVER_IP>:5000

![](./images/Screenshot%202026-01-17%20124057.png)

## Conclusion

This project shows how GitHub, Jenkins, and Docker can work together to automatically build and run an application. Using Docker containers makes it easy to run the app anywhere, keeps it isolated from other programs, and ensures it works the same on every machine. This project is a great way to learn DevOps and CI/CD basics.