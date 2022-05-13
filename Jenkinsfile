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
        withSonarQubeEnv(installationName: 'sonarqube', credentialsId: 'token-sonarqube') {
        sh "npm install sonar-scanner"
        sh "npm run sonar"
}
        
       } 
      }
    }
  }
}