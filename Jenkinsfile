pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Code Analysis') {
            steps {
                // Run a code analysis tool e.g., SonarQube
            }
        }
        stage('Security Scan') {
            steps {
                // Run a security scanning tool e.g., SonarQube
            }
        }
        stage('Deploy to Staging') {
            steps {
                // Deploy to staging server
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                // Run integration tests on staging environment
            }
        }
        stage('Deploy to Production') {
            steps {
                // Deploy to production server
            }
        }
    }
    post {
        always {
            // Send notification emails at the end of each stage
            emailext body: 'The ${STAGE_NAME} stage completed with status: ${currentBuild.currentResult}', subject: 'Pipeline Notification: ${STAGE_NAME}', to: 'shajeemano88@mail.com'
        }
        failure {
            // Send notification emails on failure
            emailext body: 'The ${STAGE_NAME} stage failed with status: ${currentBuild.currentResult}', subject: 'Pipeline Notification: ${STAGE_NAME}', to: 'shajeemano88@gmail.com'
        }
    }
}
