pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }

        }
         stage('Check Docker') {
            steps {
                sh 'which docker'
                sh 'docker --version'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("todo_app_image")
                }
            }
        }

        stage('Run Container') {
            steps {
                script {
                    dockerImage.run("-p 3000:3000")
                }
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
    }
}
