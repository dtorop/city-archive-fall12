---
layout: class
title: Generating HTML and more about directories
---

## Creating Directories

### In the Finder

There are keyboard shortcuts. `Command-Shift-N` creates a new directory. `Command-Up` jumpts to the folder which holds the current folder. When a file/folder is selected, typing `Return` (aka `Enter`) lets you rename it.

### In the Terminal

When you are running the shell within the terminal:

{% highlight bash %}
cd            # go to home directory
cd foo        # go to directory "foo" within current directory
cd ~/foo      # go to drectory "foo" within home directory
cd ..         # go up a directory, to enclosing folder
ls            # list current directory
pwd           # show current directory (and its enclosing folders)
mkdir foo     # create a directory called "foo"
rmdir foo     # remove current directory "foo" (which must be empty)
{% endhighlight %}

In Finder-world, we talk about folders. In Terminal/Shell/Python world, it is more common to call them directories, but this refers to the same thing.

Some more advanced commands:

{% highlight bash %}
ls -R foo     # list directory `foo` and recursively all directories
              # within `foo`

# WARNING! potentially very dangerous:
rm -r foo     # remove `foo` and all files and directories within `foo`
{% endhighlight %}

The latter command could be a good way to remove a lot of valuable data. Be careful!

### In Python

When you are writing a Python script, either in TextWrangler (which you then run via Python from the terminal), or directly in Python interactive mode (when you type `python` and see the `>>>` prompt):

{% highlight python %}
import os              # set things up so that you can make directories
os.mkdir("foo")         # create directory "foo" within the current directory
os.mkdir("foo/bar")     # create directory "bar" within the existing directory "foo"
os.chdir("foo")         # go into "foo" within the curent directory
                        #   ("foo" becomes the current working directory)
os.chdir("..")          # jump out one directory
{% endhighlight %}

Note the class handout is in error about `os.mkdir("foo/bar")`: I'd written there that it created "foo" within "bar", but it is the reverse.

## Some basic HTML

{% highlight html %}
This appears without markup.

<b>Bold</b>
<i>Italics</i>

<p>This is a paragraph's worth of
text, which will have a line break
before and after, and may or may
not be word wrapped depending on how
wide the display area is</p>

This is some text followed by a line break.<br/>

This is <span style="color:red;">red colored</span> within some other writing.

<div style="font-family:arial; font-size:24px; font-color:blue;">Some large-ish (24 pixel high) blue text in the Arial type font, with newlines before and after.</div>

<img src="somewhere.jpg"/>
<a href="somewhere_else.html">Click here!</a>

<table>
  <tr>
    <td>Top left table cell</td>
    <td>Middle top cell</td>
    <td>Top right</td>
  </tr>
  <tr>
    <td>left side again</td>
    <td>middle</td>
    <td>right</td>
  </tr>
  <tr>
    <td>There could be a lot of cells</td>
    <td>and more</td>
    <td>for a while</td>
  </tr>
  <tr>
    <td>But tables are going</td>
    <td>out of fashion</td>
    <td>they say.</td>
  </tr>
</table>
{% endhighlight %}

## Basic HTML document structure

This is the boilerplate... One can add to this to make the document a bit more proper, but this is enough for now.

{% highlight html %}
<html>
    <head>
        <title>You'll see this at the top of the browser window</title>
    </head>
    <body>
        All the HTML to display in the browser goes here.
    </body>
</html>
{% endhighlight %}

This would go in a file called _foo_.html (use a name you'd like for _foo_), and you'd view it in the browser (say, Safari), by using `File > Open` and opening the file (which, perhaps would be in your document folder). You can type HTML in by hand, using TextWrangler, but why, as you can...

## Use Python to Generate HTML

### A small example

{% highlight python %}
f = open("hello.html", "w")
f.write("<html>\n")
f.write("<head>\n")
f.write("<title>Hello, world</title>\n")
f.write("</head>\n")
f.write("<body>\n")
f.write("Hello, world!\n")
f.write("</body>\n")
f.write("</html>\n")
f.close()
{% endhighlight %}

Type this script into TextWrangler, save it as boilerplate.py (or give it a better name, substitute for boilerplate). Save it in your `Documents` folder. Open Terminal, and `cd Documents` to get to the script. Type `python boilerplate.py` to run the code. You should now have a file `hello.html`. Open this in Safari. You should see `Hello, world!` in your browser window.

### Repetition

{% highlight python %}
f = open("hello.html", "w")
f.write("<html>\n")
f.write("<head>\n")
f.write("<title>Hello, world</title>\n")
f.write("</head>\n")
f.write("<body>\n")
for x in range(20):
    f.write("Hello, world!<br/>\n")
f.write("</body>\n")
f.write("</html>\n")
f.close()
{% endhighlight %}

### Interpolating numbers and text into text

This is an aside, to elucidate the next examples.

{% highlight python %}
print "There are 8 mice."
print "There are %d mice."%8              # does the same as first line
print "There are %d mice."%(5+3)          # ditto

x = 8
print "There are %d mice."%x              # ditto, once you set x to 8

for x in range(8):                        # a mouse infestation
    print "There are %d mice."%x

print "There %s 8 mice."%"are"            # does the same as first line

x = "are"
print "There %s 8 mice."%x                # does the same as first line
{% endhighlight %}

The same goes for interpolating text and numbers into `f.write()`, as seen below.

### Changing font sizes

Now back to HTML...

{% highlight python %}
f = open("hello.html", "w")
f.write("<html>\n")
f.write("<head>\n")
f.write("<title>Hello, world</title>\n")
f.write("</head>\n")
f.write("<body>\n")
for x in range(10,30):
    f.write("<div style='font-size:%dpx;'>Hello, world!</div>\n"%x)
f.write("</body>\n")
f.write("</html>\n")
f.close()
{% endhighlight %}

This will go from 10 to 29 points. Another way to do this would be to make the loop:

{% highlight python %}
for x in range(20):
    f.write("<div style='font-size:%dpx;'>Hello, world!</div>"%(x+10))
{% endhighlight %}

### Random colors

{% highlight python %}
import random
pretty_colors = ["red","green","purple","blue","violet"]

f = open("hello.html", "w")
f.write("<html>\n")
f.write("<head>\n")
f.write("<title>Hello, world</title>\n")
f.write("</head>\n")
f.write("<body>\n")
for x in range(10,30):
    f.write("<div style='color:%s;'>Hello, world!</div>\n"%random.choice(pretty_colors))
f.write("</body>\n")
f.write("</html>\n")
f.close()
{% endhighlight %}

### An elaborate example

Final code From class... Overwrites text, random colors, random font size...

{% highlight python %}
import random

f=open("hello.html", "w")
f.write("<html>\n")
f.write("<head>\n")
f.write("  <title>This page will always say hello.</title>\n")
f.write("</head>\n")
f.write("<body>\n")
pet_colors = ["red","orange","yellow","blue"]
for x in range(20,5000,5):
    f.write("<span style='color:%s; "%random.choice(pet_colors));
    f.write("font-family:arial; font-size:%dpx'>"%random.randrange(100));
    f.write("Hello.")
    f.write("<div style='position:absolute; ")
    f.write("color:%s;'>This</div>"%random.choice(pet_colors))
    f.write("</span>\n")
f.write("</body>\n")
f.write("</html>\n")
f.close()
{% endhighlight %}

Note that for a while the outer `span` was a `div`.

Good luck...
