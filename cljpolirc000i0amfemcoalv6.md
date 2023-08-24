---
title: "Getting Started with ECS (Elastic Container Service) in AWS."
datePublished: Wed Jul 05 2023 12:14:39 GMT+0000 (Coordinated Universal Time)
cuid: cljpolirc000i0amfemcoalv6
slug: getting-started-with-ecs-elastic-container-service-in-aws
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688559253518/64343d0e-6b85-4c0c-a8e6-18ae6c4e182b.png
tags: aws, devops, ecs, aws-certified-solutions-architect-associate

---

### **Introduction:**

ECS (Elastic Container Service) is a powerful container orchestration service provided by Amazon Web Services (AWS). It allows you to easily deploy and manage containers at scale, providing high availability, scalability, and flexibility for your applications. In this blog post, we will walk through the essential steps to get started with ECS and explore its key features.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688550572863/dcc11f0b-7f95-49ce-bb12-856b8585c23f.png align="center")

### **Key features of ECS include:**

1. Container Management: ECS allows you to define and manage containers using Docker images. You can specify resource requirements, networking, and container definitions within task definitions.
    
2. Cluster Management: ECS allows you to create and manage clusters, which are a logical grouping of container instances. It provides features for scaling, monitoring, and auto-recovery of containers within the cluster.
    
3. Task Definitions: A task definition is a blueprint for running containers within ECS. It defines the containers to be launched, their configurations, resource requirements, networking, and more.
    
4. Task Scheduling: ECS provides a scheduler that intelligently places tasks onto container instances based on resource requirements, availability, and constraints. It ensures optimal utilization of resources and high availability of containers.
    
5. Load Balancing and Service Discovery: ECS integrates with Elastic Load Balancer (ELB) to distribute traffic across containers. It also supports service discovery, allowing containers to discover and communicate with each other using DNS.
    
6. Integration with AWS Services: ECS seamlessly integrates with other AWS services, such as IAM (Identity and Access Management), CloudWatch for monitoring, and CloudFormation for infrastructure as code deployments.
    
7. Integration with AWS Fargate: ECS can be used with AWS Fargate, a serverless compute engine for containers. Fargate allows you to run containers without managing the underlying infrastructure, providing a simplified experience.
    

ECS provides a flexible and scalable platform for running containerized applications, making it a popular choice for deploying microservices, web applications, and batch jobs. It offers a range of deployment options, including rolling updates, blue/green deployments, and auto-scaling, to ensure high availability and reliability.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688555159856/876e4e11-6ec5-4ae1-8b15-6ccdb6c8d9d7.png align="center")

### **1\. Creating an ECS Cluster:**

Login into the AWS management console and search ECS service on left side click on cluster and created a cluster of ecs.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688551010067/90b012cb-96cc-41bf-b923-75615a565b2f.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688551136871/ca7895ed-68be-43c0-89ee-9af62da22f1a.png align="center")

Now create a cluster of ecs and follow the below steps. here I am selecting default vpc.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688551356475/9ebb21ae-d12e-4244-8def-efc0681a4146.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688553304253/5f7a6d3b-e511-4346-9638-2a20cb5ada2a.png align="center")

How does infrastructure get here?

LAUNCH TYPES(can be a combination of these too)

EC2: You register and manage the EC2 instances yourself.

Fargate: Serverless; magically handled for you.

External (ECS Anywhere): For on-premises servers that you register and manage remotely.

But here I am leaving it as default as fargate.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688553433137/51f5e573-0996-43a2-b8d2-87f97d98aeff.png align="center")

Monitoring and tags are optional. if u want to give you can give this and create the cluster.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688551768667/7580aa9e-0968-4fa7-9b73-1bbf7ce04b45.png align="center")

After clicking on "create" it will create a cluster of ECS with the help of a cloud formation template.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688553911783/9c975422-10bc-409a-b0ac-7ede6729e72c.png align="center")

See our cluster created

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688554062122/c955cc62-c1ed-4991-9f06-d247f93be61b.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688554139755/56aa2225-9b75-47ab-8912-974eafe4c6a7.png align="center")

Look at the infrastructure of ECS. Fargate is created as a serverless.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688554360983/8711ff7c-3948-454f-a5df-fed2395df02e.png align="center")

### **Design a task definition.**

Now we have created a cluster of containers and then design a task definition.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688555590544/fd720a88-e16d-47b6-988e-5b5cf0042ea8.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688555625036/de9cd6d6-cb65-4771-97ad-6dd5fdbb84ea.png align="center")

For the container image URL go to the ECR tab in aws console. you can import the URL from ECR public gallery or you can import it from ecr personal repository.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688555779473/9dfb8b26-8666-4539-abad-be4795afc8bc.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688556048176/3a54185a-9e6e-40ee-bddd-c282c8098a09.png align="center")

Here i am using my personal repository.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688556148792/1575cc9c-ce75-44a4-b8e2-3e0930f8b129.png align="center")

Copy and paste my personal public repo URL link.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688556224643/62e5fb82-c49a-4211-acd8-dac47aa06580.png align="center")

And everything leaves it as default for creating task definition.

if you want you can also add containers.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688556363552/56341c64-1714-49dc-9498-fcde3f21d2f5.png align="center")

Now configure the environment, storage, monitoring, and tags.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688556498989/d99902ce-6786-4d7b-9ab4-98536d493576.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688556585765/617f53ff-be06-4489-9e10-88930b06d9c0.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688556618655/e6d96a29-a137-454f-b30a-99eca261c0b5.png align="center")

And click on the next step and review the task.

The task was created successfully.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688556762105/0ed8a0c4-6046-468a-b9eb-f8729c93a64e.png align="center")

### **Deploying a Task:**

Now deploy the task inside the cluster for that go to cluster and click on services to deploy the task.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688556966042/f75bee8a-5432-4e96-8ec1-5972814a4666.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688557061782/8ad5a101-bd44-48da-8774-6431d86606b6.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688557211950/c03a462f-9ec1-42ed-a0cc-78e58619caba.png align="center")

Scroll down in the Networking option and make sure that enable public IP.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688557380639/691938ec-d12a-4317-a1d5-376fd6b0b532.png align="center")

And create a service for the task, it will few minutes to create the service.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688557867430/edf2e840-2bcb-4d7f-86a6-827dd091a313.png align="center")

Here we set up the ECS cluster &gt;&gt; Container Instance &gt;&gt; Service &gt;&gt; Task &gt;&gt; website. Now I want to browse the container image with the help of public IP address of the task.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688558116526/d38198b8-9b63-4e54-bf04-9e0dc4e750c9.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688558152477/b91d9f76-b5c8-4bac-8b16-585956a8e8eb.png align="center")

Copy and paste of public IP address of the task into your browser.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688558261713/5e73cc83-ef67-45ef-ac87-68369b73ed15.png align="center")

### **Conclusion:**

ECS offers a robust and scalable platform for deploying and managing containers in the AWS cloud. In this blog post, we covered the essential steps to get started with ECS, from creating a cluster to deploying tasks and utilizing services. We also explored the integration with ECR to manage container images effectively. By following this guide, you'll be well-equipped to leverage ECS for your containerized applications, taking advantage of its flexibility and scalability.

Hope you like my blog...!

if u like the content follow me on LinkedIn: [https://www.linkedin.com/in/ashok-sana](https://www.linkedin.com/in/ashok-sana)

Follow my Whatsapp & telegram community: [https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3](https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3)

[https://t.me/ExplorewithAshok](https://t.me/ExplorewithAshok)

Happy learning......!

Ashok Sana