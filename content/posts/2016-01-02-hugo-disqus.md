---
title: "Setting up a simple Blog with a Static Website Generator - Part 10: Hugo Disqus"
date: "2016-01-02"
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

## 1/6/2016 Disqus {#disqus}
https://gohugo.io/extras/comments/

http://www.willwoodgate.com/index_files/adding-disqus-commenting-to-any-page-in-your-rw-website.html

```
My disqus shortname:  yourDisqusShortname

Global config file disqusShortname variable needs to be under params
https://github.com/spf13/hugo/issues/1224

config.yaml:
params:
  disqusShortname: "yourDisqusShortname"


Disqus admin page
https://yourDisqusShortname.disqus.com/admin/settings/general/
https://yourDisqusShortname.disqus.com/admin/discussions/


Install also worked with the following (but without the logic for localhost):
https://yourDisqusShortname.disqus.com/admin/settings/universalcode/

```

NOTE: the following shows example for the if statement

https://github.com/tummychow/lanyon-hugo/pull/6/files

`layouts/chrome/disqus.html`

```

<aside id=comments>
    <div><h2>Comments</h2></div>
<div id="disqus_thread"></div>
<script type="text/javascript">
    (function() {
        // Don't ever inject disqus on localhost--it creates unwanted
        // discussions from 'localhost:1313' on your disqus account...
        if (window.location.hostname == "localhost") {
            return;
        }
        var disqus_shortname = '{{ .Site.Params.disqusShortname }}';
        var disqus_identifier = '{{if isset .Params "disqus_identifier" }}{{ index .Params "disqus_identifier" }}{{ else }}{{ .Permalink }}{{end}}';
        var disqus_title = '{{if isset .Params "disqus_title" }}{{ index .Params "disqus_title" }}{{ else }}{{ .Title }}{{end}}';
        var disqus_url = '{{if isset .Params "disqus_url" }}{{ index .Params "disqus_url" | html  }}{{ else }}{{ .Permalink }}{{end}}';
        var dsq = document.createElement('script'); dsq.type = 'text/javascript'; dsq.async = true;
        dsq.src = '//' + disqus_shortname + '.disqus.com/embed.js';
        (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(dsq);
    })();
</script>
<noscript>Please enable JavaScript to view the <a href="http://disqus.com/?ref_noscript">comments powered by Disqus.</a></noscript>
<a href="http://disqus.com" class="dsq-brlink">comments powered by <span class="logo-disqus">Disqus</span></a>
</aside>
```

https://help.disqus.com/customer/en/portal/articles/472098-javascript-configuration-variables



```
spf13.com

NOTE: the following will create unwanted disqus discussions when running as localhost, so refer to https://gohugo.io/extras/comments/
to have a conditional detect localhost - see layouts/chrome/disqus.html

layouts/partials/disqus.html

$ cat partials/disqus.html
<aside id=comments>
    <div><h2> Comments </h2></div>
    {{ template "_internal/disqus.html" . }}
</aside>




from a typical post front-matter meta data in spf13.com:
disqus_identifier: 1162 http://spf13.com/?p=1162
disqus_title: WP GitHub Code Viewer
disqus_url: http://spf13.com/post/wp-github-code-viewer/



Front-Matter:  http://gohugo.io/content/front-matter/

The front matter is one of the features that gives Hugo its strength. It enables you to include the meta data of the content right with it. Hugo supports a few different formats, each with their own identifying tokens.



```
