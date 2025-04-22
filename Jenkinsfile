pipeline {
    agent any

    environment {
        IMAGE_NAME = "punitha07/flask-app:v1"
    }

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/Punitha07/flask-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${IMAGE_NAME}")
                }
            }
        }

        stage('Push to DockerHub') {
            steps {
                withDockerRegistry([credentialsId: 'dockerhub-creds', url: '']) {
                    script {
                        docker.image("${IMAGE_NAME}").push()
                    }
                }
            }
        }
    }
}
 
