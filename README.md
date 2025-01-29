# Terraform-boilerplate snippet

```bash
terraform {
  required_providers {
    aws = {
      source  = "hashicorp/aws"
      version = "~> 1.0.4"
    }
  }
}

provider "aws" {
  region = "us-east-1"
}

resource "aws_vpc" "main" {
  cidr_block = "10.1.0.0/16"
}

resource "aws_subnet" "subnet_a" {
  availability_zone = "us-east-1a"
  vpc_id           = aws_vpc.main.id
  cidr_block       = "10.1.1.0/24"
}

resource "aws_subnet" "subnet_b" {
  availability_zone = "us-east-1b"
  vpc_id           = aws_vpc.main.id
  cidr_block       = "10.1.2.0/24"
}

output "vpc_id" {
  description = "The ID of the created VPC"
  value       = aws_vpc.main.id
}

output "subnet_ids" {
  description = "The IDs of the created subnets"
  value       = [aws_subnet.subnet_a.id, aws_subnet.subnet_b.id]
}
```
