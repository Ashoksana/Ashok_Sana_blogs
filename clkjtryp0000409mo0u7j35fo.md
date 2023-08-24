---
title: "📝 Blog: Unlocking the Power of Git Stash and Cherry-Pick in DevOps 🚀"
datePublished: Wed Jul 26 2023 14:32:43 GMT+0000 (Coordinated Universal Time)
cuid: clkjtryp0000409mo0u7j35fo
slug: blog-unlocking-the-power-of-git-stash-and-cherry-pick-in-devops
tags: github, git, devops, gitcommands, 90daysofdevops

---

Hey there, DevOps Enthusiasts! 👋

Today, we are going to delve deeper into the world of Git and explore two powerful commands that every DevOps engineer should have in their toolkit: **git stash** and **git cherry-pick.** These commands can work wonders when it comes to managing your code changes efficiently and selectively applying them to different branches.

**Task-01: Git Stash - Saving Changes Like a Pro**

🚀 **Step 1: Create a New Branch and Make Some Changes** You're working on an exciting new feature, and you need to switch to a different branch urgently. But you don't want to commit the changes you've made just yet. Here's where `git stash` comes to the rescue.

👉 Create a new branch:

```bash
$git checkout -b new-feature
```

👉 Make some changes to the files in this branch.

🚀 **Step 2: Save Your Changes with Git Stash** Now that you've made changes that you want to keep, but not commit immediately, it's time to stash them away.

```bash
$git stash
```

Your changes are safely tucked away, and your working directory is clean again!

🚀 **Step 3: Switch to a Different Branch and Make Some Commits** While you were working on your new feature, some urgent bug fixes came up. Switch to the branch where you need to apply these fixes and make the necessary commits.

```bash
$git checkout main
# Make commits with bug fixes
```

🚀 **Step 4: Bring Back Your Stashed Changes** It's time to bring back those awesome changes you stashed earlier and apply them on top of your new commits.

```bash
$git stash pop
```

Voilà! Your stashed changes are now back in your working directory and on top of the new commits you made.

**Task-02: Reflecting Commit Messages from Development to Production**

🚀 **Step 1: Advancing the Development Branch** You've been hard at work on the development branch and added some fantastic features. Let's keep track of the progress with meaningful commits.

```bash
Added feature2.1 in development branch
Added feature2.2 in development branch
Feature2 completed
```

🚀 **Step 2: Creating the Production Branch** Before we reflect the commits from the development branch to production, let's create the production branch from the master branch.

```bash
$git checkout master
$git checkout -b production
```

🚀 **Step 3: Reflecting the Commits with Rebase** To ensure clean and straightforward history in the production branch, we will use `git rebase`.

```bash
$git rebase development
```

Now, the commits from the development branch are neatly reflected in the production branch.

**Task-03: Cherry-Pick for Fine-Grained Code Transfer**

🚀 **Step 1: Cherry-Picking the Optimum Commit** There's a specific feature from the development branch that we want to include in the production branch. Let's cherry-pick the commit.

```bash
$git checkout production
$git cherry-pick <commit-hash>
```

🚀 **Step 2: Enhancing the Cherry-Picked Commit** The cherry-picked commit is now part of the production branch, but we want to optimize it further. Let's make some additional changes.

```bash
This is the advancement of previous feature
Added few more changes to make it more optimized.
```

🚀 **Step 3: Commit the Optimization** We've fine-tuned the cherry-picked feature. Let's commit this optimization!

```bash
$git add .
$git commit -m "Optimized the feature"
```

🎉 Congratulations! You've mastered the art of Git stash, cherry-pick, and even reflected commits between branches. These are valuable skills that will undoubtedly boost your efficiency as a DevOps engineer. Happy coding! 🚀😎

Hope you like my blog...!

If you like the content follow me on LinkedIn: [https://www.linkedin.com/in/ashok-sana](https://www.linkedin.com/in/ashok-sana)

Follow my Whatsapp & telegram community: [https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3](https://chat.whatsapp.com/BzX1aruZIH645l29LxvgO3)

[https://t.me/ExplorewithAshok](https://t.me/ExplorewithAshok)

Happy learning......!