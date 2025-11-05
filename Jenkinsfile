pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                echo "Cloning repository..."
                git branch: 'main', url: 'https://github.com/shivansh123sharma/DevOps-Project-Two-Tier-Flask-App.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                echo "Building Docker image..."
                sh 'docker build -t flask-app .'
            }
        }

        stage('Deploy with Docker Compose') {
            steps {
                echo "Deploying with Docker Compose..."
                sh 'docker compose down || true'
                sh 'docker compose up -d --build'
            }
        }
    }

    post {
        always {
            echo "Pipeline finished."
        }
        failure {
            echo "Pipeline failed — check logs."
        }
    }
}
