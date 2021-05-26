# Install a development environment

```
sudo apt install ruby-full build-essentials
sudo gem install bundler
bundle install
```

# Start a development web server

```
bundle exec jekyll serve --host 0.0.0.0
```

# if ufw is enabled then..

```
sudo ufw allow 4000
```

# If I ever need to use plugins that are not allowed by Github...

https://github.com/jeffreytse/jekyll-deploy-action

# How to customize theme

Get path to theme files:

```
bundle info --path just-the-docs
```
