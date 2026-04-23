pipeline {
    agent any
    
    tools {
        dockerTool 'docker'
    }

    stages {
        stage('Install & Test') {
            steps {
                // Using 'docker run' is more reliable if plugins were acting up
                sh 'docker run --rm -v ${WORKSPACE}:/app -w /app python:3.9-slim sh -c "pip install -r requirements.txt"'
            }
        }

        stage('Build Image') {
            steps {
                sh 'docker build -t simple-flask-app:latest .'
            }
        }
    }
}