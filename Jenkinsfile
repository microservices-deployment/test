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
            registry = "https://cloud.docker.com/repository/docker/microservicesdep/"
            registryCredential = 'Venkata@3'
            app.push("${env.BUILD_NUMBER}")
        }
    }
       catch (err)
        {
        currentBuild.result = 'Failure'
        }
    }
