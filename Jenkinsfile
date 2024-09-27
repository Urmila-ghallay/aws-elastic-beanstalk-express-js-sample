pipeline {
  agent {
    docker { 
        image 'node:16-alpine' }
  }
  stages {
    stage('Build') {
      steps {
        sh 'npm install --save'
      }
    }
    stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        
    }
}


