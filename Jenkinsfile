pipeline {
  environment {
    registry = "https://cloud.docker.com/u/microservicesdep"
    registryCredential = 'microservicesdep'
    dockerImage = ''
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        checkout scm
    }
    }
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build("microservicesdep/image") 
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
         docker.withRegistry( '', registryCredential ) {
           dockerImage.push()
         }
        }
      }
    }
  }
}
