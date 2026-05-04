pipeline {
    agent any

    environment {
        DIRECTORY_PATH = "/usr/src/app/nodejs-app"
        STAGING_ENVIRONMENT = "Staging_Server"
        PRODUCTION_ENVIRONMENT = "Production_Server"
    }

    stages {

        stage('Build') {
            steps {
                echo "Fetching source code from: ${env.DIRECTORY_PATH}"
                echo "Installing dependencies using npm..."
                echo "Building application (npm run build)..."
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo "Running unit tests using Jest..."
                echo "Running integration tests using Supertest..."
            }
        }

        stage('Code Analysis') {
            steps {
                echo "Performing code quality analysis using ESLint..."
            }
        }

        stage('Security Scan') {
            steps {
                echo "Running security scan using npm audit / Snyk..."
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo "Deploying application to ${env.STAGING_ENVIRONMENT} AWS EC2 server..."
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo "Running API tests on staging using Postman..."
            }
        }

        stage('Deploy to Production') {
            steps {
                echo "Deploying application to ${env.PRODUCTION_ENVIRONMENT}..."
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