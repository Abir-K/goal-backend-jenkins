pipeline {
    agent any
    environment {
        // Set Docker registry details here
        DOCKER_REGISTRY = "docker.io/kaderdevops"
        DOCKER_CREDENTIALS = "dockeraccess"
    }
    stages {
        stage('Build Backend') {
            steps {
                script {
                    // Build the backend Docker image
                    docker.build("${DOCKER_REGISTRY}/goal-back-jenkins:jenkins .")
                }
            }
        }
        
        stage('Pushing Images') {
            steps {
                script {
                    docker.withRegistry("https://${DOCKER_REGISTRY}", "${DOCKER_CREDENTIALS}") {
                        docker.image("${DOCKER_REGISTRY}/goal-back-jenkins:jenkins").push()
                    }
                }
            }
        }
    }
}
