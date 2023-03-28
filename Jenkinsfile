pipeline {
    agent any
    environment {
        DOCKER_IMAGE_NAME = 'yathishbhat/nginxwebcustom'
        IP_ADDRESS = '127.0.0.1'
        PORT = '50'
    }
    stages {
        stage('Build') {
            steps {
                script {
                    sh "docker build -t ${DOCKER_IMAGE_NAME} ."
                }
            }
        }
        stage('Artifact') {
            steps {
                script {
                      docker.withRegistry('https://hub.docker.com/', 'my-registry-credentials') {

                 
                        def dockerImage = docker.image(${DOCKER_IMAGE_NAME})
                        dockerImage.tag("${env.BUILD_NUMBER}", 'latest')

                        
                        dockerImage.push("${env.BUILD_NUMBER}")
                        dockerImage.push('latest')
                      }
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    sh "docker run -d -p ${IP_ADDRESS}:${PORT}:80 ${DOCKER_IMAGE_NAME}"
                }
            }
        }
    }
}
