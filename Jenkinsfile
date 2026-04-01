pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'hanane2277/jenkins-demo'
    }

    stages {
        stage('Hello') {
            steps {
                echo 'Hello from GitHub + Jenkins 🚀'
            }
        }

        stage('Build') {
            steps {
                bat 'echo Building project...'
            }
        }

        stage('Test') {
            steps {
                bat 'echo Running tests...'
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
