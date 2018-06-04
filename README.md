
# About this playbook

This playbook builds a docker image containing sinatra-app and uploads it onto AWS ECR.
An ECS Task definition is created and then the ECS service started.

All the tasks are split into 3 distincts playbooks `build_image` , `infra` and `launch_app`.



## Pre-requisites

On the ansible control machine:
- install (ansible)[http://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#running-from-source] 
- install docker locally (used to build the Docker image) and ensure docker daemon is running
- git should also be installed.
- python >= 2.6
- boto ( used by ansible module)
- boto3 ( used by ansible module)
- botocore ( used by ansible module)
- json( used by ansible module)
- aws cli 

## Before running the playbook
- Double check that vars in group_vars/all are correctly set to match your desired config



- Make sure to set your AWS credentials in env vars:
```
export AWS_ACCESS_KEY_ID='abc'
export AWS_SECRET_ACCESS_KEY='abc'
```

so that Ansible can use those credentials to query AWS API


## Run the playbook

Go at the root folder and run the command below:
```
ansible-playbook -vvvv  site.yml
```

### Run only specific play
If - for example- you only want to run infra play:`

```
ansible-playbook -vvvv --extra-vars "@some_file.yml" infra.yml
```
