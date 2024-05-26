pipeline {
    agent any

    stages {
        stage('Deploy to k8s') {
            steps {
               withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8s', namespace: 'webapps', serverUrl: 'https://AA08E14EF6F429BF9FFF46B080106A7F.gr7.us-east-1.eks.amazonaws.com']]) 
               {
                   sh "kubectl  apply -f deployment-service.yaml"
                   sleep 60
               }
                    }
                }
                
         stage("Verify Deployment") {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: '', credentialsId: 'k8s', namespace: 'webapps', serverUrl: 'https://AA08E14EF6F429BF9FFF46B080106A7F.gr7.us-east-1.eks.amazonaws.com']]) {
                    { sh "kubectl get services -n webapps"
                }
                }
        }
    }
}
