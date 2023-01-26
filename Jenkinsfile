pipeline {
    agent any
     environment {
            DOCKER_CERT_PATH = credentials('docker')
        }
    stages {
        stage('Building docker image client') {
            steps {
                dir("client/"){
                    bat 'docker build -t rahmafrioui/client .'
                       }  
            }
        }
      stage('Login to DockerHub') {
      steps {
          bat 'docker login -u rahmafrioui -p F?73r2mo123'
        }
      }
    
       stage('Push to DockerHub front') {
            steps {
                bat 'docker push $DOCKER_CREDS_USR/client'
      }
    }
    }
}
