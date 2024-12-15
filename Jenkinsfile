pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                git url: "https://github.com/pratham7289/Html-CSS-Project.git", branch: "main"
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t pratham7289/python-app:latest .'
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    // Push the Docker image to Docker Hub
                    withCredentials([usernamePassword(credentialsId: 'docker-hub-credentials-id', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
                        sh 'docker login -u $DOCKER_USERNAME -p $DOCKER_PASSWORD'
                        sh 'docker push pratham7289/python-app:latest'
                    }
                }
            }
        }
    }
}
