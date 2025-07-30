pipeline {
    agent any

    environment {
        FIREBASE_CLI = './node_modules/.bin/firebase'         // Local Firebase CLI path
        FIREBASE_TOKEN = credentials('FIREBASE_TOKEN')        // Secure token from Jenkins credentials
    }

    stages {
        stage('Build') {
            steps {
                echo 'Installing Firebase CLI locally...'
                sh 'npm install firebase-tools'
                sh '${FIREBASE_CLI} --version'
            }
        }

        stage('Testing') {
            steps {
                echo 'Deploying to TESTING environment...'
                sh '${FIREBASE_CLI} deploy --project my-webapp-testing --only hosting --token="$FIREBASE_TOKEN"'
            }
        }

        stage('Staging') {
            steps {
                echo 'Deploying to STAGING environment...'
                sh '${FIREBASE_CLI} deploy --project my-webapp-staging --only hosting --token="$FIREBASE_TOKEN"'
            }
        }

        stage('Production') {
            steps {
                input message: 'Deploy to PRODUCTION environment?'
                echo 'Deploying to PRODUCTION...'
                sh '${FIREBASE_CLI} deploy --project my-webapp-production --only hosting --token="$FIREBASE_TOKEN"'
            }
        }
    }
}
