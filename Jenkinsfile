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
        withSonarQubeEnv(installationName: 'sonarqube', credentialsId: 'token-sonarqube') {
        sh '/opt/sonarqube/sonar \
        -Dsonar.projectKey=UQ_function-laboratory_AYC_pFv8_U0bYDpZAccC'
}
        
       } 
      }
    }
  }
}