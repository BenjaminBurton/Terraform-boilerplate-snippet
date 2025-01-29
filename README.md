# Terraform AWS VPC & Subnet Setup

## 📌 Overview

This Terraform configuration sets up a VPC (Virtual Private Cloud) and subnets in AWS. It provides a simple and scalable way to define cloud networking resources without manual configuration.

## 📁 Project Structure

```bash
/terraform-aws-vpc
│── main.tf         # Terraform configuration file
│── terraform.json  # VSCode snippet for quick setup
│── README.md       # Project documentation
│── .gitignore      # Ignore Terraform state files
```

## 🚀 Features

✅ Creates an AWS VPC with a custom CIDR block
✅ Deploys multiple subnets in different Availability Zones
✅ Pre-configured Terraform snippet for quick usage in VSCode
✅ Supports manual region selection without using variables

## 🔧 Prerequisites

- Terraform (>= 1.0.0) → Install Terraform
- AWS CLI (>= 2.0.0) → Install AWS CLI
- An AWS account with proper IAM permissions

## ⚡ Usage

## 1️⃣ Clone the Repository

```bash
git clone https://github.com/BenjaminBurton/Terraform-boilerplate-snippet
cd Terraform-boilerplate-snippet
```

## 2️⃣ Initialize Terraform

```bash
terraform init
```

## 3️⃣ Preview Changes

```bash
terraform plan
```

## 4️⃣ Apply Configuration

```bash
terraform apply
```

## 5️⃣ View Outputs (VPC & Subnet IDs)

```bash
terraform output
```

## 📜 Terraform Configuration (main.tf)

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
```

## 🛠 VSCode Terraform Snippet (terraform.json)

The json file is for your snippets, but if you want to use a simple network topology from the example shown in terraform docs [HERE](https://developer.hashicorp.com/terraform/language) then you can find the example in the variables.tf file for your convenience.

## 🛑 Cleanup

To delete all resources, run:

```bash
terraform destroy
```

## 📌 Notes

- Adjust the region and CIDR blocks if needed.
- Use terraform plan to preview changes before applying them.
- Consider using Terraform variables for flexibility in production environments.
