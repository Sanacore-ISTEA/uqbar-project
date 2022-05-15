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

    stage('SonarQube analysis') {
      steps {
        script {
          def scannerHome = tool 'SonarQube Scanner_4.7';
          withSonarQubeEnv(installationName: 'SonarQube Scanner_4.7', credentialsId: 'token-sonarQube') {
            sh "${scannerHome}/bin/sonar-scanner"
          }
        }
      }
    }
 

    stage("Quality Gate") {
      steps {
        timeout(time: 1, unit: 'MINUTES') {
          waitForQualityGate abortPipeline: true, credentialsId: 'token-sonarQube'
        }
      }
    }

  }
}
