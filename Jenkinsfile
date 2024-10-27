pipeline {
    agent any
    environment {
        DOCKER_USERNAME = "kaderdevops"  // Docker Hub username
        DOCKER_CREDENTIALS = "docker_jenkins_access" // Jenkins credentials ID
        IMAGE_NAME = "goal-backend-jenkins"
        TAG = "jenkins"
    }
    stages {
        stage('Build Backend') {
            steps {
                script {
                    // Build the frontend Docker image
                    docker.build("${DOCKER_USERNAME}/${IMAGE_NAME}:${TAG}", ".")
                }
            }
        }
        
        stage('Push Backend Image') {
            steps {
                script {
                    // Use the correct Docker Hub registry URL for login
                    docker.withRegistry("https://index.docker.io/v1/", "${DOCKER_CREDENTIALS}") {
                        docker.image("${DOCKER_USERNAME}/${IMAGE_NAME}:${TAG}").push()
                    }
                }
            }
        }
    }
}
