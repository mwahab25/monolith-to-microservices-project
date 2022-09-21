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
                 //bat "docker build -t udagram-reverseproxy ./udagram-reverseproxy"
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
                    //bat "docker tag udagram-reverseproxy mwahabsc25/udagram-reverseproxy:v1"
                    bat "docker tag udagram-api-feed mwahabsc25/udagram-api-feed:v1"
                    bat "docker tag udagram-api-user mwahabsc25/udagram-api-user:v1"
                    bat "docker tag udagram-frontend mwahabsc25/udagram-frontend:v1"
                    
                    //bat "docker push mwahabsc25/udagram-reverseproxy:v1"
                    bat "docker push mwahabsc25/udagram-api-feed:v1"
                    bat "docker push mwahabsc25/udagram-api-user:v1"
                    bat "docker push mwahabsc25/udagram-frontend:v1"
                }
            }
        }
        
        }
    }