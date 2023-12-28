---
title: "Automating AWS EC2 Management with Ansible"
datePublished: Thu Dec 28 2023 06:03:30 GMT+0000 (Coordinated Universal Time)
cuid: clqosu5e9000708jm7g53eddy
slug: automating-aws-ec2-management-with-ansible
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1703743325038/18312e01-9e35-44e9-97ac-4347a706bca9.gif
tags: aws, devops, 90daysofdevops, ansible-playbook

---

## **Introduction**

In today's rapidly evolving cloud computing landscape, automation is key to efficiently manage resources. AWS (Amazon Web Services) provides powerful cloud infrastructure, and Ansible, an open-source automation tool, can simplify the management of EC2 instances. This blog post will guide you through using Ansible to automate the creation, deletion, and stopping of EC2 instances on AWS.

## **Prerequisites**

Before you begin, make sure you have the following:

* AWS account with access key and secret key
    
* Ansible installed on your local machine
    
* AWS CLI installed for Ansible AWS module support
    

## **Install AWS CLI, Ansible, and Aws Module support.**

To interact with AWS EC2 services requires AWS CLI & Ansible. Here I installed in in my Local VM Kali Linux, not in the ec2 instance. By installing the following commands.

```bash
$ sudo apt update -y
$ sudo apt install ansible -y
$ curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
$ unzip awscliv2.zip
$ sudo ./aws/install
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703736696917/95c10ccf-3056-4758-8858-2d20555cc86d.png align="center")

## **Setting Up AWS Credentials**

To interact with AWS services, Ansible requires AWS credentials. For these, I created a user in AWS in the name of "Ansible-ec2" for generating the AWS Access key & Secret key for accessing the AWS ec2 from Kali Linux of vm using the Ansible tool.

For the "ansible-ec2" user I have given permission Ec2FullAccess.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703737427518/3273805b-8199-4d54-aab3-2f4f75d34b95.png align="center")

After that, i generated the Access key and Secret key

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703737512523/1f8e43e1-906d-43c0-91c3-4a51dcb22e72.png align="center")

Now Configure with generated aws user access key and secret key. Enter your access key, secret key, region, and output format as prompted.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703737672533/45acf5ce-5071-4549-96ab-babb27ffb3bb.png align="center")

Then install the Aws support module.

You can install it using the following command:

```bash
$ansible-galaxy collection install community.aws
```

## **Ansible Playbook for EC2 Instance Creation**

Certainly! Below is a template for a blog post on using Ansible to create, delete, and stop EC2 instances on AWS. Feel free to customize it based on your specific preferences and details.

---

# **Title: Automating AWS EC2 Management with Ansible**

## **Introduction**

In today's rapidly evolving cloud computing landscape, automation is key to efficiently manage resources. AWS (Amazon Web Services) provides powerful cloud infrastructure, and Ansible, an open-source automation tool, can simplify the management of EC2 instances. This blog post will guide you through using Ansible to automate the creation, deletion, and stopping of EC2 instances on AWS.

## **Prerequisites**

Before you begin, make sure you have the following:

* AWS account with access key and secret key
    
* Ansible installed on your local machine
    
* AWS CLI installed for Ansible AWS module support
    

## **Setting Up AWS Credentials**

To interact with AWS services, Ansible requires AWS credentials. Set up your credentials using the AWS CLI:

```yaml
bashCopy codeaws configure
```

Enter your access key, secret key, region, and output format as prompted.

## **Ansible Playbook for EC2 Instance Creation**

Create an Ansible playbook (e.g., `create_ec2.yml`) for launching an EC2 instance:

```yaml
---
- name: Create EC2 Instance
  hosts: localhost
  gather_facts: False
  tasks:
    - name: Launch EC2 Instance
      community.aws.ec2_instance:
        key_name: ashok #you have to create key pair and copy and paste in ansible-playbook directory
        instance_type: t2.micro
        image: ami-0a0f1259dd1c90938
        region: ap-south-1
        count: 1
        state: present
        tags:
          Name: ec2_test
      register: ec2
    - name: Print EC2 instance information
      debug:
        var: ec2
```

Before running the playbook, you should create the keypair and download or move to ansible playbook directory.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703738524576/adadf1e7-c072-4976-b7f4-a8a1fb7cf3cb.png align="center")

Execute the playbooks using the following commands:

```bash
$ansible-playbook ec2_create.yaml
```

## **Ansible Playbook for Stopping EC2 Instance**

For stopping an EC2 instance without terminating it, create a playbook (e.g., `stop_ec2.yml`):

```yaml
---
- name: Stop EC2 instance on AWS using Ansible playbook
  hosts: localhost
  tasks:
    - name: Get instance information
      community.aws.ec2_instance_info:
        region: ap-south-1
        filters:
          "tag:Name": "ec2_test"

    - name: Stop EC2 instance
      community.aws.ec2_instance:
        state: stopped
        region: ap-south-1
```

Execute the playbooks using the following commands:

```bash
$ansible-playbook ec2_stop.yaml
```

## **Ansible Playbook for EC2 Instance Deletion**

Create another Ansible playbook (e.g., `delete_ec2.yml`) for terminating an EC2 instance:

```yaml
---
- name: Terminate EC2 instance on AWS using Ansible playbook
  hosts: localhost
  tasks:
    - name: Get instance information
      community.aws.ec2_instance_info:
        region: ap-south-1
        filters:
          "tag:Name": "ec2_test"

    - name: terminate EC2 instance
      community.aws.ec2_instance:
        state: absent
        region: ap-south-1
```

Execute the playbooks using the following commands:

```bash
$ansible-playbook ec2_terminate.yaml
```

## **Conclusion**

Automating EC2 management with Ansible streamlines repetitive tasks increases efficiency, and ensures consistency across your AWS infrastructure. As you explore more advanced Ansible features, you can further enhance your AWS automation capabilities.

I hope you people like this blog.

1. ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695627131885/d3899b2c-dd76-4ef9-8230-870760b10aac.gif align="left")
    
    If you like this blog please follow these below Links, You will get more content like this in that links.
    
    WhatsApp Group:- [https://chat.whatsapp.com/Ii2xKz9vuW93AWt07m4AYj](https://chat.whatsapp.com/Ii2xKz9vuW93AWt07m4AYj)
    
    Telegram:- [https://t.me/ExplorewithAshok](https://t.me/ExplorewithAshok)
    
    LinkedIn: [https://www.linkedin.com/in/ashok-sana](https://www.linkedin.com/in/ashok-sana)
    
    Instagram:- [https://instagram.com/explorewithashok?igshid=OGQ5ZDc2ODk2ZA==](https://instagram.com/explorewithashok?igshid=OGQ5ZDc2ODk2ZA==)
    
    Linktree:- [https://linktr.ee/ashoksana](https://linktr.ee/ashoksana)