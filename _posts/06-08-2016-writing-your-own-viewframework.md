---
title:  "Writing your own viewframework that uses a virtual DOM"
date:   2016-06-08 21:00:00
categories: tech
description: In this article I will describe the reasoning of writing my own javascript viewframework that was inspired by ReactJS
image: /assets/img/writing-your-own-viewframework/react-header.jpg
---

For more than a year now I've been working on a fearly large project where I decided to use ReactJs for building the web frontend.

Building and composing UI components that will rerender when state changes with ReactJS is a great paradigm and it turned out to be a very good choice for us and I really wanted to know how this worked.

So, I knew ReactJs uses a virtual DOM internally to solve the problem of the slow browser DOM [LINK] and after analysing their source code on github (that was not easy to grasp btw), I decided to build something simular by myself to trully understand the concept.

I named my viewframework 'Reren' and after several tries, I now have a 'version' that contains the basic building blocks for creating and composing components that can have its own state and rerenders when it changes.

This demo will again explain the reasoning, how to build a simple component and an existing todo app build with Reren.

<iframe width="560" height="315" src="https://www.youtube.com/embed/vFfNagXrx0k" frameborder="0" allowfullscreen></iframe>

Some lessons that I've learned when writing Reren:

- The elements that you construct in your component !== virtual DOM. They only describe the desired html output. Based on that a new virtual DOM will be constructed and compared to the previous virtual DOM.
- when comparing 2 versions of a virtual DOM you can do some 'naive' approaches. for example: when traversing the virtual DOM tree and detecting that a tag was changed from a 'span' to a 'div', the best thing to do is to throw away the span and all its underlying children (without even looking further) and rebuild the tree from there (continue with the div and it's children). this sounds very strang, but most of the time this is exactly what you want and implementing a smart diffing algorithm that can detect a potential more efficient way too do this is way [too CPU expensive](https://facebook.github.io/react/docs/reconciliation.html#motivation).
- Every element or component in a list needs a unique key to uniquely identify it for detecting a change in order. An index is not good enough because when the order of items change the index will be the same.

I really enjoyed doing this and I encourage everyone who want to know more about any subject to do something simular.

note:
To be clear here: Reren is not intended to be used in production, it was only used as an exercise!

Well that’s all there is!!

If you have any comments, write them below or you can tweet me at (@rvdkooy)