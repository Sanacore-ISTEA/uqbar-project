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
        withSonarQubeEnv(installationName: 'sonarqube', credentialsId: 'token-sonarqube') {
          sh "npm install --save-dev mocha chai"
          sh "npm run test"
          sh "npm install sonar-scanner"
          sh "npm run sonar-scanner"
        }
      }
    }
  }
}