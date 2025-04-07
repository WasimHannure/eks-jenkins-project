pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'eks-token', namespace: 'eksjenkins', serverUrl: 'https://3785E11C25CDC0EB9EA698CE7D4ABF31.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'eks-token', namespace: 'eksjenkins', serverUrl: 'https://3785E11C25CDC0EB9EA698CE7D4ABF31.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n eksjenkins"
                }
            }
        }
    }
}
