---
title:  "Writing tests with react-testutils-additions"
date:   2015-09-01 21:00:00
categories: tech
description: This article will show one of the great features of react-testutils-additions, finding your components with CSS selectors!
image: /assets/img/writing-tests-with-react-testutils-additions/react-header.png
---
<div style="text-align:center">
<img src="/assets/img/writing-tests-with-react-testutils-additions/react-header.png" alt="ReactJs" width="300px" >
</div>
I'm currently working on a project where we have to replace a classic webforms application to a new/modern front-end stack. 
The frontend is pretty complicated: it is highly configurable, contains lots of workflows and the components have to interact a lot with each other. For that reason, I decided to use ReactJs with a Flux implementation next to it.

I think that ReactJs is an awesome library to build your UI with, because:

- You can componentize everything.
- It combines markup with Js (if you think about it, it makes so much sense!!)
- It's fast.
- It's only a view library, so you can use whatever you want next to it.
- It comes with Testhelpers to test your components in the DOM.

Although the testhelpers are great, some of the API methods made our tests look a bit clunky. Let's show that with an example:

{% highlight javascript %}
// first render it into the document
var Component = ReactTestUtils.renderIntoDocument(<MyComponent />);

// now find all elements with a classname: 'myclassname'
ReactTestUtils.scryRenderedDOMComponentsWithClass(Component, "myclassname");
{% endhighlight %}

OK, that looks a bit weird!

- The method names of the helpers are pretty long and hard to remember.
- As a webdeveloper it feels odd to find your components with an API like this.
- We can't combine these helpers (like: give me all the div's that have both classes 'A' and 'B').

Wouldn't it be great if we could use CSS selectors to find components?

Sure, so I decided to write a package for it. It's called *react-testutils-additions* and it extends the existing React Testutils with some convienent helpers for writing your tests.

By using react-testutils-additions, the earlier example can now be written like this:
{% highlight javascript %}
var Component = TestUtilsAdditions.renderIntoDocument(<MyComponent />);

// now find all elements with class: 'myclassname'
TestUtilsAdditions.find(Component, ".myclassname");

// we can even do this:
TestUtilsAdditions.find(Component, "table#id tr.row");
{% endhighlight %}

Much simpler right? but wait there is more:

I've also created helpers to: 

- clean up your components,
- test your props
- find single components
- and more...

Want to get started with it or need more info, check it out on <a href="https://github.com/rvdkooy/react-testutils-additions" target="_blank">github</a>.

If you have any comments, write them below or you can tweet me at ([@rvdkooy](https://twitter.com/rvdkooy))