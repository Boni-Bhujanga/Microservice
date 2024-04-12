pipeline {
    agent any

    stages {
        stage('Deploy to kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://CFDD92983661C315D231BFB1D86CE96D.gr7.ap-south-1.eks.amazonaws.com']]) {
                     sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
        
        stage('Hello') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://CFDD92983661C315D231BFB1D86CE96D.gr7.ap-south-1.eks.amazonaws.com']]) {
                      sh "kubectl get svc -n webapps"
                }
            }
        }
        
    }
}
