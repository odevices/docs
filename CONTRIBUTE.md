---
layout: default
title: How to Contribute
nav_order: 9998
---

## Install a development environment

```bash
sudo apt install ruby-full build-essentials
sudo gem install bundler
bundle install
```

## Start a development web server

```bash
bundle exec jekyll serve --host 0.0.0.0
```

## if ufw is enabled then..

```bash
sudo ufw allow 4000
```

## If I ever need to use plugins that are not allowed by Github...

https://github.com/jeffreytse/jekyll-deploy-action

## How to customize theme

Get path to theme files:

```bash
bundle info --path just-the-docs
```
