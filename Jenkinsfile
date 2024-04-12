pipeline{  
  environment {
    registry = "shariqanwar20/iba-cicd"
    registryCredential = 'dockerhub'
    dockerImage = ''
  }
  agent any
    stages {
        stage('Build'){
           steps{
              script{
                sh 'cd application'
                sh 'npm install'
              } 
           }   
        }
        stage('Building image') {
            steps{
                script {
                    dockerImage = docker.build registry + ":latest"
                    }
                }
            }
        stage('Deploying into k8s'){
        steps{
            sh 'kubectl apply -f ./k8/deployment.yml' 
        }
    }
    }
}