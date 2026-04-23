pipeline {
    agent any

    stages {
        stage('Install & Test') {
            steps {
                // This creates a virtual environment, activates it, and installs requirements
                sh '''
                    python3 -m venv venv
                    . venv/bin/activate
                    pip install -r requirements.txt
                '''
            }
        }

        stage('Build Image') {
            steps {
                // We only use Docker at the very end to package the app
                sh 'docker build -t simple-flask-app:latest .'
            }
        }
    }
}