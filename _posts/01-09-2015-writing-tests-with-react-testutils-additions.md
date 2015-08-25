---
title:  "Writing tests with react-testutils-additions"
date:   2015-09-01 21:00:00
categories: tech
description: test
image: /assets/img/writing-tests-with-react-testutils-additions/react-header.png
---

<img src="/assets/img/writing-tests-with-react-testutils-additions/react-header.png" alt="ReactJs" width="300px" >

I'm currently working on a pretty large project that involves replacing a classic webforms application to a new frontend tech stack.  The frontend is pretty complicated (configurable, lots of workflows and components that should communicate with each other), because of that I decided to use ReactJs (with a Flux implementation next to it). 

ReactJs is is an awesome library to build your UI with, here are some of the main benefits (according to me):

- You can componentize everything.
- It combines markup with Js (if you thing about it, it makes so much sense!!)
- It's fast.
- It is easy to learn.
- It's just javascript.
- It's only a UI library, so you can use whatever you want next to it.
- It comes with Testhelpers to test you components.

Althought the testhelpers are great, There is something with it that I don't really like! Let's show that with an example:

If you want to do some assertions on your component, you have to render it into the document, find the things you are interested in and do some assertion on it.

{% highlight javascript %}
var Component = ReactTestUtils.renderIntoDocument(<MyComponent />);

// now find all elements with class: 'myclassname'
ReactTestUtils.scryRenderedDOMComponentsWithClass(Component, "myclassname");
{% endhighlight %}

OK, what's with the scryRenderedDOMComponentsWithClass method??? First of all: it's a pretty long method name, that is hard to remember and secondly: for me, as a webdeveloper, it does not really make sense to find my Components like this.

And there are more of them: 'scryRenderedDOMComponentsWithTag', 'findRenderedDOMComponentWithTag', 'findRenderedDOMComponentWithClass'. 

Wouldn't it be great if you could find your ReactComponents based on CSS selectors? In the end we are all webdevelopers who have to deal with these tests, right?

So, I wrote a NPM package to make life easier