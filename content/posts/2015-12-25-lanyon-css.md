---
title: "Setting up a simple Blog with a Static Website Generator - Part 5: Lanyon CSS and static stuff"
date: "2015-12-25"
draft: "true"
description: "This is an introduction to Hugo"
categories:
    - "Education"
    - "Explanation"
    - "Tutorial"
tags:
    - "CSS"
---

The [previous][xref-1] post covered some simple configuration settings.

In this post we'll show how to create your own custom theme color for use with [Lanyon CSS](http://lanyon.getpoole.com/).  We'll also describe how to re-enable bulleted lists (which appears to be disabled in poole.css by default).  We'll also look at setting up your own favicon.

### A Brief Introduction to CSS

CSS stands for [Cascading Style Sheets](https://www.w3.org/Style/CSS/).  CSS is designed primarily to enable the separation of content from presentation (mostly commonly aspects such as fonts, colors, and layout).   By specifying CSS in a separate .css file, it reduces complexity and repetition -- changes made in a central place can apply to many documents quickly and easily.  This also helps provide site-wide consistency.

With CSS, the "cascade" refers to a priority scheme to determine which style rules apply if more than one rule matches against a particular element.  In most cases this can be thought of as local precedence.  When you have a definition of an element defined multiple times, the latest occurence / most local definition is the one that is used.

Therefore instead of directly modifying lanyon.css, we can create our own style sheet, and then make sure that it's referenced last.

> Disclaimer: I'm not a web designer.  A general rule of thumb I follow is to avoid editing files which are not "owned" or "authored" by me.  This allows flexibility for updates of the source files.  This approach might not be considered good practice for web design.  


### Custom Color Scheme {#theme}

By default, the Lanyon CSS provides [eight optional color schemes](https://github.com/poole/lanyon#themes).  

To use my own custom color, I will create a new custom custom color scheme `theme-base-0g`.   We'll create a new style sheet called `mystyles.css` within the `static/css/` directory.  Then we will copy and paste an existing stanza from `static/css/layon.css` into `static/css/mystyles.css`.  You can find the hex code for colors with a [color picker](http://www.w3schools.com/colors/colors_picker.asp).  

Add the following to `static/css/mystyles.css`:
{{< highlight css >}}
/* My Blue */
.theme-base-0g .sidebar,
.theme-base-0g .sidebar-toggle:active,
.theme-base-0g #sidebar-checkbox:checked ~ .sidebar-toggle {
  background-color: #0174DF;
}
.theme-base-0g .container a,
.theme-base-0g .sidebar-toggle,
.theme-base-0g .related-posts li a:hover {
  color: #0174DF;
}
{{< /highlight >}}

We will also need  to include a reference to `mystyles.css` in `layouts/partials/head_includes.html`


{{< highlight html >}}
  <link rel="stylesheet" href="/css/poole.css">
  <link rel="stylesheet" href="/css/lanyon.css">
  <link rel="stylesheet" href="http://fonts.googleapis.com/css?family=PT+Serif:400,400italic,700|PT+Sans:400">
  <link rel="stylesheet" href="/css/mystyles.css">

  <link rel="shortcut icon" href="/favicon.ico" type="image/x-icon" />
  <link rel="apple-touch-icon" href="/apple-touch-icon.png" />

{{< /highlight >}}

Lastly, we will update the files `layouts/partials/header.html` and `layouts/index.html` to reference the new theme.

{{< highlight html >}}

  <body class="theme-base-0g">

{{< /highlight >}}




### Re-enabling Bulleted Lists {#Lists}

One thing I noticed was that bulleted lists in markdown didn't seem to work.  Lists would not be displayed with bullets.  Neither "\*" nor "+" nor "1."  -- they all did NOT work.  

The issue seems to originate within the file `poole.css` which had stated
```
list-style-type: none;
```

To re-enable bulleted lists, we can once more override with a statement within our file `static/css/mystyles.css` with the following:

```

/* Lists */
ul, ol, dl {
  vertical-align:top;
  padding: 0 0;
  margin-top: 0;
  margin-bottom: 1rem;
  list-style-type: initial;
}

```



#### jsFiddle {#fiddle}
The following real-time editor helped tremendously in letting me figure out the proper CSS

http://jsfiddle.net/b5KH3/132/

http://jsfiddle.net/fsbhonuv/

Sep 13, 2010 Interview with jsFiddle Creator Piotr Zalewa https://davidwalsh.name/jsfiddle-interview

jsFiddle: An online playground for your JavaScript, HTML, CSS   (4/13/2012)
http://www.techrepublic.com/blog/software-engineer/jsfiddle-an-online-playground-for-your-javascript-html-css/

What is jsFiddle?  10/14/2013
http://irisclasson.com/2013/10/14/what-is-jsfiddle-the-ultimate-guide-for-the-ultimate-lightweight-tool-q-249-250/



Google:  css li meta text-align right
http://www.princexml.com/forum/topic/1673/list-item-uses-text-align-from-first-child
http://stackoverflow.com/questions/11328085/pseudo-after-align-right
http://stackoverflow.com/questions/26410013/right-align-and-left-align-ul-li-elements-in-horizontal-navigation-bar
http://stackoverflow.com/questions/19215119/multiple-lines-in-a-horizontally-floated-list-item

Google: css li display table a meta text-align
https://www.sitepoint.com/community/t/two-rows-in-one-row-vertical-alignment-maybe/110395/5
https://css-tricks.com/centering-in-the-unknown/
http://nopeople.com/CSS%20tips/vertical%20center%20with%20CSS/#html
http://stackoverflow.com/questions/3400548/how-to-vertically-align-li-elements-in-ul
http://stackoverflow.com/questions/27732903/how-do-center-an-image-vertically-within-li?lq=1


## General Formatting Reference - The Case Against Liquid Layout

The Lanyon theme is a fixed-width two-column design.

The following article proposes using percentages for a "liquid layout".
Liquid (percentages) layout in lanyon.css reference:
http://ragupappu.com/2015/04/22/setup-website-using-github-pages-and-jekyll/

I initially gave it a try, but using percentages instead of a fixed-width does not provide good formatting for blog content to be front and center - and the formating of the archives page which displays a historical list of blog posts also becomes messy.


Many  [articles](http://www.successfulblogging.com/16-rules-of-blog-writing-which-ones-are-you-breaking/) around blog design indicate that wide columns make it harder for people to read.




### Favicon {#favicon}

You can replace the default Lanyon favicon (they tiny icon that shows on the tab of your browser).

You can try generating your own at: http://www.favicon-generator.org/

You can also get pre-generated ones here:
http://www.favicon-generator.org/search/

update the file `layouts/partials/head_includes.html` with the following:
```

<link rel="shortcut icon" href="/favicon.ico" type="image/x-icon" />
<link rel="apple-touch-icon" href="/apple-touch-icon.png" />

```


Other Favicon References

https://realfavicongenerator.net/blog/apple-touch-icon-the-good-the-bad-the-ugly/

http://stackoverflow.com/questions/19029342/favicons-best-practices

https://realfavicongenerator.net/

https://realfavicongenerator.net/faq#why_ico_not_declared




## Conclusion

In this post we covered setting the theme color for your website within the Lanyon CSS.  We also described how by default Poole CSS disabled bulleted lists, and how we can re-enable bulleted lists.  We also briefly reviewed why you don't necessarily want to use a "liquid layout" for a Blog site, and also setting up your own favicon.

In the next post I will start going into the details around setting the layouts of the website.

[xref-1]: {{< relref "2015-12-24-hugo-configuration-details-simple.md" >}}
