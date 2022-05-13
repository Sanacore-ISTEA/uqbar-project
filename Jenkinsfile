pipeline {
  agent any
  stages {
    stage('test'){
      steps {
        sh 'npm test'
      }
    }
    stage('build') {
      steps {
        sh 'npm package'
      }
    }

  }
}