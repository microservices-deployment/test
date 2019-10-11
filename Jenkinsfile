pipeline {
  environment {
    registry = "https://cloud.docker.com/repository/docker/microservicesdep"
    registryCredential = 'microservicesdep'
  }
  agent any
  stage('clone repo') 
  {
       checkout scm
   }    
  
  stages {
    stage('Building image') {
      steps{
        script {
          docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
  }
}
