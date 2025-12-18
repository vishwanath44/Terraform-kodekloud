## Day-5 : Create VPC with IPv6 Using Terraform

## Task: Create an AWS VPC with IPv6 using Terraform
🔹 Objective

Create a VPC named nautilus-vpc in the us-east-1 region with an Amazon-provided IPv6 CIDR block using Terraform.
## Step-by-Step Implementation (Terraform)

## Step 1: Open the Terraform Working Directory
```bash
cd /home/bob/terraform
```
## Step 2: Create main.tf File
```bash
vi main.tf
```
## Step 3: Add the Terraform Configuration

👉 Copy exactly the code below into main.tf:
```bash
provider "aws" {
  region = "us-east-1"
}

resource "aws_vpc" "nautilus_vpc" {
  cidr_block                       = "10.0.0.0/16"
  assign_generated_ipv6_cidr_block = true

  tags = {
    Name = "nautilus-vpc"
  }
}
````

✅ What this does:

Creates a VPC in us-east-1

Enables Amazon-provided IPv6 CIDR

Tags the VPC as nautilus-vpc

## Step 4: Initialize Terraform
```bash
terraform init
```
## Step 5: Validate the Configuration
```bash
terraform validate
```
## Step 6: Preview the Changes
```bash
terraform plan
```
## Step 7: Apply the Configuration
```bash
terraform apply
```

➡️ Type yes when prompted.

## ✅ Expected Result

A new VPC named nautilus-vpc

IPv4 CIDR: 10.0.0.0/16

Amazon-generated IPv6 CIDR block

Region: us-east-1

## Test Lab Screenshot:

<img width="1741" height="996" alt="Screenshot 2025-12-18 230523" src="https://github.com/user-attachments/assets/4cf40bea-da9c-401f-a921-72b4a70977c3" />
