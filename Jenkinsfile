pipeline {
    agent any
	environment{
		dockerHOME = tool 'myDocker'
		mavenHOME = tool 'myMaven'
		PATH = "${dockerHOME}/bin:${mavenHOME}/bin:${PATH}"
	}

    stages {
        stage('version') {
            steps {
                sh 'mvn --version'
				sh 'docker --version'
            }
        }
		stage('Build') {
            steps {
                sh "mvn clean compile"
				 
				
            }
        }
		stage('Test') {
            steps {
                sh "mvn test"	
            }
        }
		stage('Integration-Test') {
            steps {
                sh "mvn failsafe:integration-test failsafe:verify"	
            }
        }
    } 
	
}






