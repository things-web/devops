pipeline {
    agent any

    stages {
        stage('Clone Code') {
            steps {
                git branch: 'main', url: 'https://github.com/yourusername/jenkins-docker-cicd-project.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-webapp .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker rm -f devops-container || true'
                sh 'docker run -d --name devops-container -p 8080:80 devops-webapp'
            }
        }

        stage('Verify Deployment') {
            steps {
                sh 'curl -f http://localhost:8080'
            }
        }
    }

    post {
        success {
            echo 'Deployment Successful!'
        }
        failure {
            echo 'Pipeline Failed!'
        }
    }
}
