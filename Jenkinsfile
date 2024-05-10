pipeline {
  agent any

  triggers {
    pollSCM( // Trigger build on new commit
      'H/5 * * * *', // Schedule: Every 5 minutes
    )
  }

  stages {
    stage('Build') {
      steps {
        echo 'Building code using Maven...' // Update with your build tool (e.g., Maven, Gradle)
      }
    }
    stage('Unit and Integration Tests') {
      steps {
        echo 'Running unit tests with JUnit...' // Replace with your test framework (e.g., JUnit, TestNG)
        echo 'Running integration tests with Selenium...' // Replace with your integration testing tool (e.g., Selenium)
      }
      post { // Configure post-actions for this stage
        success {
          // Update with Email-Ext Plugin syntax (if installed)
          emailext( // Assuming Email-Ext Plugin is used
            subject: 'Unit & Integration Tests - Success!',
            body: 'Unit and Integration Tests passed successfully!',
            recipient: 'youremail@example.com',
            attachLog: true
          )
          // Alternative option (if Email-Ext Plugin is not installed)
          // script {
          //   // Use Jenkins built-in email notification (limited features)
          //   mail(
          //     to: 'youremail@example.com',
          //     subject: 'Unit & Integration Tests - Success!',
          //     body: 'Unit and Integration Tests passed successfully!',
          //   )
          // }
        }
        failure {
          // Update with Email-Ext Plugin syntax (if installed)
          emailext( // Assuming Email-Ext Plugin is used
            subject: 'Unit & Integration Tests - Failed!',
            body: 'Unit and Integration Tests failed! Check the logs for details.',
            recipient: 'youremail@example.com',
            attachLog: true
          )
          // Alternative option (if Email-Ext Plugin is not installed)
          // script {
          //   // Use Jenkins built-in email notification (limited features)
          //   mail(
          //     to: 'youremail@example.com',
          //     subject: 'Unit & Integration Tests - Failed!',
          //     body: 'Unit and Integration Tests failed! Check the logs for details.',
          //   )
          // }
        }
      }
    }
    stage('Code Analysis') {
      steps {
        echo 'Analyzing code with SonarQube...' // Replace with your code analysis tool (e.g., SonarQube)
      }
      post { // Configure post-actions for this stage
        success {
          // Update with Email-Ext Plugin syntax (if installed)
          emailext( // Assuming Email-Ext Plugin is used
            subject: 'Code Analysis - Success!',
            body: 'Code analysis completed successfully!',
            recipient: 'youremail@example.com',
            attachLog: true
          )
          // Alternative option (if Email-Ext Plugin is not installed)
          // script {
          //   // Use Jenkins built-in email notification (limited features)
          //   mail(
          //     to: 'youremail@example.com',
          //     subject: 'Code Analysis - Success!',
          //     body: 'Code analysis completed successfully!',
          //   )
          // }
        }
        failure {
          // Update with Email-Ext Plugin syntax (if installed)
          emailext( // Assuming Email-Ext Plugin is used
            subject: 'Code Analysis - Issues Found!',
            body: 'Code analysis detected potential issues. Review the logs!',
            recipient: 'youremail@example.com',
          )
          // Alternative option (if Email-Ext Plugin is not installed)
          // script {
          //   // Use Jenkins built-in email notification (limited features)
          //   mail(
          //     to: 'youremail@example.com',
          //     subject: 'Code Analysis - Issues Found!',
          //     body: 'Code analysis detected potential issues. Review the logs!',
          //   )
          // }
        }
      }
    }
    stage('Security Scan') {
      steps {
        echo 'Scanning code for vulnerabilities with SAST tool...' // Replace with your security scanning tool (e.g., SAST scanner)
      }
      post { // Configure post-actions for this stage
        success {
          // Update with Email-Ext Plugin syntax (if installed)
          emailext( // Assuming Email-Ext Plugin is used
            subject: 'Security Scan - No Vulnerabilities Found!',
            body: 'Security scan completed successfully - No vulnerabilities detected!',
            recipient: 'youremail@example.com',
          )
          // Alternative option (if Email-Ext Plugin is not installed)
          // script {
          //   // Use Jenkins built-in email notification (limited features)
          //   mail(
          //     to: 'youremail@example.com',
          //     subject: 'Security Scan - No Vulnerabilities Found!',
          //     body: 'Security scan completed successfully - No vulnerabilities detected!',
          //   )
          // }
        }
        failure {
          // Update with Email-Ext Plugin syntax (if installed)
          emailext( // Assuming Email-Ext Plugin is used
            subject: 'Security Scan - Vulnerabilities Found!',
            body: 'Security scan detected vulnerabilities! Address them before deployment.',
            recipient: 'youremail@example.com',
            attachLog: true
          )
          // Alternative option (if Email-Ext Plugin is not installed)
          // script {
          //   // Use Jenkins built-in email notification (limited features)
          //   mail(
          //     to: 'youremail@example.com',
          //     subject: 'Security Scan - Vulnerabilities Found!',
          //     body: 'Security scan detected vulnerabilities! Address them before deployment.',
          //   )
          // }
        }
      }
      stage('Deploy to Staging') {
        steps {
          echo 'Deploying application to Staging server (e.g., AWS EC2)...' // Replace with your deployment tool (e.g., AWS CLI)
        }
      }
      stage('Integration Tests on Staging') {
        steps {
          echo 'Running integration tests on Staging environment...'  // Adapt the testing tool for the environment
        }
      }
      stage('Deploy to Production') {
        steps {
          echo 'Deploying application to Production server...' // Added closing quotation mark here
        }
      }
    }
  }
