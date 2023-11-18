pipeline {
  agent any
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  environment {
    DOCKERHUB_CREDENTIALS = credentials('dewan11415-dockerhub')
  }
  stages {
    stage('Check Location'){
        steps {
        sh '/var/lib/jenkins/workspace/app-1/task1/src/app1'
        sh 'pwd'
      }
    }
    stage('Build') {
      steps {
        sh 'docker build -t dewan11415/app1:latest .'
      }
    }
    stage('Login') {
      steps {
        sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
      }
    }
    stage('Push') {
      steps {
        sh 'docker push dewan11415/app1:latest'
      }
    }
  }
  post {
    always {
      sh 'docker logout'
    }
  }
}