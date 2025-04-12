Jenkins CI/CD Pipeline for Task 2
Overview
This repository contains the implementation of a simple Jenkins pipeline for automating the build and deployment of a Docker application. The pipeline includes the following stages:

Build: Builds the Docker image for the application.

Test: Runs any tests if required.

Deploy: Deploys the application to the target environment.

Steps to Reproduce
1. Install Jenkins
For Ubuntu:
Update your system:

bash
Copy
Edit
sudo apt update
Install Java (Jenkins requires Java):

bash
Copy
Edit
sudo apt install openjdk-11-jdk
Add the Jenkins repository and key:

bash
Copy
Edit
wget -q -O - https://pkg.jenkins.io/jenkins.io.key | sudo tee /usr/share/keyrings/jenkins.asc
sudo sh -c 'echo deb http://pkg.jenkins.io/debian/ stable main > /etc/apt/sources.list.d/jenkins.list'
Install Jenkins:

bash
Copy
Edit
sudo apt update
sudo apt install jenkins
Start Jenkins:

bash
Copy
Edit
sudo systemctl start jenkins
Enable Jenkins to start on boot:

bash
Copy
Edit
sudo systemctl enable jenkins
Access Jenkins in your web browser: Open http://localhost:8080 and follow the setup instructions. You’ll need the Jenkins unlock key, which you can find by running:

bash
Copy
Edit
sudo cat /var/lib/jenkins/secrets/initialAdminPassword
Install suggested plugins when prompted.

Create an admin user as prompted.

2. Clone the Repository
Clone the repository to your local machine:

bash
Copy
Edit
git clone https://github.com/saivijayy/task-2.git
3. Set Up Jenkins Pipeline
Open Jenkins and create a new Pipeline job.

In the Pipeline section, set the Definition to Pipeline script from SCM.

Select Git as the SCM, and provide the repository URL.

Set the Branch Specifier to */main (or the branch you’re using).

Jenkins will now automatically detect the Jenkinsfile in your repository and set up the pipeline accordingly.

4. Push Changes to Trigger Pipeline
Make a change to your repository (e.g., modify the application code).

Push the changes to GitHub.

Jenkins will automatically trigger the pipeline to Build, Test, and Deploy the application.

Pipeline Explanation
Build Stage: This step builds the Docker image based on the Dockerfile in the repository.

Test Stage: If needed, this can include unit or integration tests (though this is optional for now).

Deploy Stage: The built Docker image is deployed to your environment.

Tools Used
Jenkins: Used for automating the build and deployment pipeline.

Docker: Used to containerize the application.

GitHub: Version control system for managing the source code.
