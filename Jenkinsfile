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
           script{
             GIT_COMMIT_HASH = sh (script: "git log -n 1 --pretty=format:'%H'", returnStdout: true) 
             echo "${GIT_COMMIT_HASH}"
           }
         sh 'sudo docker build -t docker-ml-model -f Dockerfile .'
         sh 'sudo docker tag docker-ml-model:${GIT_COMMIT_HASH} 836350033173.dkr.ecr.us-east-1.amazonaws.com/erp:${GIT_COMMIT_HASH} '
         }
        }
      stage('login to ecr') {
        steps {
          sh 'aws ecr get-login-password --region us-east-1 | sudo docker login --username AWS --password-stdin 836350033173.dkr.ecr.us-east-1.amazonaws.com'
          sh 'sudo docker push 836350033173.dkr.ecr.us-east-1.amazonaws.com/erp:${GIT_COMMIT_HASH}'
    }
 }
 }
}
  
       
    
 
