pipeline {
    agent any

    environment {
        IMAGE_NAME = "flask-cicd"
    }

    stages {
        stage('Clone Source Code') {
            steps {
                git 'https://github.com/<your-user>/<your-repo>.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh "docker build -t $IMAGE_NAME ."
            }
        }

        stage('Run Docker Container') {
            steps {
                sh "docker rm -f flask_container || true"
                sh "docker run -d -p 5000:5000 --name flask_container $IMAGE_NAME"
            }
        }
    }
}
