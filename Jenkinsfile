pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t media-streaming-app:${BUILD_NUMBER} .'
            }
        }

        stage('Run Docker Container (Test)') {
            steps {
                sh '''
                docker stop media-test || true
                docker rm media-test || true
                docker run -d --name media-test -p 8081:80 media-streaming-app:${BUILD_NUMBER}
                docker ps | head -5
                '''
            }
        }
    }
}

