pipeline {
    agent any

    stages {
        stage('Setup') {
            steps {
                echo 'Setting up virtual environment and installing dependencies...'
                sh '''
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Build') {
            steps {
                echo 'Running Python script...'
                sh '''
                    . venv/bin/activate
                    python app.py
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Something went wrong in one of the stages.'
        }
    }
}
