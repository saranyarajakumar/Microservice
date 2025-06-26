pipeline {  
    agent any
 
    stages {
        stage('delpoy to kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://3A9337BFD08396AB9600430C11A5C39A.gr7.eu-west-2.eks.amazonaws.com']]) {
                sh "kubectl apply -f deployment-service.yml"
                }
            }
        }
        stage('verify Deployment') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://3A9337BFD08396AB9600430C11A5C39A.gr7.eu-west-2.eks.amazonaws.com']]) {
               sh "kubectl get svc -n webapps"
                }
            }
       }
    }
}
