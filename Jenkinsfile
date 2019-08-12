pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'BUILD'
      }
      post {
        always {
          echo "Esto siempre saldrá por pantalla"
        }
        failure {
          echo "Esto si falla"
        }
        success {
          echo "Y esto si todo ok"
        }
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
  }
  post {
    always {
      deleteDir()
    }
  }
}