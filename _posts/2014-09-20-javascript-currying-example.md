---
layout: post
title: "JavaScript Currying Example"
description: ""
category: 
tags: [javascript]
---
{% include JB/setup %}

#What is Currying?
Currying is the process of transforming a function that takes multiple arguments into a function that takes just a single argument.

Lets take a look at the following example where we want to trible some values and print the results. 

To do this we have created a function that multiplies the two input arguments. Then we are calling the function and print the results to the console. The first argument to the function is alway three as we want to trible the second argument.

{% highlight javascript %}
function multiply(a, b) {
	return a * b;
}

console.log(multiply(3, 2));	//6
console.log(multiply(3, 6));	//18
{% endhighlight %}

We can simplify this code by using currying where we reduce the arguments so that we don't need to pass in the three. There are a number of ways we can do this.

{% highlight javascript %}

var trible = function(b) {
	return multiply(3, b);
}

console.log(trible(4));		//12
console.log(trible(8));		//24

{% endhighlight %}

Here we are creating a wrapper function that wraps the multiply function and always passes three as the first parameter.

A more shorthand way of doing the same thing is the following using the bind function:

{% highlight javascript %}

var trible = multiply.bind(null, 3);

console.log(trible(4));		//12
console.log(trible(8));		//24

{% endhighlight %}

This is the exact same as the first trible function but its shorter to write. The first argument null is the "this" value to the bound function when it is called. As the multiple function does not use the "this" it is ok to pass in null. The value three will passed as the "a" argument in multiple.

Using these techniques makes it easy to reuse these functions in other ways. For example lets say we wanted a function to quadruple values. Here is how we could do it:


{% highlight javascript %}

var quadruple = multiply.bind(null, 4);

console.log(quadruple(2));		//8
console.log(quadruple(3));		//12

{% endhighlight %}


##Building Urls Example

Here is another example where we are building urls. In this example we use currying to reduce the first two arguments of simpleUrl into a function. This function is called for every value in the urls array using the map function.

{% highlight javascript %}

function simpleUrl(protocol, domain, path) {
	return protocol + "://" + domain + "/" + path;
}


var domain = "web.store.com";
var paths = ["index.html", "about.html", "content.html", "resources/header.js", "resources/footer.js"];

var urls = paths.map(simpleUrl.bind(null, "http", domain));

console.log(urls); 

/*
urls = ["http://web.store.com/index.html", "http://web.store.com/about.html", "http://web.store.com/content.html", "http://web.store.com/resources/header.js", "http://web.store.com/resources/footer.js"]
*/
{% endhighlight %}
