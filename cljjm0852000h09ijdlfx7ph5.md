---
title: "S3 cross replication"
datePublished: Sat Jul 01 2023 06:15:29 GMT+0000 (Coordinated Universal Time)
cuid: cljjm0852000h09ijdlfx7ph5
slug: s3-cross-replication
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688192095480/120c9d0c-beba-459f-8e21-155c07dbacf7.png
tags: aws, devops, aws-certified-solutions-architect-associate, s3-bucket, s3crossreplication

---

### **Introduction:**

In today's fast-paced digital landscape, businesses often require seamless data replication and backup strategies to ensure data durability and availability. AWS S3 (Simple Storage Service) comes to the rescue with its powerful cross-account replication feature, allowing organizations to replicate data across different AWS accounts. In this blog, we'll explore the benefits and implementation of S3 replication across multiple AWS accounts.

Benefits of Cross-Account S3 Replication:

1. **Enhanced Data Resiliency:** Replicating data across different AWS accounts provides an added layer of resiliency, protecting your critical data against accidental deletions, data corruption, or regional outages.
    
2. **Compliance and Governance:** Cross-account replication enables organizations to meet compliance requirements by securely storing data in separate AWS accounts, ensuring data privacy and separation of responsibilities.
    
3. **Disaster Recovery:** By replicating data to a different AWS account, you can establish a robust disaster recovery mechanism, ensuring business continuity in case of unexpected events or system failures.
    
4. **Simplified Collaboration:** Sharing data across accounts becomes easier with cross-account replication. Different teams or business units can securely access and work on the replicated data without compromising its integrity or security.
    

### **Implementing Cross-Account S3 Replication:**

**To enable cross-account replication in AWS S3, follow these steps:**

### **Step 1:**

First login 2 aws account Source s3 account and Destination s3 account.

In the source account create an s3 bucket here I created "multi-region-s3-sana" (this bucket I was created in ap-south-1)and destination I created a bucket in the name of "destination-bucket-sana"(this bucket I created in us-east-1)

Enable versioning on both the source and destination buckets. Versioning allows S3 to keep track of changes to objects and ensures accurate replication across accounts.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688119500417/12c312c6-781e-43c7-9859-ec85317891fd.png align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688187361751/243e6ea0-d837-4beb-9d2f-552e1513acf4.png align="center")

### **Step-2:**

In the source bucket create the replication rules for transferring data from different accounts to different regions.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688188091838/cfeaf200-c3fc-4106-bdda-c94fc04c30bc.png align="center")

click on the source bucket and go to the management, then create replication rule.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688188184870/638845ee-90db-49c6-a887-476d0d98dfd9.png align="center")

give replication rule id.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688188264552/cc66ebed-71a4-4c76-a96a-74dd115ce78b.png align="center")

make sure your bucket region is in the replication rule.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688189017374/e33dd484-f42a-4bd5-8c63-5f9e88b06173.png align="center")

Now in the replication rule destination, u can choose ur requirements like if you want to transfer the date within the account of different buckets of different regions. (or) if you want to transfer the data from different accounts of different regions.

Here I selected another account for that u have to destination account id and destination bucket name.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688188474181/e835914b-d45f-4064-b742-8370f8788ee4.png align="left")

In the IAM role select create a new role for replication.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688188789754/72014268-d187-4f67-be3f-bccb9c3716ea.png align="center")

And save your replication settings

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688188880266/26755f87-1d50-448d-97e1-ab8dd1496647.png align="center")

After clicking on save You will get a pop-up like this it means that if u have any existing objects to replicate to the destination bucket or not, I don't want to replicate existing objects to a destination bucket.

Based on your requirement you will select the options, here I am selecting "No, don't replicate existing objects".

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688189088343/c87338b2-3eb8-44d1-9bc8-2ca0962f0aa9.png align="center")

### **Step-3:**

Now go to the destination bucket of 2nd aws account.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688189454289/01cc6283-cb68-479b-b06f-97a0fbd797dc.png align="center")

Now go to the permission option of the destination account of aws and edit the bucket policy of the destination bucket.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688189607568/24625cab-2d6e-4d02-ac3a-d0449675b51d.png align="center")

Copy and paste this policy.[(https://docs.aws.amazon.com/AmazonS3/latest/userguide/replication-walkthrough-2.html](https://docs.aws.amazon.com/AmazonS3/latest/userguide/replication-walkthrough-2.html))

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688189896219/7db60011-3668-4e58-a1c6-a7a2ee28fee6.png align="center")

Replace the "set permission for objects" to "1" & "2" in "sid" value and also replace the AWS iam arn value to your replication rule iam arn.

replace the bucket name destination bucket name.

To get the replication arn IAM policy, go to the replication rule of the source bucket click on IAM role and copy IAM arn role, and paste it into the destination bucket policy.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688190514809/93c3c9eb-3712-4f38-b476-789711a20279.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688190556912/d7b655ce-e001-49be-9e1d-8ff37e5060da.png align="center")

Replace this thing and save it

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688190807354/1d0bd5f1-7492-4acb-a2ba-4b981c85a640.png align="center")

And finally, we did a replication of two different accounts of two different regions. Lets check if it will work or not.

For checking purpose I am uploading a few files in source bucket.

At present, in my source, nothing is there.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688191082330/1dfebee1-f05a-44a3-8a4f-4e8017942fe8.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688191180680/0f06b54c-66c4-499b-8040-6b0cb92a9e0c.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688191221560/67d2fc4c-d120-4342-b526-ca11e0462447.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688191268827/1f362db9-be5d-40fd-b5f5-5d53d8130675.png align="center")

Here I uploaded one file to my source bucket. Now go to the destination bucket and refresh the page of the 2nd AWS account.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688191446722/62f442bd-cfca-416f-a363-64ab183f5d13.png align="center")

So, here we transfer the data from one account of s3 aws to another account os s3 aws.

Hope you like my blog...!

if u like the content follow me on LinkedIn: [https://www.linkedin.com/in/ashok-sana](https://www.linkedin.com/in/ashok-sana)

Follow my Whatsapp & telegram community: [https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3](https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3)

[https://t.me/ExplorewithAshok](https://t.me/ExplorewithAshok)

Happy learning......!

Ashok sana