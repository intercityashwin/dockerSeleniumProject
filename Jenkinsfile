pipeline {
    agent any
    stages {
        stage('Build Automated Tests Jar') {
            steps {
                bat "mvn clean package -DskipTests"
            }
        }
        stage('Build Docker Image Image') {
            steps {
                bat "docker build -t=seleniumdocker ."
            }
        }
        stage('Execute Automated Tests Jar') {
             steps {
                bat "docker-compose up"
             }
        }
    }
}