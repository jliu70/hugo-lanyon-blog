---
title: "Github Flavored Markdown"
date: "2015-12-22"
description: "This post shows examples of Github Flavored Markdown syntax"
categories:
    - "Explanation"
tags:
    - "Markdown"
---

This post illustrates the syntax of the most common uses of Github Flavored Markdown.

### Additional Resources

The [Github Mastering Markdown Guide][link-1] provides a great introduction to Markdown.

[Github Markdown Basics][link-2]

[Github Flavored Markdown Reference][link-3]


## Headings
```
# Header 1
## Header 2
### Header 3
#### Header 4
##### Header 5
###### Header 6
```
# Header 1
## Header 2
### Header 3
#### Header 4
##### Header 5
###### Header 6



## Styling Text

```
*this is in italic*  and _so is this_

**this is in bold**  and __so is this__

***this is bold and italic***  and ___so is this___


<s>this is strike through text</s> and so is this ~~Mistaken text.~~
```

*this is in italic*  and _so is this_

**this is in bold**  and __so is this__

***this is bold and italic***  and ___so is this___


<s>this is strike through text</s> and so is this ~~Mistaken text.~~


## Lists

```
* an asterisk starts an unordered list
* and this is another item in the list
+ or you can also use the + character
- or the - character
```

* an asterisk starts an unordered list
* and this is another item in the list
+ or you can also use the + character
- or the - character

> NOTE: the CSS implemented with your website could alter the appearance of lists.  For example, by default the [Lanyon](http://themes.gohugo.io/lanyon/) theme does not decorate lists with bullets.  You will need to override `list-style-type: none;` within `poole.css` which is used with `lanyon.css`.  I cover details on how to do that in the example project [Lanyon CSS]({{< relref "2015-12-25-lanyon-css.md#lists" >}}) post.


## Tables

```
    First Header   | Second Header
    -------------  | -------------
    *Content Cell* | Content Cell
    Content Cell   | **Content Cell**

```


First Header   | Second Header
-------------  | -------------
*Content Cell* | Content Cell
Content Cell   | **Content Cell**



## Block Quotes
```
> Block quote content
```

> Block quote content



## Inline Code formatting
```
Here is an `inline code` text.
```

Here is an `inline code` text.

## Multiple Lines Code formatting

You can use triple backticks  (```)  to format text as its own distinct block.

```
Code Block
  if
  then
  else
```

[link-1]: https://guides.github.com/features/mastering-markdown/
[link-2]: https://help.github.com/articles/markdown-basics/
[link-3]: https://help.github.com/articles/github-flavored-markdown/
[link-5]: https://gohugo.io/extras/highlighting/
