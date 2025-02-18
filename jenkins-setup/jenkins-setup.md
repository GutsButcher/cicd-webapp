# Jenkins Server Setup Guide

This guide walks through setting up a Jenkins server using Terraform for infrastructure provisioning and Ansible for configuration management.

## Prerequisites

- Terraform installed (>= 0.12)
- Ansible installed (>= 2.9)
- AWS credentials configured

### AWS Credentials Setup

```bash
export AWS_ACCESS_KEY_ID=<your-access-key>
export AWS_SECRET_ACCESS_KEY=<your-secret-key>
```

## Infrastructure Provisioning with Terraform

Navigate to the Terraform directory and initialize:

```bash
cd terraform
terraform init
terraform apply
```

This will:
- Launch an Ubuntu 20.04 EC2 instance
- Generate SSH key pair in `./terraform/key` directory
- Configure necessary files in `./ansible` directory

## Jenkins Configuration with Ansible

Deploy Jenkins and required plugins:

```bash
cd ../ansible
ansible-playbook playbook.yml
```

### Post-Installation Setup

1. Access Jenkins UI:
   - Navigate to `http://<server-ip>:8080`
   - Login with credentials displayed in Ansible output

2. Configure Build Tools:
   - Go to "Manage Jenkins" → "Global Tool Configuration"
   - Set up Maven and JDK paths
   - Configure any additional required tools

3. Verify Installation:
   - Create a test Maven job
   - Run a build to ensure proper configuration