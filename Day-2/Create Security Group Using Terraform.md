## Day 2: Create Security Group Using Terraform

**Task Overview (Add Before Step 1)**

This task uses Terraform (Infrastructure as Code) to provision an AWS Security Group.

The Security Group will be created in the default VPC of the us-east-1 region.

Two inbound rules are required:

HTTP (Port 80) accessible from anywhere.

SSH (Port 22) accessible from anywhere.

An outbound rule is added to allow all traffic, following AWS best practices.

All resources are defined in a single Terraform file (main.tf) as required.

Terraform will manage the lifecycle of this security group in an idempotent manner.

## Step 1: Go to Terraform working directory
```bash
cd /home/bob/terraform
```
## Step 2: Create main.tf (ONLY this file)
```bash
vi main.tf
```

## Paste the entire content below ⬇️
```bash
provider "aws" {
  region = "us-east-1"
}

resource "aws_security_group" "devops_sg" {
  name        = "devops-sg"
  description = "Security group for Nautilus App Servers"
  vpc_id      = data.aws_vpc.default.id

  ingress {
    description = "HTTP"
    from_port   = 80
    to_port     = 80
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }

  ingress {
    description = "SSH"
    from_port   = 22
    to_port     = 22
    protocol    = "tcp"
    cidr_blocks = ["0.0.0.0/0"]
  }

  egress {
    from_port   = 0
    to_port     = 0
    protocol    = "-1"
    cidr_blocks = ["0.0.0.0/0"]
  }
}

data "aws_vpc" "default" {
  default = true
}
```

Save and exit:

:wq

## Step 3: Initialize Terraform
```bash
terraform init
```
## Step 4: Validate configuration (optional but safe)
```bash
terraform validate
```

## Expected:

Success! The configuration is valid.

## Step 5: Apply Terraform
```bash
terraform apply
```

## When prompted:

**Enter a value: yes**

## Step 6: Confirm success

**You should see:**

Apply complete! Resources: 1 added, 0 changed, 0 destroyed.

## ✅ Task Completion Checklist (What KodeKloud checks)

✔ Security group name: devops-sg
✔ Correct description
✔ HTTP (80) inbound from 0.0.0.0/0
✔ SSH (22) inbound from 0.0.0.0/0
✔ Default VPC used
✔ Region: us-east-1
✔ Created using Terraform main.tf only

🎉 You can now confidently mark this task as COMPLETED.


## Test Lab Screenshots:

<img width="1806" height="970" alt="Screenshot 2025-12-15 190958" src="https://github.com/user-attachments/assets/183cf59d-dc24-4536-a7c2-40f375207758" />

<img width="1073" height="955" alt="Screenshot 2025-12-15 191027" src="https://github.com/user-attachments/assets/e1c2fa90-08c6-4e68-9575-4823a67c654f" />

