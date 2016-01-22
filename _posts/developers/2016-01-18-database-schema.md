---
layout: post
title: Data Storage and Schema
modified:
categories: developers
sample: false
excerpt:
tags: []
image:
  feature:
date: 2016-01-20T15:39:55+05:30
---

Requestly is using `StorageService` - A wrapper over chrome storage to store rules. 
This means user owns all his data and is stored in his computer. 
Chrome Storage service is great and provides sufficient storage capacity to storage ~100 rules.
But there is a requirement of backend service to store some global objects. e.g Consider this use case:

  > Sharing Public Url for a list of rules

## Data Storage (Firebase)

Following Options were explored considering Requestly Use cases. 

1. Node.js + MongoDB
2. Parse
3. Firebase

Pros & Cons for each option is [captured here on github][github-share-url-issue].
After above analysis, Firebase is chosen to serve as data storage.


## Data Storage Schema

Following is the data schema thought so far:

{% highlight js %}
  requestly
    Users
      $userId
        Collections
          $collection_1
            Groups
              $group_1
                Rules
                  $rule_1
                  $rule_2
                  ...
              $group_N
                Rules
                  $rule_1
        SharedLists
          $listName_1
          $listName_n
    Public
      SharedLists
        $listName_1
          Rules
            $rule_1
            $rule_2
        
{% endhighlight %}

Every field prefixed with `$` is User provided value.

## Design Description
Above database schema allows us to do the following:

1. Create multiple collections
2. Create groups inside each collection
3. Activate/Deactivate entire group or collection
4. Only an owner can delete his public shared link 
  i.e. Set write ACL on Public/SharedLists/$list1 for the user who created it.

[github-share-url-issue]: https://github.com/requestly/chrome-extension/issues/93
