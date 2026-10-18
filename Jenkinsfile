pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'GitHub repository connected successfully!'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t aws-devops-website .'
            }
        }
    }
}
