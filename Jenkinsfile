pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/asheesh1303-netizen/jenkins-docker-demo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins-demo:latest .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker rm -f jenkins-demo || true
                '''
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                docker run -d --name jenkins-demo -p 5000:5000 jenkins-demo:latest
                '''
            }
        }
    }
}
