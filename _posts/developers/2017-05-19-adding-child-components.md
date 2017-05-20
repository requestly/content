---
layout: post
title: "Add childViews in Backbone"
modified:
categories: developers
sample: false
developerPost: true
excerpt: "How to add child components to backbone views"
tags: []
date: 2017-05-19T15:39:55 +05:30
comments: true
share: true
---

Requestly uses `Backbone` as primary UI front end developer framework. This articles demonstrates how to add 
child components/childViews to your backbone views.
 
Before starting, let's think about what do we need to create childViews. (Requirements)
- When a parent view is rendered, all of its childViews should be re-rendered
- When a parent view is destroyed, all of its childViews should be destroyed
- A parent view should have capability to list down all of its childViews and call render on them

## Step1: (Override Backbone.View.Prototype.remove function - One time step) 

{% highlight js %}

    Backbone.View.prototype.close = function() {
      if (this.childViews && this.childViews instanceof Backbone.View) {
        for (var i = 0; i < this.childViews.length; i++) {
          this.childViews[i].close();
        }
      }
    
      this.remove();
      this.unbind();
    };
{% endhighlight %}

## Step2: Define an `onBeforeRender` function in the parentView which has childViews (BaseIndexView.js has this)

{% highlight js %}
    
    /**
    * Close all subComponents so that they should be rerendered once the parent view is rendered
    */
    onBeforeRender: function() {
    if (this.childViews && this.childViews.length) {
      _.each(this.childViews, function(childView) {
        childView.close();
      })
    }
    
    this.childViews = [];
    }
{% endhighlight %}

## Step3: In ParentView define childViews and render each childView (RuleIndexView.js)

{% highlight js %}
    childViews: [],
    
    // More Code
    
    renderSubComponents: function() {
      this.childViews.push(this.renderPushNotificationComponent());
    },
    
    renderPushNotificationComponent: function() {
      this.pushNotificationView = new PushNotificationView({
        el: this.$el.find('.notification-container')
      });
    
      this.pushNotificationView.render({ update: true });
    
      return this.pushNotificationView;
    }
 
{% endhighlight %}

There are two baseViews in the code base right now.
1. BaseIndexView - For IndexViews based on collection
2. BaseView - For Model based views
 
All other views extend either of these or subsidiary of these views.