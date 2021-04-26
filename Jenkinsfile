node {
  stage('Apply Kubernetes files') {
    withKubeConfig([credentialsId: 'kubeconfig', serverUrl: 'https://devops-aks-dns-0e0112c4.hcp.eastus.azmk8s.io']) {
      sh 'kubectl apply -f my-kubernetes-directory'
    }
  }
}
