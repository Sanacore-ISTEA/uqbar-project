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
        dir("build_node")
        sh 'npm test'
      }
    }
  }
}