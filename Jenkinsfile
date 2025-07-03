pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'chmod +x gradlew'
                sh './gradlew build'
            }
        }
        stage('Run') {
            steps {
                sh './gradlew bootRun &'
                sh 'sleep 10'
            }
        }
        stage('Test Endpoint') {
            steps {
                sh 'curl "http://localhost:8081/sum?a=1&b=2"'
            }
        }
    }
}
