pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-kundu', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://7CFF96D902783A47E974C368A1307AF3.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-kundu', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://7CFF96D902783A47E974C368A1307AF3.gr7.ap-south-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
