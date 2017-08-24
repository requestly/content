---
layout: post
title: "List of Permissions in Requestly"
excerpt: "Understand why and what permissions are required in Requestly"
categories: articles
sample: false
tags: [Requestly, Permissions, Security, Chrome, Extension]
comments: true
share: true
---

# List of Permissions used in Requestly

Browser extensions play an important role in user’s daily browsing activity and
other interactions with browser. Believe it or not, everyone has a list of
favourite browser extensions and rarely you will find a “faceless” men with no
extensions installed in his browser. Essentially, browser extensions make your
browsers more powerful and feature rich.

You may have heard of this popularly known quote:

> **With Power Comes Responsibility**

The same holds true here. As helpful and powerful browser extensions are, they
can be a bit dangerous as well So it is very important to review and question
the list of permissions asked by them.

In this article, we are explaining all the permissions required by
[Requestly](https://chrome.google.com/webstore/detail/requestly-redirect-url-mo/mdnleldcmiljblolnjhpnblkcekpdkpa)
and how we use it.

#### Permissions in Requestly

![](https://cdn-images-1.medium.com/max/1600/1*lIh0W5j10gVqEHkeWFgaVA.png)

#### ContextMenus

This permission is required to add an item in chrome contextMenu. Requestly
provides a feature to toggle Requestly with Right Click and hit Deactivate. You
can read [more about it
here.](http://www.requestly.in/content/documentation/introducing-activate-deactivate-feature/)

#### Storage

[Storage permission](https://developer.chrome.com/extensions/storage) is
required to store something in chrome storage.Most Users love Requestly because
their rules are stored in Chrome itself and not on Requestly servers. This
enhances their trust factor in it.

#### WebRequest, WebRequestBlocking

[WebRequest permission](https://developer.chrome.com/extensions/webRequest) is
required to intercept network requests and modify them. If you have ever used
Requestly, you know sense that this permission is the heart of Requestly.
Because Requestly modified network requests based on User’s rules.

#### Tabs

[Tabs permission](https://developer.chrome.com/extensions/tabs) is required to
obtain page url for a given tab. This is used to redirect page urls as per
user’s rules and especially used in [UserAgent
Rule.](http://www.requestly.in/content/documentation/introducing-useragent-modification/)

### Contact
Feel free to reach out to
[requestly.extension@gmail.com](mailto:requestly.extension@gmail.com) for any
concerns you have while using Requestly. We love every feedback on Requestly and
respond to everyone. Let us know in comments if you have any more questions.
