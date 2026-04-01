pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'hanane2277/jenkins-demo'
    }

    stages {
        stage('Build') {
            steps {
                bat 'echo Building app...'
            }
        }

        stage('Test') {
            steps {
                bat 'echo Testing app...'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t %DOCKER_IMAGE% .'
            }
        }

        stage('Push Docker Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'docker-hub', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    bat 'docker login -u %USER% -p %PASS%'
                    bat 'docker push %DOCKER_IMAGE%'
                }
            }
        }
    }
}
