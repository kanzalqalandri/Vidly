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

        stage (Push to Docker Hub) {
            steps {
                echo "Pushing the images to DockerHub"
                sh "docker tag vidly-front kanzal/vidly-front"
                sh "docker tag vidly-back kanzal/vidly-back"
                sh "docker login -u kanzal -p 'kanzal123'"
                sh "docker push kanzal/vidly-front"
                sh "docker push kanzal/vidly-back"
                
            }
        }

        stage (Deploy) {
            steps {
                echo "Deploying the container with docker compose"
                sh "docker compose down && docker compose up"
            }
        }
    }
}
