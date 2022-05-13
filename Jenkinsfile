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
        withSonarQubeEnv(installationName: 'sonarqube', credentialsId: 'token-sonarqube') {
          sh 'sonar:sonar \
          -Dsonar.projectKey=UQ_function-laboratory_AYC_pFv8_U0bYDpZAccC'
        }
      }
    }
  }
}