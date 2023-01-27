pipeline {
    agent any
     environment {
             DOCKERHUB_CREDENTIALS = credentials('docker')
        }
    stages {
        stage('Building docker image client') {
            steps {
                dir("client/"){
                    bat "docker build -t $DOCKERHUB_CREDENTIALS_USR/client ."
                       }  
            }
        }
      stage('Login to DockerHub') {
      steps {
          bat "echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin"
        }
      }
    
       stage('Push to DockerHub front') {
            steps {
                bat "docker push $DOCKER_CREDS_USR/client"
      }
    }
    }
}
