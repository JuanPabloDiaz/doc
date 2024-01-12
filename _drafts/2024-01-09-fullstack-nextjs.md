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

- Follow the video tutorial for the project: [Video Tutorial](https://youtu.be/nGoSP3MBV2E?t=4940)

- Follow the Get Started guide: [Next Auth - Get Started](https://next-auth.js.org/getting-started/example)

- Follow the Add API routes guide: [Next Auth - Add API routes for app](https://next-auth.js.org/configuration/initialization#route-handlers-app)

```bash
# src/app/api/auth/[...nextauth]/route.js

export function POST(req) {
  return Response.json("ok");
}
```

#### [Credentials (Provider)](https://next-auth.js.org/configuration/providers/credentials)

Replace the code in the file with:

```bash
# src/app/api/auth/[...nextauth]/route.js

import NextAuth from "next-auth"
import CredentialsProvider from "next-auth/providers/credentials"

const handler = NextAuth({
  providers: [
  CredentialsProvider({
    name: 'Credentials',
    credentials: {
      username: { label: "email", type: "email", placeholder: "test@example.com" },
      password: { label: "Password", type: "password" }
    },
    async authorize(credentials, req) {
      // You need to provide your own logic here that takes the credentials
      // submitted and returns either a object representing a user or value
      // that is false/null if the credentials are invalid.
      // e.g. return { id: 1, name: 'J Smith', email: 'jsmith@example.com' }
      // You can also use the `req` object to obtain additional parameters
      // (i.e., the request IP address)
      const res = await fetch("/your/endpoint", {
        method: 'POST',
        body: JSON.stringify(credentials),
        headers: { "Content-Type": "application/json" }
      })
      const user = await res.json()

      // If no error and we have user data, return it
      if (res.ok && user) {
        return user
      }
      // Return null if user data could not be retrieved
      return null
	}
	  })
  ]
})
```

### [MongoDB](https://www.mongodb.com/)

For the database, we will use [MongoDB](https://www.mongodb.com/).

```bash
yarn add mongodb
```

1. create a new project on [MongoDB](https://www.mongodb.com/)
2. Build a new database
3. Create a new user with admin privileges
4. save the password in a safe place _(.env file)_
5. add the IP address
   > Note: To include `Vercel IP` address in `MongoDB` network access, you can allow connections from all IP addresses by adding `0.0.0.0/0` to the IP Access List.

### [Mongoose](https://mongoosejs.com/)

For

[Mongoose](https://mongoosejs.com/).

```bash
yarn add mongoose
```

### [bcrypt](https://yarnpkg.com/package?q=bcrypt&name=bcrypt)

To hash the password, we will use [bcrypt](https://yarnpkg.com/package?q=bcrypt&name=bcrypt).

```bash
yarn add bcrypt
```

## Connect your project to MongoDB

Once you have created a new project on [MongoDB](https://www.mongodb.com/), you can connect your project to the database.

1. Go to `mongodb.com`, open `your project` > `database` and click on `Connect` button.
2. Click on `compass` tab and copy the `connection string`.

   > The `connection string` should look like this:

   ```bash
   mongodb+srv://<username>:<password>@<cluster-url>/<database>?retryWrites=true&w=majority
   ```

3. Create a new file in the root of the project called `.env.local` and add the following:

```bash
# .env
MONGODB_URI=mongodb+srv://<username>:<password>@<cluster-url>/<database>?retryWrites=true&w=majority
```

Replace the `username`, `password`, `cluster-url` and `database` with your own values.

Example:

```bash
# .env
MONGODB_URI="mongodb+srv://1diazdev:<password>@cluster0.37flgxy.mongodb.net/"
```

```bash
# src/app/api/auth/[...nextauth]/route.js
```
