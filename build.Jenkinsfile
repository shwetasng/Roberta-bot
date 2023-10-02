pipeline {
    agent any

    environment {
        // Define your Docker Hub registry URL
        DOCKER_HUB_REGISTRY = "docker.io"
        // Define your Docker Hub username and password credentials ID
        DOCKER_HUB_CREDENTIALS = credentials('DockerHub')
        // Define your Docker image name and version
        DOCKER_IMAGE_NAME = "shwetasng/roberta"
        DOCKER_IMAGE_VERSION = "v1.0" // Replace with your desired version
    }

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    // Build and tag the Docker image
                    docker.build("${DOCKER_HUB_REGISTRY}/${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_VERSION}")
                }
            }
        }

        stage('Push Docker Image to Docker Hub') {
            steps {
                script {
                    // Authenticate with Docker Hub
                    docker.withRegistry("${DOCKER_HUB_REGISTRY}", "${DOCKER_HUB_CREDENTIALS}") {
                        // Push the Docker image to Docker Hub
                        docker.image("${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_VERSION}").push()
                    }
                }
            }
        }
    }
}
