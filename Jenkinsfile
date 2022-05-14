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
          nodejs(nodeJSInstallationNme: 'nodejs'){
            sh "npm install"
              withSonarQubeEnv(installationName: 'sonarqube', credentialsId: 'token-sonarqube') {
                sh "npm install sonar-scanner"
                sh "npm run sonar"
          }
        }
      }
    }
  }
}
