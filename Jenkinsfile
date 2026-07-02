pipeline {
    agent {
        kubernetes {
            yaml '''
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: kubectl
    image: bitnami/kubectl:latest
    command: ['cat']
    tty: true
'''
        }
    }
    stages {
        stage('Déploiement') {
            steps {
                container('kubectl') {
                    echo 'Déploiement des ressources Kubernetes...'
                    sh 'kubectl apply -f kubernetes/wordpress-deployment.yaml'
                }
            }
        }
    }
}
