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
                  sh 'terraform init'
              }
            }   
        stage('terraform plan'){
            steps{
                    sh 'terraform plan'
              } 
            }   
        stage('terraform apply'){
            steps{
                    sh 'terraform apply --auto-approve'
              }
            }      
        stage('terraform destroy'){
            steps{
                    sh 'terraform apply --auto-approve'
              }         
            }
        }
}
