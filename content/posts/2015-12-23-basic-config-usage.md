---
title: "Setting up a simple Blog with a Static Website Generator - Part 3: Quickstart - Basic Configuration and Usage"
date: "2015-12-23"
description: "This is an introduction to Hugo"
categories:
    - "Education"
    - "Explanation"
    - "Tutorial"
tags:
    - "Hugo"
---

This is part 3 in a [series of blog posts][xref-1] which outline how to setup a simple blog with a static website generator.

The [previous][xref-2] post provided some reasons why [Hugo][link-1] is my tool of choice.  I covered installation of Hugo and some pre-requisites that should help you use Hugo effectively.  I also described how Hugo needs a theme to effectively generate a presentable website, and I introduced the Lanyon theme.  Lastly, we touched upon how Hugo expects things to be organized.

Now that we have Hugo installed, let's walk through basic configuration and usage for this example blog site.  

The intent of this post is to cover the minimal number of steps to get you quickly up and running.  There are many details ommitted here.  I'll be covering select topics in greater detail in later posts.

If you're only interested in quickly launching a blog web site without making any customizations or getting into details, then follow the steps outlined in this post.

## Obtaining the Example Website
The [source code for this blog][link-2] is on [GitHub][link-3]. Readers are encouraged to download the example repository and follow along.

> If you are not familiar with Git and Github, you may download a zip file of the project directory tree.  The zip file does not download the Git repo; it only contains the example website project files.


> Click on the "Download ZIP" button to download a zip file of the example website.

{{% img src="/media/screen_shot-download_zip.png" class="third right" alt="zip download" %}}

###### In the above screen shot, the "Download ZIP" button is circled in red.

> After you download the zip file, extract the contents to begin work on the example website.




## Configuration

The very first step in creating a new Hugo site is to write [the config file][link-4]. This config file is important for at least two reasons: (1) this is where site-wide settings go (e.g., the website baseurl variable `.Site.BaseURL`), and (2) the config file dictates to some extent how Hugo will generate the website.

The example website config file `config.yaml` has the following contents:

```
---
baseurl: "http://example.com"
canonifyurls: false
title: "Hugo Blog Example"
contentdir: "content"
layoutdir: "layouts"
publishdir: "public"
indexes:
  category: "categories"
  tag: "tags"
permalinks:
  posts: "/:year/:month/:day/:title/"
  about: "/:section/"
languageCode: "en-us"
author:
  name: "Jeffrey Liu"
copyright: "2015-16"
params:
  mymasthead: "Example Blog"
DisqusShortname: "yourDisqusShortname"
GoogleAnalytics: "UA-XXXXXXX-1"

```

### The first important setting: `baseurl`

One of the first things you need to do is to set the `baseurl` configuration parameter.   You can set `baseurl` to whatever you want, but your choice will affect the setting for `canonifyurls`.

> #### Note on `canonifyurls` and how it relates to your `baseurl`
> The default Hugo value for `canonifyurls` is false.

> If your website `baseurl` will be a domain, e.g. `http://blog.example.com`, `http://www.example.com` or `http://example.com` then you can keep the default for `canonifyurls` (since v0.11 default value: false).

> If your website will be a subdirectory, e.g. `http://www.example.com/blog` or `http://example.com/blog` then make sure to add `canonifyurls: true` to your `config.yaml`, or you will run into problems (in particular one important issue: the CSS files will not load because they will need to be referenced with a *canonlicalized* path --  example: instead of just `/css/lanyon.css`, it will be with your baseURL `http://example.com/blog/css/lanyon.css`.)

> See [“Canonicalization” on the “Extras: URLs page”][link-5] for more information.

### Other settings
Within the config file `config.yaml`, you should also update the variables for `title`, `name`, `mymasthead` to your own values.


## Define Structure of Website

Hugo assumes that you organize the content of your site in a meaningful way and uses the same structure to render the website. Notice that within the config file we have the line `contentdir: "content"`. This means that all the actual content of the website should be placed somewhere within a folder named content. Hugo treats all directories in content as sections. For the example blog website we primarily use only one section: a place to hold our blog posts.

```
▾ <root>/
    ▾ content/
        ▾ posts/
```

## Create HTML Templates

The next step is to define the look and feel of your new website. Because Hugo will generate the site using HTML templates written by the user (you), this step is very subjective. The example project uses a variation of a Jekyll theme called Lanyon. The Lanyon theme is pure CSS and resides in the `/static/css` directory of the example repository.

Because there are so many files needed to fully compose a complete website, I will not go through each of them here. I will, however, display the example project directory structure:

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

Many of the files in the example project are well commented with a description of what the file as a whole does as well as an explanation of all major components in the file. If you are new to web development and/or Hugo, I encourage you to peruse through these files to get a feel for how Hugo templates work and how the site is stitched together.

In later posts, I will cover in detail some of the HTML templates and how the layout works.  We'll skip the details for now since we are only focusing on getting up and running quickly.


## Add Some Content

The next step in creating the blog is to add some actual blog posts. To do this, simply create one Markdown file (with extension .md) for each new blog post. At the top of each file you should include a front-matter metadata section that tells Hugo some things about the post. For example, consider the yaml front-matter metadata section from the top of the file `/content/posts/2015-12-15-a-test-post.md` from the example project:

```
---
title: "First sample post"
date: "2015-12-15"
description: "This should be a more useful description"
categories:
    - "Explanation"
    - "Tutorial"
    - "test"
tags:
    - "fun"
---
```

The `title` and `date` keys are mandatory.  The `description`, `categories` and `tags` keys are optional. Each of these items is used throughout the templates found in the layouts directory and gives Hugo information about the post from other pages in the website.

The rest of the file is the content of your blog post written in Markdown.  This content will be generated into HTML and presented as the actual blog post.    


## Usage {#Usage}

### Hugo server mode - Viewing your website locally before publishing it.

Hugo contains its own high-performance web server.  Simply run `hugo server` and Hugo will find an available port and run a server with your content.  The default port is `1313`.  

After running `hugo server` browse to the URL http://localhost:1313 to see your web site.

As of version **v0.15** `hugo server` by default will not generate HTML files to your publish directory; Hugo will serve your content out from memory.  

From the root folder of your project, run:
```
hugo server
```

You should see the following output:
```
$ hugo server
0 draft content
0 future content
14 pages created
0 paginator pages created
5 categories created
6 tags created
in 55 ms
Watching for changes in /path/to/rootProjectFolder/{content,layouts,static}
Serving pages from memory
Web Server is available at http://localhost:1313/ (bind address 127.0.0.1)
Press Ctrl+C to stop
```

Not only can Hugo run a server, but it can also watch your files for changes and automatically rebuild your site. Hugo will then communicate with your browser and automatically reload any open page. This even works in mobile browsers.

If you make edits/changes to your files while `hugo server` is running, then your website will automatically update.  This is the ultimate "live preview" functionality.

### Hugo - generate HTML so that you can publish your website

When you wish to publish your blog, you will simply run `hugo` and it will generate all the files needed for the web site.  You should see output similar to the following:

```
$ hugo
0 draft content
0 future content
13 pages created
0 paginator pages created
6 tags created
5 categories created
in 75 ms

```

Hugo will place all the generated files in your publish directory.  The example project publish directory is `/path/to/root/public`.  

The following shows the directory structure of the example project after a Hugo generation.  The content is organized by date derived from the `permalinks` parameter within the config file.  There is also HTML generated for the Taxonomies `categories` and `tags`.  

```
public/
├── 2015
│   └── 12
│       ├── 15
│       │   └── first-sample-post
│       │       └── index.html
│       ├── 20
│       │   └── setting-up-a-simple-blog-with-a-static-website-generator---preface
│       │       └── index.html
│       ├── 21
│       │   └── setting-up-a-simple-blog-with-a-static-website-generator---part-1-introduction-to-static-website-generators
│       │       └── index.html
│       ├── 22
│       │   ├── atom-the-text-editor-from-github
│       │   │   └── index.html
│       │   ├── github-flavored-markdown
│       │   │   └── index.html
│       │   └── setting-up-a-simple-blog-with-a-static-website-generator---part-2-installing-hugo
│       │       └── index.html
│       ├── 23
│       │   └── setting-up-a-simple-blog-with-a-static-website-generator---part-3-basic-configuration-and-usage
│       │       └── index.html
│       ├── 24
│       │   └── setting-up-a-simple-blog-with-a-static-website-generator---part-4-hugo-configuration-details---simple
│       │       └── index.html
│       ├── 25
│       │   └── setting-up-a-simple-blog-with-a-static-website-generator---part-5-lanyon-css
│       │       └── index.html
│       ├── 26
│       │   └── setting-up-a-simple-blog-with-a-static-website-generator---part-6-hugo-layouts
│       │       └── index.html
│       └── 27
│           └── setting-up-a-simple-blog-with-a-static-website-generator---part-7-hugo-advanced-usage-troubleshooting-and-debugging
│               └── index.html
├── 404.html
├── about
│   ├── index.html
│   └── index.xml
├── apple-touch-icon.png
├── categories
│   ├── education
│   │   ├── index.html
│   │   └── index.xml
│   ├── explanation
│   │   ├── index.html
│   │   └── index.xml
│   ├── index.html
│   ├── review
│   │   ├── index.html
│   │   └── index.xml
│   ├── test
│   │   ├── index.html
│   │   └── index.xml
│   └── tutorial
│       ├── index.html
│       └── index.xml
├── css
│   ├── lanyon.css
│   ├── mystyles.css
│   ├── mystyles.css.wide
│   └── poole.css
├── favicon.ico
├── index.html
├── index.xml
├── media
│   ├── screen_shot-download_zip.png
│   ├── snowflake-wide.jpg
│   └── snowflake.jpg
├── posts
│   ├── index.html
│   └── index.xml
├── sitemap.xml
└── tags
    ├── css
    │   ├── index.html
    │   └── index.xml
    ├── fun
    │   ├── index.html
    │   └── index.xml
    ├── html
    │   ├── index.html
    │   └── index.xml
    ├── hugo
    │   ├── index.html
    │   └── index.xml
    ├── index.html
    ├── markdown
    │   ├── index.html
    │   └── index.xml
    └── tools
        ├── index.html
        └── index.xml
```


### Publishing your website

Now, all you need to do is to upload the `public` directory tree to your web host.

Here are a some popular options.  

#### GitHub Pages
[GitHub Pages][link-6] is a great way to have a website hosted directly from your GitHub repository.  [GitHub pricing][link-7] offers a free tier (no private repositories - public repos only), and is a very inexpensive way to host your blog site.  Read this [local blog post][xref-4] to learn more about GitHub Pages.


#### Amazon S3 Static website hosting
Amazon Web Services (AWS) offers static website hosting within their Simple Storage Service (S3).  With AWS you are able to scale to support enterprise-level traffic.  It is not free, but costs are nominal.  You will need to pay for storage, and associated traffic to your website.  AWS provides a [calculator][link-8] to estimate your costs.

Amazon provides a great [tutorial][link-9] on hosting a static website on AWS.  The tutorial is very complete, and walks you through step-by-step on everything you need to setup a robust website.  

This [local blog post][xref-5] covers the basics of setting up for Amazon Web Services.



## Conclusion

In this post we covered basic configuration and usage of Hugo with the example project blog website.  Many details were skipped because the goal was to get up and running quickly.

In other posts, I will go into some of the details on how the Hugo configuration, CSS, and layouts work together to make a simple blog site.  With understanding of the details, you will be able to make your own customizations to the look and feel of your website.



[link-1]: http://gohugo.io
[link-2]: https://github.com/jliu70/hugo-lanyon-blog
[link-3]: https://github.com
[link-4]: https://gohugo.io/overview/configuration/
[link-5]: https://gohugo.io/extras/urls/
[link-6]: https://pages.github.com
[link-7]: https://github.com/pricing
[link-8]: https://calculator.s3.amazonaws.com/index.html
[link-9]: http://docs.aws.amazon.com/gettingstarted/latest/swh/website-hosting-intro.html
[xref-1]: {{< relref "2015-12-20-simple-blog-static-website-generator.md" >}}
[xref-2]: {{< relref "2015-12-22-installing-hugo.md" >}}
[xref-3]: {{< relref "2015-12-23-basic-config-usage.md" >}}
[xref-4]: {{< relref "2016-01-03-github-pages.md" >}}
[xref-5]: {{< relref "2016-01-04-amazon-web-services.md" >}}
