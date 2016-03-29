---
layout: post
title: "Porting Requestly to Firefox as Web Extension"
modified:
categories: developers
sample: false
excerpt: "Analysis of different chrome.extension.* APIs used in Requestly and incompatibilities in Web Extension"
tags: []
date: 2016-03-25T12:00:00 +05:30
comments: true
share: true
---

## Introduction 
Requestly is a beautiful chrome extension for modifying network requests. 
It has hit the ground hard and announced its presence in market sound and fair.
Its usage has grown tremendously over last few months. 
As of March 2016, [Chrome store shows *7.5K users*](http://bit.ly/requestly-chrome-store).
Due to simple interface with infinite possibilities it is becoming popular among web devs for testing and debugging purposes.
I have received multiple requests for developing Requestly on Firefox. 
It was certainly not easy to build Requestly with Firefox Add-On APIs 
but the support of [Web Extension APIs](https://developer.mozilla.org/en-US/Add-ons/WebExtensions/Anatomy_of_a_WebExtension) in Firefox
has made the job easy. This article is the first step in direction for porting Requestly to Firefox.

## Analysis of Chrome APIs Incompatibilities

1. **Content Scripts**: Supported
2. **Background Scripts**: Supported
3. **Storage API**: Partially Supported with following road blockers:
    - `chrome.storage.sync` is not supported. We can use 'chrome.storage.local` for the time.
    - `chrome.storage` is not accessible in Content Scripts. [Bugzilla Link](https://bugzilla.mozilla.org/show_bug.cgi?id=1197346)
4. **NameSpacing**: Currently all APIs are accessible through `chrome.*` but later on this will be moved to `browser.*` 
    - Does not require immediate change but we may have to modularize the code using browserify 
    and instantiate different packages for different browsers
5. **Packaging**: Firefox needs `xpi` extension instead of `zip`.
    - This is in roadmap that webextensions should be accepted as zip 
    but initially we may have to rename zip to xpi before uploading to FF store.
6. **Tabs**: Partially Supported for our needs.
    - In Firefox, you need the `tabs` permission if you want to include url in the queryInfo parameter to `tabs.query()`
7. **webRequest**: Partially supported but meets our needs.
    - In Firefox requests can be redirected only if their original URL uses the http or https scheme
8. **Manifest**: [Firefox manifest.json] has mandatory `applications` key and we can't use this in chrome extensions.
    - We need to maintain two different manifest files for chrome and browser and build system should pick them as per browser.
9. **Context Menus**: Fully Supported 
    
For More details, Refer [Mozilla documentation on chrome APIs Incompatibilities](https://developer.mozilla.org/en-US/Add-ons/WebExtensions/Chrome_incompatibilities)    

##  Links

1. [Mozilla Web Extension Wiki](https://wiki.mozilla.org/WebExtensions)
2. [Porting Chrome Extension to FF Web Extension](https://hacks.mozilla.org/2015/10/porting-chrome-extensions-to-firefox-with-webextensions/)
3. [Requestly Github Issue](https://github.com/requestly/chrome-extension/issues/91)

[Firefox manifest.json]: https://developer.mozilla.org/en-US/Add-ons/WebExtensions/manifest.json/applications