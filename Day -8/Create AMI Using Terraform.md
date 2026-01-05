## Day 8: Create AMI Using Terraform

## ✅ What exactly you must do

Use Terraform

Use existing EC2 instance named devops-ec2

Create an AMI

AMI name must be devops-ec2-ami

AMI must reach available state

Modify only main.tf

Terraform directory: /home/bob/terraform

## Step 1: Go to Terraform directory
```bash
cd /home/bob/terraform
ls
```

You must see main.tf.

## Step 2: Open main.tf
```bash
vi main.tf
```

(or use VS Code editor if already open)

## Step 3: Add / Update main.tf with this EXACT content

⚠️ Do not create another .tf file
```bash
provider "aws" {
  region = "us-east-1"
}

# Fetch existing EC2 instance by Name tag
data "aws_instance" "devops_ec2" {
  filter {
    name   = "tag:Name"
    values = ["devops-ec2"]
  }
}

# Create AMI from the existing EC2 instance
resource "aws_ami_from_instance" "devops_ami" {
  name               = "devops-ec2-ami"
  source_instance_id = data.aws_instance.devops_ec2.id

  lifecycle {
    create_before_destroy = true
  }

  tags = {
    Name = "devops-ec2-ami"
  }
}
```
Save & exit
```bash
ESC
```
```bash
:wq
```
Enter

## Step 4: Initialize Terraform (if not already done)
```bash
terraform init
```

✔️ You should see Terraform has been successfully initialized

## Step 5: Validate configuration
```bash
terraform validate
```

✔️ Output must be:

Success! The configuration is valid.

## Step 6: Review what Terraform will create
```bash
terraform plan
```

✔️ You should see:

aws_ami_from_instance.devops_ami will be created

Source instance ID detected automatically

## Step 7: Create the AMI
```bash
terraform apply
```

Type:

yes


✔️ Terraform will:

Snapshot the instance

Create the AMI

Wait until AMI becomes available

## Step 8: Confirm AMI creation (IMPORTANT)

Run:
```bash
terraform show
```

OR (optional AWS CLI check if allowed):

aws ec2 describe-images --owners self --filters "Name=name,Values=devops-ec2-ami"


✔️ AMI state must be:

State: available

✅ Submission checklist (VERY IMPORTANT)

Before submitting, confirm:

✔ AMI name is devops-ec2-ami

✔ AMI is in available state

✔ Used Terraform only

✔ Updated main.tf only

✔ No extra .tf files created

<img width="1669" height="928" alt="Screenshot 2026-01-05 203818" src="https://github.com/user-attachments/assets/c7658276-4399-46a0-86f9-8e6c406784ca" />
