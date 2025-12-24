## Day 6: Create Elastic IP Using Terraform

## Task: Allocate an Elastic IP using Terraform

You will create an Elastic IP (EIP) named xfusion-eip using Terraform in AWS.

This task uses Amazon Web Services and Terraform (Infrastructure as Code).

<img width="1304" height="664" alt="Screenshot 2025-12-24 193339" src="https://github.com/user-attachments/assets/6a310c80-3ed1-473c-b2fc-665549e0f8f3" />

## Step 1: Open the Terraform Working Directory

In VS Code:

Go to Explorer

Right-click → Open in Integrated Terminal

Run:
```bash
cd /home/bob/terraform
```
## Step 2: Create main.tf

Create only one file named main.tf:
```bash
vi main.tf
```
## Step 3: Add the Required Terraform Code

Copy exactly this content into main.tf:
```bash
provider "aws" {
  region = "us-east-1"
}

resource "aws_eip" "xfusion_eip" {
  tags = {
    Name = "xfusion-eip"
  }
}
```

## What this does

Configures AWS provider in us-east-1

Allocates an Elastic IP

Adds the required Name tag

Save and exit:
```bash
:wq
```
## Step 4: Initialize Terraform
```bash
terraform init
```

✔️ Downloads AWS provider
✔️ Prepares Terraform environment

## Step 5: Validate Configuration (Recommended)
```bash
terraform validate
```

✔️ Ensures syntax and configuration are correct

## Step 6: Apply Terraform Configuration
```bash
terraform apply
```

When prompted, type:
```bash
yes
```
## Step 7: Verify the Result

If successful, you’ll see:

Apply complete! Resources: 1 added, 0 changed, 0 destroyed.


## 🎉 This confirms the Elastic IP xfusion-eip is created successfully.

Optional: Verify via AWS Console

Go to EC2 → Elastic IPs

Check for xfusion-eip

## ✔️ Task Completed

You have successfully allocated an Elastic IP using Terraform following best practices.

If you want, I can also help you:

Attach this EIP to an EC2 instance

Convert this into a LinkedIn post

Add this to a GitHub README

Test Lab Screenshots:-

<img width="1724" height="892" alt="Screenshot 2025-12-24 191953" src="https://github.com/user-attachments/assets/95245561-8937-4f32-9ef6-596c9114517e" />
