---
title: "Setting up a simple Blog with a Static Website Generator - Part 1: Introduction to Static Website Generators"
date: "2015-12-21"
description: "This is an introduction to Static Website Generators"
categories:
    - "Education"
    - "Explanation"
    - "Tutorial"
tags:
    - "Hugo"
---

This is the first in a [series of blog posts][xref-2] which outline how to setup a simple blog with a static website generator.  

This post provides a general introduction to Static Website Generators and will not cover actual implementation steps.  If you're already familiar with Static Website Generators, or just impatient, you may skip ahead to the [next][xref-1] post.

## What is a Static Website Generator

Rather than reinvent the wheel, I reference a number of excellent articles to give you an overview of **what** is a static website generator, and **why** you will want to use one.  I quote some interesting tidbits from them and occasionally inject my own comments.

I admit -- I'm being lazy here.  However the referenced articles are very well written, and I doubt that I would be able to do as good a job.  I highly recommend you go read the original articles yourself.


http://www.smashingmagazine.com/2015/11/modern-static-website-generators-next-big-thing/

> ### The History of the Web  - When Static Was It

> The first ever website, Tim Berner-Lee's original home page for the World Wide Web, was static.  A website back then was a folder of HTML documents that consisted of just 18 tags.  

> As browsers evolved, so did HTML, and gradually the limitations of purely static websites started to show.

> It also quickly became evident that reserving HTML for structure and CSS for style was not enough of an abstraction to keep the content of a website (the stories, products, gallery items, etc.) separate from the design.

> Around the same time, SQL-based relational databases started going mainstream, and for many online companies, the database became the almost-holy resting place of all of their content.

> [There was] no **content model**, offering no sense of content being separate from design, each half being editable independently with the appropriate tools.

> The most mainstream answer to these problems was the LAMP stack and CMS’ such as WordPress, Drupal and Joomla. All of these played an incredibly important role in moving the web forward, enabling the Web 2.0 phenomenon, in which user-generated content became a driving factor for a lot of websites. Users went from following hyperlinks to ordering products, participating in communities and creating content.

Dynamic websites are complicated environments consisting of multiple technology components with a database backend.  However a major draw back is that if you receive a sudden influx of web traffic, your site may slow to a crawl or worse, crash.  The complexity also opens up larger attack vectors for hackers.

> We pay a huge price for the underlying complexity of dynamic code running on a server for every request — a price we could avoid paying entirely when this kind of complexity is not needed.


> ### The Modern Static Website Generator

Static Website Generators take content, typically stored in flat files rather than databases, apply it against layouts or templates and generate a structure of purely static HTML files that are ready to be delivered to the users.

> The idea of a static website generator is nothing new. Even WordPress’ largest competitor back in the day, Movable Type, had the option of working as a static website generator.

> The rise of Markdown is likely one of the primary reasons why static website generators have become so popular. Few people would dream of writing all of their content in BBCode or pure HTML, whereas Markdown is very pleasant to work with, and Markdown editors for serious writing, note-taking and blogging seem to be exploding in popularity.

> ### Why Now?

> If all of this sounds pretty awesome, that’s because it is. But why is static website technology taking off now, and why did the early generators fail to make a dent in WordPress’ dominance? What’s changed? And how far can we take this?

> Today’s generators play into a totally different ecosystem than their predecessors. Many of the constraints that made dynamic websites the best option for creating anything but the most basic online brochure have fallen away, although some remain.

> The modern browser is an operating system in its own right, no longer merely displaying documents downloaded from the web, but capable of running full-fledged web applications, making external calls to any CORS-compatible API, storing data locally, opening WebSockets to streaming servers, and even handling peer-to-peer connections to other browsers via WebRTC.

> With the maturation of browsers, many features that used to require dynamic code running on a server can be moved entirely to the client. Want comments on your website? Add Disqus, Isso or Facebook comments. Want social integration? Add Twitter or Facebook’s JavaScript widget to your website. Want real-time data updating live on your website? Add a squirt of Firebase. Want search? Add Swiftype. Want to add live chat support? Olark is there. Heck, you can even add an entire store to a static website with Snipcart.


> ### The CDN is going mainstream

CDN is "Content Delivery Network"  -- a distributed network of proxy servers which serve content to end users with high availability and high performance.  Other benefits include offloading traffic from the origin source of the content, as well as more resiliency to DDOS (Distributed Denial of Service) attacks.

> It wasn’t that long ago that CDNs were used only by companies at the scale of CNN and Facebook, rather than mere mortals.

> While Akamai still has enterprise-level pricing, today anyone can sign up for Amazon AWS and put CloudFront on top of their website. Also, companies like Fastly, MaxCDN and CloudFlare offer CDN services at prices that even a small business can afford.

Getting dynamic website caching right on CDNs can be tricky.

> [And] no matter how much you optimize a dynamic website for performance or how many thousand of dollars you throw at it, it will never give you the same basic performance guarantee as a well-tuned static website hosted right on a CDN for a few bucks a month. With performance constantly growing in importance, it’s no wonder that developers are looking for ways to pre-generate their HTML, instead of letting the server spend time and resources on generating a page for every single HTTP request.

> Static website generation also eliminates a lot of performance concerns during the development process.

> ### What's Missing?

> All of these forces have come together to create something like a perfect storm for static website generators, and it’s no wonder that more and more websites are being built statically.

> It’s not all roses, though. Before static websites go fully mainstream, a few areas need to evolve.
Picking a static website generator and starting a project can still be a surprisingly rough experience the first time around. There are a lot of ins and outs and a lot of room for improvement in the tools, documentation and resources available.

> While the ecosystem around static website generators is growing, it’s still a far cry from the mature theme marketplaces and support services of traditional dynamic platforms.

> The biggest missing piece of the puzzle, however, is content editing. While working directly in Markdown in a text editor and pushing to GitHub is close to the ideal workflow for a front-end developer, it’s not something you’d get normal, non-technical end user to participate in.

> Another option for content editing is to work directly on the underlying repository.

There are a number of web-based tools that simplifies editing of Markdown files within a Github repository.  You can use [Prose.io](http://prose.io/) which interfaces with the Github API.  Another in-browser Markdown editor is [Stack Edit](https://stackedit.io) which allows you to drag and drop the file into the editor itself.  

https://davidwalsh.name/introduction-static-site-generators

> Static site generators seem to have been becoming more and more popular recently, but they're not one of those ephemeral novelty things that grow in popularity as quickly as they fall into oblivion shortly after. For over a decade, [many different projects](https://staticsitegenerators.net/) have been maintained by lots of varied people in the community and built with a diverse range of programming languages and technologies.

> I often read on articles about this subject that "static sites are not for everyone", partially due to the lack of a UI to manage content and to the sometimes unfriendly installation process. But actually I think they can be for everyone, just not for everything.

> ### Advantages of static

> #### 1) Speed
> Perhaps the most immediately noticeable characteristic of a static site is how fast it is. As mentioned above, there are no database queries to run, no templating and no processing whatsoever on every request.

> Web servers are really good at delivering static pages quickly, and the entire site consists of static HTML files that are sitting on the server, waiting to be served, so a request is served back to the user pretty much instantly.

> #### 2) Version control for content
> [As opposed to storing in a database], In a static site, the content is typically stored in flat files and treated as any other component of the codebase. In a blog, for example, that means being able to have the actual posts stored in a GitHub repository and allowing your readers to file an issue when something is wrong or to add a correction with a pull request - how cool is that?

> #### 3) Security
> Wherever there's user input/authentication or multiple processes running code on every request, there's a potential security hole to exploit.  Static sites keep it simple, since there's not much to mess up when there's only a web server serving plain HTML pages.

> #### 4) Less hassle with the server
> Installing and maintaining the infrastructure required to run a dynamic site can be quite challenging, especially when multiple servers are involved or when something needs to be migrated.

> #### 5) Traffic surges
> Unexpected traffic peaks on a website can be a problem, especially when it relies intensively on database calls or heavy processing. Introducing caching layers such as Varnish or Memcached surely helps, but that ends up introducing more possible points of failure in the system.  

> A static site is generally better prepared for those situations, as serving static HTML pages consumes a very small amount of server resources.

> ### Disadvantages of static

> #### 1) No real-time content

> There's not really a solution for this, I'm afraid. It's the ultimate price to pay for using a static site, so it's important that you ask yourself the question "how real-time does my site need to be?" — if its concept is based around delivering real-time information then perhaps a static site isn't the right choice.

> #### 2) No user input

> You can't get around this limitation per se and start processing data in your static pages, but you can find alternative solutions for individual cases. If you need to create a contact form, there are a lot of third-party services that will handle POST requests and email you the data, or export it to a format of your choice.

> A commenting system is a slightly different animal though, since it involves not only processing user data but also appending it to a certain page. Platforms like Disqus are often used as a workaround for this and they do the job, but I'm personally not a big fan.

> #### 3) No admin UI

> It's incredibly easy to publish a blog post to WordPress or Medium. It can be done from anywhere, even from a phone, without having to install any additional software. That's not really the case with a static site.

> Typically, posts are composed in a text editor and formatted with a language like Markdown or Textile. To publish them, you'd need to regenerate the site (most engines have a watch functionality to detect file changes and regenerate the site automatically) and deploy the files to a server. It's a bit hard to do all that on a phone sitting on the beach, isn't it?

> ### Conclusions
> Switching to a static site can potentially save you time and money, as it requires less maintenance and less server resources. They're reliable, scalable and can handle high volumes of traffic quite well.

> In 2012, Obama's presidential campaign [raised $250M through a Jekyll website](http://kylerush.net/blog/meet-the-obama-campaigns-250-million-fundraising-platform/). In 2013, Healthcare.gov [switched to a CMS-free approach](https://developmentseed.org/blog/new-healthcare-gov-is-open-and-cms-free/) using Jekyll as well. Static sites are powering huge projects and are definitely not limited to blogging. There's also a strong open source community maintaining and pushing forward a wide range of engines with different flavours and features.

> However, a static site is not some magical solution that will solve all the problems — they're perfect for some cases, but terrible for others. It's vital to understand how they work and what they can do in order to assess, on a per-project basis, whether or not they're the right tool for the job.


## Blogs are a great use case for a Static Website Generator
Blog content is prepared in advance and therefore well-suited to be presented statically.  The drawback of using a static website generator is that you will remove the "dynamic" components of a website which allow users to interact with your website - typically via discussions on blog posts.  However, there are ways to add discussions to a static website.  As mentioned in one of the articles above, you can use Disqus for user comments.  I will go into details on how to add Disqus discussions in a later post.

## Overview of various Static Website Generators
There are [many static website generators](https://staticsitegenerators.net/). It can be difficult to choose which generator to use.  The following website gives an overview of some of the more popular static website generators.  

http://mashable.com/2014/08/28/static-website-generators/

> ### 1. Jekylll - the one that started the resurgence of the current wave of modern static website generators.
>Jekyll is a simple, user friendly static site generator powered by Ruby, and is also the engine behind GitHub Pages.
It takes a template directory containing raw text files, runs it through Markdown (Liquid or Textile) convertors, and generates a complete ready-to-publish static website. It features code highlighting, using Pygment's syntax highlighter, with an automatically organized site structure.

> ### 2. Octopress
> Octopress is a framework designed for Jekyll, a static blogging engine powering GitHub Pages, and makes blogging easy and beautiful, sporting a clean, responsive theme written in semantic HTML5.
Octopress has built-in integration with Twitter, Google Analytics, Google Plus, Pinboard, Disqus Comments and other services. It also includes a preview server for local staging, which will regenerate your site on-the-fly as you make changes.

> ### 3. Docpad
> DocPad is a static website generator built on Node.js and Express.js, that empowers your website with layouts, pre-processors, querying and a robust plugin system.
It comes integrated with an administrator dashboard to make publishing easier. Provided you have the right rendering plugin, you can use any templating engine you prefer, on a document-by-document basis. Since it's modular-based it's incredibly easy to extend, and is able to generate documents dynamically at runtime.

> ### 4. Hugo
> Hugo is a fast, modern static website engine with a high degree of flexibility. It doesn't depend on administrative privileges, databases, runtimes, interpreters or external libraries, and can be installed and run however you wish, and then deployed on Amazon S3, GitHub Pages, Dropbox or any web host you choose.

> Hugo was written for speed and performance, and allows you to organize your content however you want with any URL structure. You can declare your own content types, define your own metadata and use indexes to group your content. You can write content in Markdown, render changes on the fly as you develop, with support for Disqus Comments, dynamic menu creation, pretty urls, syntax highlighting and more.

> ### 5. Wintersmith
> Wintersmith is a flexible, minimalistic, multi-platform static site generator built on top of Node.js.
It puts absolutely no limits on how you work with your content, and you can transform it with plugins and structure it as you please. Wintersmith comes bundled with a Jade plugin, with community-made plugins available, and you can use your favorite templating engine. Deployment is simple, and there's no need for special hosting solutions and the performance is blazing fast as there are no database calls, no server-side API calls or any CPU/RAM overhead.

> ### 6. Middleman
> Middleman is a command-line tool for creating static websites, with Ruby and the Sinatra web framework forming the base of the tool. With Middleman you have standalone developer access to ERb, Haml, Sass for DRY stylesheets, CoffeeScript for safer, less verbose Javascript and multiple asset management solutions, including Sprockets.

> ### 7. Nanoc
> Nanoc is a static site generator written in Ruby that's ideal for building any type of web project, from personal blogs to large corporate websites.
As it's a command line application, you develop sites locally, with the generated site deployed when finished. Nanoc is extremely flexible, letting you choose your favorite templating languages, extensions and Ruby gems.

> ### 8. Metalsmith
> Metalsmith is an extremely simple static site generator, with all the logic handled by plugins, so you can simply chain them together. It works by reading all the files in your source directory, with the plugins then manipulating the files, with the results then written to the destination directory.

> ### 9. Hexo
> Hexo is a simple, powerful blog framework, which parses your posts with Markdown (or any other render engine you choose), and generates static files. It's powered by Node.js, and features multithread generating, so hundreds of files take just seconds to generate.
Hexo also supports GitHub-flavored Markdown, Octopress plugins, Jekyll, EJS, Swig and Stylus. There are nearly 40 themes to choose from, including Bootstrap and iOS-inspired options, through to a theme that generates 301 redirection pages for site migration.

> ### 10. Harp
> Harp is a static web server with built-in preprocessing, and serves Jade, Markdown, EJS, CoffeeScript, Sass, Less and Stylus as HTML, CSS and JavaScript, with no configuration necessary.

> ### 11. Cactus
> Cactus is a static website generator using Python and Django, which makes it easy to develop locally and deploy your site directly to Amazon S3. It’s easy to use, is fully extensible, and works great for any project application, including portfolios and blogs, with support for spiriting, versioning.

> ### 12. Pelican
> Pelican is a static site generator powered by Python, that requires no database or sever-side logic. You can write your own content in reStructuredText, Markdown, or AsciiDoc formats and also publish in multiple languages.

> ### 13. Sculpin
> Sculpin is a static site generator written in PHP, which converts Markdown files, Twig templates or standard HTML into a static site that can easily be deployed. With the embedded composer you can keep your source control focused and consistent.

## Conclusion
This first post provided an overview of what is and why you should use a static website generator.  It also referenced a list of some of the more popular static website generators.

In the [next][xref-1] post I'll outline some reasons why [Hugo][link-1] is my tool of choice.  I will cover installation of Hugo and some pre-requisites that will help you use Hugo effectively.  I will also describe how Hugo needs a theme to effectively generate a presentable website, and I will introduce the Lanyon theme.  

## Additional Reading

- http://www.smashingmagazine.com/2015/11/static-website-generators-jekyll-middleman-roots-hugo-review/
- http://konigi.com/blog/hello-hugo/
- http://usersnap.com/blog/hands-on-experience-with-hugo-static-site-generator/
- http://anthonyfok.org/post/getting-started-with-hugo/

[link-1]: http://gohugo.io
[xref-1]: {{< relref "2015-12-22-installing-hugo.md" >}}
[xref-2]: {{< relref "2015-12-20-simple-blog-static-website-generator.md" >}}
