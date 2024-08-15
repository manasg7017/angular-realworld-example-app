pipeline {
    agent {
        docker {
            image 'node:14' // Use a Node.js Docker image
            label 'node'
            args '-u root:root' // Optional: run as root if needed
        }
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the new repository
                git 'https://github.com/GabrielToth/Angular-V17-Template.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install npm dependencies
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                // Build the Angular application
                sh 'ng build --prod'
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
