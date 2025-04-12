# Jenkins CI/CD Pipeline for Docker Application

## Overview
This repository implements a Jenkins pipeline to automate the build and deployment of a Docker application. The pipeline includes three key stages:

1. **Build**: Creates a Docker image from the application code
2. **Test**: Executes any configured tests (optional)
3. **Deploy**: Deploys the application to the target environment

## Prerequisites
- Ubuntu/Debian server
- Java JDK 11+
- Docker installed
- GitHub account

## Installation Guide

### 1. Jenkins Setup

#### For Ubuntu/Debian systems:
```bash
# Update system packages
sudo apt update && sudo apt upgrade -y

# Install Java (Jenkins dependency)
sudo apt install openjdk-11-jdk -y

# Add Jenkins repository
wget -q -O - https://pkg.jenkins.io/jenkins.io.key | sudo tee /usr/share/keyrings/jenkins.asc
sudo sh -c 'echo deb [signed-by=/usr/share/keyrings/jenkins.asc] http://pkg.jenkins.io/debian stable main > /etc/apt/sources.list.d/jenkins.list'

# Install Jenkins
sudo apt update
sudo apt install jenkins -y

# Start and enable Jenkins service
sudo systemctl start jenkins
sudo systemctl enable jenkins
Access Jenkins:
Open http://your-server-ip:8080 in your browser

Retrieve the admin password:

bash
Copy
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
Complete the setup wizard (install suggested plugins and create admin user)

2. Repository Setup
Clone this repository to your local machine:

bash
Copy
git clone https://github.com/saivijayy/Task-2.git
Pipeline Configuration
Create Pipeline Job:

In Jenkins dashboard, click "New Item"

Enter a name and select "Pipeline" type

Click "OK"

Configure Pipeline:

Under "Pipeline" section:

Select "Pipeline script from SCM"

Choose "Git" as SCM

Enter repository URL: https://github.com/saivijayy/Task-2.git

Set branch specifier to */main

Save configuration

Triggering the Pipeline
To execute the pipeline:

Make changes to your application code

Commit and push changes to GitHub:

bash
Copy
git add .
git commit -m "Triggering Jenkins build"
git push origin main
Jenkins will automatically detect changes and run the pipeline

Pipeline Stages
Stage	Description
Build	Creates Docker image using the repository's Dockerfile
Test	Runs unit/integration tests (if configured)
Deploy	Deploys the containerized application to target environment
Technology Stack
Jenkins: CI/CD automation server

Docker: Application containerization

GitHub: Version control and source code management

Conclusion
This Jenkins pipeline provides an automated solution for building, testing, and deploying Docker applications. By integrating with GitHub, it enables a streamlined development workflow with consistent deployments.
