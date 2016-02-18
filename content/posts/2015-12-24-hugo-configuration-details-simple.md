---
title: "Setting up a simple Blog with a Static Website Generator - Part 4: Hugo Configuration Details - Simple"
date: "2015-12-24"
draft: "false"
description: "This is an introduction to Hugo"
categories:
    - "Education"
    - "Explanation"
    - "Tutorial"
tags:
    - "Hugo"
---

This is part 4 in a [series of blog posts][xref-1] which outline how to setup a simple blog with a static website generator.

The [previous][xref-2] post provided basic configuration and usage of [Hugo][link-1] with this example template website.  Many details were skipped because the goal was to allow someone to get a website up and running quickly.

Now let's walk through some simple configuration settings.


## Permalinks {#permalinks}

[Permalinks][link-3] can be set/not set per your own preference.

Use of permalinks allows you to present your content in a consistent way independently of how your content is organized.  

If you rearrange how your content is organized within your content directory, permalinks ensures that links to your posts remain constant (and therefore won't break links to them).

Here's a [great post](https://npf.io/2014/08/hugo-beyond-the-defaults/) which goes into more details of why you might use permalinks (and other cool things like [aliases](http://hugo.spf13.com/extras/aliases)).



## Hugo 404.html setup {#404}

When visitors try to retrieve a page that does not exist on your website, typically the web server will return a "404" error.  The generic 404 error doesn't provide the user with any useful information, and most users may just surf away from your site.  You can provide a more friendly experience for users by setting up a custom "404" web page.  A good custom 404 page will provide people helpful information and encourage them to explore your website.     

[Hugo documentation](https://gohugo.io/templates/404/) outlines various ways to implement 404 web page for apache, nginx, AWS S3, etc.  

> NOTE: As of Hugo v0.15, the built-in Hugo server (`hugo server`) does not support  404 templates, but you can access the page locally to test it:  http://localhost:1313/404.html
>
> Reference: https://github.com/spf13/hugo/issues/874


Related:  Setting up Hugo with Nginx  http://www.bigbeeconsultants.co.uk/blog/hosting-hugo-website-behind-nginx


## Drafts {#drafts}


Hugo has a [draft](https://gohugo.io/overview/quickstart/) feature which enables you to flag when a post is a draft (true/false).  By default Hugo will not generate HTML for content that is flagged as draft.  To flag a post as a draft, set the draft configuration parameter within the front-matter metadata (example YAML format) `draft: "true"`.  


```
---
title: "First sample post"
date: "2015-12-15"
description: "This should be a more useful description"
draft: "true"
categories:
    - "Explanation"
    - "Tutorial"
    - "test"
tags:
    - "fun"
---
```

When you call `hugo`, you can specify the option `--buildDrafts` to render the posts flagged as `draft`


```
$ hugo server --buildDrafts
12 of 12 drafts rendered
0 future content
22 pages created
0 paginator pages created
8 tags created
5 categories created
in 120 ms
Watching for changes in /path/to/root/{content,layouts,static}
Serving pages from memory
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

There's also a hugo command `hugo undraft /path/to/content/content.md` to change the draft status of posts from 'True' to 'False' and set the date to the current date.  [Hugo documentation](https://gohugo.io/commands/hugo_undraft/) has more information.


## Cross References {#cross-references}

Hugo allows you to create links between your documents.  You can specify anchors to link to a specific section.  The [Hugo Documentation](https://gohugo.io/extras/crossreferences/) has more details.

Example `relref`
```
[post on cross references]({{</* relref "2015-12-23-basic-config-usage.md#cross-references" */>}})
```

Example `anchor`
```
### Cross references {#cross-references}

```




## Conclusion

In this post we covered some simple configuration settings which are important to the look and feel of your website.  

In the next post, I will describe how to choose your theme color within the Lanyon CSS, as well as re-enabling bulleted lists.



[link-1]: http://gohugo.io
[link-2]: https://github.com/jliu70/hugo-lanyon-blog
[link-3]: http://gohugo.io/extras/permalinks
[xref-1]: {{< relref "2015-12-20-simple-blog-static-website-generator.md" >}}
[xref-2]: {{< relref "2015-12-23-basic-config-usage.md" >}}
