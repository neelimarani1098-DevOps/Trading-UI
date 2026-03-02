pipeline {
    agent any

    tools {
        nodejs 'NodeJS-18'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/neelimarani1098-DevOps/Trading-UI.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test || echo "No tests configured"'
            }
        }

        stage('Build Application') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'build/**', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'CI Build Successful'
        }
        failure {
            echo 'Build Failed ❌'
        }
    }
}
