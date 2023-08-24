---
title: "Advance Git & GitHub for DevOps Engineers."
datePublished: Mon Jul 24 2023 15:50:21 GMT+0000 (Coordinated Universal Time)
cuid: clkh1o3n1000309mjavsl3eh0
slug: advance-git-github-for-devops-engineers
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1690213729852/c6fca4e3-3351-4989-ad2a-bddb1ac37892.png
tags: aws, github, git, 90daysofdevops

---

Hey DevOps Engineers! Today, we're diving into the powerful world of Git branching, an essential skill for smooth and organized development. Let's explore the magic of branches and how they help us isolate our work and collaborate effectively.

🌿 **Branches: A Safe Playground for Your Ideas** 🌿

In Git, a branch is like a separate universe where you can work on new features, bug fixes, or experiments without affecting the main codebase. Each repository has a default branch, usually called "master," and we can create multiple other branches to work on specific tasks.

**Creating a Branch:** To get started, let's say we have a repository named "DevOps" and we want to create a new branch called "dev" for our first feature. Here's how we do it:

```bash
$git checkout -b dev
```

💡 Make sure to include a descriptive commit message like "Added new feature" to reflect the purpose of the branch.

🚀 **Let's Collaborate: Local & Remote Repositories** 🚀

We've added a text file called "version01.txt" inside "Devops/Git/" on the "dev" branch with the content "This is the first feature of our application."

**Updating the Local Repository:** Now, we'll commit our changes locally:

```bash
$git add Devops/Git/version01.txt
$git commit -m "Added new feature"
```

📤 **Pushing to the Remote Repository:** To make our changes visible to others for review, we'll push the "dev" branch to the remote repository:

```bash
$git push origin dev
```

🌈 **Growing Our Features: Let's Merge!** 🌈

We've continued to work on the "dev" branch and added three more lines to "version01.txt."

```bash
1st line>> This is the bug fix in the development branch
2nd line>> This is gadbad code
3rd line>> This feature will gadbad everything from now.
```

For each addition, we made a separate commit with appropriate messages.

**Merging the Dev Branch with Master:** To bring our fantastic new features into the main codebase, we'll merge the "dev" branch into "master."

**Git Merge:**

```bash
$git checkout master
$git merge dev
```

🔀 **Git Merge vs. Git Rebase: A Peek Behind the Curtain** 🔀

**Git Rebase:** Let's say we have a feature branch named "feature-branch" that was created from the "master" branch. During development, several commits were made on both branches.

```bash
            A---B---C  (master)
               \
                D---E---F  (feature-branch)
```

When we perform a Git rebase from "feature-branch" onto "master," the commit history is rewritten, and the changes from "feature-branch" are replayed on top of the latest "master" commit.

```bash
                A---B---C  (master)
                       \
                        D---E---F  (feature-branch)
```

💡 **Benefits of Git Rebase:**

* Maintains a cleaner and linear commit history, making it easier to follow the development flow.
    
* Avoids unnecessary merge commits, keeping the commit log tidy.
    

**Git Merge:** In this scenario, let's consider the same "master" and "feature branch" with their respective commits.

```bash
            A---B---C  (master)
               \
                D---E---F  (feature-branch)
```

When we merge "feature-branch" into "master," Git creates a new merge commit to preserve the history of both branches.

```bash
            A---B---C------G  (master)
               \           /
                D---E---F   (feature-branch)
```

💡 **Benefits of Git Merge:**

* Maintains separate logs for each branch, showcasing their unique development paths.
    
* Easily identifies merge points in the commit history.
    

💡 **Choose Wisely: Best Practices for Branching** 💡

Let's follow some industry best practices to keep our Git workflow smooth and organized:

**1\. Meaningful Branch Names:** Use descriptive names to convey the purpose of the branch. Example: "feature-user-authentication," "fix-bug-123," or "refactor-backend-performance."

**2\. Frequent Commits:** Make small, focused commits with clear messages. Example: "Added user authentication logic," "Fixed bug in login form validation," or "Optimized database queries."

**3\. Pull Requests:** Always use pull requests for merging branches to facilitate code reviews. Example: Before merging "feature-user-authentication" into "master," open a pull request and request reviews from team members.

**4\. Regular Updates:** Keep your local branches up to date with remote changes using `git pull`. Example: Before starting a new feature, update your "master" branch with `git pull origin master`.

**5\. Branch Cleanup:** Delete merged branches to keep the repository organized. Example: After merging "fix-bug-123" into "master," delete the "fix-bug-123" branch with `git branch -d fix-bug-123`.

By following these best practices, you'll ensure a clean and collaborative Git environment that will make your development journey more efficient and enjoyable! 🚀🎉

Hope you like my blog...!

If you like the content follow me on LinkedIn: [https://www.linkedin.com/in/ashok-sana](https://www.linkedin.com/in/ashok-sana)

Follow my Whatsapp & telegram community: [https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3](https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3)

[https://t.me/ExplorewithAshok](https://t.me/ExplorewithAshok)

Happy learning......!