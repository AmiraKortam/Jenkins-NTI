pipeline {
  agent any
  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/AmiraKortam/Jenkins-NTI.git'
      }
    }
    stage('Build Docker Image') {
      steps {
        script {
          docker.image('docker:latest').inside {
            docker.build('test-jenkins-image', '.')
          }
        }
      }
    }
    stage('Push Docker Image') {
      steps {
        script {
          docker.withRegistry('https://hub.docker.com/repository/docker/amiramohammed/test-jenkins/general', 'docker-hub-credentials') {
            docker.image('test-jenkins-image').push('latest')
          }
        }
      }
    }
  }
}
