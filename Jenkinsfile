pipeline { 
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/Devangam/Microservice.git'
            }
        }
        stage('Deploy To Kubernetes') {
            steps {
                withKubeConfig(caCertificate: '', clusterName: 'my-eks22', contextName: '', credentialsId: 'kube-cred', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://392ACA36C772A0AC935330B81941828C.gr7.ap-south-1.eks.amazonaws.com') {
                    sh "kubectl apply -f deployment-service.yml"
}
            }
        }
        stage('Verify Deployment') {
            steps {
               withKubeConfig(caCertificate: '', clusterName: 'my-eks22', contextName: '', credentialsId: 'kube-cred', namespace: 'webapps', restrictKubeConfigAccess: false, serverUrl: 'https://392ACA36C772A0AC935330B81941828C.gr7.ap-south-1.eks.amazonaws.com') {
                    sh "kubectl get svc -n webapps"
}
            }
        }
    }
}
