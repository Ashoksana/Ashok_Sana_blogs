---
title: "Automated Deployment of Nginx Application to Kubernetes Cluster using Docker, Ansible,Github, and AWS ECR"
datePublished: Mon Jun 26 2023 07:31:35 GMT+0000 (Coordinated Universal Time)
cuid: cljcjitid000209l19u2ka794
slug: automated-deployment-of-nginx-application-to-kubernetes-cluster-using-docker-ansiblegithub-and-aws-ecr
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1687764492362/a917dbd1-76be-4ffc-b561-ed38ef5430d4.png
tags: docker, github, aws-cli, ansible-playbook, k8scluster

---

### **Table of Contents:**

1. Understanding the Technologies
    
    * Docker: Containerization for Consistent Environments
        
    * Kubernetes: Orchestrating Containers at Scale(kops)
        
    * Ansible: Automating Infrastructure Configuration
        
    * AWS Elastic Container Registry (ECR): Secure Container Image Storage
        
2. Building and Pushing the Docker Image to AWS ECR
    
    * Setting up Docker CLI
        
    * Creating a Dockerfile for Nginx Application
        
    * Building the Docker Image
        
    * Pushing the Docker Image to AWS ECR
        
3. Creating Ansible Role for Kubernetes Deployment
    
    * Defining the Role Structure
        
    * Writing Ansible Tasks for Deployment
        
    * Configuring Kubernetes Resources (Pods, Services, etc.)
        
    * Applying the Ansible Role to the Kubernetes Cluster
        
4. Creating Ansible Playbook for Nginx Application Deployment
    
    * Defining the Playbook Structure
        
    * Including the Kubernetes Deployment Role
        
    * Specifying Variables and Configuration
        
    * Executing the Playbook
        
5. Verifying the Deployment
    
    * Accessing the Nginx Website
        
    * Testing Load Balancing and Scalability
        
    * Monitoring the Cluster with Kubernetes Tools
        

Step-1

LAUNCH INSTANCE WITH T2.MICRO, 10 GB SSD, sg-ssh&all.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687754151108/64e19b47-06b2-4c79-8a68-ad7eff9b2d4c.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687754168137/2b375a44-e79d-48b4-ab5c-9ab736184a4e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687754182724/f6c726b0-fa50-4fe1-8e98-4a62b51401c7.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687754211972/9e21c243-6685-4c56-adea-32255733bdba.png align="center")

Now connect this workspace ec2 instance to the terminal. After connect the ec2 then update the packages

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687754263227/7120d10c-a883-4320-b198-9a21dfa89341.png align="center")

Now create an IAM user of CLI, generate an access key & secret key, and give admin access. Save the access key and secret key in notepad for further use.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687754612199/5c0bb7ef-72b8-49f0-9216-1cfb8ce38306.png align="center")

Now install Aws cli.

`curl "`[`https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip`](https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip)`" -o "`[`awscliv2.zip`](http://awscliv2.zip)`"`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687754744641/fbbbdeb6-0292-4eda-a979-8013808add25.png align="center")

`sudo apt-get install unzip`

`unzip` [`awscliv2.zip`](http://awscliv2.zip)

`sudo ./aws/install`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687754845082/221bf0d7-6e46-4f08-9389-dad862d3c2df.png align="center")

After installation of AWS CLI to set a path:

`sudo vim .bashrc`

`export PATH=$PATH:/usr/local/bin/`

`source .bashrc`

Now check the version

`aws --version`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687756081663/c9a29a33-da3a-4e4e-bead-16b81d5f8ae3.png align="center")

Step-2

Install Kops and Kubectl for creating clusters of k8s (master and node) from the workspace ec2 instance.

`sudo curl -LO "`\[`https://dl.k8s.io/release/$(curl`\](https://dl.k8s.io/release/$(curl) `-L -s` [`https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl`](https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl)`"`

`sudo wget` [`https://github.com/kubernetes/kops/releases/download/v1.24.1/kops-linux-amd64`](https://github.com/kubernetes/kops/releases/download/v1.24.1/kops-linux-amd64)

Change Permissions: `sudo chmod +x kops-linux-amd64 kubectl`

Move Files: `sudo mv kubectl /usr/local/bin/kubectl`

Move Files: `sudo mv kops-linux-amd64 /usr/local/bin/kops`

`kubectl version kops version`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687756352289/28cdf161-c08c-433b-9a8e-cad79c9ca84a.png align="center")

Step-3

Configure AWS CLI in workspace ec2 instance for creating k8s clusters and etcd of s3 bucket using kops commands.

First, configure aws cli:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687756505548/42c1ce2b-3eba-44df-9b97-776ad09e6a27.png align="center")

Now create an infrastructure of k8s cluster.

first, create etcd of k8s in aws using s3 bucket as Mumbai region.

`aws s3api create-bucket --bucket sana.k8s.local --region ap-south-1 --create-bucket-configuration LocationConstraint=ap-south-1`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687756923853/cb38ddfd-5ff1-41b2-8212-3f1e949fe6c4.png align="center")

Enable Bucket Version: `aws s3api put-bucket-versioning --bucket sana.k8s.local --region ap-south-1 --versioning-configuration Status=Enabled`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687757609948/9093589f-29b0-48e3-a9c9-913cc81bba92.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687757677338/2fd7ae36-3885-423b-a6cb-c709d0f0dec1.png align="center")

EXPORT CLUSTER DATA INTO BUCKET:

`export KOPS_STATE_STORE=s3://sana.k8s.local`

GENERATE-KEY for clusters:

`ssh-keygen`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687757096936/1dfdbfc2-8987-4f5d-bd3d-50218607c2c8.png align="center")

Now create cluster from workspace instance.

`kops create cluster --name sana.k8s.local --zones ap-south-1a --master-size t2.medium --node-size t2.micro`

After creating cluster if u edit ur cluster follow this suggestion:

* list clusters with: `kops get cluster`
    
* edit this cluster with: `kops edit cluster sana.k8s.local`
    
* edit your node instance group: `kops edit ig --name=sana.k8s.local nodes-ap-south-1a`
    
* edit your master instance group: `kops edit ig --name=sana.k8s.local master-ap-south-1a`
    

Now cluster is created and now run the cluster with help of this command.

`kops update cluster --name sana.k8s.local --yes --admin`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687757499826/98c0c910-9675-4b4d-a312-1656af55ec46.png align="center")

see cluster is created.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687757549918/c5008d16-3045-42a3-8ee5-c45aebb49f4c.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687757924595/f431437e-6564-4048-b469-04cb9de10841.png align="center")

Step-4

Create Elastic Container Registry(ECR) in AWS.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687758064282/4ba160b2-1a33-4ed3-aa10-acf771ff3a3f.png align="center")

Create repo in public of ecr.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687758168811/8f353a5e-1042-4d26-bc22-cc902e405441.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687758240406/5f63943b-fbd9-4444-949f-f1e21fe1e6c7.png align="center")

Step-5

Create a dockerfile

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687758804032/e4809c87-25cd-4604-8526-2d0a12116cb2.png align="center")

Ngnix.conf

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687758857631/d05ca497-e455-47c6-94ad-d76457798d6d.png align="center")

Now clone the sample web application in my github repo for that first install git in your workspace ec2 instance.

`sudo apt-get install git -y`

`sudo git clone` [`https://github.com/Ashoksana/candy-crush.git`](https://github.com/Ashoksana/candy-crush.git) `(site1)`

`sudo git clone` [`https://github.com/Ashoksana/mario.git`](https://github.com/Ashoksana/mario.git) (site2)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687759247286/5f0147c7-65c6-48a5-877d-1e807aeccba6.png align="center")

Now build the image with your ecr repo name follow this ecr commands

`sudo apt-get install docker.io -y`

`sudo usermod -aG docker $USER`

`newgrp docker`

this is ecr "sana" repo commands.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687759583384/617002a0-5e4e-44b4-852c-bafa77f8e853.png align="center")

see now I successfully pushed image to ecr repo of aws

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687759742181/474b48da-8382-4704-81fc-6ca1b4931423.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687759776023/0604e3bf-4231-428b-8e39-3ac826cd706b.png align="center")

Step-6

After successfully image is pushed from docker cli to ecr repo of aws. Now install Ansible for deploy the web app in k8s clusters.

`sudo apt-get install ansible -y`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687760046165/210cafdf-64ed-4618-a2d3-39a552ead575.png align="center")

Now write ansble playbook

context\_name: "context name" (`kubectl config current-context`)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687760558172/80785c6e-45bb-4684-b336-08bdcf40d01c.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687762453997/ec9617c2-f6d4-43d8-8b58-245b4e578264.png align="center")

namespace\_name: "give the namespace for ur cluster"

ecr\_image: "ur ecr repo link"

app\_port: 80

deploymentservice\_name: "k8s deployment yml file"

Now create k8s deployment yaml file for pods creation.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687760898320/916877c5-6011-4b24-bf6c-33b7c56d935d.png align="center")

Step-7

Now run the playbook ansible.

`ansible-playbook deploy-nginx-app.yml`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687762707636/c093c00d-8485-4f42-939b-aa8c408046af.png align="center")

See successfully created pods in k8s from workspace ec2 instance.

`kubectl get pods -n em`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687762847209/64b620a8-f6e2-41dd-b354-c8468465d8e9.png align="center")

Step-8

Now copy the load balancer DNS of k8s cluster in AWS and browse in browser.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687763203863/168210c9-9796-47cb-ab60-1f94b0a650d1.png align="center")

`kubec svc -o wide -n em`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687763281596/93c94de4-9dcf-4f5e-acff-7bd21896add4.png align="center")

Finally u get the output.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1687763442609/a759a21f-313c-4c1d-b337-1c2aa6ffce02.png align="center")

Thank you for reading my blog......!

if u like the content follow me on LinkedIn: [https://www.linkedin.com/in/ashok-sana](https://www.linkedin.com/in/ashok-sana)

Follow my Whatsapp & telegram community: [https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3](https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3)

[https://t.me/ExplorewithAshok](https://t.me/ExplorewithAshok)

Happy learning......!

Ashok sana