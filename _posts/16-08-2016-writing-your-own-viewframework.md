---
title:  "Writing your own viewframework that uses a virtual DOM"
date:   2016-08-16 21:00:00
categories: tech
description: In this article I will describe the reasoning of writing my own javascript viewframework that was inspired by ReactJS
video: https://www.youtube.com/embed/vFfNagXrx0k
---

Writing your own view framework, really? why do you want to do that?


Well, for more than a year now I've been working on a large project where I decided to use ReactJs for building the web frontend.
Building and composing the UI with components that will rerender when state changes with ReactJS is a great paradigm and it turned out to be a very good choice for us.

So, I really wanted to know how all of this worked and aftere analyzing their source code on github (that was not easy to grasp btw), I decided to build a similar thing by myself to truly understand the concept.

I named my view framework 'Reren' and after several tries, I now have a 'version' that contains the basic building blocks for creating and composing components that can have its own state and rerenders when it changes with the help of my own virtual DOM.

I recorded this video to explain the reasoning, how to build a simple component and an existing todo app build with Reren.

<iframe width="560" height="315" src="https://www.youtube.com/embed/vFfNagXrx0k" frameborder="0" allowfullscreen></iframe>

Some lessons that I've learned while writing Reren (that also apply to ReactJs):

- The elements that you construct in your component !== virtual DOM. They only describe the desired html output. Based on that a new virtual DOM will be constructed later on to be compared with the previous virtual DOM.
- when comparing 2 versions of a virtual DOM you can do some 'naive' approaches. For example: when traversing the virtual DOM tree and detecting that a tag was changed from a `span` to a `div`, the best thing to do is to throw away the `span` and all its underlying children (without even looking further) and rebuild the tree from there (continue with the `div` and it's children). This sounds very strange, but most of the time this is exactly what you want and implementing a smart diffing algorithm that can detect a potential more efficient way too do this is way [too CPU expensive](https://facebook.github.io/react/docs/reconciliation.html#motivation). So this is an accepted tradeoff.
- Every element or component in a list needs a unique key to uniquely identify it for detecting a change in order. An index is not good enough because when the order of items change the index will be the same, resulting in a very ineffecient diff between the current and previous virtual DOM.
- I had to write out all the possibilies when comparing two trees and writing tests for it was an absolute MUST to prevent regression bugs!

I really enjoyed doing this and I encourage everyone who want to know more about any subject to do something similar.

Note:
To be clear here: Reren is not intended to be used in production, it was only used as an exercise!

Well that’s all there is!!

If you have any comments, write them below or you can tweet me at (@rvdkooy)