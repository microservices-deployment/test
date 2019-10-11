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
          dockerImage = docker.build("image") 
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
         
           docker.Image('registryCredential').push()
          
        }
      }
    }
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $registry:$BUILD_NUMBER"
      }
    }
  }
}
