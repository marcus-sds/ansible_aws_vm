# ansible_aws_vm

## login to ansible installed container or install ansible

- login to ansible container

    - install docker
   
    - docker pull

- install anisble manually

    - pip install -r requirements.txt

## Creating Several vms with AWS

### Procedure

- clone repository

    git clone https://github.com/marcus-sds/ansible_aws_vm.git
    cd ansible_aws_vm

- change value

    vi ./group_vars/all.yml
    vi aws_ec2.yml

- run script

    bash ./example
