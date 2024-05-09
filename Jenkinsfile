pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Performing build using  Maven"
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit tests using JUnit"
                echo "Running integration tests using TestNG"
            }
        }
        stage('Code Analysis') {
            steps {
                echo "Performing code analysis using SonarQube"
            }
        }
        stage('Security Scan') {
            steps {
                echo "Performing security scan using OWASP ZAP"
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo "Deploying to staging using AWS EC2"
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo "Running integration tests on staging using Selenium"
            }
        }
        stage('Deploy to Production') {
            steps {
                echo "Deploying to production using AWS EC2"
            }
        }
    }
    post {
        always {
            echo "Sending email notifications"
            emailext (
                to: 'shajeemano88@gmail.com',
                subject: 'Pipeline status: ${currentBuild.currentResult}',
                body: "Pipeline status: ${currentBuild.currentResult}\n\nLogs:\n${currentBuild.rawBuild.log}",
                attachLog: true
            )
        }
    }
}
