pipeline {
    agent any
    stages {
        stage('Build Automated Tests Jar') {
            steps {
                bat "mvn clean package -DskipTests"
            }
        }
        stage('Execute Automated Tests Jar') {
             steps {
                bat "docker-compose up"
             }
        }
    }
}