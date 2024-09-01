pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                // Add your build commands here (e.g., mvn clean install)
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                echo 'Running unit and integration tests...'
                // Add your test commands here
            }
        }
        stage('Code Analysis') {
            steps {
                echo 'Analyzing code...'
                // Add your code analysis commands here
            }
        }
        stage('Security Scan') {
            steps {
                echo 'Running security scan...'
                // Add your security scan commands here
            }
        }
        stage('Deploy to Staging') {
            steps {
                echo 'Deploying to staging...'
                // Add your staging deployment commands here
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                echo 'Running integration tests on staging...'
                // Add your staging integration tests commands here
            }
        }
        stage('Deploy to Production') {
            steps {
                echo 'Deploying to production...'
                // Add your production deployment commands here
            }
        }
    }

    post {
        always {
            script {
                echo "Sending email notification..."
                def subject = currentBuild.result == 'SUCCESS' ? 
                              "SUCCESS: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}" :
                              "FAILURE: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}"
                
                def body = currentBuild.result == 'SUCCESS' ?
                           "Good news! The build ${env.BUILD_NUMBER} of job ${env.JOB_NAME} has completed successfully." :
                           "Oops! The build ${env.BUILD_NUMBER} of job ${env.JOB_NAME} has failed. Please check the logs."
                
                try {
                    emailext(
                        to: 'namnaigamma2chai0@gmail.com',
                        subject: subject,
                        body: body
                    )
                    echo "Email sent."
                } catch (Exception e) {
                    echo "Failed to send email: ${e}"
                }
            }
        }
    }
}
