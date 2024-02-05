pipeline {
    agent any
    environment {
        dockerHOME = tool 'myDocker'
        mavenHOME = tool 'myMaven'
        PATH = "${dockerHOME}/bin:${mavenHOME}/bin:/usr/local/bin:${PATH}"
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
        stage('Get Kubernetes Nodes') {
            steps {
                sh 'kubectl get nodes -o wide'
            }
        }
    }
}
