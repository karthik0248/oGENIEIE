pipeline {
   agent any
   stages {
     stage('pull repo'){
    	steps {
          git 'https://github.com/karthik0248/oGENIEIE.git'
        }
     }
     stage('pull master'){
    	steps {
          sh 'git pull origin master'
        }
     }
     stage('docker version check'){
       steps{
          echo 'docker version check'
          sh 'docker --version'
       }
     }
     stage('docker build image'){
       steps{
          sh 'docker build -t myng:1 .'
       }
     } 
      stage('docker tag'){
        steps{
          sh 'docker tag myng:1 587589636093.dkr.ecr.ap-south-1.amazonaws.com/myng:1'
       }
     }
     stage('Push to ECR'){
       steps{
          sh '$(aws ecr get-login --no-include-email)'   
          sh 'docker push 587589636093.dkr.ecr.ap-south-1.amazonaws.com/myng:1'
       }
     }
     stage('run contianer'){
       steps{
          sh 'docker run --name mycont1 -itd -p 80:80 587589636093.dkr.ecr.ap-south-1.amazonaws.com/myng:1'
        }
     }
   }
}
