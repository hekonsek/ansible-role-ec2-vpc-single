# Ansible Role - EC2 VPC with single public subnetwork

Provisions EC2 VPN with a single public subnetwork. It ensures that:
- EC2 VPC is created 
- EC2 Internet Gateway is created
- single public subnetwork is created and assigned to VPC and Internet Gateway

## Compatibility

This playbook has been tested against Fedora 27.

## Requirements

Keep in mind that Ansible EC2 module requires you to have Boto installed: 

    sudo pip install -U boto

You can specify AWS credentials either in Boto file (for example `~/.boto`) or using environment variables:
    
    AWS_ACCESS_KEY_ID='yourKeyId' AWS_SECRET_ACCESS_KEY='yourSecretKey' ansible-playbook aws.yml

## Installation 

    ansible-galaxy install hekonsek.fedora-ec2-vpc-single,0.0

## Role variables

- `vpc_name` - **Required** VPC name. It is also used as prefix for names of subnet, internet gateway and route table.
- `region` - AWS region to use. Default region is `us-east-1` i.e. the cheapest one.

## Example playbook

```
- hosts: localhost
  connection: local
  gather_facts: false
  roles:
    - { role: hekonsek.fedora-ec2,0.11 }
```

## License

Apache 2.0
