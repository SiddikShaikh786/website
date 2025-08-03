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
                // These are examples. Keep only the one you need based on your project type.
                // sh 'npm test'    // Uncomment for Node.js
                // sh 'pytest'      // Uncomment for Python
                // sh 'mvn test'    // Uncomment for Java
                echo 'Running dummy test...'
            }
        }
    }

    post {
        success {
            mail to: "${EMAIL_RECIPIENT}",
                 subject: "✅ Build Success: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: """Hello Siddik,

✅ Jenkins job *${env.JOB_NAME}* completed successfully!

- Build Number: ${env.BUILD_NUMBER}
- Build URL: ${env.BUILD_URL}

Regards,
Jenkins"""
        }

        failure {
            mail to: "${EMAIL_RECIPIENT}",
                 subject: "❌ Build Failed: ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: """Hello Siddik,

❌ Jenkins job *${env.JOB_NAME}* failed.

- Build Number: ${env.BUILD_NUMBER}
- Build URL: ${env.BUILD_URL}

Please check the logs and fix the issue.

Regards,
Jenkins"""
        }
    }
}
