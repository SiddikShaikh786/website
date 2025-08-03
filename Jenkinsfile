pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'develop', url: 'https://github.com/SiddikShaikh786/website.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'sudo docker build -t image1 .'
            }
        }

        stage('Remove Old Container') {
            steps {
                sh 'sudo docker stop C2 || true'
                sh 'sudo docker rm C2 || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'sudo docker run -itd --name C2 -p 83:80 image1'
            }
        }
    }
}
