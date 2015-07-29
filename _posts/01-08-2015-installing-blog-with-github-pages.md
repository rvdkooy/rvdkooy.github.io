---
title:  "Installing a blog with github pages"
date:   2015-08-01 21:00:00
categories: tech
---

**Intro**

This is the first article that I'm writing for my new blog. What better topic than explaining how I installed it with the use of github pages and the Jykell static site generator?

**But...why??**

I was looking for an easy way to setup a blog and I remembered that a while ago Github added support for the Jekyll static site generator. 

- I like working with git and for me to use git commands to manage content, really makes sense.
- Its a really simple model: you create your articles in markdown and Jykell takes care of the rest by generation plain static html files for you.
- Speed, nothing renders faster than just static files.

Static files? isn't that something that we used 20 years ago?? 

Well yes, but we have much better tooling these days to dynamically generate a website that looks like it was built with a blogging engine behind it. Jekyll is such a tool. It uses conventions and tools (Liquid, SASS and markdown) to generate your website.

So let's get started:

**Installation**

***Requirements***

These are the settings that I use:
- Windows machine
- Chocolatery installed
- A texteditor which has good support for markdown (I use sublime with the markdown preview plugin)

***Setting up Github pages***

Create a repository in Github and name it: yourusername.github.io, go to the settings of the repo and use the site generator to create your website.

Or... browse the internet for more templates ([this is a nice site](http://jekyllthemes.org)), go to the author's github page, fork the repo and then rename it to yourusername.github.io.

Now clone your repo to your local drive.

***Installing Jekyll***

So now you have a clone of your github page on your local drive, we now have to install Jekyll to generate the site and start creating some nice articles.

Jekyll comes as a ruby gem/package and therefore we have to install ruby and the ruby devkit first. Getting ruby and the devkit working on a windows machine is not very straightforward as I was expecting, so these are the steps that I had to follow to get it working on my machine:

{% highlight text %}

cinst ruby
cinst ruby2.devkit
cd c:\tools\devkit
ruby dk.rb init

edit the file config.yml and add below the 3 dashes:
- C:\tools\ruby21

ruby dk.rb install 

{% endhighlight %}

now install Jekyll:

{% highlight c %}

gem install jekyll

{% endhighlight %}

For code snippets in my articles I use text highlighting in my markdown files. This is parsed by Pygments which is depending on Python. Because I don't want to depend on all these development environments I decided to use Rouge to parse my highlighted text, which is build on top of ruby. To change this I had to install Rouge first and configure Jelyll to use the Rouge parser to parse my highlighted text snippets.

{% highlight c %}

gem install rouge

{% endhighlight %}

Open your Jekyll _config.yml file (it is in the root of your website) and add the following line:

{% highlight yml %}

highlighter: rouge

{% endhighlight %}

With this, you should be ready to start, now type:

{% highlight c %}

jekyll serve --watch

{% endhighlight %}

from your website root folder

This will:

- Generate a folder with the name "_site" which will contain your compiled website.
- Start up a webserver running on port 4000 (default), where you can access your website.
- Watch for changes and regenerate the _site folder again when a file change occurs, this is partically handy when you are making changes and you want to see them immediately when you refresh you browser.

**Creating a post**

So when I want to create a new blog post, I only have to create a markdown file with the following format: YYYY-MM-DD-title.md, put it in the _posts folder and Jekyll takes care of the rest. 

now when I look in the _sites folder I see a generated html file:

![alt text](/assets/img/installing-blog-with-github-pages/generated-html-file.png "Generated html file")

this file is the actual file that will be served to the visitors of your website.

**Publish to github**

This part is really easy:
It uses Git, so I only have to commit and push my changes to my github repo to publish it.

{% highlight c %}

git add .
git commit -m "my first article, yeah"
git push

{% endhighlight %}

If you wait a minute or so, github will pick up your changes and compiles you website (the same thing that's happening on your local machine) and your new content should be available soon!

Well that's all there is!!

If you have any comments, write them below or twitter me at ([@rvdkooy](https://twitter.com/rvdkooy))