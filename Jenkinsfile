pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS3', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://0002E196D5E80C75A1C972FA47812ED2.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS3', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://0002E196D5E80C75A1C972FA47812ED2.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
