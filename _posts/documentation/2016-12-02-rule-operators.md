---
layout: post
title: "Rule Operators"
excerpt: "Documentation of various rule operators"
categories: documentation
sample: false
tags: [Requestly, Features, Help, Usage, FAQ, Rule, Operators, Matches, Wildcard]
comments: true
share: true
---

* Table of Contents
{:toc}

## Equals Operator

Equals operator does strict matching of Url interecepted by Chrome with the Url given in rule.

```
Please note that when you open www.example.com, url intercepted is www.example.com/. Note a trailing '/' slash at the end of Url.
So a rule with Equals operator and Url as www.example.com does not match www.example.com/.
So consider adding Slash ('/') at the end of url in your rule. You can alternatively create two pairs in the same rule as well.
```

Example1:

    Url in Rule: http://www.google.com
    Intercepted Url: http://www.google.com/
    Result: false (Observe trailing slash)

## Contains Operator

Contains operator does a substring search of string provided in rule inside the Url intercepted by Chrome.

Example1:

    String in Rule: yahoo
    Intercepted Url: https://www.yahoo.com/
    Result: true

Example2:

    String in Rule: com?a=1
    Intercepted Url: https://www.got.com?a=2
    Result: false

## Regex Match Operator

Regex Match Operator matches a given Regex with the Url intercepted by chrome.
You can also use the values of group expressions in your destination Urls.

Example:

    Url Matches /(.+)\.google/ig
    Destination https://$1.google.com

In this case, above regex will be matched with interecepted Url.
If regex is matched then $1 will be replaced in the destination Url and redirect happens to destination url.

## Wildcard Match Operator

Wildcard match operator matches expression with the Url interecepted by chrome.
We only support asterisk (*) as wildcard operator. * can match 0 or more characters in intercepted url.
Please note that in wildcard match, complete url is matched with given expression and *'s can be replaced with respective values in destination Url.

Example 1:

    Expression: *://*.yahoo.com
    Url: http://cricket.yahoo.com
    Result: $1 = http, $2 = cricket

Example 2:

    Expression: *yahoo
    Url: http://www.yahoo.com
    Result: Does not match. Note the trails does not match

Example 3:

    Expression: *yahoo*
    Url: http://www.yahoo.com
    Result: $1 = http://www. $2=.com

Example 4:

    Expression: http://*.yahoo.com
    Url: http://cricket.yahoo.com/
    Result: Does not match (Observe the trailing slash in Url)