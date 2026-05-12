pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                echo 'Checking out code...'
            }
        }
        stage('Docker Build') {
            steps {
                // This builds the image using the Dockerfile in your repo
                sh 'docker build -t my-devops-app:latest .'
            }
        }

        stage('Docker Deploy') {
            steps {
                // This runs your app on Port 80
                sh 'docker run -d --name my-app-container -p 80:5000 my-devops-app:latest'
            }
        }
       stage('Cleanup Old Images') {
            steps {
                // This removes all unused images and containers...
                sh 'docker system prune -f'
            }
        }

    }
}