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
          dockerImage = docker.build("microservicesdep/release5:latest") 
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
    stage('deploy to k8s')
    {
        steps
        {
        script
        {
            sh '''
            ssh root@192.168.28.149 "cd /tmp/;rm -rf *;git clone https://github.com/microservices-deployment/test.git;kubectl apply -f /tmp/test/deployment.yml"
            '''
            
        }
    }
        
    } 
  }
}

