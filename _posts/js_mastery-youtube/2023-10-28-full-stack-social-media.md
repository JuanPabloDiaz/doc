---
layout: post
title: Full Stack Social Media App
date: 2023-10-28
categories: react
tags: react vite tailwind appwrite react-query
image: https://camo.githubusercontent.com/20115e5e8c49fa30a940add791a2a5e5623d991014cf104c0044df52f8209d4d/68747470733a2f2f692e6962622e636f2f6b3442517464502f5468756d626e61696c2e706e67
---

Build a modern social app with a stunning UI with a native mobile feel, a special tech stack, an infinite scroll feature, and amazing performance using React JS, Appwrite, TypeScript, and more.

#### [Demo]()

<!-- ABOUT THE PROJECT -->

This project was developed using

[![React](https://img.shields.io/badge/React-61DAFB.svg?style=for-the-badge&logo=React&logoColor=black)](https://www.w3schools.com/whatis/whatis_react.asp)
[![Vite](https://img.shields.io/badge/Vite-646CFF.svg?style=for-the-badge&logo=Vite&logoColor=white)](https://vitejs.dev//)
[![Appwrite](https://img.shields.io/badge/Appwrite-F02E65.svg?style=for-the-badge&logo=Appwrite&logoColor=white)](https://appwrite.io/)
[![TypeScript](https://img.shields.io/badge/TypeScript-3178C6.svg?style=for-the-badge&logo=TypeScript&logoColor=white)](https://www.typescriptlang.org/)
[![Tailwind](https://img.shields.io/badge/Tailwind%20CSS-06B6D4.svg?style=for-the-badge&logo=Tailwind-CSS&logoColor=white)](https://tailwindcss.com/)
[![React-Router](https://img.shields.io/badge/React%20Router-CA4245.svg?style=for-the-badge&logo=React-Router&logoColor=white)](https://reactrouter.com/en/main)
[![React-Query](https://img.shields.io/badge/React%20Query-FF4154.svg?style=for-the-badge&logo=React-Query&logoColor=white)](https://tanstack.com/query/v3/)
[![React-Hook-Form](https://img.shields.io/badge/React%20Hook%20Form-EC5990.svg?style=for-the-badge&logo=React-Hook-Form&logoColor=white)](https://react-hook-form.com/)

## 1. Create a React Project using Vite[^tutorial-vidio-1]

```bash
npm create vite@latest
```
```bash
npm install
npm run dev
```

- [Getting Started with Vite](https://vitejs.dev/guide/)

## 2. Customize the Project (SetUp)[^tutorial-vidio-2]

A. Starting Point Of The Project: `Delete` the `src` folder and create a new one with the files `App.tsx`, `main.tsx` and edit the files [(more info)](https://github.com/JuanPabloDiaz/socialMedia/commit/a537dd5495959114c2afa51767249d972c657b88)

B. Create a `global.css` file and add the tailwind classes that we will use in the project. [(more info)](https://github.com/JuanPabloDiaz/socialMedia/commit/63c49b3a8043f76157c9e84d7f3c3702e8f79fed) [(Github gist)](https://gist.github.com/adrianhajdin/4d2500bf5af601bbd9f4f596298d33ac)

C. [Install Tailwind in the project with Vite](https://tailwindcss.com/docs/guides/vite).

```bash
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```
> Note: it will show an error if I run the project at this point. the `bg-dark-1` and `font-Inter` needs to be install (step D) 

D. Modify the `tailwind.config` file by adding the info in the [Github gist](https://gist.github.com/adrianhajdin/4d2500bf5af601bbd9f4f596298d33ac)

  - Install the necesary plugins: 
  ```
  npm install -D tailwindcss-animate
  ```
  > Make sure to install the plugin and modify [(more info)](https://github.com/JuanPabloDiaz/socialMedia/commit/755a5aa625577a880d3b7b55ffac063e220236a2)

## 3. Routing[^tutorial-vidio-3]

### Install [React Router DOM](https://www.npmjs.com/package/react-router-dom#react-router-dom) [(repo details)](https://github.com/JuanPabloDiaz/socialMedia/commit/1a1e9f1263e4723f20a76587f319b1ae9cf54668)

```bash
npm i react-router-dom
```
### A. Edit the `main.tsx` file:

```tsx
import ReactDOM from "react-dom/client";
import { BrowserRouter } from "react-router-dom";
import App from "./App";

ReactDOM.createRoot(document.getElementById("root")!).render(
  <BrowserRouter>
    <App />
  </BrowserRouter>
);
```

### B. Edit the `App.tsx` file:

```tsx
import { Routes, Route } from "react-router-dom";

import "./globals.css";
import SigninForm from "./_auth/forms/SigninForm";
import SignupForm from "./_auth/forms/SignupForm";
import { Home } from "./_root/Pages";
import AuthLayout from "./_auth/AuthLayout";
import RootLayout from "./_root/RootLayout";

const App = () => {
  return (
    <main className="flex h-screen">
      <Routes>
        {/* Public Routes */}
          <Route path="/sign-in" element={<SigninForm />} />
          <Route path="/sign-up" element={<SignupForm />} />
        {/* Private Routes */}
          <Route index element={<Home />} />
      </Routes>
    </main>
  );
};

export default App;
```
## 4. File & Folder Structure[^tutorial-vidio-4]

### A. Create & edit the files:

<ol type="a">
  <li>Create two folders: <b>"src/_auth"</b> for the Public content: sign-in & register pages. <b>"src/_root"</b> for the Private content once the user sign in</li>
  <li>Create a <b>SinginForm.tsx</b> file in the path: <i>"src/_auth/forms/SinginForm.tsx"</i>. Edit the file using the <b>rafce</b> (reactArrowFunction). And Ensure to delete the <i>import React from 'react';</i></li>
  <li>Create a <b>SingupForm.tsx</b> file in the path: <i>"src/_auth/forms/SingupForm.tsx"</i>. Edit the file using the <b>rafce</b> (reactArrowFunction). And Ensure to delete the <i>import React from 'react';</i></li>
  <li>Create a <b>AuthLayout.tsx</b> file in the path: <i>"src/_auth/AuthLayout.tsx"</i>. Edit the file using the <b>rafce</b> (reactArrowFunction). And Ensure to delete the <i>import React from 'react';</i></li>
  <li>Create a <b>Home.tsx</b> file in the path: <i>"src/_root/pages/Home.tsx"</i>. Edit the file using the <b>rafce</b> (reactArrowFunction). And Ensure to delete the <i>import React from 'react';</i></li>
  <li>Create a <b>index.tsx</b> file in the path: <i>"src/_root/pages/index.tsx"</i>. Edit the file with the code: <code>export { default as Home } from "./Home";</code></li>
  <li>Create a <b>RootLayout.tsx</b> file in the path: <i>"src/_root/RootLayout.tsx"</i>. Edit the file using the <b>rafce</b> (reactArrowFunction). And Ensure to delete the <i>import React from 'react';</i></li>
</ol>

### B. Edit the `App.tsx` file:

```tsx
import { Routes, Route } from "react-router-dom";

import "./globals.css";
import SigninForm from "./_auth/forms/SigninForm";
import SignupForm from "./_auth/forms/SignupForm";
import { Home } from "./_root/Pages";
import AuthLayout from "./_auth/AuthLayout";
import RootLayout from "./_root/RootLayout";

const App = () => {
  return (
    <main className="flex h-screen">
      <Routes>
        {/* Public Routes */}
        <Route element={<AuthLayout />}>
          <Route path="/sign-in" element={<SigninForm />} />
          <Route path="/sign-up" element={<SignupForm />} />
        </Route>
        {/* Private Routes */}
        <Route element={<RootLayout />}>
          <Route index element={<Home />} />
        </Route>
      </Routes>
    </main>
  );
};

export default App;
```

## 5. Auth Pages[^tutorial-vidio-5]

### I. SetUp [Shadcn UI](https://ui.shadcn.com/) in the Project

#### a. Install [Shadcn UI](https://ui.shadcn.com/docs/installation/vite) for Vite. 

[Shadcn UI](https://ui.shadcn.com/). is a library with multiple designed components that you can copy and paste into your apps. Accessible. Customizable. Open Source. it will be use to style the page.
- Edit `tsconfig.json` file by adding the following code to the paths section:
```bash
{
  "compilerOptions": {
    // ...
    "baseUrl": ".",
    "paths": {
      "@/*": [
        "./src/*"
      ]
    }
    // ...
  }
}
```
> The [tsconfig.json](https://github.com/JuanPabloDiaz/socialMedia/blob/main/tsconfig.json) file should look like the one in the link.

#### b. Install Node.
```bash
npm i -D @types/node
``` 
#### c. Overwrite the `vite.config.ts` file:
```bash
import path from "path"
import react from "@vitejs/plugin-react"
import { defineConfig } from "vite"

export default defineConfig({
  plugins: [react()],
  resolve: {
    alias: {
      "@": path.resolve(__dirname, "./src"),
    },
  },
})
```
#### d. Run the shadcn-ui init command to setup your project:

```bash
npx shadcn-ui@latest init
```
#### e. Configure `components.json`

You will be asked a few questions to configure `components.json`:
```bash
Would you like to use TypeScript (recommended)? no / `yes`
Which style would you like to use? › `Default`
Which color would you like to use as base color? › `Slate`
Where is your global CSS file? › › `src/index.css`
Do you want to use CSS variables for colors? › no / `yes`
Where is your tailwind.config.js located? › `tailwind.config.js`
Configure the import alias for components: › `@/components`
Configure the import alias for utils: › `@/lib/utils`
Are you using React Server Components? › no / `yes` (no)
```
This will install all the necesary components

### II. Implement the AuthLayout Page

#### a. Delete the `public` folder and replace it with the info from [this new public](https://drive.google.com/file/d/13_7FofRAC3wARqPtAVPi53QNJJRd5RH_/view?usp=sharing) folder.

#### b. Modify the `AuthLayout.tsx` file

```tsx
import { Outlet, Navigate } from "react-router-dom";

const AuthLayout = () => {
  const isAutenticated = false;

  return (
    <>
      {isAutenticated ? (
        <Navigate to="/" />
      ) : (
        <>
          <section className="flex flex-1 justify-center items-center flex-col py-10">
            <Outlet />
          </section>
          <img
            src="/assets/images/side-img.svg"
            alt="side image"
            className="hidden xl:block h-screen w-1/2 object-cover bg-no-repeat"
          />
        </>
      )}
    </>
  );
};

export default AuthLayout;

```

#### c. Modify the `SignupForm.tsx` file

- Install the `button` component from shadcn:
  ```bash
  npx shadcn-ui@latest add button
  ```
- Copy and past to `SignupForm.tsx` file
  ```tsx
  import { Button } from "@/components/ui/button";

  const SignupForm = () => {
    return (
      <div>
        <Button>click me</Button>
      </div>
    );
  };

  export default SignupForm;
  ```
  confirm it works.

### III. Create the Form for the project (which has Form, input and label components)

#### a. Go to [Shadcn-ui Components forms](https://ui.shadcn.com/docs/components/form).
Follow the steps on the Shadcn-UI site and check the documentation for more details.

- Install form component
  ```bash
  npx shadcn-ui@latest add form
  ```
- Install input component
  ```bash
  npx shadcn-ui@latest add input
  ```
- Modify the `SignupForm.tsx` file

  ```jsx
  import * as z from "zod";
  import { zodResolver } from "@hookform/resolvers/zod";

  import {
    Form,
    FormControl,
    FormDescription,
    FormField,
    FormItem,
    FormLabel,
    FormMessage,
  } from "@/components/ui/form";
  import { Input } from "@/components/ui/input";

  import { Button } from "@/components/ui/button";
  import { useForm } from "react-hook-form";

  const formSchema = z.object({
    username: z.string().min(2).max(50),
  });

  const SignupForm = () => {
    // 1. Define your form.
    const form = useForm<z.infer<typeof formSchema>>({
      resolver: zodResolver(formSchema),
      defaultValues: {
        username: "",
      },
    });

    // 2. Define a submit handler.
    function onSubmit(values: z.infer<typeof formSchema>) {
      // Do something with the form values.
      // ✅ This will be type-safe and validated.
      console.log(values);
    }

    return (
      <div>
        <Form {...form}>
          <form onSubmit={form.handleSubmit(onSubmit)} className="space-y-8">
            <FormField
              control={form.control}
              name="username"
              render={({ field }) => (
                <FormItem>
                  <FormLabel>Username</FormLabel>
                  <FormControl>
                    <Input placeholder="shadcn" {...field} />
                  </FormControl>
                  <FormDescription>
                    This is your public display name.
                  </FormDescription>
                  <FormMessage />
                </FormItem>
              )}
            />
            <Button type="submit">Submit</Button>
          </form>
        </Form>
      </div>
    );
  };

  export default SignupForm;
  ```

  > This is a **basic** but powerful form.

- Create Reusable Components by extracting the `formSchema`

    a. Create an `index.ts` file in `src/lib/validation/index.ts`
    ```jsx
    import * as z from "zod";

    export const SignupValidation = z.object({
      name: z
        .string()
        .min(2, { message: "Name is too short" })
        .max(50, { message: "Name is too long" }),
      username: z
        .string()
        .min(2, { message: "Username is too short" })
        .max(50, { message: "Username is too short" }),
      email: z.string().email(),
      password: z
        .string()
        .min(8, { message: "Password must be at least 8 characters" })
        .max(60, { message: "Password is too long" }),
    });
    ```

     b. Modify the `SignupForm.tsx` file to reuse the validation section
     
     This will modify the functionality of form but not the apperience. 
    ```jsx
    import { zodResolver } from "@hookform/resolvers/zod";

    import {
      Form,
      FormControl,
      FormDescription,
      FormField,
      FormItem,
      FormLabel,
      FormMessage,
    } from "@/components/ui/form";
    import { Input } from "@/components/ui/input";

    import { Button } from "@/components/ui/button";
    import { useForm } from "react-hook-form";
    import { SignupValidation } from "@/lib/validation";
    import { z } from "zod";

    const SignupForm = () => {
      // 1. Define your form.
      const form = useForm<z.infer<typeof SignupValidation>>({
        resolver: zodResolver(SignupValidation),
        defaultValues: {
          name: "",
          username: "",
          email: "",
          password: "",
        },
      });

      // 2. Define a submit handler.
      function onSubmit(values: z.infer<typeof SignupValidation>) {
        // Do something with the form values.
        // ✅ This will be type-safe and validated.
        console.log(values);
      }

      return (
        <div>
          <Form {...form}>
            <form onSubmit={form.handleSubmit(onSubmit)} className="space-y-8">
              <FormField
                control={form.control}
                name="username"
                render={({ field }) => (
                  <FormItem>
                    <FormLabel>Username</FormLabel>
                    <FormControl>
                      <Input placeholder="shadcn" {...field} />
                    </FormControl>
                    <FormDescription>
                      This is your public display name.
                    </FormDescription>
                    <FormMessage />
                  </FormItem>
                )}
              />
              <Button type="submit">Submit</Button>
            </form>
          </Form>
        </div>
      );
    };

    export default SignupForm;
    ```

     c. Modify the `SignupForm.tsx` file to display the form section on the sign up page
    
    ```jsx
    import { zodResolver } from "@hookform/resolvers/zod";

    import {
      Form,
      FormControl,
      FormField,
      FormItem,
      FormLabel,
      FormMessage,
    } from "@/components/ui/form";
    import { Input } from "@/components/ui/input";

    import { Button } from "@/components/ui/button";
    import { useForm } from "react-hook-form";
    import { SignupValidation } from "@/lib/validation";
    import { z } from "zod";

    const SignupForm = () => {
      const isLoading = true;

      // 1. Define your form.
      const form = useForm<z.infer<typeof SignupValidation>>({
        resolver: zodResolver(SignupValidation),
        defaultValues: {
          name: "",
          username: "",
          email: "",
          password: "",
        },
      });

      // 2. Define a submit handler.
      function onSubmit(values: z.infer<typeof SignupValidation>) {
        // Do something with the form values.
        // ✅ This will be type-safe and validated.
        console.log(values);
      }

      return (
        <Form {...form}>
          <div className="sm:w-420 flex-center flex-col">
            <img src="/assets/images/logo.svg" alt="logo" />

            <h2 className="h3-bold md:h2-bold pt-5 sm:pt-12">
              Create a new account
            </h2>
            <p className="text-light-3 small-medium md:base-regular mt-2">
              To use Snapgram enter your details
            </p>

            <form
              onSubmit={form.handleSubmit(onSubmit)}
              className="flex flex-col gap-5 w-full mt-4"
            >
              <FormField
                control={form.control}
                name="name"
                render={({ field }) => (
                  <FormItem>
                    <FormLabel>Name</FormLabel>
                    <FormControl>
                      <Input type="text" className="shad-input" {...field} />
                    </FormControl>
                    <FormMessage />
                  </FormItem>
                )}
              />
              <FormField
                control={form.control}
                name="username"
                render={({ field }) => (
                  <FormItem>
                    <FormLabel>Username</FormLabel>
                    <FormControl>
                      <Input type="text" className="shad-input" {...field} />
                    </FormControl>
                    <FormMessage />
                  </FormItem>
                )}
              />
              <FormField
                control={form.control}
                name="email"
                render={({ field }) => (
                  <FormItem>
                    <FormLabel>Email</FormLabel>
                    <FormControl>
                      <Input type="email" className="shad-input" {...field} />
                    </FormControl>
                    <FormMessage />
                  </FormItem>
                )}
              />
              <FormField
                control={form.control}
                name="password"
                render={({ field }) => (
                  <FormItem>
                    <FormLabel>Password</FormLabel>
                    <FormControl>
                      <Input type="password" className="shad-input" {...field} />
                    </FormControl>
                    <FormMessage />
                  </FormItem>
                )}
              />
              <Button type="submit" className="shad-button_primary">
                {isLoading ? (
                  <div className="flex-center gap-2">Loading...</div>
                ) : (
                  "Sign up"
                )}
              </Button>
            </form>
          </div>
        </Form>
      );
    };

    export default SignupForm;
    ```
    
    d. The styles in the project were unintentionaly modify with the intalation of shadcn, go to the `global.css` file and overwrite it using the [previous global.css](https://github.com/JuanPabloDiaz/socialMedia/commit/63c49b3a8043f76157c9e84d7f3c3702e8f79fed) file.
    
    e. The `tailwind.config` file got modify too. Overwrite it using the [previous tailwind.config](https://gist.github.com/adrianhajdin/4d2500bf5af601bbd9f4f596298d33ac) file.


### IV. Add the Loader Component

#### a. Create the `Loader.tsx` file in the path: `src/components/shared/Loader.tsx` and copy the code:

  ```tsx
  const Loader = () => {
    return (
      <div className="flex-center w-full">
        <img src="/assets/icons/loader.svg" alt="loader" width={24} height={24} />
      </div>
    );
  };
  export default Loader;
  ```
  Include the Loader component to the `SignupForm.tsx` file:

  ```tsx
  import { zodResolver } from "@hookform/resolvers/zod";
  import { Link } from "react-router-dom";

  import {
    Form,
    FormControl,
    FormField,
    FormItem,
    FormLabel,
    FormMessage,
  } from "@/components/ui/form";
  import { Input } from "@/components/ui/input";

  import { Button } from "@/components/ui/button";
  import { useForm } from "react-hook-form";
  import { SignupValidation } from "@/lib/validation";
  import { z } from "zod";
  import Loader from "@/components/shared/Loader";

  const SignupForm = () => {
    const isLoading = false;

    // 1. Define your form.
    const form = useForm<z.infer<typeof SignupValidation>>({
      resolver: zodResolver(SignupValidation),
      defaultValues: {
        name: "",
        username: "",
        email: "",
        password: "",
      },
    });

    // 2. Define a submit handler.
    function onSubmit(values: z.infer<typeof SignupValidation>) {
      // Do something with the form values.
      // ✅ This will be type-safe and validated.
      console.log(values);
    }

    return (
      <Form {...form}>
        <div className="sm:w-420 flex-center flex-col">
          <img src="/assets/images/logo.svg" alt="logo" />

          <h2 className="h3-bold md:h2-bold pt-5 sm:pt-12">
            Create a new account
          </h2>
          <p className="text-light-3 small-medium md:base-regular mt-2">
            To use Snapgram, Please enter your details
          </p>

          <form
            onSubmit={form.handleSubmit(onSubmit)}
            className="flex flex-col gap-5 w-full mt-4"
          >
            <FormField
              control={form.control}
              name="name"
              render={({ field }) => (
                <FormItem>
                  <FormLabel>Name</FormLabel>
                  <FormControl>
                    <Input type="text" className="shad-input" {...field} />
                  </FormControl>
                  <FormMessage />
                </FormItem>
              )}
            />
            <FormField
              control={form.control}
              name="username"
              render={({ field }) => (
                <FormItem>
                  <FormLabel>Username</FormLabel>
                  <FormControl>
                    <Input type="text" className="shad-input" {...field} />
                  </FormControl>
                  <FormMessage />
                </FormItem>
              )}
            />
            <FormField
              control={form.control}
              name="email"
              render={({ field }) => (
                <FormItem>
                  <FormLabel>Email</FormLabel>
                  <FormControl>
                    <Input type="email" className="shad-input" {...field} />
                  </FormControl>
                  <FormMessage />
                </FormItem>
              )}
            />
            <FormField
              control={form.control}
              name="password"
              render={({ field }) => (
                <FormItem>
                  <FormLabel>Password</FormLabel>
                  <FormControl>
                    <Input type="password" className="shad-input" {...field} />
                  </FormControl>
                  <FormMessage />
                </FormItem>
              )}
            />
            <Button type="submit" className="shad-button_primary">
              {isLoading ? (
                <div className="flex-center gap-2">
                  <Loader />
                  Loading...
                </div>
              ) : (
                "Sign up"
              )}
            </Button>
            <p className="text-small-regular text-light-2 text-center mt-2">
              Already have an account?
              <Link
                to="/sign-in"
                className="text-primary-500 text-small-semibold ml-1"
              >
                Log in
              </Link>
            </p>
          </form>
        </div>
      </Form>
    );
  };

  export default SignupForm;
  ```
## 6. Auth Functionality[^tutorial-vidio-6]

### I. [Appwrite](https://cloud.appwrite.io/)

A. Install appwrite dependency
  ```bash
  npm install appwrite
  ```

B. Go to [cloud.appwrite.io](https://cloud.appwrite.io/), login with Github and create a new project.

C. In Appwrite, Copy the `Project ID` provided.

D. Create a `config.ts` file located in the path `src/lib/appwrite/config.ts` and add the code below:

```ts
import { Client, Account, Databases, Storage, Avatars } from "appwrite";

export const appwriteConfig = {
  projectId: import.meta.env.VITE_APPWRITE_PROJECT_ID,
};
```

E. Create a `.env.local` file **`OUTSIDE`** of the `src`. In the path `./.env.local` and add the code below:
> Warning: Make sure it's save at the `root` of the project and not in the `src` folder (I had issues bc I save it in the wrong place.)

```bash
VITE_APPWRITE_PROJECT_ID='YOUR_APPWRITE_PROJECT_ID'
```
> Replace the *'YOUR_APPWRITE_PROJECT_ID'* with your actual ID number.

F. Create a `vite-env.d.ts` file located in the path `src/vite-env.d.ts` and add the code below:

```ts
/// <reference types="vite/client" />
```

G. Modify the `config.ts` file

```ts
import { Client, Account, Databases, Storage, Avatars } from "appwrite";

export const appwriteConfig = {
  projectId: import.meta.env.VITE_APPWRITE_PROJECT_ID,
  url: import.meta.env.VITE_APPWRITE_URL,
};

export const client = new Client();

client.setProject(appwriteConfig.projectId);
client.setEndpoint(appwriteConfig.url);
export const account = new Account(client);
export const databases = new Databases(client);
export const storage = new Storage(client);
export const avatars = new Avatars(client);
```

H. Modify the `.env.local` file. Which should be located in the root of the project (`./.env.local`)
```bash
VITE_APPWRITE_PROJECT_ID='YOUR_APPWRITE_PROJECT_ID'
VITE_APPWRITE_URL='https://cloud.appwrite.io/v1'
```
> Replace the *'YOUR_APPWRITE_PROJECT_ID'* with your actual ID number.

- Learn More: [Appwrite user](https://appwrite.io/docs/references/cloud/server-nodejs/users) | [Appwrite React](https://appwrite.io/docs/quick-starts/react#step-4) | [.Env Variables](https://vitejs.dev/guide/env-and-mode.html)

I. Create a `api.ts` file in the path `src/lib/appwrite/api.ts`

```ts
import { ID } from "appwrite";
import { INewUser } from "@/types";
import { account } from "./config";

export async function createUserAccount(user: INewUser) {
  try {
    const newAccount = await account.create(
      ID.unique(),
      user.email,
      user.password,
      user.name
    );
    return newAccount;
  } catch (error) {
    console.log(error);
    return error;
  }
}
```

J. Create a `index.ts` file in the path `src/types/index.ts` and add the code from [Github gist](https://gist.github.com/adrianhajdin/4d2500bf5af601bbd9f4f596298d33ac)

```ts
export type INavLink = {
  imgURL: string;
  route: string;
  label: string;
};
export type IUpdateUser = {
  userId: string;
  name: string;
  bio: string;
  imageId: string;
  imageUrl: URL | string;
  file: File[];
};
export type INewPost = {
  userId: string;
  caption: string;
  file: File[];
  location?: string;
  tags?: string;
};
export type IUpdatePost = {
  postId: string;
  caption: string;
  imageId: string;
  imageUrl: URL;
  file: File[];
  location?: string;
  tags?: string;
};
export type IUser = {
  id: string;
  name: string;
  username: string;
  email: string;
  imageUrl: string;
  bio: string;
};
export type INewUser = {
  name: string;
  email: string;
  username: string;
  password: string;
};
```

K. Modify the `SignupForm.tsx` file

```jsx
import { zodResolver } from "@hookform/resolvers/zod";
import { Link } from "react-router-dom";

import {
  Form,
  FormControl,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from "@/components/ui/form";

import { Input } from "@/components/ui/input";

import { Button } from "@/components/ui/button";
import { useForm } from "react-hook-form";
import Loader from "@/components/shared/Loader";
import { SignupValidation } from "@/lib/validation";
import { z } from "zod";
import { createUserAccount } from "@/lib/appwrite/api";

const SignupForm = () => {
  const isLoading = false;

  // 1. Define your form.
  const form = useForm<z.infer<typeof SignupValidation>>({
    resolver: zodResolver(SignupValidation),
    defaultValues: {
      name: "",
      username: "",
      email: "",
      password: "",
    },
  });

  // 2. Define a submit handler.
  async function onSubmit(values: z.infer<typeof SignupValidation>) {
    const newUser = await createUserAccount(values);
    console.log(newUser);
  }

  return (
    <Form {...form}>
      <div className="sm:w-420 flex-center flex-col">
        <img src="/assets/images/logo.svg" alt="logo" />

        <h2 className="h3-bold md:h2-bold pt-5 sm:pt-12">
          Create a new account
        </h2>
        <p className="text-light-3 small-medium md:base-regular mt-2">
          To use Snapgram, Please enter your details
        </p>

        <form
          onSubmit={form.handleSubmit(onSubmit)}
          className="flex flex-col gap-5 w-full mt-4"
        >
          <FormField
            control={form.control}
            name="name"
            render={({ field }) => (
              <FormItem>
                <FormLabel>Name</FormLabel>
                <FormControl>
                  <Input type="text" className="shad-input" {...field} />
                </FormControl>
                <FormMessage />
              </FormItem>
            )}
          />
          <FormField
            control={form.control}
            name="username"
            render={({ field }) => (
              <FormItem>
                <FormLabel>Username</FormLabel>
                <FormControl>
                  <Input type="text" className="shad-input" {...field} />
                </FormControl>
                <FormMessage />
              </FormItem>
            )}
          />
          <FormField
            control={form.control}
            name="email"
            render={({ field }) => (
              <FormItem>
                <FormLabel>Email</FormLabel>
                <FormControl>
                  <Input type="email" className="shad-input" {...field} />
                </FormControl>
                <FormMessage />
              </FormItem>
            )}
          />
          <FormField
            control={form.control}
            name="password"
            render={({ field }) => (
              <FormItem>
                <FormLabel>Password</FormLabel>
                <FormControl>
                  <Input type="password" className="shad-input" {...field} />
                </FormControl>
                <FormMessage />
              </FormItem>
            )}
          />
          <Button type="submit" className="shad-button_primary">
            {isLoading ? (
              <div className="flex-center gap-2">
                <Loader />
                Loading...
              </div>
            ) : (
              "Sign up"
            )}
          </Button>
          <p className="text-small-regular text-light-2 text-center mt-2">
            Already have an account?
            <Link
              to="/sign-in"
              className="text-primary-500 text-small-semibold ml-1"
            >
              Log in
            </Link>
          </p>
        </form>
      </div>
    </Form>
  );
};

export default SignupForm;
```

L. Go to the Sign up page (`http://localhost:5173/Sign-up`) and fill out the form.

M. Go to the Auth tab in the [Appwrite](https://cloud.appwrite.io/) page to check that the new user has been created. (reload page if needed)

## 7. Storage & Database Design[^tutorial-vidio-7]

### I. [Storage](https://appwrite.io/docs/products/storage)

A. Go to the Storage tab in the [Appwrite](https://cloud.appwrite.io/) page, click on `Create bucket` and type `media` under the name of the bucket.

B. Copy the Storage ID (media) and paste it in the `./.env.local` file:

```bash
VITE_APPWRITE_URL='https://cloud.appwrite.io/v1'
VITE_APPWRITE_PROJECT_ID='YOUR_APPWRITE_PROJECT_ID'
VITE_APPWRITE_STORAGE_ID='YOUR_APPWRITE_STORAGE_ID'
```

### II. [Database](https://appwrite.io/docs/products/databases)

A. Go to the Database tab in the [Appwrite](https://cloud.appwrite.io/) page, click on `Create Database` and type `snapgram` under the name of the database. (no need to enter a database ID, it will be generated automaticaly)

B. Copy the Database ID (snapgram) and paste it in the `./.env.local` file:

```bash
VITE_APPWRITE_URL='https://cloud.appwrite.io/v1'
VITE_APPWRITE_PROJECT_ID='YOUR_APPWRITE_PROJECT_ID'
VITE_APPWRITE_STORAGE_ID='YOUR_APPWRITE_STORAGE_ID'
VITE_APPWRITE_DATABASE_ID='YOUR_APPWRITE_DATABASE_ID'
```

C. Under the new Database (snapgram), click on `Create Collection` and type `Posts` then create.

D. Go to `settings` (inside Posts) > `Permissions` > `+` > `Any` > check all the boxes > `update`.

E. Under the new Database (snapgram), click on `Create Collection` and type `Users` then create.

F. Go to `settings` (inside Users) > `Permissions` > `+` > `Any` > check all the boxes > `update`.

G. Under the new Database (snapgram), click on `Create Collection` and type `Saves` then create.

D. Go to `settings` (inside Saves) > `Permissions` > `+` > `Any` > check all the boxes > `update`.

### III. Database Relations in Appwrite[^tutorial-vidio-7a]...

A. **`Posts` Collection** > *`Relationship`*
1. Click the `Attributes` tab > `Create Attribute` > *`Relationship`*
2. **Relationship**,
    - Select `Two-Way Relationship`
    - Related Collection: `Users`
    - Attribute Key: `creator` (delete `users`)
    - Attribute Key(related collection): `posts`
    - Relation: `Many-to-One`
    - On deleting a document: `Null`
    - Create

B. **`Posts` Collection** > *`Relationship`*
1. Click the `Attributes` tab > `Create Attribute` > *`Relationship`*
2. **Relationship**,
    - Select `Two-Way Relationship`
    - Related Collection: `Users`
    - Attribute Key: `likes` (delete `users`)
    - Attribute Key(related collection): `liked`
    - Relation: `Many-to-Many`
    - On deleting a document: `Null`
    - Create

C. **`Posts` Collection** > *`String`*
1. Click the `Attributes` tab > `Create Attribute` > *`String`*
2. **String**,
    - Attribute Key: `caption`
    - size: `2200`
    - Default: `null`
    - Create

D. **`Posts` Collection** > *`String`*
1. Click the `Attributes` tab > `Create Attribute` > *`String`*
2. **String**,
    - Attribute Key: `tags`
    - size: `2200`
    - Default: `null`
    - `Array`
    - Create

E. **`Posts` Collection** > *`URL`*
1. Click the `Attributes` tab > `Create Attribute` > *`URL`*
2. **URL**,
    - Attribute Key: `imageUrl`
    - `Required`
    - Create

F. **`Posts` Collection** > *`String`*
1. Click the `Attributes` tab > `Create Attribute` > *`String`*
2. **String**,
    - Attribute Key: `imageId`
    - size: `2200`
    - `Required`
    - Create

G. **`Posts` Collection** > *`String`*
1. Click the `Attributes` tab > `Create Attribute` > *`String`*
2. **String**,
    - Attribute Key: `location`
    - size: `2200`
    - Create

----
#### Indexes tab:
Go to the indexes tab under Posts

H. **`Posts` Collection** > *`String`*
1. Click the `Indexes` tab > `Create index` > *`String`*
2. **String**,
    - Index Key: `caption`
    - Index type: `FullText`
    - Attribute: `caption`
    - Order: `DESC`
    - Create

---
#### Users:

I. **`Users` Collection** > *`String`*
1. Click the `Attributes` tab > `Create Attribute` > *`String`*
2. **String**,
    - Attribute Key: `name`
    - size: `2200`
    - Default: `null`
    - Create

J. **`Users` Collection** > *`String`*
1. Click the `Attributes` tab > `Create Attribute` > *`String`*
2. **String**,
    - Attribute Key: `username`
    - size: `2200`
    - Default: `null`
    - Create

K. **`Users` Collection** > *`String`*
1. Click the `Attributes` tab > `Create Attribute` > *`String`*
2. **String**,
    - Attribute Key: `accountId`
    - size: `2200`
    - Default: `null`
    - Required
    - Create

L. **`Users` Collection** > *`Email`*
1. Click the `Attributes` tab > `Create Attribute` > *`Email`*
2. **Email**,
    - Attribute Key: `email`
    - Required
    - Create

M. **`Users` Collection** > *`String`*
1. Click the `Attributes` tab > `Create Attribute` > *`String`*
2. **String**,
    - Attribute Key: `bio`
    - size: `2200`
    - Default: `null`
    - Create

N. **`Users` Collection** > *`String`*
1. Click the `Attributes` tab > `Create Attribute` > *`String`*
2. **String**,
    - Attribute Key: `imageId`
    - size: `2200`
    - Default: `null`
    - Create

O. **`Users` Collection** > *`URL`*
1. Click the `Attributes` tab > `Create Attribute` > *`URL`*
2. **URL**,
    - Attribute Key: `imageUrl`
    - `Required`
    - Create

---
#### Saves:

P. **`Saves` Collection** > *`Relationship`*
1. Click the `Attributes` tab > `Create Attribute` > *`Relationship`*
2. **Relationship**,
    - Select `Two-Way Relationship`
    - Related Collection: `Users`
    - Attribute Key: `user`
    - Attribute Key(related collection): `save`
    - Relation: `Many-to-One`
    - On deleting a document: `Null`
    - Create

P. **`Saves` Collection** > *`Relationship`*
1. Click the `Attributes` tab > `Create Attribute` > *`Relationship`*
2. **Relationship**,
    - Select `Two-Way Relationship`
    - Related Collection: `Posts`
    - Attribute Key: `post`
    - Attribute Key(related collection): `save`
    - Relation: `Many-to-One`
    - On deleting a document: `Null`
    - Create

### IV. Integrate

1. Go to Appwrite > Select the project > database Tab > Select the database just created (snapgram)

2. Copy the `collection ID` for `Saves`
3. Copy the `collection ID` for `Users`
4. Copy the `collection ID` for `Posts`
5. Paste them in the `./.env.local` file:

```bash
VITE_APPWRITE_URL='https://cloud.appwrite.io/v1'
VITE_APPWRITE_PROJECT_ID='YOUR_APPWRITE_PROJECT_ID'
VITE_APPWRITE_STORAGE_ID='YOUR_APPWRITE_STORAGE_ID'
VITE_APPWRITE_DATABASE_ID='YOUR_APPWRITE_DATABASE_ID'
VITE_APPWRITE_SAVES_COLLECTION_ID='YOUR_APPWRITE_SAVES_COLLECTION_ID'
VITE_APPWRITE_USER_COLLECTION_ID='YOUR_APPWRITE_USER_COLLECTION_ID'
VITE_APPWRITE_POST_COLLECTION_ID='YOUR_APPWRITE_POST_COLLECTION_ID'
```

6. Modify the `config.ts` file (`src/lib/appwrite/config.ts`)

```ts
import { Client, Account, Databases, Storage, Avatars } from "appwrite";

export const appwriteConfig = {
  url: import.meta.env.VITE_APPWRITE_URL,
  projectId: import.meta.env.VITE_APPWRITE_PROJECT_ID,
  databaseId: import.meta.env.VITE_APPWRITE_DATABASE_ID,
  storageId: import.meta.env.VITE_APPWRITE_STORAGE_ID,
  userCollectionId: import.meta.env.VITE_APPWRITE_USER_COLLECTION_ID,
  postCollectionId: import.meta.env.VITE_APPWRITE_POST_COLLECTION_ID,
  savesCollectionId: import.meta.env.VITE_APPWRITE_SAVES_COLLECTION_ID,
};

export const client = new Client();
// console.log(import.meta.env.MODE);

client.setEndpoint(appwriteConfig.url);
client.setProject(appwriteConfig.projectId);

console.log(appwriteConfig.url);
console.log(appwriteConfig.projectId);

export const account = new Account(client);
export const databases = new Databases(client);
export const storage = new Storage(client);
export const avatars = new Avatars(client);
```
> Warning: Double check that your config.ts (appwrite) are using the exact same names as your ENV.LOCAL variables.

> I had a `bug` When I sign up a user, the new account gets created on Appwrite. But I was only seeing it on the `Auth` section and not in the `database > users` section on Appwrite. (Resolved it by using the EXACT same variable names)


### V. Complete Back-End SetUp

6. Modify the `api.ts` file (`src/lib/appwrite/api.ts`)

```ts
import { ID } from "appwrite";

import { INewUser } from "@/types";
import { account, appwriteConfig, avatars, databases } from "./config";

export async function createUserAccount(user: INewUser) {
  try {
    const newAccount = await account.create(
      ID.unique(),
      user.email,
      user.password,
      user.name
    );

    if (!newAccount) throw Error;

    const avatarUrl = avatars.getInitials(user.name);

    const newUser = await saveUserToDB({
      accountId: newAccount.$id,
      email: newAccount.email,
      name: newAccount.name,
      username: user.username,
      imageUrl: avatarUrl,
    });

    return newUser;
  } catch (error) {
    console.log(error);
    return error;
  }
}

export async function saveUserToDB(user: {
  accountId: string;
  email: string;
  name: string;
  imageUrl: URL;
  username?: string;
}) {
  try {
    const newUser = await databases.createDocument(
      appwriteConfig.databaseId,
      appwriteConfig.userCollectionId,
      ID.unique(),
      user
    );
    return newUser;
  } catch (error) {
    console.log(error);
    return error;
  }
}
```

### VI. Add [Toast](https://ui.shadcn.com/docs/components/toast) Component from Shadcn UI

A. Install Toast
```bash
npx shadcn-ui@latest add toast
```

B. Modify the `App.tsx` 

```tsx
import { Routes, Route } from "react-router-dom";

import "./globals.css";
import SigninForm from "./_auth/forms/SigninForm";
import SignupForm from "./_auth/forms/SignupForm";
import { Home } from "./_root/Pages";
import AuthLayout from "./_auth/AuthLayout";
import RootLayout from "./_root/RootLayout";
import { Toaster } from "@/components/ui/toaster";

const App = () => {
  return (
    <main className="flex h-screen">
      <Routes>
        {/* Public Routes */}
        <Route element={<AuthLayout />}>
          <Route path="/sign-in" element={<SigninForm />} />
          <Route path="/sign-up" element={<SignupForm />} />
        </Route>
        {/* Private Routes */}
        <Route element={<RootLayout />}>
          <Route index element={<Home />} />
        </Route>
      </Routes>

      <Toaster />
    </main>
  );
};

export default App;
```

C. Modify the `SignUpForm.tsx` 

```tsx
import { zodResolver } from "@hookform/resolvers/zod";
import { Link } from "react-router-dom";

import { useToast } from "@/components/ui/use-toast";

import {
  Form,
  FormControl,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from "@/components/ui/form";

import { Input } from "@/components/ui/input";

import { Button } from "@/components/ui/button";
import { useForm } from "react-hook-form";
import Loader from "@/components/shared/Loader";
import { SignupValidation } from "@/lib/validation";
import { z } from "zod";
import { createUserAccount } from "@/lib/appwrite/api";

const SignupForm = () => {
  const { toast } = useToast();
  const isLoading = false;

  // 1. Define your form.
  const form = useForm<z.infer<typeof SignupValidation>>({
    resolver: zodResolver(SignupValidation),
    defaultValues: {
      name: "",
      username: "",
      email: "",
      password: "",
    },
  });

  // 2. Define a submit handler.
  async function onSubmit(values: z.infer<typeof SignupValidation>) {
    const newUser = await createUserAccount(values);

    if (!newUser) return;
    console.log(newUser);
    return toast({
      title: "Sign up failed. Please try again later.",
    });
  }

  // const session = await signInAccount();

  return (
    <Form {...form}>
      <div className="sm:w-420 flex-center flex-col">
        <img src="/assets/images/logo.svg" alt="logo" />

        <h2 className="h3-bold md:h2-bold pt-5 sm:pt-12">
          Create a new account
        </h2>
        <p className="text-light-3 small-medium md:base-regular mt-2">
          To use Snapgram, Please enter your details
        </p>

        <form
          onSubmit={form.handleSubmit(onSubmit)}
          className="flex flex-col gap-5 w-full mt-4"
        >
          <FormField
            control={form.control}
            name="name"
            render={({ field }) => (
              <FormItem>
                <FormLabel>Name</FormLabel>
                <FormControl>
                  <Input type="text" className="shad-input" {...field} />
                </FormControl>
                <FormMessage />
              </FormItem>
            )}
          />
          <FormField
            control={form.control}
            name="username"
            render={({ field }) => (
              <FormItem>
                <FormLabel>Username</FormLabel>
                <FormControl>
                  <Input type="text" className="shad-input" {...field} />
                </FormControl>
                <FormMessage />
              </FormItem>
            )}
          />
          <FormField
            control={form.control}
            name="email"
            render={({ field }) => (
              <FormItem>
                <FormLabel>Email</FormLabel>
                <FormControl>
                  <Input type="email" className="shad-input" {...field} />
                </FormControl>
                <FormMessage />
              </FormItem>
            )}
          />
          <FormField
            control={form.control}
            name="password"
            render={({ field }) => (
              <FormItem>
                <FormLabel>Password</FormLabel>
                <FormControl>
                  <Input type="password" className="shad-input" {...field} />
                </FormControl>
                <FormMessage />
              </FormItem>
            )}
          />
          <Button type="submit" className="shad-button_primary">
            {isLoading ? (
              <div className="flex-center gap-2">
                <Loader />
                Loading...
              </div>
            ) : (
              "Sign up"
            )}
          </Button>
          <p className="text-small-regular text-light-2 text-center mt-2">
            Already have an account?
            <Link
              to="/sign-in"
              className="text-primary-500 text-small-semibold ml-1"
            >
              Log in
            </Link>
          </p>
        </form>
      </div>
    </Form>
  );
};

export default SignupForm;
```
## 8. [TanStack Query](https://tanstack.com/query/latest) (React Query)[^tutorial-vidio-8]

### I. Install [React Query](https://www.npmjs.com/package/@tanstack/react-query)

```bash
npm install @tanstrack/react-query
```
### II. Create a `queriesAndMutations.ts` file 

Located in `src/lib/react-query/queriesAndMutations.ts` and copy the code below:

```ts
// Source code: https://github.com/adrianhajdin/social_media_app

import {
  useQuery,
  useMutation,
  useQueryClient,
  useInfiniteQuery,
} from "@tanstack/react-query";

import { createUserAccount, signInAccount } from "@/lib/appwrite/api";
import { INewUser } from "@/types";

export const useCreateUserAccount = () => {
  return useMutation({
    mutationFn: (user: INewUser) => createUserAccount(user),
  });
};

export const useSignInAccount = () => {
  return useMutation({
    mutationFn: (user: { email: string; password: string }) =>
      signInAccount(user),
  });
};
```

### IV. Modify the `SignupForm.tsx` file

```tsx
import { zodResolver } from "@hookform/resolvers/zod";
import { Link, useNavigate } from "react-router-dom";

import { useToast } from "@/components/ui/use-toast";

import {
  Form,
  FormControl,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from "@/components/ui/form";

import { Input } from "@/components/ui/input";

import { Button } from "@/components/ui/button";
import { useForm } from "react-hook-form";
import Loader from "@/components/shared/Loader";
import { SignupValidation } from "@/lib/validation";
import { z } from "zod";
import {
  useCreateUserAccount,
  useSignInAccount,
} from "@/lib/react-query/queriesAndMutations";
import { useUserContext } from "@/context/AuthContext";

const SignupForm = () => {
  const { toast } = useToast();
  const { checkAuthUser, isLoading: isUserLoading } = useUserContext();
  const navigate = useNavigate();

  const { mutateAsync: createUserAccount, isPending: isCreatingAccount } =
    useCreateUserAccount();

  const { mutateAsync: signInAccount, isPending: isSigningIn } =
    useSignInAccount();

  // 1. Define your form.
  const form = useForm<z.infer<typeof SignupValidation>>({
    resolver: zodResolver(SignupValidation),
    defaultValues: {
      name: "",
      username: "",
      email: "",
      password: "",
    },
  });

  // 2. Define a submit handler.
  async function onSubmit(values: z.infer<typeof SignupValidation>) {
    const newUser = await createUserAccount(values);

    if (!newUser) {
      return toast({
        title: "Sign up failed. Please try again later.",
      });
      // console.log(newUser);
    }

    const session = await signInAccount({
      email: values.email,
      password: values.password,
    });

    if (!session) {
      return toast({
        title: "Sign in failed. Please try again later.",
      });
    }

    const isLoggedIn = await checkAuthUser();

    if (isLoggedIn) {
      form.reset();

      navigate("/");
    } else {
      return toast({ title: "Sign up failed. Please try again later." });
    }
  }

  return (
    <Form {...form}>
      <div className="sm:w-420 flex-center flex-col">
        <img src="/assets/images/logo.svg" alt="logo" />

        <h2 className="h3-bold md:h2-bold pt-5 sm:pt-12">
          Create a new account
        </h2>
        <p className="text-light-3 small-medium md:base-regular mt-2">
          To use Snapgram, Please enter your details
        </p>

        <form
          onSubmit={form.handleSubmit(onSubmit)}
          className="flex flex-col gap-5 w-full mt-4"
        >
          <FormField
            control={form.control}
            name="name"
            render={({ field }) => (
              <FormItem>
                <FormLabel>Name</FormLabel>
                <FormControl>
                  <Input type="text" className="shad-input" {...field} />
                </FormControl>
                <FormMessage />
              </FormItem>
            )}
          />
          <FormField
            control={form.control}
            name="username"
            render={({ field }) => (
              <FormItem>
                <FormLabel>Username</FormLabel>
                <FormControl>
                  <Input type="text" className="shad-input" {...field} />
                </FormControl>
                <FormMessage />
              </FormItem>
            )}
          />
          <FormField
            control={form.control}
            name="email"
            render={({ field }) => (
              <FormItem>
                <FormLabel>Email</FormLabel>
                <FormControl>
                  <Input type="email" className="shad-input" {...field} />
                </FormControl>
                <FormMessage />
              </FormItem>
            )}
          />
          <FormField
            control={form.control}
            name="password"
            render={({ field }) => (
              <FormItem>
                <FormLabel>Password</FormLabel>
                <FormControl>
                  <Input type="password" className="shad-input" {...field} />
                </FormControl>
                <FormMessage />
              </FormItem>
            )}
          />
          <Button type="submit" className="shad-button_primary">
            {isCreatingAccount || isSigningIn || isUserLoading ? (
              <div className="flex-center gap-2">
                <Loader />
                Loading...
              </div>
            ) : (
              "Sign up"
            )}
          </Button>
          <p className="text-small-regular text-light-2 text-center mt-2">
            Already have an account?
            <Link
              to="/sign-in"
              className="text-primary-500 text-small-semibold ml-1"
            >
              Log in
            </Link>
          </p>
        </form>
      </div>
    </Form>
  );
};

export default SignupForm;
```

### V. Modify the `api.ts` file

Located in `src/lib/appwrite/api.ts`

```ts
// Source code: https://github.com/adrianhajdin/social_media_app

import { ID, Query } from "appwrite";

import { appwriteConfig, account, databases, avatars } from "./config";
import { INewUser } from "@/types";

export async function createUserAccount(user: INewUser) {
  try {
    const newAccount = await account.create(
      ID.unique(),
      user.email,
      user.password,
      user.name
    );

    if (!newAccount) throw Error;

    const avatarUrl = avatars.getInitials(user.name);

    const newUser = await saveUserToDB({
      accountId: newAccount.$id,
      email: newAccount.email,
      name: newAccount.name,
      username: user.username,
      imageUrl: avatarUrl,
    });

    return newUser;
  } catch (error) {
    console.log(error);
    return error;
  }
}

export async function saveUserToDB(user: {
  accountId: string;
  email: string;
  name: string;
  imageUrl: URL;
  username?: string;
}) {
  try {
    const newUser = await databases.createDocument(
      appwriteConfig.databaseId,
      appwriteConfig.userCollectionId,
      ID.unique(),
      user
    );
    return newUser;
  } catch (error) {
    console.log(error);
  }
}

export async function signInAccount(user: { email: string; password: string }) {
  try {
    const session = await account.createEmailSession(user.email, user.password);
    return session;
  } catch (error) {
    console.log(error);
  }
}

export async function getCurrentUser() {
  try {
    const currentAccount = await account.get();
    if (!currentAccount) throw Error;

    const currentUser = await databases.listDocuments(
      appwriteConfig.databaseId,
      appwriteConfig.userCollectionId,
      [Query.equal("accountId", currentAccount.$id)]
    );
    if (!currentUser) throw Error;
    return currentUser.documents[0];
  } catch (error) {
    console.log(error);
    return null;
  }
}
```

### VI. Create a `AuthContext.tsx` file

Located in `src/context/AuthContext.tsx`

```tsx
// Source code: https://github.com/adrianhajdin/social_media_app

import { getCurrentUser } from "@/lib/appwrite/api";
import { IContextType, IUser } from "@/types";
import { createContext, useContext, useEffect, useState } from "react";
import { useNavigate } from "react-router-dom";

export const INITIAL_USER = {
  id: "",
  name: "",
  username: "",
  email: "",
  imageUrl: "",
  bio: "",
};

const INITIAL_STATE = {
  user: INITIAL_USER,
  isLoading: false, //* check this line ---> isPending maybe
  isAuthenticated: false,
  setUser: () => {},
  setIsAuthenticated: () => {},
  checkAuthUser: async () => false as boolean,
};

const AuthContext = createContext<IContextType>(INITIAL_STATE);

export function AuthProvider({ children }: { children: React.ReactNode }) {
  const [user, setUser] = useState<IUser>(INITIAL_USER);
  const [isLoading, setIsLoading] = useState(false);
  const [isAuthenticated, setIsAuthenticated] = useState(false);

  const navigate = useNavigate();

  const checkAuthUser = async () => {
    setIsLoading(true);
    try {
      const currentAccount = await getCurrentUser();
      if (currentAccount) {
        setUser({
          id: currentAccount.$id,
          name: currentAccount.name,
          username: currentAccount.username,
          email: currentAccount.email,
          imageUrl: currentAccount.imageUrl,
          bio: currentAccount.bio,
        });
        setIsAuthenticated(true);
        return true;
      }
      return false;
    } catch (error) {
      console.log(error);
      return false;
    } finally {
      setIsLoading(false);
    }
  };

  useEffect(() => {
    if (
      localStorage.getItem("cookieFallback") === "[]" ||
      localStorage.getItem("cookieFallback") === null
    )
      navigate("/sign-in");

    checkAuthUser();
  }, []);

  const value = {
    user,
    setUser,
    isLoading,
    isAuthenticated,
    setIsAuthenticated,
    checkAuthUser,
  };

  return <AuthContext.Provider value={value}>{children}</AuthContext.Provider>;
}

export const useUserContext = () => useContext(AuthContext);
```

### VII. Modify the `main.tsx` file

Located in `src/main.tsx`

```tsx
// Source code: https://github.com/adrianhajdin/social_media_app

import ReactDOM from "react-dom/client";
import { BrowserRouter } from "react-router-dom";

import { AuthProvider } from "@/context/AuthContext";
import { QueryProvider } from "@/lib/react-query/QueryProvider";

import App from "./App";

ReactDOM.createRoot(document.getElementById("root")!).render(
  <BrowserRouter>
    <QueryProvider>
      <AuthProvider>
        <App />
      </AuthProvider>
    </QueryProvider>
  </BrowserRouter>
);
```

### VII. Create a `QueryProvider.tsx` file

Located in `src/lib/react-query/QueryProvider.tsx`

```tsx
// Source code: https://github.com/adrianhajdin/social_media_app

import React from "react";
import { QueryClientProvider, QueryClient } from "@tanstack/react-query";

const queryClient = new QueryClient();

export const QueryProvider = ({ children }: { children: React.ReactNode }) => {
  return (
    <QueryClientProvider client={queryClient}>{children}</QueryClientProvider>
  );
};
```

### VIII. Test the Sign up Section

A. Go to the http://localhost:5173/sign-up and fill out the form.

B. Check in [Appwrite](https://cloud.appwrite.io/) if the new account has been created.
- Under **Auth** > Users.
- Under **Databases** > snapgram > Users.

C. Debugging as needed

Debugging example from the [video](https://youtu.be/_W3R2VwRyF4?t=6975).

### IX. Modify the `SigninForm.tsx` file

Located in `src/_auth/forms/SigninForm.tsx`

```tsx
import { zodResolver } from "@hookform/resolvers/zod";
import { Link, useNavigate } from "react-router-dom";
import { useForm } from "react-hook-form";

import {
  Form, FormControl, FormField, FormItem, FormLabel, FormMessage,
} from "@/components/ui/form";
import { useToast } from "@/components/ui/use-toast";
import { Input } from "@/components/ui/input";
import { Button } from "@/components/ui/button";
import { SigninValidation } from "@/lib/validation";
import { z } from "zod";
import Loader from "@/components/shared/Loader";
import { useSignInAccount } from "@/lib/react-query/queriesAndMutations";
import { useUserContext } from "@/context/AuthContext";

const SigninForm = () => {
  const { toast } = useToast();
  const { checkAuthUser, isLoading: isUserLoading } = useUserContext();
  const navigate = useNavigate();

  const { mutateAsync: signInAccount } = useSignInAccount();

  // 1. Define your form.
  const form = useForm<z.infer<typeof SigninValidation>>({
    resolver: zodResolver(SigninValidation),
    defaultValues: {
      email: "",
      password: "",
    },
  });

  // 2. Define a submit handler.
  async function onSubmit(values: z.infer<typeof SigninValidation>) {
    const session = await signInAccount({
      email: values.email,
      password: values.password,
    });

    if (!session) {
      return toast({
        title: "Sign in failed. Please try again later.",
      });
    }

    const isLoggedIn = await checkAuthUser();

    if (isLoggedIn) {
      form.reset();

      navigate("/");
    } else {
      return toast({ title: "Sign in failed. Please try again later." });
    }
  }

  return (
    <Form {...form}>
      <div className="sm:w-420 flex-center flex-col">
        <img src="/assets/images/logo.svg" alt="logo" />

        <h2 className="h3-bold md:h2-bold pt-5 sm:pt-12">
          Log in to your account
        </h2>
        <p className="text-light-3 small-medium md:base-regular mt-2">
          Welcome back! Please enter your details to enjoy Snapgram
        </p>

        <form
          onSubmit={form.handleSubmit(onSubmit)}
          className="flex flex-col gap-5 w-full mt-4"
        >
          <FormField
            control={form.control}
            name="email"
            render={({ field }) => (
              <FormItem>
                <FormLabel>Email</FormLabel>
                <FormControl>
                  <Input type="email" className="shad-input" {...field} />
                </FormControl>
                <FormMessage />
              </FormItem>
            )}
          />
          <FormField
            control={form.control}
            name="password"
            render={({ field }) => (
              <FormItem>
                <FormLabel>Password</FormLabel>
                <FormControl>
                  <Input type="password" className="shad-input" {...field} />
                </FormControl>
                <FormMessage />
              </FormItem>
            )}
          />
          <Button type="submit" className="shad-button_primary">
            {isUserLoading ? (
              <div className="flex-center gap-2">
                <Loader />
                Loading...
              </div>
            ) : (
              "Sign in"
            )}
          </Button>
          <p className="text-small-regular text-light-2 text-center mt-2">
            Don't have an account?
            <Link
              to="/sign-up"
              className="text-primary-500 text-small-semibold ml-1"
            >
              Sign up
            </Link>
          </p>
        </form>
      </div>
    </Form>
  );
};

export default SigninForm;
```

### X. Modify the `index.ts` file

Located in `src/lib/validation/index.ts`

```ts
// Source code: https://github.com/adrianhajdin/social_media_app

import * as z from "zod";

export const SignupValidation = z.object({
  name: z
    .string()
    .min(2, { message: "Name is too short" })
    .max(50, { message: "Name is too long" }),
  username: z
    .string()
    .min(2, { message: "Username is too short" })
    .max(50, { message: "Username is too short" }),
  email: z.string().email(),
  password: z
    .string()
    .min(8, { message: "Password must be at least 8 characters" })
    .max(60, { message: "Password is too long" }),
});

export const SigninValidation = z.object({
  email: z.string().email(),
  password: z
    .string()
    .min(8, { message: "Password must be at least 8 characters" })
    .max(60, { message: "Password is too long" }),
});
```

## 9. HomePage[^tutorial-vidio-9]

### I. Modify the `RootLayout.tss` file 

Located in `src/_root/RootLayout.tsx` and copy the code below:

```tsx
// Source code: https://github.com/adrianhajdin/social_media_app

import Bottombar from "@/components/shared/Bottombar";
import LeftSidebar from "@/components/shared/LeftSidebar";
import Topbar from "@/components/shared/Topbar";

import { Outlet } from "react-router-dom";

const RootLayout = () => {
  return (
    <div className="w-full md:flex">
      <Topbar />
      <LeftSidebar />

      <section className="flex flex-1 h-full">
        <Outlet />
      </section>

      <Bottombar />
    </div>
  );
};

export default RootLayout;
```

- Create a Component name `Topbar.tsx` Located in `src/components/shared/Topbar.tsx` and run `rafce`.
-  Create a Component name `LeftSidebar.tsx` Located in `src/components/shared/LeftSidebar.tsx` and run `rafce`.
-  Create a Component name `Bottombar.tsx` Located in `src/components/shared/Bottombar.tsx` and run `rafce`.


### II. Modify Component: `Topbar.tsx` 

Located in `src/components/shared/Topbar.tsx`

```tsx
// Source code: https://github.com/adrianhajdin/social_media_app

import { Link, useNavigate } from "react-router-dom";
import { Button } from "../ui/button";
import { useSignOutAccount } from "@/lib/react-query/queriesAndMutations";
import { useEffect } from "react";
import { useUserContext } from "@/context/AuthContext";

const Topbar = () => {
  const { mutate: signOut, isSuccess } = useSignOutAccount();
  const navigate = useNavigate();
  const { user } = useUserContext();

  useEffect(() => {
    if (isSuccess) navigate(0);
  }, [isSuccess]);

  return (
    <section className="topbar">
      <div className="flex-between py-4 px-5">
        <Link to="/" className="flex gap-3 items-center">
          <img
            src="/assets/images/logo.svg"
            alt="logo"
            width={130}
            height={325}
          />
        </Link>

        <div className="flex gap-4">
          <Button
            variant="ghost"
            className="shad-button_ghost"
            onClick={() => signOut()}
          >
            <img src="/assets/icons/logout.svg" alt="logout" />
          </Button>
          <Link to={`/profile/${user.id}`} className="flex-center gap-3">
            <img
              src={user.imageUrl || "assets/images/profile.png"}
              alt="profile avatar"
              className="h-8 w-8 rounded-full"
            />
          </Link>
        </div>
      </div>
    </section>
  );
};

export default Topbar;
```

### III. Modify the `queriesAndMutations.ts`

Located in `src/lib/react-query/queriesAndMutations.ts`

```ts
// Source code: https://github.com/adrianhajdin/social_media_app

import {
  useQuery,
  useMutation,
  useQueryClient,
  useInfiniteQuery,
} from "@tanstack/react-query";

import {
  createUserAccount,
  signInAccount,
  signOutAccount,
} from "@/lib/appwrite/api";
import { INewUser } from "@/types";

export const useCreateUserAccount = () => {
  return useMutation({
    mutationFn: (user: INewUser) => createUserAccount(user),
  });
};

export const useSignInAccount = () => {
  return useMutation({
    mutationFn: (user: { email: string; password: string }) =>
      signInAccount(user),
  });
};

export const useSignOutAccount = () => {
  return useMutation({
    mutationFn: signOutAccount,
  });
};
```

### IV. Modify the `api.ts`

Located in `src/lib/appwrite/api.ts`

```ts
// Source code: https://github.com/adrianhajdin/social_media_app

import { ID, Query } from "appwrite";

import { appwriteConfig, account, databases, avatars } from "./config";
import { INewUser } from "@/types";

export async function createUserAccount(user: INewUser) {
  try {
    const newAccount = await account.create(
      ID.unique(),
      user.email,
      user.password,
      user.name
    );

    if (!newAccount) throw Error;

    const avatarUrl = avatars.getInitials(user.name);

    const newUser = await saveUserToDB({
      accountId: newAccount.$id,
      email: newAccount.email,
      name: newAccount.name,
      username: user.username,
      imageUrl: avatarUrl,
    });

    return newUser;
    console.log("new user created: " + newUser);
  } catch (error) {
    console.log(error);
    return error;
  }
}

export async function saveUserToDB(user: {
  accountId: string;
  email: string;
  name: string;
  imageUrl: URL;
  username?: string;
}) {
  try {
    const newUser = await databases.createDocument(
      appwriteConfig.databaseId,
      appwriteConfig.userCollectionId,
      ID.unique(),
      user
    );
    return newUser;
  } catch (error) {
    console.log(error);
  }
}

export async function signInAccount(user: { email: string; password: string }) {
  try {
    const session = await account.createEmailSession(user.email, user.password);
    return session;
  } catch (error) {
    console.log(error);
  }
}

export async function getCurrentUser() {
  try {
    const currentAccount = await account.get();
    if (!currentAccount) throw Error;

    const currentUser = await databases.listDocuments(
      appwriteConfig.databaseId,
      appwriteConfig.userCollectionId,
      [Query.equal("accountId", currentAccount.$id)]
    );
    if (!currentUser) throw Error;

    return currentUser.documents[0];
  } catch (error) {
    console.log(error);
    return null;
  }
}

export async function signOutAccount() {
  try {
    const session = await account.deleteSession("current");

    return session;
  } catch (error) {
    console.log(error);
  }
}
```

### V. Modify Component: `LeftSidebar.tsx` 

Located in `src/components/shared/LeftSidebar.tsx`

```tsx
// Source code: https://github.com/adrianhajdin/social_media_app

import { Link, NavLink, useNavigate, useLocation } from "react-router-dom";
import { Button } from "../ui/button";
import { useSignOutAccount } from "@/lib/react-query/queriesAndMutations";
import { useEffect } from "react";
import { useUserContext } from "@/context/AuthContext";
import { sidebarLinks } from "@/constants";
import { INavLink } from "@/types";

const LeftSidebar = () => {
  const { pathname } = useLocation();
  const { mutate: signOut, isSuccess } = useSignOutAccount();
  const navigate = useNavigate();
  const { user } = useUserContext();

  useEffect(() => {
    if (isSuccess) navigate(0);
  }, [isSuccess]);

  return (
    <nav className="leftsidebar">
      <div className="flex flex-col gap-11">
        <Link to="/" className="flex gap-3 items-center">
          <img
            src="/assets/images/logo.svg"
            alt="logo" width={170} height={36}
          />
        </Link>
        <Link to={`/profile/${user.id}`} className="flex gap-3 items-center">
          <img
            src={user.imageUrl || "/assets/icons/profile-placeholder.svg"}
            alt="profile" className="h-14 w-14 rounded-full"/>
          <div className="flex flex-col">
            <p className="body-bold">{user.name}</p>
            <p className="small-regular text-light-3">@{user.username}</p>
          </div>
        </Link>
        <ul className="flex flex-col gap-6">
          {sidebarLinks.map((link: INavLink) => {
            const isActive = pathname === link.route;
            return (
              <li
                key={link.label}
                className={`leftsidebar-link group ${
                  isActive && "bg-primary-500"
                }`}
              >
                <NavLink
                  to={link.route}
                  className="flex gap-4 items-center p-4"
                >
                  <img
                    src={link.imgURL}
                    alt={link.label}
                    className={`group-hover:invert-white ${
                      isActive && "invert-white"
                    }`}
                  />
                  {link.label}
                </NavLink>
              </li>
            );
          })}
        </ul>
      </div>
      <Button
        variant="ghost"
        className="shad-button_ghost"
        onClick={() => signOut()}
      >
        <img src="/assets/icons/logout.svg" alt="logout" />
        <p className="small-medium lg:base-medium">Logout</p>
      </Button>
    </nav>
  );
};

export default LeftSidebar;
```

### VI. Create a constants: `index.ts` file 

Located in `src/constants/index.ts` | From [(Github gist)](https://gist.github.com/adrianhajdin/4d2500bf5af601bbd9f4f596298d33ac)

```tsx
export const sidebarLinks = [
  {
    imgURL: "/assets/icons/home.svg",
    route: "/",
    label: "Home",
  },
  {
    imgURL: "/assets/icons/wallpaper.svg",
    route: "/explore",
    label: "Explore",
  },
  {
    imgURL: "/assets/icons/people.svg",
    route: "/all-users",
    label: "People",
  },
  {
    imgURL: "/assets/icons/bookmark.svg",
    route: "/saved",
    label: "Saved",
  },
  {
    imgURL: "/assets/icons/gallery-add.svg",
    route: "/create-post",
    label: "Create Post",
  },
];

export const bottombarLinks = [
  {
    imgURL: "/assets/icons/home.svg",
    route: "/",
    label: "Home",
  },
  {
    imgURL: "/assets/icons/wallpaper.svg",
    route: "/explore",
    label: "Explore",
  },
  {
    imgURL: "/assets/icons/bookmark.svg",
    route: "/saved",
    label: "Saved",
  },
  {
    imgURL: "/assets/icons/gallery-add.svg",
    route: "/create-post",
    label: "Create",
  },
];
```

### VII. Modify the `App.tsx` file 

Located in `src/App.tsx`

```tsx
// Source code: https://github.com/adrianhajdin/social_media_app

import { Routes, Route } from "react-router-dom";

import "./globals.css";
import SigninForm from "./_auth/forms/SigninForm";
import SignupForm from "./_auth/forms/SignupForm";
import { AllUsers, CreatePost, EditPost, Explore, Home, PostDetails, Profile, Saved, UpdateProfile, } from "./_root/Pages";
import AuthLayout from "./_auth/AuthLayout";
import RootLayout from "./_root/RootLayout";
import { Toaster } from "@/components/ui/toaster";

const App = () => {
  return (
    <main className="flex h-screen">
      <Routes>
        {/* Public Routes */}
        <Route element={<AuthLayout />}>
          <Route path="/sign-in" element={<SigninForm />} />
          <Route path="/sign-up" element={<SignupForm />} />
        </Route>
        {/* Private Routes */}
        <Route element={<RootLayout />}>
          <Route index element={<Home />} />
          <Route path="/explore" element={<Explore />} />
          <Route path="/saved" element={<Saved />} />
          <Route path="/all-users" element={<AllUsers />} />
          <Route path="/create-post" element={<CreatePost />} />
          <Route path="/update-post/:id" element={<EditPost />} />
          <Route path="/posts/:id" element={<PostDetails />} />
          <Route path="/profile/:id/*" element={<Profile />} />
          <Route path="/update-profile/:id" element={<UpdateProfile />} />
        </Route>
      </Routes>

      <Toaster />
    </main>
  );
};

export default App;
```

### VIII. Create multiple files under the pages folder and run `rafce`

1. Located on `src/_root/pages/`
2. Create a `Explore.tsx` file and run `rafce`.
3. Create a `Saved.tsx` file and run `rafce`.
4. Create a `CreatePost.tsx` file and run `rafce`.
5. Create a `Profile.tsx` file and run `rafce`.
6. Create a `UpdateProfile.tsx` file and run `rafce`.
7. Create a `EditPost.tsx` file and run `rafce`.
8. Create a `PostDetails.tsx` file and run `rafce`.
9. Create a `LikedPosts.tsx` file and run `rafce`.
10. Create a `AllUsers.tsx` file and run `rafce`.

> Delete `import React from "react";` from all the new files.

### IX. Modify the `index.ts` file on pages 

Located in `src/_root/pages/index.ts`

```ts
export { default as Home } from "./Home";
export { default as Explore } from "./Explore";
export { default as Saved } from "./Saved";
export { default as CreatePost } from "./CreatePost";
export { default as Profile } from "./Profile";
export { default as UpdateProfile } from "./UpdateProfile";
export { default as EditPost } from "./EditPost";
export { default as PostDetails } from "./PostDetails";
export { default as LikedPosts } from "./LikedPosts";
export { default as AllUsers } from "./AllUsers";
```

### IV. Modify Component: `Bottombar.tsx` 

Located in `src/components/shared/Bottombar.tsx`

```tsx
// Source code: https://github.com/adrianhajdin/social_media_app

import { bottombarLinks } from "@/constants";
import { Link, useLocation } from "react-router-dom";

const Bottombar = () => {
  const { pathname } = useLocation();
  return (
    <section className="bottom-bar">
      {bottombarLinks.map((link) => {
        const isActive = pathname === link.route;
        return (
          <Link
            to={link.route}
            key={link.label}
            className={`${
              isActive && "bg-primary-500 rounded-[10px]"
            } flex-center flex-col gap-1 p-2 transition`}
          >
            <img
              src={link.imgURL}
              alt={link.label}
              width={16}
              height={16}
              className={`${isActive && "invert-white"}`}
            />
            <p className="tiny-medium text-light-2">{link.label}</p>
          </Link>
        );
      })}
    </section>
  );
};

export default Bottombar;
```

## 10. Create Post[^tutorial-vidio-10]

### I. Open & Modify the `CreatePost.tsx` file 
Located in `src/_root/pages/CreatePost.tsx`

```tsx
// Source code: https://github.com/adrianhajdin/social_media_app

import PostForm from "@/components/forms/PostForm";

const CreatePost = () => {
  return (
    <div className="flex flex-1">
      <div className="common-container">
        <div className="max-w-5xl flex-start gap-3 justify-start w-full">
          <img
            src="/assets/icons/add-post.svg"
            width={36}
            height={36}
            alt="add"
          />
          <h2 className="h3-bold md:h2-bold text-left w-full">Create Post</h2>
        </div>

        <PostForm />
      </div>
    </div>
  );
};

export default CreatePost;
```

### II. Create a Component: `PostForm.tsx` 

Located in `src/components/forms/PostForm.tsx` and run `rafce`. Delete `import React from "react";`

- Go to [Shadcn-ui Components forms](https://ui.shadcn.com/docs/components/form).

Follow the steps on the Shadcn-UI site and check the documentation for more details.

- Install Textarea component from shadcn-ui

  ```bash 
  npx shadcn-ui@latest add textarea
  ```

The Components: `Form`, `input` & `button` should be already install.
- If not, please install them:
  ```bash
  npx shadcn-ui@latest add form
  
  npx shadcn-ui@latest add input
  ```

- Here is an example of a Basic form that could be use as a **_Form Template_**

```tsx
  import * as z from "zod";
  import { zodResolver } from "@hookform/resolvers/zod";

  import {
    Form,
    FormControl,
    FormDescription,
    FormField,
    FormItem,
    FormLabel,
    FormMessage,
  } from "@/components/ui/form";
  import { Input } from "@/components/ui/input";

  import { Button } from "@/components/ui/button";
  import { useForm } from "react-hook-form";

  const formSchema = z.object({
    username: z.string().min(2).max(50),
  });

  const FormTemplate = () => {
    // 1. Define your form.
    const form = useForm<z.infer<typeof formSchema>>({
      resolver: zodResolver(formSchema),
      defaultValues: {
        username: "",
      },
    });

    // 2. Define a submit handler.
    function onSubmit(values: z.infer<typeof formSchema>) {
      // Do something with the form values.
      // ✅ This will be type-safe and validated.
      console.log(values);
    }

    return (
      <div>
        <Form {...form}>
          <form onSubmit={form.handleSubmit(onSubmit)} className="space-y-8">
            <FormField
              control={form.control}
              name="username"
              render={({ field }) => (
                <FormItem>
                  <FormLabel>Username</FormLabel>
                  <FormControl>
                    <Input placeholder="shadcn" {...field} />
                  </FormControl>
                  <FormDescription>
                    This is your public display name.
                  </FormDescription>
                  <FormMessage />
                </FormItem>
              )}
            />
            <Button type="submit">Submit</Button>
          </form>
        </Form>
      </div>
    );
  };

  export default FormTemplate;
  ```

  > This is a **basic** but powerful form.

Modify the Component: `PostForm.tsx`. Located in `src/components/forms/PostForm.tsx`

```tsx
*************************** MODIFY POSTFORM BELOW ****************************
```
```tsx
// Source code: https://github.com/adrianhajdin/social_media_app

import { zodResolver } from "@hookform/resolvers/zod";
import { useForm } from "react-hook-form";
import * as z from "zod";

import { Button } from "@/components/ui/button";
import {
  Form,
  FormControl,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from "@/components/ui/form";
import { Input } from "@/components/ui/input";
import { Textarea } from "../ui/textarea";
import FileUploader from "../shared/FileUploader";
import { PostValidation } from "@/lib/validation";
import { Models } from "appwrite";
import { useCreatePost } from "@/lib/react-query/queriesAndMutations";
import { useUserContext } from "@/context/AuthContext";
import { useToast } from "../ui/use-toast";
import { useNavigate } from "react-router-dom";

type PostFormProps = {
  post?: Models.Document;
};

const PostForm = ({ post }: PostFormProps) => {
  const {
    mutateAsync: createPost,
    // isPending: isLoadingCreate
  } = useCreatePost();
  // Hooks:
  const { user } = useUserContext();
  const { toast } = useToast();
  const navigate = useNavigate();

  // 1. Define your form.
  const form = useForm<z.infer<typeof PostValidation>>({
    resolver: zodResolver(PostValidation),
    defaultValues: {
      caption: post ? post?.caption : "",
      file: [],
      location: post ? post?.location : "",
      tags: post ? post.tags.join(",") : "",
    },
  });

  // 2. Define a submit handler.
  async function onSubmit(values: z.infer<typeof PostValidation>) {
    const newPost = await createPost({
      ...values,
      userId: user.id,
    });

    // if NO new post, show error
    if (!newPost) {
      toast({
        title: "Please try again",
      });
    }
    // if new post, redirect to home page
    navigate("/");
  }

  return (
    <Form {...form}>
      <form
        onSubmit={form.handleSubmit(onSubmit)}
        className="flex flex-col gap-9 w-full max-w-5xl"
      >
        <FormField
          control={form.control}
          name="caption"
          render={({ field }) => (
            <FormItem>
              <FormLabel className="shad-form_label">Caption</FormLabel>
              <FormControl>
                <Textarea
                  className="shad-textarea custom-scrollbar"
                  {...field}
                />
              </FormControl>
              <FormMessage className="shad-form_message" />
            </FormItem>
          )}
        />
        <FormField
          control={form.control}
          name="file"
          render={({ field }) => (
            <FormItem>
              <FormLabel className="shad-form_label">Add Photos</FormLabel>
              <FormControl>
                <FileUploader
                  fieldChange={field.onChange}
                  mediaUrl={post?.imageUrl}
                />
              </FormControl>
              <FormMessage className="shad-form_message" />
            </FormItem>
          )}
        />
        <FormField
          control={form.control}
          name="location"
          render={({ field }) => (
            <FormItem>
              <FormLabel className="shad-form_label">Add Location</FormLabel>
              <FormControl>
                <Input type="text" className="shad-input" {...field} />
              </FormControl>
              <FormMessage className="shad-form_message" />
            </FormItem>
          )}
        />
        <FormField
          control={form.control}
          name="tags"
          render={({ field }) => (
            <FormItem>
              <FormLabel className="shad-form_label">
                Add Tags (separated by comma " , ")
              </FormLabel>
              <FormControl>
                <Input
                  type="text"
                  className="shad-input"
                  placeholder="JS, React, NextJS"
                  {...field}
                />
              </FormControl>
              <FormMessage className="shad-form_message" />
            </FormItem>
          )}
        />

        <div className="flex gap-4 items-center justify-end">
          <Button type="button" className="shad-button_dark_4">
            Cancel
          </Button>
          <Button
            type="submit"
            className="shad-button_primary whitespace-nowrap"
          >
            Submit
          </Button>
        </div>
      </form>
    </Form>
  );
};

export default PostForm;
```

### III. Create a Component: `FileUploader.tsx` 

Located in `src/_root/pages/CreatePost.tsx` and run `rafce`. Delete `import React from "react";`

- Install [React dropzone](https://www.npmjs.com/package/react-dropzone)
  ```tsx
  npm install react-dropzone
  ```

Modify the Component: `FileUploader.tsx` 
Located in `src/components/shared/FileUploader.tsx`

``` tsx
************************* MODIFY FILE UPLOADER BELOW *************************
```
```tsx
// Source code: https://github.com/adrianhajdin/social_media_app

import React, { useState, useCallback } from "react";
import { FileWithPath, useDropzone } from "react-dropzone";
import { Button } from "../ui/button";

type FileUploaderProps = {
  fieldChange: (FILES: File[]) => void;
  mediaUrl: string;
};

const FileUploader = ({ fieldChange,  mediaUrl}: FileUploaderProps) => {
  const [file, setFile] = useState<File[]>([]);
  const [fileUrl, setFileUrl] = useState(mediaUrl);

  const onDrop = useCallback(
    (acceptedFiles: FileWithPath[]) => {
      setFile(acceptedFiles);
      fieldChange(acceptedFiles);
      setFileUrl(URL.createObjectURL(acceptedFiles[0]));
    },
    [file]
  );

  const { getRootProps, getInputProps } = useDropzone({
    onDrop,
    accept: { "image/*": [".png", ".jpg", ".jpeg", ".svg"] },
  });

  return (
    <div
      {...getRootProps()}
      className="flex flex-center flex-col bg-dark-3 rounded-xl cursor-pointer"
    >
      <input {...getInputProps()} className="cursor-pointer" />
      {fileUrl ? (
        <>
          <div className="flex flex-1 justify-center w-full p-5 lg:p-10">
            <img
              src={fileUrl}
              alt="uploaded image"
              className="file_uploader-img"
            />
          </div>
          <p className="file_uploader-label">Click or drag photo to replace</p>
        </>
      ) : (
        <div className="file_uploader-box">
          <img
            src="/assets/icons/file-upload.svg"
            width={96}
            height={77}
            alt="file-upload"
          />
          <h3 className="base-medium text-light-2 mb-2 mt-6">
            Drag Photo here
          </h3>
          <p className="text-light-4 small-regular mb-6">SVG, PNG, JPG</p>
          <Button className="shad-button_dark_4">Browse from computer</Button>
        </div>
      )}
    </div>
  );
};

export default FileUploader;
```

### IV. Modify the Validation file: `index.ts`
Located in `src/lib/validation/index.ts`

```ts
// Source code: https://github.com/adrianhajdin/social_media_app

import * as z from "zod";

export const SignupValidation = z.object({
  name: z
    .string()
    .min(2, { message: "Name is too short" })
    .max(50, { message: "Name is too long" }),
  username: z
    .string()
    .min(2, { message: "Username is too short" })
    .max(50, { message: "Username is too short" }),
  email: z.string().email(),
  password: z
    .string()
    .min(8, { message: "Password must be at least 8 characters" })
    .max(60, { message: "Password is too long" }),
});

export const SigninValidation = z.object({
  email: z.string().email(),
  password: z
    .string()
    .min(8, { message: "Password must be at least 8 characters" })
    .max(60, { message: "Password is too long. Maximum 60 caracters" }),
});

export const PostValidation = z.object({
  caption: z
    .string()
    .min(5, { message: "Minimum 5 caracters" })
    .max(2200, { message: "Maximum 2,200 caracters" }),
  file: z.custom<File[]>(),
  location: z
    .string()
    .min(1, { message: "This field is required" })
    .max(100, { message: "This field is too long" }),
  tags: z.string(),
});
```


### V. Modify the `api.ts`
Located in `src/lib/appwrite/api.ts`

```ts
// Source code: https://github.com/adrianhajdin/social_media_app

import { ID, Query } from "appwrite";

import { appwriteConfig, account, databases, avatars, storage } from "./config";
import { INewPost, INewUser } from "@/types";

// ============================================================
// AUTH
// ============================================================

// ============================== SIGN UP
export async function createUserAccount(user: INewUser) {
  try {
    const newAccount = await account.create(
      ID.unique(),
      user.email,
      user.password,
      user.name
    );

    if (!newAccount) throw Error;

    const avatarUrl = avatars.getInitials(user.name);

    const newUser = await saveUserToDB({
      accountId: newAccount.$id,
      email: newAccount.email,
      name: newAccount.name,
      username: user.username,
      imageUrl: avatarUrl,
    });

    return newUser;
    console.log("new user created: " + newUser);
  } catch (error) {
    console.log(error);
    return error;
  }
}

// ============================== SAVE USER TO DB
export async function saveUserToDB(user: {
  accountId: string;
  email: string;
  name: string;
  imageUrl: URL;
  username?: string;
}) {
  try {
    const newUser = await databases.createDocument(
      appwriteConfig.databaseId,
      appwriteConfig.userCollectionId,
      ID.unique(),
      user
    );
    return newUser;
  } catch (error) {
    console.log(error);
  }
}

// ============================== SIGN IN
export async function signInAccount(user: { email: string; password: string }) {
  try {
    const session = await account.createEmailSession(user.email, user.password);
    return session;
  } catch (error) {
    console.log(error);
  }
}

// ============================== GET USER
export async function getCurrentUser() {
  try {
    const currentAccount = await account.get();
    if (!currentAccount) throw Error;

    const currentUser = await databases.listDocuments(
      appwriteConfig.databaseId,
      appwriteConfig.userCollectionId,
      [Query.equal("accountId", currentAccount.$id)]
    );
    if (!currentUser) throw Error;

    return currentUser.documents[0];
  } catch (error) {
    console.log(error);
    return null;
  }
}

// ============================== SIGN OUT
export async function signOutAccount() {
  try {
    const session = await account.deleteSession("current");

    return session;
  } catch (error) {
    console.log(error);
  }
}

// ============================================================
// POSTS
// ============================================================

// ============================== CREATE POST
export async function createPost(post: INewPost) {
  try {
    // *** Upload file to appwrite storage ***
    const uploadedFile = await uploadFile(post.file[0]);

    // If No file, throw error
    if (!uploadedFile) throw Error;

    // *** Get file url ***
    const fileUrl = getFilePreview(uploadedFile.$id);
    // If no file url, delete file from storage and throw error
    if (!fileUrl) {
      await deleteFile(uploadedFile.$id);
      throw Error;
    }

    // *** Convert tags into array ***
    const tags = post.tags?.replace(/ /g, "").split(",") || [];

    // *** Create post ***
    const newPost = await databases.createDocument(
      appwriteConfig.databaseId,
      appwriteConfig.postCollectionId,
      ID.unique(),
      {
        creator: post.userId,
        caption: post.caption,
        imageUrl: fileUrl,
        imageId: uploadedFile.$id,
        location: post.location,
        tags: tags,
      }
    );

    // If No New POST, delete file from storage
    if (!newPost) {
      await deleteFile(uploadedFile.$id);
      throw Error;
    }

    return newPost;
  } catch (error) {
    console.log(error);
  }
}

// ============================== UPLOAD FILE
export async function uploadFile(file: File) {
  try {
    const uploadedFile = await storage.createFile(
      appwriteConfig.storageId,
      ID.unique(),
      file
    );

    return uploadedFile;
  } catch (error) {
    console.log(error);
  }
}

// ============================== GET FILE URL
export function getFilePreview(fileId: string) {
  try {
    const fileUrl = storage.getFilePreview(
      appwriteConfig.storageId,
      fileId,
      2000,
      2000,
      "top",
      100
    );

    if (!fileUrl) throw Error;

    return fileUrl;
  } catch (error) {
    console.log(error);
  }
}

// ============================== DELETE FILE
export async function deleteFile(fileId: string) {
  try {
    await storage.deleteFile(appwriteConfig.storageId, fileId);

    return { status: "ok" };
  } catch (error) {
    console.log(error);
  }
}

// ============================== GET POPULAR POSTS (BY HIGHEST LIKE COUNT)
export async function getRecentPosts() {
  try {
    const posts = await databases.listDocuments(
      appwriteConfig.databaseId,
      appwriteConfig.postCollectionId,
      [Query.orderDesc("$createdAt"), Query.limit(20)]
    );

    if (!posts) throw Error;

    return posts;
  } catch (error) {
    console.log(error);
  }
}
```

### VI. Modify the `queriesAndMutations.ts` file 

Located in `src/lib/react-query/queriesAndMutations.ts`

```ts
// Source code: https://github.com/adrianhajdin/social_media_app

import {
  useQuery,
  useMutation,
  useQueryClient,
  // useInfiniteQuery,
} from "@tanstack/react-query";

import { QUERY_KEYS } from "@/lib/react-query/queryKeys";

import {
  createUserAccount,
  signInAccount,
  signOutAccount,
  createPost,
  getRecentPosts,
} from "@/lib/appwrite/api";
import { INewPost, INewUser } from "@/types";

// ============================================================
// AUTH QUERIES
// ============================================================

export const useCreateUserAccount = () => {
  return useMutation({
    mutationFn: (user: INewUser) => createUserAccount(user),
  });
};

export const useSignInAccount = () => {
  return useMutation({
    mutationFn: (user: { email: string; password: string }) =>
      signInAccount(user),
  });
};

export const useSignOutAccount = () => {
  return useMutation({
    mutationFn: signOutAccount,
  });
};
// ============================================================
// POST QUERIES
// ============================================================

export const useCreatePost = () => {
  const queryClient = useQueryClient();

  return useMutation({
    mutationFn: (post: INewPost) => createPost(post),
    onSuccess: () => {
      queryClient.invalidateQueries({
        queryKey: [QUERY_KEYS.GET_RECENT_POSTS],
      });
    },
  });
};

export const useGetRecentPosts = () => {
  return useQuery({
    queryKey: [QUERY_KEYS.GET_RECENT_POSTS],
    queryFn: getRecentPosts,
  });
};
```

### VII. Create a `queryKeys.ts` file

Located in `src/lib/react-query/queryKeys.ts`

```ts
export enum QUERY_KEYS {
  // AUTH KEYS
  CREATE_USER_ACCOUNT = "createUserAccount",

  // USER KEYS
  GET_CURRENT_USER = "getCurrentUser",
  GET_USERS = "getUsers",
  GET_USER_BY_ID = "getUserById",

  // POST KEYS
  GET_POSTS = "getPosts",
  GET_INFINITE_POSTS = "getInfinitePosts",
  GET_RECENT_POSTS = "getRecentPosts",
  GET_POST_BY_ID = "getPostById",
  GET_USER_POSTS = "getUserPosts",
  GET_FILE_PREVIEW = "getFilePreview",

  //  SEARCH KEYS
  SEARCH_POSTS = "getSearchPosts",
}
```
From [Github gist](https://gist.github.com/adrianhajdin/4d2500bf5af601bbd9f4f596298d33ac)
> [Learn more about Query Keys](https://tanstack.com/query/v4/docs/react/guides/query-keys)

### VIII. Appwrite Permissions

1. Go to Appwrite > Storage > media > Settings > Permissions > any > all checkmarks > update.

- [Keep watching video](https://youtu.be/_W3R2VwRyF4?t=12752)


### IX. Test Create Post

- [Testing this section](https://youtu.be/_W3R2VwRyF4?t=11801)

### X. Modify the `Home.tsx`

Located in `src/_root/pages/Home.tsx`
``` tsx
************************* MODIFY HOME BELOW *************************
```
```tsx
import Loader from "@/components/shared/Loader";
import PostCard from "@/components/shared/PostCard";
import { useGetRecentPosts } from "@/lib/react-query/queriesAndMutations";
import { Models } from "appwrite";

const Home = () => {
  // Hook:
  const {
    data: posts,
    isPending: isPostLoading,
    // isError: isErrorPosts,
  } = useGetRecentPosts();

  return (
    <div className="flex flex-1">
      <div className="home-container">
        <div className="home-posts">
          <h2 className="h3-bold md:h2-bold text-left w-full">Home Feed</h2>
          {isPostLoading && !posts ? (
            <Loader />
          ) : (
            <ul className="flex flex-col flex-1 gap-9 w-full">
              {posts?.documents.map((post: Models.Document) => (
                // <li>{post.caption}</li>
                <PostCard post={post} key={post.caption} />
              ))}
            </ul>
          )}
        </div>
      </div>
    </div>
  );
};

export default Home;
```

## 11. Post Card[^tutorial-vidio-11]

### I. Create Component: `PostCard.tsx`

Located in `src/components/shared/PostCard.tsx` and run `rafce`

```tsx
// import { formatDateString } from "@/lib/utils";
import { formatDistanceToNowStrict } from "date-fns";

import { Models } from "appwrite";
import { Link } from "react-router-dom";
import { useUserContext } from "@/context/AuthContext";
import PostStats from "./PostStats";

type PostCardProps = {
  post: Models.Document;
};
const PostCard = ({ post }: PostCardProps) => {
  const { user } = useUserContext();
  //   console.log("post:", post);

  if (!post.creator) return;

  return (
    <div className="post-card">
      <div className="flex-between">
        <div className="flex items-center gap-3">
          <Link to={`/profile/${post.creator.$id}`}>
            <img
              src={
                post?.creator?.imageUrl ||
                "/assets/icons/profile-placeholder.svg"
              }
              alt="creator"
              className="rounded-full w-12 lg:h-12"
            />
          </Link>
          <div className="flex flex-col">
            <p className="base-medium lg:body-bold text-light-1">
              {post.creator.name}
            </p>
            <div className="flex-center gap-2 text-light-3">
              <p className="subtle-semibold lg:small-regular">
                {/* {formatDateString(post.$createdAt)} */}
                {formatDistanceToNowStrict(new Date(post.$createdAt), {
                  addSuffix: true,
                })}
              </p>
              -
              <p className="subtle-semibold lg:small-regular">
                {post.location}
              </p>
            </div>
          </div>
        </div>
        <Link
          to={`/update-post/${post.$id}`}
          className={`${user.id !== post.creator.$id && "hidden"}`}
        >
          <img src="/assets/icons/edit.svg" alt="edit" width={20} height={20} />
        </Link>
      </div>
      <Link to={`/posts/${post.$id}`}>
        <div className="small-medium lg:base-medium py-5 ">
          <p>{post.caption}</p>
          <ul className="flex gap-1 mt-2">
            {post.tags.map((tag: string) => (
              <li key={tag} className="text-light-3">
                #{tag}
              </li>
            ))}
          </ul>
        </div>
        <img
          src={post.imageUrl || "/assets/icons/profile-placeholder.svg"}
          alt="post image"
          className="post-card_img"
        />
      </Link>
      <PostStats post={post} userId={user.id} />
    </div>
  );
};

export default PostCard;
```

#### A. Use ChatGPT or Copilot to create a function for you to modify the date string.

My Output:

It suggested me to...

1. Install the [date-fns](https://www.npmjs.com/package/date-fns) library by running:
    ```bash
    npm install date-fns --save
    ```
    > This will modify the string of date to a more human friendly readable date.

2. Then, you can import the `formatDistanceToNow` function and use it to format the `post.$createdAt` date. Here's how you can modify your code:
    ```ts
    import { formatDistanceToNow } from 'date-fns';

    // ...

    return (
      <div className="post-card">
        {/* ... */}
        <p className="subtle-semibold lg:small-regular">
          {formatDistanceToNowStrict(new Date(post.$createdAt), { addSuffix: true })}
        </p>
        {/* ... */}
      </div>
    );

    //  Input
    Date String = 2023-11-09T15:39:36.442+00:00
    
    // Output 
    3 hours ago
    ```
    [Learn More](https://date-fns.org/v2.30.0/docs/formatDistanceToNow)

#### B. Or Just use the code from [`utils.ts`](https://gist.github.com/adrianhajdin/4d2500bf5af601bbd9f4f596298d33ac)

Located in `src/lib/utils.ts`

```ts
// Code Source: https://gist.github.com/adrianhajdin/4d2500bf5af601bbd9f4f596298d33ac

import { type ClassValue, clsx } from "clsx";
import { twMerge } from "tailwind-merge";

export function cn(...inputs: ClassValue[]) {
  return twMerge(clsx(inputs));
}

export const convertFileToUrl = (file: File) => URL.createObjectURL(file);

export function formatDateString(dateString: string) {
  const options: Intl.DateTimeFormatOptions = {
    year: "numeric",
    month: "short",
    day: "numeric",
  };

  const date = new Date(dateString);
  const formattedDate = date.toLocaleDateString("en-US", options);

  const time = date.toLocaleTimeString([], {
    hour: "numeric",
    minute: "2-digit",
  });

  return `${formattedDate} at ${time}`;
}

// 
export const multiFormatDateString = (timestamp: string = ""): string => {
  const timestampNum = Math.round(new Date(timestamp).getTime() / 1000);
  const date: Date = new Date(timestampNum * 1000);
  const now: Date = new Date();

  const diff: number = now.getTime() - date.getTime();
  const diffInSeconds: number = diff / 1000;
  const diffInMinutes: number = diffInSeconds / 60;
  const diffInHours: number = diffInMinutes / 60;
  const diffInDays: number = diffInHours / 24;

  switch (true) {
    case Math.floor(diffInDays) >= 30:
      return formatDateString(timestamp);
    case Math.floor(diffInDays) === 1:
      return `${Math.floor(diffInDays)} day ago`;
    case Math.floor(diffInDays) > 1 && diffInDays < 30:
      return `${Math.floor(diffInDays)} days ago`;
    case Math.floor(diffInHours) >= 1:
      return `${Math.floor(diffInHours)} hours ago`;
    case Math.floor(diffInMinutes) >= 1:
      return `${Math.floor(diffInMinutes)} minutes ago`;
    default:
      return "Just now";
  }
};

export const checkIsLiked = (likeList: string[], userId: string) => {
  return likeList.includes(userId);
};
```

### II. Create `PostStats.tsx`

Located in `src/components/shared/PostStats.tsx` and run `rafce`

```tsx
import React, { useState, useEffect } from "react";
import {
  useLikePost,
  useSavePost,
  useDeleteSavedPost,
  useGetCurrentUser,
} from "@/lib/react-query/queriesAndMutations";
import { Models } from "appwrite";
import { checkIsLiked } from "@/lib/utils";
import Loader from "./Loader";

type PostStatsProps = {
  post: Models.Document;
  userId: string;
};

const PostStats = ({ post, userId }: PostStatsProps) => {
  const likesList = post.likes.map((user: Models.Document) => user.$id); // list of user ids who liked the post
  //  console.log("likesList:", likesList);

  // useState:
  const [likes, setLikes] = useState<string[]>(likesList); // list of user ids who liked the post
  const [isSaved, setIsSaved] = useState(false); // is the post saved by the current user?

  const { mutate: likePost } = useLikePost();
  const { mutate: savePost, isPending: isSavingPost } = useSavePost();
  const { mutate: deleteSavePost, isPending: isDeletingSaved } =
    useDeleteSavedPost();

  // who is the current user?
  const { data: currentUser } = useGetCurrentUser();

  const savedPostRecord = currentUser?.save.find(
    (record: Models.Document) => record.post.$id === post.$id
  );

  useEffect(() => {
    setIsSaved(savedPostRecord ? true : false); // or: setIsSaved(!!savedPostRecord);
    // { Saved: true } => !savedPostRecord => !false = true
    // { Saved: false } => !savedPostRecord => !true = false
  }, [currentUser]);

  const handleLikePost = (
    e: React.MouseEvent<HTMLImageElement, MouseEvent>
  ) => {
    e.stopPropagation();

    let likesArray = [...likes];

    const hasLiked = likesArray.includes(userId);

    if (hasLiked) {
      likesArray = likesArray.filter((Id) => Id !== userId);
    } else {
      likesArray.push(userId);
    }

    setLikes(likesArray);
    likePost({ postId: post.$id, likesArray });
  };

  const handleSavePost = (
    e: React.MouseEvent<HTMLImageElement, MouseEvent>
  ) => {
    e.stopPropagation();

    if (savedPostRecord) {
      setIsSaved(false);
      return deleteSavePost(savedPostRecord.$id);
    }

    savePost({ userId: userId, postId: post.$id });
    setIsSaved(true);
  };

  const containerStyles = location.pathname.startsWith("/profile")
    ? "w-full"
    : "";

  return (
    <div
      className={`flex justify-between items-center z-20 ${containerStyles}`}
    >
      <div className="flex gap-2 mr-5">
        <img
          src={`${
            checkIsLiked(likes, userId)
              ? "/assets/icons/liked.svg"
              : "/assets/icons/like.svg"
          }`}
          alt={checkIsLiked(likes, userId) ? "liked" : "like"}
          width={20}
          height={20}
          onClick={(e) => handleLikePost(e)}
          className="cursor-pointer"
        />

        <p className="small-medium lg:base-medium">{likes.length}</p>
      </div>

      <div className="flex gap-2">
        {isSavingPost || isDeletingSaved ? (
          <Loader />
        ) : (
          <img
            src={isSaved ? "/assets/icons/saved.svg" : "/assets/icons/save.svg"}
            alt="share"
            width={20}
            height={20}
            className="cursor-pointer"
            onClick={handleSavePost}
          />
        )}
      </div>
    </div>
  );
};

export default PostStats;
```

### III. Modify the `api.ts`
Located in `src/lib/appwrite/api.ts`

```ts
// Source code: https://github.com/adrianhajdin/social_media_app

import { ID, Query } from "appwrite";

import { appwriteConfig, account, databases, avatars, storage } from "./config";
import { INewPost, INewUser } from "@/types";

// ============================================================
// AUTH
// ============================================================

// ============================== SIGN UP
export async function createUserAccount(user: INewUser) {
  try {
    const newAccount = await account.create(
      ID.unique(),
      user.email,
      user.password,
      user.name
    );

    if (!newAccount) throw Error;

    const avatarUrl = avatars.getInitials(user.name);

    const newUser = await saveUserToDB({
      accountId: newAccount.$id,
      email: newAccount.email,
      name: newAccount.name,
      username: user.username,
      imageUrl: avatarUrl,
    });

    return newUser;
    console.log("new user created: " + newUser);
  } catch (error) {
    console.log(error);
    return error;
  }
}

// ============================== SAVE USER TO DB
export async function saveUserToDB(user: {
  accountId: string;
  email: string;
  name: string;
  imageUrl: URL;
  username?: string;
}) {
  try {
    const newUser = await databases.createDocument(
      appwriteConfig.databaseId,
      appwriteConfig.userCollectionId,
      ID.unique(),
      user
    );
    return newUser;
  } catch (error) {
    console.log(error);
  }
}

// ============================== SIGN IN
export async function signInAccount(user: { email: string; password: string }) {
  try {
    const session = await account.createEmailSession(user.email, user.password);
    return session;
  } catch (error) {
    console.log(error);
  }
}

// ============================== GET USER
export async function getCurrentUser() {
  try {
    const currentAccount = await account.get();
    if (!currentAccount) throw Error;

    const currentUser = await databases.listDocuments(
      appwriteConfig.databaseId,
      appwriteConfig.userCollectionId,
      [Query.equal("accountId", currentAccount.$id)]
    );
    if (!currentUser) throw Error;

    return currentUser.documents[0];
  } catch (error) {
    console.log(error);
    return null;
  }
}

// ============================== SIGN OUT
export async function signOutAccount() {
  try {
    const session = await account.deleteSession("current");

    return session;
  } catch (error) {
    console.log(error);
  }
}

// ============================================================
// POSTS
// ============================================================

// ============================== CREATE POST
export async function createPost(post: INewPost) {
  try {
    // *** Upload file to appwrite storage ***
    const uploadedFile = await uploadFile(post.file[0]);

    // If No file, throw error
    if (!uploadedFile) throw Error;

    // *** Get file url ***
    const fileUrl = getFilePreview(uploadedFile.$id);
    // If no file url, delete file from storage and throw error
    if (!fileUrl) {
      await deleteFile(uploadedFile.$id);
      throw Error;
    }

    // *** Convert tags into array ***
    const tags = post.tags?.replace(/ /g, "").split(",") || [];

    // *** Create post ***
    const newPost = await databases.createDocument(
      appwriteConfig.databaseId,
      appwriteConfig.postCollectionId,
      ID.unique(),
      {
        creator: post.userId,
        caption: post.caption,
        imageUrl: fileUrl,
        imageId: uploadedFile.$id,
        location: post.location,
        tags: tags,
      }
    );

    // If No New POST, delete file from storage
    if (!newPost) {
      await deleteFile(uploadedFile.$id);
      throw Error;
    }

    return newPost;
  } catch (error) {
    console.log(error);
  }
}

// ============================== UPLOAD FILE
export async function uploadFile(file: File) {
  try {
    const uploadedFile = await storage.createFile(
      appwriteConfig.storageId,
      ID.unique(),
      file
    );

    return uploadedFile;
  } catch (error) {
    console.log(error);
  }
}

// ============================== GET FILE URL
export function getFilePreview(fileId: string) {
  try {
    const fileUrl = storage.getFilePreview(
      appwriteConfig.storageId,
      fileId,
      2000,
      2000,
      "top",
      100
    );

    if (!fileUrl) throw Error;

    return fileUrl;
  } catch (error) {
    console.log(error);
  }
}

// ============================== DELETE FILE
export async function deleteFile(fileId: string) {
  try {
    await storage.deleteFile(appwriteConfig.storageId, fileId);

    return { status: "ok" };
  } catch (error) {
    console.log(error);
  }
}

// ============================== GET POPULAR POSTS (BY HIGHEST LIKE COUNT)
export async function getRecentPosts() {
  try {
    const posts = await databases.listDocuments(
      appwriteConfig.databaseId,
      appwriteConfig.postCollectionId,
      [Query.orderDesc("$createdAt"), Query.limit(20)]
    );

    if (!posts) throw Error;

    return posts;
  } catch (error) {
    console.log(error);
  }
}

// ============================== LIKE / UNLIKE POST
export async function likePost(postId: string, likesArray: string[]) {
  try {
    const updatedPost = await databases.updateDocument(
      appwriteConfig.databaseId,
      appwriteConfig.postCollectionId,
      postId,
      {
        likes: likesArray,
      }
    );
    // if there is no updated post, throw error
    if (!updatedPost) throw Error;

    return updatedPost;
  } catch (error) {
    console.log(error);
  }
}

// ============================== SAVE POST
export async function savePost(userId: string, postId: string) {
  try {
    const updatedPost = await databases.createDocument(
      appwriteConfig.databaseId,
      appwriteConfig.savesCollectionId,
      ID.unique(),
      {
        user: userId,
        post: postId,
      }
    );

    if (!updatedPost) throw Error;

    return updatedPost;
  } catch (error) {
    console.log(error);
  }
}

// ============================== DELETE SAVED POST
export async function deleteSavedPost(savedRecordId: string) {
  try {
    const statusCode = await databases.deleteDocument(
      appwriteConfig.databaseId,
      appwriteConfig.savesCollectionId,
      savedRecordId
    );

    if (!statusCode) throw Error;

    return { status: "Ok" };
  } catch (error) {
    console.log(error);
  }
}
```

### IV. Modify the `queriesAndMutations.ts` file 

Located in `src/lib/react-query/queriesAndMutations.ts`

```ts
// Source code: https://github.com/adrianhajdin/social_media_app

import {
  useQuery,
  useMutation,
  useQueryClient,
  // useInfiniteQuery,
} from "@tanstack/react-query";

import { QUERY_KEYS } from "@/lib/react-query/queryKeys";

import {
  createUserAccount,
  signInAccount,
  signOutAccount,
  createPost,
  getRecentPosts,
  likePost,
  savePost,
  deleteSavedPost,
  getCurrentUser,
} from "@/lib/appwrite/api";
import { INewPost, INewUser } from "@/types";

// ============================================================
// AUTH QUERIES
// ============================================================

export const useCreateUserAccount = () => {
  return useMutation({
    mutationFn: (user: INewUser) => createUserAccount(user),
  });
};

export const useSignInAccount = () => {
  return useMutation({
    mutationFn: (user: { email: string; password: string }) =>
      signInAccount(user),
  });
};

export const useSignOutAccount = () => {
  return useMutation({
    mutationFn: signOutAccount,
  });
};
// ============================================================
// POST QUERIES
// ============================================================

export const useCreatePost = () => {
  const queryClient = useQueryClient();

  return useMutation({
    mutationFn: (post: INewPost) => createPost(post),
    onSuccess: () => {
      queryClient.invalidateQueries({
        queryKey: [QUERY_KEYS.GET_RECENT_POSTS],
      });
    },
  });
};

export const useGetRecentPosts = () => {
  return useQuery({
    queryKey: [QUERY_KEYS.GET_RECENT_POSTS],
    queryFn: getRecentPosts,
  });
};

export const useLikePost = () => {
  const queryClient = useQueryClient();
  return useMutation({
    mutationFn: ({
      postId,
      likesArray,
    }: {
      postId: string;
      likesArray: string[];
    }) => likePost(postId, likesArray),
    onSuccess: (data) => {
      queryClient.invalidateQueries({
        queryKey: [QUERY_KEYS.GET_POST_BY_ID, data?.$id],
      });
      queryClient.invalidateQueries({
        queryKey: [QUERY_KEYS.GET_RECENT_POSTS],
      });
      queryClient.invalidateQueries({
        queryKey: [QUERY_KEYS.GET_POSTS],
      });
      queryClient.invalidateQueries({
        queryKey: [QUERY_KEYS.GET_CURRENT_USER],
      });
    },
  });
};

export const useSavePost = () => {
  const queryClient = useQueryClient();
  return useMutation({
    mutationFn: ({ userId, postId }: { userId: string; postId: string }) =>
      savePost(userId, postId),
    onSuccess: () => {
      queryClient.invalidateQueries({
        queryKey: [QUERY_KEYS.GET_RECENT_POSTS],
      });
      queryClient.invalidateQueries({
        queryKey: [QUERY_KEYS.GET_POSTS],
      });
      queryClient.invalidateQueries({
        queryKey: [QUERY_KEYS.GET_CURRENT_USER],
      });
    },
  });
};

export const useDeleteSavedPost = () => {
  const queryClient = useQueryClient();
  return useMutation({
    mutationFn: (savedRecordId: string) => deleteSavedPost(savedRecordId),
    onSuccess: () => {
      queryClient.invalidateQueries({
        queryKey: [QUERY_KEYS.GET_RECENT_POSTS],
      });
      queryClient.invalidateQueries({
        queryKey: [QUERY_KEYS.GET_POSTS],
      });
      queryClient.invalidateQueries({
        queryKey: [QUERY_KEYS.GET_CURRENT_USER],
      });
    },
  });
};

// ============================================================
// USER QUERIES
// ============================================================

export const useGetCurrentUser = () => {
  return useQuery({
    queryKey: [QUERY_KEYS.GET_CURRENT_USER],
    queryFn: getCurrentUser,
  });
};
```

## 12. Post CRUD[^tutorial-vidio-12]


### I. Modify the `EditPost.tsx`

Located in `src/_root/Pages/EditPost.tsx`

```tsx
import PostForm from "@/components/forms/PostForm";
import Loader from "@/components/shared/Loader";
import { useGetPostById } from "@/lib/react-query/queriesAndMutations";
import { useParams } from "react-router-dom";

const EditPost = () => {
  const { id } = useParams();
  const { data: post, isPending } = useGetPostById(id || "");

  if (isPending) {
    return <Loader />;
  }
  return (
    <div className="flex flex-1">
      <div className="common-container">
        <div className="max-w-5xl flex-start gap-3 justify-start w-full">
          <img
            src="/assets/icons/add-post.svg"
            width={36}
            height={36}
            alt="add"
          />
          <h2 className="h3-bold md:h2-bold text-left w-full">Edit Post</h2>
        </div>

        <PostForm action="Update" post={post} />
      </div>
    </div>
  );
};

export default EditPost;
```

### II. Modify the `CreatePost.tsx`

Located in `src/_root/Pages/CreatePost.tsx`

```tsx
import PostForm from "@/components/forms/PostForm";

const CreatePost = () => {
  return (
    <div className="flex flex-1">
      <div className="common-container">
        <div className="max-w-5xl flex-start gap-3 justify-start w-full">
          <img
            src="/assets/icons/add-post.svg"
            width={36}
            height={36}
            alt="add"
          />
          <h2 className="h3-bold md:h2-bold text-left w-full">Create Post</h2>
        </div>

        <PostForm action="Create" />
      </div>
    </div>
  );
};

export default CreatePost;

```

### III. Modify the `PostForm.tsx`

Located in `src/components/forms/PostForm.tsx`

```tsx
import { zodResolver } from "@hookform/resolvers/zod";
import { useForm } from "react-hook-form";
import * as z from "zod";

import { Button } from "@/components/ui/button";
import {
  Form,
  FormControl,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from "@/components/ui/form";
import { Input } from "@/components/ui/input";
import { Textarea } from "../ui/textarea";
import FileUploader from "../shared/FileUploader";
import { PostValidation } from "@/lib/validation";
import { Models } from "appwrite";
import {
  useCreatePost,
  useUpdatePost,
} from "@/lib/react-query/queriesAndMutations";
import { useUserContext } from "@/context/AuthContext";
import { useToast } from "../ui/use-toast";
import { useNavigate } from "react-router-dom";

type PostFormProps = {
  post?: Models.Document;
  action: "Create" | "Update";
};

const PostForm = ({ post, action }: PostFormProps) => {
  const { mutateAsync: createPost, isPending: isLoadingCreate } =
    useCreatePost();
  const { mutateAsync: updatePost, isPending: isLoadingUpdate } =
    useUpdatePost();
  // Hooks:
  const { user } = useUserContext();
  const { toast } = useToast();
  const navigate = useNavigate();

  // 1. Define your form.
  const form = useForm<z.infer<typeof PostValidation>>({
    resolver: zodResolver(PostValidation),
    defaultValues: {
      caption: post ? post?.caption : "",
      file: [],
      location: post ? post?.location : "",
      tags: post ? post.tags.join(",") : "",
    },
  });

  // 2. Define a submit handler.
  async function onSubmit(values: z.infer<typeof PostValidation>) {
    // if action is update, update post
    if (action === "Update") {
      const updatedPost = await updatePost({
        ...values,
        postId: post?.$id,
        imageId: post?.imageId,
        imageUrl: post?.imageUrl,
      });

      // if NO updated post, show error
      if (!updatedPost) {
        toast({
          title: "Please try again",
        });
      }
      // if updated post, redirect to post page
      return navigate("/posts/${post?.$id}");
    }
    // if it doesn't edit the post, create post
    const newPost = await createPost({
      ...values,
      userId: user.id,
    });

    // if NO new post, show error
    if (!newPost) {
      toast({
        title: "Please try again",
      });
    }
    // if new post, redirect to home page
    navigate("/");
  }
  console.log(post?.imageUrl);
  return (
    <Form {...form}>
      <form
        onSubmit={form.handleSubmit(onSubmit)}
        className="flex flex-col gap-9 w-full max-w-5xl"
      >
        <FormField
          control={form.control}
          name="caption"
          render={({ field }) => (
            <FormItem>
              <FormLabel className="shad-form_label">Caption</FormLabel>
              <FormControl>
                <Textarea
                  className="shad-textarea custom-scrollbar"
                  {...field}
                />
              </FormControl>
              <FormMessage className="shad-form_message" />
            </FormItem>
          )}
        />
        <FormField
          control={form.control}
          name="file"
          render={({ field }) => (
            <FormItem>
              <FormLabel className="shad-form_label">Add Photos</FormLabel>
              <FormControl>
                <FileUploader
                  fieldChange={field.onChange}
                  mediaUrl={post?.imageUrl}
                />
              </FormControl>
              <FormMessage className="shad-form_message" />
            </FormItem>
          )}
        />
        <FormField
          control={form.control}
          name="location"
          render={({ field }) => (
            <FormItem>
              <FormLabel className="shad-form_label">Add Location</FormLabel>
              <FormControl>
                <Input type="text" className="shad-input" {...field} />
              </FormControl>
              <FormMessage className="shad-form_message" />
            </FormItem>
          )}
        />
        <FormField
          control={form.control}
          name="tags"
          render={({ field }) => (
            <FormItem>
              <FormLabel className="shad-form_label">
                Add Tags (separated by comma " , ")
              </FormLabel>
              <FormControl>
                <Input
                  type="text"
                  className="shad-input"
                  placeholder="JS, React, NextJS"
                  {...field}
                />
              </FormControl>
              <FormMessage className="shad-form_message" />
            </FormItem>
          )}
        />

        <div className="flex gap-4 items-center justify-end">
          <Button type="button" className="shad-button_dark_4">
            Cancel
          </Button>
          <Button
            type="submit"
            className="shad-button_primary whitespace-nowrap"
            disabled={isLoadingCreate || isLoadingUpdate}
          >
            {isLoadingCreate || (isLoadingUpdate && "Loading...")}
            {action} Post
          </Button>
        </div>
      </form>
    </Form>
  );
};

export default PostForm;
```

### IV. Modify the `api.ts`
Located in `src/lib/appwrite/api.ts`

```ts
// Source code: https://github.com/adrianhajdin/social_media_app

import { ID, Query } from "appwrite";

import { appwriteConfig, account, databases, avatars, storage } from "./config";
import { INewPost, INewUser, IUpdatePost } from "@/types";

// ============================================================
// AUTH
// ============================================================

// ============================== SIGN UP
export async function createUserAccount(user: INewUser) {
  try {
    const newAccount = await account.create(
      ID.unique(),
      user.email,
      user.password,
      user.name
    );

    if (!newAccount) throw Error;

    const avatarUrl = avatars.getInitials(user.name);

    const newUser = await saveUserToDB({
      accountId: newAccount.$id,
      email: newAccount.email,
      name: newAccount.name,
      username: user.username,
      imageUrl: avatarUrl,
    });

    return newUser;
    console.log("new user created: " + newUser);
  } catch (error) {
    console.log(error);
    return error;
  }
}

// ============================== SAVE USER TO DB
export async function saveUserToDB(user: {
  accountId: string;
  email: string;
  name: string;
  imageUrl: URL;
  username?: string;
}) {
  try {
    const newUser = await databases.createDocument(
      appwriteConfig.databaseId,
      appwriteConfig.userCollectionId,
      ID.unique(),
      user
    );
    return newUser;
  } catch (error) {
    console.log(error);
  }
}

// ============================== SIGN IN
export async function signInAccount(user: { email: string; password: string }) {
  try {
    const session = await account.createEmailSession(user.email, user.password);
    return session;
  } catch (error) {
    console.log(error);
  }
}

// ============================== GET USER
export async function getCurrentUser() {
  try {
    const currentAccount = await account.get();
    if (!currentAccount) throw Error;

    const currentUser = await databases.listDocuments(
      appwriteConfig.databaseId,
      appwriteConfig.userCollectionId,
      [Query.equal("accountId", currentAccount.$id)]
    );
    if (!currentUser) throw Error;

    return currentUser.documents[0];
  } catch (error) {
    console.log(error);
    return null;
  }
}

// ============================== SIGN OUT
export async function signOutAccount() {
  try {
    const session = await account.deleteSession("current");

    return session;
  } catch (error) {
    console.log(error);
  }
}

// ============================================================
// POSTS
// ============================================================

// ============================== CREATE POST
export async function createPost(post: INewPost) {
  try {
    // *** Upload file to appwrite storage ***
    const uploadedFile = await uploadFile(post.file[0]);

    // If No file, throw error
    if (!uploadedFile) throw Error;

    // *** Get file url ***
    const fileUrl = getFilePreview(uploadedFile.$id);
    // If no file url, delete file from storage and throw error
    if (!fileUrl) {
      await deleteFile(uploadedFile.$id);
      throw Error;
    }

    // *** Convert tags into array ***
    const tags = post.tags?.replace(/ /g, "").split(",") || [];

    // *** Create post ***
    const newPost = await databases.createDocument(
      appwriteConfig.databaseId,
      appwriteConfig.postCollectionId,
      ID.unique(),
      {
        creator: post.userId,
        caption: post.caption,
        imageUrl: fileUrl,
        imageId: uploadedFile.$id,
        location: post.location,
        tags: tags,
      }
    );

    // If No New POST, delete file from storage
    if (!newPost) {
      await deleteFile(uploadedFile.$id);
      throw Error;
    }

    return newPost;
  } catch (error) {
    console.log(error);
  }
}

// ============================== UPLOAD FILE
export async function uploadFile(file: File) {
  try {
    const uploadedFile = await storage.createFile(
      appwriteConfig.storageId,
      ID.unique(),
      file
    );

    return uploadedFile;
  } catch (error) {
    console.log(error);
  }
}

// ============================== GET FILE URL
export function getFilePreview(fileId: string) {
  try {
    const fileUrl = storage.getFilePreview(
      appwriteConfig.storageId,
      fileId,
      2000,
      2000,
      "top",
      100
    );

    if (!fileUrl) throw Error;

    return fileUrl;
  } catch (error) {
    console.log(error);
  }
}

// ============================== DELETE FILE
export async function deleteFile(fileId: string) {
  try {
    await storage.deleteFile(appwriteConfig.storageId, fileId);

    return { status: "ok" };
  } catch (error) {
    console.log(error);
  }
}

// ============================== GET POPULAR POSTS (BY HIGHEST LIKE COUNT)
export async function getRecentPosts() {
  try {
    const posts = await databases.listDocuments(
      appwriteConfig.databaseId,
      appwriteConfig.postCollectionId,
      [Query.orderDesc("$createdAt"), Query.limit(20)]
    );

    if (!posts) throw Error;

    return posts;
  } catch (error) {
    console.log(error);
  }
}

// ============================== LIKE / UNLIKE POST
export async function likePost(postId: string, likesArray: string[]) {
  try {
    const updatedPost = await databases.updateDocument(
      appwriteConfig.databaseId,
      appwriteConfig.postCollectionId,
      postId,
      {
        likes: likesArray,
      }
    );
    // if there is no updated post, throw error
    if (!updatedPost) throw Error;

    return updatedPost;
  } catch (error) {
    console.log(error);
  }
}

// ============================== SAVE POST
export async function savePost(userId: string, postId: string) {
  try {
    const updatedPost = await databases.createDocument(
      appwriteConfig.databaseId,
      appwriteConfig.savesCollectionId,
      ID.unique(),
      {
        user: userId,
        post: postId,
      }
    );

    if (!updatedPost) throw Error;

    return updatedPost;
  } catch (error) {
    console.log(error);
  }
}

// ============================== DELETE SAVED POST
export async function deleteSavedPost(savedRecordId: string) {
  try {
    const statusCode = await databases.deleteDocument(
      appwriteConfig.databaseId,
      appwriteConfig.savesCollectionId,
      savedRecordId
    );

    if (!statusCode) throw Error;

    return { status: "Ok" };
  } catch (error) {
    console.log(error);
  }
}

// ============================== GET POST BY ID
export async function getPostById(postId?: string) {
  if (!postId) throw Error;

  try {
    const post = await databases.getDocument(
      appwriteConfig.databaseId,
      appwriteConfig.postCollectionId,
      postId
    );

    if (!post) throw Error;

    return post;
  } catch (error) {
    console.log(error);
  }
}

// ============================== UPDATE POST
export async function updatePost(post: IUpdatePost) {
  const hasFileToUpdate = post.file.length > 0;

  try {
    let image = {
      imageUrl: post.imageUrl,
      imageId: post.imageId,
    };

    if (hasFileToUpdate) {
      // Upload new file to appwrite storage
      const uploadedFile = await uploadFile(post.file[0]);
      if (!uploadedFile) throw Error;

      // Get new file url
      const fileUrl = getFilePreview(uploadedFile.$id);
      if (!fileUrl) {
        await deleteFile(uploadedFile.$id);
        throw Error;
      }

      image = { ...image, imageUrl: fileUrl, imageId: uploadedFile.$id };
    }

    // Convert tags into array
    const tags = post.tags?.replace(/ /g, "").split(",") || [];

    //  Update post
    const updatedPost = await databases.updateDocument(
      appwriteConfig.databaseId,
      appwriteConfig.postCollectionId,
      post.postId,
      {
        caption: post.caption,
        imageUrl: image.imageUrl,
        imageId: image.imageId,
        location: post.location,
        tags: tags,
      }
    );

    // Failed to update
    if (!updatedPost) {
      // Delete new file that has been recently uploaded
      if (hasFileToUpdate) {
        await deleteFile(image.imageId);
      }

      // If no new file uploaded, just throw error
      throw Error;
    }

    // Safely delete old file after successful update
    if (hasFileToUpdate) {
      await deleteFile(post.imageId);
    }

    return updatedPost;
  } catch (error) {
    console.log(error);
  }
}

// ============================== DELETE POST
export async function deletePost(postId?: string, imageId?: string) {
  if (!postId || !imageId) return;

  try {
    const statusCode = await databases.deleteDocument(
      appwriteConfig.databaseId,
      appwriteConfig.postCollectionId,
      postId
    );

    if (!statusCode) throw Error;

    await deleteFile(imageId);

    return { status: "Ok" };
  } catch (error) {
    console.log(error);
  }
}
```

### V. Modify the `queriesAndMutations.ts` file 

Located in `src/lib/react-query/queriesAndMutations.ts`

```ts
// Source code: https://github.com/adrianhajdin/social_media_app

import {
  useQuery,
  useMutation,
  useQueryClient,
  // useInfiniteQuery,
} from "@tanstack/react-query";

import { QUERY_KEYS } from "@/lib/react-query/queryKeys";

import {
  createUserAccount,
  signInAccount,
  signOutAccount,
  createPost,
  getRecentPosts,
  likePost,
  savePost,
  deleteSavedPost,
  getCurrentUser,
  getPostById,
  updatePost,
  deletePost,
} from "@/lib/appwrite/api";
import { INewPost, INewUser, IUpdatePost } from "@/types";

// ============================================================
// AUTH QUERIES
// ============================================================

export const useCreateUserAccount = () => {
  return useMutation({
    mutationFn: (user: INewUser) => createUserAccount(user),
  });
};

export const useSignInAccount = () => {
  return useMutation({
    mutationFn: (user: { email: string; password: string }) =>
      signInAccount(user),
  });
};

export const useSignOutAccount = () => {
  return useMutation({
    mutationFn: signOutAccount,
  });
};
// ============================================================
// POST QUERIES
// ============================================================

export const useCreatePost = () => {
  const queryClient = useQueryClient();

  return useMutation({
    mutationFn: (post: INewPost) => createPost(post),
    onSuccess: () => {
      queryClient.invalidateQueries({
        queryKey: [QUERY_KEYS.GET_RECENT_POSTS],
      });
    },
  });
};

export const useGetRecentPosts = () => {
  return useQuery({
    queryKey: [QUERY_KEYS.GET_RECENT_POSTS],
    queryFn: getRecentPosts,
  });
};

export const useLikePost = () => {
  const queryClient = useQueryClient();
  return useMutation({
    mutationFn: ({
      postId,
      likesArray,
    }: {
      postId: string;
      likesArray: string[];
    }) => likePost(postId, likesArray),
    onSuccess: (data) => {
      queryClient.invalidateQueries({
        queryKey: [QUERY_KEYS.GET_POST_BY_ID, data?.$id],
      });
      queryClient.invalidateQueries({
        queryKey: [QUERY_KEYS.GET_RECENT_POSTS],
      });
      queryClient.invalidateQueries({
        queryKey: [QUERY_KEYS.GET_POSTS],
      });
      queryClient.invalidateQueries({
        queryKey: [QUERY_KEYS.GET_CURRENT_USER],
      });
    },
  });
};

export const useSavePost = () => {
  const queryClient = useQueryClient();
  return useMutation({
    mutationFn: ({ userId, postId }: { userId: string; postId: string }) =>
      savePost(userId, postId),
    onSuccess: () => {
      queryClient.invalidateQueries({
        queryKey: [QUERY_KEYS.GET_RECENT_POSTS],
      });
      queryClient.invalidateQueries({
        queryKey: [QUERY_KEYS.GET_POSTS],
      });
      queryClient.invalidateQueries({
        queryKey: [QUERY_KEYS.GET_CURRENT_USER],
      });
    },
  });
};

export const useDeleteSavedPost = () => {
  const queryClient = useQueryClient();
  return useMutation({
    mutationFn: (savedRecordId: string) => deleteSavedPost(savedRecordId),
    onSuccess: () => {
      queryClient.invalidateQueries({
        queryKey: [QUERY_KEYS.GET_RECENT_POSTS],
      });
      queryClient.invalidateQueries({
        queryKey: [QUERY_KEYS.GET_POSTS],
      });
      queryClient.invalidateQueries({
        queryKey: [QUERY_KEYS.GET_CURRENT_USER],
      });
    },
  });
};

// ============================================================
// USER QUERIES
// ============================================================

export const useGetCurrentUser = () => {
  return useQuery({
    queryKey: [QUERY_KEYS.GET_CURRENT_USER],
    queryFn: getCurrentUser,
  });
};

export const useGetPostById = (postId?: string) => {
  return useQuery({
    queryKey: [QUERY_KEYS.GET_POST_BY_ID, postId],
    queryFn: () => getPostById(postId),
    enabled: !!postId,
  });
};

export const useUpdatePost = () => {
  const queryClient = useQueryClient();
  return useMutation({
    mutationFn: (post: IUpdatePost) => updatePost(post),
    onSuccess: (data) => {
      queryClient.invalidateQueries({
        queryKey: [QUERY_KEYS.GET_POST_BY_ID, data?.$id],
      });
    },
  });
};

export const useDeletePost = () => {
  const queryClient = useQueryClient();
  return useMutation({
    mutationFn: ({ postId, imageId }: { postId?: string; imageId: string }) =>
      deletePost(postId, imageId),
    onSuccess: () => {
      queryClient.invalidateQueries({
        queryKey: [QUERY_KEYS.GET_RECENT_POSTS],
      });
    },
  });
};
```

## 13. Post Details[^tutorial-vidio-13]

### I. Modify the `PostDetails.tsx`

Located in `src/_root/Pages/PostDetails.tsx`

```tsx
import { useGetPostById } from "@/lib/react-query/queriesAndMutations";
import { useParams, Link } from "react-router-dom";
import PostStats from "@/components/shared/PostStats";
import { useUserContext } from "@/context/AuthContext";
import { formatDistanceToNowStrict } from "date-fns";
import Loader from "@/components/shared/Loader";
import { Button } from "@/components/ui/button";

const PostDetails = () => {
  const { id } = useParams();
  const { user } = useUserContext();

  // fetch
  const { data: post, isPending } = useGetPostById(id);

  const handleDeletePost = () => {};

  return (
    <div className="post_details-container">
      {isPending ? (
        <Loader />
      ) : (
        <div className="post_details-card">
          <img src={post?.imageUrl} alt="post" className="post_details-img" />

          <div className="post_details-info">
            <div className="flex-between w-full">
              <Link
                to={`/profile/${post?.creator.$id}`}
                className="flex items-center gap-3"
              >
                <img
                  src={
                    post?.creator.imageUrl ||
                    "/assets/icons/profile-placeholder.svg"
                  }
                  alt="creator"
                  className="w-8 h-8 lg:w-12 lg:h-12 rounded-full"
                />
                <div className="flex gap-1 flex-col">
                  <p className="base-medium lg:body-bold text-light-1">
                    {post?.creator.name}
                  </p>
                  <div className="flex-center gap-2 text-light-3">
                    <p className="subtle-semibold lg:small-regular ">
                      {formatDistanceToNowStrict(
                        new Date(post?.$createdAt || ""),
                        {
                          addSuffix: true,
                        }
                      )}
                    </p>
                    •
                    <p className="subtle-semibold lg:small-regular">
                      {post?.location}
                    </p>
                  </div>
                </div>
              </Link>

              <div className="flex-center">
                <Link
                  to={`/update-post/${post?.$id}`}
                  className={`${user.id !== post?.creator.$id && "hidden"}`} // hide edit button if user is not the creator
                >
                  <img
                    src={"/assets/icons/edit.svg"}
                    alt="edit"
                    width={24}
                    height={24}
                  />
                </Link>

                <Button
                  onClick={handleDeletePost}
                  variant="ghost"
                  className={`ghost_details-delete_btn ${
                    user.id !== post?.creator.$id && "hidden" // hide delete button if user is not the creator
                  }`}
                >
                  <img
                    src={"/assets/icons/delete.svg"}
                    alt="delete"
                    width={24}
                    height={24}
                  />
                </Button>
              </div>
            </div>

            <hr className="border w-full border-dark-4/80" />

            <div className="flex flex-col flex-1 w-full small-medium lg:base-regular">
              <p>{post?.caption}</p>
              <ul className="flex gap-1 mt-2">
                {post?.tags.map((tag: string, index: string) => (
                  <li
                    key={`${tag}${index}`}
                    className="text-light-3 small-regular"
                  >
                    #{tag}
                  </li>
                ))}
              </ul>
            </div>

            <div className="w-full">
              <PostStats post={post} userId={user.id} />
            </div>
          </div>
        </div>
      )}
    </div>
  );
};

export default PostDetails;
```

### II. Modify the `PostStats.tsx`

Located in `src/_root/Pages/PostStats.tsx`

```tsx
import React, { useState, useEffect } from "react";
import {
  useLikePost,
  useSavePost,
  useDeleteSavedPost,
  useGetCurrentUser,
} from "@/lib/react-query/queriesAndMutations";
import { Models } from "appwrite";
import { checkIsLiked } from "@/lib/utils";
import Loader from "./Loader";

type PostStatsProps = {
  post: Models.Document;
  userId: string;
};

const PostStats = ({ post, userId }: PostStatsProps) => {
  const likesList = post.likes.map((user: Models.Document) => user.$id); // list of user ids who liked the post
  //  console.log("likesList:", likesList);

  // useState:
  const [likes, setLikes] = useState<string[]>(likesList); // list of user ids who liked the post
  const [isSaved, setIsSaved] = useState(false); // is the post saved by the current user?

  const { mutate: likePost } = useLikePost();
  const { mutate: savePost, isPending: isSavingPost } = useSavePost();
  const { mutate: deleteSavePost, isPending: isDeletingSaved } =
    useDeleteSavedPost();

  // who is the current user?
  const { data: currentUser } = useGetCurrentUser();

  const savedPostRecord = currentUser?.save.find(
    (record: Models.Document) => record.post.$id === post.$id
  );

  useEffect(() => {
    setIsSaved(savedPostRecord ? true : false); // or: setIsSaved(!!savedPostRecord);
    // { Saved: true } => !savedPostRecord => !false = true
    // { Saved: false } => !savedPostRecord => !true = false
  }, [currentUser]);

  const handleLikePost = (
    e: React.MouseEvent<HTMLImageElement, MouseEvent>
  ) => {
    e.stopPropagation();

    let likesArray = [...likes];

    const hasLiked = likesArray.includes(userId);

    if (hasLiked) {
      likesArray = likesArray.filter((Id) => Id !== userId);
    } else {
      likesArray.push(userId);
    }

    setLikes(likesArray);
    likePost({ postId: post.$id, likesArray });
  };

  const handleSavePost = (
    e: React.MouseEvent<HTMLImageElement, MouseEvent>
  ) => {
    e.stopPropagation();

    if (savedPostRecord) {
      setIsSaved(false);
      return deleteSavePost(savedPostRecord.$id);
    }

    savePost({ userId: userId, postId: post.$id });
    setIsSaved(true);
  };

  const containerStyles = location.pathname.startsWith("/profile")
    ? "w-full"
    : "";

  return (
    <div
      className={`flex justify-between items-center z-20 ${containerStyles}`}
    >
      <div className="flex gap-2 mr-5">
        <img
          src={`${
            checkIsLiked(likes, userId)
              ? "/assets/icons/liked.svg"
              : "/assets/icons/like.svg"
          }`}
          alt={checkIsLiked(likes, userId) ? "liked" : "like"}
          width={20}
          height={20}
          onClick={(e) => handleLikePost(e)}
          className="cursor-pointer"
        />

        <p className="small-medium lg:base-medium">{likes.length}</p>
      </div>

      <div className="flex gap-2">
        {isSavingPost || isDeletingSaved ? (
          <Loader />
        ) : (
          <img
            src={isSaved ? "/assets/icons/saved.svg" : "/assets/icons/save.svg"}
            alt="share"
            width={20}
            height={20}
            className="cursor-pointer"
            onClick={handleSavePost}
          />
        )}
      </div>
    </div>
  );
};

export default PostStats;
```





## 14. Explore Page[^tutorial-vidio-14]
## 15. Search Results[^tutorial-vidio-15]
## 16. Active Lesson[^tutorial-vidio-16]


## 17. Deployment[^tutorial-vidio-17]

This project will be deploy using:

[![Vercel](https://img.shields.io/badge/Vercel-000000.svg?style=for-the-badge&logo=Vercel&logoColor=white)](https://www.Vercel.com)

1. Go to their [website](https://www.Vercel.com) and login with Github.
2. In the Vercel Dashboard, click on `Add New` > `Project`
3. Select the Github Repo from the list
4. Under Configure Project > **Environment Variables**
> Add the Environment Variables to Vercel by coping the code from `.env.local` 
5. Click `Deploy`

### Deployment is Done but Trow Error

The page is up but there is an error due to the CORS policy.

![Deployment Error image](./img/deploymentError.PNG)


### How to Fix The CORS Policy Error?

1. Go to the `Project` in Appwrite > and add the new plataform
- Project: `SocialMedia`
- Add a Platform: `web` > `+`
2. Under `Register your hostname`
- Name: `socialmedia`
- Hostname: `*.vercel.app`
- Click `Next`
- Click `Skip optional Steps`






<!-- LICENSE -->

## License 📜

Distributed under the MIT License. See `LICENSE.txt` for more information.

<!-- OTHER PROJECTS -->

## Projects 🚀

[![](https://img.shields.io/badge/Platzi_Repos-121f3d?style=for-the-badge&logo=Platzi&logoColor=98CA3F)](#)
[![](https://img.shields.io/badge/2021-222?style=for-the-badge)](https://github.com/JuanPabloDiaz/platzi/tree/main/2021)
[![](https://img.shields.io/badge/2022-222?style=for-the-badge)](https://github.com/JuanPabloDiaz/platzi/tree/main/2022)

## Courses & Certifications

For more information regarding my completed courses and certificates, please click on:

[![](https://img.shields.io/badge/Platzi_Profile-121f3d?style=for-the-badge&logo=Platzi&logoColor=98CA3F)](https://platzi.com/p/1diazdev/)<!-- ACKNOWLEDGMENTS -->

## Acknowledgments 📚

Resources list that I find helpful and would like to give credit to.

- [Tailwindcss.com](https://tailwindcss.com/)
- [Tailwind CSS Cheat Sheet](https://tailwindcomponents.com/cheatsheet/)
- Video: [How To Use Tailwind CSS With React](https://www.youtube.com/watch?v=W99CEOBCPSI)
- [Create a Landing Page with React.JS and tailwind CSS](https://medium.com/@chiragmehta900/create-a-responsive-landing-page-with-react-js-and-tailwind-css-fa09ffb24cb7)
- [Pesticides extension](https://chrome.google.com/webstore/detail/pesticide-for-chrome/bakpbgckdnepkmkeaiomhmfcnejndkbi) to check the layout of the page
- How to set [React background Image](https://www.freecodecamp.org/news/react-background-image-tutorial-how-to-set-backgroundimage-with-inline-css-style/)

## Footnotes  Time Stamps 📺
[^tutorial-vidio-1]: [00:00:00 - Intro](https://www.youtube.com/watch?v=_W3R2VwRyF4&t=0s)
[^tutorial-vidio-2]: [00:05:56 - Setup](https://www.youtube.com/watch?v=_W3R2VwRyF4&t=356s)
[^tutorial-vidio-3]: [00:15:50 - Routing](https://www.youtube.com/watch?v=_W3R2VwRyF4&t=950s)
[^tutorial-vidio-4]: [00:18:51 - File & Folder Structure](https://www.youtube.com/watch?v=_W3R2VwRyF4&t=1131s)
[^tutorial-vidio-5]: [00:23:49 - Auth Pages](https://www.youtube.com/watch?v=_W3R2VwRyF4&t=1429s)
[^tutorial-vidio-6]: [00:51:16 - Auth Functionality - Appwrite](https://www.youtube.com/watch?v=_W3R2VwRyF4&t=3076s)
[^tutorial-vidio-7]: [01:02:39 - Storage & Database Design](https://www.youtube.com/watch?v=_W3R2VwRyF4&t=3759s)
[^tutorial-vidio-7a]: [01:05:40 - Create Relations in AppWrite](https://youtu.be/_W3R2VwRyF4?t=3943)
[^tutorial-vidio-8]: [01:31:21 - TanStack Query](https://www.youtube.com/watch?v=_W3R2VwRyF4&t=5481s)
[^tutorial-vidio-9]: [02:15:48 - HomePage](https://www.youtube.com/watch?v=_W3R2VwRyF4&t=8148s)
[^tutorial-vidio-10]: [02:48:27 - Create Post](https://www.youtube.com/watch?v=_W3R2VwRyF4&t=10107s)
[^tutorial-vidio-11]: [03:39:48 - Post Card](https://www.youtube.com/watch?v=_W3R2VwRyF4&t=13188s)
[^tutorial-vidio-12]: [04:32:53 - Post CRUD](https://www.youtube.com/watch?v=_W3R2VwRyF4&t=16373s)
[^tutorial-vidio-13]: [04:49:44 - Post Details](https://www.youtube.com/watch?v=_W3R2VwRyF4&t=17384s)
[^tutorial-vidio-14]: [05:02:03 - Explore Page](https://www.youtube.com/watch?v=_W3R2VwRyF4&t=18123s)
[^tutorial-vidio-15]: [05:29:03 - Search Results](https://www.youtube.com/watch?v=_W3R2VwRyF4&t=19743s)
[^tutorial-vidio-16]: [05:39:22 - Active Lesson](https://www.youtube.com/watch?v=_W3R2VwRyF4&t=20362s)
[^tutorial-vidio-17]: [05:45:58 - Deployment](https://www.youtube.com/watch?v=_W3R2VwRyF4&t=20758s)