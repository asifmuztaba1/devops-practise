pipeline {
    agent any

    stages {
        stage('Build and Push Docker Image') {
            steps {
                script {
                    def dockerImage = docker.build('devops-practise:1.0', '.')
                    dockerImage.push()
                }
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                container('kubectl') {
                    sh 'kubectl apply -f k8s-deployment.yaml'
                }
            }
        }
    }
}
