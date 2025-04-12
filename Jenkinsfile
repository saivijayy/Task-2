pipeline {
    agent any

    environment {
        PATH = "/usr/local/bin:/usr/bin:${env.PATH}"
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
                sh 'npm test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying the app...'
                sh 'docker build -t jenkins-ci-app .'
            }
        }
    }
}
