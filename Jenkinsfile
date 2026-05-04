pipeline {
    agent any

    environment {
        DIRECTORY_PATH = "/usr/src/app/my-code"
        TESTING_ENVIRONMENT = "Staging_Server"
        PRODUCTION_ENVIRONMENT = "Yuen Yi Cheng"
    }

    stages {

        stage('Build') {
            steps {
                echo "Fetching source code from: ${env.DIRECTORY_PATH}"
                echo "Compiling the code and generating artefacts..."
            }
        }

        stage('Test') {
            steps {
                echo "Running Unit Tests..."
                echo "Running Integration Tests..."
            }
        }

        stage('Code Quality Check') {
            steps {
                echo "Performing code quality analysis..."
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying to testing environment: ${env.TESTING_ENVIRONMENT}"
            }
        }

        stage('Approval') {
            steps {
                script {
                    input message: "Approve deployment to Production?", ok: "Approve"
                }
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Deploying to production environment: ${env.PRODUCTION_ENVIRONMENT}"
            }
        }
    }

    post {
        success {
            echo "Pipeline completed successfully!"
        }
        failure {
            echo "Pipeline failed. Please check logs."
        }
    }
}