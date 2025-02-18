# Deployment Guide

This guide covers the process of setting up the deployment environment and configuring Jenkins for automated deployments.

## Prerequisites

- Ansible server with Docker installed
- Jenkins server configured with "Publish over SSH" plugin
- AWS account with EKS permissions

## Setup Steps

1. Configure Deployment Server
   - Install Ansible and Docker
   - Verify connectivity from Jenkins server

2. Jenkins SSH Configuration
   - Navigate to "Manage Jenkins" → "Configure System"
   - Add deployment server in "Publish over SSH" section
   - Test connection

3. Deployment Files Setup
   - Copy contents of `./deploy/ansible` to Ansible server
   - Verify file permissions and ownership

4. EKS Workstation Setup
   - Launch EC2 instance for EKS management
   - Configure IAM role with EKS permissions
   - Set up SSH access from Ansible server
   - Follow [EKS Cluster Setup Guide](eks_cluster.md)

5. Jenkins Job Configuration
   - Create new Maven job
   - Configure SCM: `https://github.com/yankils/hello-world.git`
   - Add build steps:
     ```bash
     # Maven build commands here
     ```
   - Configure post-build actions:
     - Copy: `webapp/target/*.war`
     - Remove prefix: `webapp/target`
     - Execute Ansible playbooks:
       ```bash
       ansible-playbook docker-build.yml
       ansible-playbook k8s-build.yml
       ```