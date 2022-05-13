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
        sh 'npm test'
      }
    }

    stage('SonarQube Analysis') {
      def scannerHome = tool 'sonarqube';
      steps {
        withSonarQubeEnv(installationName: 'sonarqube', credentialsId: 'token-sonarqube') {
          sh 'sh "${scannerHome}/bin/sonar-scanner" \
          -Dsonar.projectKey=UQ_function-laboratory_AYC_pFv8_U0bYDpZAccC'
        }
      }
    }
  }
}