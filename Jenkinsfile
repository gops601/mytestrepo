pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-app .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                  docker rm -f flask-app-container || true
                  docker run -d --name flask-app-container -p 8082:5000 flask-app
                '''
            }
        }
    }
}
