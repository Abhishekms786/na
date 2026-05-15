pipeline {
    agent any

    environment {
        IMAGE_NAME = "abhishekms2005/my-python-app"
        DOCKERHUB_CREDENTIALS = "dockerhub-creds"
    }

    stages {

        stage('Clone Repository') {
            steps {
                git 'https://github.com/Abhishekms786/na.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${IMAGE_NAME}:latest")
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('', DOCKERHUB_CREDENTIALS) {
                        docker.image("${IMAGE_NAME}:latest").push()
                    }
                }
            }
        }
    }
}
