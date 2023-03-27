pipeline {
    agent any
    environment {
        DOCKER_IMAGE_NAME = 'nginxwebcustom'
        IP_ADDRESS = '127.0.0.1'
        PORT = '50'
    }
    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    sh "docker build -t ${DOCKER_IMAGE_NAME} ."
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    sh "docker run -d -p ${IP_ADDRESS}:${PORT}:80 ${DOCKER_IMAGE_NAME}"
                }
            }
        }
    }
}
