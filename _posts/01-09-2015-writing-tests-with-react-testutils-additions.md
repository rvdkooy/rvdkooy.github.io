---
title:  "Writing tests with react-testutils-additions"
date:   2015-09-01 21:00:00
categories: tech
description: test
image: /assets/img/writing-tests-with-react-testutils-additions/react-header.png
---

<img src="/assets/img/writing-tests-with-react-testutils-additions/react-header.png" alt="ReactJs" width="300px" >

I'm currently working on a project that involves replacing a classic webforms application to a new/modern frontend stack. The frontend is pretty complicated: it is highly configurable, contains lots of workflows and has components that interact with each other, so I decided to use ReactJs (with a Flux implementation next to it). 

ReactJs is an awesome library to build your UI with, for me these are the main benefits:

- You can componentize everything.
- It combines markup with Js (if you thing about it, it makes so much sense!!)
- It's fast.
- It is easy to learn.
- It's only a UI library, so you can use whatever you want next to it.
- ReactJs and Flux complement each other so well.
- It comes with Testhelpers to test you components.

Althought the testhelpers are great, the API made our tests look a bit cluncky. Let's show that with an example:

{% highlight javascript %}
// first render it into the document
var Component = ReactTestUtils.renderIntoDocument(<MyComponent />);

// now find all elements with a classname: 'myclassname'
ReactTestUtils.scryRenderedDOMComponentsWithClass(Component, "myclassname");
{% endhighlight %}

OK, that looks a bit weird!

- The method names of the helpers are pretty long and hard to remember.
- For a webdeveloper it feels odd to find your components like this.
- We can't combine these helpers (like: give me all the div's that have both classes 'A' and 'B').

Wouldn't it be great if we could just find our components by using CSS selectors?

Yes of course, we do this all the time as frontend developers!

So I wrote a package to do that, it's called react-testutils-additions and it extends all the existing React Testutils helpers with extra ones, like finding your components based on CSS selectors.

The earlier example can now be written like this:
{% highlight javascript %}
var Component = TestUtilsAdditions.renderIntoDocument(<MyComponent />);

// now find all elements with class: 'myclassname'
TestUtilsAdditions.find(Component, ".myclassname");

// we can even do this:
TestUtilsAdditions.find(Component, "table#id tr.row");
{% endhighlight %}

Much simpler right?

I've created helpers to: 

- clean up your components,
- test your props
- find single components
- and more...

Want to get started with it or need more info, check the readme on [Github](https://github.com/rvdkooy/react-testutils-additions).

If you have any comments, write them below or you tweet me at ([@rvdkooy](https://twitter.com/rvdkooy))