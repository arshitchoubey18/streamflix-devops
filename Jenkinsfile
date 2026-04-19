pipeline {
    agent any

    environment {
        IMAGE_NAME = "streamflix-devops"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/arshitchoubey18/streamflix-devops.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build App') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f streamflix-app || true
                docker run -d -p 8080:80 --name streamflix-app $IMAGE_NAME
                '''
            }
        }
    }
}