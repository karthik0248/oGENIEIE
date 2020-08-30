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
     stage('run contianer'){
       steps{
          sh 'docker run --name mycont1 -itd -p 81:80 myng:1'
          sh 'docker run --name mycont2 -itd -p 82:80 myng:1'
          sh 'docker run --name mycont3 -itd -p 83:80 myng:1'
        }
     }
   }
}
