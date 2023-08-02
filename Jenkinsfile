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
                sh "docker build -t vidly-front ./frontend"
                sh "docker build -t vidly-back ./backend"
            }
        }
    }
}
