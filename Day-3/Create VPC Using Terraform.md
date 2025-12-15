## Day 3: Create VPC Using Terraform

## Terraform Task: Create a VPC in AWS
 **Task Overview**

Create an AWS VPC using Terraform with the following requirements:

VPC Name: datacenter-vpc

Region: us-east-1

IPv4 CIDR Block: Any valid private range

Terraform Directory: /home/bob/terraform

File to Create: main.tf (do not create any other .tf file)

## Step-by-Step Execution Guide
## Step 1️⃣ Open Terminal

In VS Code

Right-click under EXPLORER

Select Open in Integrated Terminal

## Step 2️⃣ Go to Terraform Directory
```bash
cd /home/bob/terraform
```
## Step 3️⃣ Create main.tf
```bash
vi main.tf
```

Paste the Terraform code shown below and save:
```bash
provider "aws" {
  region = "us-east-1"
}

resource "aws_vpc" "datacenter_vpc" {
  cidr_block = "10.0.0.0/16"

  tags = {
    Name = "datacenter-vpc"
  }
}
```
Press ESC

Type :wq

Press Enter

## Step 4️⃣ Initialize Terraform
```bash
terraform init
```

✅ This downloads the AWS provider.

## Step 5️⃣ Validate Configuration (Optional but Recommended)
```bash
terraform validate
```
## Step 6️⃣ Review the Execution Plan
```bash
terraform plan
```
## Step 7️⃣ Apply Terraform Configuration
```bash
terraform apply
```
Type **yes** when prompte

## ✅ Expected Result

A VPC named datacenter-vpc is created in us-east-1

Terraform output ends with:

Apply complete! Resources: 1 added, 0 changed, 0 destroyed.

## Test Lab Screenshots: 

<img width="1740" height="924" alt="Screenshot 2025-12-15 215652" src="https://github.com/user-attachments/assets/b6a5f2aa-18e5-419c-a4dc-970f6d1480b4" />

<img width="1757" height="949" alt="Screenshot 2025-12-15 215614" src="https://github.com/user-attachments/assets/bc2b1b88-dbb6-4364-84d5-9557e71d8c60" />

