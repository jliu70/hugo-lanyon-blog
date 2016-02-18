---
title: "Setting up a simple Blog with a Static Website Generator - Part 8: Hugo Taxonomies"
date: "2015-12-28"
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

https://gohugo.io/taxonomies/overview/



### taxonomies {#taxonomies}
`2.` Tweaked config.yaml to add  `tags` taxonomy and `Permalinks`

Apparently, if you supply a [permalink pattern](http://hugo.spf13.com/extras/permalinks), you can organize your content anyway you want, and Hugo will override your organization with the specified pattern.

This is neat, because you can have files organized by date or subject matter in a subdirectory, but they all come out using the same organized pattern.


By default the template already included `categories` taxonomy

{{< highlight diff >}}
$ git diff config.yaml
diff --git a/config.yaml b/config.yaml
index d8bb4b7..2689cb1 100644
--- a/config.yaml
+++ b/config.yaml
@@ -1,9 +1,15 @@
 ---
+canonifyurls: true
 contentdir: "content"
 layoutdir: "layouts"
 publishdir: "public"
 indexes:
   category: "categories"
-baseurl: "http://spencerlyon2.github.io/hugo_gh_blog"
+  tag: "tags"
+baseurl: "http://spencerlyon2.github.io/blog"
 title: "Hugo Blog Template for GitHub Pages"
-...
+permalinks:
+  posts: "/:year/:month/:day/:title/"
+languageCode: "en-us"
+author:
+  name: "Jeffrey Liu"
{{< /highlight >}}

Added `layouts/chrome/tags.html`

```

<!--
  This file is a template that is included various places to have a list of
  that particular posts categories generated.
-->
<div class="container">
  <ul class="catlist">
    <li><em>Tags: </em></li>
    {{ range .Params.tags }}
      <li><a href="/tags/{{ . | urlize }}">{{ . }}</a> </li>
    {{ end }}
  </ul>
</div>

```

Added `layouts/indexes/tag.html`

```
<!--
  This file is used to render a list of all posts that belong to a specific
  tag.
-->


{{ template "chrome/header.html" . }}

  {{ template "chrome/sidebar.html" . }}

  <!--
    Taken from Lanyon example site.

    Putting everything in the wrap div makes the whole page slide over when the
    navigation button is pressed.

    The masthead is a special Lanyon class that is above the horizontal line at
    the top of each page. To me it seemed like a place to put the page title.

    We want the title to be Blog Posts and we want it to be a link to the
    root of the /posts section of the site.

  -->
  <div class="wrap">
    <div class="masthead">
      <div class="container">
        <h3 class="masthead-title">
          <a href="/" title="Home">Home</a>
        </h3>
      </div>
    </div>

  <!-- Show summary of all posts in a tag -->
    <div class="container content">
      <h1 class="post-title">Content Tags</h1>
        <section id="main">
          <div>
            <h5><a href="/tags">Full Tags Index</a></h5>
            <h2>Posts in &ldquo;{{ .Title }}&rdquo;</h2>
            {{ range .Data.Pages }}
            {{ .Render "summary"}}
            {{ end }}
          </div>
        </section>

    </div>
  </div>

  <label for="sidebar-checkbox" class="sidebar-toggle"></label>

  <!-- Include footer (ends <body> and <html>) -->
  {{ template "chrome/footer.html" }}
```
