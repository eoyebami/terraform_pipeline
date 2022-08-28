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
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    credentialsId: "aws-jenkins-demo",
                    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY'
                ]]) {
                    sh 'terraform plan'
                }
              } 
            }   
        stage('terraform apply'){
            steps{
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    credentialsId: "aws-jenkins-demo",
                    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY'
                ]]) {
                    sh 'terraform apply --auto-approve'
                }   
              }
            }      
        stage('terraform destroy'){
            steps{
                withCredentials([[
                    $class: 'AmazonWebServicesCredentialsBinding',
                    credentialsId: "aws-jenkins-demo",
                    accessKeyVariable: 'AWS_ACCESS_KEY_ID',
                    secretKeyVariable: 'AWS_SECRET_ACCESS_KEY'
                ]]) {
                    sh 'terraform destroy --auto-approve'
                } 
              }         
            }
        }
}

