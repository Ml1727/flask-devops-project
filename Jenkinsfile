pipeline {
    agent any

    environment {
        PATH = "/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin:/snap/bin"
    }

    stages {
        stage('Clone Repo') {
            steps {
                checkout scm
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t flask-app:latest .'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh '''
                  kubectl version --client
                  kubectl apply -f k8s-deployment.yaml
                '''
            }
        }
    }
}
