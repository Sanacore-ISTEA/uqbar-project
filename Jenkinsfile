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
          sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=IV_istea---virtualizacion_AYCG_eOVveIWPZuRFBuF'
        }
      }
    }
  }
}