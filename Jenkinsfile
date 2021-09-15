pipeline {
    agent any

    stages {
        stage('SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/mahesh-123123/e.git'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                  bat 'docker build -t maheshreddy123/ee:v1 .'
                 
                }
            }
        }
        
          stage('Push to Docker Hub') {
            steps {
                script {
                    withDockerRegistry(credentialsId: 'dockerhub',  url: '') {
                bat 'docker push maheshreddy123/ee:v1'
               
                }
              }
            }
          }
        
        stage('Email') {
            steps {
                mail bcc: '', body: '''Dear Sir,
                        i am Mahesh  from testing department. web application was successfully git clone, 
                        maven build, docker build, push docker hub, 
                        deploy in tomcat sending to mail..''', cc: '', from: '', replyTo: '', subject: 'jenkins to docker hub', to: 'mmssrraju123@gmail.com'
                
            }
        }
    }
}
