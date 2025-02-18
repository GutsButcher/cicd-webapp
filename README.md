# CICD Webapp Project

A comprehensive CI/CD pipeline implementation for deploying a Java web application on Amazon EKS using Jenkins, Terraform, and Ansible.

## Project Overview

This project sets up an end-to-end CI/CD pipeline with the following components:
- Jenkins server provisioned using Terraform and configured with Ansible
- Docker containerization of the Java web application
- Kubernetes deployment on Amazon EKS
- Automated build and deployment process

## Project Structure

```
.
├── README.md                 # Main project documentation
├── deploy/                   # Deployment configurations
│   ├── ansible/             # Ansible playbooks for deployment
│   ├── eks_cluster.md       # EKS cluster setup guide
│   └── README.md            # Deployment instructions
└── jenkins-setup/           # Jenkins infrastructure
    ├── ansible/             # Ansible configs for Jenkins
    ├── jenkins-setup.md     # Jenkins setup guide
    └── terraform/           # Terraform configurations
```

## Prerequisites

- AWS Account with appropriate permissions
- Terraform >= 0.12
- Ansible >= 2.9
- AWS CLI configured
- Basic knowledge of Jenkins, Docker, and Kubernetes

## Quick Start

1. Set up Jenkins server:
   ```bash
   cd jenkins-setup/terraform
   terraform init && terraform apply
   cd ../ansible
   ansible-playbook playbook.yml
   ```

2. Configure Jenkins:
   - Access Jenkins UI on port 8080
   - Configure Maven and JDK tools
   - Set up required plugins

3. Deploy application:
   - Follow instructions in `deploy/README.md`
   - Set up EKS cluster using guide in `deploy/eks_cluster.md`

## Detailed Documentation

- [Jenkins Setup Guide](jenkins-setup/jenkins-setup.md)
- [Deployment Guide](deploy/README.md)
- [EKS Cluster Setup](deploy/eks_cluster.md)

## Jenkins Configuration

The Jenkins server is configured with:
- Maven integration
- Docker build capabilities
- Kubernetes deployment tools
- SSH publishing functionality

## Deployment Process

The deployment process includes:
1. Building Java application
2. Creating Docker image
3. Pushing to container registry
4. Deploying to EKS cluster


