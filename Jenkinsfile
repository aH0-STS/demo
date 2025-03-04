
pipeline {
    agent any

    environment {
        DOCKER_IMAGE = 'saiyash000/my-flask-app:latest'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git url:'https://github.com/aH0-STS/demo.git',branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Push Docker Image') {
            steps {
                withDockerRegistry([credentialsId: 'docker-hub-credentials', url: 'https://index.docker.io/v1/']) {
                    sh 'docker push $DOCKER_IMAGE'
                }
            }
        }
    }
}
