# Installing Ruby and Ruby Gems

MacOs Monterey already has Ruby 2.6 installed, so step 1 is not really necessary

### 1. Get and Install Ruby
```sh
$ brew install ruby
```

Add Ruby´s and Ruby Gems system wide path to /.zprofile

```sh
$ rv=$(/opt/homebrew/opt/ruby/bin/ruby -v | awk -F '[. ]'  '{print $2 "." $3 ".0"}') 
PATH=/opt/homebrew/ruby/bin:$PATH
```


2. Istall bundle and jekyll Gems

We will install the gems as user specific gems. No global rights are necessary.

```sh
$ gem install --user-install bundler jekyll
```

Add the user specific gem path to /.zprofile
```sh
$ rv=$(/opt/homebrew/opt/ruby/bin/ruby -v | awk -F '[. ]'  '{print $2 "." $3 ".0"}') 

# gem path for user install of jekyll (Ruby > 3.0)
$HOME/.local/share/gem/ruby/$rv/bin:$PATH

# gem path for user install of jekyll (Ruby = 2.6)
$HOME/.gem/ruby/$rv/bin:$PATH
```



