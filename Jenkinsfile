pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Check out the code from the specified Git repository
                git 'https://github.com/IBM/template-node-angular.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install the necessary dependencies
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                // Build the Angular project in production mode
                sh 'npx ng build --prod' // Use npx to ensure Angular CLI is available
            }
        }

        stage('Archive') {
            steps {
                // Archive the build artifacts
                archiveArtifacts artifacts: 'dist/**', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed.'
        }
    }
}
