---
layout: post
title: "Introducing De-Activate Feature"
excerpt: "What is meant by Deactivating Requestly and How to use it"
categories: articles
sample: false
tags: [Requestly, Features, Help, Usage, FAQ]
comments: true
share: true
---

You can now Activate/Deactivate requestly with your right click anywhere on any page.
If you deactivate Requestly, your rules won't be affected but they won't be executed anymore.
Similarly, When you activate Requestly, your active rules will get starting to execute.

## How to use

You can use *Right click* on any page to see the option to deactivate requestly.
When requestly is deactivated, same option converts to activate requestly.

<figure>
  <center>
	  <img src="{{ site.baseurl }}/images/deactivate-option-in-menu.png" alt="image">
    <figcaption>Snapshot of right click context menu on google.com</figcaption>
  </center>
</figure>

## How to know if Requestly is Deactivated

You can instantly know the state by looking the color of icon in toolbar menu.

<figure>
  <img src="{{ site.baseurl }}/images/256x256_greyscale.png" alt="image">
  <figcaption>Requestly icon has greyish color in deactivated state</figcaption>
</figure>

## Is there any other way to deactivate Requestly

You can disable any extension on your Chrome browser by following steps:

  1. Go to `chrome://extensions`
  2. UnCheck `Enable` after Requestly
  3. You can enable it later when you need.

This is a bit longer process. That's why this feature is introduced with which you can
deactivate Requestly with just single click.

## Implementation Details

For intercepting network requests, Requestly adds three types of listeners

1. [OnBeforeRequest](https://developer.chrome.com/extensions/webRequest#event-onBeforeRequest){:target='_blank'}: Used in Redirect and Replace Rules
2. [OnBeforeSendHeaders](https://developer.chrome.com/extensions/webRequest#type-OnSendHeadersOptions){:target='_blank'}: Used to Modify Request Headers
3. [OnHeadersReceived](https://developer.chrome.com/extensions/webRequest#event-onHeadersReceived){:target='_blank'}: Used to modify Response Headers

So, when Requestly is deactivated all these listeners are unregistered. These listeners are registered again when user activates requestly.
You can find out relevant piece of code in [background.js on github](https://github.com/blunderboy/requestly/blob/master/src/background/background.js){:target='_blank'}

Once User deactivates Requestly, this information is stored inside `chrome.sync.storage`
So if User has deactivated Requestly on one machine, it would automatically deactivate on other synced Chrome browsers.

## Links
- [Requestly Github Repo](http://github.com/blunderboy/requestly){:target='_blank'}
- [Requestly on Chrome Store](https://chrome.google.com/webstore/detail/requestly/mdnleldcmiljblolnjhpnblkcekpdkpa){:target='_blank'}
