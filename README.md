In this article, we will
Create a VPC, Subnets, and Configure network requirements.
Create EC2 instances with Auto scaling group and Launch template.
Create a Load balancer with a target group to the Auto Scaling group.
Setting up the Environment
1. Install AWS CLI and configure
If you don’t have AWS CLI already, install AWS CLI to your system based on your OS by following the instructions here.

Installing or updating the latest version of the AWS CLI
Install the AWS CLI on your system.
docs.aws.amazon.com

The next step is to configure your AWS profile to use in the CLI. Follow the instructions from the official documentation based on your machine type.

Configuring the AWS CLI
Configure the AWS Command Line Interface (AWS CLI) and specify the settings for interacting with AWS.
docs.aws.amazon.com

2. Install Terraform
Install Terraform in your system, if you don't have it already. Follow the instructions based on your platform on the official site given below.

Install Terraform | Terraform | HashiCorp Developer
Install Terraform on Mac, Linux, or Windows by downloading the binary or using a package manager (Homebrew or…
developer.hashicorp.com

3. Initialise Project
Create an empty project directory and create a file called main.tf within it.

Firstly we need to add information about the provider (Here, we will be using AWS Provider). We will also configure AWS credentials, so we could provision resources in the AWS cloud.


You can configure the AWS credentials in the provider section. Here, I am using  Access and Secret keys , Please provide in Access and Secret keys(AWS root user) in  Main.tf Access and Secret keys 

Now that we have set the provider set, we have to initialise Terraform to use it. (This command will download/update the providers).

terraform init
then run
terraform plan - gives view of changes to be deployed
terraform apply - deploys resources to the cloud
After the changes are deployed,

Go to AWS Console and sign in.
Go to Load Balancer under EC2 service.
Select the load balancer that we created and copy the DNS name.
Hit the URL in the browser


user data file: (to run Web server)
#!/bin/bash
sudo yum update -y
sudo yum install -y httpd
sudo systemctl start httpd
sudo systemctl enable httpd
echo "<h1>Hello World from $(hostname -f)</h1>" > /var/www/html/index.html

Terraform destroy
If you want to destroy all the resources created using Terraform in this project, you can use terraform destroy command.
