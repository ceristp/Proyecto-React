pipeline {
     environment {
        DOCKERHUB_USERNAME = 'ceristp00'
        DOCKERHUB_PASSWORD = credentials('DockerHub_credentials')
        DOCKERHUB_REPO = 'ceristp00/Proyecto-React'
    }

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
    

        stage('Dockerize') {
            steps {
                script {
                    // Build
                    sh "docker build -t $DOCKERHUB_REPO:latest ."

                    // Log
                    sh "docker login -u $DOCKERHUB_USERNAME -p $DOCKERHUB_PASSWORD"

                    // Push
                    sh "docker push $DOCKERHUB_REPO:latest"
                }
            }
        }
    }
    post {
        always {
        }
    }
}