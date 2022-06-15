`---
---

It is assumed that you already have installed the `bundle` and `jekyll` gems..

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

For Ruby > 3.0 we have to add the gem `webrick`

```sh
$ bundle add webrick
```

We have to add the follwing line to the `Gemfile`.

```
gem "webrick"
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



### Setting up from a pull of directory

```sh
$ cd <new dir>
$ git init
$ git branch -M main
$ git remote add github https://github.com/max-fic/testsite.git
$ git pull github main
$ bundle config set --local path 'vendor/bundle'
$ bundle install
$ bundle add jekyll webrick