pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''
                    docker login ...
                    docker build ...
                    docker tag ...
                    docker push ...
                '''
                }
        }
    }
}