pipeline {
  agent any 
  environment{
    CREDENTIALS = credentials('dockerhub')
  }
  stages {
    stage  ("Install dependeincies") {
      agent {
        docker {image 'node:lts-buster-slim'}
      }
      steps {
        sh 'pwd'
        sh 'ls'
        sh 'npm install'
      }
    }
    stage ("Test"){
      agent {
        docker {image 'node:lts-buster-slim'}
      }
      steps{
        sh 'npm run test'
      }
    }
    stage ("Build"){
      agent {
        docker {image 'node:lts-buster-slim'}
      }
      steps{
        sh 'npm run build'
      }
    } 
    stage ("Build Dockerfile") {
      steps{
        sh 'docker build -t georgeelhamy/jenkins:latest'
      }
    }
    stage ("login") {
      steps{
        sh 'echo usernamre = ${CREDENTIALS_USR}'
        sh 'echo password = ${CREDENTIALS_PSW}'
        SH 'docker login -u ${CREDENTIALS_USR} -p ${CREDENTIALS_PSW}
      }
    }
    stage ("Push to dockerHub"){
      steps{
        sh 'docker push georgeelhamy/jenkins:latest'
      }
    }
  }
}
