pipeline {
  agent {
    docker {
      image 'node:lts-buster-slim'
    }
  }
  stages {
    stage  ("Install dependeincies") {
      steps {
        sh 'pwd'
        sh 'ls'
        sh 'npm install'
      }
    }
    stage ("Test"){
      steps{
        sh 'npm run test'
      }
    }
    stage ("Build"){
      steps{
        sh 'npm run build'
      }
    } 
    stage ("Build Dockerfile") {
      steps{
        sh 'docker build -t georgeelhamy/jenkins:latest'
      }
    }
    // stage ("Push to dockerHub"){
    //   steps{
    //     sh 'docker push georgeelhamy/jenkins:latest'
    //   }
    // }
  }
}
