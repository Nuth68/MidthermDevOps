pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/Nuth68/MidthermDevOps.git'
            }
        }

        stage('Build') {
            steps {
                sh 'chmod +x ./mvnw && ./mvnw clean package'
            }
        }

        stage('Deploy using Ansible') {
            steps {
                sh '''
                ansible-playbook deploy.yml
                '''
            }
        }
    }

    post {

        success {
            emailext (
                to: 'pravevinuth888@gmail.com',
                subject: "SUCCESS: Midterm-2026-your_name",
                body: "Build successful!\nWebsite: http://143.198.91.135/midterm/nuth"
            )
        }

        failure {
            emailext (
                to: 'pravevinuth888@gmail.com',
                subject: "FAILED: Midterm-2026-your_name",
                body: "Build failed! Check Jenkins logs.\nBuild number: ${BUILD_NUMBER}"
            )
        }
    }
}