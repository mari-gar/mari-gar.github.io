---
layout: post
title:  "How to create a GitHub pages website"
date:   2021-01-31
categories: GitHub
---

*Special Note: This guide is made by a beginner for beginners. If you come across any type of error, my best advice is to go to [Stack Overflow for help.](https://stackoverflow.com/questions/tagged/github-pages)* 

Setting up a website with Github Pages isn't quite user-friendly even with hundreds of guides out there. It is tempting to simply set it up using a few themes already available when you create your website for the first time [using this guide to GitHub Pages](https://guides.github.com/features/pages/). However, you will soon find out that this can be a more complicated approach into building a website on GitHub, which I can attest to by personal experience.

I have pulled the following instructions from different sources and summarized them so that it's easy to follow for a beginner like me who has zero knowledge but quite resourceful. Simply enter the codes in the same order and replace terms whenever it is required. 

In this method, you will generate a local repository (i.e., folder) for your website which you will push (i.e., upload) to an online repository for your website on GitHub.

1. **Install Git Bash.** Follow this link for more info: [How to install Git](http://blackwell.math.yorku.ca//tmp/happygit/happy-git-with-r/_book/install-git.html)

    Git Bash is your command line terminal where you will put all your codes in. You can only type one line of code at a time. In this guide, you will sometimes see codes with multiple lines. In reality, you type one line, hit enter, then type the second line and hit enter.

2. **Connect to your GitHub account using Git Bash.** Doing this will enable you to push your local repository online on GitHub. 

    Type the following code into Git Bash (or aka command line). Update `email@example.com` with either your (1) GitHub-provided private email, or (2) the email you used to register for a GitHub account. Your private email can be found in your [Email Settings](https://github.com/settings/emails) which is in the format `ID+username@users.noreply.github.com`. If you want to use your actual email, you must uncheck *Block command line pushes that expose my email* in the [Email Settings](https://github.com/settings/emails). You can read more about [emails on GitHub here.](https://docs.github.com/en/github/setting-up-and-managing-your-github-user-account/setting-your-commit-email-address)

    ```
    $ git config --global user.email "email@example.com"
    ```

    You will receive a notification to authorize this connection via your web browser. Follow the instructions to authorize this connection and move to the next step.

3. **Set up your GitHub Pages site.** Follow the instructions here: [Setting up GitHub Pages](https://docs.github.com/en/github/working-with-github-pages/creating-a-github-pages-site)

4. **Install Ruby.** Follow the instructions here to install Ruby: [How to install Ruby](https://www.ruby-lang.org/en/documentation/installation/#rubyinstaller)

    Ruby is required for using gems (a type of command) and gems are required to install Bundler and Jekyll. Bundler makes it easy to get Jekyll up and running. And finally, Jekyll is the most convenient way to use website themes and other website functionalities. It creates the entire framework for the website for you.

    The following are combined instructions from [GitHub guide to Jekyll](https://docs.github.com/en/github/working-with-github-pages/creating-a-github-pages-site-with-jekyll) and [Jekyll's Guide to using Jekyll with Bundler](https://jekyllrb.com/tutorials/using-jekyll-with-bundler/)
 
5. **Install Bundler.** You can either install Bundler on your default root folder or you can create a new root folder for this (so it doesn't mess up with all your other files, etc.). If you want to make a new root folder, use the following code on your command line:

    ```
    $ mkdir ROOTFOLDER
    ```

    If you don't want to make a root folder, simply skip the above code and use the following to install Bundler.

    ```
    $ cd ROOTFOLDER
    $ gem install bundler
    ```

6. **Create a Gemfile in the same folder.** Use the code below to create a Gemfile.

    ```
    $ bundle init
    ```

    In the Gemfile for Bundler, delete all existing content and replace it with the latest content as shown in the installation procedure in the [Bundler website](http://bundler.io). Save the file and exit.

7. **Make a repository for your website.** To create a repository (i.e., folder), replace `WEBSITEFOLDER` in the code below with the name of your repository on GitHub. Then change the directory folder to `WEBSITEFOLDER`. 

    ```
    $ git init WEBSITEFOLDER
    $ cd WEBSITEFOLDER
    ```

   The branch for this repository is set to `(master)` by default. A branch is a version of the master. You can only use one active branch for the website at a time. You may add or change the branch you use according to the instructions on [#6 at GitHub guide to Jekyll](https://docs.github.com/en/github/working-with-github-pages/creating-a-github-pages-site-with-jekyll)

9. **Set up Jekyll using Bundler.** Use the codes below. You can find more explanation for this in [Jekyll's tutorial on using Bundler](https://jekyllrb.com/tutorials/using-jekyll-with-bundler/).

    ```
    $ bundle config set --local path 'vendor/bundle'
    $ bundle add jekyll
    $ bundle exec jekyll new --force --skip-bundle . 
    $ bundle install
    ```

10. **Update GitHub Pages version in your Gemfile.** Open the Gemfile inside the `WEBSITEFOLDER` and replace `VERSION` with the actual number for the latest Github Pages [dependency version](https://pages.github.com/versions/):

    ```
    $ gem "github-pages", "~> VERSION", group: :jekyll_plugins
    ```

11. **View your website!** To see how your website looks like run the following code to make the site active on a local URL: http://127.0.0.1:4000

    ```
    $ bundle exec jekyll serve
    ```

11. **Connect your local repository to your online repository.** Replace `USERNAME` with your GitHub username on the code below.

    ```
    $ git remote add origin https://github.com/USERNAME/USERNAME.github.io.git
    ```

12. **Push the repository to GitHub.** In this case, the default branch name is `master`.

    ```
    $ git push -u origin BRANCH
    ```

If your website is set to public, you should see your website live and online!
 

### Creating and Updating your website

Pages and posts are text files you can create using your Notepad but are saved as a `.markdown` or `.md` file format. You can learn how to format using markdown using [this guide](https://guides.github.com/features/mastering-markdown/). 

Follow [this guide for to make a blog post](https://jekyllrb.com/docs/posts/) and [this guide to create a web page](https://docs.github.com/en/github/working-with-github-pages/adding-content-to-your-github-pages-site-using-jekyll).

You can create a post in three ways: 
**First**, you can [create it within GitHub using this guide](https://docs.github.com/en/github/working-with-github-pages/adding-content-to-your-github-pages-site-using-jekyll). 

**Second**, you can create the markdown file locally and and [upload it on GitHub.](https://github.blog/2016-02-18-upload-files-to-your-repositories/)

**Lastly**, you can [push the locally created markdown file to GitHub via the command line.](https://docs.github.com/en/github/managing-files-in-a-repository/adding-a-file-to-a-repository-using-the-command-line).

To use the command line, replace `FOLDER/FILE.md` with the path to the file you want to push. Replace `COMMENT` with your comment about the file. This is necessary to complete the `git commit` step. Lastly, replace `BRANCH` with the branch where you saved your website as. In this case, it is `master`.

    ```
    $ cd WEBSITEFOLDER
    $ git add FOLDER/FILE.md
    $ git commit -m "COMMENT"
    $ git push origin BRANCH
    ```

If no error comes up, then your update is successful! 