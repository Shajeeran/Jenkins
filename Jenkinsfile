pipeline {
    agent any

    parameters {
        string(name: 'emailRecipient', defaultValue: 'shajeemano88@gmail.com', description: 'Email address to receive notifications')
        booleanParam(name: 'attachLog', defaultValue: true, description: 'Attach build log to email')
    }

    triggers {
        pollSCM(
            'H/5 * * * *'
        )
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building code using Maven...'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit tests with JUnit...'
                echo 'Running integration tests with Selenium...'
            }
            post {
                success {
                    emailext(
                        subject: 'Unit & Integration Tests - Success!',
                        body: 'Unit and Integration Tests passed successfully!',
                        to: "${params.emailRecipient}",
                        attachLog: "${params.attachLog}"
                    )
                }
                failure {
                    emailext(
                        subject: 'Unit & Integration Tests - Failed!',
                        body: 'Unit and Integration Tests failed! Check the logs for details.',
                        to: "${params.emailRecipient}",
                        attachLog: "${params.attachLog}"
                    )
                }
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code with SonarQube...'
            }
            post {
                success {
                    emailext(
                        subject: 'Code Analysis - Success!',
                        body: 'Code analysis completed successfully!',
                        to: "${params.emailRecipient}",
                        attachLog: "${params.attachLog}"
                    )
                }
                failure {
                    emailext(
                        subject: 'Code Analysis - Issues Found!',
                        body: 'Code analysis detected potential issues. Review the logs!',
                        to: "${params.emailRecipient}",
                        attachLog: "${params.attachLog}"
                    )
                }
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Scanning code for vulnerabilities with SAST tool...'
            }
            post {
                success {
                    emailext(
                        subject: 'Security Scan - No Vulnerabilities Found!',
                        body: 'Security scan completed successfully - No vulnerabilities detected!',
                        to: "${params.emailRecipient}",
                        attachLog: "${params.attachLog}"
                    )
                }
                failure {
                    emailext(
                        subject: 'Security Scan - Vulnerabilities Found!',
                        body: 'Security scan detected vulnerabilities! Address them before deployment.',
                        to: "${params.emailRecipient}",
                        attachLog: "${params.attachLog}"
                    )
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying application to Staging server (e.g., AWS EC2)...'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on Staging environment...'
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying application to Production server...'
            }
        }
    }
}
