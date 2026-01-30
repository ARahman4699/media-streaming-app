pipeline {
    agent any

    stages {
        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/ARahman4699/media-streaming-app.git'
            }
        }

        stage('Build App') {
            steps {
                echo "Building application..."
            }
        }

        stage('Test App') {
            steps {
                echo "Running basic tests..."
            }
        }
    }
}
