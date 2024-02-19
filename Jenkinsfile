pipeline {
    agent any
    
    stages {
        stage('Git Checkout') {
            steps {
                git 'https://github.com/adikesavanaidug2404/hotstarproject.git'
            }
        }
        stage('Build&Tag Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-token', toolName: 'docker') {
                        sh "docker build -t adikesavanaidug2404/hotstartpro:v1 ."
                    }
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-token', toolName: 'docker') {
                        sh "docker push adikesavanaidug2404/hotstartpro:v1"
                    }
                }
            }
        }
        stage('Push Docker Image') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'docker-token', toolName: 'docker') {
                        sh "docker run -d -p 3000:3000 adikesavanaidug2404/hotstartpro:v1"
                    }
                }
            }
        }
    }
}
