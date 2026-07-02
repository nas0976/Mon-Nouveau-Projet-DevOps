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
                    echo 'Déploiement des ressources Kubernetes...'
                    sh 'kubectl apply -f kubernetes/wordpress-deployment.yaml'
                }
            }
        }
    }
}
