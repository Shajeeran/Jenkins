pipeline {
    agent any

    environment {
        DIRECTORY_PATH = 'C:\\ProgramData\\Jenkins\\.jenkins\\jobs\\New Jenkins pipeline ver2\\builds\\1'  
        TESTING_ENVIRONMENT = "testing environment"
        PRODUCTION_ENVIRONMENT = "shajeeran's production env"  
    }

    stages {
        stage('Build') {
            steps {
                script {
                    echo 'Fetching source code from the directory path specified by the environment variable.'
                    echo 'Compiling the code and generating any necessary artifacts.'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    echo 'Running unit tests...'
                    echo 'Running integration tests...'
                }
            }
        }
        stage('Code Quality Check') {
            steps {
                script {
                    echo 'Checking the quality of the code.'
                }
            }
        }
        stage('Deploy') {
            steps {
                script {
                    echo "Deploying the application to ${TESTING_ENVIRONMENT} specified by the environment variable."
                }
            }
        }
        stage('Approval') {
            steps {
                script {
                    echo 'Waiting for manual approval...'
                    sleep 10
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                script {
                    echo "Deploying the code to ${PRODUCTION_ENVIRONMENT} environment."
                }
            }
        }
    }
}
