pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // This pulls your code from GitHub
                checkout scm
            }
        }

        stage('Install & Test') {
            steps {
                // This runs your tests inside a temporary Python container
                // so you don't have to install Python on your Jenkins server
                sh 'pip install -r requirements.txt'
                sh 'pytest test_app.py'
            }
        }

        stage('Build Docker Image') {
            steps {
                // This builds your final app image
                sh 'docker build -t my-flask-app:latest .'
            }
        }
    }
}