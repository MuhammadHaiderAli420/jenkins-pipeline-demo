pipeline {
    agent any

    environment {
        DEPENDENCY_CHECK_REPORT = 'dependency-check-report.html'
        RECIPIENT_EMAIL = 'm.alihaider0224420@gmail.com'
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building the application...'
                sh 'mvn clean package'
            }
        }

        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                sh 'mvn test'
            }
        }

        stage('Code Analysis') {
            steps {
                echo 'Performing code analysis with SonarQube...'
                withSonarQubeEnv('SonarQube') {
                    sh 'mvn sonar:sonar'
                }
            }
        }

        stage('Security Scan') {
            steps {
                echo 'Running security scan with OWASP Dependency-Check...'
                sh '''
                    dependency-check.sh --project "jenkins-pipeline-demo" --scan . --format HTML --out .
                '''
            }
        }

        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging environment...'
                // Replace with your deployment script/commands
                sh './deploy-to-staging.sh'
            }
        }

        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
                // Replace with your integration test commands
                sh './run-integration-tests.sh'
            }
        }

        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production environment...'
                // Replace with your deployment script/commands
                sh './deploy-to-production.sh'
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
