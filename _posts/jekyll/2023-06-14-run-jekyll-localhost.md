---
layout: post
title: "How to Run this Static Site Project in Local"
date: 2023-06-14 09:00:00 -0500
categories: jekyll launch
tags: jekyll portfolio project github markdown localhost
pin: true
image: /assets/img/banners-posts/laptop.jpg
---

Now that I have this documentation site up and running (which I did a couple months ago using Jekyll).
I am not sure how to I run the site with Jekyll in local and make some changes...

> 💡 Make sure that I have all the Prerequisites install on the machine. If not, check the previos post [How To Create Static Site Generator with Jekyll](https://www.docs.jpdiaz.dev/posts/create-site-jekyll/)

## Run the Jekyll Commands to:

### Install Dependencies

```bash
bundle
```

or

```bash
bundle install
```

### Run as Local

**To run the project as localhost after completing everything** (serving your site)

```bash
bundle exec jekyll s
```

or

```bash
bundle exec jekyll serve
```

### Run as Local with Auto-Reload

**To run the project as localhost and reload the site ** (serving your site)

```bash
bundle exec jekyll s --livereload
```
