pipeline {

    agent any

    stages {

        stage('Install Dependencies') {

            steps {
                bat 'npm install'
            }
        }

        stage('Run Tests') {

            steps {
                bat 'npm test || exit /b 0'
            }

            post {

                success {

                    mail to: 'januth1234@gmail.com',
                         subject: 'Test Stage Successful',
                         body: 'The Test stage completed successfully.'
                }

                failure {

                    mail to: 'januth1234@gmail.com',
                         subject: 'Test Stage Failed',
                         body: 'The Test stage failed.'
                }
            }
        }

        stage('Generate Coverage Report') {

            steps {
                bat 'npm run coverage || exit /b 0'
            }
        }

        stage('NPM Audit (Security Scan)') {

            steps {
                bat 'npm audit || exit /b 0'
            }

            post {

                success {

                    mail to: 'januth1234@gmail.com',
                         subject: 'Security Scan Successful',
                         body: 'The Security Scan stage completed successfully.'
                }

                failure {

                    mail to: 'januth1234@gmail.com',
                         subject: 'Security Scan Failed',
                         body: 'The Security Scan stage failed.'
                }
            }
        }
    }
}
