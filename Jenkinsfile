pipeline {
    agent {
        kubernetes {
            yaml '''
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: jnlp
    image: jenkins/inbound-agent:3355.v388858a_47b_33-3-jdk21
  - name: kubectl
    image: dtzar/helm-kubectl:latest
    command: ['cat']
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
                sh 'kubectl apply -f kubernetes/wordpress-service.yaml'
                }
            }
        }
    }
}
