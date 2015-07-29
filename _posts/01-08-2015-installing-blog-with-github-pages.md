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

{% highlight c %}
cinst ruby
cinst ruby2.devkit
{% endhighlight %}

goto the c:\tools\devkit folder and type:

{% highlight text %}
ruby dk.rb init

edit the file config.yml and add below the 3 dashes:
- C:\tools\ruby21

ruby dk.rb install 
{% endhighlight %}

This will configure the ruby devkit, which we need to be able to run Jekyll.

Now install Jekyll:

{% highlight c %}
gem install jekyll
{% endhighlight %}

For code snippets in my articles I use text highlighting in my markdown files. This is parsed by the Jekyll plugin Pygments.rb which is depending on Python. We now need to install python2 (pygments.rb gem does not work with Python3)

{% highlight c %}

cinst python2

{% endhighlight %}

With this, you should be ready to start, now from your website root folder type:

{% highlight c %}

jekyll serve --watch

{% endhighlight %}

This will:

- Generate a folder "_site" which will contain your compiled website.
- Start up a webserver running on port 4000 (default), where you can access your website.
- Watch for changes and regenerate the _site folder again when a file change occurs, this is partically handy when you are making changes and you want to see them immediately when you refresh you browser.

**Creating a post**

So when I want to create a new blog post, I only have to 

- create a markdown file in the _posts folder with the following format: YYYY-MM-DD-title.md, 
- start your file with some meta data: 
{% highlight c %}
---
title:  "Installing a blog with github pages"
date:   2015-08-01 21:00:00
categories: tech
---
{% endhighlight %}

and Jekyll takes care of the rest. 

now when I look in the _sites folder I see a generated html file:

![alt text](/assets/img/installing-blog-with-github-pages/generated-html-file.png "Generated html file")

this file is the actual file that will be served to the visitors of your website.

you can check this when you open your browser and go to: http://localhost:4000

**Publish to github**

So when you article is ready to be published, you use git commands:

{% highlight c %}

git add --all // stages all your changed files
git commit -m "my first article, yeah" // creates a commit with a message
git push // pushes the changes to github

{% endhighlight %}

If you wait a minute or so, github will pick up your changes and compiles you website (the same thing that's happening on your local machine) and your new content should be available soon!

Well that's all there is!!

If you have any comments, write them below or twitter me at ([@rvdkooy](https://twitter.com/rvdkooy))