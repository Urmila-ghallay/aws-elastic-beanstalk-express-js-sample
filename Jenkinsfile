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
        stage('Deliver') { 
            steps {
                sh './jenkins/scripts/deliver.sh' 
                input message: 'Finished using the web site? (Click "Proceed" to continue)' 
                sh './jenkins/scripts/kill.sh' 
            }
        }
    }
}


