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
        echo 'Testing...'
          snykSecurity(
            snykInstallation: 'snyk@manual',
            snykTokenId: 'Snyk-API-Token',
          
        )
      
      }
    }
    stage('Deploy') { 
            steps {
                echo 'Deploying application...'
            }
        }
    }
}
