pipeline {
  agent {
    docker { 
        image 'node:16' }
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
                sh 'npm start'
              
            }
        }
        stage('Deliver') { 
            steps {
                echo 'Deploying application...'
            }
        }
    }
}


