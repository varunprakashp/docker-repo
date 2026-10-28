pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-website .'
            }
        }

        stage('Deploy Website') {
            steps {
                sh '''
                    docker rm -f my-website || true
                    docker run -d \
                      --name my-website \
                      -p 8081:80 \
                      devops-website
                '''
            }
        }
    }
}got 