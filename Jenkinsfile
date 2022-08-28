pipeline{
    agent any
    tools {
    terraform 'Terraform'
    }  
    stages{
        stage('Git clone'){
            steps{
                git branch: 'main', url: 'https://github.com/eoyebami/terraform_pipeline.git'
            }
        }
        stage('terraform init'){
            steps{
                withCredentials([<object of type com.cloudbees.jenkins.plugins.awscredentials.AmazonWebServicesCredentialsBinding>]) {
                sh 'terraform init'
              } 
            }
        }    
        stage('terraform plan'){
            steps{
                withCredentials([<object of type com.cloudbees.jenkins.plugins.awscredentials.AmazonWebServicesCredentialsBinding>]) {

                sh 'terraform plan'
              } 
            }   
        }
        stage('terraform apply'){
            steps{
                withCredentials([<object of type com.cloudbees.jenkins.plugins.awscredentials.AmazonWebServicesCredentialsBinding>]) {
                sh 'terraform apply --auto-approve'
              } 
            }      
        }
        stage('terraform destroy'){
            steps{
                withCredentials([<object of type com.cloudbees.jenkins.plugins.awscredentials.AmazonWebServicesCredentialsBinding>]) {
                sh 'terraform apply --auto-approve'
              }
            }         
        }
    }
}
