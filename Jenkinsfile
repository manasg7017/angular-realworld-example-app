pipeline {
    agent any

    environment {
        NODE_HOME = tool name: 'NodeJS', type: 'nodejs' // Ensure NodeJS is configured
        PATH = "${NODE_HOME}/bin:${env.PATH}" // Update PATH to include Node.js
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the repository
                git branch: 'main', url: 'https://github.com/manasg7017/angular-realworld-example-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                script {
                    // Install npm dependencies
                    sh 'npm ci' // Use npm ci for faster installation
                }
            }
        }

        stage('Build') {
            steps {
                script {
                    // Build the Angular application
                    sh 'npm run build --prod'
                }
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
