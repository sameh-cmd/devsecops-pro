pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("TON_DOCKERHUB_USERNAME/devsecops-demo:latest")
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('', 'dockerhub-credentials') {
                        docker.image("TON_DOCKERHUB_USERNAME/devsecops-demo:latest").push()
                    }
                }
            }
        }
    }
}
