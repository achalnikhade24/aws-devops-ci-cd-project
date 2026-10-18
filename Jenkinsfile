
pipeline {
    agent any

    environment {
        DOCKERHUB_REPO = 'achaldocker01/aws-devops-website'
    }

    stages {
        stage('Checkout') {
            steps {
                echo 'GitHub repository connected successfully!'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKERHUB_REPO:latest .'
            }
        }

        stage('Push to Docker Hub') {
            steps {
                withCredentials([usernamePassword(
                    credentialsId: 'dockerHub-creds',
                    usernameVariable: 'DOCKER_USER',
                    passwordVariable: 'DOCKER_TOKEN'
                )]) {
                    sh '''
                        echo "$DOCKER_TOKEN" | docker login -u "$DOCKER_USER" --password-stdin
                        docker push "$DOCKERHUB_REPO:latest"
                        docker logout
                    '''
                }
            }
        }
    }
}
