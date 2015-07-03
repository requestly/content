---
layout: post
title: "Bypass IFrame Busting Header"
excerpt: "How to by-pass HTTP Response Header which prevents rendering of a website in Iframe"
categories: articles
sample: false
tags: [Requestly, Headers, ClickJacking, Security]
comments: true
share: true
---

Any technique which prevents a website from being rendered inside Iframe comes under Iframe Busting Techniques.
Due to Security issues like <a href="https://www.owasp.org/index.php/Clickjacking_Defense_Cheat_Sheet" target="_blank">
clickjacking</a>, various types of Iframe busting techniques are used.

## Simple Iframe Busting (JS Code)

{% highlight html %}
<script>
  if(top != window) {
    top.location = window.location
  }
</script>
{% endhighlight %}

This is one of the simple Iframe Busting techniques which just says

> If current `window` is not `top` window, change the url of top window.

This technique is considered week as there are easy options to bypass it.

### Bypass Iframe Code Busters

1. [Using HTML5 sandbox attribute](https://developer.mozilla.org/en/docs/Web/HTML/Element/iframe)
2. [Using onBeforeUnload handler](https://developer.mozilla.org/en-US/docs/Web/API/WindowEventHandlers/onbeforeunload)

`sandbox` attribute can be used on iframe to allow forms, popups and scripts but block parent navigation.
So the frame won't be able to change Url of parent window. It just throws an error in console.
Checkout this [demo on Jsbin](http://jsbin.com/vokacihihu/1/edit?html,output). You should see the following error in
developer tools.

{% highlight html %}
Unsafe JavaScript attempt to initiate navigation for frame with URL "http://null.jsbin.com/runner" from frame with URL
 "http://go.sap.com/index.html". The frame attempting navigation is `sandboxed`, and is therefore disallowed from
 navigating its ancestors.
{% endhighlight %}

## Reliable Iframe Busting (X-Frame-Options)

<a href="https://developer.mozilla.org/en-US/docs/Web/HTTP/X-Frame-Options" target="_blank">X-Frame-Options</a>
response header is very reliable approach for busting Iframes. Its not easy to bypass this HTTP response header.
One may need to setup a proxy server to fetch the content from website and return the response to browser.

### X-Frame-Options Values

There are three possible values for X-Frame-Options:

1. **DENY**: Browser will not render page inside frame irrespective of the domain of parent page.
2. **SAMEORIGIN**: Browser will render page inside iframe only if page domain is same as domain of parent page.
3. **ALLOW-FROM uri**: Browser will render page inside iframe only if domain of parent page is same as specified as `uri`.

Checkout this [demo on Jsbin](http://jsbin.com/harefaluyu/1/edit?html,output). You should see the following error in
developer tools.

{% highlight html %}
  Refused to display 'https://in.yahoo.com/?p=us' in a frame because it set 'X-Frame-Options' to 'DENY'.
{% endhighlight %}

There is no simple way to circumvent this response header. This is why this is considered as one of the most reliable
Iframe Busting techniques.

### Bypass X-Frame-Options header on your machine

There are tools available to bypass HTTP response header on your machine though.

1. [Charles Proxy](http://www.charlesproxy.com/){:target='_blank'}
2. [Fiddler](http://www.telerik.com/fiddler){:target='_blank'}
3. Browser extensions like
[Requestly](http://chrome.google.com/webstore/detail/requestly/mdnleldcmiljblolnjhpnblkcekpdkpa){:target='_blank'}
for Chrome,
[Modify Response Headers](https://addons.mozilla.org/en-us/firefox/addon/modify-response-headers/){:target='_blank'}
for Firefox


### Using Requestly (Chrome) to modify Headers

[Requestly]({{ site.chrome_store_url }}){:target='_blank'} is a popular
Chrome Extension which allows you to modify HTTP(s) requests. It can be used to remove HTTP response header like this:

<figure>
	<img src="{{ site.baseurl }}/images/requestly_header_modification.png" alt="image">
  <figcaption>
    <center>
      <a href="http://chrome.google.com/webstore/detail/requestly/mdnleldcmiljblolnjhpnblkcekpdkpa"
        title="Using Requestly to modify HTTP Response Headers">
        Using Requestly (Chrome) to remove X-Frame-Options Response Header
      </a>.
    </center>
  </figcaption>
</figure>

### Import Requestly Rule

Requestly also provides another great feature to export/import rules.You can
[download above rule here and import in your extension]({{ site.url }}{{ site.baseurl }}/assets/rules/remove-x-frame-options-header-requestly-rule.txt){:target='_blank'}

### Using Modify Response Header (Firefox)

[Modify Response Headers](https://addons.mozilla.org/en-us/firefox/addon/modify-response-headers/){:target='_blank'}
is a firefox add-on which allows you to modify HTTP(s) response headers. It can be used to remove HTTP response header like this:

<figure>
	<img src="{{ site.baseurl }}/images/modify_response_headers.png" alt="image">
  <figcaption>
    <center>
      <a href="https://addons.mozilla.org/en-us/firefox/addon/modify-response-headers/"
        title="Using Requestly to modify HTTP Response Headers">
        Using Modify Response Headers (Firefox) to remove X-Frame-Options Response Header
      </a>.
    </center>
  </figcaption>
</figure>

### Further Reading

* [https://www.owasp.org/index.php/Clickjacking](https://www.owasp.org/index.php/Clickjacking){:target='_blank'}
* [http://www.html5rocks.com/en/tutorials/security/sandboxed-iframes/](http://www.html5rocks.com/en/tutorials/security/sandboxed-iframes/){:target='_blank'}
* [https://developer.mozilla.org/en-US/docs/Web/HTTP/X-Frame-Options](https://developer.mozilla.org/en-US/docs/Web/HTTP/X-Frame-Options){:target='_blank'}
