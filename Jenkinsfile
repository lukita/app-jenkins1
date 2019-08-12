pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'BUILD'
      }
    }
    
    stage('Test') {
      steps {
        echo 'TEST'
      }
    }
    stage('Deploy') {
      steps {
        echo 'DEPLOY'
      }
    } 
    post {
      always {
        echo "Esto siempre saldrá por pantalla"
        deleteDir()
      }
      failure {

      }
      success {

      }
    }
  }
}