pipeline {
    agent any

    // Optional: environment variables
    environment {
        IMAGE_NAME = "flask-ci-cd-app"
        CONTAINER_NAME = "flask-app"
        PORT = "5000"
    }

    stages {

        stage('Checkout Code') {
            // This ensures Jenkins checks out the correct branch
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: 'main']], // explicitly specify main branch
                    userRemoteConfigs: [[url: 'https://github.com/ganesh-966/jenkins-docker-demo.git']]
                ])
            }
        }

        stage('Build Docker Image') {
            steps {
                echo "Building Docker image..."
                sh "docker build -t ${IMAGE_NAME} ."
            }
        }

        stage('Run Docker Container') {
            steps {
                echo "Running Docker container..."
                sh """
                docker stop ${CONTAINER_NAME} || true
                docker rm ${CONTAINER_NAME} || true
                docker run -d -p ${PORT}:${PORT} --name ${CONTAINER_NAME} ${IMAGE_NAME}
                """
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully!"
        }
        failure {
            echo "Pipeline failed. Check logs for errors."
        }
    }
}
