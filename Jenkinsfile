pipeline {
    agent any

    environment {
        DOCKER_EXE_PATH = "C:\\Program Files\\Docker\\Docker"
        IMAGE_NAME = "your-docker-username/your-image-name"
        IMAGE_TAG = "${env.BUILD_NUMBER}"
    }

    stages {
        stage('Build') {
            steps {
                bat 'mvn -B -DskipTests clean package'
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
        }

        stage('Build and Push Docker Image') {
            steps {
                script {
                    // Build Docker image
                    bat "\"${DOCKER_EXE_PATH}\" build -t ${IMAGE_NAME}:${IMAGE_TAG} ."
                    
                    // Push Docker image
                    bat "\"${DOCKER_EXE_PATH}\" push ${IMAGE_NAME}:${IMAGE_TAG}"
                }
            }
        }
    }
}
