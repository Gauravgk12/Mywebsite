pipeline {
    agent any

    environment {
        IMAGE_NAME = "mywebsite-image"
        CONTAINER_NAME = "mywebsite-container"
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/Gauravgk12/Mywebsite.git', branch: 'main'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build(IMAGE_NAME)
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    // Stop and remove if container already exists
                    sh """
                        docker rm -f ${CONTAINER_NAME} || true
                        docker run -d --name ${CONTAINER_NAME} -p 8080:80 ${IMAGE_NAME}
                    """
                }
            }
        }
    }

    post {
        success {
            echo "Docker container '${CONTAINER_NAME}' is running on port 8080."
        }
        failure {
            echo "Something went wrong. Check the logs."
        }
    }
}
