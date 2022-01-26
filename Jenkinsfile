pipeline {
    agent {
        docker {
            image 'node:latest'
        }
    }
    stages {
        stage('npm install') {
            steps {
                sh 'npm install'
            }
        }

        stage('install client dependencies') {
            steps {
                sh 'cd client'
                sh 'npm install'
            }
        }

        stage('install server dependencies') {
            steps {
                sh 'cd ..'
                sh 'cd server'
                sh 'npm install'
            }
            
        }
    }
}