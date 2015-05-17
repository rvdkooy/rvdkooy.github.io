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

Static files? isn't that something that we use 20 years ago?? 
Well yes, but we have much better tooling these days to make it look like a dynamically generated website. Jekyll is such a tool. It uses tool like:

- Liquid to generate your HTML files
- SASS to compile your css files
- Markdown to create articles

On top of that it comes with a local webserver and file watcher to kick off the tooling to generate the entire website for you.

So when I want to create a new blog post, I only have to create a markdown file, put it in the correct folder (_posts) with some predefined values and a new article will apear on my website.

I only have to commit this file and push it to my github pages repository and after a minute or so the article will also be available online.

**Installation**

***Setting up Github pages***

***Getting a template***

***Installing Jekyll***

**Creating a post**

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