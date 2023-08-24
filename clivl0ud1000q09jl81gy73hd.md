---
title: "Building a Web Application with Tomcat and MySQL: A Step-by-Step Guide"
datePublished: Wed Jun 14 2023 10:41:30 GMT+0000 (Coordinated Universal Time)
cuid: clivl0ud1000q09jl81gy73hd
slug: building-a-web-application-with-tomcat-and-mysql-a-step-by-step-guide
tags: aws, mysql, devops, apache-tomcat

---

In today's digital era, web applications have become an integral part of our daily lives. From social media platforms to e-commerce websites, these applications provide us with seamless user experiences and powerful functionalities. Behind the scenes, there are robust technologies working together to make these applications possible.

One such combination is Tomcat and MySQL. Tomcat, a widely used Java-based web server, provides a reliable and scalable environment for hosting web applications. On the other hand, MySQL, a popular open-source relational database management system, offers a robust and efficient way to store and manage data.

In this step-by-step guide, we will explore the process of building a web application using Tomcat and MySQL. We will dive into the key concepts, configuration steps, and best practices that will help you harness the full potential of these technologies.

Whether you are a seasoned developer or a beginner in web application development, this guide will provide you with valuable insights and practical knowledge to get started with building your own web application using Tomcat and MySQL.

So, let's embark on this exciting journey and learn how to build a web application that is reliable, scalable, and data-driven with the powerful combination of Tomcat and MySQL.

Let's start the task....

Open the Aws Management console and login into your account.

Go to the launch instances in the AWS console and create instances as per below steps.

![](https://lh6.googleusercontent.com/CcvWYml6iTs1kRdg93Lc5sQwL1twv8fXANZp8WibO9h5ouh1o8BC_F8ZwC5QKBFcLfMGhrEdprBzh5dlxYnxKqzutps8KPbNI2wPN_R0PvDiOzDfsQbd6P2AIDXDpr2uuLDuVcI8CcakwsiPaQ32Rg align="left")

* Select public subnet and select sg- ssh & tomcat(8080). For private ec 2 select sg- ssh&mysql(3306)
    

![](https://lh4.googleusercontent.com/hbQVyIhabRgp4R0iMsR0UGaRAXi0EGEyY0mAVdfppFz0dbN50dLObHxAlT8gCWph3tyj50M3u35vd-nr99oEMCPKnJxQCF7C3AMKFsHylbTwttC748Sog3dV2nBfe_SKBGZtHrkfESBgep6fFom3FA align="left")

* Connect public instances to terminal app
    

![](https://lh6.googleusercontent.com/7okASLCiSKKfc37ZPuv38Oyp6BNH42mQXeqtPIPHo0usMgMTp2AP8F_fKzwTjjSwk_2urGvJWE1-XTL2mBFvA1vO4YkHOFircI9j4uTu5pIp4CZJ0LsbD0Ct0BW8AmigHuhJnokLWiBovVQCvQOBJQ align="left")

* After connect public ec2 in Terminal and new tab , secure pem file from physical machine to local public ec2 (bastion host) .
    
* Commad is scp -I ……..pem …….pem ec2-user@public ip address:~
    

![](https://lh3.googleusercontent.com/MeWHziDXUfdi6IQxoTYmuaNKndENAy_lv3dwVyWeFv2e9DeP5OF-VrQ-B0g4EGhl707Lcs87UvGSB1JvobULuM9_xZcwnuRD3Tz1SmhKZo8bG_1ozr7TUzMHDf5B9oK6rFtjQ8E44U2HPxszrE59cw align="left")

* Install java
    
* sudo yum -y install java-1.8.0 java-1.8.0-devel
    
* after installation check version ( java -version)
    

![](https://lh5.googleusercontent.com/I1O7CTsDO8bStLbA1vG_uao1kA8Xc8o9NXZwKiIRRrPoMzB4oXO26_8G8vR1yC8XwHG1kEPeXxDl1PzmrFTHKn7PRj22N2CY4RsfqV3KLI4rfYUElVrrAs1rqffW7Q67sac-w1AJl4kiLesUVigSQQ align="left")

* Download Tomcat Binary in /home directory from bowser
    
* Command is wget [https://archive.apache.org/dist/tomcat/tomcat-7/v7.0.94/bin/apache-tomcat-7.0.94.tar.gz](https://archive.apache.org/dist/tomcat/tomcat-7/v7.0.94/bin/apache-tomcat-7.0.94.tar.gz)
    
* **Extract tar file command is tar xvf apache-tomcat-7.0.94.tar.gz**
    

![](https://lh5.googleusercontent.com/1f3JLY1BF5prhoIhJGhdZ-SIIoJGUwJ6cpnGrWHV-4WDtGuyJEOb4AzIGXOxkTIttb11DywJHKaFfk9DBQOtK7F8khPbTjVqpVTsFwiGfIWmLvXLFkX2pNEEet7wjnC3mMpU8SaC58AzdHm2c0TUVg align="left")

* **Now Install git and clone java code**
    
* **Sudo yum install git -y**
    
* **git clone**  [**https://github.com/Ashoksana/aws-rds-java.git**](https://github.com/Ashoksana/aws-rds-java.git)
    
* **By using java code is cloned**
    

![](https://lh5.googleusercontent.com/Y-Tyf_8CjAvb6IoIuHOQHRHlbOxLVk_bwDWw9YSZl_lQ7YLrJAMoB1u94gK0Rrsull1XOdfa6AuU1jlXrsedT2YQdTCQHUhVTPrDuePbgrO583-fR3uxVAEA2LVZH5RDOgHXjlqF6dWSVxDOtUqdZQ align="left")

* **Open cd aws-rds-java**
    
* **Then cd src/main/webapp/**
    
* **Edit file sudo vim sudo login.jsp and userRegistration.jsp**
    

![](https://lh4.googleusercontent.com/yGiRi6GS0s7QDPrTr-SUiYHcesM_2NYadiHZd0vgjftkkOsQbVKnsiDXNWjiAEstLwo0jIS4Mwt_j1jbrkOJ2oXlgIrPAGHM1xlV9NySCyHpRjy56fqBDXuVyRbegCWKvwdvY9q4oLgNa0bwomPx1A align="left")

* **Edit 6th line in both login.jsp & userRegestration.jsp and paste RDS endpoint**
    
* **After go back to home directory cd ~**
    

![](https://lh5.googleusercontent.com/8TNCehRc_MTyIHpuw4cHBqPF60GrKFP8zgvu6b-02TuuiM9yoyQMldpCI55iEIVRNjmYRN0RnDWmYBFp7fEuDWnzZIbv69DIVqjJWBb2uzqnMkQ2TOHpz-vmg8C1ZR10GokoTm8HbnOOXdcTOoLZOw align="left")

* **Open cd aws-rds-java directory.**
    
* **Install maven sudo yum -y install maven**
    
* **Run maven package**
    
* **After mvn package installed in aws-rds-java directory . You will find Target dir & loginwebapp file.**
    
* **This Loginwepp file cp and paste in tomcat apache file.**
    

![](https://lh5.googleusercontent.com/1_YoYG7Lg5NcojjARk25DoG0Uu2Qb1LrRpWZoEymHNBMyMPNUIS_0re3HNyssH51pcxEULG2HmQSXyhjLT5tS2gSFI_rMKhLwIvuLx6lo1suexBrbX5opdegTR_2KeMg2jmRHrqQ8RpRpaa6hkWCHA align="left")

* **Before copying file, check the port 8080 is run or not.**
    
* **Sudo netstat -ntpl.**
    

![](https://lh4.googleusercontent.com/j-SyGjQgKM7FaIyvRSD95UDself5JPtzf8tw5Ibr4G_xbB_Tx8GxGlowvRD36Ur-oDkEufv4B3CChV_fX5tFHiVHQQfH2C40QOLU0r8GbAsBw6rcxufTuUsec5xDS032xlSNiUOfB5M1akNqtBmQ0w align="left")

* **See above pic there is no port 8080.**
    
* **For this You have startup the tomcat apache webserver.**
    
* **cd apache-tomcat-7.0.94/**
    
* **./bin/startup.sh**
    

![](https://lh3.googleusercontent.com/YAzvx6GS_FuF_4AMssxmAyuzPtPKB_11t_bs74saZpWbhZDfMm4pzTHp15POTS4yQcPkxjUbfEiDr0H0jrd7O_olkdjr1xpcGxFSy8qKDXMTFHpu6npQ9gg5q5Dh6-fT6VEEuF1hOBa3oL52HS4vCw align="left")

* Copy Public ec2 ip address and paste it browser.
    
* Ip:8080
    

![](https://lh4.googleusercontent.com/pt7I-o0IfrSyPJ49Y6fV8WFt1EAvcAOXyaGtbUYYkLdgugISa9jtrfoHGRA-b3epQvPiUoYI-sml_JFQe9Ev3Z-CFaAAhU3guPsaJU_OoMlV6MWrIpUQdqOFM0y67QTzOxXW-iI4SVYRGp1n0Uymwg align="left")

* In aws-rds-java/target/
    
* Copy war file paste it in apache-tomcat/webapps/
    

![](https://lh3.googleusercontent.com/SgO7tJb-kwnroEZvomE8U4GTGIxjuiEFrJJiu3ConA5LE1198Z-usdO05kk1iLYQCg-EA5AbvhU95S9CDyBdUeK1uUfooOOVrie3zE3VOCEYSVbLbpWr-hHVCaA7RYxmLxGok5e7GfTZbYdza67r-g align="left")

* Now reload apache-tomcat file. And click the right side   manger app.
    
* You see sign option and press cancel.
    
* **Then after get 401 error page. Go back to terminal and open cd apache-tomcat-7.0.94/**
    
* Edit **sudo vim conf/tomcat-users.xml**
    
* Then after press Shift+g,
    

![](https://lh4.googleusercontent.com/66ept1XN9PqJANh0JOREuK0sx7T0Rvryu43Wz0RLh7aRfzP-pCmcFnUB8xe1YxLMSCdMrBF1YYRe-Fz_kRwOTlWM5jwB06wwGgC_l2RAmGBsosY0HaiB-n49XXtz-kCFQECeQbSDG7ds6Wjt8c-54Q align="left")

![](https://lh6.googleusercontent.com/tgf4437iwMmnxsGdIfsuhTx-dn9fvoE_mud0bRQHmgQkBCnZ2tS1WYIB9suEkfgiY2SIMHrqkzeMwcXzMKRNu_MLEGP_SPLVMg5aCnpxDzsEvIBTXj8j15PFqOELxUf6j2rwLGUPrWG1mN0JmCattA align="left")

* After press Shift+g. you get like this interface.
    
* Above &lt;tomcat user&gt; paste this &lt;role rolename="manager-gui"/&gt;
    

&lt;user username="tomcat" password="tomcat" roles="manager-gui"/&gt;

* Then save and exit :wq
    

![](https://lh4.googleusercontent.com/CFEVWIWrwK3K9vb9mmtib0qKp9sGh3ffbdKxO7mjqlmFPiTR1Kn6bK7jiALyd7DCgV1_TlhyAWyZJsvw9OMOGlHGBLNUSL-BIqp5R2sF-E3TglxCIHvhoBNX8PGILxIDpRiwHtrX9_nEIhuXdXi6OQ align="left")

* After that shutdown tomcat server and again startup server
    
* **cd apache-tomcat-7.0.94/**
    
* ./bin/shutdown.sh
    
* ./bin/startup.sh
    
* Reload the tomcat server
    
* Click manager app, user “tomcat” password “tomcat”
    
* After this type web page will come. And login option also will seen.
    

![](https://lh5.googleusercontent.com/kfajIzdvAHPbl4ouUeZEFkkxFp0cwjm4UVBw3b6FgO1nRpdzouMVhBl6ksNjQ2LI5GzUTZaWTgdFPEj2SQIorMAnrziMF4oLg_IF2t_TR6ef2JXRAJxqvLMvYI4XzWbqWeWkEWXnJXQH2YfdKy6iuQ align="left")

* **In pub ec 2 instances securely copy pem file and paste it in private instance**
    
* **Before that chmod 400 …..pem file**
    
* **Then scp -i …..pem ……pem ec2-user-pvtip:~ (Bastion host)**
    
* **Now connect pvt ec2 instances in pub ec2 instances.**
    
* Install mysql client in pvt ec2 instance.
    
* sudo yum -y install mysql
    

![](https://lh4.googleusercontent.com/08drKdkntOtWqk1Vq_MRYOg12QCML4XH0bQ6JfuFs0ixfejvajXTJJN7A5qtckzMWDXj-RAbKnsKVlfVbF9dq3gemcGV5SNgOmrvhmMghV18AyyNAWUP7GwI25yKdz3i8gxjeYRfKeO-kF3fx293eA align="left")

* And connect the data base of RDS .
    
* Command is mysql -h DB endpoint address -u admin (user) -p and press enter
    
* And create db in name of ‘jwt’ (create datebase jwt;)
    
* Create tables in jwt data base.
    
* Select database (use jwt;)
    
* CREATE TABLE `USER` (
    

`id` int(10) unsigned NOT NULL auto\_increment,

`first_name` varchar(45) NOT NULL,

`last_name` varchar(45) NOT NULL,

`email` varchar(45) NOT NULL,

`username` varchar(45) NOT NULL,

`password` varchar(45) NOT NULL,

`regdate` date NOT NULL,

PRIMARY KEY (\`id\`)

) ENGINE = InnoDB DEFAULT CHARSET = latin1;

![](https://lh5.googleusercontent.com/O9XPOBAXtot8uGisehF0NYOqzaxldWcS0SPwHIJpFPSGn7wT1i05HSOD5YKstv4nrJFH3HS3HoaDylsZwKbGrK93ibmXWzoLqv0aMlEXAPyqNxqUi9ukqmMm3xglE5Iws-C9c0uDrmDt7RQRFaSYSg align="left")

![](https://lh6.googleusercontent.com/peH97tOIKfR3rtuLWVvQpRw_1YimzYwSv_Mi97UlSqKpIjrcB1mq_kXAPkrjunG6TUML5g1Yd4S2vdD0YATTZu4AHflDAjqEoID4UyVLUInDZp0QUcmf4MAG1pVlctB7kQ3LC-TK3hVqGxcZNUG8XA align="left")

* Now go back to tomcat web page and click loginwepp.
    
* Then register in that page.
    
* 1st name; Ashok; last name: Sana; email: [sanaashokreddy1997@gmail.com](mailto:sanaashokreddy1997@gmail.com); User name: Reddy; password: reddy123
    
* And click submit.
    
* And go back to tables of db jwt and show tables above  date is seen in our tables.
    

![](https://lh5.googleusercontent.com/Ub8MHq15jQx8kc3U-JTw3rfIKCH6TOrk-0HmJUSMdlnXw_KnqFNJ9qizrw-9Xaj_u7CS7N-77RXDnyg5Jzfs8LzTqxwWqb2EIn3sdmNk-WW5U9ctT_AEsA6Zud0a4hz5h3rOFSe96mr8RXo7FY4DDQ align="left")

![](https://lh4.googleusercontent.com/rcPmpepXcnvuzm5NZ47lh2v2hHA5fKWHD4E1Dmy8TxIJ-Foh7nP4vjt85pDE82lTw0clrM6bkaGdjYqTLEO-E-0mI3F_wSLns33Y-XLV0axW3hINkmMIcb-6O5x9bFkztZO8cj1c1dVM2IXvBv0CUA align="left")

Conclusion:

Congratulations on completing our step-by-step guide to building a web application with Tomcat and MySQL! You've learned how to create a powerful and efficient web application using Tomcat as the web server and MySQL as the database management system.

Here are the key takeaways:

Tomcat provides a reliable platform for hosting Java-based web applications, while MySQL offers a robust and efficient way to store and manage data.

You've learned how to configure Tomcat and MySQL, including setting up server environments, creating databases, configuring connections, and deploying web applications.

Remember to follow best practices for securing your applications, optimizing performance, and monitoring.

Building web applications is an iterative process, and with the knowledge gained from this guide, you'll be able to enhance your application's performance, security, and functionality over time.

Thank you for joining us on this journey. If you have any questions or feedback, feel free to reach out. Happy coding and best of luck with your future web application projects!

#Tomcat #MySQL #WebApplication #Java #Database #Development