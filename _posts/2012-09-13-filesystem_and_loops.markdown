---
layout: class
title: The Filesystem, Variables, and Loops
---

Type in these examples! Try them out! Vary them! Think about Borges' infinite library! Make work!

## The Filesystem

Use the Terminal to run all these commands.

What is the current directory?

{% highlight bash %}
pwd
{% endhighlight %}

Go to your home directory:

{% highlight bash %}
cd
{% endhighlight %}

Go to the Documents directory inside the home directory:

{% highlight bash %}
cd Documents
{% endhighlight %}

Create a directory called `art_code` within the current directory:

{% highlight bash %}
mkdir art_code
{% endhighlight %}

Go back to the home directory, then go to the `art_code` directory within `Documents`:

{% highlight bash %}
cd
cd Documents/art_code
{% endhighlight %}

Create an empty file called `foo`:

{% highlight bash %}
touch foo
{% endhighlight %}


Write `This is a test.` to a file called `bar`:

{% highlight bash %}
echo This is a test. > bar
{% endhighlight %}

Write `This is a short test.` with no final return to a file called `bar2`:

{% highlight bash %}
echo -n This is a short test. > bar
{% endhighlight %}

Remove the file called `foo`:

{% highlight bash %}
rm foo
{% endhighlight %}

Rename the file called `bar` to `foobar`:

{% highlight bash %}
mv bar foobar
{% endhighlight %}

See a listing of all files in the current directory:

{% highlight bash %}
ls
{% endhighlight %}

See a verbose listing of all files in the current directory (including file sizes in bytes):

{% highlight bash %}
ls -l
{% endhighlight %}

Go up a directory (to `Documents` if you were in `art_code`)

{% highlight bash %}
cd ..
{% endhighlight %}

Make another directory, called `good_art`, and move everything in `art_code` to `good_art`:


{% highlight bash %}
mkdir good_art
mv art_code/* good_art
{% endhighlight %}

## Variables

Assign values to variables then print the values:

{% highlight python %}
x = "This is a test"
print x
y = 42
print y
verbosename = "short value"
print verbosename
{% endhighlight %}

Math with variables:

{% highlight python %}
a = 17
b = 23
print b - a
print b * a
{% endhighlight %}

## Loops

Print `something` five times:

{% highlight python %}
for i in range(5):
    print "something"
{% endhighlight %}

Do a few things three times, then do something else:

{% highlight python %}
for i in range(3):
    print "do this"
    print "do that"
    print "and something else"
print "and now something else."
{% endhighlight %}

See the loop counter:

{% highlight python %}
for x in range(10):
    print "The count is..."
    print x
print "But did the count reach ten?"
{% endhighlight %}

Another way to write a loop:

{% highlight python %}
x = 0
while x < 10:
    print "foo"
    x = x + 1
{% endhighlight %}

Text art with loops:

{% highlight python %}
for x in range(8):
   print "oooOOOOooo" * x
{% endhighlight %}

## Creating files with Python

{% highlight python %}
f = open("foo.txt", "w")
f.write("This is a line ending in a newline.\n")
f.write("This line just ends, all of a sudden.")
f.close()
{% endhighlight %}
