pipeline {
  agent any

      environment {
        tag = sh(returnstdout: true, script: "git rev-parse --short=10 head").trim()
    }

 stages {
       stage('checkout') {
         steps {
            git 'https://github.com/quamarar/docker-ml.git'

           }
         }
        
      
       stage('build docker image') {
         steps {
         sh 'sudo docker build  -f Dockerfile . -t docker-ml-model:${tag}'
         }
        }
      stage('login to ecr') {
        steps {
          sh 'aws ecr get-login-password --region us-east-1 | sudo docker login --username AWS --password-stdin 836350033173.dkr.ecr.us-east-1.amazonaws.com'
          sh 'sudo docker tag docker-ml-model:${tag} 836350033173.dkr.ecr.us-east-1.amazonaws.com/erp:${tag}'
          sh 'sudo docker push 836350033173.dkr.ecr.us-east-1.amazonaws.com/erp:latest'
    }
 }
 }
}
  
       
    
 
