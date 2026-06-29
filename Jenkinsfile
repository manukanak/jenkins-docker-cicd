stage('Debug') {
    steps {
        sh 'whoami'
        sh 'id'
        sh 'groups'
        sh 'which docker'
        sh 'docker ps'
    }
}
pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins-docker-cicd:v1 .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run -d -p 8081:80 --name website-container jenkins-docker-cicd:v1 || true'
            }
        }
    }
}
