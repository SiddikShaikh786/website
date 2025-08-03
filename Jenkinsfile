pipeline {
    agent any
     environment {
        EMAIL_RECIPIENT = 'siddikhshaikh786@gmail.com'
    }
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
       stage('Run Tests') {
            steps {
              sh 'npm test'      // for Node
              sh 'pytest'        // for Python
              sh 'mvn test'      // for Java
    }
}
 
    }
}
