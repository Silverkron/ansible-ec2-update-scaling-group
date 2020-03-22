# How to update your Scaling Group on AWS

I use Ansible to deploy my applications on AWS. It's perfect to move my code on an EC2 instance with zero downtime but complicatand I just completed this configuration to update all instances on my scaling group.
So, my normal workflow is:

- deploy my tested software on the staging environment (an EC2 instance)
- create an AMI image from Staging 
- create a new launcher with this new AMI image
- update the scaling group of production

I will show you in this repository how to deploy on production environment starting from the staging

## How to start

* Install [Python](https://www.python.org/downloads/)
* Install [pip](https://pip.pypa.io/en/stable/installing/) 
* Install [Ansible](https://www.ansible.com/) with `sudo apt-get install ansible` or `brew install ansible`
* Install [AWS Cli](https://aws.amazon.com/it/cli/) with `pip install awscli`
* Install [Boto](https://github.com/boto/boto) with `pip install python-boto` (Ansible uses Boto to interact with AWS)

## Set your AWS credentials

Now you need to place your AWS access key and secret into `~/.aws/credentials`. For example:
```bash
[default]
aws_access_key_id = <access key>
aws_secret_access_key = <secret key>
```

## Set right group_vars with AWS parameters

you can set the right configuration on the group_vars file to build the right AMI, create a launcher and update the scaling group. 
So, you should edit `group_vars/all/aws_parameters.yaml`.

## Are you ready?

Now we are ready to start your first deploy 🚀🚀🚀. Use:
```bash
ansible-playbook deploy.yml
```

That's all! Please, send me any message to improve this repo 💪🏻
