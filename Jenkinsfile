pipeline {
  agent {
    docker {
      image 'docker:latest'  
      label 'my-node'
    }
  }
  stages {
    stage('Checkout') {
      steps {
        git 'https://github.com/AmiraKortam/Jenkins-NTI.git'
      }
    }
    stage('Build Docker Image') {
      steps {
        script {
          docker.build('test-jenkins-image', '.')
        }
      }
    }
    stage('Push Docker Image') {
      steps {
        script {
          docker.withRegistry('https://amiramohammed/test-jenkins', 'docker-hub-credentials') {
            docker.image('test-jenkins-image').push('latest')
          }
        }
      }
    }
  }
}
