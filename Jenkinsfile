pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                // Add your build commands here
            }
        }

        stage('Test') {
            // This stage only runs if the branch name matches 'main'
            // Change 'main' to 'master' if that is what your branch is named
            when {
                branch 'main' 
            }
            steps {
                echo 'Testing..'
                // Add your test commands here
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying....'
                // Add your deployment commands here
            }
        }
    }

    // Post-build actions section
    post {
        always {
            echo 'The build process has finished. This message always appears.'
        }
        success {
            echo 'Build successful! This only runs if all stages pass.'
        }
        failure {
            echo 'Build failed. This only runs if a stage fails.'
        }
    }
}
