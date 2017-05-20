---
layout: post
title: "Rules Json Format"
modified:
categories: developers
developerPost: true
sample: false
excerpt: "Format of different rule types stored in database"
tags: []
date: 2016-05-05T08:05:55 +05:30
comments: true
share: true
---

* Table of Contents
{:toc}

## Keys Set

1. creationDate: Used to display `Created On` Column on Index Page. Also used for creating Id of rule.
2. id: Identifier - $RuleType_$creationDate

## Redirect Rule Format

### Redirect Rule (v1)

{% highlight js %}
 
  redirect_rule_v1 = { 
    creationDate: 1404740537779,
    description: 'Testing Redirect Rule',
    destination: 'http://www.facebook.com',
    id: 'Redirect_1404740537779',
    name: 'Redirecting Google to FB',
    ruleType: 'Redirect',
    source: {
      key: 'Url',
      operator: 'Contains',
      values: ['google.com'],
    },
    status: 'Inactive'
  }
  
{% endhighlight %}

### Redirect Rule (v2) - Latest

To support Multiple Redirect Entries within a single Redirect Rule)
Move `source`, `destination` field inside `pairs`.

{% highlight js %}
 
  redirect_rule_v2 = { 
   creationDate: 1404740537779,
   description: 'Testing Redirect Rule',
   id: 'Redirect_1404740537779',
   name: 'Redirecting Google to FB',
   ruleType: 'Redirect',
   status: 'Inactive',
   pairs: [
     {
       source: {
         key: 'Url',
         operator: 'Contains',
         value: 'google.com'
       },
       destination: 'http://www.facebook.com' 
     }
   ]
 }
  
{% endhighlight %}

## Cancel Rule Format

There is no difference between Redirect Rule Json and Cancel Rule Json except there is no `destination` field in Cancel Rule

## Replace Rule Format

### Replace Rule (v1)

{% highlight js %}
 
  replace_rule_v1_ = { 
   creationDate: 1426230518638,
   description: 'Shortcut for JIRA issues. Just write TGT-6638 in browser and see the magic',
   id: 'Replace_1426230518638',
   name: 'My Domain Name shortcuts',
   ruleType: 'Replace',
   status: 'Inactive',
   pairs: [
     {
       from: 'sachin:8880',
       status: 'Inactive',
       to: 'sachin.corp.example.com:8080' 
     },
     {
       from: 'http://appserver/',
       status: 'Inactive',
       to: 'app-mango.corp.example.com:8080' 
      }
   ]
 }
  
{% endhighlight %}

### Replace Rule (v2)

Add `source` object inside each rule pairs and `version` field in rule.

{% highlight js %}
 
  replace_rule_v1_ = { 
   creationDate: 1426230518638,
   description: 'Shortcut for JIRA issues. Just write TGT-6638 in browser and see the magic',
   id: 'Replace_1426230518638',
   name: 'My Domain Name shortcuts',
   ruleType: 'Replace',
   status: 'Inactive',
   version: 2,
   pairs: [
     {
        from: 'sachin:8880',
        status: 'Inactive',
        to: 'sachin.corp.example.com:8080',
        source: {
          key: 'Url',
          operator: 'Contains',
          value: 'http://sachin:8080/tweet-service'
        }
     },
     {
        from: 'http://appserver/',
        status: 'Inactive',
        to: 'app-mango.corp.example.com:8080',
        source: {
          key: 'Url',
          operator: 'Contains',
          value: ''
        }
      }
   ]
 }
  
{% endhighlight %}

## User-Agent Rule Format

{% highlight js %}
 
  user_agent_rule = {
    "creationDate": 1494081686203,
    "description": "Load android mobile version of facebook website",
    "id": "UserAgent_1494081686203",
    "name": "facebook in android mobile",
    "pairs": [
      {
        "env": "android.phone",
        "envType": "device", // envType=device|browser|custom
        "source": {
          "key": "Url",
          "operator": "Contains",
          "requestType": "mainFrame", // requestType=mainFrame|pageRequest
          "value": "facebook.com"
        },
        "userAgent": "Mozilla/5.0 (Linux; Android 5.1.1; Nexus 6 Build/LYZ28E) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/57.0.2987.133 Mobile Safari/537.36"
      }
    ],
    "ruleType": "UserAgent",
    "status": "Active"
  }
  
{% endhighlight %}

### Notes:
1. status field inside pairs is not used now.
2. Empty value in source means it is ignored and rule can apply to any Url.
3. With source field, you can constrain your replace functionality to certain Urls.
4. Github Issue: https://github.com/requestly/chrome-extension/issues/121
