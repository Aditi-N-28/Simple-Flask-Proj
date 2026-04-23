pipeline {
    agent none // We specify agents per stage

    stages {
        stage('Install & Test') {
            agent {
                docker { image 'python:3.9-slim' }
            }
            steps {
                // This runs INSIDE the python container
                sh 'pip install -r requirements.txt'
                // sh 'pytest' // Uncomment this if you have tests
            }
        }

        stage('Build Image') {
            agent any // This runs on the Jenkins node to build the Docker image
            steps {
                sh 'docker build -t simple-flask-app:latest .'
            }
        }
    }
}