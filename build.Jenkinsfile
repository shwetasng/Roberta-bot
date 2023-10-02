pipeline {
    agent any

    environment {
        // add jenkins to docker group first.
        DOCKER_HUB_REGISTRY = "docker.io"
        DOCKER_HUB_CREDENTIALS = credentials('DockerHub')
        DOCKER_IMAGE_NAME = "shwetasng/roberta"
        DOCKER_IMAGE_VERSION = "v1.0" 
    }

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${DOCKER_HUB_REGISTRY}/${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_VERSION}")
                }
            }
        }

        stage('Push Docker Image to Docker Hub') {
            steps {
                script {
                    docker.withRegistry("${DOCKER_HUB_REGISTRY}", "${DOCKER_HUB_CREDENTIALS}") {
                        docker.image("${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_VERSION}").push()
                    }
                }
            }
        }
    }
}
