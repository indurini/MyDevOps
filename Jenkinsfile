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
                sh 'firebase deploy --project your-test-project-id --only hosting'
            }
        }

        stage('Staging') {
            steps {
                echo 'Deploying to STAGING environment...'
                sh 'firebase deploy --project your-staging-project-id --only hosting'
            }
        }

        stage('Production') {
            steps {
                input message: 'Deploy to PRODUCTION environment?'
                echo 'Deploying to PRODUCTION...'
                sh 'firebase deploy --project your-production-project-id --only hosting'
            }
        }
    }
}
