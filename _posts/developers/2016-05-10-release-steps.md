---
layout: post
title: "Requestly release process"
modified:
categories: developers
sample: false
excerpt: "Steps for building Requestly to deploy on Chrome Store"
tags: []
date: 2016-05-10T18:03:30 +05:30
comments: true
share: true
---

## Steps

1. Checkout master branch and fetch it `git checkout master && git pull origin master`
2. Checkout `production` branch - `git checkout production && git pull origin production`
3. Merge master branch to it - `git merge master`
4. Run Unit tests - `grunt test`
5. Update version number in `Shared.js, manifest.json, package.json, Gruntfile.json`
6. Run build command - `grunt build`
7. Upload the build to [Chrome Store](chrome.google.com/webstore/developer/dashboard)
8. Commit the files - `git add . && git commit -m "Requestly va.b.c released"`
9. Push to production branch - `git push origin production`
10. Add tag - `git tag -a va.b.c`
11. Push the tags - `git push --tags origin`
12. Merge to master - `git checkout master && git merge production`

## Notes

1. Requestly uses `grunt-zipup` to create a zip file of source code. 
This tool only works on Unix or Mac So requestly's zip can only be created on Linux/Mac OS.
