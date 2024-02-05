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
	post{
		always {
			ech0 'I am awesome. I run always'
		}
		success {
			ech0 'I run when you are successful'
		}
		failure {
			ech0 'I run when you fail'
		}
	}
}




