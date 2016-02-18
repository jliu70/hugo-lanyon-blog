---
title: "Setting up a simple Blog with a Static Website Generator - Part 2: Installing Hugo"
date: "2015-12-22"
description: "This post describes how to install Hugo and some recommended pre-requisites"
categories:
    - "Explanation"
    - "Tutorial"
tags:
    - "Hugo"
---

This is part 2 in a [series of blog posts][xref-1] which outline how to setup a simple blog with a static website generator.

The [previous][xref-2] post provided an overview of what is and why you should use a Static Website Generator.  It also provided a reference to a list of some of the more popular static website generators.

In this post I outline some reasons why [Hugo][link-1] is my tool of choice.  I  also cover installation of Hugo and recommend some pre-requisites that should help you use Hugo effectively.  I describe how Hugo needs a theme to effectively generate a presentable website, and I introduce the Lanyon theme.  

## Hugo Static Website Generator

I use [Hugo][link-1] as my static website generator.  Hugo is cross-platform, simple to install, and simple to use.

Hugo is built from [Go](https://golang.org), and thus is available as a single binary across multiple platforms (Linux/Mac OS X/Windows).  Having a single binary makes it easy to install and use.  Once downloaded it can be run from anywhere. You don't need to install it into a global location.  There are no dependencies on administrative privileges, databases, runtimes, interpreters or external libraries.  

### Hugo official documentation

This series of blog posts is not intended to be a replacement of the official Hugo documentation.  The Hugo website contains well-written, comprehensive documentation.  The [Hugo Introduction](http://gohugo.io/overview/introduction/) is a great place to start.  If you are not already a web designer, it does require time and patience to absorb all of the concepts and details.  

The [Hugo Quickstart](http://gohugo.io/overview/quickstart/) walks you through setting up a Hugo website from scratch.  For the more visually inclined, the Quickstart page includes a great video.  IMHO, as a non-web designer I found the Quickstart presented tons of information all at once, and I felt overwhelmed.   I agree with the last Quickstart step which states "Have fun" and encourages you to experiment.

### Learn by doing, learn by teaching

There's no substitute for getting your hands dirty and playing with Hugo.  The best way to learn is through trial and error.  I learned a lot just by setting up this website and trying to tweak settings.  I encourage you to do the same.  Feel free to experiment and try different things on your own.  

Another great way to learn is to try to teach.  The primary aim of this series of blog posts is to help others learn and save time by providing a roadmap to follow -- similar to how markers help guide a hiker along a trail.  However through the process of writing, I have recorded a lot of details I would have simply glossed over or forgotten.  By attempting to explain how things worked, it forced me to dive into the material rather than just scratching the surface.


## Hugo Installation

[Hugo][link-1] is built from [Go](https://golang.org), and thus is available as a single binary across multiple platforms (Linux/Mac OS X/Windows).  

It's very simple to install Hugo.  The official Hugo website provides instructions on how to install Hugo for Mac and Windows.  

- `Mac`
https://gohugo.io/tutorials/installing-on-mac/
(Note: I used [homebrew](http://brew.sh) to install Hugo on my Mac.)

- `Windows`
https://gohugo.io/tutorials/installing-on-windows/
(Note: My Windows setup differs slightly as I'm using Git Bash shell for Windows.)


- For `Linux`, you can download a package file or source tarball from [Hugo Github Repo][link-2]
There is also a [tutorial from Digital Ocean](https://www.digitalocean.com/community/tutorials/how-to-install-and-use-hugo-a-static-site-generator-on-ubuntu-14-04) which covers Ubuntu 14.04.

Once downloaded Hugo can be run from anywhere. You don't need to install Hugo into a global location.  There are no dependencies on administrative privileges, databases, runtimes, interpreters or external libraries.

## Pre-requisites

While Hugo is fast and simple to use, there are still a few pre-requisites that are highly recommended to help you use Hugo effectively.

`Markdown`

The core functionality of Hugo is the presentation of your content written in [markdown][link-3].
If you don't already know markdown, you should take a few minutes to become familiar with it before proceeding.  Markdown is very easy to work with.  If you have ever edited pages on a wiki, you may find that markdown syntax is familiar.
Hugo uses a dialect of markdown that is almost the same as [GFM (GitHub Flavored Markdown)][link-4] -- a slight difference is with [code block syntax highlighting][link-5] which is provided either server-side ([Pygments](http://pygments.org)) or client-side (JavaScript).
You can also visit the [Github Flavored Markdown Reference][link-6] to quickly review markdown syntax available to Hugo.
Since version **0.14**, Hugo also allows you to use *external helpers* to author content in other [supported formats][link-7].

Here's a [local blog post][xref-4] which illustrates common text formatting you can do with Github Flavored Markdown.  


`Markdown Editors`

Using your operating system's built-in text editor such as `vi`, `notepad`, or `textedit` to edit Markdown isn't that great.  I recommend using powerful plain-text editors which usually provide syntax highlighting, short cuts, and possibly live preview.  

There are a number of web-based tools that simplifies editing of Markdown files.  Because they are web-based, you don't have to worry about installing an application on your computer.  If you're hosting your project within a Github repository, You can use [Prose.io](http://prose.io/) which interfaces with the Github API.  Another in-browser Markdown editor is [Stack Edit](https://stackedit.io) which allows you to drag and drop the file into the editor itself.  

There are a number of desktop editors for Markdown.  Previously I've used a dedicated Markdown editor [Haroopad](http://pad.haroopress.com), but recently I've switched to [Atom, the Text Editor from Github](https://atom.io).  Atom Editor is an open source, Node.js based application, and is available for Windows/Mac/Linux.  Atom Editor is not just for Markdown files as it supports syntax highlighting for many other types of files (HTML, CSS, python, shell script), and it's easily extended with a vast ecosystem of [plugins](https://atom.io/packages).  I cover Atom Editor in more detail with this [local blog post][xref-5].


`CSS`

CSS is [Cascading Style Sheets](https://en.wikipedia.org/wiki/Cascading_Style_Sheets).  You don't *have* to learn CSS to use Hugo.  However, if you wish to make customizations to your website layout and style, it is imperative to learn at least a bit of CSS.  All modern web design is via CSS (and now also SASS/SCSS).
While a full tutorial of CSS is beyond the scope of setting up a Hugo-generated website, in this series of articles I'll touch upon some CSS basics.



## Hugo is a tool

As with many other static website generators, out of the box Hugo does not automatically make a presentable website.  You need to implement a theme first, or otherwise your site will be really bare-bones.  If you're a web designer, you might be comfortable generating a custom theme yourself. Otherwise, Hugo has an [ecosystem of themes](http://themes.gohugo.io) waiting for you.

If you search the web regarding Hugo, you will find many web articles that give a very elementary introduction to setting up Hugo -- typically with the [Hyde-X theme](http://themes.gohugo.io/hyde-x/).  I found them educational; however for the non-web-designer, it may be a bit much to make the leap from those introductions to a full fledged website.  

For this blog website, I use a [Lanyon-based](http://themes.gohugo.io/lanyon/) theme.  [Lanyon ](http://lanyon.getpoole.com) is a great theme from the Jekyll ecosystem. I'm aiming to get the same look and interactions as the original Lanyon.  

While Hugo is flexible enough to turn almost any static content into a website, the Lanyon theme is focused on blog-like use cases. Lanyon includes a sidebar that is hidden by default, and can be toggled with a button (implemented entirely in CSS). The sidebar gives some convenient navigation links, but when it is hidden it is discreet and places your content front and center.



## Hugo Core Concepts

Hugo is a templating engine to generate static web pages.  It does so by separating your content (Markdown files) from the actual layout of the website.

Hugo references a single directory tree and uses it as the input for creating a complete website.  Within that directory tree you will have sub-directories for content, static files, website templates, and the target location of the generated static website.

### Main "areas" within Hugo:  

- Content
  - All your markdown files - the content of your web site
- Static
  - Your static website files - typically CSS, Javascript, and Image files
- Layouts
  - Your website template files - the layout of your web site
- Public
  - Where Hugo places the generated static website

#### Example directory tree
```
▾ <root>/
    config.yaml
    ▾ content/
        ▾ about/
            me.md
        ▾ posts/
            <blog posts>.md
    ▾ static/
        ▾ css/
            lanyon.css
            poole.css
        ▾ media/
            snowflake.jpg
        favicon.ico
        apple-touch-icon.png
    ▾ layouts/
        ▾ partials/
            <templates to be used in other files>.html
        ▾ posts/
            li.html
            single.html
            summary.html
        ▾ indexes/
            category.html
            indexes.html
            posts.html
            tags.html
        index.html
    README.md
    ▾ public/
        <your statically generated website files and directories>
```
The directory tree tells us a lot about the target website:

  - The website intends to have two different types of content: about and posts.
  - The website uses Lanyon CSS.  (`static/css/lanyon.css`)
  - It will also apply two different indexes to that content: categories and tags.
  - It will be displaying `posts` content in three different views: a list, a summary and a single post view.

The directory structure and templates provide the majority of the configuration for a site.  In fact, a config file (`config.yaml` or `config.toml`) isn't even needed for many websites since the defaults use commonly-used patterns.

### Organization
By default Hugo generates the structure of your website based upon how you organize your content, though this can be overriden.  Hugo treats all directories in content as sections.  The official Hugo documentation on [organization](http://gohugo.io/content/organization/) provides examples and details.  

#### Example - Hugo default generated URLs based upon content organization
```
.
└── content/
    ├── post/
    |   ├── firstpost.md   // <- http://1.com/post/firstpost/
    |   ├── happy/
    |   |   └── ness.md    // <- http://1.com/post/happy/ness/
    |   └── secondpost.md  // <- http://1.com/post/secondpost/
    └── quote/
        ├── first.md       // <- http://1.com/quote/first/
        └── second.md      // <- http://1.com/quote/second/
```

[Permalinks](http://gohugo.io/extras/permalinks) allows you to organize your content anyway you want, and Hugo will override your organization with the specified Permalink pattern. You can have files organized by date in one subdirectory and by subject matter in another subdirectory, but with Permalinks they can all come out using the same organized pattern.

This series of blog posts (and this website) is based upon a simple structure and uses Permalinks to organize by date.  I'll cover the configuration of Permalinks in detail within a later post.

### Front Matter

Markdown files have [front matter](http://gohugo.io/content/front-matter/) defined at the top of every file.  Front matter is just a set of metadata.  The front matter is one of the features that gives Hugo it's strength. It enables you to include the meta data of the content right with it.


Hugo supports [multiple front matter formats](http://gohugo.io/content/front-matter/).  In the following example, we use the [YAML](http://www.yaml.org/) format delineated by three dashes:

{{< highlight yaml >}}
---
title: "This is my title"
date: "2015-12-26"
description: "This is my description."
categories:
    - "Education"
    - "Explanation"
    - "Tutorial"
tags:
    - "Hugo"
---

This is my page.

{{< /highlight >}}

Hugo requires the front matter to have the following variables defined:

- **title** - The title for the content
- **date** -  The date the content will be sorted by

Hugo also has optional front matter which can be defined:

- **description** - The description for the content
- **taxonomies** -  The field name of the plural form of the index (see *tags* and *categories* above).  These will be reviewed in detail in a later post.


## Conclusion

Now that we've installed Hugo, recommended some helpful pre-requisites, described how Hugo needs a theme to effectively generate a presentable website, introduced the Lanyon theme, and touched upon how Hugo expects things to be organized, we're ready to begin using it to generate a blog.  In the [next][xref-3] post I will cover basic Hugo configuration and usage.  


[link-1]: http://gohugo.io
[link-2]: https://github.com/spf13/hugo/releases
[link-3]: http://gohugo.io/content/example/
[link-4]: https://guides.github.com/features/mastering-markdown/
[link-5]: https://gohugo.io/extras/highlighting/
[link-6]: https://help.github.com/articles/github-flavored-markdown/
[link-7]: http://gohugo.io/content/supported-formats
[link-8]: https://gohugo.io/extras/crossreferences/
[link-9]: https://help.github.com/articles/markdown-basics/
[xref-1]: {{< relref "2015-12-20-simple-blog-static-website-generator.md" >}}
[xref-2]: {{< relref "2015-12-21-introduction-static-website-generator.md" >}}
[xref-3]: {{< relref "2015-12-23-basic-config-usage.md" >}}
[xref-4]: {{< relref "2015-12-22-github-flavored-markdown.md" >}}
[xref-5]: {{< relref "2015-12-22-atom-editor.md" >}}
