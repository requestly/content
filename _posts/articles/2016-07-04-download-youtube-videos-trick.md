---
layout: post
title: "Download Youtube Videos"
excerpt: "Shortcut trick to download youtube videos using Keepvid"
categories: articles
sample: false
tags: [Requestly, Youtube, Videos, Download]
comments: true
share: true
---

Presenting a simple trick to download youtube videos. Suppose you want to download the following youtube video
`https://www.youtube.com/watch?v=dJR-n8szgBc` which is about Chrome Dev Tools debugging. You can simply use keepvid.com to download it.
Just paste the youtube Url in input box of keepvid and it will shown you a list of options based on video quality and you can download by clicking on the respective link.

## Usual Steps to download
1. Copy youtube video Url which you want to download
2. Open keepvid.com
3. Paste youtube video url in input field
4. Select the video qualilty to download

## Shortcut Trick

1. Create a Requestly Rule to redirect to keepvid based on query param

{% highlight text %}
  Source: Url Matches /(.+)youtube\.com(.+)&__d/ig
  Destination: http://keepvid.com/?url=$1youtube.com$2
{% endhighlight %}

<figure>
	<img src="{{ site.baseurl }}/images/youtube-videos-download-trick.png" alt="image">
  <figcaption>
    <center>
      <a href="http://chrome.google.com/webstore/detail/requestly/mdnleldcmiljblolnjhpnblkcekpdkpa"
        title="Using Requestly to redirect to keepvid when __d query param is present">
        Using Requestly to redirect to keepvid when __d query param is present
      </a>.
    </center>
  </figcaption>
</figure>

2. Open any youtube video which you want to download
3. Just append `&__d` to existing Url
4. Select the video qualilty to download

**Note:** Please note that `__d` is variable name and you can replace it with any other string you like. Just be aware to not use a string which can come in  a video url otherwise it will mess up with youtube link.

## Other Methods
1. You can also create a simple bookmarklet script to achieve the same thing
2. You can also write a 2 line Js code and use TamperMonkey Chrome Extension to achieve this.

Any suggestions/questions are welcome.  