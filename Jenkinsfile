pipeline {
    agent any
    stages {
        stage('Stage 1 Echo') {
                steps {
                    echo "Hello World !!"
                }
            }
        stage('Build and Package Automated Tests as executable Jar') {
            steps {
                sh "mvn clean package -DskipTests"
            }
        }
        stage('Build Docker File') {
             steps {
                sh "docker build -t=seleniumdocker ."
             }
        }
        stage('Spin up Selenium Grid Infrastructure') {
             steps {
                sh "docker-compose up -d hub chrome firefox"
             }
        }
        stage('Execute the Test Suite') {
             steps {
                 sh "docker-compose up tests"
             }
        }
    }
    post{
          always {
                    archiveArtifacts artifacts : 'output/**'
                    sh "docker-compose down"
                 }
    }
}