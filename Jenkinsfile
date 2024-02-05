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
			echi 'I am awesome. I run always'
		}
		success {
			echi 'I run when you are successful'
		}
		failure {
			echi 'I run when you fail'
		}
	}
}




