pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS2', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://88A8B6512B25C4D5CB2B8E71394A2122.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS2', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://88A8B6512B25C4D5CB2B8E71394A2122.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
