pipeline {
    agent any
 
    environment {
       
       AZURE_SUBSCRIPTION_ID='4917809c-4753-4722-81bf-a1b4429fd9ca'
       AZURE_TENANT_ID='819948b9-e473-435d-b429-6f100444732f'
        
    }

    stages {
        stage('Example') {
            steps {
                   withCredentials([usernamePassword(credentialsId: 'myAzureCredential', passwordVariable: 'CLIENT_SECRET', usernameVariable: 'AZURE_CLIENT_ID')]) {
                          
			   sh '''
			   
                                    az login --service-principal -u $AZURE_CLIENT_ID -p $CLIENT_SECRET -t $AZURE_TENANT_ID
		     
		                    az aks get-credentials --resource-group Temenos-POC-RG --name AKS-Temenos 
		     
		                    /usr/local/bin/kubectl get nodes
		     
		                    /usr/local/bin/kubectl apply -f k8s-deployment.yaml --validate=false
				    
				    /usr/local/bin/kubectl get pods
				    
				    /usr/local/bin/kubectl get services
				    
				    /home/ec2-user/helm install deployacrimage deployacrimage/
		     
						'''
			   
			   
                       }
                  }
	     }
      }
}	
