pipeline {
    agent any
    //environment {
        //dockerHOME = tool 'myDocker'
        //mavenHOME = tool 'myMaven'
        //PATH = "${dockerHOME}/bin:${mavenHOME}/bin:/usr/local/bin:${PATH}"//
    }

    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
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

