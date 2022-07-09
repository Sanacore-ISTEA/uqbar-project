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
          //  sh "${scannerHome}/bin/sonar-scanner"
          sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=UQ_function-laboratory_AYC_pFv8_U0bYDpZAccC'
          }
        }
      }
    }
 

    stage("Quality Gate") {
      steps {
        script{
          timeout(time: 1, unit: 'MINUTES') {
            def qg = waitForQualityGate abortPipeline: true, credentialsId: 'token-sonarQube';        
            if (qg.status != 'OK') {                                
                              echo "Status: ${qg.status}"
                              error "Pipeline aborted due to quality gate failure: ${qg.status}"
              }
          }
        }      
      }
    }

  }
}
