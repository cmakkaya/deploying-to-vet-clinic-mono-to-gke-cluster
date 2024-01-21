pipeline {
    agent any
    environment {
        APP_NAME="Microservice Vet Clinic"
        APP_REPO_NAME="cmakkaya/deploying-to-vet-clinic-mono-to-gke-cluster"
    }
    
    stages {    
        stage('Deploy to GKE') {
            steps{
                sh "kubectl delete -f ."
            }
        }    
    }    
    post {
        always {
            echo 'Deleting all local images'
            sh 'docker image prune -af'
        }
    }
}