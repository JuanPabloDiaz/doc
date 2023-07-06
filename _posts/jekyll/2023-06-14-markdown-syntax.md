---
layout: post
title: "Markdown Syntax"
date: 2023-06-14 09:00:00 -0500
author: juan
categories: jekyll customize
tags: jekyll portfolio project markdown typography
image: /assets/img/featured-posts/code.jpg
math: true
mermaid: true
---

This post has been sourced from [**Chirpy**](https://chirpy.cotes.page/posts/text-and-typography/) and it is intended to demonstrate Markdown syntax rendering, You can also utilize it as a writing example. For more information, please visit the [markdown documentation guide](https://www.markdownguide.org/basic-syntax). Now, let's begin exploring the markdown syntax.

## Headings

To create a heading, add number signs (#) in front of a word or phrase. The number of number signs you use should correspond to the heading level. For example, to create a heading level three (<h3>), use three number signs (e.g., ### My Header). Or you can also use html tags.

| Markdown                    | HTML                          |
| :-------------------------- | :---------------------------- |
| # H1 - Heading level 1      | <h1>H1 - Heading level 1</h1> |
| ## H2 - Heading level 2     | <h2>H2 - Heading level 2</h2> |
| ### H3 - Heading level 3    | <h3>H3 - Heading level 3</h3> |
| #### H4 - Heading level 4   | <h4>H4 - Heading level 4</h4> |
| ##### H5 - Heading level 5  | <h5>H5 - Heading level 5</h5> |
| ###### H6 - Heading level 6 | <h6>H6 - Heading level 6</h6> |

<h5>Rendered Output</h5>

<h1>H1 - Heading level 1</h1>
<h2>H2 - Heading level 2</h2>
<h3>H3 - Heading level 3</h3>
<h4>H4 - Heading level 4</h4>
<h5>H5 - Heading level 5</h5>
<h6>H6 - Heading level 6</h6>

## Paragraph

To create paragraphs, use a blank line to separate one or more lines of text.

Generating random paragraphs can be an excellent way for writers to get their creative flow going at the beginning of the day. The writer has no idea what topic the random paragraph will be about when it appears. This forces the writer to use creativity to complete one of three common writing challenges. The writer can use the paragraph as the first one of a short story and build upon it. A second option is to use the random paragraph somewhere in a short story they create. The third option is to have the random paragraph be the ending paragraph in a short story. No matter which of these challenges is undertaken, the writer is forced to use creativity to incorporate the paragraph into their writing.

## Lists

You can organize items into ordered and unordered lists.

### Ordered list

1. Firstly
2. Secondly
3. Thirdly

### Unordered list

```markdown
- Chapter
  - Section
    - Paragraph
```

<h5>Rendered Output</h5>

- Chapter
  - Section
    - Paragraph

### Mix list

You can nest an unordered list in an ordered list, or vice versa.

```markdown
1. First item
2. Second item
   - Indented item
     - Indented item
3. Third item
```

<h5>Rendered Output</h5>

1. First item
2. Second item
   - Indented item
     - Indented item
3. Third item

### ToDo list

```markdown
- [ ] Job
  - [x] Step 1
  - [x] Step 2
  - [ ] Step 3
```

<h5>Rendered Output</h5>

- [ ] Job

  - [x] Step 1
  - [x] Step 2
  - [ ] Step 3

  ### Hover Text

```markdown
[id1]: ## "your hover text"

This is a [hover text][id1] example.
```

<h5>Rendered Output</h5>

[id1]: ## "your hover text"

This is a [hover text][id1] example.

### Description list

```markdown
Def-name
\ \ : description/definition
```

<h5>Rendered Output</h5>

Sun
: the star around which the earth orbits

Moon
: the natural satellite of the earth, visible by reflected light from the sun

## Block Quote

Add "> " to the beginning of the paragraph

> This line shows the _block quote_.

## Prompts

```markdown
> An example showing the `tip` type prompt.
> {: .prompt-tip }
```

> An example showing the `tip` type prompt.
> {: .prompt-tip }

```markdown
> An example showing the `info` type prompt.
> {: .prompt-info }
```

> An example showing the `info` type prompt.
> {: .prompt-info }

> An example showing the `warning` type prompt.
> {: .prompt-warning }

> An example showing the `danger` type prompt.
> {: .prompt-danger }

## Tables

To add a table, just copy and modify the code below

```markdown
| Company | Contact      | Country |
| :------ | :----------- | ------: |
| Tesla   | Maria Anders | Germany |
```

<h5>Rendered Output</h5>

| Company | Contact          | Country |
| :------ | :--------------- | ------: |
| Tesla   | Maria Anders     | Germany |
| Apple   | Helen Bennett    |      UK |
| Rolex   | Giovanni Rovelli |   Italy |

## Links

To create a link, enclose the link text in brackets (e.g., [Markdown Guide]) and then follow it immediately with the URL in parentheses (e.g., (https://www.markdownguide.org/basic-syntax/#overview)).

```markdown
[link-name](link-url)
```

<h5>Rendered Output</h5>

[Markdown Guide](https://www.markdownguide.org/basic-syntax/#overview)

#### To quickly turn a URL into a link, enclose it in angle brackets "<>".

```markdown
<https://www.markdownguide.org/basic-syntax>
```

<h5>Rendered Output</h5>
<https://www.markdownguide.org/basic-syntax>

## Emphasis

You can add emphasis by making text bold or italic.

### Bold

```markdown
**bold text**
```

This is a **bold text**

### Italic

remove the "\"

```markdown
\*Italic text\*
```

This is an _italic text_

## Footnote

Click the hook will locate the footnote[^footnote], and here is another footnote[^fn-nth-2].

## Inline code

```markdown
`Inline Code`
```

This is an example of `Inline Code`.

## Filepath

```markdown
Here is the `/path/to/the/file.extend`{: .filepath}.
```

Here is the `/path/to/the/file.extend`{: .filepath}.

## Code blocks

### Common

```

This is a common code snippet, without syntax highlight and line number.

```

### Specific Language

```bash
if [ $? -ne 0 ]; then
  echo "The command was not successful.";
  #do the needful / exit
fi;
```

### Specific filename

@import
"colors/light-typography",
"colors/dark-typography";

````

{: file='\_sass/jekyll-theme-chirpy.scss'}

## Mathematics

The mathematics powered by [**MathJax**](https://www.mathjax.org/):

$$ \sum\_{n=1}^\infty 1/n^2 = \frac{\pi^2}{6} $$

When $a \ne 0$, there are two solutions to $ax^2 + bx + c = 0$ and they are

$$ x = {-b \pm \sqrt{b^2-4ac} \over 2a} $$

## Mermaid SVG

```mermaid
 gantt
  title  Adding GANTT diagram functionality to mermaid
  apple :a, 2017-07-20, 1w
  banana :crit, b, 2017-07-23, 1d
  cherry :active, c, after b a, 1d
````

## Add Images

### Default (with caption)

![Desktop View](/assets/img/featured-posts/default.jpg){: width="972" height="589" }
_Full screen width and center alignment_

### Left aligned

![Desktop View](/assets/img/featured-posts/default.jpg){: width="972" height="589" .w-75 .normal}

### Float to left

![Desktop View](/assets/img/featured-posts/default.jpg){: width="972" height="589" .w-50 .left}
Praesent maximus aliquam sapien. Sed vel neque in dolor pulvinar auctor. Maecenas pharetra, sem sit amet interdum posuere, tellus lacus eleifend magna, ac lobortis felis ipsum id sapien. Proin ornare rutrum metus, ac convallis diam volutpat sit amet. Phasellus volutpat, elit sit amet tincidunt mollis, felis mi scelerisque mauris, ut facilisis leo magna accumsan sapien. In rutrum vehicula nisl eget tempor. Nullam maximus ullamcorper libero non maximus. Integer ultricies velit id convallis varius. Praesent eu nisl eu urna finibus ultrices id nec ex. Mauris ac mattis quam. Fusce aliquam est nec sapien bibendum, vitae malesuada ligula condimentum.

### Float to right

![Desktop View](/assets/img/featured-posts/default.jpg){: width="972" height="589" .w-50 .right}
Praesent maximus aliquam sapien. Sed vel neque in dolor pulvinar auctor. Maecenas pharetra, sem sit amet interdum posuere, tellus lacus eleifend magna, ac lobortis felis ipsum id sapien. Proin ornare rutrum metus, ac convallis diam volutpat sit amet. Phasellus volutpat, elit sit amet tincidunt mollis, felis mi scelerisque mauris, ut facilisis leo magna accumsan sapien. In rutrum vehicula nisl eget tempor. Nullam maximus ullamcorper libero non maximus. Integer ultricies velit id convallis varius. Praesent eu nisl eu urna finibus ultrices id nec ex. Mauris ac mattis quam. Fusce aliquam est nec sapien bibendum, vitae malesuada ligula condimentum.

### Dark/Light mode & Shadow

The image below will toggle dark/light mode based on theme preference, notice it has shadows.

![light mode only](/assets/img/featured-posts/default.jpg){: .light .w-75 .shadow .rounded-10 w='1212' h='668' }
![dark mode only](/assets/img/featured-posts/default.jpg){: .dark .w-75 .shadow .rounded-10 w='1212' h='668' }

## Video

Adding a Youtube video is super easy, you just copy the code below and modify the id. Make sure to delete the dashes (-)

```
{-% include embed/youtube.html id='xopvkx6CpNs' %-}
```

<h5>Rendered Output</h5>

{% include embed/youtube.html id='xopvkx6CpNs' %}

📺 [Watch Video](https://www.youtube.com/watch?v=Aq6eoMjW7V0)

## Reverse Footnote

[^footnote]: The footnote source
[^fn-nth-2]: The 2nd footnote source
