---
layout: class
title: Amazon S3 plus more HTML/CSS and Python
---

## CSS/HTML

That is, Cascading Style Sheets within HTML.

### CSS Placement

{% highlight html %}
<html>
<head>
  <title>This is a test</title>
</head>
<body>
  <h1>This is the first header</h1>
  <div>One.</div>
  <div style="color:purple;">Two.</div>
  <div style="position: relative; left:10px; top:20px; font-weight: bold; color:red;">
    Three.
  </div>
  <div style="color:green;">Four.</div>
</body>
</html>
{% endhighlight %}

Compare `position: relative;` with `position: absolute`. Compare using `left`, `right`, `top`, and `bottom` attributes.

### CSS Classes

CSS can go in the `head` of the HTML document. Classes connect specific tags to the appropriate CSS.

{% highlight html %}
<html>
<head>
<style type="text/css">
h1 {
  color:blue;
}

h2 {
  position:absolute;
  left:200px;
  top:150px;
  color:red;
}

div.diap {
  color:green;
}
</style>
</head>

<body>
<h1>This is the first header</h1>
<h2>This is a heading with an absolute position</h2>
<div>One</div>
<div>Two</div>
<div class="diap">Three</div>
<div>Four</div>
</body>

</html>
{% endhighlight %}

## Python Flow of Control

### Functions

{% highlight python %}
def times_four(value):
    print value * 4

def times_something(value, n):
    print value * n

times_four(3000)
times_four(500000)

times_something(50, 4)

def longer_function(something):
    print "This is a multi-line function"
    print "which will eventually print something"
    print something

longer_function("or other")
{% endhighlight %}

### Comments

{% highlight python %}
# Everything after a # is ignored on each line
# which is good for writing notes to yourself
# and others within the program, as well as to
# temporarily hide code from the computer so it
# doesn't evaluate it.
{% endhighlight %}

### Conditionals

{% highlight python %}
# This is a test of flow of control and
# comparisons of values with if statements

# varieties of comparisons
if 5 == 5:
    print "That's true."
if 5 != 15:
    print "That's true."
if 5 < 15:
    print "That's true."
if 15 > 5:
    print "That's true."
if 15 < 5:
    print "That's not true, though."

# comparing to a variable
x = 5
if x == 5:
    print "That's true."

# comparing in a loop
print "before for loop"
for x in range(5):
    print "in the for loop"
    print "x is now %d"%x
    if x == 3:
        print "Almost there!"
print "done with for loop"

# comparing in a function
def is_big(num):
    if num > 1000:
        print "Gosh, %d is more than I can count to."%num
    else:
        print "Hey, %d isn't a number worth computing."%num

is_big(10)
is_big(5000)
{% endhighlight %}

## Amazon Web Services Simple Storage Service (aka AWS S3)

### Getting an AWS account

Set up for an AWS account via the `Sign Up Now` button on the [AWS homepage](https://aws.amazon.com/). Use a [good password](https://encrypted.google.com/search?hl=en&q=how+to+create+a+good+password)!

### Setting up the Bucket (S3)

Go to the [AWS console](https://console.aws.amazon.com/) and select S3.

Choose `Create Bucket` from the top of the left pane, and create a bucket called something like `YOURNAME.diap.ccny.edu` in region `US Standard`. This bucket will act as your website. For YOURNAME, use a one word version of your name (I use `dtorop`).

Select your bucket in the left pane (`Buckets`) and click the `Properties` button to the right under `Objects and Folders`. The properties pane will appear at the bottom.

Choose the `Website` tab in the `Properties` pane and check `Enabled`. Type `index.html` as your `Index Document`. Click `Save`. If you click on the `Endpoint` link, you should now be able to see your website. At the top of the page, you'll see a message `403 Forbidden`. Don't worry.

Choose the `Permissions` tab in the `Properties` pane and click `Add bucket policy`. Paste the following into the `Bucket Policy Editor` which appears up:

{% highlight json %}
{
	"Version": "2008-10-17",
	"Statement": [
		{
			"Sid": "PublicReadForGetBucketObjects",
			"Effect": "Allow",
			"Principal": {
				"AWS": "*"
			},
			"Action": "s3:GetObject",
			"Resource": "arn:aws:s3:::YOURNAME.diap.ccny.edu/*"
		}
	]
}
{% endhighlight %}

Substitute for `YOURNAME` the same one word version of your name you used to name the bucket.

Click `Save` (you may have to type then delete something to activate that button). Now your website will display `404 Not Found` when you refresh its page. This is better than forbidden.

### Uploading a page to S3

Once you've set up the bucket as a website, you can use it to see your HTML on the web. Click `Upload` under the `Objects and Folders` pane. Click `Add Files` and use the dialog to select the HTML file which you want to put up on the web. Click `Start Upload`. The `Transfers` pane will appear. Wait until the upload is done.

You can now view your file on the website. Use your browser to go to the address made by following your site URL (`http://YOURNAME.diap.ccny.edu.s3-website-us-east-1.amazonaws.com/`) with the name of the file you uploaded. For example, I put a file up at [http://dtorop.diap.ccny.edu.s3-website-us-east-1.amazonaws.com/kaprow.html](http://dtorop.diap.ccny.edu.s3-website-us-east-1.amazonaws.com/kaprow.html).

## A start of a Kaprow example

{% highlight python %}
import random

def a_sound():
    pet_sounds = ["drip","shhhh","meow","clank"]
    return random.choice(pet_sounds)

def sound_span():
    f.write("<span style='color:%s; "%random.choice(pet_colors));
    f.write("font-family:arial; font-size:%dpx'>"%random.randrange(100));
    f.write(a_sound())
    f.write("</span>\n")

f=open("kaprow.html", "w")
f.write("<html>\n")
f.write("<head>\n")
f.write("  <title>Say hi to Cage</title>\n")
f.write("<body>\n")
pet_colors = ["red","orange","yellow","gray"]
for x in range(20,5000,5):
    for y in range(random.randrange(3,10)):
        sound_span()
    f.write("<div style='position:absolute; color:%s;'>"
            %random.choice(pet_colors))
    f.write("%s</div>"%a_sound())
f.write("</body>\n")
f.write("</html>\n")
f.close()
{% endhighlight %}

Make something textured.
