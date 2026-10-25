pipeline {
    agent any

    options {
        timestamps()
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
                echo 'Brightz Academy source code checked out'
            }
        }

        stage('Validate Project') {
            steps {
                sh '''
                    test -f Dockerfile
                    test -f docker-compose.yml
                    test -d backend
                    test -d frontend
                    echo "Project validation successful"
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
            echo 'Brightz Academy pipeline completed successfully'
        }
        failure {
            echo 'Pipeline failed. Check Console Output.'
        }
    }
}
