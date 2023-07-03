---
layout: post
title: "How to Add Featured Images to Jekyll Posts"
date: 2023-06-30 09:00:00 -0500
author: juan
categories: jekyll customize
tags: jekyll featured-img
pin: true
image: /assets/img/featured-posts/design.jpg
---

Have you ever desired to incorporate an image at the beginning of your Jekyll post but lacked the knowledge on how to accomplish it? Fear not, for it is a simple task requiring only a small portion of code.

You can watch the [video](https://www.youtube.com/watch?v=6oKO-7gsM4s&t=725s) below and follow along with this post, which explains how I added a featured image[^feature-img] at the beginning of all my posts. Yes, that's right—for every single post, even those without an image set by me. It automatically uses a default image for all those posts where I didn't set one.

{% include embed/youtube.html id='6oKO-7gsM4s' %}
_Watch [Part 2](https://www.youtube.com/watch?v=1GskmTFLrA4&t=0s)_

## Requirements

To effectively engage in this project and follow along the content outlined in the article and the video starting from the [7th minute](https://youtu.be/6oKO-7gsM4s?t=447), you will require the following items:

- Basic HTML, CSS and Markdown knowledge.
- Basic Jekyll knowledge. Check [previous Jekyll posts](../../categories/jekyll/) for more content.
<!-- - Basic Jekyll knowledge. Check [previous Jekyll posts](https://docs.jpdiaz.dev/categories/jekyll/) for more content. -->
- A funtional Jekyll site with at least two post files.
- Some images to work with (located at assets/img/)

If you do not have much time but you have experience using Jekyll. I suggest you to watch the video from [12th minute](https://www.youtube.com/watch?v=6oKO-7gsM4s&t=725s) instead. And jump to [Minute 12](#minute-12) in this post.

## Add Image Path to YAML Front Matter

There are multiple ways to add an image into your post, using an html image tag or a markdown syntax. However, you can also add it by including an image field on the YAML Front Matter[^YAML]. (video: [Add image](https://youtu.be/6oKO-7gsM4s?t=447))

Copy and past the code below to your YAML Front Matter:

```markdown
---
image: /assets/img/featured-posts/default.jpg
---
```

Add the following code to display the image in your post. (delete the \* from the code)

```text
![alternative text]({*{ page.image }*})
```

Add the relative url in case your image is not displaying with the previous code. (delete the \* from the code)

```text
![alternative text]({*{- page.image | relative_url -}*})
```

## Modify the \_layout/post.html file

[Locate and understand the post layout](https://www.youtube.com/watch?v=6oKO-7gsM4s&t=725s)

```markdown
{-% include lang.html %-}
{-%- if page.image -%-}
```

img <>

```markdown
<img
  src="{{- page.image | relative_url -}}"
  alt="featured image"
  class="featured-image-post"
/>
```

```markdown
{-%- else -%-}
{-%- assign postImage = "/assets/img/featured-posts/default.jpg" -%-}
```

```markdown
<img
  src="{{- postImage | relative_url -}}"
  alt="Default featured image"
  class="featured-image-post"
/>
```

```markdown
{-%- endif -%-}
```

## Minute 12

```markdown
{-% include lang.html %-}
{-%- if page.image -%-}
<img src="{{- page.image | relative_url -}}" alt="featured image" class="featured-image-post"/>
{-%- else -%-}
{-%- assign postImage = "/assets/img/featured-posts/default.jpg" -%-}
<img src="{{- postImage | relative_url -}}" alt="Default featured image" class="featured-image-post"/>
{-%- endif -%-}
```

<h5>Rendered Output</h5>

{% include lang.html %} {%- if page.image -%}
<img
  src="{{- page.image | relative_url -}}"
  alt="featured image"
  class="featured-image-post"
/>
{%- else -%} {%- assign postImage = "/assets/img/featured-posts/default.jpg" -%}
<img
  src="{{- postImage | relative_url -}}"
  alt="Default featured image"
  class="featured-image-post"
/>
{%- endif -%}

---

#### Footnote

[^feature-img]: An image that represent the contents, mood, or theme of a post or page.
[^YAML]: Placed at the top of a page and is used for maintaining metadata for the page and its contents.
