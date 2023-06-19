---
layout: post
title: "How to Create a Subdomain"
date: 2023-06-19 03:00:00 -0500
categories: domain
tags: dns subdomain porkbun vercel github-pages
---

<!-- Dropdown in Markdown: https://gist.github.com/citrusui/07978f14b11adada364ff901e27c7f61 -->

<details>
<summary>
What is a Subdomain?
</summary>
<br>
Watch this video to learn more about Subdomain and how to use them.
<br>

{% include embed/youtube.html id='HYXiFs-JQBM' %}

By: Eli the Computer Guy

</details>
<br>

> 💡 Note: It is important to mention that the subdomain can link to a completely different website.
> <br> To link another site just add the DNS records from the host to the new subdomain.

<br>

In this article, you will learn how to connect your projects hosted on GitHub Pages or Vercel to a custom sub-domain in Porkbun.

## How to Add and Configure a SubDomain on Porkbun and Vercel

![url components](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5854c918c697912ffd6c1d7a/images/616f54ff9ccf62287e5ed89e/file-11KfXM8UHZ.png "url components")

### Prerequisites

- Own a custom domain in Porkbun.
  > Check this article for details on [How to Purchase and Configure Your New Domain in Porkbun](https://www.docs.jpdiaz.dev/posts/new-domain/).
- Have a project deployed in Vercel.

### Step by Step in Vercel

1. Go to Vercel and login.
2. Open the project you want to link.
3. Click on Domains.
4. Type the subdomain that you previously configured and click the "Add" button.
5. Use the information from Vercel to link your domain in Porkbun.

### Step by Step in Porkbun

1. Go to Porkbun and login.
2. Click on "Account" button > "Domain Managment" button.
3. Locate your domain and click the "Details" button > "edit" option next to "DNS Records".
4. Add the subdomain in the host field (ex: if url is doc.jpdiaz.dev, add "doc" for the host).
5. Add a "cname.vercel-dns.com." in the answer field.
6. Click Add.
   > Check the [Porkbun documentation](https://kb.porkbun.com/article/200-how-to-create-a-subdomain) for more details.

---

## Adding and Configuring a Subdomain on Porkbun and GitHub Pages

### Prerequisites

- Own a custom domain in Porkbun.
  > Check this article for details on [How to Purchase and Configure Your New Domain in Porkbun](https://www.docs.jpdiaz.dev/posts/new-domain/).
- Enable GitHub Pages
  > check the [Github documentation](https://docs.github.com/en/pages/quickstart) for more details.

### Step by Step in GitHub Pages

1. Go to GitHub and login.
2. Open the repository you want to link.
3. Click on the "settings" button > "pages".
4. Under "Custom domain", type the subdomain and click the "save" button.
5. Use the information from Vercel to link your domain in Porkbun.

### Step by Step in Porkbun

1. Go to Porkbun and login.
2. Click on "Account" button > "Domain Managment" button.
3. Locate your domain and click the "Details" button > "edit" option next to "DNS Records".
4. Add the subdomain in the host field (ex: if url is doc.jpdiaz.dev, add "doc" for the host).
5. Add a "cname.vercel-dns.com." in the answer field.
6. Click Add.
   > Check the [Porkbun documentation](https://kb.porkbun.com/article/200-how-to-create-a-subdomain) for more details.
