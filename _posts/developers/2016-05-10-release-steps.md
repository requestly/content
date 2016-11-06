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

- Checkout master branch and fetch it `git checkout master && git pull origin master`
- Checkout `production` branch - `git checkout production && git pull origin production`
- Merge master branch to it - `git merge master`
- Run Unit tests - `grunt test`
- Update version number in `Shared.js, manifest_chrome.json, mainfest_firefox.json, package.json, Gruntfile.json`
- Run build command - `grunt release-chrome`
- Upload the build to [Chrome Store](https://chrome.google.com/webstore/developer/dashboard)
- Delete the earliest build. We want to keep only 3 previous builds.
- grunt select-firefox
- Create an alias if not already done like this. Write it inside ~/.bashrc
- alias sign_requestly_build="web-ext sign --api-key=??? --api-secret=???"
- sign_requestly_build
- cp -r web-ext-artifacts/* builds/web-ext-artifacts/
- rm -rf web-ext-artifacts
- Copy the new artifact to dropbox (We currently host firefox builds on dropbox. We will change this to requestly server later)
- Update updates.json inside dropbox directory
- Update firefox download link on requestly home page
- Commit the files - `git add . && git commit -m "Requestly va.b.c released"`
- Push to production branch - `git push origin production`
- Add tag - `git tag -a va.b.c`
- Push the tags - `git push --tags origin`
- Merge to master - `git checkout master && git merge production`

## Notes

1. Requestly uses `grunt-zipup` to create a zip file of source code. 
This tool only works on Unix or Mac So requestly's zip can only be created on Linux/Mac OS.
