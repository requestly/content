---
layout: post
title: "Execute JS hosted on Github"
excerpt: "Learn how you to use JS/CSS and other files hosted on github in your code"
categories: articles
sample: false
tags: [Requestly, Github, Headers, UseCases]
comments: true
share: true
---

Github is a well known online project hosting service.
Users checkin their scripts, styleshets and other file types as part of their project.
Sometimes, We need to refer the scripts present on github in any other project.
This article explains how you can achieve this use case with the help of Requestly using a very simple trick.

## Explanation - Why raw github urls don't work  ?

We analyzed the response headers set by github when serving `raw.githubusercontent.com/<file_path>` files.
We tried to open a very simple [JS file hosted on github](https://raw.githubusercontent.com/sachinjain024/practicebook/master/web-extensions-master/storage/background.js)
with the following contents:

    var BG = BG || {};
    BG.Methods = BG.Methods || {};

We found that Github sends `X-Content-Type-Options` response header which prevents modern browsers to estimate the mime type of content.
Hence, browsers render the raw github files as plain text.

## Solution 1

Using [Requestly](https://chrome.google.com/webstore/detail/requestly/mdnleldcmiljblolnjhpnblkcekpdkpa), Users can modify request and response headers.
We tried removing `X-Content-Type-Options` response header using Requestly which did the trick. Just as simple as that.

Here is a screenshot of the rule:

<figure>
	<img src="{{ site.baseurl }}/images/articles/remove-x-content-type-header.png" alt="image">
  <figcaption>
    <center>
      <a href="http://chrome.google.com/webstore/detail/requestly/mdnleldcmiljblolnjhpnblkcekpdkpa"
        title="Using Requestly to remove x-content-type-header">
        Using Requestly to remove x-content-type response header on raw github files
      </a>.
    </center>
  </figcaption>
</figure>

## Steps

1. Install Requestly from [http://www.requestly.in](http://www.requestly.in)
2. Go to [Rules Page](http://www.requeslty.in/rules)
3. Click on Add Icon to create a rule
4. Select Modify Headers
5. Give a Name and Descripton
6. Select `Remove` -> `Response` -> `X-Content-Type-Options`
7. In Source field, enter `Url` -> `Contains` -> `raw.githubusercontent.com`

## Solution 2

Using [Requestly](https://chrome.google.com/webstore/detail/requestly/mdnleldcmiljblolnjhpnblkcekpdkpa), Users can
setup rule to replace host or actually anything in URL. [RawGit](https://rawgit.com) is an online service which removes this
header and adds a mimetype for the files.

<figure>
	<img src="{{ site.baseurl }}/images/articles/replace-host-rawgit.png" alt="image">
  <figcaption>
    <center>
      <a href="http://chrome.google.com/webstore/detail/requestly/mdnleldcmiljblolnjhpnblkcekpdkpa"
        title="Using Requestly to replace raw.githubusercontent.com with rawgithub.com">
        Using Requestly to replace raw.githubusercontent.com with rawgithub.com
      </a>.
    </center>
  </figcaption>
</figure>

## Steps

1. Install Requestly from [http://www.requestly.in](http://www.requestly.in)
2. Go to [Rules Page](http://www.requeslty.in/rules)
3. Click on Add Icon to create a replace rule
4. Replace raw.githubusercontent.com with rawgit.com

## How to test

We created a simple JS Fiddle to test out if we can use raw github files as scripts in our code. Here is the [Fiddle](https://jsfiddle.net/1uc9t2cw/)
with the following code

{% highlight htmls %}
<center id="msg"></center>

<script src="https://raw.githubusercontent.com/sachinjain024/practicebook/master/web-extensions-master/storage/background.js"></script>
<script>
try {
  if (typeof BG.Methods !== 'undefoned') {
    document.getElementById('msg').innerHTML = 'Script evaluated successfully!';
  }
} catch (e) {
  document.getElementById('msg').innerHTML = 'Problem evaluating script';
}
</script>
{% endhighlight %}

If you see `Script evaluated successfully!`, It means you are able to use raw github file in your code
Otherwise `Problem evaluating script` indicates that there is some problem while executing script from raw github source.

## References

- [Stackoverflow: Link and execute external Javascript file hosted on Github](http://stackoverflow.com/q/17341122/816213)