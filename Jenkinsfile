pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                deleteDir()
                script {
                    withCredentials([usernamePassword(credentialsId: 'github-credentials', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                        sh 'git clone https://github.com/itzchioma/Terraform-Jenkins-docker-intergation.git'
                    }
                }
            }
        }

        stage('Terraform Init') {
            steps {
                script {
                    // Use withCredentials to set AWS credentials for this stage
                    withCredentials([aws(accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws-credentials', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY')]) {
                        dir('terraform-jenkins') { // Assuming Terraform files are in the cloned directory
                            sh 'terraform init'
                        }
                    }
                }
            }
        }

               stage('Terraform Plan') {
            steps {
                script {
                    // Use withCredentials to set AWS credentials for this stage
                    withCredentials([aws(accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws-credentials', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY')]) {
                        dir('terraform-jenkins') { // Assuming Terraform files are in the cloned directory
                            sh 'terraform apply Plan'
                        }
                    }
                }
            }
        }

        stage('Terraform Apply') {
            steps {
                script {
                    // Use withCredentials to set AWS credentials for this stage
                    withCredentials([aws(accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws-credentials', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY')]) {
                        dir('terraform-jenkins') { // Assuming Terraform files are in the cloned directory
                            sh 'terraform apply -auto-approve'
                        }
                    }
                }
            }
        }

stage('Terraform State list') {
    steps {
        script {
            // Use withCredentials to set AWS credentials for this stage
            withCredentials([aws(accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws-credentials', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY')]) {
                dir('terraform-jenkins') { // Assuming Terraform files are in the cloned directory
                    // List Terraform state resources
                    sh 'terraform state list'
                }
            }
        }
    }
}


                stage('Terraform destroy') {
            steps {
                script {
                    // Use withCredentials to set AWS credentials for this stage
                    withCredentials([aws(accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'aws-credentials', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY')]) {
                        dir('terraform-jenkins') { // Assuming Terraform files are in the cloned directory
                            sh 'terraform destroy -auto-approve'
                        }
                    }
                }
        }
    }
 }
}