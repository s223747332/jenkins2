pipeline {
    agent any

    environment {
        LOG_FILE = "build_output.log" // defining log file
    }

    stages {
        stage('Build') {
            steps {
                script {
                    sh """
                        echo 'Building...' | tee ${LOG_FILE} 
                        # Simulate build step and log output to the file
                        echo 'Fetching source code...' >> ${LOG_FILE}
                        echo 'Compiling code...' >> ${LOG_FILE}
                    """
                }
            }
        }
        stage('Unit and Integration Tests') {
            steps {
                script {
                    sh """
                        echo 'Running unit and integration tests...' | tee -a ${LOG_FILE}
                        # Simulate tests
                        echo 'Unit tests passed...' >> ${LOG_FILE}
                        echo 'Integration tests passed...' >> ${LOG_FILE}
                    """
                }
            }
        }
        stage('Code Analysis') {
            steps {
                script {
                    sh """
                        echo 'Analyzing code...' | tee -a ${LOG_FILE}
                        # Simulate code analysis
                        echo 'Code analysis completed...' >> ${LOG_FILE}
                    """
                }
            }
        }
        stage('Security Scan') {
            steps {
                script {
                    sh """
                        echo 'Running security scan...' | tee -a ${LOG_FILE}
                        # Simulate security scan
                        echo 'Security scan completed...' >> ${LOG_FILE}
                    """
                }
            }
        }
        stage('Deploy to Staging') {
            steps {
                script {
                    sh """
                        echo 'Deploying to staging...' | tee -a ${LOG_FILE}
                        # Simulate deployment to staging
                        echo 'Deployment to staging successful...' >> ${LOG_FILE}
                    """
                }
            }
        }
        stage('Integration Tests on Staging') {
            steps {
                script {
                    sh """
                        echo 'Running integration tests on staging...' | tee -a ${LOG_FILE}
                        # Simulate staging tests
                        echo 'Staging integration tests passed...' >> ${LOG_FILE}
                    """
                }
            }
        }
        stage('Deploy to Production') {
            steps {
                script {
                    sh """
                        echo 'Deploying to production...' | tee -a ${LOG_FILE}
                        # Simulate production deployment
                        echo 'Deployment to production completed...' >> ${LOG_FILE}
                    """
                }
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
                        body: body,
                        attachmentsPattern: "${env.LOG_FILE}", // Attach the  log file
                        attachLog: true // attach Jenkins console log
                        // added the log file attachment
                    )
                    echo "Email sent with log file attached."
                } catch (Exception e) {
                    echo "Failed to send email: ${e}"
                }
            }
        }
    }
}
