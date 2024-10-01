pipeline {
    agent any 

    stages {
        stage('Deploy To Kubernetes') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: 'jenkins', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://67F00237F41449653622C5D7B1E841AB.gr7.us-east-1.eks.amazonaws.com']]) {
                     sh "kubectl apply -f deployment-service.yml"
                }
            }
        }   
        
        stage('verfify Deployment') {
            steps {
                withKubeCredentials(kubectlCredentials: [[caCertificate: '', clusterName: 'EKS-1', contextName: 'jenkins', credentialsId: 'k8-token', namespace: 'webapps', serverUrl: 'https://67F00237F41449653622C5D7B1E841AB.gr7.us-east-1.eks.amazonaws.com']]) {
                    sh "kubectl get all -n webapps"
                }
            }    
        }
    }
}
