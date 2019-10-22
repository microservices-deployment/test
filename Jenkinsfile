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
    stage('Deploy to k8s')
    {
        steps
        {
        script
        {
            sh '''
            ssh root@192.168.28.149 "kubectl apply -f /tmp/deployment.yml"
            
            '''
            
        }
    }}
  }
}
