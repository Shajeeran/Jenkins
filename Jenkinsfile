pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                // Compile and package code using Maven
                sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                // Run unit tests
                sh 'mvn test'
                // Run integration tests
                sh 'mvn integration-test'
            }
        }
        stage('Code Analysis') {
            steps {
                // Analyze code using SonarQube
                sh 'sonar-scanner'
            }
        }
        stage('Security Scan') {
            steps {
                // Perform security scan using OWASP Dependency-Check
                sh 'dependency-check --project <project-name> --scan <project-directory>'
            }
        }
        stage('Deploy to Staging') {
            steps {
                // Deploy application to staging server (AWS EC2)
                sh 'aws ec2 deploy <staging-server>'
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                // Run integration tests on staging environment
                sh 'mvn integration-test'
            }
        }
        stage('Deploy to Production') {
            steps {
                // Deploy application to production server (AWS EC2)
                sh 'aws ec2 deploy <production-server>'
            }
        }
    }
    
    post {
        // Send notification email with status and logs for test and security scan stages
        success {
            emailext subject: "Pipeline Success",
                      body: "Pipeline ran successfully.",
                      to: "your-email@example.com"
        }
        failure {
            emailext subject: "Pipeline Failure",
                      body: "Pipeline failed. Check logs for details.",
                      to: "your-email@example.com"
        }
    }
}
