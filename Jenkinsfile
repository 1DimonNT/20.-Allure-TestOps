pipeline {
    agent any

    environment {
        ALLURE_ENDPOINT = 'https://allure.autotests.cloud/'
        ALLURE_TOKEN = '23b4a183-838b-482d-a376-8294dd4bd586'
        ALLURE_PROJECT_ID = '5200'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Setup Python') {
            steps {
                bat 'python -m venv venv'
                bat 'venv\\Scripts\\activate && pip install -r requirements.txt'
            }
        }

        stage('Run tests') {
            steps {
                bat 'venv\\Scripts\\activate && pytest --alluredir=allure-results'
            }
        }

        stage('Upload to Allure TestOps') {
            steps {
                bat 'venv\\Scripts\\activate && allurectl upload allure-results'
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}