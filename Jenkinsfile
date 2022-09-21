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
                 sh("docker build -t udagram-reverseproxy ./udagram-reverseproxy")
                }
            }
        }
        
         stage('push'){
            steps {
                 script{
                    withCredentials([string(credentialsId: 'docker-mwahab', variable: 'dockerhubpwd')]) {
                        sh("docker login -u mwahabsc25 -p ${dockerhubpwd}")
                    }        
                }
            }
        }
        
        }
    }