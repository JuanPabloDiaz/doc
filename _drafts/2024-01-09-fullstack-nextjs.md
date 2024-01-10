---
layout: post
title: "Fullstack Food Ordering App with Next.js 14 (react.js, mongo, tailwind)"
date: 2024-01-09
author: juan
categories: fullstack
tags: nextjs reactjs tailwindcss mongodb
image: #/assets/img/featured-posts/code.jpg
---

## Create a new Next.js project with Next.js 14

Run the following command to create a new Next.js project:

```bash
yarn create next-app
```

Learn more: [Create next-app](https://nextjs.org/docs/api-reference/create-next-app)

Then, follow the instructions on the screen to create a new project.

```bash
What is your project named?  culinary-code
Would you like to use TypeScript?  `No` / Yes
Would you like to use ESLint?  No / `Yes`
Would you like to use Tailwind CSS?  No / `Yes`
Would you like to use `src/` directory?  No / `Yes`
Would you like to use App Router? (recommended)  No / `Yes`
Would you like to customize the default import alias (@/*)?  `No` / Yes
```

More info: [Next.js 14](https://nextjs.org/blog/next-14)

Run the project:

```bash
cd culinary-code
yarn dev
```

## Install plugins

### Prettier

```bash
yarn add --dev prettier prettier-plugin-tailwindcss
```

Then add the plugin to your Prettier configuration file:

```bash
# file name:    .prettierrc
{
  "plugins": ["prettier-plugin-tailwindcss"]
}
```

### Icons from Heroicons

Check out the icons from [Heroicons](https://heroicons.com/)

### [Next Auth](https://next-auth.js.org/)

For the authentication, we will use [Next Auth](https://next-auth.js.org/).

```bash
yarn add next-auth
```

Follow the Get Started guide: [Next Auth - Get Started](https://next-auth.js.org/getting-started/example)

Follow the Add API routes guide: [Next Auth - Add API routes](https://next-auth.js.org/getting-started/example#add-api-routes)

```bash
# src/app/api/auth/[...nextauth]/route.js

export function POST(req) {
  return Response.json("ok");
}

```

### [MongoDB](https://www.mongodb.com/)

For the database, we will use [MongoDB](https://www.mongodb.com/).

```bash
yarn add mongodb
```
