pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Installing Firebase CLI...'
                sh 'npm install -g firebase-tools'
                sh 'firebase --version'
            }
        }

        stage('Testing') {
            steps {
                echo 'Deploying to TESTING environment...'
                sh 'firebase deploy --project my-webapp-testing --only hosting'
            }
        }

        stage('Staging') {
            steps {
                echo 'Deploying to STAGING environment...'
                sh 'firebase deploy --project my-webapp-staging --only hosting'
            }
        }

        stage('Production') {
            steps {
                input message: 'Deploy to PRODUCTION environment?'
                echo 'Deploying to PRODUCTION...'
                sh 'firebase deploy --project my-webapp-production --only hosting'
            }
        }
    }
}
