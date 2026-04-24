pipeline {
    agent any

    // 1. Tools Section: Matches the name in Manage Jenkins -> Tools
    tools {
        maven 'Maven3' 
    }

    // 2. Environment Variables: Accessible across all stages
    environment {
        APP_VERSION = '2.4.0'
        SCAN_LEVEL = 'High'
    }

    stages {
        stage('Initialize') {
            steps {
                echo "Initializing Pipeline for Version: ${env.APP_VERSION}"
                // Verify Maven is correctly linked in Jenkins
                bat 'mvn -version'
            }
        }

        stage('Build') {
            steps {
                echo "Building version ${env.APP_VERSION}..."
                echo 'Maven build step initiated.'
                // In a real project, you would use: bat 'mvn clean install'
            }
        }

        stage('Test') {
            // 3. Conditionals: Only runs if the branch is 'main' (or 'master')
            // Change 'main' to 'master' if that is your branch name
            when {
                branch 'main'
            }
            steps {
                echo "Running security tests at level: ${env.SCAN_LEVEL}"
                echo 'Testing..'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying version ${env.APP_VERSION} to the server..."
                echo 'Deploying....'
            }
        }
    }

    // 4. Post-Build Actions: Runs after the stages finish
    post {
        always {
            echo "Execution of version ${env.APP_VERSION} is complete."
        }
        success {
            echo 'Build Status: SUCCESS - All stages passed!'
        }
        failure {
            echo 'Build Status: FAILURE - Please check the logs.'
        }
    }
}
