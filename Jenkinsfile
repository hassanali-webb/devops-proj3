pipeline {
    agent any

    stages {
        stage('Pull Code') {
            steps {
                git branch: 'main', url: 'https://github.com/hassanali-webb/devops-proj3.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-app .'
            }
        }
        stage('Stop Old Container') {
            steps {
                sh 'docker ps -q --filter "name=devops-container" | xargs -r docker stop'
                sh 'docker ps -a -q --filter "name=devops-container" | xargs -r docker rm'
            }
        }
        stage('Run Container') {
            steps {
                sh 'docker run -d --name devops-container -p 5000:5000 devops-app'
            }
        }
    }
}
