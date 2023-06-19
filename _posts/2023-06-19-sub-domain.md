---
layout: post
title: "How to Create a Subdomain"
date: 2023-06-19 03:00:00 -0500
categories: domain
tags: portfolio project github frontend hosting subdomain porkbun vercel
---

# How to Add and Configure a SubDomain on Porkbun and Vercel

![url components](https://d33v4339jhl8k0.cloudfront.net/docs/assets/5854c918c697912ffd6c1d7a/images/616f54ff9ccf62287e5ed89e/file-11KfXM8UHZ.png "url components")

## Prerequisites

- Own a custom domain in Porkbun.
  > Check this article for details on [How to Purchase and Configure Your New Domain in Porkbun](https://www.jpdiaz.top/posts/new-domain/).
- Have a project deployed in Vercel.

## Step by Step in Vercel

1. Go to Vercel and login.
2. Open the project you want to link.
3. Click on Domains.
4. Type the subdomain that you previously configured and click the "Add" button.
5. Use the information from Vercel to link your domain in Porkbun.

## Step by Step in Porkbun

1. Go to Porkbun and login.
2. Click on "Account" button > "Domain Managment" button.
3. Locate your domain and click the "Details" button > "edit" option next to "DNS Records".
4. Add the subdomain in the host field (ex: if url is doc.jpdiaz.dev, add "doc" for the host).
5. Add a "cname.vercel-dns.com." in the answer field.
6. Click Add.
   > Check the [Porkbun documentation](https://kb.porkbun.com/article/200-how-to-create-a-subdomain) for more details.
