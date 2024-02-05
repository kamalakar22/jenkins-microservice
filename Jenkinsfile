pipeline {
    agent { docker { image 'maven:13.8'}}
    stages {
        stage('GIT') {
            steps {
                git branch: 'main', url: 'https://github.com/kamalakar22/jenkins-microservice.git'
            }
        }

        stage('Build') {
            steps {
				sh 'node --version'
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






