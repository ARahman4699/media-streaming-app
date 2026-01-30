pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "abdurrahman72/media-streaming-app"
    }

    stages {
        stage('Checkout Code') {
            steps {
                // Pull code from GitHub
                git url: 'https://github.com/ARahman4699/media-streaming-app.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                // Build Docker image with BUILD_NUMBER and latest tag
                sh "docker build -t ${DOCKER_IMAGE}:${BUILD_NUMBER} -t ${DOCKER_IMAGE}:latest ."
            }
        }

        stage('Push Docker Image') {
            steps {
                // Push both tags to Docker Hub
                sh "docker push ${DOCKER_IMAGE}:${BUILD_NUMBER}"
                sh "docker push ${DOCKER_IMAGE}:latest"
            }
        }

        stage('Deploy') {
            steps {
                // Run your Ansible playbook
                sh "ansible-playbook deploy.yml"
            }
        }
    }

    post {
        success {
            echo 'Pipeline finished successfully ✅'
        }
        failure {
            echo 'Pipeline failed ❌ Check logs!'
        }
    }
}

