# arruko.packer-ecs

## Packer Build for ECS Images

This repository provides a Packer build script for creating Amazon Machine Images (AMIs) for running custom AWS EC2 Container Service (ECS) Container Instance images. This repository was forked from original repo, modifying project structure in order to use it as an Ansible [role](https://galaxy.ansible.com/arruko/packer-ecs) instead of a ```Make``` script.

## Role Variables

Please refer to the [defaults file](/defaults/main.yml) for an up to date list of input parameters.

## Installation

To install this repository and used it as part of your Ansible project you can simply use the following commands:

```
ansible galaxy install arruko.packer-ecs
```

## Dependencies

This role depends on ```arruko.aws-sts``` role for AWS temporary user session. You can use the following commands to install it:

```
ansible galaxy install arruko.aws-sts
```

## Example Playbook

- hosts: {{ env }}
  roles:
     - role: arruko.packer-ecs
  vars:
    packer_aws_account_id: "YOUR_AWS_ACCOUNT_ID"
    packer_aws_admin_role: "YOUR_AWS_ADMIN_ROLE_NAME"
    packer_aws_sts_region: "YOUR_AWS_REGION"

Run:

```
ansible-playbook playbook.yml -e env=production
```

You must specify ```env``` variable at runtime in order to use this role.

## Errata

No known issues.

## TODO

- Unit Testing with Molecule

## Further Reading

- [Latest Amazon ECS-Optimized AMI](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/ecs-optimized_AMI.html)
- [Packer AMI Builder reference](https://www.packer.io/docs/builders/amazon-ebs.html)
- [Configuring CloudWatch logs](http://docs.aws.amazon.com/AmazonECS/latest/developerguide/using_cloudwatch_logs.html)

## License

This project is licensed under the terms of the [MIT License](/LICENSE)