pipeline {
    agent any
    environment {
        PATH=sh(script:"echo $PATH:/usr/local/bin", returnStdout:true).trim()
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

    post {
        always {
            echo 'Deleting all local images'
            sh 'docker image prune -af'
        }
    }
}