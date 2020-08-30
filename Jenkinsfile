pipeline {
   agent any
   tools {
      jdk 'jdk1.8'
      maven 'maven3'
    }
    stages{
      stage('git pull'){
        steps{
            echo 'pulling git repo'
            git 'https://github.com/karthik0248/oGENIEIE.git'
          }
        }
        stage('docker version'){
           steps{
             sh 'docker --version'
           }
         }
         stage('Image build')
           steps{
              sh 'docker build -t myng:1 .'
           }
         }
         stage('docker tag'){
            steps{
               sh 'docker tag myng:1 587589636093.dkr.ecr.ap-south-1.amazonaws.com/myng:1'
           }
         }
         stage('push image to ECR'){
            steps{
               sh '$(aws ecr grt-login --no-include-email)'
               sh 'docker push 587589636093.dkr.ecr.ap-south-1.amazonaws.com/myng:1'
           }
         } 
         stage('start docker contain'){
           steps{
              sh 'docker run --name Myynag -itd -p 80:80 myng:1'
           }
         }
      } 
  }
