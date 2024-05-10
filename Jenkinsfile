pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                // Build code using Maven
                sh 'mvn clean package'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                // Run unit tests using JUnit
                sh 'mvn test'
                
                // Run integration tests using a framework like Selenium
                sh 'selenium-runner'
            }
        }

        stage('Code Analysis') {
            steps {
                // Integrate a code analysis tool like SonarQube
                withSonarQubeEnv('SonarQube') {
                    sh 'sonar-scanner'
                }
            }
        }

        stage('Security Scan') {
            steps {
                // Perform security scan using a tool like OWASP ZAP
                sh 'owasp-zap -cmd'
            }
        }

        stage('Deploy to Staging') {
            steps {
                // Deploy application to staging server, e.g., AWS EC2
                sh 'aws deploy staging'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                // Run integration tests on staging environment
                sh 'selenium-runner-staging'
            }
        }

        stage('Deploy to Production') {
            steps {
                // Deploy application to production server, e.g., AWS EC2
                sh 'aws deploy production'
            }
        }
    }

    post {
        success {
            // Send notification email on successful completion
             emailext body: "Pipeline succeeded", subject: "Pipeline Success", to: "shajeemano88@gmail.com"
        }
        failure {
            // Send notification email on failure with logs attached
            emailext body: "Pipeline failed", subject: "Pipeline Failure", to: "shajeemano88@gmail.com", attachLog: true
        }
    }
}
