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
        success {
            script {
                def emailBody = """\
                Good news! The build ${env.BUILD_NUMBER} of job ${env.JOB_NAME} has completed successfully.
                """
                sh """
                echo '${emailBody}' | mail -s "SUCCESS: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}" namnaigamma2chai@gmail.com
                """
            }
        }
        failure {
            script {
                def emailBody = """\
                Oops! The build ${env.BUILD_NUMBER} of job ${env.JOB_NAME} has failed. Please check the logs.
                """
                sh """
                echo '${emailBody}' | mail -s "FAILURE: ${env.JOB_NAME} - Build #${env.BUILD_NUMBER}" namnaigamma2chai@gmail.com
                """
            }
        }
    }
}
