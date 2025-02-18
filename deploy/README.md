# Procedure to deploy

1- Create a server that have Ansible & Docker installed

2- Add the server to Jenkins 'publish over SSH' section

3- Add files on ./deploy/ansible to Ansible server

4- Create EC2 to be as workstation for eks cluster, attach IAM Role for it, integrate to be accessed from Ansible server

5- On Jenkins job post-build actions -> Copy artifacts \*.war to ansible server
                                     -> Issue commands to apply playbooks
