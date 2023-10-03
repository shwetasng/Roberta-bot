pipeline {
    agent any


    stages {
        stage('Build Docker Image') {
            steps{
                withCredentials([
                    usernamePassword(CredentialdId: 'DockerHub', usernameVariable: 'USERNAME', passwordVariable:'password')
                ]) {
                    sh '''
                    docker login --username $USERNAME --password $PASSWORD
                    docker build -t roberta:latest .
                    docker tag roberta:latest shwetasng/roberta:latest
                    docker push shwetasng/roberta:latest
                    '''
                }
            }
        }
        // stage('Trigger Deploy') {
        //     steps {
        //         build job: '<deploy-job-name>', wait: false, parameters: [
        //         string(name: 'ROBERTA_IMAGE_URL', value: "<full-url-to-docker-image>")
        // ]
        //     }
        // }
    }
}
