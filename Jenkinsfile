pipeline {
    
    agent any

    environment {
        def ecrRepo=" "
        def region="eu-north-1"
    }

    stages {

        stage('login to nexus repository') {
           steps {

           }
        }
        stage('Pull image from nexus repository') {
           steps {
              sh 'docker pull 15.206.81.210:9001/docker-hosted/devopsschool'
           }
        }

        stage('Push image to ecr') {
           steps {
              sh 'aws ecr get-login-password --region ${region} | docker login --username AWS --password-stdin ${ecrRepo}'
              sh 'docker tag 15.206.81.210:9001/docker-hosted/devopsschool ${ecrRepo}'
              sh 'docker push ${ecrRepo}'
           }
        }
        
         stage('Create eks cluster and node groups') {
           steps {
               sh 'ansible-playbook eks.yml' 
           }
        }
               
    }
}
