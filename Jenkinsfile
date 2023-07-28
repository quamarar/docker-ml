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
         sh 'docker build -t docker-ml-model -f Dockerfile .'
         }
        }
      }
    }
  
       
    
 
