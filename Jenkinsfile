pipeline {
    agent any

    parameters {
        choice(
            name: 'ENVIRONMENT',
            choices: ['dev', 'staging', 'prod'],
            description: 'Select the deployment environment'
        )
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/<username>/online-exam-parameterized.git'
            }
        }

        stage('Build') {
            steps {
                bat 'python -m py_compile app.py'
                echo "Build successful for ${params.ENVIRONMENT}"
            }
        }

        stage('Test') {
            steps {
                bat 'python app.py'
            }
        }

        stage('Deploy') {
            steps {
                echo "Deploying Online Examination System to ${params.ENVIRONMENT}"
            }
        }
    }
}
