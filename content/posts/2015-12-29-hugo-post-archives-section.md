---
title: "Setting up a simple Blog with a Static Website Generator - Part 8: Hugo Post Archives Section"
date: "2015-12-29"
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


## Changes to enable `Post Archives` {#archives}


`1.` Edit `static/css/mystyles.css` to add the relevant "postlist" entries

`2.` Modify `layouts/indexes/posts.html`

got this following tweak `.Data.Pages.GroupByDate "2006"` from `spf13 layouts/_default/section.html`  - tweak css based from `spf13/static/css/mystyles.css`

```
$ git diff layouts/indexes/posts.html
diff --git a/layouts/indexes/posts.html b/layouts/indexes/posts.html
index e368059..7fc6c55 100644
--- a/layouts/indexes/posts.html
+++ b/layouts/indexes/posts.html
@@ -4,7 +4,7 @@

 {{ template "chrome/header.html" . }}

-<body class="theme-base-08">
   {{ template "chrome/sidebar.html" . }}

   <!-- See /layouts/indexes/category.html for explanation of this section -->
@@ -12,7 +12,7 @@
     <div class="masthead">
       <div class="container">
         <h3 class="masthead-title">
-          <a href="/posts" title="Blog">Blog Posts</a>
+          <a href="/" title="Home">Home</a>
         </h3>
       </div>
     </div>
@@ -27,13 +27,15 @@
     <div class="container content">
     <p>Here are all my blog posts, in descending order by creation date. If you would like to view them by topic, see the <a href="/categories">Categories</a> page.</p>
       <h1 class="post-title">All Blog Posts (By Date)</h1>
-        <section id="main">
-          <ul id="list">
-            {{ range .Data.Pages }}
-            {{ .Render "li"}}
-            {{ end }}
-          </ul>
-        </section>
+      <!-- got this following tweak GroupByDate "2006" from spf13 layouts/_default/section.html  - now just need to customize posts/li.html  can tweak css based of spf13/static/css/_mystiles.css  -->
+            {{ range .Data.Pages.GroupByDate "2006" }}
+           <h2>{{ .Key }}</h2>
+               <ul class="postlist">
+               {{ range .Pages }}
+                   {{ .Render "li"}}
+                {{ end }}
+               </ul>
+           {{ end }}
     </div>
   </div>
```

`3.` Edit `layouts/posts/li.html`

Reference `ul class="postlist"` from `mystyles.css`
```
$ cat layouts/posts/li.html
    <ul class="postlist">
    <li>
      <a href="{{ .Permalink }}">{{ .Title }} {{ if .GetParam "draft"}}DRAFT{{end}}</a>
      <span>{{ .Date.Format "Mon, Jan 2, 2006" }}</span>
    </li>
    </ul>
```



`4.` Add sidebar menu for "Post Archives" and "Tags"
```
$ git diff layouts/chrome/sidebar.html
diff --git a/layouts/chrome/sidebar.html b/layouts/chrome/sidebar.html
index d69004b..bf97e79 100644
--- a/layouts/chrome/sidebar.html
+++ b/layouts/chrome/sidebar.html
@@ -18,7 +18,11 @@
   <nav class="sidebar-nav">
     <a class="sidebar-nav-item" href="/">Home</a>

-    <a class="sidebar-nav-item" href="/posts">Blog</a>
+    <a class="sidebar-nav-item" href="/posts">Post Archives</a>
+
+    <a class="sidebar-nav-item" href="/categories">Post Categories</a>
+
+    <a class="sidebar-nav-item" href="/tags">Content Tags</a>
   </nav>

   <div class="sidebar-item">
```

### References
http://spf13.com/post/
