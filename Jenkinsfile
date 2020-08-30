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
          sh 'docker run --name mycont1 -itd -p 80:80 myng:1'
        }
     }
   }
}
