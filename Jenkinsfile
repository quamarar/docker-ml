pipeline {
  agent any

 stages {
       stage('checkout') {
         steps {
         checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/quamarar/docker-ml.git']])
         }
        }
      
       stage('build docker image') {
         steps {
         sh 'docker build -t docker-ml-model -f Dockerfile .'
         }
        }
      }
    }
  
       
    
 
