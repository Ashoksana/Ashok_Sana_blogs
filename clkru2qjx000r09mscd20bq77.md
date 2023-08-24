---
title: "Build 3-tier Architecture of PHP-LAMP with Terraform Tool #part-1"
datePublished: Tue Aug 01 2023 05:03:15 GMT+0000 (Coordinated Universal Time)
cuid: clkru2qjx000r09mscd20bq77
slug: build-3-tier-architecture-of-php-lamp-with-terraform-tool-part-1
tags: terraform, terraweekchallenge

---

 **Introduction:**

In modern web application development, a 3-tier architecture is a popular approach for building scalable and robust systems. The combination of PHP, Apache, MySQL, and Linux (known as PHP-LAMP) forms the backbone of many web applications. In this blog post, we will explore how to leverage the power of Terraform, an infrastructure as a code tool, to provision a 3-tier architecture of PHP-LAMP on a cloud platform of your choice.

**Understanding the 3-Tier Architecture:**

**PHP:**

* PHP is a server-side scripting language used for web development.
    
* It helps create dynamic web pages and handle various tasks like form submissions and database interactions.
    
* It acts as the core programming language in the application tier.
    

**Apache:**

* Apache is a widely used web server that hosts web applications.
    
* It receives client requests, delivers static and dynamic content, and manages communication between the user interface and the application logic.
    
* It plays the role of the web server in the presentation tier.
    

**MySQL:(mariadb)**

* MySQL is an open-source relational database management system (RDBMS).
    
* It stores and manages structured data used by web applications.
    
* It serves as the backend database in the data tier, handling data storage and retrieval.
    

**Linux:**

* Linux is an open-source operating system used as the foundation for hosting web applications.
    
* It provides a stable and secure environment for running web servers.
    
* It offers various distributions like Ubuntu, CentOS, and Debian, which are commonly used for web server deployments.
    

**What is Terraform?**

Terraform is a tool for managing and provisioning infrastructure using code. It allows you to define your infrastructure configuration in a simple and readable language. With Terraform, you can easily create and manage resources across various cloud providers or on-premises environments.

**Key concepts in Terraform:**

**Providers:** Plugins that let Terraform interact with different infrastructure platforms or services like AWS, Azure, or Google Cloud.

![](https://blogger.googleusercontent.com/img/a/AVvXsEg4SkiuUUSNPbgpS1aknOgZ6iwcr8hHov6JxU3ov8gkNt0DC4Z1C6F3L2wAtp-HPj1Wsy1LyekKL4ZJTFbrMaV1DJLRhaLa8roHY7qeiuQECLfwgL5f8RHIZLK8MJqG4v_viqG4wrRMDRbUpO02rgOHBlAIe2Jo3J-fECcuHvnuwKqQPUox9ruY5eE7OQ align="left")

  

**Resources:** Building blocks in Terraform that represent infrastructure components such as virtual machines, networks, or databases.

![](https://blogger.googleusercontent.com/img/a/AVvXsEheGFODLl2g6kzwJb49QIS0Qt9x_wtmJPm96lW1Pu8rArfbvRd-0RxwRVDttSGy3Mz4rLYG3u32Tk17Z9kZePwWAzE-YX869fc4fgMwKHuG5nDZs6_x-QW-vc1aqTOK5lbtLlc9Wrjgy2_lsiJmIDr4Xa0_7fH6frPTM0YjLW-p-01fCU7HStuaNuEWHw=w355-h125 align="left")

  

**Variables:** Parameters that allow you to customize your infrastructure configuration and make it reusable.

![](https://blogger.googleusercontent.com/img/a/AVvXsEhY1fbhUxRwAfJPI2dyA23cHHsYpn9vAhk740PodOeTlqkC46QFNFxp2raOOdwlqSx1dYkKHWT3VurwlF5I46kzqTRAYCU9KcMFVgAr-UWlTL1XU4udht5J-77pJJMDNPtghgRhPgzwVlRx11MYYAAs7Ics_xdI_WsEs1IY190_Daqbbz1OqGG1TByKQg=w438-h180 align="left")

**State:** A file that keeps track of the current state of your infrastructure, enabling Terraform to make targeted changes and avoid unwanted modifications.

![](https://blogger.googleusercontent.com/img/a/AVvXsEiAcbOJ_e9mRc9NrleANx8klmxCUe1weN2cGTStgU2hL8NvkD-Uev9_CgR5-okvCYoVGtFUghHkemZh8pHf0kQWpOZFRPRuYl1ynbj-OOE9evuXeDevqI2maSLfyzHo8peMzcWphlfbcda891RHWKFsY0WAmapxM69-0nl4UsQCJjmlTPd6UYtW1hlX5g=w386-h151 align="left")

**  
Setting up the Development Environment:**

**Determine your operating system:**

Terraform supports various operating systems, including **Windows, macOS,** and **Linux**. Make sure you know which operating system you are using.

**Download the Terraform binary:**

Visit the official Terraform website: [https://www.terraform.io/downloads.html](https://www.terraform.io/downloads.html)

Download the appropriate Terraform binary for your operating system.

Terraform is distributed as a single binary file.

![](https://blogger.googleusercontent.com/img/a/AVvXsEi-kNPjY4bgZGpuAuEhJyCiNjtHR6IECYfalH25QCPTgyiMD_5EV_0-SIvJcD47dJ7jvpzcbbq84Dqhr6Jeom5TQXfnHO73qUwRGuwNvMRTahHJWm7AhiTnSb14KjOwHSGuI4YQ0aFb0m08NPF3k4eWqQE4UwpeW2Jgw95b2lp8rBdfv2-ldDZUE3b8-Q=w525-h283 align="left")

  
After clicking on this you will be downloaded as a zip file and extract the file of terraform.

![](https://blogger.googleusercontent.com/img/a/AVvXsEiLN1zWki3atMvtkp99k0hbggV9Ylx8Zil66z5kyJuLZV4UCYpDIaS8j2BTc_RoEFsGbOy-NR8V3VMl3-iEKxV_GuUrzEkdDWT4kcXWWQu2sESaKC2FJLNqN7twu_jm75DKflu08waMFerXiYCDRsm-Yx7s45SeO6egzHIOoLRgbQY729MU6seBIpA7pA align="left")

  
Now copy the Terraform installation file path and go search box of windows type &lt;Edit the system environmental variables&gt;

u will get this pop click on advance and Environmental variables.

![](https://blogger.googleusercontent.com/img/a/AVvXsEh2fX_95M0a-1iBk_aMKxs3Kx219jjylg0vfSg2MpSV3CMEh9sS9RuyObH18IH6DQ2F5DfTLttwNmtQFPFdJaZexpqWGQveSiqBTumhV1xnYdvMSZDS4w06BtZuqwa_kMpJvnT5N0A_ZqZPqpNB_9fKJXXPtXSXUebMp65xxIe-Rf8RbT81GCx8VdTDkg=w388-h372 align="left")

  
click on the path of system variables

![](https://blogger.googleusercontent.com/img/a/AVvXsEjFRwBp6DIyvEPYIX8f6slwoOxYbVgwpun24DIFIlLQqUoVWTRWnlcA0Ia1e4wndCoaojBRt0Oc9divCzNLamZzLojRufDoqFSRRHtI3kckQ2HVq0c3kHlBxUUq_BjOW7KBeBlhqeE2jmd-5RuK-oM1E8jT0d6hhf6ev41ReEbCRQY8BQ8DK-_3sLBgkQ=w473-h201 align="left")

click on edit option

![](https://blogger.googleusercontent.com/img/a/AVvXsEgoOsIl0ILiohrXv-sfU0M7et3SnoP7dDo_vpNTS_pTCFtyPX9dpZ6BLZ4Z3yJ1rCTgP6Wt-FdtFl7CyUztk5s7q-bNiPS4DIDHHRygief1x4LSWmXns__8u6dFK0FDAwfcY0HsjyrVn96X-j9VDtjgTJgEjA1F3RnEnhT1LlzYqA62nIJGtXYDD-pFbg=w504-h111 align="left")

  
  
Now click on "NEW" then, copy and paste of terraform file path.

![](https://blogger.googleusercontent.com/img/a/AVvXsEh0FZdJeFdQQl5RftelyiFcSUDbcm55ISuig0uTLA5S8pcAAWwIiD39iBTqxGXDlD6BF7cHoJ7m8vjrMKWszw4cgs-qeIkRG35yNXbmPHIWOnAiH1ZSJCIVu_ZiPAfaO1K_Snbv1ftG4XgPIgFlStoNacig0yun2T8UQBhTCAHQwddRw3nOr0Ur3cjhLQ=w465-h226 align="left")

That's it then click "ok" for save purposes your terraform is installed in windows os.

For confirmation, is your terraform installed or not. Open the command prompt or Windows power shell.

![](https://blogger.googleusercontent.com/img/a/AVvXsEh2o44SdwZJc0kiguaAbCoFMJbPoohD6JaEaUp09_4yoJ6mgaB4lpl7H8d8qrQYJo9P-i0yKPPxMsqwq2WgPg3ZXtkbY-k2InbxnXFwLqR-Dsj3tBEzN8wEh47VtD6wKlvKBfg4ablp4xiK25k6B2nq6Cub1G4TdFJsBH6F7iV49p0pssTsFkyxz5l-hQ=w565-h137 align="left")

  
I am ending this blog here this is the first part of a blog in the second part I will write how to set up the 3-tier application on AWS with Terraform tool.

Thank you for reading this blog. if u like this content,

Follow me on Linkedin; [https://www.linkedin.com/in/ashok-sana](https://www.linkedin.com/in/ashok-sana)

Follow on Whatsapp: [https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3](https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3)

Follow on telegram: [https://t.me/awsdevopscontent](https://t.me/awsdevopscontent)