---
title: 'Set up GitHub pages &#038; Custom domain for GitHub pages'
author: sarathlal
layout: post
tags:
  - GitHub pages
---
GitHub pages are public website / blog for us and our GitHub projects. We can host our static website / blog in GitHub same like our repositories using GitHub pages for free of cost.

If you have a user account in GitHub, you can create a single user / organization pages and multiple project pages for your gitHub repositories. The user / organization pages stand for public website / blog for user or organization. The project pages are public website for our projects hosted in GitHub repositories.

All GitHub pages served over HTTP, not HTTPS. Also they can only handle static files like HTML, CSS, JavaScript etc. The user / organization pages and project pages are almost identical except some points.

##  User / Organization pages

The user / organization pages lives in a custom repository dedicated to serve its files in GitHub.

*   This repository must use the `username.github.io` naming scheme.
*   The content in the `master` branch is use to build and publish the Pages.
*   We can use custom domain for User / Organization pages.

##  Project pages

The Project Pages in GitHub are kept in the same repository as the project they are for.

*   The content in the `gh-pages` branch is use to build and publish the Pages.
*   We can also use custom domain for each project pages.

##  Set up User / Organization pages

*   Create a new repository in github.com with the name `your_username.github.io`.
*   Make a local folder for our GitHub repository.

		mkdir your_repository

*   Then move into that directory.

		cd your_repository

*   Initialize git.

		git init

*   Connect our local repository to our GitHub repository.

		git remote add origin https://github.com/your_username/your_username.github.io.git

*   Make our Website Files (HTML, CSS etc) in that folder and then add them for repository.

		git add .

*   After adding these files to our repo, we need to commit the changes.

		git commit -m "First commit"

*   Then last, we want to push our changes to GitHub.

		git push -u origin master

Now you can meet your website / blog at `http://your_username.github.io`. If it is not happened, please wait for 10 t0 20 minutes.

##  Set up project pages

*   First make a local folder for our GitHub repository.

		mkdir your_repository

*   Then move into that directory.

		cd your_repository

*   Initialize git.

		git init

*   Clone a copy of existing GitHub project repo in to our local folder.

		git clone https://github.com/your_username/your_repository.git

*   Creating an Orphan Branch for this repo that will hold all of our website files.

		git checkout --orphan gh-pages

*   If we already have files in our `master` branch of our GitHub repo, we want to remove these files from the new `gh-pages` branch.

		git rm -rf .

*   Make our Website Files (HTML, CSS etc) in that branch folder and then add them for repository.

		git add .

*   After adding these files to our repo, we need to commit the changes.

		git commit -m "First commit"

*   Then last, we want to push our changes to GitHub.

		git push origin gh-pages

After 10 to 20 minutes, we can reach our project web pages / blog from `http://your_username.github.io/your_repository/`.

##  Custom domain for User / organization and project pages

We already discussed about various GitHub pages and how we can set up them. GitHub pages also allow us to map our custom domain to this pages. That means, we can use our own domain name (URL) for user / organization pages and project pages.

The custom domain help us to keep an identity among community. It is very easy and it cost little bucks.

Setting up custom domain for both type GitHub pages are similar in nature. So following description is applicable for user / organization pages and project pages.

Before any further action, I believe that you already purchased your favorite domain name. I consider that, `http://ourdomain.com` is our custom domain for GitHub pages.

Then we want to set the domain in our repository and change DNS records to look up GitHub pages servers.

###  Set the domain in our repository

*   First create a file named `CNAME` in the root of our pages.
*   The content in that file is our domain name(or sub domain name) only.

		ourdomain.com

*   If you are doing changes in local repo, then add, commit and push files to GitHub remote repository.

###  Modify DNS records for GitHub pages

We want to change DNS records of our custom domain by logging in to control / administration panel of our name registrar.

Actually we&#8217;re telling the registrar that anytime a web user tries to access our site, it should send that user to GitHub&#8217;s servers.

First we want to create a `A` record (short for &#8220;address&#8221;) that maps the domain to the Internet Protocol (IP) address of GitHub. Currently github&#8217;s DNS Zone located at `204.232.175.78` and we want to use it as IP adress in DNS settings.

Then we want to create a CNAME records in DNS settings to handle www requests. Since many users may automatically add a www prefix to any web address, we should tell our registrar to treat the www version of our domain name the same way as the root.

With the help of this change, we can tell the registrar that the www name (www.sarathlal.com) is really an alias, and the official (canonical) name is the root name (sarathlal.com).

Interface for DNS management is entirely different for different registrar. So remember that we want to add two records in DNS settings.

1.  `A` record ( host name / name: ourdomain.com, value or IP address or URL: 204.232.175.78 )
2.  `CNAME` record ( host name / name: www.ourdomain.com, value or IP address or URL: 204.232.175.78 )

After all updates, we want to wait some hours to get it works. Theoretically it can take as long as 3 days for these type of changes to propagate through the INTERNET, although 30 minutes to a couple of hours is more typical.

Once the propagation is complete, we mapped our custom domain in to GitHub pages and then we can use our GitHub pages like `http://ourdomain.com`.

##  conclusion

The git, GitHub and GitHub pages are bit confusing for a beginner to understand. I just write it as a basic intro and you must read other articles and tutorials to get well.

But if you want to swim well, you must be in water. So first make a GitHub account, then make some sample repository for GitHub pages and play with them via commands. The whole things are become easier than you think.
