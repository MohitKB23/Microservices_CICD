pipeline { 
    agent any

    stages {
        stage('Deploy To Kubernetes') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://ED05698D178A444A943D8C0D3CB2EAF1.gr7.ap-south-1.eks.amazonaws.com']]) {
                     sh "kubectl apply -f deployment-service.yml"
                   
                }
            }
        }
        
        stage('Verify Deployment') {
            steps {
            withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://ED05698D178A444A943D8C0D3CB2EAF1.gr7.ap-south-1.eks.amazonaws.com']]) {
                     sh "kubectl get svc -n webapps"
                }
            }
        }
    }
}
