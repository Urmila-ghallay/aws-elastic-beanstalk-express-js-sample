pipeline {
  agent {
    docker { 
        image 'node:16-alpine' }
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
          // Fails the build if critical vulnerabilities are found and outputs the log to snyk-failure-log.txt file
          sh 'snyk test --severity-threshold=critical | tee snyk-failure-log.txt' 
          //sh 'snyk test' 
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
      // log file name
      archiveArtifacts artifacts: 'logging.txt', fingerprint: true  
      echo 'logs' }  
      cleanWs()
      
    }
      
}   
      



