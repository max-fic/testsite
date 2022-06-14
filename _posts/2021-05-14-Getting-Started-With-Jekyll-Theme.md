---
layout: default
title: Getting Started with a Jekyll theme
---
### Getting the pool/lanyon theme
```sh
# Initialize the repo
$ mkdir mysite
$ cd mysite
$ git init
$ git remote add origin https://github.com/poole/lanyon.git
$ git pull origin master
```

### Init Bundle
```sh
$ bundle init
```

Edit the gem file add the jekyll-paginate gem
```
# In Gem
gem: "jekyll-paginate"
```

Remove posts in _posts that were shipped with the repo:
```
$ rm _posts/*
```
Add Gemfile.lock to .gitignore


### Edit the configuration file
Edit the `_config.yml` file and set a custom title, tagline and other stuff.
```yaml
# Setup
title:               Maximilian Fichtl
tagline:             'YAPS: Yet another personal site'
description:         'A place where I can put all my personal stuff.'
url:                 https://max-fic.github.io
# baseurl: set only if project is not under root on  production server
baseurl:             ''
paginate:            5
permalink:           pretty

# About/contact
author:
  name:              Maximilian Fichtl
  url:               https://max-fic.github.io
  email:             mfichtl@yahoo.com

markdown: kramdown
```

### Remove absolute links that use site.url
We will sustitute `absolute_url` for `relative_url` in the following files:
```
index.html
_includes/sidebar.html
_includes/head.html
```

The shipped template uses `post.url | absolute_url` which will break in test settings. Better to change to

### Create some content
We will write some blog posts and put them into _posts.

#### Creating a tag page
```html
---
page.title: Blogs by Tag
layout: page
---

{% for tag in site.tags %}
  <h3>{{ tag[0] }}</h3>
  <ul>
    {% for post in tag[1] %}
      <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endfor %}
  </ul>
{% endfor %}
```

### ENabling TeX in Webpage
Put this code into _includes/head.html
```html
<script type="text/javascript" id="MathJax-script" async
  src="https://cdn.jsdelivr.net/npm/mathjax@3/es5/tex-svg.js">
</script>
```