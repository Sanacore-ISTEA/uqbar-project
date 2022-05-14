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
          sonar.projectKey=UQ_function-laboratory_AYC_pFv8_U0bYDpZAccC
          def scannerHome = tool 'SonarScanner';
          withSonarQubeEnv() {
          sh "${scannerHome}/bin/sonar-scanner"
        }
        
       } 
      }
    }
  }
}