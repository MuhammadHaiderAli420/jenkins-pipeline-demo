pipeline {
    agent any

    environment {
        RECIPIENT_EMAIL = 'your-email@example.com'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                bat 'mvn clean package'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                bat 'mvn test'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis with SonarQube (simulated)...'
                bat 'echo Simulated SonarQube analysis'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Running security scan (simulated)...'
                bat 'echo Simulated OWASP scan'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging (simulated)...'
                bat 'echo Simulated deploy to staging'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging (simulated)...'
                bat 'echo Simulated integration tests on staging'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production (simulated)...'
                bat 'echo Simulated deploy to production'
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed.'
        }
        success {
            mail to: "${env.RECIPIENT_EMAIL}",
                 subject: "SUCCESS: Jenkins Build ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "Good news! The build succeeded. Check it here: ${env.BUILD_URL}"
        }
        failure {
            mail to: "${env.RECIPIENT_EMAIL}",
                 subject: "FAILURE: Jenkins Build ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "Unfortunately, the build failed. Check the details: ${env.BUILD_URL}"
        }
    }
}
