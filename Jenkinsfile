pipeline {
    agent any
    environment {
        STAGING_BUCKET = 'my-staging-bucket'
        PRODUCTION_BUCKET = 'my-production-bucket'
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Install Dependencies') {
            steps {
                script {
                    try {
                        sh 'npm install'
                    } catch (Exception e) {
                        echo "Error during npm install: ${e}"
                        error "Stopping pipeline due to npm install failure."
                    }
                }
            }
        }
        stage('Build') {
            when {
                expression { fileExists('package.json') }
            }
            steps {
                sh 'npm run build'
            }
        }
        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                sh "aws s3 sync build/ s3://${PRODUCTION_BUCKET}/"
            }
        }
        stage('Deploy to Staging') {
            when {
                branch 'develop'
            }
            steps {
                sh "aws s3 sync build/ s3://${STAGING_BUCKET}/"
            }
        }
    }
    post {
        always {
            echo "Pipeline completed for branch: ${env.BRANCH_NAME}"
        }
        failure {
            echo "Pipeline failed for branch: ${env.BRANCH_NAME}"
        }
    }
}

