pipeline{  
  environment {
    registry = "shariqanwar20/iba-cicd"
    registryCredential = 'dockerhub'
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
            bat 'kubectl apply -f deployment.yml'
        }
    }
}

}