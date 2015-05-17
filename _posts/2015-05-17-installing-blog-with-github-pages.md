---
title:  "Installing a blog with github pages"
date:   2015-05-17 21:00:00
categories: tech
---

**Intro**

This is the first article that I'm writing for my new blog. What better topic than explaining how I installed it with the use of github pages and the Jykell static site generator?

lets go:

**But...why??**

I was looking for an easy way to setup a blog and off course there was the obvious choice of installing wordpress, but I really dislike wordpress!! (the reason is out of scope, maybe I will do another post on this later :-) ). I remembered that Github added support for the Jekyll static site generator. So, I thought: lets try this one because I use Github all the time and as a developer the possibilities are unlimited.

**Github and Jekyll**

Github has to ability to serve a static website for you which is called github pages. You basically set up a repository and you can use git to pull, push, commit, branch and merge to get your files into that repository and Github takes care of serving those files.

Static files? isn't that something that we used 20 years ago?? 

Well yes, but we have much better tooling these days to make it look like a dynamically generated website. Jekyll is such a tool. It is a static website generator which uses conventions and tools like Liquid, SASS and markdown to generate your website.

**Installation**

***Setting up Github pages***
There are two ways to setup github pages:
You can create a repository and name it: username.github.io, go to the settings of the repo and use the site generator where you can pick some nice themes and generate articles.

or you can browse the internet for more templates ([this is a nice one](http://jekyllthemes.org))
go to the authors github page, fork the repo, rename it to username.github.io and clone it locally to start creating articles or make some adjustments in the theme. I did the latter.

***Installing Jekyll***
So now you have a clone of the theme on your local drive, we now have to install Jekyll to generate the site and some articles.

Jekyll comes as a ruby gem/package and therefore we have to install ruby and the ruby devkit. For installation guidance for your OS go to [here](https://www.ruby-lang.org/en/documentation/installation/)


install Jekyll:

{% highlight c %}

gem install jekyll

{% endhighlight %}

For a more complete Jekyll Guidance go to the [documentation](http://jekyllrb.com/docs/installation/)

browse to your cloned github pages repo and type:

{% highlight c %}

jekyll serve --watch

{% endhighlight %}

This will:

- Generate a folder with the name "_site" in the which will contain your complete compiled website
- Start up a webserver running on port 4000 (default), where you can access your website.
- Watch for changes and regenerate the _site folder again when a file change occurs, this is partically handy when you are making changes and you want to see them immediately when you refresh you browser.



**Creating a post**

So when I want to create a new blog post, I only have to create a markdown file, put it in the _posts with 
and a new article will apear on my website.

I only have to commit this file and push it to my github pages repository and after a minute or so the article will also be available online.

**Customizations**

**links**






<!-- 

 * lorem
 * ipsum

1. dolor
2. sit

| First Header | Second Header |
|--------------|---------------|
| Table Cell   | Table Cell    |

**Blockquote**

> They who can give up essential liberty to obtain a little temporary safety, deserve neither liberty nor safety.
> 
> _Benjamin Franklin_

**Code**

{% highlight c %}

static void asyncEnabled(Dict* args, void* vAdmin, String* txid, struct Allocator* requestAlloc)
{
    struct Admin* admin = Identity_check((struct Admin*) vAdmin);
    int64_t enabled = admin->asyncEnabled;
    Dict d = Dict_CONST(String_CONST("asyncEnabled"), Int_OBJ(enabled), NULL);
    Admin_sendMessage(&d, txid, admin);
}

{% endhighlight %}
 -->