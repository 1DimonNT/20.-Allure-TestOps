pipeline {
    agent any

    environment {
        ALLURE_ENDPOINT = 'https://allure.autotests.cloud/'
        ALLURE_TOKEN = '23b4a183-838b-482d-a376-8294dd4bd586'
        ALLURE_PROJECT_ID = '5200'
    }

    stages {
        stage('Setup') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                sh 'pytest --alluredir=allure-results'
            }
        }
    }

    post {
        always {
            script {
                sh 'allurectl upload allure-results'
            }
            cleanWs()
        }
    }
}