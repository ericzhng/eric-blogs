---
title: 'How to set up Jekyll for github pages in Windows?'
date: 2018-09-14
banner: /eric-blogs/images_posts/github-jekyll.jpg
thumbnail: /eric-blogs/images/github.svg
categories:
- Software
- Website
tags:
  - Windows
  - Jekyll
  - GitHub
  - WSL
---

In this blog, I want to talk about how to set up Jekyll in Windows environment, mainly Windows 10, since you can enable the Linux bash.

<!--more-->

# Major steps

## 1. Set up Linux subsystem in Windows 10
* In Windows 10, go to Settings -> Update & Security -> For Developers, select Developer Mode under "Use developer features".
* Navigate to Control Panel -> Programs and Features, Click "Turn Windows features on or off", and toggle "Windows Subsystem for Linux" to on and click OK to return.
* Restart your computer to take effects.
* After restart, open Bash by searching it in search box, and type "y" to install the linux subsystem.
  * Sometimes, you will be prompted to go to Microsoft Store to download and install it.
  * Choose ubuntu and click "Get" to download and install.
* Create a user name and password for an account.
* If everything goes successfully, you should be able to run common linux commands such as `clear` and `ls` in the Bash.

## 2. Install all necessary files for Jekyll in Linux subsystem
* Open Bash in Windows 10, and update our repo lists and packages
  - `sudo apt-get update -y`
  - `sudo apt-get upgrade -y`

* (Optional) Add the repository from BrightBox, which has an optimized Ruby version in Ubuntu.
   * `sudo apt-add-repository ppa:brightbox/ruby-ng`
* Before we install Jekyll, we need to make sure we have all the required dependencies.
  * `sudo apt-get update`
  * `sudo apt-get install build-essential patch ruby-dev zlib1g-dev liblzma-dev`
  * (might work as well, same function as last commands) `sudo apt-get install ruby ruby-dev make build-essential`
* Update Ruby gems
  * `sudo gem update`
* Install Jekyll
  * `sudo gem install jekyll bundler`
* Test whether Jekyll is installed successfully
  * `jekyll -v`
* Install all of the required gems
  * `bundle install`

## 3. Build your local Jekyll site forked from GitHub
* Open cmd, and type `bash` to get in Bash environment.
* In Bash, navigate to the root directory of your local Jekyll site repository.
* Run following command to run the Jekyll site:
  * `bundle exec jekyll serve`
* Preview the changes in your web browser at "localhost:4000".

# Some common errors

## Error 1
 * When executing `bundle exec jekyll serve`, you may came across errors like the following:
   - "Could not find minitest-5.11.3 in any of the sources"
   - "Run `bundle install` to install missing gems."

 * Solution
   * This is most probably you forget to execute last command in Step 2. Type `bundle install` in Bash and execute. You may be required to input your password.

## Error 2
 * When executing `bundle install`, the following error messages might appear:
   - "Gem::Ext::BuildError: ERROR: Failed to build gem native extension."
   - "An error occurred while installing nokogiri (1.8.4), and Bundler cannot continue. Make sure that `gem install nokogiri -v '1.8.4' --source 'https://rubygems.org/'` succeeds before bundling."

 * Solution
   * First install nokogiri by itself in Linux subsystem ('sudo gem install nokogiri'), then try "bundle install" again!

Reference:
------
* [1] [How to Enable the Linux Bash Shell in Windows 10?](https://www.laptopmag.com/articles/use-bash-shell-windows-10)
* [2] [Setting up your GitHub Pages site locally with Jekyll.](https://help.github.com/articles/setting-up-your-github-pages-site-locally-with-jekyll/)
* [3] [Jekyll on Windows.](https://jekyllrb.com/docs/installation/windows/)
