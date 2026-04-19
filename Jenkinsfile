pipeline {
    agent any

    environment {
        IMAGE_NAME = "arshitchoubey18/streamflix"
    }

    stages {
        stage('Checkout') {
            steps {
                    git branch: 'main', url: 'https://github.com/arshitchoubey18/streamflix-devops.git'
            }
        }

        stage('Install') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Docker Push') {
            steps {
                sh 'docker push $IMAGE_NAME'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker rm -f streamflix || true
                docker run -d -p 8080:80 --name streamflix $IMAGE_NAME
                '''
            }
        }
    }
}