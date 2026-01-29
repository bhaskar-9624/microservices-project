pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-3', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://5E071B77E254660E05E40081ABAADCCD.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-3', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://5E071B77E254660E05E40081ABAADCCD.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
