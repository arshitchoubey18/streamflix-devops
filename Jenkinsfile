pipeline {
  agent any

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Install') {
      steps {
        script {
          docker.image('node:20-alpine').inside {
            sh 'node -v'
            sh 'npm ci'
          }
        }
      }
    }

    stage('Build') {
      steps {
        script {
          docker.image('node:20-alpine').inside {
            sh 'npm run build'
          }
        }
      }
    }

    stage('Docker Build') {
      steps {
        sh 'docker build -t arshitchoubey18/streamflix:latest .'
      }
    }

    stage('Docker Push') {
      steps {
        withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
          sh 'echo $PASS | docker login -u $USER --password-stdin'
          sh 'docker push arshitchoubey18/streamflix:latest'
        }
      }
    }
  }
}