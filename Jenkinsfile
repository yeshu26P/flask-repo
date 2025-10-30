pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/yeshu26P/flask-repo.git'
            }
        }

        stage('Build') {
            steps {
                sh 'echo "Installing dependencies..."'
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Test') {
            steps {
                sh 'echo "Running tests..."'
                sh 'pytest test_app.py || true'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'echo "Building Docker image..."'
                sh 'docker build -t flask-app .'
            }
        }

        stage('Deploy') {
            steps {
                sh 'echo "Starting Flask container..."'
                sh 'docker run -d -p 5000:5000 flask-app'
            }
        }
    }
}

