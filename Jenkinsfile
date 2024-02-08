		
		
pipeline {
    agent any
    environment {
        dockerHOME = tool 'myDocker'
        mavenHOME = tool 'myMaven'
        PATH = "${dockerHOME}/bin:${mavenHOME}/bin:/usr/local/bin:${PATH}"
	SONAR_HOST_URL = 'http://localhost:9000/'
        SONAR_TOKEN = credentials('squ_a96b052f08c7788256a6209a0b4384e5153bb65c') 
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
          stage('sonar') {
            steps {
                withSonarQubeEnv('sonarqube'){
                sh 'mvn sonae:sonar'
				}
            }
        }
        stage('docker build image') {
            steps {
                script {
                    dockerImage = docker.build("kamalakar2210/hello-world-nodejs:${env.BUILD_TAG}")
                }
            }
        }
        stage('docker push image') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub') {
                        dockerImage.push()
                        dockerImage.push('latest')
                    }
                }
            }
        }
        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
        }
    }
}
