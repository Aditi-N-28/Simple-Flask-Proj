pipeline {
    agent any
    
    tools {
        dockerTool 'docker' 
    }

    stages {
        stage('Install & Test') {
            steps {
                script {
                    // This manually finds the path where Jenkins installed the Docker tool
                    def dockerPath = tool name: 'docker', type: 'dockerTool'
                    
                    // We use the full path to the docker executable
                    sh "${dockerPath}/bin/docker run --rm -v ${WORKSPACE}:/app -w /app python:3.9-slim sh -c 'pip install -r requirements.txt'"
                }
            }
        }

        stage('Build Image') {
            steps {
                script {
                    def dockerPath = tool name: 'docker', type: 'dockerTool'
                    
                    sh "${dockerPath}/bin/docker build -t simple-flask-app:latest ."
                }
            }
        }
    }
}