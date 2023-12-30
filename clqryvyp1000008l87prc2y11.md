---
title: "Deploy Simple NGINX application IN GKE of Google Cloud Platform"
datePublished: Sat Dec 30 2023 11:16:11 GMT+0000 (Coordinated Universal Time)
cuid: clqryvyp1000008l87prc2y11
slug: deploy-simple-nginx-application-in-gke-of-google-cloud-platform
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1703934894393/9c111448-f721-4c1f-ad7c-6b6da1361a23.png
tags: docker, kubernetes, devops, gcp, gke, 90daysofdevops

---

### **Step 1: Set up Google Cloud Platform (GCP) Project**

1. **Create a GCP Account:** If you don't have a Google Cloud Platform account, sign up for one.
    
2. **Create a Project:** Create a new project in the Google Cloud Console.
    
3. **Enable Billing:** Make sure to enable billing for your project.
    
4. **Enable the Kubernetes Engine API:** In the Google Cloud Console, navigate to the "APIs & Services" -&gt; "Dashboard." Enable the "Kubernetes Engine API."
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703928024147/46df75b1-a164-4ab9-8673-1d4e87ac4603.png align="center")
    

### **Step 2: Enable CloudShell**

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703928099620/9a9a05e0-a4c0-411f-b79c-4ac186765378.png align="center")

### **Step 3: Set Up** `gcloud` Configurations

Run the following commands to configure `gcloud` with your GCP project:

```bash
$gcloud auth login
$gcloud config set project ashok-198510
```

Replace `PROJECT_ID` with your GCP project ID.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703928197945/cc14c834-95e7-4e19-88fd-9c6b297dfdeb.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703928227982/169f4ec7-2c99-41bc-82d6-94193efb15ba.png align="center")

### **Step 4: Pull Nginx image, Copy your web-app html file to docker and push to Google Container Registry**

1. First pull the nginx image following command.
    
    ```bash
    $docker pull nginx:latest
    ```
    

Then run the nginx image

```bash
$docker run -d -p 80:80 nginx:latest
```

1. second download or create any sample index.html page. Here i cloned from my git hub repo in that repo only copy the index.html and ashok.png.
    
    a. This is repo link [https://github.com/Ashoksana/explorewithashok.git](https://github.com/Ashoksana/explorewithashok.git)
    
    `git clone` [`https://github.com/Ashoksana/explorewithashok.git`](https://github.com/Ashoksana/explorewithashok.git)
    
2. Next copy the index.html and ashok.png for deploying my webpage to internet.
    
    ```bash
    $docker cp index.html <container-id>:/usr/share/nginx/html/
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703931339989/15b28e3b-d665-4cd7-85e3-ed995859051d.png align="center")
    
    Now check the docker container web interface.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703932341658/f0589144-187f-4ba4-8b4f-2cf2a586877f.png align="center")
    
    you will get web inerface like this
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703932370508/8c62158e-006f-4685-a5a5-a8d403e6a77f.png align="center")
    
    Then update the image using docker commit command
    
    `docker commit <containerid> explorewithashok/web:version`
    
    ```bash
    $docker commit <container-id> /web:version1
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703931480192/95a80605-f4fb-4463-b413-a76b88e90f24.png align="center")
    
    Tag the image for push this image to Google container registry using following commands.
    
    Before this you have to enable the container registry api.
    
    ```bash
    $gcloud services enable containerregistry.googleapis.com
    $docker tag explorewithashok/web:version1 gcr.io/ashok-198510/explorewithashok:version1
    ```
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703931680340/ad996206-673d-4fc1-9a76-d7cf1ca6ffdf.png align="center")
    
    Now push the image to Google Container Registry
    
    ```bash
    $docker push gcr.io/ashok-198510/explorewithashok:version1
    ```
    
    this error means you should give docker auth permission to gcloud using following command.
    
    `gcloud auth configure-docker`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703932002849/486e3b30-557d-47cc-89fd-2b7c2f281879.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703932526481/a08c389d-c3ea-4a18-8bf2-19463ba4bccf.png align="center")
    
    After above command issue will reslove.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703932240682/ffcc551b-09ed-4787-b389-38d57852ca20.png align="center")
    
    Afer image pushed into GCR now go to the Container Registry console.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703932452911/6d1596b0-c805-4cbc-95e0-f6e4c443f7b9.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703932462142/8024401e-cf50-4dcb-adbf-79eb2e347d54.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703932474717/78a072d5-630c-4984-9373-7c58de59b77b.png align="center")
    
    these are image details like zone, version, iamge name
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703932593263/b2320bfe-e39a-4238-9604-be3637eb2a10.png align="center")
    
    In above it clearly shown we can directly deploy our application using deploy option but we are devops engineer best practice is deploy through Gcloud cli.
    

Know more about GCR follow this document [https://cloud.google.com/container-registry/docs/pushing-and-pulling?\_ga=2.111514180.-173018589.1570384092](https://cloud.google.com/container-registry/docs/pushing-and-pulling?_ga=2.111514180.-173018589.1570384092)

### **Step 5: Setup the zone for Cluster Create a GKE Cluster**

Run the following command to create a GKE cluster:

```bash
$gcloud config set compute/zone us-central1-a
$gcloud container clusters create <CLUSTER_NAME> --num-nodes=3
```

Replace `CLUSTER_NAME` with the desired name for your cluster. Eg: `gcloud container clusters create ashoksana --num-nodes=3`

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703933158389/9a3e207f-03d0-4ab1-ab2a-614c63541dac.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703933199215/ddfb9944-9954-44f0-82c8-e36551d7bb55.png align="center")

### **Step 5: Configure** `kubectl`

Run the following command to configure `kubectl` to use your GKE cluster:

```bash
$gcloud container clusters get-credentials CLUSTER_NAME
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703933087502/e924a0bd-b688-47db-b4ef-c57a337ab237.png align="center")

### **Step 6: Deploy a Sample Website**

For deploy the sample website in GKE run following comand:

```bash
$kubectl create deployment web-app --image=gcr.io/ashok-198510/explorewithashok:version1
$kubectl expose deployment web-app --type LoadBalancer --port 80 --target-port 80
# To get pods
$kubectl get pods
# To get service
$Kubectl get services
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703933421144/e4e7c99b-6a91-43f2-aa1b-132834e756f4.png align="center")

Now you want to host application in internet copy the external ip and pppaste it in brower of your desktop.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703933620207/44ffcdf5-e4e6-47c6-ac1b-743f93fbb3d8.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703933628491/fe58c212-7564-4d9e-a4c4-ae9eab16ec3e.png align="center")

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1703933636883/e8951415-7088-4e94-be1b-1e1155eaf816.png align="center")

Congratulations! You've successfully created a GKE cluster and deployed a sample website. Keep in mind that this is a basic setup, and in a production environment, you would likely want to use a more complex configuration and consider security best practices.

After completion of your please delete GKE cluster using following command

<mark>gcloud container clusters delete &lt;cluster-name&gt;</mark>

I hope you people like this blog.

If you like this blog please follow these below Links, You will get more content like this in that links.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695627131885/d3899b2c-dd76-4ef9-8230-870760b10aac.gif align="left")

WhatsApp Group:- [https://chat.whatsapp.com/Ii2xKz9vuW93AWt07m4AYj](https://chat.whatsapp.com/Ii2xKz9vuW93AWt07m4AYj)

Telegram:- [https://t.me/ExplorewithAshok](https://t.me/ExplorewithAshok)

LinkedIn: [https://www.linkedin.com/in/ashok-sana](https://www.linkedin.com/in/ashok-sana)

Instagram:- [https://instagram.com/explorewithashok?igshid=OGQ5ZDc2ODk2ZA==](https://instagram.com/explorewithashok?igshid=OGQ5ZDc2ODk2ZA==)

Linktree:- [https://linktr.ee/ashoksana](https://linktr.ee/ashoksana)