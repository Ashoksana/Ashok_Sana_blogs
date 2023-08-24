---
title: "🔒 Understanding Linux File Permissions and Ownership 🔒"
datePublished: Thu Jul 20 2023 14:28:55 GMT+0000 (Coordinated Universal Time)
cuid: clkb8zydo000709msfrg5227d
slug: understanding-linux-file-permissions-and-ownership
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1689863284883/d9938b9f-cbda-4b2d-bb84-7f73336f2166.png
tags: linux, aws, devops

---

Hey there, fellow tech enthusiasts! Today, we're going to dive into the intriguing world of Linux File Permissions and Ownership. 🐧

So, what's all this fuss about permissions and ownership? In Linux, every file and directory comes with a set of access rights that determine who can do what with it. These access rights are categorized into three groups:

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1689861351358/83432404-2f43-4b62-af86-03a0a2256b2b.png align="center")

1. Owner 👑: The owner of the file or application. This is the individual who created the file or the user who currently holds it.
    
2. Group 🤝: The group that owns the file or application. Groups allow multiple users to share common permissions on files, making it easier to manage access.
    
3. Others 🌍: Everyone else on the system who is not the owner or part of the group. These users have the least privileged access.
    
    Now, let's get hands-on and play with some commands! 😎
    
    ### **Changing Ownership and Group 🧑‍🤝‍🧑🧑‍👧‍👧**
    
    Suppose we have a directory named "project\_files" with its current owner as "Shubham" and group as "Trainwithshubham." Now, we want to change the ownership to "Ashok" and the group to "Explorewithashok."
    
    ```bash
    $ ls -l project_files
    drwxr-xr-x 3 Shubham Trainwithshubham 4096 Jul 20 12:00 project_files
    
    $ sudo chown Ashok:Explorewithashok project_files
    $ ls -l project_files
    drwxr-xr-x 3 Ashok Explorewithashok 4096 Jul 20 12:00 project_files
    ```
    
    Now, "Ashok" is the owner, and "Explorewithashok" is the new group for the "project\_files" directory.
    
    😎 **Group Permission:** The group refers to a collection of users who share common access rights to the file. When a file is created, it inherits the group of the user who created it. The `chgrp` command is used to change the group ownership of a file:
    
    ```bash
    chgrp new_group file.txt
    ```
    
    ### To change permissions for the owner, group, and others simultaneously, we can use a shorthand notation with `chmod`. For instance:
    
    ```bash
    chmod u=rw,g=r,o=r file.txt
    ```
    
    This command grants read and write permissions to the owner, read permissions to the group, and read permissions to others.
    
    ### **Changing Permissions Numerically**
    
    Suppose we have a script called "my\_script.sh" with the following permissions:
    
    ```bash
    $ ls -l my_script.sh
    -rwxr-xr-- 1 sana group3 1024 Jul 20 14:30 my_script.sh
    ```
    
    We want to give the owner full access, the group read and execute permissions, and others no permissions.
    
    ```bash
    $ chmod 750 my_script.sh
    $ ls -l my_script.sh
    -rwxr-x--- 1 sana group3 1024 Jul 20 14:30 my_script.sh
    ```
    
    Now, the owner has read, write, and execute permissions (7), the group has read and execute permissions (5), and others have no permissions (0).
    
    Here's the breakdown of the numeric codes:
    
    * 7 (Owner): Read (4) + Write (2) + Execute (1)
        
    * 5 (Group): Read (4) + Execute (1)
        
    * 0 (Others): (0)
        
    
    ### **Adding and Removing Permissions**
    
    You have a script named "my\_script.sh," and you want to allow the owner to execute it and grant read and execute permissions to the group while removing all permissions from others.
    
    ```bash
    bashCopy code$ chmod u+x my_script.sh    # Add execute permission for the owner
    $ chmod g+rx my_script.sh   # Add read and execute permissions for the group
    $ chmod o-rwx my_script.sh  # Remove all permissions from others
    ```
    
    ### **Access Control Lists (ACL)**
    
    Let's say you have a shared directory called "shared\_docs," and you want to give "user1" read-and-write access and "user2" read-only access to all files inside that directory.
    
    ```bash
    $ setfacl -m u:Shubham:rw shared_docs
    $ setfacl -m u:Ashok:r shared_docs
    ```
    
    Now, "Shubham" can read and write any file inside "shared\_docs," while "Ashok" can only read them.
    
    Example 2: Suppose we have a file called "shared\_file.txt" that should be accessible by multiple users and groups. Let's set specific ACL rules:
    
    ```bash
    bashCopy code$ ls -l shared_file.txt
    -rw-r--r-- 1 userD groupD 512 Jul 20 13:00 shared_file.txt
    
    $ setfacl -m u:userE:rw shared_file.txt  # User "userE" can read and write
    $ setfacl -m g:groupE:r shared_file.txt  # Group "groupE" can read
    
    $ getfacl shared_file.txt
    # file: shared_file.txt
    # owner: userD
    # group: groupD
    user::rw-
    user:userE:rw-      # specific user "userE" has read and write access
    group::r--
    group:groupE:r--    # specific group "groupE" has read access
    ```
    
    ### **Removing ACL Entries**
    
    You realize you mistakenly gave "Ashok" write access to "important\_file.txt" using ACL. Let's fix that!
    
    ```bash
    $ setfacl -x u:Ashok important_file.txt
    ```
    
    This command removes the ACL entry for "Ashok" on "important\_file.txt," reverting them to the default permissions.
    
    😎 Remember, understanding these concepts is vital for maintaining data security and access control on your system. So, keep exploring, and don't forget to have fun with those Linux commands! 🚀🐧💻
    
    Happy hacking! 👩‍💻👨‍💻
    

Hope you like my blog...!

If you like the content follow me on LinkedIn: [https://www.linkedin.com/in/ashok-sana](https://www.linkedin.com/in/ashok-sana)

Follow my Whatsapp & telegram community: [https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3](https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3)

[https://t.me/ExplorewithAshok](https://t.me/ExplorewithAshok)

Happy learning......!