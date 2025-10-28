pipeline {
    agent any

    stages {
        stage('Setup') {
            steps {
                echo 'Setting up virtual environment and installing dependencies...'
                bat '''
                    python -m venv venv
                    call venv\\Scripts\\activate
                    python -m pip install --upgrade pip
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Build') {
            steps {
                echo 'Running Python script...'
                bat '''
                    call venv\\Scripts\\activate
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
