---
title: "Setting up a simple Blog with a Static Website Generator - Part 6: Hugo layouts"
date: "2015-12-26"
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

## Part 6: Hugo Layouts
- explanation of partials
- explanation of posts/li.html posts/single.html posts/summary.html
- masthead - one reason for separate root/index.html  - also seems to be a Hugo requirement
- Summary vs Description - for some reason summary formatting sucks
- pagination
- Footer

The [previous][xref-1] post covered setting the theme color for your website within the Lanyon CSS.  We also described how by default Poole CSS disabled bulleted lists, and how we can re-enable bulleted lists.  We also briefly reviewed why you don't necessarily want to use a "liquid layout" for a Blog site, and also setting up your own favicon.

In this post I will start going into the details around setting the layouts of the website.

### Templates



1/13/2016 https://gowalker.org/github.com/bobthecow/hugo
  A good primer, but a little outdated?   Layout - Templates - Template roles

Templates

Hugo uses the excellent golang html/template library for it's template engine. It is an extremely lightweight engine that provides a very small amount of logic. In our experience that it is just the right amount of logic to be able to create a good static website

This document will not cover how to use golang templates, but the golang docs provide a good introduction.

Template roles

There are 5 different kinds of templates that Hugo works with.

  index.html

This file must exist in the layouts directory. It is the template used to render the homepage of your site.

  rss.xml

  This file must exist in the layouts directory. It will be used to render all rss documents. The one provided in the example application will generate an ATOM format.

  Important: Hugo will automatically add the following header line to this file.

  <?xml version="1.0" encoding="utf-8" standalone="yes" ?>

  Indexes

  An index is a page that list multiple pieces of content. If you think of a typical blog, the tag pages are good examples of indexes.

  Content Type(s)

  Hugo supports multiple types of content. Another way of looking at this is that Hugo has the ability to render content in a variety of ways as determined by the type.


### Partials
Hugo [partials](https://gohugo.io/templates/partials/) allows users to break up templates into parts, and grants users the ability to override the partial theme with local layouts.

To reference a partial template stored in a subfolder, e.g. `/layout/partials/post/tag/list.html`, call it this way:

```
  {{ partial "post/tag/list" . }}
```
Note that the subdirectories you create under `/layout/partials` can be named whatever you like.

> NOTE: it is important to pass the second parameter `.` as this specifies that variables be passed onto the partial template.  Without it you will find that your variables will no longer be defined and may break how your page is generated.



  Adding a new content type

  Adding a type is easy.

  Step 1: Create a directory with the name of the type in layouts.Type is always singular. Eg /layouts/post.

  Step 2: Create a file called single.html inside your directory. Eg /layouts/post/single.html.

  Step 3: Create a file with the same name as your directory in /layouts/indexes/. Eg /layouts/index/post.html.

  Step 4: Many sites support rendering content in a few different ways, for instance a single page view and a summary view to be used when displaying a list of contents on a single page. Hugo makes no assumptions here about how you want to display your content, and will support as many different views of a content type as your site requires. All that is required for these additional views is that a template exists in each layout/type directory with the same name.

  For these, reviewing the example site will be very helpful in order to understand how these types work.

  Variables

  Hugo makes a set of values available to the templates. Go templates are context based. The following are available in the context for the templates.

  .Title The title for the content.
  .Description The description for the content.
  .Keywords The meta keywords for this content.
  .Date The date the content is published on.
  .Indexes These will use the field name of the plural form of the index (see tags and categories above)
  .Permalink The Permanent link for this page.
  .FuzzyWordCount The approximate number of words in the content.
  .RSSLink Link to the indexes' rss link

  Any value defined in the front matter, including indexes will be made available under .Params. Take for example I'm using tags and categories as my indexes. The following would be how I would access them:

  .Params.Tags
  .Params.Categories
  Also available is .Site which has the following:

  .Site.BaseUrl The base URL for the site as defined in the config.json file.
  .Site.Indexes The names of the indexes of the site.
  .Site.LastChange The date of the last change of the most recent content.
  .Site.Recent Array of all content ordered by Date, newest first

  Content

  Hugo uses markdown files with headers commonly called the front matter. Hugo respects the organization that you provide for your content to minimize any extra configuration, though this can be overridden by additional configuration in the front matter.

  Organization

  In Hugo the content should be arranged in the same way they are intended for the rendered website. Without any additional configuration the following will just work.





  http://spf13.com/post/hugo-summer2014-update/


1/12/2016 another very terse url introducing Hugo http://usersnap.com/blog/hands-on-experience-with-hugo-static-site-generator/



http://www.humboldtux.net/sbcb-demo/post/post-01/
  Building a theme with Hugo

https://www.digitalocean.com/community/tutorials/how-to-install-and-use-hugo-a-static-site-generator-on-ubuntu-14-04
  A good tutorial for Linux users

  1/12/2016 Octopress theme for Hugo  https://discuss.gohugo.io/t/theme-sshq/413

  1/12/2016 another url introducing Hugo http://usersnap.com/blog/hands-on-experience-with-hugo-static-site-generator/


  ### 1/12/2016 http://j3ff.com/blog/building-a-site-with-hugo/
  Useful but very terse.



`4`. Changed `Summary` to `Description`

  For some reason summary formatting sucked.  Description is a [front-matter meta field ](http://gohugo.io/content/front-matter/) you can control with a brief statement or even the first paragraph of a post.

  > The front matter is one of the features that gives Hugo its strength. It enables you to include the meta data of the content right with it. Hugo supports a few different formats, each with their own identifying tokens.


  ```
  $ git diff layouts/posts/summary.html
  diff --git a/layouts/posts/summary.html b/layouts/posts/summary.html
  index 5021ca9..43c87c7 100644
  --- a/layouts/posts/summary.html
  +++ b/layouts/posts/summary.html
  @@ -17,7 +17,7 @@
         <div class="meta">{{ .Date.Format "Mon, Jan 2, 2006" }}</div>
       </header>

  -    {{ .Summary }}
  +    {{ .Description }}
       <footer>
           <a href='{{ .Permalink }}'><nobr>Read more →</nobr></a>
       </footer>
  ```

  Example post front-matter description

  ```
  ---
  title: "Setting up Hugo a really really really really really really really really really really really really really long title"
  date: "2015-12-26"
  description: "This is an introduction to Hugo"
  categories:
    - "Education"
    - "Explanation"
    - "Tutorial"
  tags:
    - "Hugo"
    - "CSS"
  ---

  ```




### Pagination {#pagination}

  `5.` Changed pagination labels

  ```
  $ git diff layouts/chrome/prev_next.html
  diff --git a/layouts/chrome/prev_next.html b/layouts/chrome/prev_next.html
  index 833d065..d5cd93c 100644
  --- a/layouts/chrome/prev_next.html
  +++ b/layouts/chrome/prev_next.html
  @@ -17,13 +17,13 @@
     <hr />
     {{if .Prev}}
       <span class="left">
  -    &nbsp; <em>&laquo; Previous:</em> <a class="next" href="{{.Prev.Permalink}}">{{.Prev.Title}}</a>
  +    &nbsp; <em>&laquo; Newer:</em> <a class="next" href="{{.Prev.Permalink}}">{{.Prev.Title}}</a>
       </span>
     {{end}}

     {{if .Next}}
       <span class="right">
  -    <em>Next: </em><a class="next" href="{{.Next.Permalink}}"> &nbsp; {{ .Next.Title }}</a> &raquo;
  +    <em>Older: </em><a class="next" href="{{.Next.Permalink}}"> &nbsp; {{ .Next.Title }}</a> &raquo;
       </span>
     {{end}}
   </div>
  ```




## Changes for footer 1/6/2016 {#footers}

  `layouts/chrome/footer.html`

  ```

  <!--
    This is the main footer for the website. It is included on every page.

    It is very basic. It has some text and a link back to the home page of the
    site.

    It includes the google analytics template from /layouts/chrome/ga.html

    It also closes the <body> and <html> tags for each page.
  -->

  <div class="container content">
  <footer>
    <div>
      <p class="right credit">
      &copy; 2015-16 Jeff Liu.  <a href="http://creativecommons.org/licenses/by/3.0/" title="Creative Commons Attribution">Some rights reserved</a>; please attribute properly and link back. <br>
      Powered by <a href="http://gohugo.io">Hugo</a>.
      </p>
    </div>
  </footer>
  </div>

  {{ template "chrome/ga.html" . }}

  </body>
  </html>
  ```


  [xref-1]: {{< relref "2015-12-25-lanyon-css.md" >}}
