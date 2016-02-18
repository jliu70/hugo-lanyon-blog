---
title: "Setting up a simple Blog with a Static Website Generator - Part 8: Hugo Code Block Syntax Highlighting with Pygments"
date: "2015-12-31"
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

## Adding Pygments {#pygments}

The Hugo executable has one *optional* external dependency for source code highlighting (Pygments).  If you want to have source code highlighting using the [highlighting shortcode](https://gohugo.io/extras/highlighting/), you will need to install the Python-based [Pygments](http://pygments.org) program.


https://gohugo.io/extras/highlighting/

- Install Python from python.org.  Version 2.7.x is sufficient
- Run `pip install Pygments` in order to install Pygments.  Once installed, Pygments gives you a command `pygmentize`.  Make sure it sits in your PATH, otherwise Hugo can not find it.

Hugo gives you two options,
pygmentsuseclasses = false (default)

pygmentsstyle (default "monokai")


http://pygments.org/docs/styles/

{{< highlight python >}}
Microsoft Windows [Version 6.1.7601]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

C:\Users\jeffrey.liu>python
Python 3.4.0 (v3.4.0:04f714765c13, Mar 16 2014, 19:25:23) [MSC v.1600 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> from pygments.styles import STYLE_MAP
>>> STYLE_MAP.keys()
dict_keys(['native', 'pastie', 'trac', 'monokai', 'fruity', 'manni', 'tango', 'perldoc', 'borland', 'bw', 'friendly', 'colorful', 'vim', 'vs', 'murphy', 'rrt',
'emacs', 'default', 'autumn'])
>>>
{{< /highlight >}}

## NOTE: http://pygments.org  - seems like pygments uses static/css/syntax.css if you choose option `pygmentsuseclasses = true`   - wonder if it handles unknown syntax or missing pygmentize better with classes use

### 1/20/2016 So, apparently pygments was already installed on the Windows laptop, so it just worked.  

### 1/20/2016 Installed on Mac
```
jeffrey-lius-imac:git jliu$ sudo easy_install pip
Password:
Searching for pip
Reading https://pypi.python.org/simple/pip/
Best match: pip 8.0.0
Downloading https://pypi.python.org/packages/source/p/pip/pip-8.0.0.tar.gz#md5=5601c4323464add1482291634142894d
Processing pip-8.0.0.tar.gz
Writing /tmp/easy_install-lFmLfr/pip-8.0.0/setup.cfg
Running pip-8.0.0/setup.py -q bdist_egg --dist-dir /tmp/easy_install-lFmLfr/pip-8.0.0/egg-dist-tmp-YMAvQl
warning: no previously-included files found matching '.coveragerc'
warning: no previously-included files found matching '.mailmap'
warning: no previously-included files found matching '.travis.yml'
warning: no previously-included files found matching '.landscape.yml'
warning: no previously-included files found matching 'pip/_vendor/Makefile'
warning: no previously-included files found matching 'tox.ini'
warning: no previously-included files found matching 'dev-requirements.txt'
warning: no previously-included files found matching 'appveyor.yml'
no previously-included directories found matching '.travis'
no previously-included directories found matching 'docs/_build'
no previously-included directories found matching 'contrib'
no previously-included directories found matching 'tasks'
no previously-included directories found matching 'tests'
Adding pip 8.0.0 to easy-install.pth file
Installing pip script to /usr/local/bin
Installing pip2.7 script to /usr/local/bin
Installing pip2 script to /usr/local/bin


Installed /Library/Python/2.7/site-packages/pip-8.0.0-py2.7.egg
Processing dependencies for pip
Finished processing dependencies for pip

jeffrey-lius-imac:git jliu$ sudo pip install pygments
The directory '/Users/jliu/Library/Caches/pip/http' or its parent directory is not owned by the current user and the cache has been disabled. Please check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
The directory '/Users/jliu/Library/Caches/pip' or its parent directory is not owned by the current user and caching wheels has been disabled. check the permissions and owner of that directory. If executing pip with sudo, you may want sudo's -H flag.
Collecting pygments
  Downloading Pygments-2.1-py2-none-any.whl (754kB)
    100% |████████████████████████████████| 757kB 750kB/s
Installing collected packages: pygments
Successfully installed pygments-2.1


jeffrey-lius-imac:git jliu$ which pygmentize
/usr/local/bin/pygmentize
```


## maybe try a different style? specify `pygmentsstyle: "tango"` within `config.yaml`  Tango may be bland, but good with default poole.css.   Otherwise, stick to "monokai" default with updated mystyles.css

Updated mystyles.css  to modify background color so that highlighted code is more "visible" as default poole.css theme has a light background color.  Reference: https://discuss.gohugo.io/t/pygments-howto/405/6

{{< highlight css >}}

.highlight pre{
  background-color: #424242;
}

{{< /highlight >}}
