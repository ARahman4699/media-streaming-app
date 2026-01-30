pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "rahman4699/media-streaming-app:${BUILD_NUMBER}"
    }

    stages {

        stage('Checkout Code') {
            steps {
                // Pull code from GitHub
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                // Build Docker image with current build number
                sh 'docker build -t $DOCKER_IMAGE .'
            }
        }

        stage('Push Docker Image') {
            steps {
                // Push image to Docker Hub
                sh 'docker push $DOCKER_IMAGE'
            }
        }

        stage('Deploy') {
            steps {
                // Run Ansible playbook to deploy container
                sh 'ansible-playbook deploy.yml'
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully!"
        }
        failure {
            echo "Pipeline failed! Check logs for errors"
        }
    }
}
}
