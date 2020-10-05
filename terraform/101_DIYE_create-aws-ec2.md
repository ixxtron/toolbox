# Step-by-step examples...

## Configuration
The set of files used to describe infrastructure in Terraform is simply known as a Terraform configuration. We're going to write our first configuration now to launch a single VM instance.

The format of the configuration files is documented here. We recommend using JSON for creating configuration files.

Create a configuration an instance.tf file with your favourite editor like vim, nano etc.:

## Create an AWS EC2 with Terraform

### 1. Declaring your terraform `(.tf)` file
Here, replace the access_key and secret_access with your AWS IAM user credentials with enough permissions attached. You can go to IAM console on AWS
```
provider "aws" {
  access_key = "XuserAWsACCESS_KEY_HERE"
  secret_key = "XuserAWsSECRET_KEY_HERE"
  region     = "us-east-1"
}

resource "aws_instance" "example" {
  ami           = "ami-2757f631"
  instance_type = "t2.micro"
}
```
- Note that you must have this file in a self-contained directory such as `terraform101/myawsec2.tf

### 2. Initializing the working directory for terraform
`terraform init`
- "The terraform init command is used to initialize a working directory containing Terraform configuration files. This is the first command that should be run after writing a new Terraform configuration or cloning an existing one from version control. It is safe to run this command multiple times."

### 3. Provisioning the Amazon EC2
`terraform apply`
- Verify that your instance did indeed get provisioned by checking the AWS Management Console

## Destroy resources
### 1. Terminating all resources with terraform
`terraform destory`
- You're done!
