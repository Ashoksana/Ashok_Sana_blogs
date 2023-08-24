---
title: "Day-07: Understanding package manager and systemctl"
datePublished: Fri Jul 21 2023 04:27:03 GMT+0000 (Coordinated Universal Time)
cuid: clkc2xt7m000e09jy13nufkvm
slug: day-07-understanding-package-manager-and-systemctl
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689913536056/b4c1e7a5-f3a8-410e-914b-c2971a88a6b3.png
tags: linux, devops, linux-for-beginners, linux-commands

---

Hello there, tech enthusiasts! Today, we're going to dive into the exciting world of package managers and learn how to install two powerful tools, Docker and Jenkins, on Ubuntu and CentOS systems using these package managers. 🚀

🐧 **Package Manager - What's That?**

Before we start, let's quickly understand what a package manager is in Linux. 🤔

A package manager is like a magic wand 🪄 for your operating system. It allows you to effortlessly install, remove, upgrade, configure, and manage software packages. Think of these packages as little gift boxes 🎁 containing amazing applications, both graphical and command-line tools, or even software libraries that other programs need to function. These packages come bundled with the necessary binary executables, configuration files, and sometimes information about their dependencies. 🎉

💼 **Package - Unwrapping the Gifts**

Alright, let's get a clearer picture of what a package exactly is. 📦

A package typically refers to an application, but it could be anything from a user-friendly GUI app to a powerful command-line tool or a software library essential for other programs. It's like a neatly wrapped present 🎁, containing all the goodies required to get the software up and running on your system. This includes the executable program itself, configuration files, and sometimes crucial information about any other software it relies on. 🎁

📦 **Different Kinds of Package Managers**

Now, let's explore some popular package managers and the systems they're used on. 📦

* **RPM Package Manager**: This one is used on various Linux distributions and has package managers like Yum and DNF. 🍽️
    
* **DEB Package Manager**: This system is commonly found on Debian-based distributions, and it features package managers like apt-get and aptitude. 🧭
    

Now, let's get our hands dirty and install Docker and Jenkins on Ubuntu and CentOS using these package managers! 🧰

🐳 **Installing Docker with Package Managers** 🐳

**Ubuntu - Using apt-get** 🍅

To install Docker on Ubuntu, open up your terminal and type in the following command:

```bash
$sudo apt-get update
$sudo apt-get install docker.io
```

**CentOS - Using yum** 🐮

For CentOS, use the yum package manager to install Docker:

```bash
$sudoy  yum update
$sudo yum install docker
```

🔨 **Installing Jenkins with Package Managers** 🔨

**Ubuntu - Using apt-get** 🍅

To install Jenkins on Ubuntu, follow these commands:

```bash
$sudo apt-get update
$sudo apt-get install jenkins
```

**CentOS - Using yum** 🐮

For CentOS, use the yum package manager to install Jenkins:

```bash
$sudo yum update
$sudo yum install jenkins
```

🔎 **systemctl and systemd - Managing Services** 🔎

Now that we have Docker and Jenkins installed, let's learn about systemctl, which helps us examine and control services managed by systemd. 🛠️

**systemd** is the superhero that manages services on Unix-like operating systems (most of them, not all). It handles starting, stopping, and maintaining these services with ease. 🦸‍♂️

🐋 **Checking Docker Service Status** 🐋

To check the status of Docker service, simply enter the following command:

```bash
$systemctl status docker
```

🛑 **Stopping Jenkins Service** 🛑

Let's put Jenkins on pause for a moment. Use the following commands to stop the Jenkins service:

```bash
$sudo systemctl stop jenkins
```

📸 **Before and After Screenshots** 📸

Take screenshots before stopping the Jenkins service and after stopping it, and witness the magical change! ✨

📜 **systemctl vs service - The Showdown** 📜

Now, let's get into a thrilling showdown of systemctl vs service! 👊

Both systemctl and service are used to control services, but systemctl is the newer, more powerful contender, while service is the traditional champion. 🥋

To check the Docker status, use:

```bash
$systemctl status docker
```

💻 *vs* 🖥️

```bash
$service docker status
```

In this corner, we have systemctl with its detailed status report, and in the opposite corner, we have the service command with its compact display. 🥊

Choose your fighter and unleash the power of service management! 🥋🛡️

There you have it, folks! We've explored the enchanting world of package managers, installed Docker and Jenkins on Ubuntu and CentOS, and discovered the might of systemctl and systemd. 🌟

Remember, with package managers at your disposal, installing and managing software becomes as easy as a few magical commands! So go ahead, explore, and make the most of these powerful tools. Happy coding! 🚀🔥

I hope you enjoyed this thrilling adventure! Until next time! 👋😊

Hope you like my blog...!

If you like the content follow me on LinkedIn: [https://www.linkedin.com/in/ashok-sana](https://www.linkedin.com/in/ashok-sana)

Follow my Whatsapp & telegram community: [https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3](https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3)

[https://t.me/ExplorewithAshok](https://t.me/ExplorewithAshok)

Happy learning......!