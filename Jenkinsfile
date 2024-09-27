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
                sh 'npm run'            
                sh 'npm test'
            }
        }
        stage('Deliver') { 
            steps {
                echo 'Deploying application...'
            }
        }
    }
}


