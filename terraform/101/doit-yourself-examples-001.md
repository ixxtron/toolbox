# Step-by-step examples...

## create new aws instance
1. The 'awsinstance-sample1.tf' configuration code file must be in its own directory `(i.e. terraform-aws-instance/example1instance.tf)`

2. Open the `.tf` file with you favorite code editor and include the following
```
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 2.70"
    }
  }
}

provider "aws" {
  profile = "default"
  region  = "us-west-2"
}

resource "aws_instance" "example" {
  ami           = "ami-830c94e3"
  instance_type = "t2.micro"
}
```
