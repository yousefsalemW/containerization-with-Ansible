pipeline {
    agent any

    environment {
        IMAGE_NAME = "containerization-app"
        IMAGE_TAG  = "latest"
        CONTAINER  = "containerization-app"
    }

    stages {

        stage('Checkout Source Code') {
            steps {
                echo "Downloading source code..."
                checkout scm
            }
        }

        stage('Show Workspace') {
            steps {
                echo "Workspace contents:"
                sh 'pwd'
                sh 'ls -lah'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo "Building Docker image..."
                sh 'docker build -t ${IMAGE_NAME}:${IMAGE_TAG} .'
            }
        }

        stage('Remove Old Container') {
            steps {
                echo "Removing old container if it exists..."

                sh 'docker stop ${CONTAINER} || true'
                sh 'docker rm ${CONTAINER} || true'
            }
        }

        stage('Run Container') {
            steps {
                echo "Starting new container..."

                sh 'docker run -d --name ${CONTAINER} -p 3000:3000 ${IMAGE_NAME}:${IMAGE_TAG}'
            }
        }

        stage('Verification') {
            steps {
                echo "Checking running containers..."

                sh 'docker ps'
            }
        }
    }

    post {

        success {
            echo "Pipeline completed successfully."
        }

        failure {
            echo "Pipeline failed."
        }

        always {
            echo "Pipeline execution finished."
        }

    }
}