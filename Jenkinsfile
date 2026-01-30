stage('Build Docker Image') {
    steps {
        // Build image with BUILD_NUMBER AND latest tag
        sh 'docker build -t abdurrahman72/media-streaming-app:${BUILD_NUMBER} -t abdurrahman72/media-streaming-app:latest .'
    }
}

stage('Push Docker Image') {
    steps {
        // Push both BUILD_NUMBER tag AND latest tag to Docker Hub
        sh 'docker push abdurrahman72/media-streaming-app:${BUILD_NUMBER}'
        sh 'docker push abdurrahman72/media-streaming-app:latest'
    }
}

