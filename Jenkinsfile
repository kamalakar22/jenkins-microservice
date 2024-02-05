pipeline {
    agent { docker { image 'maven:3.6.3'}}
    stages {
        stage('GIT') {
            steps {
                git branch: 'main', url: 'https://github.com/kamalakar22/jenkins-microservice.git'
            }
        }

        stage('Build') {
            steps {
				sh 'mvn --version'
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






