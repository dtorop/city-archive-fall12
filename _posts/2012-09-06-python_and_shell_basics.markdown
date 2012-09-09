---
layout: class
title: Python and Shell Basics
---

## Overview

Instructions are for OS X. Check out [Exercise 0](http://learnpythonthehardway.org/book/ex0.html) of Learn Python the Hard Way for more advice and how to download [TextWrangler](http://www.barebones.com/products/textwrangler/).

## Open terminal

* Click on the magnifying glass in top right.
* Type `Terminal`
* Wait for Application `Terminal` to appear in the menu
* Click `Terminal`
* You are now in Terminal, with the shell (bash) running

## Basic shell commands

* `echo This is a test` - prints This is a test
* `ls` - lists current directory
* `ls Documents` - lists contents of documents directory
* `cd Documents` - go to the Documents directory
* `python` - run Python as a REPL (interactive
* `python test1.py` - run test1.py as a Python script
* `python test1.py > output.txt` - run test1.py as a Python script, send its output to the file output.txt

## Command line editing

For both the shell and Python, up arrow recalls history of recent commands, down arrow goes forward through history. You can then edit a command and type `return` to run it.

## Basic Python commands

### Printing strings

{% highlight python %}
print "Hello, world!"
print 'This is a test'
print "This is a 'test'."
print 'This is a "test".'
print "This is a \"test\"."
print 'This is a \'test\'.'
{% endhighlight %}

### Math

{% highlight python %}
print 5 * 12
print 1 + 3
print 24 / 3
print 5 - 2
{% endhighlight %}

### Repeating strings

{% highlight python %}
print "Test" * 5
print "Hello " * 5
{% endhighlight %}

### Loops to repeat

{% highlight python %}
for x in range(10):
    print "Test"
{% endhighlight %}

Without line breaks:

{% highlight python %}
for x in range(10):
    print "Hello",
{% endhighlight %}

### Random numbers

{% highlight python %}
import random
print random.randrange(10)
{% endhighlight %}

### Looping a random number of times

{% highlight python %}
import random
for x in range(random.randrange(10)):
    print "Testing."
{% endhighlight %}
