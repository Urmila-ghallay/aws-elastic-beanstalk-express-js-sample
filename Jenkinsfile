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
    
    stage('Security Testing') {
      steps {
        script {
          // Run Snyk test
          withCredentials([string(credentialsId: 'Snyk-API', variable: 'SNYK_TOKEN')]) {
            sh 'snyk test --token=$SNYK_TOKEN'
          }
        }
      
      }
    }
    stage('Deploy') { 
            steps {
                echo 'Deploying application...'
            }
        }
    }
}
