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
                 bash 'docker build -t udagram-reverseproxy ./udagram-reverseproxy'
                }
            }
        }
        
         stage('push'){
            steps {
                 script{
                    withCredentials([string(credentialsId: 'docker-mwahab', variable: 'dockerhubpwd')]) {
                        bash 'docker login -u mwahabsc25 -p ${dockerhubpwd}'
                    }        
                }
            }
        }
        
        }
    }