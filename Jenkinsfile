pipeline {
    agent any

    environment {
        DOCKER_BUILDKIT = 1
        PATH = "/usr/local/bin:/usr/bin:$PATH"
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                docker.image('node:18').inside {
                    sh 'npm install'
                }
            }
        }

        stage('Test') {
            steps {
                docker.image('node:18').inside {
                    sh 'echo "No tests yet" && exit 0'
                }
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
