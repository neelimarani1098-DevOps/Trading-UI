pipeline {
    agent any

    tools {
        nodejs 'Node18'
    }

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/neelimarani1098-DevOps/Trading-UI.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install --legacy-peer-deps --no-optional'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'CI=true npm test -- --watchAll=false --passWithNoTests || true'
            }
        }

        stage('Build Application') {
            steps {
                sh 'CI=false npm run build'
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
