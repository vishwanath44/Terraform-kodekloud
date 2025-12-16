## Day 4: Create VPC with CIDR Using Terraform

## Task Goal (Quick Summary)

## Create an AWS VPC using Terraform with:

Name: devops-vpc

Region: us-east-1

CIDR: 192.168.0.0/24

Terraform directory: /home/bob/terraform

File name: main.tf (only this file)

## Terraform – Create AWS VPC (devops-vpc)

## Step 1: Go to Terraform working directory
```bash
cd /home/bob/terraform
```
## Step 2: Create main.tf
```bash
vi main.tf
```
## Step 3: Add Terraform configuration
```bash
provider "aws" {
  region = "us-east-1"
}

resource "aws_vpc" "devops_vpc" {
  cidr_block = "192.168.0.0/24"

  tags = {
    Name = "devops-vpc"
  }
}
```

Save and exit:

**ESC :wq**

## Step 4: Initialize Terraform
```bash
terraform init
```
## Step 5: Validate configuration
```bash
terraform validate
```

## Expected output:

Success! The configuration is valid.

## Step 6: Apply Terraform configuration
```bash
terraform apply
```

When prompted:

Do you want to perform these actions?


## Type:

yes

## Step 7: Verify VPC creation
```bash
terraform state list
```

## Expected:

aws_vpc.devops_vpc

## Lab Test Screenshots:

<img width="1771" height="985" alt="Screenshot 2025-12-16 225552" src="https://github.com/user-attachments/assets/252d333b-bce8-43f5-9645-8e7ab5ab41a5" />
