pipeline {
  agent any


  environment {
    GIT_COMMIT_HASH = sh (script: "git rev-parse --short HEAD", returnStdout: true)   
  }
  
 stages {
       stage('checkout') {
         steps {
            git 'https://github.com/quamarar/docker-ml.git'

           }
         }
        
      
       stage('build docker image') {
         steps {
         sh 'sudo docker build -t docker-ml-model:${GIT_COMMIT_HASH} -f Dockerfile .'
         sh 'sudo docker tag docker-ml-model:${GIT_COMMIT_HASH} 836350033173.dkr.ecr.us-east-1.amazonaws.com/erp:${GIT_COMMIT_HASH} '
         }
        }
   
      stage('login to ecr') {
        steps {
          sh 'aws ecr get-login-password --region us-east-1 | sudo docker login --username AWS --password-stdin 836350033173.dkr.ecr.us-east-1.amazonaws.com'
          sh 'sudo docker push 836350033173.dkr.ecr.us-east-1.amazonaws.com/erp:${GIT_COMMIT_HASH}'
    }
 }
   
      stage('pushing to pm') {
        steps {
          sh 'aws ssm put-paramater --name "MSIL/Image" --value "${GIT_COMMIT_HASH}" '
      
    }
 }
   
 }
}
  
       
    
 
