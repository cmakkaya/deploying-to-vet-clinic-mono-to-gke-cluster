pipeline {
    agent any
    environment {
        APP_NAME="Microservice Vet Clinic"
        APP_REPO_NAME="cmakkaya/microservices-application-vet-clinic-production"
    }
    
    stages {
        stage ('Clean Workspace'){
            steps{
                cleanWs()
            }
        }      
        stage('Deploy to GKE') {
            steps{
                sh "kubectl apply -f ."
            }
        }    
    }    
}