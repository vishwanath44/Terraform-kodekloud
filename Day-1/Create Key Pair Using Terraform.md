## Day 1: Create Key Pair Using Terraform

## ✅ Task Goal

**Create an AWS key pair using Terraform**

Key name: datacenter-kp

Type: RSA

Private key saved at: /home/bob/datacenter-kp.pem

Terraform directory: /home/bob/terraform

File: main.tf only

## Step 1: Open terminal

In VS Code → Right-click Explorer → Open in Integrated Terminal
```bash
cd /home/bob/terraform
```
## Step 2: Create main.tf
```bash
vi main.tf
```

## Paste this exact content:
```bash
resource "tls_private_key" "datacenter" {
  algorithm = "RSA"
  rsa_bits  = 2048
}

resource "aws_key_pair" "datacenter_kp" {
  key_name   = "datacenter-kp"
  public_key = tls_private_key.datacenter.public_key_openssh
}

resource "local_file" "private_key" {
  content         = tls_private_key.datacenter.private_key_pem
  filename        = "/home/bob/datacenter-kp.pem"
  file_permission = "0400"
}
```

Save and exit (:wq).

## Step 3: Initialize Terraform
```bash
terraform init
```
## Step 4: Apply configuration
```bash
terraform apply -auto-approve
```
## Step 5: Verify
```bash
ls -l /home/bob/datacenter-kp.pem
```

**File should exist with read-only permissions.**

✅ Task Completed

✔ Key pair created

✔ RSA type used

✔ Private key saved correctly

✔ Only main.tf used

## Test Lab Screenshots:-

<img width="526" height="394" alt="Screenshot 2025-12-14 194114" src="https://github.com/user-attachments/assets/1dee0ab0-6088-4fe9-b1a7-f5b10aacfaa5" />  
<img width="1006" height="914" alt="Screenshot 2025-12-14 194123" src="https://github.com/user-attachments/assets/436463b3-5787-4b94-953f-67ad0644c78d" />
<img width="1700" height="900" alt="Screenshot 2025-12-14 194147" src="https://github.com/user-attachments/assets/ff19710e-e172-44dd-91cd-8fb720b653d4" />
<img width="1050" height="915" alt="Screenshot 2025-12-14 194211" src="https://github.com/user-attachments/assets/b33d643c-0c37-4b59-a640-f5c0093facc2" />
<img width="1033" height="979" alt="Screenshot 2025-12-14 194220" src="https://github.com/user-attachments/assets/8dfa60f1-46f0-4330-a274-63e96895c112" />




