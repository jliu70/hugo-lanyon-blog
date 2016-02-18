---
title: "Setting up a simple Blog with a Static Website Generator - Part 11: Hugo Shortcodes"
date: "2016-01-01"
draft: "true"
description: "This is an introduction to Hugo"
categories:
    - "Education"
    - "Explanation"
    - "Tutorial"
tags:
    - "CSS"
---

# Draft - Raw, Un-edited


## 12/27/2015 Added short codes for IMG embedding referenced from spf13.com {#shortcodes}
```
	layouts/shortcodes/

img.html		scribd.html		slideshare.html		speakerdeck.html	vimeo.html		youtube.html

```

His talk begins at around 1:49:00 in the following video:
<iframe width="720" height="480" src="https://www.youtube.com/embed/Fx304EfqtMo" frameborder="0" allowfullscreen></iframe>


{{% img src="/media/resize-partition.gif" class="third right" alt="resize partition" %}}

Hrm.  Wonder what are the advantages for shortcode.

## shortcode for embedding image for markdown
## NOTE: this has been expanded and elaborated more from the original!!
Shortcode?  for Embedding image?  NOTE: `class="headshot"` within shortcode does not work properly within markdown content file.  Can't use HTML to add a new div container like I did in `layouts/index.html`.  

Although in about/me.md I just called a straight up HTML img tag.

{{% img src="/media/accountImageJeff.jpg" class="headshot" alt="account Jeff" %}}
Hrm. Wonder what are the advantages for shortcode.

<img class="headshot" src="/media/accountImageJeff.jpg" alt="account Jeff"></img>
Hrm. Wonder what are the advantages for shortcode.

<img class="third right" src="/media/snowflake-wide.jpg" alt="snowflake-wide"></img>

Hrm. Wonder what are the advantages for shortcode.
{{% img src="/media/snowflake-wide.jpg" class="third right" alt="snowflake-wide" %}}
Hrm. Wonder what are the advantages for shortcode.


## Changes for photo 1/2/2016

`layouts/index.html`

```
+        <div class="team-member">
         <!-- About me subsection -->
         <h2>About me</h2>

@@ -60,6 +61,9 @@

         <p>It might even include a picture: </p>

+        <img class="headshot" src="/media/accountImageJeff.jpg" alt="account Jeff"></img>
+        </div>
```

`static/css/mystyles.css`

```

.team-member{
  float: center;
}
.headshot{
  width: 100px;
  display: block;
  margin: 0 auto;
  -webkit-border-radius: 100%;
  -moz-border-radius: 100%;
  border-radius: 100%;
}
```
