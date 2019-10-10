node {
    def app
    try {
        
        stage('clone repo')
        {
            checkout scm
        }
        
        stage('Docker Build')
        {
            app = docker.build("image1")
        }
        stage('Push')
        {
            environment {
                 registry = "https://cloud.docker.com/repository/registry-1.docker.io/microservicesdep/test"
                 registryCredential = 'Venkata@3'
                        }
        }
       } catch (err)
        {
        currentBuild.result = 'Failure'
        }
    }
