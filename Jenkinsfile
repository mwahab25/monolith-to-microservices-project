pipeline {
    agent any
    stages {
         stage('Clone repository') { 
            steps { 
                script{
                checkout scm
                }
            }
        }

        stage('Build') { 
            steps { 
                script{
                 bat "docker build -t udagram-reverseproxy ./udagram-reverseproxy"
                }
            }
        }
        
         stage('push'){
            steps {
                 script{
                    withCredentials([string(credentialsId: 'docker-mwahab', variable: 'dockerhubpwd')]) {
                        bat "docker login -u mwahabsc25 -p ${dockerhubpwd}"
                    }        
                }
            }
        }
        
        }
    }