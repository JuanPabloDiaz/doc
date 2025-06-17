---
layout: post
title: "Domain Migration"
date: 2025-06-17
categories: domain
tags: dns domain porkbun vercel netlify
image: /assets/img/errors/triggered-ssr-endpoint.png
---

As a software engineer, I've always been a fan of Vercel. A few weeks ago I migrated a project from Cloudflare to Vercel—and it worked great until I accidentally triggered an SSR endpoint (`/_render`) that spiked resource usage and paused my entire account. (learn more [here](https://github.com/JuanPabloDiaz/favorite/issues/16))

## 🚨 Quick recap

| Issue             | Impact                                                  |
|------------------|---------------------------------------------------------|
| Deployment       | Project `favorite` ran SSR on Vercel                   |
| Usage Spike      | Millions of SSR calls → account paused                 |
| Route `/_render` | 112k+ requests in <12 h, 2.38 GB out, 14M invocations    |

## 🔧 Temporary fix: migrate to Netlify

- Deleted/Paused the project from Vercel (June 16)
- DNS now points to Netlify
- Portfolio is live at [https://jpdiaz.netlify.app](https://jpdiaz.netlify.app)

Next: switch the project to static generation, cache SSR, and block crawlers before re-deploying it safely.


<details>
<summary>
Hosting Migration
</summary>
<br>
Watch this video to learn more about Hosting and how to use them.
<br>

{% include embed/youtube.html id='lvF_WmIoVnw' %}


</details>
<br>

## How to temporarily migrate your Hosting from Vercel to Netlify

1. Login to Vercel, Netlify and Porkbun.
2. Go to Porkbun and save your records (A, CNAME, etc). I mean the records that point to your domain.

![Porkbun Records](/assets/img/domain/lujoymoda-records.png)

3. Go to Netlify and create a new site with the repository you want to migrate.
4. Go to Netlify and 


## My Porkbun-Vercel Records

### jcdistributioncorp.com
![Records](/assets/img/domain/jcdistributioncorp-records.png)

**Records that you should NOT change:**
- MX records (email): fwd1.porkbun.com y fwd2.porkbun.com - KEEP IT THE SAME
- TXT record (SPF for email): El SPF para correo - KEEP IT THE SAME
- CNAME wildcard *.lujoymoda.com: OPTIONAL, but better keep it

### lujoymoda.com
![Records](/assets/img/domain/lujoymoda-records.png)

**You only need to change the A and CNAME records**
- Record A: `lujoymoda.com` → `76.76.21.21`
- This should change to the IP of Netlify
- Record CNAME: `www.lujoymoda.com` → `cname.vercel-dns.com`
- This should change to the domain of Netlify

### talentoparati.com
![Records](/assets/img/domain/talentoparati-records.png)

<details>
<summary>
Talento Para Ti records
</summary>
<br>

<table>
  <thead>
    <tr>
      <th>Type</th>
      <th>Host</th>
      <th>Answer</th>
      <th>TTL</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>A</td>
      <td>talentoparati.com</td>
      <td>76.76.21.21</td>
      <td>600</td>
    </tr>
    <tr>
      <td colspan="5">Notes: REPLACE THIS RECORD</td>
    </tr>
    <tr>
      <td>CNAME</td>
      <td>www.talentoparati.com</td>
      <td>cname.vercel-dns.com</td>
      <td>600</td>
    </tr>
    <tr>
      <td colspan="5">Notes: REPLACE THIS RECORD</td>
    </tr>
    <tr>
      <td>CNAME</td>
      <td>new.talentoparati.com</td>
      <td>cname.vercel-dns.com</td>
      <td>600</td>
    </tr>
    <tr>
      <td colspan="5">Notes: github.com/JuanPabloDiaz/new-site-astro-talentoparati</td>
    </tr>
    <tr>
      <td>CNAME</td>
      <td>url.talentoparati.com</td>
      <td>cname.dub.co</td>
      <td>600</td>
    </tr>
    <tr>
      <td colspan="5">Notes: acortador de links con app.dub.co</td>
    </tr>
    <tr>
      <td>CNAME</td>
      <td>www.links.talentoparati.com</td>
      <td>cname.vercel-dns.com</td>
      <td>600</td>
    </tr>
    <tr>
      <td colspan="5">Notes: linke.ro/talentoparati</td>
    </tr>
    <tr>
      <td>CNAME</td>
      <td>*.talentoparati.com</td>
      <td>pixie.porkbun.com</td>
      <td>600</td>
    </tr>
    <tr>
      <td colspan="5">Notes: </td>
    </tr>
    <tr>
      <td>CNAME</td>
      <td>professional.talentoparati.com</td>
      <td>cname.vercel-dns.com</td>
      <td>600</td>
    </tr>
    <tr>
      <td colspan="5">Notes: github.com/JuanPabloDiaz/professional</td>
    </tr>
    <tr>
      <td>CNAME</td>
      <td>profesional.talentoparati.com</td>
      <td>cname.vercel-dns.com</td>
      <td>600</td>
    </tr>
  </tbody>
</table>

</details>

**You only need to change 2 records**:

**Records to change:**
1. **Record A**: `talentoparati.com` → `76.76.21.21`
   - Change to the IP of Netlify
2. **Record CNAME**: `www.talentoparati.com` → `cname.vercel-dns.com`
   - Change to the domain of Netlify (e.g: `your-site.netlify.app`)

**Records to keep:**
- **MX**: `fwd1.porkbun.com` (email) - **KEEP IT**
- **Wildcard** `*.talentoparati.com` → `pixie.porkbun.com` - **KEEP IT**
- **All other subdomains** (new, url, professional, dev, etc.) - **KEEP IT**

**Why keep the subdomains?**
Because those specific subdomains:
- Are separated projects that work independently
- Some point to GitHub Pages, others to dub.co, linke.ro
- Are not related to your main site
- If you change them, you will break those services

**Simple approach:**
Change only what you need for `talentoparati.com` and `www.talentoparati.com` to work. The rest keep it.

### charlotte-us.com
![Records](/assets/img/domain/charlotte-us-records.png)

**You only need to change the A and CNAME records**
- Record A: `charlotte-us.com` → `76.76.21.21`
- This should change to the IP of Netlify
- Record CNAME: `www.charlotte-us.com` → `cname.vercel-dns.com`
- This should change to the domain of Netlify

### miguediaz.com
![Records](/assets/img/domain/miguediaz-records.png)

**You only need to change the A and CNAME records**
- Record A: `miguediaz.com` → `76.76.21.21`
- This should change to the IP of Netlify
- Record CNAME: `www.miguediaz.com` → `cname.vercel-dns.com`
- This should change to the domain of Netlify

### jpdiaz.dev 
![Records](/assets/img/domain/jpdiaz-dev-records.png)

**You only need to change the A and CNAME records**
- Record A: `jpdiaz.dev` → `76.76.21.21`
- This should change to the IP of Netlify
- Record CNAME: `www.jpdiaz.dev` → `cname.vercel-dns.com`
- This should change to the domain of Netlify





----



