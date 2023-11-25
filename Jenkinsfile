pipeline {
    agent any

    stages {
        stage('Clonar Repositorio') {
            steps {
                // Paso para clonar el repositorio desde GitHub
                git 'https://github.com/ceristp/Proyecto-React'
            }
        }

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
                    // Paso para ejecutar pruebas automatizadas
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