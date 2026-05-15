pipeline {
    agent {
        label 'python3-jenkins-agent-1'
    }

    environment {
        ALLURE_ENDPOINT = 'https://allure.autotests.cloud/'
        ALLURE_TOKEN = '23b4a183-838b-482d-a376-8294dd4bd586'
        ALLURE_PROJECT_ID = '5200'
    }

    stages {
        stage('Setup') {
            steps {
                sh 'pip install --break-system-packages -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                sh 'pytest --alluredir=allure-results || true'
            }
        }

        stage('Upload to Allure TestOps') {
            steps {
                sh 'curl -L0 https://github.com/allure-framework/allurectl/releases/latest/download/allurectl_linux_amd64 -o ./allurectl'
                sh 'chmod +x ./allurectl'
                sh './allurectl upload allure-results'
            }
        }
    }

    post {
        always {
            cleanWs()
        }
    }
}