pipeline {
    agent any
    stages {
        stage('GIT') {
            steps {
                git branch: 'main', url: 'https://github.com/kamalakar22/jenkins-microservice.git'
            }
        }

        stage('Build') {
            steps {
                echo "Build"
            }
        }

        stage('Test') {
            steps {
                echo "Test"
            }
        }
    }
}




