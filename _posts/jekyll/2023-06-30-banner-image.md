---
layout: post
title: "How to Add Featured Images to Jekyll Posts"
date: 2023-06-30 09:00:00 -0500
author: juan
categories: jekyll customize
tags: jekyll banner-img
pin: true
image: /assets/img/banners-posts/design.jpg
---

Have you ever desired to incorporate an image at the beginning of your Jekyll post but lacked the knowledge on how to accomplish it? Fear not, for it is a simple task requiring only a small portion of code.

You can watch the [video](https://www.youtube.com/watch?v=6oKO-7gsM4s&t=725s) below and follow along with this post, which explains how I added a banner image at the beginning of all my posts. Yes, that's right—for every single post, even those without an image set by me. It automatically uses a default image for all those posts where I didn't set one.

{% include embed/youtube.html id='6oKO-7gsM4s' %}

> Watch it from minute 12". (usefull info before but its not for that)

_Watch [Part 2](https://www.youtube.com/watch?v=1GskmTFLrA4&t=0s)_

## Requirements

For this project and to follow along this article and the video from minute 7", you need the following:

- Basic HTML, CSS and Markdown knowledge.
- Basic Jekyll knowledge. Check [previous Jekyll posts](../../categories/jekyll/) for more content.
<!-- - Basic Jekyll knowledge. Check [previous Jekyll posts](https://docs.jpdiaz.dev/categories/jekyll/) for more content. -->
- A funtional Jekyll site with at least two post files.
- Some images to work with (located at assets/img/)

Verify the image displays

### Code to add an image into the ....

#### Add the path location to the layout section of the blog page:

```markdown
---
image: /assets/img/banners-posts/default.jpg
---
```

#### Add to the begining of the blog page:

```markdown
![alternative text]({{ page.image }})
```

text here

```markdown
{% include lang.html %} {%- if page.image -%}
```

img <>

```markdown
<img
  src="{{- page.image | relative_url -}}"
  alt="Banner/featured image"
  class="featured-image-post"
/>
```

```markdown
{%- else -%} {%- assign postImage = "/assets/img/banners-posts/default.jpg" -%}
```

```markdown
<img
  src="{{- postImage | relative_url -}}"
  alt="Default banner/featured image"
  class="featured-image-post"
/>
```

```markdown
{%- endif -%}
```

```markdown
{-% include lang.html %-}
{-%- if page.image -%-}
<img src="{{- page.image | relative_url -}}" alt="Banner/featured image" class="featured-image-post"/>
{-%- else -%-}
{-%- assign postImage = "/assets/img/banners-posts/default.jpg" -%-}
<img src="{{- postImage | relative_url -}}" alt="Default banner/featured image" class="featured-image-post"/>
{-%- endif -%-}
```

<h5>Rendered Output</h5>

{% include lang.html %} {%- if page.image -%}
<img
  src="{{- page.image | relative_url -}}"
  alt="Banner/featured image"
  class="featured-image-post"
/>
{%- else -%} {%- assign postImage = "/assets/img/banners-posts/default.jpg" -%}
<img
  src="{{- postImage | relative_url -}}"
  alt="Default banner/featured image"
  class="featured-image-post"
/>
{%- endif -%}
