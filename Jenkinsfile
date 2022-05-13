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
        sh 'mvn clean package sonar:sonar \
        -Dsonar.projectKey=UQ_function-laboratory_AYC_pFv8_U0bYDpZAccC'
        }
        
       } 
      }
    }
  }
}