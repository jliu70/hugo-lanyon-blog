---
title: "Setting up a simple Blog with a Static Website Generator - Part 7: Hugo Advanced Usage Troubleshooting and Debugging"
date: "2015-12-27"
draft: "true"
description: "This is an introduction to Hugo"
categories:
    - "Education"
    - "Explanation"
    - "Tutorial"
tags:
    - "Hugo"
---

# Draft - Raw, Un-edited



NOTE: this links (accredits) to another great blog which is quite similar to what I'm making.  It looks nice, but it doesn't have some features I have implemented.  The code and the environment seems to be much cleaner though.
https://github.com/xaprb/xaprb-src.git
```
Maybe look at his config.yaml  
    GoogleAnalytics variable
NOTE: I was not able to get it to work for me initially.  Turns out it was an error in how I was referencing the partial -- missing the trailing dot   {{ partial "footer.html" . }} in various templates
Very subtle - but the missing dot still rendered HTML, but did not find the variables.  

```




http://zackofalltrades.com/notes/2014/05/hugo-from-scratch/
A good primer
```
Dump variables during testing:
Various other languages have tools to dump variable content (pprint, var_dump, Data::Dumper, etc.).

printf "%+v" is the golang equivalent of these, and as the variables pages is pretty sparse on how data is actually structured in Hugo, I’ve found this to be helpful when doing printf debugging:

{{ .Site | printf "%+v" }}
This could also come in handy for other more complex formatting needs.
```

http://gohugo.io/templates/variables/

https://discuss.gohugo.io/t/define-variables/1800/2



## RSS feed
setting up RSS feed  with `layouts/rss.xml`

The RSS feed is generated to `public/index.xml`




1/12/2016 http://j3ff.com/blog/building-a-site-with-hugo/
Useful but very terse.
```
Trials and Travails

At one point I had {{ template "chrome/footer.html" }} rather than {{ template "chrome/footer.html" . }} and without the last “.” the template did not have the variables available to it and of course I spent entirely too long figuring that out.

```
`this happened to me as well  :)`




# Tools - https://gohugo.io/tools/

> Lists many useful tools which includes migration tools allows you to migrate from other platforms to Hugo.
