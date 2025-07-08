pipeline {
    agent any

    stages {
        stage('Clone Source') {
            steps {
                git 'https://github.com/DoiHmolongvoito/simple-flask-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("flask-app")
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker rm -f flask-app || true'
                sh 'docker run -d -p 5000:5000 --name flask-app flask-app'
            }
        }
    }
}
