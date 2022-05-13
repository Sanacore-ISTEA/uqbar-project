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
      steps {
        script{
        sh "npm install sonar-scanner"
        withSonarQubeEnv(installationName: 'sonarqube', credentialsId: 'token-sonarqube') {
        sh 'sonar-scanner -Dsonar.projectKey=UQ_function-laboratory_AYC_pFv8_U0bYDpZAccC -Dsonar.sources=./src'
}
        
       } 
      }
    }
  }
}