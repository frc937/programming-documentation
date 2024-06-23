---
description: An overview of git and how we use it on FRC team 937.
---

# git and How Team 973 Programs

{% hint style="info" %}
**A Note on Capitalization:**

git is intentionally not capitalized here because its proper name is in lowercase, since it is a command-line tool.
{% endhint %}

## Introduction

This is the fourth and final part of our FRC programming crash course, which will go over git, GitHub, and some basic procedures for how we program on FRC Team 937.

## git

We use git as our version control system. If you don't know what version control is, don't worry—we'll cover it in a moment.

We recommend this wonderful video to learn git:

{% embed url="https://www.youtube.com/watch?v=USjZcfj8yxE" %}

Or a text version of the same video available here:

{% embed url="https://videotutorials.notion.site/Introduction-to-Git-ac396a0697704709a12b6a0e545db049" %}

Don't worry about following along, installing git on your machine, or memorizing the exact commands. We'll get you started with a git GUI in a bit, so you won't need to know the exact command-line syntax—just the high-level concepts. We'll also help you install git on your machine, since installing it on the school computers can be tricky.

As a minor correction, the primary branch is now called "main" by default.

## GitHub

We use GitHub to host our git repositories, provide CI/CD through GitHub Actions, and manage Pull Requests.&#x20;

We recommend this wonderful video to learn the basics of GitHub:

{% embed url="https://www.youtube.com/watch?v=nhNq2kIvi9s" %}

Or the text version of the video available here:

{% embed url="https://videotutorials.notion.site/Introduction-to-GitHub-202af6f64bbd4299b15f238dcd09d2a7" %}

## How Team 937 Programs

Generally, each year, we'll roughly follow this paradigm:

1. Create a new command-based robot project and upload it to a GitHub repo. Name the project and the repo `robotXXXX`, with `XXXX` being the year of the season (so `robot2024` for the 2024 season robot)
2. Plan out which programmers are going to implement which features and/or bugfixes
3. Programmers each make a topic branch (or branches) _within the original GitHub repo_ (no need to fork) for each feature/bugfix
4. Once the feature or bugfix is implemented, the programmer creates a PR and student leadership reviews it
5. Rinse and repeat steps 2-4 until the robot is good to go!

More information about our programming norms and how we program can be found here:

{% content-ref url="../reference/programming-norms.md" %}
[programming-norms.md](../reference/programming-norms.md)
{% endcontent-ref %}
