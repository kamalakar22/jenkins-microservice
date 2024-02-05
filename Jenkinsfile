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
		stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
    } 
}
