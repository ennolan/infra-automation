# Immutable Infrastructure Automation with Packer, Ansible, Terraform and GitHub Actions

![image](https://github.com/ennolan/infra-automation/blob/main/diagram.png)

# Introduction
This project leverages the power of Packer, Ansible, Terraform, and GitHub Actions to automate the creation of an immutable infrastructure. Immutable infrastructure is a model where servers, once deployed, are never modified. Instead, changes are made by deploying new servers built from a common image. Immutable infrastructure is a very popular approach in modern cloud application environments.

# Prerequisites
1.	**Local machine setup**: Install and configure Git, Terraform, and vscode. 
2.	**IAM Role**: Create a role in AWS IAM, with necessary permissions for Packer. 
3.	**GitHub repository secrets**: You need to configure valid credentials. 
4.	**Project structure**: Arrange your project directories and files.

# Project Walkthrough
**Packer**: Packer is used to create identical machine images for multiple platforms. It starts with a base image, adds server software, and application code, then converts it into an image. This ensures that we’re deploying the exact same image, regardless of when we deploy it.

**Ansible**: Ansible simplifies configuration management and task automation. It applies server-specific configurations on the base image during the baking process.

**Terraform**: Terraform creates and manages your infrastructure resources like VPCs, subnets, security groups, and instances. Instead of modifying existing instances, it creates new instances with the updated configuration when needed.

**GitHub Actions**: GitHub Actions automates the entire process, enhancing efficiency. The [workflow](https://github.com/ennolan/infra-automation/blob/main/.github/workflows/packer-ansible-terraform.yml) consists of two jobs: packer-ansible and Terraform-commands. The packer-ansible job sets up Packer and Ansible, and builds an Amazon Machine Image (AMI). The Terraform-commands job sets up Terraform and applies a Terraform plan to provision infrastructure.
