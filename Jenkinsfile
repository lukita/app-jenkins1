pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t app .'
      }
    }
    stage('Test') {
      steps {
        echo 'TEST'
        sh 'docker run -it app'
        sh '/bin/nc -vz localhost 80'
      }
      post {
        always {
          sh 'docker stop app'
        }
      }
    }
    stage('Push Registry') {
      steps {
        sh 'docker tag app karekai/app:stable'
        sh 'docker push karekai/app:stable'
      }
    }
  }
  post {
    always {
      deleteDir()
    }
  }
}