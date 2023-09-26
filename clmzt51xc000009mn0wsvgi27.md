---
title: "🐳 Reducing Docker Image Size by 95%: A Step-by-Step Guide 🚀"
datePublished: Tue Sep 26 2023 04:18:38 GMT+0000 (Coordinated Universal Time)
cuid: clmzt51xc000009mn0wsvgi27
slug: reducing-docker-image-size-by-95-a-step-by-step-guide
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1695643340503/b84148bd-5f51-4ef8-8c6e-bb9b8018ffc7.gif
tags: docker, aws, devops, 90daysofdevops

---

Are you tired of dealing with bloated Docker images that take up too much storage space and slow down your container deployments? 😩 Well, you're in luck! In this blog post, we'll show you how to reduce the size of your Docker image dramatically by up to 95%. 🎉

## **Why Does Image Size Matter? 🤔**

The size of your Docker image matters for several reasons:

* Faster Deployment: Smaller images deploy faster, reducing container startup times.
    
* Efficient Resource Usage: Smaller images use fewer resources, making them more efficient.
    
* Lower Bandwidth Costs: Smaller images consume less bandwidth when pulling from a registry.
    

## **Step 1: Choose a Minimal Base Image 🐦**

Start by choosing a minimal base image that suits your application's needs. A popular choice is the Alpine Linux image, known for its small size.

```bash
# Use Alpine Linux as the base image
FROM alpine:3.14
```

## **Step 2: Use Multi-Stage Builds 🏗️**

Multi-stage builds allow you to compile and build your application in one stage and then copy the artifacts into a smaller final stage. This reduces the image size significantly.

```bash
# Build stage
FROM golang:1.17 AS build
WORKDIR /app
COPY . .
RUN go build -o myapp

# Final stage
FROM alpine:3.14
WORKDIR /app
COPY --from=build /app/myapp .
```

## **Step 3: Minimize Dependencies 📦**

Remove unnecessary dependencies and files from your image to make it as lean as possible.

```bash
# Remove unnecessary packages
RUN apk --no-cache del .build-deps
```

## **Step 4: Use .dockerignore 🚮**

Create a `.dockerignore` file to exclude files and directories that don't need to be included in the image.

```bash
node_modules
.git
```

## **Step 5: Compress Artifacts 🗜️**

Compress your application artifacts before copying them into the image. This reduces the overall image size.

```bash
# Compress artifacts before copying
RUN tar -czf myapp.tar.gz myapp
```

## **Step 6: Optimize Dockerfile Layers 🍰**

Combine multiple RUN commands into a single layer to reduce the number of layers in your image.

```bash
# Combine multiple RUN commands
RUN apk --no-cache add package1 package2 && \
    apk --no-cache add package3 package4
```

## **Step 7: Clean Up 🧹**

Clean up temporary files and caches in your Dockerfile to further reduce the image size.

```bash
# Clean up
RUN rm -rf /var/cache/apk/* /tmp/*
```

## **Step 8: Build Your Image 🏭**

Build your optimized Docker image using the following command:

```bash
docker build -t myapp:optimized .
```

## **Step 9: Verify the Size Reduction 📊**

After building the image, compare its size to the original image:

```bash
docker images
```

You'll be amazed by how much space you've saved! 🎈

Below I am providing examples of large and small size images. Some case studies.  
**Case Study: Optimizing Docker Image Size for a Python Application 🐳📏**

### **Scenario 🗺️**

You are developing a Python application that performs data analysis on a large dataset. Initially, you created a Docker image with convenience in mind, resulting in a large-size image. However, you've realized the need for a smaller, more efficient image to improve deployment speed and resource usage. 😕🚀

### **Large-Size Docker Image 📦**

**Dockerfile for the Large-Size Image:**

```bash
# Use a heavyweight base image
FROM ubuntu:20.04

# Install Python and dependencies
RUN apt-get update && \
    apt-get install -y python3 python3-pip

# Copy a large dataset into the image
COPY large_dataset.csv /app/

# Install additional unnecessary packages
RUN pip3 install pandas numpy

# Run the Python application
CMD ["python3", "app.py"]
```

**Characteristics of the Large-Size Image:**

* Base image: Ubuntu 20.04
    
* Includes unnecessary Python packages (`pandas`, `numpy`)
    
* Copies a large dataset into the image
    
* Total image size: Considerably large 📈
    

### **Small-Size Docker Image 🎯**

**Dockerfile for the Small-Size Image:**

```bash
# Use a minimal base image
FROM python:3.8-slim as build

# Copy only necessary files
COPY app.py /app/
COPY requirements.txt /app/

# Install Python dependencies
RUN pip install --no-cache-dir -r /app/requirements.txt

# Create a minimal final image
FROM python:3.8-slim

# Copy files from the build stage
COPY --from=build /usr/local/lib/python3.8 /usr/local/lib/python3.8
COPY --from=build /usr/local/bin /usr/local/bin

# Run the Python application
CMD ["python3", "/app/app.py"]
```

**Characteristics of the Small-Size Image:**

* Base image: Python 3.8 slim
    
* Minimizes unnecessary dependencies
    
* No large dataset copied
    
* Total image size: Significantly smaller 📉
    

### **Results 📊**

* The large-size image was convenient during development but had a considerable footprint.
    
* The small-size image was optimized for production, resulting in a significantly smaller size.
    
* Deployment and resource usage with the small-size image were more efficient.
    
* Testing showed that the functionality and performance of the application were not compromised by the size reduction. 👍🏼⚙️
    

### **Case Study Conclusion 🏁**

Optimizing Docker images is crucial for efficient containerization. By carefully considering dependencies, base images, and file management, you can significantly reduce image sizes without sacrificing functionality. In this case, transitioning from a large-size image to a small-size image improved deployment speed and resource efficiency while maintaining application functionality. 🙌🏼🛠️

### **Blog Post Conclusion 🎯**

By following these steps and best practices, you can dramatically reduce the size of your Docker images. Smaller images lead to faster deployments, more efficient resource usage, and lower bandwidth costs. Embrace these techniques to optimize your images and enjoy the benefits of improved containerized applications. 🚀

challenges, but you've got this! 💪 Happy Dockering! 😄🐋

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695627131885/d3899b2c-dd76-4ef9-8230-870760b10aac.gif align="center")

1. If you like the content follow me on LinkedIn: [https://www.linkedin.com/in/ashok-sana](https://www.linkedin.com/in/ashok-sana)
    
    Follow my Whatsapp & telegram community: [https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3](https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3)
    
    [https://t.me/ExplorewithAshok](https://t.me/ExplorewithAshok)
    
    Happy learning......!