pipeline {
  agent any

 stages {
       stage('checkout') {
         steps {
           git 'https://github.com/quamarar/docker-ml.git'
         }
        }
      
       stage('build docker image') {
         steps {
         sh 'sudo docker build -t docker-ml-model -f Dockerfile .'
         }
        }
      stage('login to ecr') {
        steps {
          sh 'aws ecr get-login-password --region us-east-1 | sudo docker login --username AWS --password-stdin 836350033173.dkr.ecr.us-east-1.amazonaws.com'
      }
    }
      stage('tagging and pushing image to ecr'){
        steps {
          sh 'sudo docker tag docker-ml-model:latest 836350033173.dkr.ecr.us-east-1.amazonaws.com/erp:latest'
    }
 }
 }
}
  
       
    
 
