---
layout: post
title: "How to Add Featured Images to Jekyll Posts"
date: 2023-06-30 09:00:00 -0500
author: juan
categories: jekyll customize
tags: jekyll featured-img
image: /assets/img/featured-posts/design.jpg
---

Have you ever desired to incorporate an image at the beginning of your Jekyll post but lacked the knowledge on how to accomplish it? Fear not, for it is a simple task requiring only a small portion of code.

You can watch the [video](https://www.youtube.com/watch?v=6oKO-7gsM4s&t=725s) below and follow along with this post, which explains how I added a featured image[^feature-img] at the beginning of all my posts. Yes, that's right—for every single post, even those without an image set by me. It automatically uses a default image for all those posts where I didn't set one.

# Part 1: Add a featured image to your posts

{% include embed/youtube.html id='6oKO-7gsM4s' %}

## Requirements

To effectively engage in this project and follow along the content outlined in the article and the video starting from the [7th minute](https://youtu.be/6oKO-7gsM4s?t=447), you will require the following items:

- Basic HTML, CSS and Markdown knowledge.
- Basic Jekyll knowledge. Check [previous Jekyll posts](../../categories/jekyll/) for more content.
<!-- - Basic Jekyll knowledge. Check [previous Jekyll posts](https://docs.jpdiaz.dev/categories/jekyll/) for more content. -->
- A funtional Jekyll site with at least two post files.
- Some images to work with (located at assets/img/)

If you do not have much time but you have experience using Jekyll. I suggest you to watch the video from [12th minute](https://www.youtube.com/watch?v=6oKO-7gsM4s&t=725s), and jump to section 2:[Modify the \_layout/post.html file](#modify-the-_layoutposthtml-file) in this post.

---

Section 1 starts from the [7th minute](https://youtu.be/6oKO-7gsM4s?t=447) of the video.

## Add Image Path to YAML Front Matter

There are multiple ways to add an image into your post, using an html image tag or a markdown syntax. However, you can also add it by including an image field on the YAML Front Matter[^YAML]. (video: [Add image](https://youtu.be/6oKO-7gsM4s?t=447))
By adding the image field in the YAML Front Matter, it also makes the image visible/appear at the preview for the post.

1. Copy and past the code below to your YAML Front Matter:

```markdown
---
image: /assets/img/featured-posts/default.jpg
---
```

> 📚 For more details on how to [set featured image](https://chriskyfung.github.io/amp-affiliately-jekyll-theme/front-matter-guide/#set-featured-image), visit the Front Matter Guide.

<!-- code below for the order list, more details: https://stackoverflow.com/a/41575690/9374650 -->

{:start="2"}

2. Add the following code to display the image in your post. (delete the `*` from the code)

```text
![alternative text]({*{ page.image }*})
```

- Add the relative url in case your image is not displaying with the previous code. (delete the `*` from the code)

```text
![alternative text]({*{- page.image | relative_url -}*})
```

---

Section 2 starts from the 12th minute of the video.

## Modify the **\_layout/post.html** file

In order to modify the layout of the post and display the featured image on top of every post, you need to locate and understand the post layout.

1. Go to the `_layout` folder and open the `post.html` file

> 📚 If you are missing the `_layout` folder. Visit related issue on [Stackoverflow](https://stackoverflow.com/questions/38891463/jekyll-default-installation-doesnt-have-layouts-directory) or [Jekyll themes docs](https://jekyllrb.com/docs/themes/).
>
> - Once you understand what is going on, go ahead and [override the theme default](https://jekyllrb.com/docs/themes/#overriding-theme-defaults)

<!-- code below for the order list, more details: https://stackoverflow.com/a/41575690/9374650 -->

{:start="2"}

2.  Choose where you need the featured image to be
3.  Add the code below to display the image.

```html
<img
  src="{{- page.image | relative_url -}}"
  alt="featured image"
  class="featured-image-post"
/>
```

## Include a Default Image

{:start="4"}

4. Include an `if` & `else` statement to the code from step 3 (delete the `*` from the code):

```text
{*% include lang.html %*}
{*%- if page.image -%*}
<img
  src="{{- page.image | relative_url -}}"
  alt="featured image"
  class="featured-image-post"
/>
{*%- else -%*}
{*%- assign postImage = "/assets/img/featured-posts/default.jpg" -%*}
<img
  src="{{- postImage | relative_url -}}"
  alt="Default featured image"
  class="featured-image-post"
/>
{*%- endif -%*}
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

<br>
<br>
## Resize the Featured Image

In order to modify the image style, you need to add some CSS.

{:start="5"}

5. Go to the `_sass` folder and open the `_layout.scss` file

   > 📚 Missing the `_sass` folder? Visit related issue on [Stackoverflow](https://stackoverflow.com/questions/38891463/jekyll-default-installation-doesnt-have-layouts-directory) or [Jekyll themes docs](https://jekyllrb.com/docs/themes/).

6. Add the CSS code bellow
   > The file name could be different, just look for the appropriate `.scss` file

```css
.featured-image-post {
  width: 100%;
  height: 150px;
  object-fit: cover;
}
```

<br>
<br>

---

# Part 2: Add featured images to the list of posts (blog roll, posts reel)

{% include embed/youtube.html id='1GskmTFLrA4' %}

## Modify the **\_layout/home.html** file (Part 2)

In order to modify the layout of the blog roll or list of posts and display the featured image, you need to locate and understand the post layout.

1. Go to the `_layout` folder and open the `home.html` file

   > 📚 Missing the `_layout` folder? Visit related issue on [Stackoverflow](https://stackoverflow.com/questions/38891463/jekyll-default-installation-doesnt-have-layouts-directory) or [Jekyll themes docs](https://jekyllrb.com/docs/themes/).

   <!-- code below for the order list, more details: https://stackoverflow.com/a/41575690/9374650 -->

{:start="2"}

2.  Choose where you need the featured image to be
3.  Add the code below to display the image on the blog roll.

```html
<img
  src="{{- post.image | relative_url -}}"
  alt="blog roll image"
  class="blog-roll-image"
/>
```

## Include a Default Image (Part 2)

{:start="4"}

4. Include an `if` & `else` statement to the code from step 3 (delete the `*` from the code):

```text
    {*%- if post.image -%*}
      <img src="{*{- post.image | relative_url -}*}" alt="" class="blog-roll-image">
    {*%- else -%*}
      {*%- assign postImage = "/assets/img/featured-posts/default.jpg" -%*}
      <img src="{{- postImage | relative_url -}}" alt="" class="blog-roll-image">
    {*%- endif -%*}
```

<h5>Rendered Output</h5>

{%- if post.image -%}
<img src="{{- post.image | relative_url -}}" alt="blog roll image" class="blog-roll-image" width="75px" height="75px" >
{%- else -%}
{%- assign postImage = "/assets/img/featured-posts/default.jpg" -%}
<img src="{{- postImage | relative_url -}}" alt="blog roll image" class="blog-roll-image" width="200" height="200" >
{%- endif -%}
<br>
<br>

## Resize the Featured Image (Part 2)

In order to modify the image style, you need to add some CSS.

{:start="5"}

5. Go to the `_sass` folder and open the `_layout.scss` file
6. Add the CSS code bellow
   > The file name could be different, just look for the appropriate `.scss` file

```css
.blog-roll-image {
  width: 75px;
  height: 75px;
  object-fit: cover;
  float: left;
}
```

<!-- ACKNOWLEDGMENTS -->

## Acknowledgments 📚

Resources list that I find helpful and would like to give credit to.

- [Bill Raymond](https://talk.jekyllrb.com/t/learn-how-to-add-featured-images-to-your-posts/4852)

<br>

---

<!-- Footnote -->

[^feature-img]: An image that represent the contents, mood, or theme of a post or page.
[^YAML]: Placed at the top of a page and is used for maintaining metadata for the page and its contents.
