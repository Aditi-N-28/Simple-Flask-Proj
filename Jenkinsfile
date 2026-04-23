pipeline {
    agent any
    
    tools {
        dockerTool 'docker'
    }

    stages {
        stage('Install & Test') {
            steps {
                // This script block ensures the Docker tool is actually in the PATH
                script {
                    def dockerHome = tool name: 'docker', type: 'dockerTool'
                    withEnv(["PATH+DOCKER=${dockerHome}/bin"]) {
                        sh 'docker run --rm -v ${WORKSPACE}:/app -w /app python:3.9-slim sh -c "pip install -r requirements.txt"'
                    }
                }
            }
        }

        stage('Build Image') {
            steps {
                script {
                    def dockerHome = tool name: 'docker', type: 'dockerTool'
                    withEnv(["PATH+DOCKER=${dockerHome}/bin"]) {
                        sh 'docker build -t simple-flask-app:latest .'
                    }
                }
            }
        }
    }
}