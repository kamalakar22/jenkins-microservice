pipeline {
    agent any
    environment {
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
                sh 'mvn -B -DskipTests clean package'
            }
        }
		stage('docker build image'){
			steps{
				script{
					docker.build("kamalakar2210/hello-world-nodejs:$(env.BUILD_TAG)")
				}
			}
		}
		
    } 
}
