pipeline {
    agent any
    environment {
        DOCKER_IMAGE = "your-dockerhub-username/static-html-site:latest"  // Replace with your Docker Hub username and image name
        DOCKER_CREDENTIALS = 'docker-hub-credentials-id'                 // Replace with the ID of your Docker Hub credentials in Jenkins
    }
    stages {
        stage('Checkout Code') {
            steps {
                // Clone the repository containing the Dockerfile and project files
                git 'https://github.com/your-repo/your-html-css-project.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t $DOCKER_IMAGE .'
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    // Login and push the Docker image to Docker Hub
                    docker.withRegistry('https://index.docker.io/v1/', DOCKER_CREDENTIALS) {
                        sh 'docker push $DOCKER_IMAGE'
                    }
                }
            }
        }
    }
}
