pipeline {
    agent any

    environment {
        IMAGE_NAME = 'saivijayy/devops-intern-app'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            agent {
                docker { image 'node:18' }
            }
            steps {
                sh 'npm install'
            }
        }

        stage('Test') {
            agent {
                docker { image 'node:18' }
            }
            steps {
                sh 'npm test'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying the app..."
                sh 'docker build -t $IMAGE_NAME .'
                sh 'docker rm -f app-container || true'
                sh 'docker run -d -p 3000:3000 --name app-container $IMAGE_NAME'
            }
        }
    }
}
