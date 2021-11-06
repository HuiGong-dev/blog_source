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

this will create a new Markdown file named `Hello world` in the content/posts directory. Open the file with your favorite editor (shout out to [VS Code](https://code.visualstudio.com/)) and change the `draft: true` to `draft: false`.

Now, start the Hugo server to preview your site:

```Shell
hugo server -D
```

You can then check your new site at http://localhost:1313/.

Next step is to configure the `config.toml` file. Open it with your favorite editor and set `baseURL` to `https://username.github.io/`. Remember to replace `username` to your own username on GitHub. The code below shows how it looks like by my side.

```Toml
theme = "hyde"
baseURL = 'https://huigong-dev.github.io/'
languageCode = 'en-us'
```

Great! You're all set! Finally it's time to build your site:

```Shell
hugo -D
```

code of your site will be generated under `./public/`. Change directory to `public/`, do `git init` and set remote to your GitHub pages repository. Push to your GitHub pages repository and your site should be live within seconds.

### Create a blog source repository in GitHub

Okay, now your site is live, what's next? A problem used to bother me a lot was: how can I update my blog on multiple computers? Say, I have wrote something for my blog on my PC at home and now I'm on the way with a laptop. How can I continue my work? Well the answer is: create a GitHub repository just for your source code. I said "just" because the `public/` directory is within the source code directory and we need to ignore `public/` and push the rest of them to github. Another benefit is that you can use GitHub Actions to glue your source code and blog together, which means you don't need to build and deploy your site every time you changed anything in your site, GitHub Actions will do all the boring stuff for you. Sounds nice? Here is how:

Head over to GitHub and create a new repository with name like `blog_source` or anything that reminds you it's the source of your blog. Set it as remote repository for your source code and add `public/` to `.gitignore`.

```Shell
touch .gitignore
echo "public/" >> .gitignore
```

push it to GitHub and next time you want to edit your blog on another machine you just need to pull it from GitHub and continue the work.

### Automate the deploy using GitHub Actions

This is one of the exciting part building a blog with GitHub Pages. Before building this blog I knew almost nothing about GitHub Actions but after using it, it was amazing! Automating the boring stuff always makes me hyped!

Fist step is to create a GitHub personal access token. Follow the official documents [here](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token) for more information.

Next, Head over to your `blog_source` repository on GitHub and click `Settings -> Secrets -> new repository secret`. Paste the token you just got, set the name to `ACTIONS_DEPLOY_KEY` and hit the `Add secret` button.

Add the file `.github/workflows/pages.yml` below to your source code repository. The `external_repository` points to your blog repository.

```Yml
name: hugo publish

on:
  push:
    branches:
    - main

jobs:
  build-deploy:
    runs-on: macos-latest
    steps:
    - name: Git checkout
      uses: actions/checkout@v2
    
    - name: Update theme
      run: git submodule update --init --recursive

    - name: Setup Hugo
      uses: peaceiris/actions-hugo@v2
      with:
        hugo-version: '0.88.1'

    - name: Build
      run: hugo  --minify

    - name: Deploy
      uses: peaceiris/actions-gh-pages@v3
      with:
        personal_token: ${{ secrets.ACTIONS_DEPLOY_KEY }}
        external_repository: your-github-name/your-github-name.github.io
        publish_branch: main
        publish_dir: ./public
        user_name: your-name
        user_email: your-email
```

And we are done! GitHub Actions will do all the boring "build and deploy" routine and you can concentrate on content creating and more.

Happy blogging!
