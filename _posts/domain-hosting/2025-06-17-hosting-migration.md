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
- DNS now points to Netlify at [jpdiaz.dev](https://jpdiaz.dev)
- Portfolio is live at [jpdiaz.netlify.app](https://jpdiaz.netlify.app)
- Vercel account is paused [jpdiaz.vercel.app](https://jpdiaz.vercel.app)

Next: switch the project to static generation, cache SSR, and block crawlers before re-deploying it safely.

---

## How to temporarily migrate your Hosting from Vercel to Netlify

1. Login to Netlify and Porkbun.
2. Go to Porkbun and save your records (A, CNAME, etc). I mean the records that point to your domain.

    ![Porkbun Records](/assets/img/domain/lujoymoda-records.png)

    **You only need to change the A and CNAME records**

    <h3>DNS Records Update</h3>

    | Tipo  | Host              | Vercel Value           | Netlify Value                 |
    | :---- | :---------------- | :--------------------- | :-------------------------- |
    | A     | lujoymoda.com     | 76.76.21.21            | **75.2.60.5** |
    | CNAME | www.lujoymoda.com | cname.vercel-dns.com   | **dyr.netlify.app** |
    | ALIAS | *.lujoymoda.com | cname.vercel-dns.com   | **apex-loadbalancer.netlify.com** |

3. Go to Netlify and create a new project with the repository you want to migrate.
4. Once the project is setup. Add a domain `lujoymoda.com` to the project.
5. Go to Porkbun and update the records to point to the new IP address of Netlify.
6. Wait for the DNS to propagate.
7. Visit `lujoymoda.com` to verify.

This experience reminded me of the importance of understanding how SSR impacts serverless costs. From now on, I’ll default to static generation when possible — and always back up my critical projects across providers.

----

## My DNS Configurations (Backup Records)

Before doing the migration, it's a good idea to save the DNS records.

<details>
<summary>JCDistributionCorp.com</summary>

<img src="/assets/img/domain/jcdistributioncorp-records.png" alt="JCDistributionCorp records">

<div>
    <strong>Records that you should NOT change:</strong>
    <ul>
      <li>MX records (email): fwd1.porkbun.com y fwd2.porkbun.com - KEEP IT THE SAME</li>
      <li>TXT record (SPF for email): El SPF para correo - KEEP IT THE SAME</li>
      <li>CNAME wildcard *.lujoymoda.com: OPTIONAL, but better keep it</li>
    </ul>
</div>

</details>

<details>
<summary>lujoymoda.com</summary>

<img src="/assets/img/domain/lujoymoda-records.png" alt="lujoymoda.com records">

**You only need to change the A and CNAME records**
- Record A: `lujoymoda.com` → `76.76.21.21`
- This should change to the IP of Netlify: `75.2.60.5`
- Record CNAME: `www.lujoymoda.com` → `cname.vercel-dns.com`
- This should change to the domain of Netlify: `dyr.netlify.app`

To learn more about how to migrate your Hosting from Vercel to Netlify, check out the [step by step guide](#step-by-step-guide)

</details>

<details>
<summary>talentoparati.com</summary>
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


**You only need to change 2 records**:

**Records to change:**
1. **Record A**: `talentoparati.com` → `76.76.21.21`
   - Change to the IP of Netlify: `75.2.60.5`
2. **Record CNAME**: `www.talentoparati.com` → `cname.vercel-dns.com`
   - Change to the domain of Netlify: `your-site.netlify.app`

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

</details>

<details>
<summary>charlotte-us.com</summary>

![Records](/assets/img/domain/charlotte-us-records.png)

**You only need to change the A and CNAME records**
- Record A: `charlotte-us.com` → `76.76.21.21`
- This should change to the IP of Netlify: `75.2.60.5`
- Record CNAME: `www.charlotte-us.com` → `cname.vercel-dns.com`
- This should change to the domain of Netlify: `charlotte-us.netlify.app`

</details>

<details>
<summary>miguediaz.com</summary>

**You only need to change the A and CNAME records**
- Record A: `miguediaz.com` → `76.76.21.21`
- This should change to the IP of Netlify: `75.2.60.5`
- Record CNAME: `www.miguediaz.com` → `cname.vercel-dns.com`
- This should change to the domain of Netlify: `madiaz.netlify.app`

</details>

<details>
<summary>jpdiaz.dev</summary>

<img src="/assets/img/domain/jpdiaz-records.png" alt="jpdiaz.dev records">
<img src="/assets/img/domain/jpdiaz-records2.png" alt="www.jpdiaz.dev records">

**You only need to change the A and CNAME records**
- Record A: `jpdiaz.dev` → `76.76.21.21`
- This should change to the IP of Netlify: `75.2.60.5`
- Record CNAME: `www.jpdiaz.dev` → `cname.vercel-dns.com`
- This should change to the domain of Netlify.

</details>

----

## Step by Step Guide

The above table is a summary of the changes you need to make. but here is a step by step guide using the example of `lujoymoda.com`

<details>
<summary>lujoymoda.com</summary>

<h3>1. Change the A record:</h3>
<ul>
  <li><strong>Type</strong>: A</li>
  <li><strong>Host</strong>: <code>lujoymoda.com</code></li>
  <li><strong>Value</strong>: Change from <code>76.76.21.21</code> → <code>75.2.60.5</code></li>
</ul>

<h3>2. Change the CNAME record of www:</h3>
<ul>
  <li><strong>Type</strong>: CNAME</li>
  <li><strong>Host</strong>: <code>www.lujoymoda.com</code></li>
  <li><strong>Value</strong>: Change from <code>cname.vercel-dns.com</code> → <code>apex-loadbalancer.netlify.com</code></li>
</ul>

<h2>Important:</h2>
<ul>
  <li><strong>DO NOT touch</strong> the MX records (email)</li>
  <li><strong>DO NOT touch</strong> the TXT (SPF)</li>
  <li><strong>DO NOT touch</strong> the wildcard <code>*.lujoymoda.com</code></li>
</ul>

<h2>After the change:</h2>
<ol>
  <li>Save the changes in your DNS</li>
  <li>Wait 5–30 minutes for propagation</li>
  <li>Visit <code>lujoymoda.com</code> to verify</li>
</ol>

</details>

## Conclusion

This experience taught me the importance of anticipating SSR costs and planning for redundancy. Going forward, I'll favor static builds, implement caching, and maintain multi-cloud backups to ensure reliability.