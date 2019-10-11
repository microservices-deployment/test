pipeline {
  environment {
    registry = "https://cloud.docker.com/repository/docker/microservicesdep"
    registryCredential = 'microservicesdep'
  }
  agent any
  stages {
  stage('clone repo') 
  {
    steps {
       checkout scm
   }   
  }
    stage('Building image') {
      steps{
        script {
          docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
  }
}
