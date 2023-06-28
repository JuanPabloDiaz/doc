---
layout: post
title: "Customize the Favicon"
date: 2023-06-27 09:00:00 -0500
author: cotes
categories: Blogging jekyll Tutorial localhost
tags: portfolio project github markdown favicon
---

<!-- Dropdown in Markdown: https://gist.github.com/citrusui/07978f14b11adada364ff901e27c7f61 -->

<details>
<summary>
What is To Customize the Favicon?
</summary>
<br>

Customizing the favicon refers to the process of changing the small icon that appears in the browser tab or bookmark bar when someone visits your website. The favicon is a visual representation of your website and helps users easily identify and locate your site among their open tabs or bookmarks.
<br>

The favicon typically appears as a 16x16 pixel or 32x32 pixel image and is usually saved in the ICO (icon) format, although other image formats like PNG or GIF can also be used. By customizing the favicon, you can give your website a unique visual identity and make it more recognizable to users.
<br>

To customize the favicon for your website, you need to create an image that you want to use as your favicon and save it in the appropriate format (ICO, PNG, GIF, etc.). Once you have the favicon image ready, you can upload it to your website's root directory and add a reference to it in the HTML code of your web pages.
<br>

The HTML code to add a favicon typically looks like this:
<br>

```html
<link rel="icon" type="image/png" href="/path/to/favicon.png" />
```

<br>

In this example, the `href` attribute specifies the path to the favicon image file. You would need to replace `/path/to/favicon.png` with the actual path to your favicon image.
<br>

By customizing the favicon, you can enhance the branding and visual appeal of your website, making it more memorable for visitors.
<br>

</details>
<br>

This documentation article has been sourced from [**Chirpy Doc**](https://chirpy.cotes.page/posts/customize-the-favicon/).

If desired, you can replace them with your own. The following sections will provide guidance on creating and replacing the default favicons.

<b>The [favicons](https://www.favicon-generator.org/about/) of [**Jekyll Theme Chirpy**](https://github.com/cotes2020/jekyll-theme-chirpy/) are located in the directory <mark><i>assets/img/favicons/</i></mark>. If you wish to customize it with your own logo or icon, the following sections will guide you through the process of creating and replacing the default favicons. For more information about favicons, you can visit [Favicon Generator](https://www.favicon-generator.org/about/).</b>

> ✔️⚠️ Warning: the path is `assets/img/favicons/`{: .filepath}

> ❌🚫 Which is <b>NOT</b> the same as `_posts/assets/img/favicons/`{: .filepath}

### 💥Project error 💥

I had some issues when I was trying to Customize the Favicon. I were only able to view the favicon with my logo in localhost. For some reason, the images and the changes I made were not getting deployed, and I didn't see it in my GitHub for the project either. I clean my cache and tried several things as well from multiple blogs but nothing seems to work.
I noticed that the customize Favicon images get switched back to the originals after stopping the server and running the "bundle exec jekyll s" command.
I didnt know what could be causing this issue??

### 🏁 Resolution 🏁

After several hours of research and trial and error, I have finally achieved success! :D

The images and folders that I was adding into my Jekyll assets were getting deleted because I was adding them inside the wrong folder.

> 💡 <mark>I add them inside <i>\_site/assets/img</i> folder instead of <i>assets/img/favicons</i></mark>

The \_site folder is deleted and rebuilt after every change or jekyll build execution. You should put your files in the /images/ directory in the main project folder.

In Terminal, navigate to the root directory of the specific jekyll folder (e.g. /theme-name/) and use the command jekyll build to rebuild the \_site folder reflecting any changes you've made.

Stackoverflow: [Jekyll assets get deleted](https://stackoverflow.com/questions/45090500/jekyll-assets-get-deleted)

![JD Logo black](/assets/img/juanDiaz-logo/jd-logo-black.png){: width="200" height="200"}![JD Logo cream](/assets/img/juanDiaz-logo/jd-logo-cream.png){: width="200" height="200"}![JD Logo white](/assets/img/juanDiaz-logo/jd-logo-white.png){: width="200" height="200"}

## Generate the favicon

Prepare a square image (PNG, JPG, or SVG) with a size of 512x512 or more, and then go to the online tool [**Real Favicon Generator**](https://realfavicongenerator.net/) and click the button <kbd>Select your Favicon image</kbd> to upload your image file.

In the next step, the webpage will show all usage scenarios. You can keep the default options, scroll to the bottom of the page, and click the button <kbd>Generate your Favicons and HTML code</kbd> to generate the favicon.

## Download & Replace

Download the generated package, unzip and delete the following two from the extracted files:

- `browserconfig.xml`{: .filepath}
- `site.webmanifest`{: .filepath}

And then copy the remaining image files (`.PNG`{: .filepath} and `.ICO`{: .filepath}) to cover the original files in the directory `assets/img/favicons/`{: .filepath} of your Jekyll site. If your Jekyll site doesn't have this directory yet, just create one.

The following table will help you understand the changes to the favicon files:

| File(s) | From Online Tool | From Chirpy |
| ------- | :--------------: | :---------: |
| `*.PNG` |        ✓         |      ✗      |
| `*.ICO` |        ✓         |      ✗      |

> ✓ means keep, ✗ means delete.
> {: .prompt-info }

The next time you build the site, the favicon will be replaced with a customized edition.
