pipeline {
    agent any
    stages {
        stage('Déploiement') {
            steps {
                echo 'Déploiement des ressources Kubernetes...'
                sh 'kubectl apply -f kubernetes/wordpress-deployment.yaml'
                sh 'kubectl apply -f kubernetes/wordpress-service.yaml'
            }
        }
    }
}
