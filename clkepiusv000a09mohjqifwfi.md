---
title: "Basic Git & GitHub:"
datePublished: Sun Jul 23 2023 00:34:49 GMT+0000 (Coordinated Universal Time)
cuid: clkepiusv000a09mohjqifwfi
slug: basic-git-github
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690073609929/dbb5ed0d-105d-494b-97eb-f4db0070abb9.png
tags: github, git, gitcommands

---

**Introduction:** As a DevOps engineer, mastering version control is crucial to streamline collaborative development and ensure project success. In this blog, we will embark on an exciting journey into the world of Git and GitHub, unraveling their significance, key concepts, and how they revolutionize modern software development. Let's dive in! 🏊‍♂️

**What is Git and Why is it Important? 🎯** Git is a powerful version control system that empowers developers to track changes to files and collaborate seamlessly. Its significance lies in the following aspects:

1. Version Tracking: Git maintains a detailed history of changes, enabling effortless navigation between versions and easy rollback to previous states if needed. ⏳
    
2. Collaboration: Multiple team members can work simultaneously on the same project without conflicts, merging their changes into a unified version. 👥
    
3. Backup & Restore: Git ensures data integrity by storing a distributed copy of the entire repository, reducing the risk of data loss. 💾
    
4. Branching & Merging: Developers can create branches to work on specific features or fixes independently and later merge them into the main codebase. 🌿
    

**Difference Between Main Branch and Master Branch: 🌱** The difference between the "main" and "master" branch lies in the evolving language of inclusivity. Git has made a conscious decision to move away from potentially controversial terms.

In the past, the default branch was called "master," but it is now recommended to use "main" as the default branch name to promote a more inclusive and diverse environment. 🌈

**Explaining the Difference Between Git and GitHub: 🔄** Git and GitHub are often used interchangeably, but they serve different purposes:

1. Git: Git is a distributed version control system that resides on your local machine. It tracks changes and allows version control even without an internet connection. 🖥️
    
2. GitHub: GitHub, on the other hand, is a web-based platform that hosts repositories remotely. It leverages Git's functionality and provides additional collaboration tools, making it an excellent platform for teams to share, collaborate, and contribute to projects. 🌐
    

**How to Create a New Repository on GitHub? 🏗️** Creating a new repository on GitHub is a breeze! Follow these steps:

1. Log in to your GitHub account. 👤
    
2. Click on the "+" icon in the top-right corner and select "New repository." ➕
    
3. Name your repository (e.g., "Devops") and provide an optional description.
    
4. Choose between public or private visibility, depending on your project's needs. 🔒
    
5. Click "Create repository," and voila! Your repository is ready for action. 🚀
    

**Difference Between Local & Remote Repository and Connecting Them: 🏠📡** A local repository resides on your machine, while a remote repository is hosted on a server, like GitHub. Here's the difference:

* Local Repository: It's where you make changes and track version history locally. 🏠
    
* Remote Repository: It's a centralized version of your project hosted on a server accessible by collaborators. 📡
    

To connect your local repository to the remote repository:

1. Create a new repository on GitHub.
    
2. Copy the repository's URL.
    
3. In your local terminal, navigate to your project folder.
    
4. Use the command:
    
    ```bash
    $git remote add origin <repository_url>
    ```
    
    This links your local repository to the remote one.
    

**Tasks:**

**Task-1: Set Your User Name and Email Address** 📝 Before diving into Git and GitHub, configure your user name and email address to be associated with your commits. Use the following commands:

```bash
$git config --global user.name "Your Name"
$git config --global user.email "youremail@example.com"
```

**Task-2: Create a Repository Named "Devops" on GitHub** 🏗️ Follow the steps mentioned earlier to create a new repository named "Devops" on GitHub.

**Connect Your Local Repository to the Repository on GitHub** 🔄 Use the command mentioned in the previous section to connect your local repository to the newly created "Devops" repository on GitHub.

**Create a New File in Devops/Git/Day-02.txt & Add Content** 📄 Using your favorite text editor, create a file named "Day-02.txt" within the "Devops/Git" directory. Add some engaging content to showcase your skills.

**Push Your Local Commits to the Repository on GitHub** 📡 Once you've made your changes, use the following commands to commit and push your changes to the remote repository:

```bash
$git add .
$git commit -m "Added Day-02.txt"
$git push origin main
```

**Conclusion:** 🎉 Congratulations! You've taken a giant leap into the world of Git and GitHub, equipping yourself with the fundamental skills to collaborate, version control, and manage your projects like a true DevOps pro. By harnessing the power of Git and embracing the collaborative nature of GitHub, you are now poised to contribute effectively to your team's success. So, go forth, explore, and let your DevOps journey flourish! 🚀

Hope you like my blog...!

If you like the content follow me on LinkedIn: [https://www.linkedin.com/in/ashok-sana](https://www.linkedin.com/in/ashok-sana)

Follow my Whatsapp & telegram community: [https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3](https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3)

[https://t.me/ExplorewithAshok](https://t.me/ExplorewithAshok)

Happy learning......!