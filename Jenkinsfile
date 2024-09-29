pipeline {
  agent {
    docker { 
        image 'node:16' }
  }
  environment {
    // Store your Snyk token in Jenkins credentials 
    SNYK_TOKEN = credentials('snyk-token-api')
  }
  stages {
    stage('Build') {
      steps {
        sh 'npm install --save'
      }
    }

    stage('Snyk Security Testing for Vulnerability') {
      steps {
        script { 
          // Run Snyk test 
          sh 'npm install -g snyk' 
          sh 'snyk test' 
          } 
      } 
    } 
    stage('Snyk Monitor') { 
      steps { 
        script { 
          // Run Snyk monitor to track vulnerabilities 
          sh 'snyk monitor'
          } 
      } 
    } 

    stage('Deploy') { 
            steps {
                echo 'Deploying application...'
            }
    }
  }

  post {
      // Clean after build
    always {
      echo 'Cleaning up' }
      sucess {
        echo 'Build completed successfully' }

      failure {
        echo 'build failed'
      }


    }
      //cleanWs()
      
      
}


