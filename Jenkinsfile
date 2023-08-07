pipeline {
    agent any
    stages {
        stage('Install dependencies') {
            steps {
                echo "sh 'npm install'"
            }
        }

        stage('Build') {
            steps {
                echo "sh 'npm run build'"                
            }
        }
    }
}
