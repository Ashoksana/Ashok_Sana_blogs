---
title: "Title: Understanding Dockerfile Keywords and Their Usage"
datePublished: Mon Jul 10 2023 04:38:34 GMT+0000 (Coordinated Universal Time)
cuid: cljwdi8qz000809l9do7rf5cf
slug: title-understanding-dockerfile-keywords-and-their-usage
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688963866777/d7abd472-184b-42f3-914c-826fb9f596e7.png
tags: docker, aws, dockerfile

---

### **Introduction**:

Docker has revolutionized the way software applications are deployed and managed, providing a lightweight and portable solution for containerization. A Dockerfile is a text file that contains a set of instructions to build a Docker image. These instructions are executed in order, creating a layered approach to constructing an image. In this blog, we will explore the most commonly used Dockerfile keywords and provide examples of their usage.

1. FROM:
    
    The "FROM" keyword sets the base image for subsequent instructions in the Dockerfile. It specifies the starting point for building your image. Here's an example:
    

`FROM ubuntu:latest`

This instruction sets the base image as the latest version of Ubuntu.

1. MAINTAINER:
    
    The "MAINTAINER" keyword (deprecated, use LABEL instead) specifies the author of the image. It is used to provide contact information for the person responsible for maintaining the image. Here's an example:
    

`LABEL maintainer="john@example.com"`

1. RUN:
    
    The "RUN" keyword executes commands in a new layer on top of the current image and commits the results. It is used to install packages, update the system, or perform any other necessary tasks during the image build process. Here's an example:
    
    `RUN apt-get update && apt-get install -y python3`
    

This instruction updates the package lists and installs Python 3.

1. CMD:
    
    The "CMD" keyword provides defaults for an executing container. It specifies the command to be run when the container starts. Here's an example:
    
    `CMD ["python", "`[`app.py`](http://app.py)`"]`
    

This instruction sets the default command to execute the "[app.py](http://app.py)" Python script.

1. EXPOSE:
    
    The "EXPOSE" keyword informs Docker that the container listens on the specified network ports at runtime. However, it does not actually make the ports accessible. Here's an example:
    
    `EXPOSE 8080`
    
    This instruction exposes port 8080 within the container.
    
2. ENV:
    
    The "ENV" keyword sets environment variables within the container. These variables can be accessed during the build process and when the container is running. Here's an example:
    
    `ENV DB_HOST=`[`localhost`](http://localhost) `DB_PORT=5432`
    
    This instruction sets the environment variables for the database host and port.
    
3. ADD:
    
    The "ADD" keyword copies files, directories, or remote files to the container. However, it invalidates caches, so it is recommended to use "COPY" instead. Here's an example:
    
    `ADD app.tar.gz /app`
    
    This instruction copies the "app.tar.gz" file to the "/app" directory within the container.
    
4. COPY:
    
    The "COPY" keyword copies files or directories to the container. By default, it copies files as the root user, regardless of the USER/WORKDIR settings. The "--chown" option can be used to change ownership. Here's an example:
    
    `COPY` [`app.py`](http://app.py) `/app/`
    
    This instruction copies the "[app.py](http://app.py)" file to the "/app" directory within the container.
    
5. ENTRYPOINT:
    
    The "ENTRYPOINT" keyword configures the container to run as an executable. It specifies the command that should be executed when the container starts. Here's an example:
    
    `ENTRYPOINT ["python", "`[`app.py`](http://app.py)`"]`
    
    This instruction sets the entry point for the container to execute the "[app.py](http://app.py)" Python script.
    
6. VOLUME:
    
    The "VOLUME" keyword creates a mount point for externally mounted volumes or other containers. It allows data to persist beyond the lifecycle of the container. Here's an example:
    
    `VOLUME /data`
    
    This instruction creates a volume at the "/data" directory within the container.
    

### **Conclusion:**

Understanding the various Dockerfile keywords is essential for building efficient and reliable Docker images. Each keyword serves a specific purpose in the containerization process, allowing you to customize and configure your application environment. By mastering these keywords, you can create Docker images that are easily reproducible and scalable, simplifying the deployment of your applications.

Hope you like my blog...!

if u like the content follow me on LinkedIn: [https://www.linkedin.com/in/ashok-sana](https://www.linkedin.com/in/ashok-sana)

Follow my Whatsapp & telegram community: [https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3](https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3)

[https://t.me/ExplorewithAshok](https://t.me/ExplorewithAshok)

Happy learning......!

Ashok Sana