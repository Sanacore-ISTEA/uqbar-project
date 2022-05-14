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
                        env.NODEJS_HOME = "${tool 'NodeJS'}"
                def scannerHome = tool "sonarqube"
        sh "npm i sonarqube-scanner"
        withSonarQubeEnv(installationName: 'sonarqube', credentialsId: 'token-sonarqube') {
        sh 'sonarqube-scanner -Dsonar.projectKey=UQ_function-laboratory_AYC_pFv8_U0bYDpZAccC -Dsonar.sources=./src'
}
        
       } 
      }
    }
  }
}