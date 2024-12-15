pipeline {
    agent any
    stages {
        stage('Checkout Code') {
            steps {
                // Clone the repository containing the Dockerfile and project files
                git 'https://github.com/pratham7289/Html-CSS-Project.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    // Build the Docker image and tag it as 'latest'
                    sh 'docker build -t pratham7289/python-app:latest .'
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    // Login and push the Docker image with the 'latest' tag to Docker Hub
                    docker.withRegistry('https://index.docker.io/v1/', 'docker-hub-credentials-id') {
                        sh 'docker push pratham7289/python-app:latest'
                    }
                }
            }
        }
    }
}
