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
              docker.withRegistry('https://cloud.docker.com/repository/registry-1.docker.io/microservicesdep/test', 'Venkata@3')
              app.push("${env.BUILD_NUMBER}")
         }
        }
       catch (err)
        {
        currentBuild.result = 'Failure'
        }
    }
