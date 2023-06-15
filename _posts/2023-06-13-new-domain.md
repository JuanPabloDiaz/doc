---
layout: post
title: "Purchase and Configure Your New Domain"
date: 2023-06-13 09:00:00 -0500
categories: domain
tags: portfolio project github frontend hosting
---

# How to Purchase and Configure your New Domain

## How to purchase a Domain

1. Go to Porkbun and login
2. Search for the domain name
3. select the extension that you prefer. (.com, .org)
4. Follow the steps to complete purchase.

## How to Configure your New Domain with Github Pages

1. Login to Github
2. Make sure your repo has the same name as your username
3. Enable github pages under configurations.
4. Go to Porkbun and select your new domain.
5. Click on DNS
6. Add an A - Address record under type.
7. Leave the host field empty.
8. Add 76.76.21.21 in the answer field.
9. Click Add.
10. Add an CNAME - Canonical name record.
11. Add WWW in the host field.
12. Add cname.vercel-dns.com. in the answer field.
13. Click Add.

## How to Configure Your New Domain with Vercel

1. Login to Vercel and Porkbun.
2. Go to the project you want to link in Vercel.
3. Click on Domains.
4. Type the domain that you previously purchased and click Add.
5. Go to Vercel and use the information from vercel to link your domain in Porkbun.
6. Add an A - Address record under type.
7. Leave the host field empty.
8. Add 76.76.21.21 in the answer field.
9. Click Add.
10. Add an CNAME - Canonical name record.
11. Add WWW in the host field.
12. Add cname.vercel-dns.com. in the answer field.
13. Click Add.
14. Wait a couple minutes and visit the site.

📺 [Watch Video](https://www.youtube.com/watch?v=W3jKJ3V_4V4)
