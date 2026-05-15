pipeline {
    agent {
        label 'python3'
    }

    environment {
        ALLURE_ENDPOINT = 'https://allure.autotests.cloud/'
        ALLURE_TOKEN = '23b4a183-838b-482d-a376-8294dd4bd586'
        ALLURE_PROJECT_ID = '5200'
    }

    stages {
        stage('Setup Python') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run tests') {
            steps {
                sh 'pytest --alluredir=allure-results'
            }
        }

        stage('Upload to Allure TestOps') {
            steps {
                sh 'allurectl upload allure-results'
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}