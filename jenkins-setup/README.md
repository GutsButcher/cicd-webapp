# Terraform 

Pre-requisite:
- Terrafrom installed
- aws credentials
```bash
export AWS_ACCESS_KEY_ID=<>
export AWS_SECRET_ACCESS_KEY=<>
```
Procedure:
```bash
cd terraform
terraform init
terraform apply
```
This should
- Create Ubuntu 20.04 EC2 Instance
- Create SSH key pair on ./terraform/key directory
- Setup needed information on ./ansible directory

# Ansible 
- Ansible installed
```bash
cd ../ansible
ansible-playbook playbook.yml
```

By this you have a configured Jenkins server with credentials printed on screen.

next:
install maven

access Jenkins UI that runs on port 8080 and specify maven & JDK tools paths on Tools settings

Now you can create Maven Jenkins Job
