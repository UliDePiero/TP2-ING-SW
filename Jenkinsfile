pipeline {
  agent any
  stages {
    stage('Build') {
      agent {
        docker {
          image 'node:6-alpine'
          args 'p 3000:3000'
        }

      }
      steps {
        sh 'npm install'
      }
    }
    stage('Test') {
      environment {
        CI = 'true'
      }
      steps {
        sh './jenkins/scripts/test.sh'
      }
    }
    stage('Validate') {
      steps {
        input 'Finished using the web site? (Click "Proceed" to continue)'
        sh './jenkins/scripts/kill.sh'
      }
    }
    stage('Deploy') {
      steps {
        echo 'End'
      }
    }
  }
}