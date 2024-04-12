pipeline{  
  environment {
    registry = "shariqanwar20/iba-cicd"
    registryCredential = 'dockerhub'
    kubeconfigCredentialId = "KUBECONFIG"
    dockerImage = ''
  }
  agent any
    stages {
    stage('Build') {
        steps {
            script {
                bat 'npm install'
            }   
        }
    }
    stage('Building image') {
        steps {
            script {
                  dockerImage = docker.build registry + ":latest"
                 }
        }
    }
    stage('Deploying into k8s') {
            steps {
                script {
                        withCredentials([file(credentialsId: kubeconfigCredentialId, variable: 'KUBECONFIG')]) {
                        bat 'kubectl apply -f ./k8s/deployment.yml'
                    }
                }
            }
        }
}

}