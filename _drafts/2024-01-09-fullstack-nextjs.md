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

### [Bcrypt](https://yarnpkg.com/package?q=bcrypt&name=bcrypt)

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
MONGODB_URL=mongodb+srv://<username>:<password>@<cluster-url>/<database>?retryWrites=true&w=majority
```

Replace the `username`, `password`, `cluster-url` and `database` with your own values.

Example:

```bash
# .env
MONGODB_URL="mongodb+srv://1diazdev:<password>@cluster0.37flgxy.mongodb.net/"
```

- Replace the `password` with your own value.
- Add the `.env` file to the .gitignore file.

> Remember to add something after the `.net/` in the `connection string`. if not, it will run as a test database (I believe).

### Password contains unescaped characters

The error message "Password contains unescaped characters" suggests that your MongoDB password contains special characters that need to be URL encoded.

In a MongoDB connection string, the password must be URL encoded if it contains any of the following characters: `/, ?, :, @, &, =, +, $, ,, #`.

#### Solution

Your MongoDB password contains special characters that need to be URL encoded.

You can use an online URL encoder to encode your password. Here's an example of how to encode your password:

1. Go to an online URL encoder, such as [ urlencoder.org](www.urlencoder.org).
2. Enter your password into the encoder.
3. Click "Encode".
4. Copy the encoded password.
5. Replace the password in your MONGODB_URL with the encoded password. The updated MONGODB_URL should look something like this:

   ```bash
   MONGODB_URL="mongodb+srv://1diazdev:encodedPassword@cluster0.37flgxy.mongodb.net/culinary-code"
   ```

6. Replace encodedPassword with the encoded password you got from the URL encoder.

> For more details. Follow the [Video Tutorial](https://youtu.be/nGoSP3MBV2E?t=5451)

Create the register route by creating a new file located at `src/app/api/register/route.js` and add the following:

```bash
# src/app/api/register/route.js
import { User } from "@/app/models/User";
import mongoose from "mongoose";

export async function POST(req) {
  const body = await req.json();
  const mongoDbUrl = process.env.MONGODB_URL;

  if (!mongoDbUrl) {
    throw new Error("The MONGODB_URL environment variable is not set.");
  }

  mongoose.connect(mongoDbUrl);
  const createdUser = await User.create(body);
  return Response.json(createdUser);
}
```

## Create modules for the app

For [Mongoose](https://mongoosejs.com/), we will create a new folder called `modules` in the `src` folder.

```bash
# src/modules/User.js
import { model, models, Schema } from "mongoose";

const UserSchema = new Schema(
  {
    name: { type: String },
    email: { type: String, required: true, unique: true },
    password: { type: String },
    image: { type: String },
  },
  { timestamps: true },
);

export const User = models?.User || model("User", UserSchema);
```
