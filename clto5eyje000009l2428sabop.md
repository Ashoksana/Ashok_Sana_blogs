---
title: "Aws-web Appilication Firewall"
datePublished: Tue Mar 12 2024 09:06:58 GMT+0000 (Coordinated Universal Time)
cuid: clto5eyje000009l2428sabop
slug: aws-web-appilication-firewall
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1710234225709/0f398f7b-8082-4d66-8aeb-a3997d4a34c9.gif
tags: aws, security, devops, 90daysofdevops, waf

---

![Diagram showing how AWS WAF integrates with other AWS services to protect your web applications from exploits.](https://d1.awsstatic.com/Product-Page-Diagram_AWS-Web-Application-Firewall%402x.5f24d1b519ed1a88b7278c5d4cf7e4eeaf9b75cf.png align="left")

### **Introduction:**

In the ever-evolving landscape of cybersecurity, safeguarding your web applications against malicious attacks is paramount. Amazon Web Services (AWS) provides a robust solution in the form of AWS WAF (Web Application Firewall), offering advanced protection and control over your web applications. In this comprehensive guide, we'll explore the key features, benefits, and best practices of AWS WAF, empowering you to fortify your online assets against potential threats.

1. Understanding AWS WAF: AWS WAF is a cloud-based web application firewall that helps protect your web applications from common web exploits. It enables you to create custom rules to filter and monitor HTTP and HTTPS traffic, allowing you to mitigate security risks and ensure the availability and integrity of your applications.
    
2. Key Features and Capabilities: a. Rule Creation: AWS WAF allows you to create custom rules to filter, allow, block, or monitor web requests based on various conditions such as IP addresses, HTTP headers, query parameters, and more.
    
3. Managed Rule Sets: AWS WAF comes with pre-configured managed rule sets that can be easily integrated to protect against common web attacks like SQL injection, cross-site scripting (XSS), and more. This ensures a quick and effective defense mechanism without the need for extensive manual configuration.
    
4. Integration with AWS Services: Seamlessly integrate AWS WAF with other AWS services like Amazon CloudFront, AWS Application Load Balancer, and Amazon API Gateway, providing a holistic approach to securing your web applications.
    

### **Benefits of AWS WAF:**

1. **Enhanced Security**: Protect your applications from a wide range of web exploits and attacks, ensuring the confidentiality, integrity, and availability of your online assets.
    
2. **Flexibility and Customization:** Tailor security rules to meet the specific needs of your applications, allowing for granular control over the filtering and monitoring of web traffic.
    
3. **Cost-Effective:** With a pay-as-you-go pricing model, AWS WAF offers cost-effective security measures, eliminating the need for upfront investments in hardware or infrastructure.
    

### **Best Practices for Implementing AWS WAF:**

1. **Regularly Update Managed Rule Sets**: Keep your web applications protected by staying up-to-date with the latest managed rule sets provided by AWS WAF. This ensures that your security measures align with emerging threats and vulnerabilities.
    
2. **Monitor and Analyze Web Traffic:** Utilize AWS WAF logging and monitoring features to gain insights into your web traffic. Regularly review and analyze logs to identify patterns or anomalies that may indicate potential security risks.
    
3. **Conduct Regular Security Audits:** Perform routine security audits to assess the effectiveness of your AWS WAF configuration. This proactive approach allows you to identify and address potential vulnerabilities before they can be exploited.
    

Lets's do demo......

![Amazon Web Services (AWS) Web Application Firewall (WAF) Service Delivery  in Dubai, Abu Dhabi and UAE](https://www.integrauae.com/images/homepageimages/aws-waf-service-delivery.png align="left")

### **Step-1:**

1. login into the AWS CONSOLE.
    
2. Create aws ec2 instances (2 or more) in that instances host any sample application for demo purpose.
    
    `#!/bin/bash`
    
    `sudo yum update -y`
    
    `sudo yum upgrade -y`
    
    `sudo yum install httpd -y`
    
    `sudo systemctl enable httpd`
    
    `sudo systemctl start httpd`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710222461600/c3bbda52-2078-4017-ada3-66fa58e3c2bc.png align="center")
    
    check the httpd is running or not using public of instances.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710222544995/1c0c4d70-2bd3-477a-ae8a-ca96cbbe004b.png align="center")
    

### **Step-2:**

1. Create a Target group for the common connection for those Ec2 instances.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710222855693/b6537858-9cdd-4df4-b960-7dfc68c0508c.png align="center")
    
2. Now create a Application Load Balancer and connect to target group.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710222984312/c3bceefd-3c41-403d-84e1-677d45f83220.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710223048860/57c23099-edeb-4eda-ab51-81c1e3f3941e.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710223116301/50ec0c3a-2b21-4a1d-9b37-4dc43e14cff0.png align="center")
    
    Check the load balancer DNS url if it is work or not.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710223323392/e8c0271e-a4c7-4229-9472-7b451bb519eb.png align="center")
    

### **Step-3:**

1. Now create a AWS WAF for our application to Ec2 instances.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710223834770/8d01aba4-395a-4e4c-ad39-53cdc70e5cde.png align="center")
    
2. Before the creation of AWS WAF create ip sets.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710223931642/0db76da2-3658-4158-b415-a649063b5cad.png align="center")
    
    Enter IP set rule name.
    
    Choose region and IP version.
    
    Add the IP address list.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710225660781/62c1d714-53a5-4d4e-b631-ac9b87729fa9.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710225709052/1532d3d5-0202-4c19-9a5d-30b7a309f37b.png align="center")
    
    3. Create Web ACL (access control list).
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710224601356/3f5e76bd-19e6-4da9-975a-7a25694c9166.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710224682777/4e9bdff5-b51a-487c-9111-0e62f98c26cd.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710224723097/5b696a9a-c5ab-41b1-89c5-dc69d798ae82.png align="center")
        
        Add rule and rule groups.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710225791048/6f5391d5-fd6c-4d2d-971d-43ddb6e5557c.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710224875803/63d9b502-8a7f-4ac9-bc46-3a9074be23e2.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710224910106/01f8ec83-23c7-4f1b-bff6-3738160edf94.png align="center")
        
        Follow the default steps to create Web-Acl's and finally you created the web acl.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710226026060/3765a1be-c6f0-4308-82b1-bfba049382af.png align="center")
        

Try to access a load balancer from the IP which is define in the IP sets rules group We get 403 forbidden message because WAF block that IP.

403 Forbidden error, it means that you do not have permission to view the requested file or resource.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710226296140/16386b93-3144-4772-98c5-3c622d20c8b2.png align="center")

It means for my local server ip dont have access to http appication inside the ec2 instance. The AWS WAF blocking my IP address to access.

If you want to see the waf dashbord which is blocking or access.

Go to webAcl.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710226482952/535f8bbd-8129-4ba7-8893-30ecb9427efd.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710226565550/46e056ac-fa89-424e-a530-010d23667c7b.png align="center")

From WEB ACL we filter the traffic and check all details Like blocked, allowed IP, Sample of bot detection, client device types, attack type, top 10 countries, etc...

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1710226605213/92d8a3b1-c0f9-49ac-b386-c917aa5c5c6f.png align="center")

Thank you.................