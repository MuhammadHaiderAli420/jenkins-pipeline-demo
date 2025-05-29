pipeline {
    agent any

    environment {
        RECIPIENT_EMAIL = 'm.alihaider0224420@gmail.com'
        LOG_FILE = 'build_log.txt'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Using Gradle as the build automation tool'
                bat "echo gradle build simulated >> ${env.LOG_FILE}"
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running tests (simulated)...'
                bat "echo gradle test simulated >> ${env.LOG_FILE}"
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Running static code analysis with simulated tool'
                bat "echo Running SpotBugs or PMD (simulated) >> ${env.LOG_FILE}"
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Performing security scan (simulated)'
                bat "echo Simulating OWASP Dependency-Check >> ${env.LOG_FILE}"
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Simulating deployment to staging'
                bat "echo Simulated deploy to staging server >> ${env.LOG_FILE}"
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Simulating integration tests on staging'
                bat "echo Simulated staging integration tests >> ${env.LOG_FILE}"
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Simulating deployment to production'
                bat "echo Simulated deploy to production server >> ${env.LOG_FILE}"
            }
        }
    }

    post {
        always {
            echo 'Pipeline execution completed.'
        }
        success {
            emailext(
                to: "${env.RECIPIENT_EMAIL}",
                subject: "SUCCESS: Jenkins Build ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "The build succeeded. Log attached.\n\nCheck the build: ${env.BUILD_URL}",
                attachmentsPattern: "${env.LOG_FILE}"
            )
        }
        failure {
            emailext(
                to: "${env.RECIPIENT_EMAIL}",
                subject: "FAILURE: Jenkins Build ${env.JOB_NAME} #${env.BUILD_NUMBER}",
                body: "The build failed. Log attached.\n\nCheck the details: ${env.BUILD_URL}",
                attachmentsPattern: "${env.LOG_FILE}"
            )
        }
    }
}
