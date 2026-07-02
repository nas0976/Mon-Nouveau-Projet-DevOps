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
  - name: jnlp
    image: jenkins/inbound-agent:3355.v388858a_47b_33-3-jdk21
'''
        }
    }
    stages {
        stage('Deploy') {
            steps {
                container('kubectl') {
                    echo 'Vérification de kubectl...'
                    sh 'which kubectl || echo "kubectl introuvable"'
                    sh 'kubectl version --client || echo "Erreur version kubectl"'
                    echo 'Déploiement des ressources...'
                    sh '/opt/bitnami/kubectl/bin/kubectl apply -f kubernetes/wordpress-deployment.yaml'
                }
            }
        }
    }
}
