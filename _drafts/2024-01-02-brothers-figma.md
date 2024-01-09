---
layout: post
title: "How to Run Sandar Project"
date: 2024-01-02
categories: 
tags: 
image: /assets/img/featured-posts/code4.jpg
pin: true
---


The Sandar project is the project that Miguel purchased from [https://ui8.net/](https://ui8.net/)

The project has the figma, HTML and React files.

## How to Run the project with Next.js and yarn

- You need to have yarn and next install on the pc

```bash
npm install --global yarn
npm install --global next
```

- Go to sandar-next

```bash
yarn install
```

- error?

```bash
opensslErrorStack: [ 'error:03000086:digital envelope routines::initialization error' ], library: 'digital envelope routines', reason: 'unsupported', code: 'ERR_OSSL_EVP_UNSUPPORTED' }

Node.js v18.17.0 error Command failed with exit code 1.
```

Solution:
To fix this issue, you can downgrade your Node.js to version 16 or below, which uses OpenSSL 1.1.1. You can use Node Version Manager (NVM) to easily switch between Node.js versions.


```bash
nvm install 16
nvm use 16
```

- Run

```bash
yarn built
yarn start
```