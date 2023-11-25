pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                script {
                    checkout scm
                }
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    sh 'npm install'
                }
            }
        }

        stage('Build and Test') {
            steps {
                script {
                    sh 'npm test'
                }
            }
        }

        stage('Start Application') {
            steps {
                script {
                    sh 'npm start'
                }
            }
        }
    }

    post {
        always {
        }
    }
}