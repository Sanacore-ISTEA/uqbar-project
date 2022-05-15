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
          def scannerHome = tool 'SonarQube';
          withSonarQubeEnv(installationName: 'sonarqube', credentialsId: 'token-sonarqube') {
            sh "${scannerHome}/bin/sonar-scanner"
          }
        }
      }
    }
 

    stage("Quality Gate") {
      steps {
        timeout(time: 1, unit: 'MINUTES') {
          waitForQualityGate abortPipeline: true, credentialsId: 'token-sonarQube'
               if (qualitygate.status != "OK") {
         error "Pipeline aborted due to quality gate coverage failure: ${qualitygate.status}"
      }
        }
      }
    }

  }
}
