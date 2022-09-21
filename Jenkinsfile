
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
                 sh 'docker build -t udagram-reverseproxy ./udagram-reverseproxy'
                }
            }
        }
        stage('tag'){
            steps {
                 script{
                    echo 'tag'
                 //sh 'docker tag udagram-reverseproxy mwahabsc25/udagram-reverseproxy:v1'
                }
            }
        }
        stage('push') {
            steps {
                script{
                    echo 'push'
                     //sh 'docker push mwahabsc25/udagram-reverseproxy:v1'
                    }
                }
            }
        }
    }
}