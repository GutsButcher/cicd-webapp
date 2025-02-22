# Amazon EKS Cluster Setup Guide

A comprehensive guide for setting up a Kubernetes cluster on Amazon EKS.

## Prerequisites

- EC2 instance for EKS management
- AWS CLI (latest version)
- IAM permissions for EKS

## Installation Steps

### 1. Install kubectl

```bash
curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.21.2/2021-07-05/bin/linux/amd64/kubectl
chmod +x ./kubectl
sudo mv ./kubectl /usr/local/bin 
kubectl version --short --client
```

### 2. Install eksctl

```bash
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp
sudo mv /tmp/eksctl /usr/local/bin
eksctl version
```

### 3. IAM Configuration

Required permissions:
- IAM
- EC2
- CloudFormation

Reference: [Minimum IAM Policies](https://eksctl.io/usage/minimum-iam-policies/)

### 4. Cluster Creation

```bash
eksctl create cluster \
  --name k8s-cluster \
  --region us-east-1 \
  --node-type t2.small \
  --nodes-min 2 \
  --nodes-max 2 \
  --zones us-east-1a,us-east-1b
```

Note: t2.micro instances are insufficient for production workloads.

### 5. Cluster Management

Delete cluster:
```bash
sudo eksctl delete cluster k8s-cluster --region us-east-1 --force
```

Verify cluster:
```bash
kubectl get nodes
```

## Additional Resources

- [Official AWS EKS Documentation](https://docs.aws.amazon.com/eks/latest/userguide/getting-started-eksctl.html)
- [eksctl Documentation](https://eksctl.io/)
