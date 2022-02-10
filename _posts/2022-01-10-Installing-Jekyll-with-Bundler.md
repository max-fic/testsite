---
---

It is assumed that you already have installed `bundler`.

### Common Installation

First we create the directory that will hold the site's structure

```
$ mkdir testsite
$ cd testsite
```

Next we instruct `bundle` to use a local version of its configuration
 (register of dependecies) in ./vendor/bundle so we can keep configurations separate in case we have various sites.

```
$ bundle init
$ bundle config set --local path 'vendor/bundle'
$ bundle install
```


Next we install the jekyll gem (and its dependencies)

```
$ bundle add jekyll
```

Finally we create an empty jekyll structure

```
$ bundle exec jekyll new --force -skip-bundle .
$ bundle install
```

Now we have a directory prepared to receive posts and pages for the website.

### Optional Steps For Use with Git

Optionally (if we use git source control) we should add
`.bundle` and `vendor/bundle` to the `.gitignore` file.

### Optional Steps for Use with Github Pages

Optionally, if we want to use the site with Github Pages, we have to edit the 
`Gemfile`. 

Change the line

```gem jekyll, "~> 4.2.1"```

to

```# gem jekyll, "~> 4.2.1"```


Change the line

```# gem "github-pages", group: :jekyll_pluginsa```

to

```gem "github-pages", group: :jekyll_pluginsa```

and finally change 

```
gem jekyll-feed, "~> 0.12"
```

to

```
gem jekyll-feed
```

Finally we have to run

```
$ bundle install github-pages
$ bundle update
```


