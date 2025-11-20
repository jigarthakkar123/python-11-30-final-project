pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/jigarthakkar123/python-11-30-final-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t django-app .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                    docker stop django-container || true
                    docker rm django-container || true
                    docker run -d -p 8000:8000 --name django-container django-app
                '''
            }
        }
    }
}
