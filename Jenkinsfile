pipeline {
    agent any
    
    // Defining global variables accessible by all stages
    environment {
        APP_VERSION = '2.4.0'
        SCAN_LEVEL = 'High'
    }

    stages {
        stage('Build') {
            steps {
                // Using the environment variable with the $ sign
                echo "Building Application Version: ${env.APP_VERSION}"
                echo "Security Scan Level: ${env.SCAN_LEVEL}"
            }
        }

        stage('Test') {
            when {
                branch 'main' 
            }
            steps {
                echo "Running tests for version ${env.APP_VERSION}..."
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying version ${env.APP_VERSION} to Production."
            }
        }
    }

    post {
        always {
            echo "Pipeline for version ${env.APP_VERSION} has completed."
        }
    }
}
