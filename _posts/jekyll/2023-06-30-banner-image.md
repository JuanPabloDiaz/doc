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

THIS POST NEED SOME WORK...

STEP BY STEP ON WHAT <mark>I DID</mark>

Have you ever desired to incorporate a graphic at the beginning of your Jekyll post but lacked the knowledge on how to accomplish it? Fear not, for it is a simple task requiring only a small portion of code.

{% include embed/youtube.html id='6oKO-7gsM4s' %}
_watch the series_

> Remember to watch from minute 12. (usefull info before but its not for that)

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
/>
{%- endif -%}
```
