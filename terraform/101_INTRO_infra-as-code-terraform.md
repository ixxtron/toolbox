## Creating an AWS EC2 Instance with Terraform (using an HCL file)
```
/ //
/ The provider block tells terraform what platform to build our platform on. 
/ Requiring authentication for the aws account with access & secret key arguments.
/ // /// //// 
provider "aws" {
  access_key  = "ACCESS_KEY"
  secret_key  = "SECRET_KEY"
  region      = "us-east-1"
}


/ //
/ The resource block defines the infrustracture component we're creating.  
/ Each resource type has speficic parameterrequirements.  
/ For example here the resource type of an *aws instance* requires the 
/ parameters: `ami` and `instance_type` there are other parameters we can include but they are optional.
/ // /// ////
/ resource "<provider>_<resource_type>" "name" {
/   config options....
/   key = "value
/   key2 = "another value"
/ }

resource "aws_instance" "example" {
  ami           = "ami-12345a678"
  instance_type = "t2.micro"
}
```

* **HCL** - Harshicorp Configuration Language (delcarative file)
---
### Infrastructure as Code
Infrastructure is described using a high-level configuration syntax. This allows a blueprint of your datacenter to be versioned and treated as you would any other code. Additionally, infrastructure can be shared and re-used.

If you are new to infrastructure as code as a concept, it is the process of managing infrastructure in a file or files rather than manually configuring resources in a user interface. A resource in this instance is any piece of infrastructure in a given environment, such as a virtual machine, security group, network interface, etc.

At a high level, Terraform allows operators to use HCL to author files containing definitions of their desired resources on almost any provider (AWS, GCP, GitHub, Docker, etc) and automates the creation of those resources at the time of apply.

### Workflows
A simple workflow for deployment will follow closely to the steps below. We will go over each of these steps and concepts more in-depth throughout this track, so don't panic if you don't understand the concepts immediately.

1. Scope - Confirm what resources need to be created for a given project.
2. Author - Create the configuration file in HCL based on the scoped parameters
3. Initialize - Run `terraform init` in the project directory with the configuration files. This will download the correct provider plug-ins for the project.
4. Plan & Apply - Run `terraform plan` to verify creation process and then `terraform apply` to create real resources as well as state file that compares future changes in your configuration files to what actually exists in your deployment environment.

### Execution Plans
Terraform has a "planning" step where it generates an execution plan. The execution plan shows what Terraform will do when you call apply. This lets you avoid any surprises when Terraform manipulates infrastructure.


### Resource Graph
Terraform builds a graph of all your resources, and parallelizes the creation and modification of any non-dependent resources. Because of this, Terraform builds infrastructure as efficiently as possible, and operators get insight into dependencies in their infrastructure.

### Change Automation
Complex changesets can be applied to your infrastructure with minimal human interaction. With the previously mentioned execution plan and resource graph, you know exactly what Terraform will change and in what order, avoiding many possible human errors.



### Advantages of Terraform
While many of the current offerings for infrastructure as code may work in your environment, Terraform aims to have a few advantages for operators and organizations of any size.

* Platform Agnostic
* State Management
* Operator Confidence


### Platform Agnostic
In a modern datacenter, you may have several different clouds and platforms to support your various applications. With Terraform, you can manage a heterogenous environment with the same workflow by creating a configuration file to fit the needs of your project or organization.

### State Management
Terraform creates a state file when a project is first initialized. Terraform uses this local state to create plans and make changes to your infrastructure. Prior to any operation, Terraform does a refresh to update the state with the real infrastructure. This means that Terraform state is the source of truth by which configuration changes are measured. If a change is made or a resource is appended to a configuration, Terraform compares those changes with the state file to determine what changes result in a new resource or resource modifications.

### Operator Confidence
The workflow built into Terraform aims to instill confidence in users by promoting easily repeatable operations and a planning phase to allow users to ensure the actions taken by Terraform will not cause disruption in their environment. Upon `terraform apply`, the user will be prompted to review the proposed changes and must affirm the changes or else Terraform will not apply the proposed plan.




