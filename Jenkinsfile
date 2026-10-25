pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Validate') {
            steps {
                sh '''
                    test -f Dockerfile
                    test -f docker-compose.yml
                    test -d backend
                    test -d frontend
                '''
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t brightz-academy:latest .'
            }
        }
    }

    post {
        success {
            echo 'Brightz Academy pipeline SUCCESS'
        }
        failure {
            echo 'Pipeline failed. Check Console Output.'
        }
    }
}
