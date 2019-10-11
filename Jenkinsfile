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
             docker.withRegistry('https://cloud.docker.com', 'microservicesdep') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
         }
        }
       catch (err)
        {
        currentBuild.result = 'Failure'
        }
    }
