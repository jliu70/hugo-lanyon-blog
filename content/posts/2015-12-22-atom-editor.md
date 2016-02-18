---
title: "Atom the Text Editor from Github"
date: "2015-12-22"
description: "This post gives an overview of Github Atom Editor"
categories:
    - "Review"
tags:
    - "Tools"
---


Using your operating system's built-in text editor such as `vi`, `notepad`, or `textedit` to edit Markdown isn't that great.

[Atom, the Text Editor from Github][link-1] is an open source, Node.js based application, and is available for Windows/Mac/Linux.  Atom provides syntax highlighting, short cuts, and markdown live preview.  Atom Editor is not just for Markdown files as it supports syntax highlighting for many other types of files (HTML, CSS, python, shell script), and it's easily extended with a vast ecosystem of [packages](https://atom.io/packages).


Rather than reinvent the wheel, I reference a number of excellent articles and quote some interesting tidbits from them and occasionally inject my own comments.

I admit -- I'm being lazy here.  The referenced articles are very well written, and I doubt that I would be able to do as good a job.  I highly recommend you go read the original articles yourself.

http://blogs.msdn.com/b/silverlining/archive/2015/05/18/atom-io-for-markdown-editing.aspx

> ### Markdown support

> Out of the box, Atom has pretty good support for Markdown. It has syntax highlighting and rendered preview functionality right out of the box, along with support for things like [GitHub flavored Markdown](https://guides.github.com/features/mastering-markdown/). However, if you are coming from a dedicated Markdown editor such as Markdown Pad you may miss features like a preview that scrolls in sync with the Markdown view.

> Fortunately, Atom has a variety of community generated packages that can be installed to provide additional functionality. Here are the ones I recommend:

> [Markdown-Writer](https://atom.io/packages/markdown-writer): Adds a bunch of keyboard commands for things like text formatting and creating links & images, along with support for popular static site blogging platforms.

> [Markdown-Scroll-Sync](https://atom.io/packages/markdown-scroll-sync): Makes the rendered preview scroll in sync with the Markdown view.

> [Markdown-Format](https://atom.io/packages/markdown-format): Makes your Markdown pretty when you save. Things like renumbering lists so they are actually in order (vs. the 1, 2, 3, 5, 5, 5, 8, 9 I always seem to end up with,) and padding cells in GitHub Flavored Markdown tables so they are more readable.

> There's more than this, so I'll leave it to you to explore the other Markdown related packages.

> ### Installing packages

> Once you've installed Atom.io, to install these or any other packages, perform the following steps:

> - From the **File** menu, select **Settings**, then **Install**. Enter the name of the package you wish to install (or part of the name, such as **Markdown** to see all packages that contain that word.)

> - Click the **Install** button beside the package. If you want to read more about the package before installing, click the title of the package and it will open your browser and display more information.

While the quoted article refers many excellent Markdown Atom packages, I did not install any.  With Hugo's [built-in high-performance web server][xref-1], I don't really have a need for a Markdown preview which scrolls in sync.   As for the other features, I haven't really tried them out, as I haven't really needed them.  Don't let that stop you from trying out different packages.  

> ### Tips

> - To toggle the Markdown preview, use ctrl-shift-m.

> - If you've opened Atom to a specific folder, and it's showing the tree view side bar, you can dismiss it with `ctrl-\` on `Windows/Linux` (or `command-\` on `Mac`).

> - Atom.io checks for package updates automatically. If you see a blue box in the lower right-hand corner, that means some packages have been updated. Click on the blue box to install them.

> - If you're working in a folder that contains a lot of Markdown files, don't even try using the tree view. It's 100x easier to use `ctrl-t` on `Windows/Linux` (or `command-t` on `Mac`) and then start typing the file name you want to open. This will search through the directory structure for files that match the text you've entered, and you can then click the one you want.

> - If you need to change the indentation for a section of text (for example, a section of source code,) just select it and hit `ctrl-[ or ]` on `Windows/Linux` (or `command-[ or ]` on `Mac`) to change the indent level.


http://readwrite.com/2014/05/20/github-atom-5-tips-getting-started-tutorial-corey-johnson

> ### How To Install A Package

> The toughest part about developing Atom, according to Johnson, was making sure each user could select the right amount of tools for her needs. Some people will want tools to parse HTML; others will want Python debuggers. But if Atom came with all of these already installed, it’d be huge, unwieldy, and full of features that are useful to some and useless to others.

> So instead, Atom uses “packages,” mini-plugins that you can install to add new features to your workspace. And since Atom is coded in JavaScript, anybody that already knows JavaScript can build a package that meets their exact specifications.  

> “The cool thing about Atom is it’s hackable,” Johnson said. “We left out a feature people wanted, and already three developers built packages to fill the gap.”

> Hit command + , (the command key and the comma key) to open up Settings. Suddenly, your editing screen will be eclipsed by a GUI. On the side, you’ll see a list of options, followed by the packages you already have installed.

> In order to add new packages, simply click “packages” on the left. You can search for a specific package, or install one of the ones Atom has featured.

> ### How To Use A Package

> Once you’ve installed any package, either click on the “Settings” button right below its name, or click the package itself in the left-hand column. This will take you to a list of keystrokes you can use to summon that package’s features.

> This is Color Picker, a package that adds a GUI to color hex code selection. It only has one keystroke—command + shift + c—in order to activate its abilities.

> I’ll go over to some CSS I’m editing, put my cursor on the body text, and hit that keystroke. Voila! A GUI pops up to help me visually gauge the right color for my project.

> ## How To Remember Shortcuts

> “Wait a minute, what does it do again if I press the command key and the comma key?” There are two basic ways to figure out essentially every keystroke.

> First, there’s command + . (the command key and the period key pressed together). Press this and a window will pop up at the bottom of your screen. As long as it’s up, hit any keystroke you like and it’ll tell you what that keystroke does. (To make it go away, hit command + . again.)

> There’s also command + shift + p, which brings up a scrolling list of every possible thing you can do in Atom with your current package configuration. For example, if I forgot how to split window panes, I can press command + shift + p and then write “split” in order to find the solution—which is to hit command + k and then an arrow key.  



### Additional Resources
Atom Blog: http://blog.atom.io/

Some cool packages to extend Atom
http://www.sitepoint.com/10-essential-atom-add-ons/

Long list of recommended packags to extend Atom
http://elijahmanor.com/github-atom-packages/

Plugins for markdown editing
http://tedcurran.net/2015/05/12/make-your-perfect-markdown-editor-with-atom-editor-plugins/

[link-1]:https://atom.io/
[xref-1]: {{< relref "2015-12-23-basic-config-usage.md#Usage" >}}
