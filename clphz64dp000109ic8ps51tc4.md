---
title: "🔍 Finding Phone Number Info with Docker and Linux🐧📱"
datePublished: Tue Nov 28 2023 06:46:41 GMT+0000 (Coordinated Universal Time)
cuid: clphz64dp000109ic8ps51tc4
slug: finding-phone-number-info-with-docker-and-linux
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1701153949544/2e785758-4f36-4fda-9b20-e85f48f99044.png
tags: linux, docker, hacking, phone, 90daysofdevops

---

In this blog post, we dive into the world of PhoneInfoga, a tool designed not for hacking phone numbers, but for extracting valuable information about them. The objective is to shed light on unknown numbers that may have recently called or to assist in penetration testing scenarios, always emphasizing responsible and ethical use.

**Key Points:**

1. **Introduction to PhoneInfoga:** Understanding its Purpose and Application
    
    * Clarification that the tool is not for hacking but rather for extracting information.
        
    * Highlighting the common scenarios where such tools can prove useful, such as identifying unknown callers or performing penetration tests with explicit permission.
        
2. **Ethical Use and <mark>Legal Disclaimer</mark>:**
    
    * Emphasizing the importance of ethical use and the need for explicit permission when engaging in any form of hacking, even for legitimate purposes like penetration testing.
        
    * Clearly stating that the content is part of an <mark>educational process</mark> and should <mark>not be misused for unauthorized activities</mark>.
        
3. **Installation and Setup:**
    
    * Providing insights into the two options for running PhoneInfoga – on any Linux distribution or any cloud VM
        
    * Explaining the installation process using Docker.
        
4. **Tool Demonstration:**
    
    * Walking through the actual use of PhoneInfoga, showcasing both command-line interactions and the user-friendly web interface.
        
    * Illustrating the tool's capabilities by running a scan on a US-based phone number and interpreting the obtained information, including location, carrier details, and more.
        
5. **Ensuring Ethical Practices:**
    
    * Discussing the importance of responsible behavior while using the tool, especially when dealing with sensitive information.
        
    * Encouraging readers to adopt ethical hacking practices and reinforcing the message that the tool should only be employed for lawful and authorized purposes.
        

### Requirements for this practical:

1. Linux distro (ubuntu, centos, Redhat, kali). Here I am using the 'Kali Linux VM in my local server of a virtual box, you can use a cloud (Aws, Gcp, Azure) of VMs.
    
2. Install docker and git on your Linux machine.
    

### Setup or Configure the requirements :

1. Follow the below images for this lab
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701147962290/5b638523-c141-464d-8d8c-3f9b94ffaa28.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701148054301/fa275284-e6f4-42e7-94f1-43a76f7477ed.png align="center")
    
    After logging into your VM of Kali Linux install docker and git.
    
    👇👇👇here I already installed docker by using the following commands.
    
    `sudo apt install docker.io -y`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701148384056/b7e3e651-a17e-4841-89a1-9b77ef38bf2e.png align="center")
    
    Can't wait to get info from phone numbers
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701148671982/0899e64d-9e9b-48f4-bdaa-de9c4c019030.gif align="center")
    

### Create PhoneInfoga Docker container:

1. Open this Github link [https://github.com/Ashoksana/phoneinfoga.git](https://github.com/Ashoksana/phoneinfoga.git)
    
2. After opening this link scroll down you will see documentation under readme.md.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701150120182/b92af0d6-24bf-463a-b61b-e5abe88b89a9.png align="center")
    
3. After this, you will get one page that is related to the 'phoneonfoga' tool installation.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701150268043/9501498c-fb4b-4913-9ab5-b079c86f563a.png align="center")
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701150313305/bb6509aa-860b-4a55-b3ed-561f88c37af9.png align="center")
    
4. Copy the above docker pull command and paste in the kali linux, then pull the image.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701150484270/dcc171f4-b69d-4cc2-a18a-f584f8a512a4.png align="center")
    
5. Now run the image and also give any phone number as below follow the command to scan the Phone number info. Here I am tried the spam number for scanning and getting info purposes.
    
    This is the command to scan phone number info `docker run -it sundowndev/phoneinfoga scan -n <countrycode phone_number>`
    
    example: `docker run -it sundowndev/phoneinfoga scan -n 911725348151`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701150822193/bb562f82-2658-4e40-bea3-1ee514597c5d.jpeg align="center")
    
    Country code should be mandatory.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701151009943/7f3b5c3f-ecf3-463c-bb17-7d0a83a3e90d.png align="center")
    
    Hurry the phone number is scanned with help of this tool.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701151094674/a1829377-8b16-4068-9311-6e6de3a20910.png align="center")
    
    see this scan the phone and give the phone number info.
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701151178851/59671ba2-82b5-411f-8041-dccb0a0a0aab.png align="center")
    
6. Above one we scan through CLI. Now we can also check GUI by using this command.
    
    `docker run -it -p 8080:8080 sundowndev/phoneinfoga serve -p 8080`
    
    ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701151873230/75ba522a-a717-4aee-b314-719fbcf1ab8b.png align="center")
    
    1. Open the Google Chrome and give http://your\_ipaddress:8080.
        
        you will get an interface after this command.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701152851713/fae3c83b-c9f4-4a7b-9324-c41143b69f34.png align="center")
        
        Then give any spam number to a lab to get information for that number.
        
    2. Scroll down you will get Google links you will get ip address of a particular device. It will scan the phone number of that number connected to the internet as in the image shown below.
        
    3. Click on any drop-down you will get a link.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701153017582/01b4016d-6e5a-42e5-a8ae-472e6efe2a0f.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701153216297/d392e376-29cf-44e7-9ed5-3d1b9d56528a.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701153250395/44474560-1f47-4f8d-9133-eca0c4fa9c44.png align="center")
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1701153293328/8f6128b0-0713-4e5c-a6a1-567d82ace167.gif align="center")
        
        I hope you people like this blog.
        
        ![](https://cdn.hashnode.com/res/hashnode/image/upload/v1695627131885/d3899b2c-dd76-4ef9-8230-870760b10aac.gif align="left")
        
        If you like this blog please follow these below Links, You will get more content like this in that links.
        
        WhatsApp Group:- [https://chat.whatsapp.com/Ii2xKz9vuW93AWt07m4AYj](https://chat.whatsapp.com/Ii2xKz9vuW93AWt07m4AYj)
        
        Telegram:- [https://t.me/ExplorewithAshok](https://t.me/ExplorewithAshok)
        
        LinkedIn: [https://www.linkedin.com/in/ashok-sana](https://www.linkedin.com/in/ashok-sana)
        
        Instagram:- [https://instagram.com/explorewithashok?igshid=OGQ5ZDc2ODk2ZA==](https://instagram.com/explorewithashok?igshid=OGQ5ZDc2ODk2ZA==)
        
        Linktree:- [https://linktr.ee/ashoksana](https://linktr.ee/ashoksana)