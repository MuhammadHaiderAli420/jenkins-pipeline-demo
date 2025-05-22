pipeline {
    agent any

    environment {
        RECIPIENT_EMAIL = 'm.alihaider0224420@gmail.com'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Using Gradle as the build automation tool'
                bat 'echo gradle build simulated'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running tests (simulated)...'
                bat 'echo gradle test simulated'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Running static code analysis with simulated tool'
                bat 'echo Running SpotBugs or PMD (simulated)'
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan (simulated)'
                bat 'echo Simulating OWASP Dependency-Check'
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Simulating deployment to staging'
                bat 'echo Simulated deploy to staging server'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Simulating integration tests on staging'
                bat 'echo Simulated staging integration tests'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Simulating deployment to production'
                bat 'echo Simulated deploy to production server'
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
                 body: "The build succeeded. Check it here: ${env.BUILD_URL}"
        }
        failure {
            mail to: "${env.RECIPIENT_EMAIL}",
                 subject: "FAILURE: Jenkins Build ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                 body: "The build failed. Check the details: ${env.BUILD_URL}"
        }
    }
}
