pipeline {
  environment {
    registry = "https://cloud.docker.com/u/microservicesdep"
    registryCredential = 'microservicesdep'
    dockerImage = ''
  }
  agent any
  stages {
    
    stage('Building Docker image') {
      steps{
        script {
          dockerImage = docker.build("microservicesdep/sample") 
        }
      }
    }
    stage('Push Image to Dockerhub') {
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
