pipeline {
    agent any

    // 1. Parameters Section: Defines the user input fields
    parameters {
        string(name: 'DEPLOY_ENV', defaultValue: 'Staging', description: 'Enter the Target Environment')
        choice(name: 'LOG_LEVEL', choices: ['INFO', 'DEBUG', 'ERROR'], description: 'Select the logging level')
        booleanParam(name: 'EXECUTE_TESTS', defaultValue: true, description: 'Check to run the Test stage')
    }

    tools {
        maven 'Maven3' 
    }

    environment {
        APP_VERSION = '2.4.0'
    }

    stages {
        stage('Initialize') {
            steps {
                echo "Starting build for Version: ${env.APP_VERSION}"
                echo "Target Environment: ${params.DEPLOY_ENV}"
                echo "Log Level set to: ${params.LOG_LEVEL}"
                bat 'mvn -version'
            }
        }

        stage('Build') {
            steps {
                echo 'Maven build step initiated...'
            }
        }

        stage('Test') {
            // 2. Conditional Logic: Only runs if the boolean parameter is checked
            when {
                expression { return params.EXECUTE_TESTS == true }
            }
            steps {
                echo "Executing tests as requested by user..."
                echo 'Testing..'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying to ${params.DEPLOY_ENV} environment."
                echo 'Deploying....'
            }
        }
    }

    post {
        always {
            echo "Pipeline finished for version ${env.APP_VERSION}."
        }
    }
}
