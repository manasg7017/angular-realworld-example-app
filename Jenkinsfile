pipeline {
    agent any

    environment {
        PATH = "${env.PATH}:/usr/bin"  // Ensure /usr/bin is in the PATH
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/manasg7017/angular-realworld-example-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'echo "Node version:" && node -v'
                sh 'echo "NPM version:" && npm -v'
                sh 'echo "PATH is: ${PATH}"'
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                sh 'ng build --prod'
            }
        }

        stage('Archive') {
            steps {
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
