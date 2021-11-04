---
title: "How to build personal blog using GitHub Pages and Hugo"
date: 2021-11-02T11:00:32+01:00
draft: false
tags: [GitHub Pages, Hugo, GitHub Action]
categories: [Personal Project]
---

You want to build a personal blog but don't want to spend too much time building everything from scratch? Me too! After some research I get to know there're several static site generator out there and the most used generators are: [Jekyll](https://jekyllrb.com/), [Hexo](https://hexo.io/) and [Hugo](https://gohugo.io/). All of them can work perfectly with [GitHub Pages](https://pages.github.com/). I chose Hugo as my site generator and it worked perfectly.

## What is Hugo

Hugo is a static site generator written in [Go](https://golang.org/).

## Why Hugo

It's blazing fast! Hugo's official website states it is "the world’s fastest framework for building websites" and after using it I've nothing to complain about the speed.

Besides, building a blog with Hugo is simple and easy. Here is how:

## Step by step

### Set up GitHub Pages

Head over to [GitHub](https://github.com/), login and create a new public repository named `username.github.io`. Be sure the `username` is exactly the same as your GitHub username. For example: my username is `HuiGong-dev` so my repository should be named as `HuiGong-dev.github.io`. Check the official guide [here]((https://pages.github.com/)) if you met any problem.

### Install Hugo

I'm using MacOS and the installation is quite simple with [Homebrew](https://brew.sh/):

```Shell
brew install hugo
```

To check your installation:

```Shell
hugo version
```

the hugo version should show up if the installation is successful.

### Create your site

```Shell
hugo new site your-site-name
```

replace `your-site-name` with the name of your site. You can name it anything you want. The command above will create a folder named `your-site-name` in your current working directory. For example, if the current working directory is `/Users/huigong/projects`, your site will be located in `/Users/huigong/your-site-name`. If you are not sure about your working directory, just type `pwd` in your terminal:

```Shell
$ pwd
/Users/huigong/projects
```

and the output shows your working directory.

### Choose a theme

```Shell
cd your-site-name
git init
git submodule add https://github.com/spf13/hyde.git
```

There're around 300 themes for Hugo. I chose [hyde](https://github.com/spf13/hyde) for my blog. You can find a theme that fits you best [here](https://themes.gohugo.io/). If none of them is the perfect theme for you, you may consider create your own theme in the future and contribute to the Hugo community :)

Don't forget to configure the theme in `config.toml`. Simply add a line `theme = "hyde"` in the file. Replace `hyde` to the name of your own theme if you picked another theme.

### Build your site and push to GitHub

Creating content in Hugo is simple:

```Shell
hugo new posts/hello-world.md
```

this will create a new Markdown file named `Hello world` in the content/posts directory. Open the file with your favorite editor (shout out for VS Code) and change the `draft: true` to `draft: false`

### Create a blog source repository in GitHub

### Push source code to GitHub

### Automate the deploy using GitHub Action
