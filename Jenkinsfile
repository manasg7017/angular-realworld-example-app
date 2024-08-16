pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/manasg7017/angular-realworld-example-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
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
