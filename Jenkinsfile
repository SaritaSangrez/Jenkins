pipeline {
    agent any
    stages {
        stage('Build') {
            // Logic: Always build, no condition needed here usually
            steps {
                echo 'Building..'
            }
        }

        stage('Test') {
            // Logic: Only run tests if we are on the 'main' branch
            when {
                branch 'main'
            }
            steps {
                echo 'Testing..'
            }
        }

        stage('Deploy') {
            // Logic: Only deploy if the 'Test' stage passed AND we are on 'main'
            when {
                allOf {
                    branch 'main'
                    // You could add other conditions here, like an environment variable
                }
            }
            steps {
                echo 'Deploying....'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution finished.'
        }
    }
}
