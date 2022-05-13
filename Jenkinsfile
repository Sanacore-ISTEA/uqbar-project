pipeline {
  agent any
  stages {
    stage('test'){
      steps {
        sh 'mvn test'
      }
    }
    stage('build') {
      steps {
        sh 'mvn package'
      }
    }

  }
}