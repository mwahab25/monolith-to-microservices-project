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
                 bat "docker build -t udagram-api-feed ./udagram-api-feed"
                 bat "docker build -t udagram-api-user ./udagram-api-user"
                 bat "docker build -t udagram-frontend ./udagram-frontend"
                }
            }
        }
        
         stage('push'){
            steps {
                 script{
                    withCredentials([string(credentialsId: 'docker-mwahab', variable: 'dockerhubpwd')]) {
                        bat "docker login -u mwahabsc25 -p ${dockerhubpwd}"
                    }        
                    bat "docker tag udagram-reverseproxy mwahabsc25/udagram-reverseproxy:latest"
                    bat "docker tag udagram-api-feed mwahabsc25/udagram-api-feed:latest"
                    bat "docker tag udagram-api-user mwahabsc25/udagram-api-user:latest"
                    bat "docker tag udagram-frontend mwahabsc25/udagram-frontend:latest"
                    
                    bat "docker push mwahabsc25/udagram-reverseproxy"
                    bat "docker push mwahabsc25/udagram-api-feed"
                    bat "docker push mwahabsc25/udagram-api-user"
                    bat "docker push mwahabsc25/udagram-frontend"
                }
            }
        }
        
        }
    }