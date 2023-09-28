pipeline {
    
    agent any

    stages {
        
         stage('Create eks cluster and node groups') {
           steps {
               sh 'ansible-playbook eks-new.yml' 
           }
        }
               
    }
}
