pipeline {
    agent any
     environment {
             DOCKERHUB_CREDENTIALS = credentials('docker')
        }
    stages {
        stage('Building docker image client') {
            steps {
                dir("client/"){
                    sh "docker build -t $DOCKERHUB_CREDENTIALS_USR/client ."
                       }  
            }
        }
      stage('Login to DockerHub') {
      steps {
          sh "docker login -u $DOCKERHUB_CREDENTIALS_USR -p $DOCKERHUB_CREDENTIALS_PSW"
        }
      }
    
       stage('Push to DockerHub front') {
            steps {
                sh "docker push $DOCKERHUB_CREDENTIALS_USR/client"
      }
    }
    }
}
