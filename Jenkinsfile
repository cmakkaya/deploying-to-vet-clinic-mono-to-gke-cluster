pipeline {
    agent any
    environment {
        PATH=sh(script:"echo $PATH:/usr/local/bin", returnStdout:true).trim()
        APP_NAME="Microservice Vet Clinic"
        APP_REPO_NAME="cmakkaya/microservices-application-vet-clinic-production"        
        AWS_ACCOUNT_ID=sh(script:'export PATH="$PATH:/usr/local/bin" && aws sts get-caller-identity --query Account --output text', returnStdout:true).trim()
        AWS_REGION="us-east-1"
        ECR_REGISTRY="${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_REGION}.amazonaws.com"
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