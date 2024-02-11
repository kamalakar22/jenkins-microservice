		
pipeline {
    agent any

    environment {
        PATH = "$PATH:/opt/maven/bin"
    }

    stages {
        stage('Build') {
            steps {
                 sh 'mvn -B -DskipTests clean package'
            }
        }
		stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
        }
		
    }
}
