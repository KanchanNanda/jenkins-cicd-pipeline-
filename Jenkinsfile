pipeline {

    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                url: 'git@github.com:KanchanNanda/jenkins-cicd-pipeline.git'
            }
        }


        stage('Build Docker Image') {
            steps {
                sh '''
                docker build -t jenkins-demo ./app
                '''
            }
        }


        stage('Remove Old Container') {
            steps {
                sh '''
                docker stop jenkins-demo-container || true
                docker rm jenkins-demo-container || true
                '''
            }
        }


        stage('Run New Container') {
            steps {
                sh '''
                docker run -d \
                -p 8081:80 \
                --name jenkins-demo-container \
                jenkins-demo
                '''
            }
        }
    }
}
