# 🧩 Jenkins CI/CD Pipeline for Maven + Docker + Kubernetes + Nexus + Sonarqube

This repository contains a complete Jenkins Declarative Pipeline that automates the process of building a Java application with Maven, running code quality checks via SonarQube, containerizing the app using Docker, pushing the image to a private Docker registry, and deploying it to a Kubernetes cluster (MicroK8s).

---

## 📁 Repository Structure
.
├── Dockerfile # Docker image definition
├── devweb.yml # Kubernetes deployment manifest
├── Jenkinsfile # Declarative Jenkins pipeline
├── pom.xml # Maven build file
└── src/ # Java application source code

## 🚀 Pipeline Overview
The Jenkins pipeline performs the following stages:

1. **Checkout**: Clone the application source code from GitHub.
2. **Build**: Compile and package the code using Maven.
3. **SonarQube Analysis**: Perform static code analysis for code quality.
4. **Docker Build**: Build a Docker image for the application.
5. **Docker Push**: Push the image to a Nexus repository on AWS EC2 Instance.
6. **Deploy**: Deploy the application to a Kubernetes cluster (MicroK8s).

🛠️ Prerequisites
To successfully use this pipeline:

Jenkins is installed and configured with:
Maven (tool name: mvn)
SonarQube integration
Docker installed on the Jenkins agent
A Nexus registry is running at ec2-18-215-154-157.compute-1.amazonaws.com:5000
Kubernetes is running (MicroK8s in this case) and kubectl is available
Jenkins credentials:
ID: nexus_credential
Type: Username with Password
Used for authenticating Docker push

✅ Technologies Used
Jenkins – CI/CD orchestration
Maven – Build tool
SonarQube – Static code analysis
Docker – Containerization
MicroK8s – Lightweight Kubernetes
Nexus – Image storage and distribution

🧪 How to Run
Push this code to your GitHub repository.
In Jenkins:
Create a new Pipeline Job.
Configure the Pipeline to use the Jenkinsfile from this repo.
Run the pipeline manually or configure GitHub Webhooks for CI/CD automation.

🙋‍♂️ Author
Chinwe Ebube Onaifoh
📫 onaifohchinwe094@gmail.com
📞 +1 (437) 473-4649
📍 Ajax, Ontario, Canada
