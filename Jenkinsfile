		
pipeline {
    agent any

    environment {
       PATH = "C:\\maven\\bin;" + "\"" + env.PATH + "\""
    }

    stages {
        stage('Build') {
            steps {
                bat 'mvn -B -DskipTests clean package'
            }
        }
        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
            }
        }
    }
}

