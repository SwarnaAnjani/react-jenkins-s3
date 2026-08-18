pipeline {
    agent any

    environment {
        S3_BUCKET = 'swarna-react-jenkins-demo-2026'
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build React App') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Deploy to S3') {
            steps {
                sh 'aws s3 sync dist/ s3://$S3_BUCKET --delete'
            }
        }
    }

    post {
        success {
            echo 'React application deployed successfully to S3!'
        }

        failure {
            echo 'Deployment failed!'
        }
    }
}