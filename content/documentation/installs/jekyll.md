---
title: Jekyll
toc: true
type: book
date: "2019-12-10T00:00:00Z"
draft: false

# Prev/next pager order (if `docs_section_pager` enabled in `params.toml`)
weight: 3
---

## What is Jekyll

Jekyll is a framework that takes different, easy to read/format, small files and builds a static website for you. These small files are usually in markdown format, so it’s really straightforward to edit them without messing things up and just focusing on the content (e.g., posts in a blog).

When you run Jekyll on the terminal, it puts all the smaller files and reads the configuration file to decide which parts to include. The resulting static website is built on the `_site` folder. You should never edit any file on this folder.

## Install RubyGems

The first step to get Jekyll on your system is to install Ruby:

```bash
sudo pacman -S ruby ruby-rdoc --needed
gem update
gem update --system
```

## Install Jekyll

Then you can simply install Jekyll using Gem, Ruby's the package manager:

```bash
gem install jekyll
```

## Install bundle and jekyll theme dependencies

Most Jekyll templates come with a `Gemfile` that specifies which plugins/packages are needed. To install these automatically, you need `bundle`:

```bash
gem install bundle
```

Then you just open a terminal on your template's root folder and execute `bundle`:
```bash
cd PATH
bundle install
```

## Set virtual environment

To build your website and run it locally (useful for testing and making sure everything works), just run:
```bash
jekyll serve --watch
```

Some Jekyll templates/websites will give you an error similar to the following one:
```
Traceback (most recent call last):
...
/home/user/.gem/ruby/2.6.0/gems/bundler-2.0.1/lib/bundler/runtime.rb:319:in `check_for_activated_spec!':
You have already activated public_suffix 3.0.3, but your Gemfile requires public_suffix 2.0.5.
Prepending `bundle exec` to your command may solve this. (Gem::LoadError)
```

Just prepend `bundle exec` as it suggests, and you'll be fine:
```bash
bundle exec jekyll serve --watch
```

I honestly just use this last command exclusively, defined as an alias in my `.zshrc` file:
```bash
alias jekyll-serve="bundle exec jekyll serve --watch"
```
as it works in all scenarios.
