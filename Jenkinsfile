pipeline {
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-kundu', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://EA10B5AFE29FA7BC2111ACA3F26A8AC5.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl apply -f deployment-service.yml"
                    
                }
            }
        }
        
        stage('verify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-kundu', contextName: '', credentialsId: 'k8s-token', namespace: 'webapps', serverUrl: 'https://EA10B5AFE29FA7BC2111ACA3F26A8AC5.gr7.ap-southeast-1.eks.amazonaws.com']]) {
                    sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
