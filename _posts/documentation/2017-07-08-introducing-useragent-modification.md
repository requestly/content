---
layout: post
title: "UserAgent Modification"
excerpt: "Spoof userAgent in your browser with Requestly"
categories: documentation
sample: false
tags: [Requestly, Feature, Documentation, UserAgent, Testing]
comments: true
share: true
---

The User-Agent request header is most commonly used by servers to identify its client’s application type, 
operating system, software vendor or software version. Based on the User-Agent string, 
server selects suitable content to be sent in response. 
For instance, when a website is opened in a mobile device, 
it usually looks quite compact and different compared to the way it opens in desktop.

Now imagine if your browser allows you to override the User-Agent string, you could see any version of a website you like!
All you need to do is to install [Requestly](http://www.requestly.in/) extension in your browser and enjoy the fun.

<figure>
  <a href="{{ site.baseurl }}/images/documentation/introducing-useragent/useragent-card-highlighted.jpeg">
  	<img src="{{ site.baseurl }}/images/documentation/introducing-useragent/useragent-card-highlighted.jpeg" alt="image">
  </a>
  <figcaption><center>UserAgent Rule Card</center></figcaption>
</figure>

You can choose among popular devices like Android Phone, iPhone, tablets or web browsers like Internet Explorer, Safari, etc. 
Or you may also specify a custom User-Agent string to experience a specific version of website.

Requestly has a simple rule builder where you specify the source request URL or domain and select type of User Agent. 
You may also choose whether to override User-Agent only for the website URL or for all HTTP requests originating from that page.

<figure>
  <a href="{{ site.baseurl }}/images/documentation/introducing-useragent/useragent-ruleeditor.jpeg">
  	<img src="{{ site.baseurl }}/images/documentation/introducing-useragent/useragent-ruleeditor.jpeg" alt="image">
  </a>
  <figcaption><center>UserAgent Rule Editor</center></figcaption>
</figure>

<figure>
  <a href="{{ site.baseurl }}/images/documentation/introducing-useragent/ua-selectdevice.jpeg">
  	<img src="{{ site.baseurl }}/images/documentation/introducing-useragent/ua-selectdevice.jpeg" alt="image">
  </a>
  <figcaption><center>UserAgent Select Device</center></figcaption>
</figure>

<figure>
  <a href="{{ site.baseurl }}/images/documentation/introducing-useragent/ua-selectbrowser.jpeg">
  	<img src="{{ site.baseurl }}/images/documentation/introducing-useragent/ua-selectbrowser.jpeg" alt="image">
  </a>
  <figcaption><center>UserAgent Select Browser</center></figcaption>
</figure>

Requestly also allows you to set your custom UserAgent.

<figure>
  <a href="{{ site.baseurl }}/images/documentation/introducing-useragent/ua-custom.jpeg">
  	<img src="{{ site.baseurl }}/images/documentation/introducing-useragent/ua-custom.jpeg" alt="image">
  </a>
  <figcaption><center>Setting Custom UserAgent String</center></figcaption>
</figure>

The best part of this extension is that you may run different rules for different websites simultaneously.

Requestly also has a great application in web-development where you usually want to test your website on different platforms.

The extension also allows to create rules to redirect requests, modify request/response headers and block requests for personal usage or web development. 
It also allows to host files to library and share rules with friends.

Please give it a try and share your valuable feedback with us. We will try to improve and help you in best possible way.
For further questions, feel free to reach out at `requestly.extension@gmail.com` or tweet to `@requestly_ext`. Hope you like this feature.

## Links
- [Requestly Github Repo](https://github.com/requestly/requestly-issues){:target='_blank'}
- [Requestly on Chrome Store](https://chrome.google.com/webstore/detail/requestly/mdnleldcmiljblolnjhpnblkcekpdkpa){:target='_blank'}
- [Introducing UserAgent Feature - Article on Medium](https://medium.com/@requestly_ext/switching-user-agent-in-browser-f57fcf42a4b5)
