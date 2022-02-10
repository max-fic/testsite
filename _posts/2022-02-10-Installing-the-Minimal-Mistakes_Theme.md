---
---

Steps necessary to install the theme `minimla-mistakes` as a gem based theme.


Go to the site directory

```
$ cd testsite
```

Edit the Gemfile to include the theme gem and to include the  jekyll-include-cache plugin by adding the lines

```
gem "minimal-mistakes-jekyll"
gem "jekyll-include-cache, group: :jekyll_plugins" 
```

and changing

```
gem "minima", "~> 2.5"
```

to

```
# gem "minima", "~> 2.5"
```


Now run bundle 

Finally edit the  _config.yml file

```
theme: minimal-mistakes-jekyll
plugins: ... jekyll-include-cache
repository: <username>/repo # if used with Github Pages gem
```

If the site is being used with the github pages gem, you should get a personal access key for 
github as described [in this post.](https://knightcodes.com/miscellaneous/2016/09/13/fix-github-metadata-error.html)
