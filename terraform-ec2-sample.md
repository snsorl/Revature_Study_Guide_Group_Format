# Sample AWS EC2 Instance Using Terraform

## Project structure

``` text
terraform-ec2/
├── main.tf
├── variables.tf
├── outputs.tf
└── terraform.tfvars
```

## `main.tf`

``` hcl
terraform {
  required_providers {
    aws = {
      source = "hashicorp/aws"
    }
  }

  required_version = ">= 1.5.0"
}

provider "aws" {
  region = var.aws_region
}

resource "aws_instance" "example" {
  ami           = var.ami_id
  instance_type = var.instance_type

  tags = {
    Name = "terraform-ec2"
  }
}
```

## `variables.tf`

``` hcl
variable "aws_region" {
  description = "AWS region"
  type        = string
  default     = "ap-south-1"
}

variable "ami_id" {
  description = "AMI ID for the EC2 instance"
  type        = string
}

variable "instance_type" {
  description = "EC2 instance type"
  type        = string
  default     = "t3.micro"
}
```

## `outputs.tf`

``` hcl
output "instance_id" {
  description = "ID of the EC2 instance"
  value       = aws_instance.example.id
}

output "public_ip" {
  description = "Public IP address"
  value       = aws_instance.example.public_ip
}
```

## `terraform.tfvars`

Replace the AMI ID with an AMI that exists in your selected AWS region.

``` hcl
aws_region    = "ap-south-1"
ami_id        = "ami-xxxxxxxxxxxxxxxxx"
instance_type = "t3.micro"
```

## Run Terraform

Initialize the Terraform project:

``` bash
terraform init
```

Preview the infrastructure changes:

``` bash
terraform plan
```

Create the EC2 instance:

``` bash
terraform apply
```

When prompted, enter:

``` text
yes
```

## Destroy the EC2 instance

When you no longer need the instance:

``` bash
terraform destroy
```

## Notes

-   The example uses the AWS Mumbai region (`ap-south-1`) by default.
-   The AMI ID must be valid for the selected AWS region.
-   This is a minimal example and relies on AWS's default networking
    configuration.
-   For a more complete Terraform setup, you can create the VPC, subnet,
    security group, and EC2 instance entirely with Terraform.
-   Do not commit `terraform.tfstate` or sensitive Terraform variable
    files containing secrets to Git.
