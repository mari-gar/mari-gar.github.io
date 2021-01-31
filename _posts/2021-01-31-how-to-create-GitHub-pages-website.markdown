---
layout: post
title:  "How to create a GitHub pages website"
date:   2021-01-31
categories: GitHub
---

Setting up a website with Github Pages is absolutely daunting because of hundreds of guides out there (including this!) and so it is tempting to simply set it up using a few themes already available when you create your website https://guides.github.com/features/pages/. However, you will soon find out that this can be a more complicated approach into building a website using GitHub Pages, very much like how I did some time ago.

If you prefer to have everything set up for you, setting up Jekyll on your website is the best way to go although this method is not without its own set of challenges. Many guides have taken me right in the middle of how to build the website without considering that I know very minimal about how everything works. This guide is built for anyone who is like me - a resourceful beginner. 

1. Install Git Bash. Follow this link for more info: http://blackwell.math.yorku.ca//tmp/happygit/happy-git-with-r/_book/install-git.html

Git Bash is your terminal where you will put all your codes in.

2. On Git Bash, connect to your Github account using your commit email. Doing this will enable you to push your local repository online, to your GitHub account. Make sure in your Email settings that your that you have unchecked the option for *Block command line pushes that expose my email.* For more info go to: https://github.blog/2017-04-11-private-emails-now-more-private/

```
$ git config --global user.email "email@example.com"
```

You will receive a notification to authorize this connection.

3. Set up your GitHub Pages site: https://docs.github.com/en/github/working-with-github-pages/creating-a-github-pages-site

4. Install Ruby. Follow this link for more info: https://www.ruby-lang.org/en/documentation/installation/#rubyinstaller

Ruby is required for using gems and gems are required to install Bundler and Jekyll.

The following are combined instructions from https://docs.github.com/en/github/working-with-github-pages/creating-a-github-pages-site-with-jekyll and https://jekyllrb.com/tutorials/using-jekyll-with-bundler/
 
5. Now we're ready to install Bundler. You can either install Bundler on your default root folder or you can create a new root folder for this (so it doesn't mess up with all your other files, etc.). If you want to make a root folder, follow the below:

```
$ mkdir ROOTFOLDER
$ cd ROOTFOLDER
$ gem install bundler
```

If you don't want to make a root folder, simply skip the first line above and start with the second line.

6. Create a gemfile in the same folder.

```
$ bundle init
```

7. In the Gem file for Bundler, delete all existing content and replace it with the latest content as shown in the installation procedure in the Bundler website http://bundler.io. Save this file and exit.

8. Make a repository for your website (a folder for your website but in GitHub terms). This will create a folder with git file inside.

```
$ git init WEBSITEFOLDER
```

Change the directory folder to WEBSITEFOLDER. The branch for this folder is set to `(master)` folder by default. A branch is a version of the master. You can only use one active branch for the website at a time. 

```
$ cd WEBSITEFOLDER
```

The following sets up Jekyll using Bundler. You can find more explanation for this in Jekyll's website: https://jekyllrb.com/tutorials/using-jekyll-with-bundler/

```
$ bundle config set --local path 'vendor/bundle'
$ bundle add jekyll
$ bundle exec jekyll new --force --skip-bundle . 
$ bundle install
```

9. Open the Gemfile inside the WEBSITEFOLDER and replace VERSION with the actual number for the latest Github Pages version:

```
$ gem "github-pages", "~> VERSION", group: :jekyll_plugins
```

10. To see how your website looks like run the following code to make the site active on a local URL: http://127.0.0.1:4000

```
$ bundle exec jekyll serve
```

11. Now, time to connect it to your account. Add WEBSITEFOLDER to your GitHub URL:

```
$ git remote add origin https://github.com/USERNAME/USERNAME.github.io.git
```

12. Push the repository to Github. In this case, the default branch name is `master`

```
$ git push -u origin BRANCH
```

13. Whenever you want to update your file locally and push it to GitHub, go to: https://docs.github.com/en/github/managing-files-in-a-repository/adding-a-file-to-a-repository-using-the-command-line

Check if update is successful:

```
$ git status
```

If you have any problems regarding installation, Google and Stackoverflow are your best friends!