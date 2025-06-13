pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'MY-EKS2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://0A27366EB5A01D24A5B9F8A164D86225.yl4.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'MY-EKS2', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://0A27366EB5A01D24A5B9F8A164D86225.yl4.us-east-2.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
