pipeline {
    agent any
    environment {
        DOCKER_IMAGE_NAME = 'nginxweb1'
        CONTAINER_NAME = 'my-docker-container1'
        IP_ADDRESS = '127.0.0.1'
        PORT = '80'
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
                    sh "docker run -d -p ${IP_ADDRESS}:${PORT}:${PORT} --name ${CONTAINER_NAME} ${DOCKER_IMAGE_NAME}"
                }
            }
        }
    }
}
