pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/yourusername/DevOps-CI-CD-Project.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-ci-cd .'
            }
        }
        stage('Push to DockerHub') {
            steps {
                withDockerRegistry([credentialsId: 'dockerhub-creds', url: '']) {
                    sh 'docker tag devops-ci-cd yourdockerhubusername/devops-ci-cd:latest'
                    sh 'docker push yourdockerhubusername/devops-ci-cd:latest'
                }
            }
        }
        stage('Deploy') {
            steps {
                sh 'docker run -d -p 5000:5000 yourdockerhubusername/devops-ci-cd:latest'
            }
        }
    }
}
