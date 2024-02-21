---
title: "Stow - Manage your dotfiles with ease."
date: 2024-02-19
description: "Why stow is great and how to get set up!"
draft: true
---

# Use Stow for Your Dotfiles. Please.

Ever since I took an interest in dotfiles (*I blame you emacs*) and their magical ability to configure applications and tweak each little setting to my liking, I've been hooked. I spend more time configuring things than using them, _in the true developer way_.

However, I always ran into one issue: I have multiple hard drives and have never found a great way to manage my config files. I always had slightly different configs based on the machine I was on, due to the nature of tweaking as I go. Well, not anymore! **Stow** is incredible. I've been using it for a while now, and it's made my life much easier.

# Well, What is Stow?

[Stow](https://www.gnu.org/software/stow/) is a powerful symlink farm manager that simplifies the task of managing and deploying software packages, especially useful for handling dotfiles across multiple machines.

As described by themselves:

> It takes distinct packages of software and/or data located in separate directories on the filesystem and makes them appear to be installed in the same place.

Couple this with using Git to store all of your config files, and you can easily manage them all in one repository/directory. It's bliss.

So, let's get into setting it up!

# Guide

## Step 1: Git and Stow

First things first: make sure you've got Git and Stow installed. Installing Stow is as easy as whispering sweet nothings into your terminal:

``` shell
sudo apt-get install stow # For Debian/Ubuntu
brew install stow # For the macOS crowd, I believe
```

And Git, well, if you haven't got Git, I'm surprised you found this article.

## Step 2: Quick Setup

Kick things off by creating a dedicated Git repository for your dotfiles.

`mkdir ~/dotfiles cd ~/dotfiles git init`

Think of this new folder as your home directory, so you want to replicate its structure within the folder.

If you have your Alacritty config at 

`~/.config/alacritty/alacritty.toml`

then it should be the same, i.e.

`~/dotfiles/.config/alacritty/alacritty.toml`.

## Step 3: Stow Away Your Treasures

While there are other methods, I found the easiest way was to move the configs I needed using something like `mv` to my dotfiles repository and then using `stow .`. This command sym-links your files back to their original locations in your `dotfiles` repository.

## Step 4: Commit to Git!

Now they're all being managed in a non-hidden directory. Cool, but you don't get the full benefit of this until you add Git into the mix. Pushing them to a remote repository means that no matter where you are, or how many times you've reinvented your machine, your personalised setup is just a few commands away.

``` shell
git add .
git commit -m "Behold, my dotfiles!"
git remote add origin <remote-repository-url>
git push -u origin master
```

Now, if you make a change in `~/.config/alacritty/alacritty.toml`, then when you go back to your dotfiles repo, you will see (with a good ole `git status`) that you can commit and manage those files with version control. This also lets you pull in any config changes from other machines at any time or revert your changes after breaking them!

# Conclusion

I love Stow, and in tandem with Git, this is your toolkit for managing dotfiles across your many machines and systems. It provides a straightforward, reliable method to ensure your environment is always just the way you like it, no matter where you find yourself.

It's easy, and it works. What more can you ask for?

# Want to know more?

- Incredible video & aeshtetically pleasing video by [Dreams of Autonomoy](https://www.youtube.com/watch?v=y6XCebnB9gs)
- [Stows Website](https://www.gnu.org/software/stow/) previously linked