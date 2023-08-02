pipeline {
    agent any 
    
    stages {
        stage("Clone Code") {
            steps {
                echo "Cloning the code"
                git url: "https://github.com/kanzalqalandri/Vidly.git", branch: "master"
            }
        }
        
        stage("Build") {
            steps {
                echo "Building the image"
                script {
                    docker.build("vidly-front", "./frontend")
                    docker.build("vidly-back", "./backend")
                }
            }
        }
        
    }
}

