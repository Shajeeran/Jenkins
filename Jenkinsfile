pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo "Performing build using Maven"
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit tests using JUnit"
                echo "Running integration tests using TestNG"
            }
            post {
                success {
                    emailext (
                        to: 'your_email@example.com', // Specify the recipient email address
                        subject: 'Unit and Integration Tests Success',
                        body: 'Unit and Integration tests have passed successfully.',
                        attachLog: true
                    )
                }
                failure {
                    emailext (
                        to: 'your_email@example.com', // Specify the recipient email address
                        subject: 'Unit and Integration Tests Failed',
                        body: 'Unit and Integration tests have failed. Please check the logs for details.',
                        attachLog: true
                    )
                }
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
            post {
                success {
                    emailext (
                        to: 'your_email@example.com', // Specify the recipient email address
                        subject: 'Security Scan Success',
                        body: 'Security scan has passed successfully.',
                        attachLog: true
                    )
                }
                failure {
                    emailext (
                        to: 'your_email@example.com', // Specify the recipient email address
                        subject: 'Security Scan Failed',
                        body: 'Security scan has failed. Please check the logs for details.',
                        attachLog: true
                    )
                }
            }
        }
        // Define other stages as per your requirements
    }
}
