pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t app:test .'
      }
    }
    stage('Test') {
      steps {
        echo 'TEST'
        sh 'docker run -d -p 80:80 --name app app:test'
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
        withCredentials([usernamePassword(credentialsId: 'DockerHubUser', passwordVariable: 'password', usernameVariable: 'username')]) {
          sh 'docker login -u $username -p $password'
          sh 'docker tag app:test karekai/app:stable'
          sh 'docker push karekai/app:stable'
        }
      }
    }
  }
  post {
    always {
      deleteDir()
    }
  }
}