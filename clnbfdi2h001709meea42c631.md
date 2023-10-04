---
title: "Title: "Launching Your First Linux VM on Google Cloud Platform (GCP): A Step-by-Step Guide" 🚀🐧"
datePublished: Wed Oct 04 2023 07:26:31 GMT+0000 (Coordinated Universal Time)
cuid: clnbfdi2h001709meea42c631
slug: title-launching-your-first-linux-vm-on-google-cloud-platform-gcp-a-step-by-step-guide
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1696404295867/c8570842-50c4-4291-94d2-77ca3e6bef71.gif
tags: compute-engine, cloud-computing, devops, gcp, 90daysofdevops

---

### **Introduction to Google Cloud Platform (GCP) 🌍**

In the vast landscape of cloud computing, Google Cloud Platform (GCP) stands out as a powerful, innovative, and user-friendly cloud solution. Let’s dive into the why, how, when, and where of GCP, and also explore how it stacks up against its major competitors, AWS and Azure.

### **Why Choose Google Cloud Platform?**

**Innovation and Scalability:** GCP is renowned for its innovation, leveraging Google's expertise in data management, machine learning, and analytics. It offers seamless scalability, allowing businesses to grow without worrying about infrastructure constraints.

**Global Network Infrastructure:** Google operates one of the largest and most advanced global networks, ensuring fast and reliable connectivity to GCP services from anywhere in the world.

**Data Analytics and AI:** GCP provides robust data analytics and AI capabilities, enabling businesses to gain valuable insights from their data and leverage machine learning technologies to drive innovation.

**Security and Compliance:** GCP emphasizes security, with advanced identity management, encryption, and compliance features, ensuring that your data is protected and compliant with industry standards.

### **How to Get Started with GCP?**

Getting started with GCP is straightforward. Simply create an account, set up your project, and start using GCP services. The GCP console provides an intuitive interface for managing resources, making it accessible for beginners and powerful for advanced users.

### **When to Choose GCP?**

**For Innovation:** If your organization values innovation and wants to leverage cutting-edge technologies like AI, machine learning, and data analytics, GCP is an excellent choice.

**Scalability Needs:** GCP's seamless scalability makes it ideal for businesses with fluctuating workloads or those experiencing rapid growth.

**Global Reach:** If your business operates globally and requires a robust and well-connected infrastructure worldwide, GCP's global network is a significant advantage.

### **Where Can You Use GCP?**

GCP services are available in regions across the world, including North America, Europe, Asia, and more. Google Cloud has data centers strategically located in these regions, ensuring low-latency access to its services globally.

### **GCP vs AWS vs Azure: Key Differences**

**1\. Service Offerings:**

* **GCP:** Known for its data analytics, machine learning, and big data services.
    
* **AWS:** Offers a vast array of services, including a rich set of machine learning tools.
    
* **Azure:** Strong integration with Microsoft products, extensive hybrid cloud solutions.
    

**2\. Pricing:**

* **GCP:** Competitive pricing, especially for certain services like BigQuery.
    
* **AWS:** Offers a wide variety of pricing models, can be cost-effective with careful planning.
    
* **Azure:** Often offers hybrid licensing options for businesses using Microsoft products.
    

**3\. Ecosystem and Integration:**

* **GCP:** Tight integration with Google Workspace (formerly G Suite) and other Google services.
    
* **AWS:** Extensive ecosystem and third-party integrations.
    
* **Azure:** Seamless integration with Microsoft products like Office 365 and Windows Server.
    

**4\. Global Network:**

* **GCP:** Boasts Google’s extensive global network infrastructure for fast and reliable connections.
    
* **AWS:** Globally distributed data centers, solid network infrastructure.
    
* **Azure:** Large number of global data centers and extensive network capabilities.
    

Today, we’re diving into the world of Google Cloud Platform (GCP) to help you launch your very first Linux Virtual Machine (VM). Don’t worry if you’re new to this – we've got your back! Let’s get started on this exciting journey. 😊

### **Step 1: Create a GCP Account 🌐**

1. If you haven’t already, head over to the [**Google Cloud Platform**](https://cloud.google.com/) website, sign in or create an account.
    
2. Follow the instructions to create your account, provide the necessary information and agree to the terms of service.
    
3. Set up billing information to enable GCP services. You will be eligible for a free trial with an initial $300 credits means INR 24969rs to explore GCP and Activate them.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696396060007/e762ed9f-da5e-48a0-99b0-42ebfe237a05.png align="center")
    

### **Step 2: Access the GCP Console 🖥️**

Once you’re logged in, navigate to the GCP Console. It's your control center for all things cloud-related.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696395884542/4b0dfcfb-f75d-44ac-8a58-fe3c40b20e60.png align="center")

### **Step 3: Create a New Project 🏗️**

Projects help you organize resources and manage permissions. Create a new project and give it a meaningful name.

### **OR**

Leaving it as the default project means Google Cloud Platform provides you with a default project.

Here I am creating a new project, for that click the dropdown button of "My First Project". it will show as a pop-up.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696396407065/efd29af6-df0a-4a05-a7e5-454c516f7ba9.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696396591766/532fcbac-cda7-438a-abe1-a7fcb3746203.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696396662388/92634ddd-caf7-44f0-b81e-7939f614d93a.png align="center")

Here I already created one 1project as custom and another one which created by Gcp default. So, here shows me that i have only 23 projects left for Free trail account.

### **Step 4: Compute Engine APIs 💳**

Before you start spinning up VMs, make sure billing is enabled for your project. Also, enable necessary APIs such as Compute Engine API.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696397617048/84d4bd27-b77d-4c03-bfc3-6e49f2834f88.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696397784546/3c363625-b8fd-45a8-bfbf-b8cc53e8d6fb.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696397849433/f2b15412-9d6a-47c9-8556-7aec4898251a.png align="center")

Now Navigate to the Compute Engine section in the GCP Console.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696398099468/48f515fa-1782-4826-a106-3fc9fa7eb4a5.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696398145186/8be65569-9f5c-4972-9f9d-e18fcf0fde96.png align="center")

### **Step 5: Launch a Linux VM 🐧**

1. Click on the Navigation menu (☰) and go to Compute Engine &gt; VM instances.
    
2. Click the “Create” button.
    
3. Choose your desired region and zone for your VM.
    
4. Select a machine type. For beginners, a small instance will do just fine.
    
5. Under the Boot disk section, click “Change” and select a Linux distribution of your choice (like Ubuntu, CentOS, or Debian).
    
6. Set the desired Disk size and click “Select”.
    
7. Click “Create” to create your VM.
    
8. Configure the firewall settings by selecting "Allow HTTP traffic" or any other ports you need to open.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696398204450/d3ded066-c799-4a10-8574-ac644c40ccb2.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696398328983/174285ff-bcd2-442b-8950-57369715278f.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696398765594/4b309516-7439-4f23-a659-a801013a53a9.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696398889611/368c5c4e-d88d-49be-a49f-a6ecb21c70a6.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696398994059/facb1cbf-de43-4d05-a4c5-e44ff1ea65b1.png align="center")

Finally VM of gcp is creating.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696399074545/05b5084e-7aae-4be2-9a7a-d99b855ab1a0.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696399132254/be65ae21-9f1a-4cc7-8b5a-2e9522eb71be.png align="center")

Now click on SSH it will open GCP browser terminal to connect the debian linux machine of gcp cloud.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696399328849/e591104e-ff03-4f9d-94a8-e20d81fb3791.png align="center")

After that again you get one more pop-up for authantication.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696399397670/e48b5853-93fd-452c-9ad8-73314c6ef5b6.png align="center")

Finally your in Gcp Vm of linux machine. successfully we are created one virtually laptop or desktop in cloud using Gcp.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696399510676/ecbaabd9-92a0-4eb9-9567-0f3fbd11ef8f.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696399570902/5e24ca48-a1f5-40f6-8ff3-1d9f0c93e31a.png align="center")

### **Step 6: Explore and Have Fun! 🎉**

Congratulations! You’ve successfully launched your first Linux VM on GCP. Now you can install software, host websites, or do whatever your heart desires in your cloud-based Linux environment.

### **Step 7: Deletion of VM of Gcp**

After completion of your work with that vm, please delete or stop the instance because it will charged you account untill and unless you stop or delete vm

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1696399969501/b166030f-61ef-43ea-bb13-663a6da3a807.png align="center")

Remember, it's your responsibility to manage your cloud resources efficiently. So, after your VM has served its purpose, make sure to stop or delete it promptly. This way, you control costs, enhance security, optimize resources, and contribute to a greener planet.

I hope you people like this blog.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695627131885/d3899b2c-dd76-4ef9-8230-870760b10aac.gif align="left")

If you like this blog please follow these below Links, You will get more content like this in that links.

WhatsApp Group:- [https://chat.whatsapp.com/Ii2xKz9vuW93AWt07m4AYj](https://chat.whatsapp.com/Ii2xKz9vuW93AWt07m4AYj)

Telegram:- [https://t.me/ExplorewithAshok](https://t.me/ExplorewithAshok)

LinkedIn: [https://www.linkedin.com/in/ashok-sana](https://www.linkedin.com/in/ashok-sana)

Instagram:- [https://instagram.com/explorewithashok?igshid=OGQ5ZDc2ODk2ZA==](https://instagram.com/explorewithashok?igshid=OGQ5ZDc2ODk2ZA==)

Linktree:- [https://linktr.ee/ashoksana](https://linktr.ee/ashoksana)