pipeline {
    agent any
    stages {
        stage('Build and Package Automated Tests as executable Jar') {
            steps {
                bat "mvn clean package -DskipTests"
            }
        }
        stage('Spin up Selenium Grid Infrastructure') {
             steps {
                bat "docker-compose up -d hub chrome firefox"
             }
        }
        stage('Execute the Test Suite') {
             steps {
                 bat "docker-compose up tests"
             }
        }
        post('Spin down Selenium Grid Infrastructure') {
             always {
                 archiveArtifacts artifacts : 'output/**'
                 bat "docker-compose down"
             }
        }
    }
}