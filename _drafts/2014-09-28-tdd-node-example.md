---
layout: post
title: "NodeJS TDD Example"
description: "This is a small example of how to unit test a NodeJS module using Jasmine"
category: 
tags: [javascript, node, TDD, jasmine]
---
{% include JB/setup %}

#Unit testing a NodeJS module

The functionality that we are going to implement using TDD techniques is going to be a URL builder. It is going to take as its input an array of files (HTML and other web resources) and output full URL paths to these file. 

{% highlight javascript %}

Configurations:
var protocol = "http";
var domain = "web.store.com";

Inputs:
var paths = ["index.html", "about.html", "content.html", "resources/header.js", "resources/footer.js"];

Output:
var urls = ["http://web.store.com/index.html", "http://web.store.com/about.html", "http://web.store.com/content.html", "http://web.store.com/resources/header.js", "http://web.store.com/resources/footer.js"]
{% endhighlight %}

Some of the code used in this post has been developed and expained in a previous post. If you need you need information of what the code does then have a look back at this blog [post](/2014/09/20/javascript-currying-example)

#Installing Jasmine
todo - add details here of how to install and run a test


#Node Module Test

Here is the first draft of the test. It import the url builder module and calls buildSimpleUrl function giving as parameter the protocol, domain name and the file name.
{% highlight javascript %}
// File: spec/url-builder-spec.js

// Import the url builder Module
var urlBuilder = require("../url-builder");

describe("building single url", function () {
  it("should build url from the protocol, domain, and file name", function () {
    var url = builder.buildSimpleUrl("http", "store.com", "index.html");
    expect(url).toEqual("http://store.com/index.html");
  }); 
});
{% endhighlight %}

As the url builder module has not been created yet jasmine gives the following error:

{% highlight text %}
Failures:

  1) building single url should build url from the protocol, domain, and file name
   Message:
     ReferenceError: builder is not defined
   Stacktrace:
     ReferenceError: builder is not defined
    at null.<anonymous> (/home/jholleran/development/javascript/jasmine/url-builder/spec/url-builder-spec.js:13:15)

Finished in 0.023 seconds
1 test, 1 assertion, 1 failure, 0 skipped

{% endhighlight %}

Here is the simplist module code to get the test to pass.

{% highlight javascript %}
// File: url-builder.js

exports.buildSimpleUrl = function(protocol, domain, path) {
	return protocol + "://" + domain + "/" + path;
}
{% endhighlight %}

Now the test passes.
{% highlight text %}
Finished in 0.011 seconds
1 test, 1 assertion, 0 failures, 0 skipped
{% endhighlight %}
