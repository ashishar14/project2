
pipeline {

    agent any

    stages {

        stage('Clone') {

            steps {
                git 'https://github.com/ashishar14/project2.git'
            }
        }

        stage('Build Docker Image') {

            steps {
                sh 'docker build -t analytics-website:v1 .'
            }
        }

        stage('Push Image') {

            steps {
                sh 'docker tag analytics-website:v1 ashishar14/analytics-website:v1'
                sh 'docker push ashishar14/analytics-website:v1'
            }
        }

        stage('Deploy Kubernetes') {

            steps {
                sh 'kubectl apply -f deployment.yaml'
                sh 'kubectl apply -f service.yaml'
            }
        }
    }
}
