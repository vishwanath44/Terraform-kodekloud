## Day 7: Create EC2 Instance Using Terraform

## ✅ Task Goal (Quick Summary)

We will use Terraform to create one EC2 instance with:

Name tag: datacenter-ec2

AMI: ami-0c101f26f147fa7fd (Amazon Linux)

Instance type: t2.micro

Key pair: datacenter-kp (RSA – created by Terraform)

Security group: default security group

File: only main.tf

Directory: /home/bob/terraform

## Step 1: Go to Terraform Working Directory
```bash
cd /home/bob/terraform
```
Verify directory:
```bash
pwd
```
## Step 2: Open main.tf
```bash
vi main.tf
```

⚠️ Delete everything inside the file first

## Step 3: Paste this FINAL & CORRECT main.tf

👉 Copy exactly as-is
```bash
provider "aws" {
  region = "us-east-1"
}

# Generate RSA Private Key
resource "tls_private_key" "datacenter_key" {
  algorithm = "RSA"
  rsa_bits  = 2048
}

# Create AWS Key Pair
resource "aws_key_pair" "datacenter_kp" {
  key_name   = "datacenter-kp"
  public_key = tls_private_key.datacenter_key.public_key_openssh
}

# Get Default VPC
data "aws_vpc" "default" {
  default = true
}

# Get Default Security Group
data "aws_security_group" "default" {
  filter {
    name   = "group-name"
    values = ["default"]
  }

  filter {
    name   = "vpc-id"
    values = [data.aws_vpc.default.id]
  }
}

# Create EC2 Instance
resource "aws_instance" "datacenter_ec2" {
  ami                    = "ami-0c101f26f147fa7fd"
  instance_type          = "t2.micro"
  key_name               = aws_key_pair.datacenter_kp.key_name
  vpc_security_group_ids = [data.aws_security_group.default.id]

  tags = {
    Name = "datacenter-ec2"
  }
}
```
## Step 4: Save & Exit
ESC
```bash
:wq
```
ENTER

## Step 5: Initialize Terraform (IMPORTANT)

Because we added tls provider:
```bash
terraform init
```

✅ You should see:

Terraform has been successfully initialized!

## Step 6: Validate Again
```bash
terraform validate
```

✅ Expected output:

Success! The configuration is valid.

## Step 7: Apply (Create EC2)
```bash
terraform apply
```

Type:

yes

## ✅ FINAL SUCCESS MESSAGE (This means PASS)
Apply complete! Resources: 3 added, 0 changed, 0 destroyed.


## Resources:

tls_private_key

aws_key_pair

aws_instance

## 🎯 Task Checklist (All Met)

✔ EC2 Name tag → datacenter-ec2

✔ AMI → ami-0c101f26f147fa7fd

✔ Instance type → t2.micro

✔ RSA key → datacenter-kp

✔ Default security group → attached

✔ Only main.tf used

✔ Terraform best practice

## Test Lab Screenshots:

<img width="1760" height="971" alt="Screenshot 2025-12-28 231919" src="https://github.com/user-attachments/assets/f71e191c-2537-46b5-a942-a517cda82923" />
