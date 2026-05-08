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

                always {

                    emailext(
                        to: 'YOUR_EMAIL@gmail.com',
                        subject: 'Test Stage Result',
                        body: 'The Test stage has completed.',
                        attachLog: true
                    )
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

                always {

                    emailext(
                        to: 'YOUR_EMAIL@gmail.com',
                        subject: 'Security Scan Result',
                        body: 'The Security Scan stage has completed.',
                        attachLog: true
                    )
                }
            }
        }
    }
}
