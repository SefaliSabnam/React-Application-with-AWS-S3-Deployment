pipeline {
    agent any
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
        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }
        stage('Deploy to S3') {
            when {
                branch 'main'
            }
            steps {
                sh 'aws s3 sync build/ s3://my-react-app-bucket/'
            }
        }
        stage('Deploy to Staging S3') {
            when {
                branch 'develop'
            }
            steps {
                sh 'aws s3 sync build/ s3://my-react-app-staging-bucket/'
            }
        }
    }
}
