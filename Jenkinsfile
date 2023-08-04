pipeline {
    agent any

    environment {
        AWS_ACCESS_KEY_ID = credentials('aws-access-key-id')
        AWS_SECRET_ACCESS_KEY = credentials('aws-secret-access-key')
        AWS_REGION = 'us-east-1' // Replace with your desired AWS region
        S3_BUCKET_NAME = 'jenkins-s3-demo' // Replace with your S3 bucket name
    }

    stages {
        stage('Install dependencies') {
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
            steps {
                withAWS(region: env.AWS_REGION, credentials: 'aws-credentials') {
                    sh "aws s3 sync build/ s3://${env.S3_BUCKET_NAME}/ --delete"
                }
            }
        }
    }
}
