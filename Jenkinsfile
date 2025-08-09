pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/nehruprasad/node-jenkins-app.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t node-jenkins-app .'
            }
        }
        stage('Run Docker Container') {
            steps {
                // Stop and remove container if it exists
                bat 'docker stop node-jenkins-container || exit 0'
                bat 'docker rm node-jenkins-container || exit 0'
                // Run container
                bat 'docker run -d -p 3000:3000 --name node-jenkins-container node-jenkins-app'
            }
        }
    }
}
