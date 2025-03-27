pipeline {
  agent any
  
   tools {nodejs "node"}
    
  stages {
    stage("GitHub git cloning") {
            steps {
                script {
                    git branch: 'main', url: 'https://github.com/dajari1/react-docker2.git' 
                   
                }
            }
        }
     
    stage('starting npm installation.......') {
      steps {
        sh 'npm install'
      }
    }
  
     stage('Build Docker Image for the app') {
            steps {
                script {
                 
                  sh 'printenv'
                  sh 'git version'
                 
                  sh 'docker build -t dajari1/node-app5.0 .'
                }
            }
        }


        stage('Docker Image deployment to DockerHub') {
            steps {
                script {
                  
                 withCredentials([string(credentialsId: 'DennisID', variable: 'DennisID')]) {
                    sh 'docker login -u dajari1 -p ${DennisID}'
            }
           
            sh 'docker push dajari1/node-app5.0:latest'
        }
            }   
        }
        

  }
}
         
     

  

