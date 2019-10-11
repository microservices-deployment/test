node {
    def app
    environment {
                 registry = "https://cloud.docker.com/repository/registry-1.docker.io/microservicesdep/test"
                 registryCredential = 'Venkata@3'
                  }
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
            docker.withRegistry( "" )
            {
            app.push("${env.BUILD_NUMBER}")
            }
        }
       } catch (err)
        {
        currentBuild.result = 'Failure'
        }
    }
