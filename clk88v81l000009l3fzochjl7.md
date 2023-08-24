---
title: "Project: Implementing CI/CD Pipeline on AWS (Complete cicd)"
datePublished: Tue Jul 18 2023 12:01:55 GMT+0000 (Coordinated Universal Time)
cuid: clk88v81l000009l3fzochjl7
slug: project-implementing-cicd-pipeline-on-aws-complete-cicd
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689681359090/1ffac5e1-7b6b-4e29-a22b-47fd9815da63.png
tags: aws, devops, aws-code-build, terraform-autoscaling-aws-cloudinfrastructure-devops-infrastructureascode-cloudcomputing-automation-cloudnative-awsautoscaling-elasticity, awscodepipeline

---

**Requirements:**

1. AWS Account: You will need access to an AWS account with appropriate permissions to create and manage AWS resources.
    
2. Sample Web Application: A simple web application (e.g., a basic HTML/JavaScript application) that can be deployed on AWS.
    
3. AWS Services: The CI/CD pipeline will leverage the following AWS services:
    
    * AWS CodeCommit: For hosting the source code repository.
        
    * AWS CodeBuild: To build and package the application.
        
    * AWS CodeDeploy: To automate deployment to the target environment.
        
    * AWS CodePipeline: To orchestrate the CI/CD process.
        

**Steps to Implement the CI/CD Pipeline:**

**Step 1: Set up the Code Repository**

1. Create a new AWS CodeCommit repository to host your source code.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689661327991/c66117eb-0028-466e-8702-c46bda65b7f9.png align="center")

![](https://miro.medium.com/v2/resize:fit:560/0*TIwcHVvZRD3nOm9i align="left")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689661409257/5b8a6e51-f1c0-4ae8-a0fe-e5b8d7e18176.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689661491415/88f8cf3b-e61d-426b-ac70-bcb159a07593.png align="center")

The repository is created in Code commit as a "cicd-repo"

1. Clone the repository to your local development environment.
    
    before that, you have to install git software on your laptop and go to IAM of aws select an existing or create a new user, go to a security credential generate the "HTTPs git credential." copy and save it in your notepad for further purpose.
    

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689662325914/7f0ee35f-8de9-4195-a54c-85aa6284302e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689662369014/d055bc77-a807-451c-aa1a-ce5fbaefe156.png align="center")

In security credentials scroll down.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689662430949/4f49eddb-adf8-41f7-867d-94a3e0663ca3.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689662466547/315a64cc-f558-4c25-a59c-d100a404833b.png align="center")

1. Add your sample web application code to the repository.
    
    a. Now set up the CLI user and generate the secret key and access key, for accessing the aws environment through cli. Now, clone the repository "git clone &lt;url&gt;"
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689663753747/406f998c-3024-408c-aaff-e4fa3dce3aaf.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689663842021/7dc81d90-8d3d-47a0-9126-c02a07bf261e.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689663882968/bdaad0c3-a650-4d15-a548-1f2ac8b36494.png align="center")
    
    Install aws cli on your local machine.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689663990051/54bf3dcd-a9f3-4bd7-9f96-8ec6d11766cd.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689664128429/492d6978-726e-4b04-81b6-f75a3fb50dfc.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689664176069/45fb8dc4-10f4-4f06-9757-97140fc9b913.png align="center")
    
    Clone the code commit repository in your machine.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689664883087/b18964f6-753b-42dc-b62c-7576e3d0584c.png align="center")
    
    You will get one pop-up related to git and pass the HTTPs git credentials below the pop-up
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689664959171/4c90be3c-aa71-491e-8cf2-225ecfbe6699.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689665160402/ff4e63b9-bba1-42c6-a0f7-9ade94144ac3.png align="center")
    
    Now add a few file for your application inside this empty repository.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689665264736/c7140369-601b-4154-a1b1-1c824ef30e12.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689665484878/99d9a991-e0dc-4f59-9c15-e99befaefc08.png align="center")
    
    The above following files you have to add in "CICD-REPO" code commit repo. Now these files add to code-commit repo using these commands. `git add .` `git commit -m "this code for cicd" , git push --all`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689665676337/5294ff10-bd50-4a2f-87ac-0d1501fc7a13.png align="center")
    
    Now check AWS code commit console whether these filess updated or not.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689665751199/37aa85c7-8cec-4d94-8c89-394a057f692f.png align="center")
    
    our application files are updated in the code commit repo
    

**Step 2: Configure AWS CodeBuild**

Define a build specification file (e.g., `buildspec.yml`) in the root of your repository. This file specifies the build steps and dependencies.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689679422128/544bfd50-c38d-4a7a-92e8-2961254cc6cb.png align="center")

Configure a CodeBuild project that references the build specification file and defines the build environment. Set up CodeBuild to trigger a build whenever changes are pushed to the CodeCommit repository.

Now, the rest of the things leave as it is, and click on “Create Build Project”

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689667875898/18384c88-bc12-45fa-8897-3a0c6d5b09b7.png align="center")

In Source section, Select

Source provider: AWS CodeCommit.

Repository: demo-app

Reference Type: Branch

Branch: Main

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689667922476/3dd01b39-b625-4344-b20e-a70882085b1a.png align="center")

In the Environment section, Select

Environment Image: Managed Image

Operating System: Ubuntu

Runtime: Standard

Image: &lt;latest one&gt;

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689668015497/200ce9e5-44b1-472e-afb3-8b6b24cd6dbf.png align="center")

For this, a service role will be required and it will be created automatically when we select the “New Service Role”. In the BuildSpec section, click on “Use a build spec file”.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689668159896/e476db1f-5951-41e0-b92b-f6d71afc4a1b.png align="center")

![](https://miro.medium.com/v2/resize:fit:296/0*et-8OeVYS_KT2orb align="left")

Now, click on “Start Build”.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689668324255/fb8868f8-cd7c-48bd-bb4f-3816ba65c050.png align="center")

Here, you can see the “Phase Details”.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689670805779/f7d89356-851f-4b68-9cd2-634b512ccb25.png align="center")

We can give “Artifacts upload location” if we want to build the code on some specific location.

Goto “Edit” button and click on “Artifacts”

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689670925273/05520bc2-e47a-4d0c-8bf5-5ef1fb113d1a.png align="center")

For this, you have to create a bucket and enable versioning.

Type: S3 Bucket. (Create a new S3 bucket if you haven’t created it)

Bucket Name: &lt;Your created bucket&gt;

Name: &lt;Your folder name in S3 bucket&gt; (Go and create one)

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689671122460/c5358821-ac44-4b5b-8765-e387914c7f04.png align="center")

The bucket was created.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689671295509/d3445351-bc01-46ce-8c2b-ef170839bcba.png align="center")

Click on “Update Artifact”. Next time, whenever you start a build, your files will go there. Let’s give it a try by building it.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689671439516/593e3921-f85a-4f5f-a3da-cdc876e9fe96.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689671479441/d15abde9-090f-4190-8336-3737dc293873.png align="center")

**Step 3: Configure AWS CodeDeploy**

1. Define an application in CodeDeploy that represents your web application.
    
    Open the AWS Management Console and navigate to the CodeDeploy service.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689671792823/51954382-b3dd-4061-9396-ca916f80950b.png align="center")
    
    Click on "Create application" to start the application creation process.
    
    Select the compute platform that your web application runs on (EC2, Lambda, or ECS). Choose the appropriate option based on your deployment target.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689671856440/7ab3d885-d25e-4663-bb87-0d6cd9dca696.png align="center")
    
    Here I am using EC2 instances, choose the deployment group that represents the set of instances where your application will be deployed. If you haven't created a deployment group yet, you can create one during the application creation process.
    
    For creating a deployment group, you have to create one ec2 as a test environment purpose and select in the deployment group.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689672000166/18006a90-bbd3-4340-a6a9-1a0c65b15424.png align="center")
    
    Here I created an EC2 instance of amazon Linux (t2.micro).
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689672392762/ba9fb8b8-e610-46c2-b563-c2c39b037e89.png align="center")
    
    Now go to the IAM and create 2 roles one for codedeploy purpose and another for connection between codedeploy and ec2.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689672524219/2c3fb12e-e030-49b1-a7f8-ea2a35094c20.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689672567810/2313528e-3c19-4430-902c-943dd7f0b324.png align="center")
    
    1st role was created and now creates the second role for ec2 and code deploy.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689672674565/018d5df6-5b9f-4aa8-be79-acc00e1f84b3.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689672756413/4d74a3da-4ff5-4213-ae17-ad8bf55a06fd.png align="center")
    
    Now go to Ec2 instance and attach the code deploy role in "testing instance".
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689672863688/2eca5801-8871-4063-92c0-709be84df63e.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689672893176/d74e3549-de3a-432d-93f9-1680049ce033.png align="center")
    
    And now give the tags name for identification of the deployment group as Key = "Environment" and Value = "Testing".
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689673081438/4a93d4ef-c880-49c7-b21c-8d3e6cbed359.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689673119484/717149a6-78e9-41de-b70d-0defefcd8f34.png align="center")
    
    Now open your ec2 instance and install "code deploy agent" by using the following commands.
    
    ````bash
    # Installing the CodeDeploy agent on EC2
    ```
    sudo yum update -y
    sudo yum install -y ruby wget
    wget https://aws-codedeploy-eu-west-1.s3.eu-west-1.amazonaws.com/latest/install
    chmod +x ./install
    sudo ./install auto
    sudo service codedeploy-agent status
    ```
    ````
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689674205382/5e864422-22f7-4b5e-8a23-9b64c6bba261.png align="center")
    
2. Configure deployment settings, such as deployment type (in-place or blue/green) and deployment configuration. Select In-place.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689673265107/843a3f02-79be-4b79-b293-fffd69e1164b.png align="center")
    
    In the place of environment configuration, you should give ec2 and given tags names of testing ec2
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689673429278/bc6125c4-4554-4d2d-8530-3a1d579073c7.png align="center")
    
    The remaining thing leave it as a default and create deployment group.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689673496803/5bd930ff-0d1d-409d-a9a4-08d4b8f60018.png align="center")
    
    For deployment of applications on the internet (www), you have to create another S3 bucket for **<mark>revision</mark>** of the application.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689676454698/97a38ef7-9497-4d13-8807-782991d76dd7.png align="center")
    
    For this, you have to set aws cli in your machine. in starting of this blog i already setup aws cli.
    
    ````bash
    # create a bucket and enable versioning
    ```
    aws s3 mb s3://cicd-explorewithashok --region ap-south-1 --profile cicd
    aws s3api put-bucket-versioning --bucket cicd-explorewithashok --versioning-configuration Status=Enabled --region ap-south-1 --profile cicd
    ```
    
    # deploy the files into S3
    ```
    aws deploy push --application-name cicd-deploy --s3-location s3://cicd-explorewithashok/codedeploy-ashok/app.zip --ignore-hidden-files --region ap-south-1 --profile cicd
    ```
    ````
    

Now create a deployment.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689676528635/dacda20b-8a62-49ae-aa34-4b6321fc00f3.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689676596668/dc6f7d00-38a8-43c8-9743-46f7682395a6.png align="center")

Here you select the revision type as s3 for this u have to run above s3 aws cli commands.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689676705652/2dd00862-49f6-4435-9da0-be2594fb40c1.png align="center")

And create a deployment.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689676758083/9d2788ab-8b5d-4d51-8703-34f70b1745f0.png align="center")

Finally, our Test Ec2 instance is attached to the code deployment now go to the test ec2 instance copy the public IP address, and paste it into the browser you will get your application output.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689677338367/e73670d6-adf4-4a40-82c6-477a3e1ed76d.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689679150056/705bcf45-7f21-4c19-b5e8-3289dcdeb157.png align="center")

**Step 4: Create the CI/CD Pipeline with AWS CodePipeline**

1. Create a new AWS CodePipeline pipeline.
    
2. Configure the pipeline's source stage to use the CodeCommit repository.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689677524563/aba0f5f8-98de-4de6-849f-34a5faa39982.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689677629550/517eb7a1-ef03-436d-b67f-701588328598.png align="center")
    
3. Add a build stage that references the CodeBuild project created earlier.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689677672261/9205d663-100a-400c-a931-fa2fc339bc00.png align="center")
    
4. Add a deploy stage that references the CodeDeploy application and deployment group. Review and create a pipeline
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689677709787/ed743a62-7a27-4274-973a-a70d2a894f52.png align="center")
    
    Congratulations guys We build successfully CICD on AWS.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689677964659/fb396230-8cfe-47a7-926a-88626d62520e.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689677988833/98f9b9b2-0a17-4a0e-a0cf-ebaf043fd98e.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689678018222/f643ebce-5aa1-42c6-a346-2984e7c71f32.png align="center")
    
    See, here I deploy only as Dev/Test environment. if you want to do production deployment the same as how we created testing deployment same like you have to create a production environment but don't forget to install a code-deploy agent inside production EC2.
    
    This is output of our application.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689679298200/48acd3fb-b4a4-41b5-9c5f-8548fb93874d.png align="center")
    

Project code Githublink \[[https://github.com/Ashoksana/explorewithashok.git](https://github.com/Ashoksana/explorewithashok.git)\]

Hope you like my blog...!

if u like the content follow me on LinkedIn: [https://www.linkedin.com/in/ashok-sana](https://www.linkedin.com/in/ashok-sana)

Follow my Whatsapp & telegram community: [https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3](https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3)

[https://t.me/ExplorewithAshok](https://t.me/ExplorewithAshok)

Happy learning......!