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
    command: ['sleep']
    args: ['99d']
    tty: true
'''
        }
    }
    stages {
        stage('Deploy') {
            steps {
                container('kubectl') {
                    echo 'Déploiement des ressources...'
                    sh 'kubectl apply -f kubernetes/wordpress-deployment.yaml'
                }
            }
        }
    }
}
