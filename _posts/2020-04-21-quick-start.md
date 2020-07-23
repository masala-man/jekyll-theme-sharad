---
layout: coverpost
title: "Quick Start Guide"
date: 2020-04-21
author: Ayush Shenoy
tags: jekyll
cover: jpg
---

Sharad is a fast, beautiful and responsive theme for your jekyll sites.
<!--more-->

# Features

- Responsive and usable across devices
- Full jekyll markdown support
- Lightweight and fast
- Easy configuration
- Included rakefile

### Screenshots

There are two layouts to choose from for posts and one default layout.

**1.coverpost**
![](/assets/img/coverpost.png)  
<br>

**2. plainpost**
![](/assets/img/plainpost.png)  
<br>

**3. default**
![](/assets/img/default.png)
<br>

**4. list of posts**
![](/assets/img/posts.png)

### Front Matter

Here's the front matter for this post

- `layout: coverpost`
- `title: "Quick Start Guide"`
- `date: 2020-04-21`
- `author: Ayush Shenoy`
- `tags: jekyll`
- `cover: /assets/img/red.jpg`

### Captions

If you want to have images with captions, all you have to do is use standard markdown syntax immediately followed by a the caption in italics

```md
![](image_url)
*caption*
```

### Excerpts

A excerpt from the page is shown in the list of posts under each post's title. This is usually the first paragraph of the post. If you want to specify it manually, add a `<!--more-->` tag to mark the end of the page's excerpt.

### Rakefile

A rakefile is included for easy creation of posts and serving previews. See rakefile comments for more information.   
Commands:  
- `rake post` - Create a new post
- `rake clean` - Delete generated site
- `rake preview` - Start a live preview

# Installation

`git clone https://www.github.com/masala-man/jekyll-theme-sharad`  
`bundle install`  
`jekyll serve`  <br><br>

# License

The MIT License (MIT)

Copyright (c) 2020 Ayush Shenoy

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
