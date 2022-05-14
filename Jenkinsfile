pipeline {
  agent any
  stages {
        stage('Install dependencies') {
      steps {
        sh 'npm install'
      }
    }
    stage('test'){
      steps {
        sh 'npm run build'
      }
    }

    stage('SonarQube Analysis') {
      steps {
        script{
        def scannerHome = tool 'SonarQubeScanner4'
          withSonarQubeEnv('SonarQubeScanner4') {
            sh "${scannerHome}/bin/sonar-scanner"
        }
        
       } 
      }
    }
  }
}