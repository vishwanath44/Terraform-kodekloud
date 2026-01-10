## Day 9: Create EBS Volume Using Terraform

# Step-by-Step Correct Solution
## Step 1: Go to Terraform working directory

Open terminal and run:
```bash
cd /home/bob/terraform
```

Check directory is empty or ready:
```bash
ls
```
## Step 2: Create main.tf file
```bash
vi main.tf
```

Press i to enter insert mode and paste this exact content:
```bash
provider "aws" {
  region = "us-east-1"
}

resource "aws_ebs_volume" "xfusion_volume" {
  availability_zone = "us-east-1a"
  size              = 2
  type              = "gp3"

  tags = {
    Name = "xfusion-volume"
  }
}
```

Save and exit:

ESC
:wq

## Step 3: Initialize Terraform
```bash
terraform init
```

You should see:

Terraform has been successfully initialized!

## Step 4: Validate configuration
```bash
terraform validate
```

Expected output:

Success! The configuration is valid.

## Step 5: Create execution plan
```bash
terraform plan
```

Check that it shows:

+ aws_ebs_volume.xfusion_volume

## Step 6: Apply Terraform
```bash
terraform apply
```

Type:
```bash
yes
```

Wait until you see:

Apply complete! Resources: 1 added.

✅ Final Verification (Optional but recommended)
```bash
terraform state list
```

You should see:

aws_ebs_volume.xfusion_volume

🎯 Task Completed Successfully

Your EBS volume:

Name: xfusion-volume

Type: gp3

Size: 2 GiB

Region: us-east-1

## Test Lab Screenshot: 

<img width="1754" height="958" alt="Screenshot 2026-01-10 144446" src="https://github.com/user-attachments/assets/187ef6a4-0fbe-490b-ab2b-a4071b374332" />
