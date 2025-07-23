pipeline {
    agent any

    environment {
        VENV = 'venv'
    }

    stages {
        stage('Create Virtual Environment') {
            steps {
                sh 'python3 -m venv $VENV'
            }
        }

        stage('Install Dependencies') {
            steps {
                sh './$VENV/bin/pip install --upgrade pip'
                sh './$VENV/bin/pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                sh './$VENV/bin/python -m pytest app/test_calculator.py'
            }
        }
    }

    post {
        success {
            echo '✅ Tests passed!'
        }
        failure {
            echo '❌ Tests failed!'
        }
    }
}

