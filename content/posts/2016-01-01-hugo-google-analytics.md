---
title: "Setting up a simple Blog with a Static Website Generator - Part 10: Hugo with Google Analytics"
date: "2016-01-01"
draft: "true"
description: "This is an introduction to Hugo"
categories:
    - "Education"
    - "Explanation"
    - "Tutorial"
tags:
    - "Hugo"
---

# Draft

There was a time when simply publishing a website was enough.  However, it is increasingly important to maximize your web presence.  You need to know how your website is performing, the results you are achieving, and how you are getting your visitors.  Google understands this importance like no one else, and they place a high priority on providing users important analytics and metrics.  Many people might not have heard of [Google Analytics](https://www.google.com/analytics) or find the concepts confusing.

From "Hello Startup" Page 145

> Your goal is not to be published in a scientific journal but to gather data that increases the odds that you’re making good decisions. To do that, simple, imperfect methods are usually good enough.

> Moreover, as is a common theme in this book, measurement is an iterative process. You don’t have to set up the perfect tracking and analytics system from day one. You don’t have to measure everything to get value out of measuring. In fact, you usually get the most bang for the buck off of the initial few measurements, and then diminishing returns with more and more elaborate methods. Start small, perhaps by tracking just a single metric (see “The magic number”), and then gradually evolve your approach to measure more and more.


I won't even try to write a simple Google Analytics guide because a super awesome guide with plenty of screen shots already exists.  This guide gives a clear description on what Google Analytics is and the information that it provides. The guide then goes into each of the steps of setting up Google Analytics, which can be a long and confusing process. The guide then shows you how to view the collected information and what you can do with it.  Check it out and make sure you understand and use these basics!



## Absolute Beginner's Guide to Google analytics
https://moz.com/blog/absolute-beginners-guide-to-google-analytics

> If you don't know what Google Analytics is, haven't installed it on your website, or have installed it but never look at your data, then this post is for you. While it's hard for many to believe, there are still websites that are not using Google Analytics (or any analytics, for that matter) to measure their traffic. In this post, we're going to look at Google Analytics from the absolute beginner's point of view. Why you need it, how to get it, how to use it, and workarounds to common problems.

> ## Why every website owner needs Google Analytics

> Do you have a blog? Do you have a static website? If the answer is yes, whether they are for personal or business use, then you need Google Analytics. Here are just a few of the many questions about your website that you can answer using Google Analytics.

> - How many people visit my website?
> - Where do my visitors live?
> - Do I need a mobile-friendly website?
> - What websites send traffic to my website?
> - What marketing tactics drive the most traffic to my website?
> - Which pages on my website are the most popular?
> - How many visitors have I converted into leads or customers?
> - Where did my converting visitors come from and go on my website?
> - How can I improve my website's speed?
> - What blog content do my visitors like the most?

> There are many, many additional questions that Google Analytics can answer, but these are the ones that are most important for most website owners. Now let's look at how you can get Google Analytics on your website.


NOTE: there are some really useful user comments there as well.



Some user comments around views:

> Another tip for beginners: When you create your GA account, a View called "All Website Data" is created. Leave this view alone! You want that View to remain exactly as it is, tracking all data from all visitors.

> What you should do next is create a new View, let's call it "MyWebsite.com - filter internal IPs - 6.24.15". Use this new View to begin playing around with your data, adding Filters that exclude traffic to your website from your company, your home, etc.

> Create new Views whenever necessary to allow you a safe sandbox to play with your data. If you don't like how your experiments with your GA data turned out, you can modify or delete those Views.

> But you can do so knowing that all your website data is safely captured in "All Website Data".



> Great point! It's also important to note that a new View does not go back and filter historic data. It only applies to data collected after it is created.



> Good points - I'd always advise people to have at least 3 basic views - leave All Website Data as a back up, create a Test view where you can try things out and not worry about making mistakes. And a third view for day to day reporting based on properly adjusted and filtered data. Particularly pertinent when filtering out bots/spiders, employee visits, etc.

> And views are indeed long term filters. No going back to retrieve data you didn't capture in the first place!



> Yes - you ALWAYS want to make new views in test views. Once you lose data in GA, there's no going back :/


Another topic from user comment:

> Thank you Kristi! this is a great walkthrough for beginners. I know that everyone have their preferred set of basic initial configurations but I have two other Google Analytics features that I would like to recommend as well:

> 1) Under any graphic report you will find an area in which you can add notes (aka annotation) with specific dates that will help you to log when a campaign started, website changes or improvements. With this is really easy to track any occurrence that may positively or negatively influence traffic on your website. I like to add notes such as "Improved home page layout", "PPC campaign started". Google "Google analytics annotations" for more info.

> 2) in Admin Under any VIEW and Channel Settings select "Manage brand terms" there you will have the opportunity to indicate which keywords belong to your brand and almost automatically you will have an additional "Brand Search" segment that will come really handy in your future reports.



And other user comments:

> Great post. I've seen and modified many 00s of GA account set ups from organisations of all sizes over the years. Even now, it is surprising how few of them are properly set up in the way in which you have cogently outlined above. Sticking with the default view, failure to filter and lack of goals are still the stand out issues.

> If you have no goals defined, what exactly are you analysing? As Avanash Kaushik memorably described it, without goals, you are merely "data puking".



Question on excluding your IP address - best to create a new view and then excluding your IP address:

> One question: how do yo prevent GA from counting your visits/ sessions to the website being analysed? I'm redesigning it and uploading new content (all while the website is live) and I enter it dozens of times a day to check improvements. I don't want to see my visits being included in the reports. Any suggestions?

> You can do that by creating a new view for your website and excluding your IP address to hide internal traffic. The directions for that can be found on https://support.google.com/analytics/answer/1034840?hl=en. :)




Dealing with spam:

> The only thing missing from this article is how to filter out SPAM, which for a small traffic website is an absolute must. A few of our client websites generate <1000 hits / month, but get 2-3000 SPAM hits! I've found creating an allow filter from your host kills off 95+% of bots.




## 1/12/2016 Google Analytics {#analytics}
Set up a Google Analytics account to get basic site statistics.

http://www.google.com/analytics/



```
1/13/2016   Signed up with account "jeff@usedgoodies.com"
Seems like you need to enable Analytics within Google Apps
Then it seems like a seprate login.  
```

### Turn on Google Analytics for users
https://support.google.com/a/answer/6304816

Turn Google Analytics on or off for users

If you're an administrator of Google accounts for an organization, you can control who uses Google Analytics from their account. Just turn Analytics on or off for those people in your Admin console. People who have Analytics turned on can use it to monitor traffic at your websites or mobile apps.

To control who uses Analytics in your organization
Before you begin: To turn the service on or off for select groups of users, put their accounts in an organizational unit.

In your Google Admin console (at admin.google.com)...

Go to Apps > Additional Google Services > Google Analytics.
https://admin.google.com/AdminHome#AppDetails:service=Google+Analytics

At the top of the gray box, click Settings and choose:

On for everyone to turn on the service for all users (click again to confirm).

Off to turn off the service for all users (click again to confirm).

On for some organizations to change the setting only for some users.

If you chose On for some organizations:

Select the organization that contains the users whose settings you want to change.

Click Override or Inherit, whichever is showing.

Click On Turn on icon or Off Turn off icon to change the setting.

Click Apply. Then click again to confirm.

Learn more about the organizational structure.

Click Apply.


### Next Step:  Google Analytics Help Center
https://support.google.com/analytics#topic=3544906


### Getting Started with Google Analytics
https://support.google.com/analytics/answer/1008015?hl=en&ref_topic=3544906

Sign in  http://www.google.com/analytics/



```
Tracking ID
UA-XXXXXXXXX-1

Status
Receiving traffic in past 48 hours.
1 active users right now. See details in real-time traffic reports.
```

Website tracking
This is the Universal Analytics tracking code for this property.
To get all the benefits of Universal Analytics for this property, copy and paste this code into every webpage you want to track.

Add the following to ga.html

```

<script>
  (function(i,s,o,g,r,a,m){i['GoogleAnalyticsObject']=r;i[r]=i[r]||function(){
  (i[r].q=i[r].q||[]).push(arguments)},i[r].l=1*new Date();a=s.createElement(o),
  m=s.getElementsByTagName(o)[0];a.async=1;a.src=g;m.parentNode.insertBefore(a,m)
  })(window,document,'script','//www.google-analytics.com/analytics.js','ga');

  ga('create', '{{ .Site.GoogleAnalytics }}', 'auto');
  ga('send', 'pageview');

</script>
```

Get started with Analytics

Find your way around Analytics

Manage and configure Analytics

Hierarchy of accounts, users, properties, and views

Set up (web)

Set up (mobile apps)

Diagnostics messages

Universal Analytics (UA)

Glossary
