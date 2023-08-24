---
title: "Demystifying Docker Networking: A Deep Dive with Practical Examples"
datePublished: Sat Aug 12 2023 16:33:15 GMT+0000 (Coordinated Universal Time)
cuid: cll88kg1c000808l6afqb18rw
slug: demystifying-docker-networking-a-deep-dive-with-practical-examples
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1691857641335/e51e71d6-e8b2-4b66-9cca-2ced9079f87e.png
tags: docker, devops, networking, 90daysofdevops

---

**Introduction:** Docker has revolutionized the way we develop, deploy, and manage applications by enabling us to encapsulate applications and their dependencies in isolated containers. One of the key aspects of Docker is networking, which facilitates communication between containers, services, and the external world. In this blog, we'll explore the world of Docker networking, its types, and provide practical examples to understand each type better.

**What is Docker?** Docker is a platform that allows you to develop, deploy, and run applications inside lightweight, portable, and self-sufficient containers. Containers package an application's code, runtime, libraries, and dependencies, ensuring consistent behavior regardless of the environment they are executed in. For instance, a web application developed in Docker can be easily moved from a developer's laptop to a production server without worrying about compatibility issues.

**Why Use Docker?** Docker offers several advantages:

1. **Isolation:** Containers are isolated from each other and from the host system, ensuring that applications run in a consistent environment.
    
2. **Portability:** Docker containers are consistent across different environments, reducing the "it works on my machine" problem.
    
3. **Resource Efficiency:** Containers share the host OS kernel, consuming fewer resources compared to traditional virtual machines.
    
4. **Scalability:** Dockerized applications can be easily scaled up or down as needed.
    

**What is Docker Networking?** Docker networking enables communication between containers, as well as between containers and external networks. It allows containers to expose ports, access external services, and communicate with other containers, enabling microservices architecture.

**Types of Docker Networking:**

1. **Bridge Network:** This is the default network created when Docker is installed. Containers on a bridge network can communicate with each other and the host system, but not directly with external networks. Example: `docker network create mybridge`
    
2. **Custom Bridge Network:** You can create your own bridge network for containers to communicate with each other and the host. Example: `docker network create --driver bridge mycustombridge`
    
3. **Host Network:** Containers using the host network share the host's networking namespace, effectively bypassing Docker's network isolation. This can be useful when networking performance is critical. Example: `docker run --network host myapp`
    
4. **None Network:** Containers on the 'none' network have no external connectivity. This is useful when a container should have isolated communication. Example: `docker run --network none myisolatedapp`
    
5. **Overlay Network:** Overlay networks enable communication between containers across multiple Docker hosts. This is crucial for multi-host setups, often used in orchestration tools like Docker Swarm or Kubernetes. Example: Setting up Docker Swarm with overlay network.
    
6. **Macvlan Network:** This type of network allows containers to appear as separate physical devices on the network. It's useful when you need containers to have their IP addresses. Example: Configuring Macvlan network for containers.
    
7. **IPvlan Network:** Similar to Macvlan, IPvlan allows multiple containers to share the same physical network interface, but each container has its own IP address. Example: Using IPvlan to assign unique IP addresses to containers.
    

**Detailed Explanation with Practical Examples:** Let's take a closer look at how to create and use these networks with practical examples. Suppose you have a microservices application consisting of a web server and a database.

1. **Bridge Network:**
    
    ```bash
    docker network create myapp_bridge
    docker run --network myapp_bridge -d --name webserver nginx
    docker run --network myapp_bridge -d --name database postgres
    ```
    
2. **Custom Bridge Network:**
    
    ```bash
    docker network create --driver bridge mycustom_bridge
    docker run --network mycustom_bridge -d --name webserver nginx
    docker run --network mycustom_bridge -d --name database postgres
    ```
    
3. **Host Network:**
    
    ```bash
    docker run --network host -d --name webserver nginx
    ```
    
4. **None Network:**
    
    ```bash
    docker run --network none -d --name isolated_app my_isolated_image
    ```
    
5. **Overlay Network (Docker Swarm):**
    
    ```bash
    # Initialize Docker Swarm
    docker swarm init
    # Create overlay network
    docker network create -d overlay myoverlay_network
    # Deploy services using the overlay network
    docker service create --network myoverlay_network --name web nginx
    docker service create --network myoverlay_network --name database postgres
    ```
    
6. **Macvlan Network:** Setting up Macvlan network requires more complex configuration and might involve network setup on the host itself.
    
    1. *Example*: Running a container with Macvlan networking:
        
        ```bash
        docker network create -d macvlan --subnet=192.168.1.0/24 --gateway=192.168.1.1 -o parent=eth0 mymacvlan
        docker run -d --name macvlan-container --network mymacvlan nginx
        ```
        
7. **IPvlan Network:** Similar to Macvlan, setting up IPvlan network requires host-level configuration.
    
    1. *Example*: Running a container with IPvlan networking:
        
        ```bash
        docker network create -d ipvlan --subnet=192.168.2.0/24 --gateway=192.168.2.1 -o parent=eth0 myipvlan
        docker run -d --name ipvlan-container --network myipvlan nginx
        ```
        

**Conclusion:** Docker networking plays a crucial role in connecting containers and enabling seamless communication within microservices architectures. By understanding the various types of Docker networking and their practical implementations, you're equipped to design and manage networking for your Dockerized applications effectively. Whether it's creating custom networks, achieving host-level performance, or scaling across multiple hosts, Docker's networking capabilities have you covered.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1691857912597/c828dd6d-c94c-4ea9-8f40-98ee161afbe3.png align="center")

Hope you like my blog...!

If you like the content follow me on LinkedIn: [https://www.linkedin.com/in/ashok-sana](https://www.linkedin.com/in/ashok-sana)

Follow my Whatsapp & telegram community: [https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3](https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3)

[https://t.me/ExplorewithAshok](https://t.me/ExplorewithAshok)

Happy learning......!