pipeline {
    agent any
    environment {
        DOCKER_IMAGE_NAME = 'my-jenkins-image'
        DOCKER_CONTAINER_NAME = 'my-jenkins-container'
    }

    stages {
        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${DOCKER_IMAGE_NAME}:${env.BUILD_NUMBER}", "-f /wtt-resume-parser-demo-aws/pms/Dockerfile .")
                }
            }
        }
        
        stage('Run Docker Container') {
            steps {
                script {
                    docker.image("${DOCKER_IMAGE_NAME}:${env.BUILD_NUMBER}").run("-d --name ${DOCKER_CONTAINER_NAME}")
                }
            }
        }
    }
}
