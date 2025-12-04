pipeline { 
    agent any 
    stages { 
        stage('Build') { 
            steps { 
                echo "Build Docker Image" 
                bat "docker build -t mypythonflask2app ." 
            } 
        }
          stage('Run') { 
            steps { 
                echo "Run application in Docker Container" 
                bat "docker rm -f mycontainer || exit 0" 
                
                bat "docker run -d -p 5001:5000 --name mycontainer mypythonflask2app" 
                    
            } 
        } 
    } 
    post { 
        success { 
            echo 'Pipeline completed successfully!' 
        } 
        failure { 
            echo 'Pipeline failed. Please check the logs.' 
        } 
    } 
}
