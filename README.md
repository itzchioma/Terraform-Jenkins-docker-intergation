## Terraform-Jenkins-docker-intergation
### A Complete Overview of Jenkins-terraform-docker intergation

### Technology to have for this particular deploy
+ Aws account
+ Installing Jenkins on Ubuntu ,,https://www.jenkins.io/doc/book/installing/linux/,,
+ Dockerhub account

#### Prerequisite
+ Basic understanding of Jenkins, Terraform, Docker, AWS
+ A server with Jenkins & Terraform pre-installed
+ An access key & secret key created the AWS

##### Lets, start with the configuration of the project

- Step 1:- installing Jenkins on Ubuntu.
<!-- Installing Jenkins via command line -->
```bash
sudo apt-get update
sudo apt-get install jenkins
sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \
  https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key
echo "deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc]" \
  https://pkg.jenkins.io/debian-stable binary/ | sudo tee \
  /etc/apt/sources.list.d/jenkins.list > /dev/null
sudo systemctl enable jenkins
sudo systemctl start jenkins
sudo systemctl status jenkins
```

- Step 1:- Install Terraform plugin
- Create an ec2 instance from AWS console.
- ssh into the ec2 instance and configure Jenkins
- In order to integrate Jenkins with Terraform, we need to install the Terraform plugin in Jenkins.
- Go to Manage Jenkins -> Manage Plugins -> Search “Terraform Plugin” -> Click on Install -> Restart the Jenkins

- Step 2:- Configure the Terraform plugin
- Go to Manage Jenkins -> Global Tool Configuration -> Search for “Terraform” -> Add Path of the Terraform.

- Step 4:- Install Multibranch pipeline plugin
- For this project, we will create the multibranch pipeline. In order to create that we need to install a Multibranch pipeline
- Go to Manage Jenkins -> Manage Plugins -> Search “Pipeline: Multibranch” -> Install the plugin -> Restart the Jenkins
  
- Step 5:- Create the Multibranch pipeline
- Click on New Item -> Click on Multibranch Pipeline -> Click on OK
- Now we need to configure the project
- Go to Branch sources -> Click on Git -> Add the repository URL
- By default in the Build Configuration By Jenkins is selected.
- Click on Save
- Now Jenkins will Scan the Multibranch Pipeline Log
  
- Now click on the Build with parameter
