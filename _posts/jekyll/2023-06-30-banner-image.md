---
layout: post
title: "Add Featured Images to Jekyll Posts"
date: 2023-06-30 09:00:00 -0500
author: cotes
categories: jekyll documentation
tags: portfolio project markdown typography
image: /assets/img/banners-posts/laptop.jpg
pin: true
math: true
mermaid: true
---

Have you ever desired to incorporate a graphic at the beginning of your Jekyll post but lacked the knowledge on how to accomplish it? Fear not, for it is a simple task requiring only a small portion of code.

{% include embed/youtube.html id='6oKO-7gsM4s' %}
_watch the series_

> Remember to watch from minute 12. (usefull info before but its not for that)

### Code

Add to the layout of the blog page:

```markdown
---
image: /assets/img/banners-posts/default.jpg
---
```

Add to the begining of the blog page:

```markdown
![alternative text]({{ page.image }})
```

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
/>{%- endif -%}
