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
          sonar.projectKey=UQ_function-laboratory_AYC_pFv8_U0bYDpZAccC
          steps {
          def scannerHome = tool 'SonarScanner';
          withSonarQubeEnv(installationName: 'SonarScanner', credentialsId: 'token-sonarqube') {
            sh "${scannerHome}/bin/sonar-scanner"
          }       
       } 
    }
  }
}