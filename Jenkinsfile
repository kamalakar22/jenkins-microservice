pipeline {
    agent any
	environment{
		dockerHOME = tool 'myDocker'
		mavenHOME = tool 'myMaven'
		PATH = "$dockerHOME/bin:$mavenHOME/bin$PATH"
	}

    stages {
        stage('version') {
            steps {
                sh 'mvn --version'
				sh 'docker --version'
            }
        }
    } 
	
}






