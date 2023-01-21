pipeline {
    agent any
      tools {
    // a bit ugly because there is no `@Symbol` annotation for the DockerTool
    // see the discussion about this in PR 77 and PR 52: 
    // https://github.com/jenkinsci/docker-commons-plugin/pull/77#discussion_r280910822
    // https://github.com/jenkinsci/docker-commons-plugin/pull/52
    'org.jenkinsci.plugins.docker.commons.tools.DockerTool' '18.09'
  }
  environment {
    DOCKER_CERT_PATH = credentials('id-for-a-docker-cred')
  }
      
    stages {
        stage('Building docker image client') {
            steps {
                dir("client/"){
                    sh 'docker build -t $DOCKER_CREDS_USR/client .'
                       }  
            }
        }
      stage('Login to DockerHub') {
      steps {
          sh 'docker login -u $DOCKER_CREDS_USR -p $DOCKER_CREDS_PSW'
        }
      }
    
       stage('Push to DockerHub front') {
            steps {
                sh 'docker push $DOCKER_CREDS_USR/client'
      }
    }
    }
}
