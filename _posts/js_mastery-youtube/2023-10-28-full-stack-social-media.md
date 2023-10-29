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
[![Appwrite](https://img.shields.io/badge/Appwrite-F02E65.svg?style=for-the-badge&logo=Appwrite&logoColor=white)](https://appwrite.io/)
[![TypeScript](https://img.shields.io/badge/TypeScript-3178C6.svg?style=for-the-badge&logo=TypeScript&logoColor=white)](https://www.typescriptlang.org/)
[![Tailwind](https://img.shields.io/badge/Tailwind%20CSS-06B6D4.svg?style=for-the-badge&logo=Tailwind-CSS&logoColor=white)](https://tailwindcss.com/)

## 1. Create a React Project using Vite

```bash
npm create vite@latest
```
```bash
npm install
npm run dev
```

- [Getting Started with Vite](https://vitejs.dev/guide/)

## 2. Customize the Project (SetUp)

A. Starting Point Of The Project: `Delete` the `src` folder and create a new one with the files `App.tsx`, `main.tsx` and edit the files [(more info)](https://github.com/JuanPabloDiaz/socialMedia/commit/a537dd5495959114c2afa51767249d972c657b88)

B. Create a `global.css` file and add the tailwind classes that we will use in the project. [(more info)](https://github.com/JuanPabloDiaz/socialMedia/commit/63c49b3a8043f76157c9e84d7f3c3702e8f79fed)

C. [Install Tailwind in the project with Vite](https://tailwindcss.com/docs/guides/vite).

```bash
npm install -D tailwindcss postcss autoprefixer
npx tailwindcss init -p
```
> Note: it will show an error if I run the project at this point. the `bg-dark-1` and `font-Inter` needs to be install (step D) 

D. Modify the `tailwind.config` file by adding the info in the [Github repo](https://gist.github.com/adrianhajdin/4d2500bf5af601bbd9f4f596298d33ac)

  - Install the necesary plugins: 
  ```
  npm install -D tailwindcss-animate
  ```
  > Make sure to install the plugin and modify [(more info)](https://github.com/JuanPabloDiaz/socialMedia/commit/755a5aa625577a880d3b7b55ffac063e220236a2)

## 3. Routing

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
import SignupnForm from "./_auth/forms/SignupnForm";
import { Home } from "./_root/Pages";
import AuthLayout from "./_auth/AuthLayout";
import RootLayout from "./_root/RootLayout";

const App = () => {
  return (
    <main className="flex h-screen">
      <Routes>
        {/* Public Routes */}
          <Route path="/sign-in" element={<SigninForm />} />
          <Route path="/sign-up" element={<SignupnForm />} />
        {/* Private Routes */}
          <Route index element={<Home />} />
      </Routes>
    </main>
  );
};

export default App;
```
## 4. File & Folder Structure

### Create & edit the files:

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
import SignupnForm from "./_auth/forms/SignupnForm";
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
          <Route path="/sign-up" element={<SignupnForm />} />
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

## 5. Auth Pages

### A. Install [Shadcn UI](https://ui.shadcn.com/docs/installation/vite) for Vite. 

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
> The `tsconfig.json` file should look like:
   ```bash
   {
  "compilerOptions": {
    "target": "ES2020",
    "useDefineForClassFields": true,
    "lib": ["ES2020", "DOM", "DOM.Iterable"],
    "module": "ESNext",
    "skipLibCheck": true,

    /* Bundler mode */
    "moduleResolution": "bundler",
    "allowImportingTsExtensions": true,
    "resolveJsonModule": true,
    "isolatedModules": true,
    "noEmit": true,
    "jsx": "react-jsx",

    /* Linting */
    "strict": true,
    "noUnusedLocals": true,
    "noUnusedParameters": true,
    "noFallthroughCasesInSwitch": true,
    /* Shadcn UI */
    "baseUrl": ".",
    "paths": {
      "@/*": ["./src/*"]
    }
  },

  "include": ["src"],
  "references": [{ "path": "./tsconfig.node.json" }]
}
```

### B. Install Node.
```bash
# (so you can import "path" without error)
npm i -D @types/node
``` 
### C. Overwrite the `vite.config.ts` file:
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
### D. Run the shadcn-ui init command to setup your project:

```bash
npx shadcn-ui@latest init
```
### E. Configure components.json
You will be asked a few questions to configure components.json:
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

### F. Modify the `AuthLayout.tsx` file

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
          <section>
            <Outlet />
          </section>
        </>
      )}
    </>
  );
};

export default AuthLayout;
```




## 6. Auth Functionality - Appwrite
## 7. Storage & Database Design
## 8. TanStack Query
## 9. HomePage
## 10. Create Post
## 11. Post Card
## 12. Post CRUD
## 13. Post Details
## 14. Explore Page
## 15. Search Results
## 16. Active Lesson






## last step. Deployment

There are multiple ways to deploy a React app in just minutes. Here is an article that explains 8 different ways to [Deploy a React App](https://blog.logrocket.com/8-ways-deploy-react-app-free/#:~:text=For%20your%20React%20app%2C%20you,whenever%20you%20push%20your%20changes.).

[![Vercel](https://img.shields.io/badge/Vercel-000000.svg?style=for-the-badge&logo=Vercel&logoColor=white)](https://www.Vercel.com)

- From a [Github Repo](https://www.youtube.com/watch?v=sauV-3_Nn60)
- From a [new project on your machine](https://www.youtube.com/watch?v=FvsvHzcwOmQ)

[![Firebase](https://img.shields.io/badge/Firebase-FFCA28.svg?style=for-the-badge&logo=Firebase&logoColor=black)](https://www.Firebase.com)

1. Install Firebase:
   ```bash
    npm install -g firebase-tools
   ```
2. Login with your Firebase or Google account.
   ```bash
   firebase login
   ```
3. Follow steps on [blog](https://blog.logrocket.com/8-ways-deploy-react-app-free/#firebase)

[![Netlify](https://img.shields.io/badge/Netlify-00C7B7.svg?style=for-the-badge&logo=Netlify&logoColor=white)](https://www.Netlify.com)

[![GitHub Pages](https://img.shields.io/badge/GitHub%20Pages-222222.svg?style=for-the-badge&logo=GitHub-Pages&logoColor=white)](https://pages.github.com/)

[![Heroku](https://img.shields.io/badge/Heroku-430098.svg?style=for-the-badge&logo=Heroku&logoColor=white)](https://www.Heroku.com)

[![Surge](https://img.shields.io/badge/Surge-FFDE91.svg?style=for-the-badge&logo=&logoColor=black)](https://surge.sh/)

1. Make sure to have latest Node.js
2. Install Surge:

```bash
 npm install --global surge
```

3. Now, run surge from within any directory, to publish that directory onto the web.

[![Render](https://img.shields.io/badge/Render-46E3B7.svg?style=for-the-badge&logo=Render&logoColor=white)](https://www.Render.com)

From a Github Repo. [Learn More](https://blog.logrocket.com/8-ways-deploy-react-app-free/#render)

[![GitLab Pages](https://img.shields.io/badge/GitLab_Pages-FC6D26.svg?style=for-the-badge&logo=GitLab&logoColor=white)](https://www..com)

---

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
