---
layout: post
title: "E-commerce Site with React.js, Vite.js and Tailwind CSS"
date: 2023-11-15
categories: platzi 2023
tags: react vite tailwind
image: /assets/img/featured-posts/learn.jpg
---

Here is how to create an E-commerce site using React.js, Vite.js and TailwindCSS. The course name is: "[Curso de React.js con Vite.js y TailwindCSS](https://platzi.com/cursos/react-vite-tailwindcss/)".

<!-- ABOUT THE PROJECT -->

## Description 💡

Build an Online Store with React.js, the most in-demand tool for frontend developers. It integrates Vite.js for the development environment, TailwindCSS for style management and React Router DOM for routes and navigation. Transform Figma prototypes into professional web applications and deploy them to production with your Teffcode teacher.

- Build components to view products, purchase orders and filter by category
- Implement client-side navigation with React Router.
- Consume the Platzi Fake Store using React.js.


Visit the [Figma Design](https://www.figma.com/file/TGm6gNug6PEwEbV8M0Kyll/JSM-YT---Instagram-Clone?type=design&node-id=1-113&mode=design) and see how the feature should look like

### [Demo](https://shopi.jpdiaz.work)

### Built With 🔑

This project is based on React.js con Vite.js y TailwindCSS

![React](https://img.shields.io/badge/React-61DAFB.svg?style=for-the-badge&logo=React&logoColor=black)
![Vite](https://img.shields.io/badge/Vite-646CFF.svg?style=for-the-badge&logo=Vite&logoColor=white)
![Tailwind-CSS](https://img.shields.io/badge/Tailwind%20CSS-06B6D4.svg?style=for-the-badge&logo=Tailwind-CSS&logoColor=white)
![React-Router](https://img.shields.io/badge/React%20Router-CA4245.svg?style=for-the-badge&logo=React-Router&logoColor=white)
![Figma](https://img.shields.io/badge/Figma-F24E1E.svg?style=for-the-badge&logo=Figma&logoColor=white)

# Content

## 1. Create a React Project using Vite

### I. Go to [Vite](https://vitejs.dev//).js and click on [Get Started](https://vitejs.dev/guide/#scaffolding-your-first-vite-project)

### II. Run command:

```bash
npm create vite@latest ./
```

### III. Configure the **Vite Project**

You will be asked a few questions:
```bash
Need to install the following packages:
create-vite@4.4.1
Ok to proceed? (y) no / `yes`
Select a Framework: › `React`
Select a variant? › `Javascript`
```

### IV. Run command:

```bash
npm install
npm run dev
```

- [Getting Started with Vite](https://vitejs.dev/guide/)

## 2. SetUp by Customizing the Project

This is the Starting Point Of The Project, where we will...

### I. Delete unnecesary files

- Delete the `assets` folder and create a new `assets` folder.
- Delete the `public` folder and create a new `public` folder.
- Delete the content from `src/App.css` (keep the file)
- Delete the content from `src/index.css` (keep the file)
- Delete the content from `src/App.jsx` (keep the file)
- Add the code below to `src/App.jsx`:
    ```jsx
    import "./App.css";
    function App() {
    return (
        <>
        <div>
        Hello World
        </div>
        </>
    );
    }
    export default App;
    ```

### II. [Install Tailwind in the project with Vite](https://tailwindcss.com/docs/guides/vite).

- Run commands:

    ```bash
    npm install -D tailwindcss postcss autoprefixer
    npx tailwindcss init -p
    ```

### III. Follow the [Tailwind documentation for Vite](https://tailwindcss.com/docs/guides/vite).

- Modify the `tailwind.config` file

    ```js
    /** @type {import('tailwindcss').Config} */
    export default {
    content: [
        "./index.html",
        "./src/**/*.{js,ts,jsx,tsx}",
    ],
    theme: {
        extend: {},
    },
    plugins: [],
    }
    ```

- Add the Tailwind directives to your CSS

    ```css
    @tailwind base;
    @tailwind components;
    @tailwind utilities;
    ```

- Run the project

    ```bash
    npm run dev
    ```

## 3. Create The Pages and Routes

For the [Structure](https://blog.webdevsimplified.com/2022-07/react-folder-structure/):

- Create a `Pages` folder inside the `src` folder
- Inside `src/Pages`, create files:
    - `Home/index.jsx`
    - `MyAccount/index.jsx`
    - `MyOrder/index.jsx`
    - `MyOrders/index.jsx`
    - `NotFound/index.jsx`
    - `SignIn/index.jsx`
> Run `rafce`, delete `import React from "react";` and ensure the routing works and the app is not broken. (modify the `main.jsx` & `App.jsx`)

- Move and rename the `App.jsx` file >> to `src/Pages/App/index.jsx`
- Modify the `src/Pages/App/index.jsx`
    ```jsx
    import "./App.css";
    import Home from "../Home";
    import MyAccount from "../MyAccount";
    import MyOrder from "../MyOrder";
    import MyOrders from "../MyOrders";
    import NotFound from "../NotFound";
    import SignIn from "../SignIn";

    function App() {
    return (
        <>
        <div className="flex flex-col">
            <Home />
            <MyAccount />
            <MyOrder />
            <MyOrders />
            <NotFound />
            <SignIn />
        </div>
        </>
    );
    }

    export default App;
    ```
- Modify the `main.jsx`
    ```jsx
    import React from "react";
    import ReactDOM from "react-dom/client";
    import App from "./Pages/App/index.jsx";
    import "./index.css";

    ReactDOM.createRoot(document.getElementById("root")).render(
    <React.StrictMode>
        <App />
    </React.StrictMode>
    );
    ```

## 4. Routing

### Install [React Router DOM](https://www.npmjs.com/package/react-router-dom#react-router-dom) 

```bash
npm i react-router-dom
```

### I. Edit the `App/index.jsx` file:
Located in `src/Pages/App/index.jsx`

```jsx
import { useRoutes, BrowserRouter } from "react-router-dom";
import Home from "../Home";
import MyAccount from "../MyAccount";
import MyOrder from "../MyOrder";
import MyOrders from "../MyOrders";
import NotFound from "../NotFound";
import SignIn from "../SignIn";
import "./App.css";

const AppRoutes = () => {
  let routes = useRoutes([
    { path: "/", element: <Home /> },
    { path: "/my-account", element: <MyAccount /> },
    { path: "/my-order", element: <MyOrder /> },
    { path: "/my-orders", element: <MyOrders /> },
    { path: "/sign-in", element: <SignIn /> },
    { path: "*", element: <NotFound /> },
  ]);
  return routes;
};

const App = () => {
  return (
    <BrowserRouter>
      <AppRoutes />
    </BrowserRouter>
  );
};
export default App;
```

## 4. **Navbar** Component

### I. Create the `Navbar` Component

Located in `src/Components/Navbar/index.jsx`

```jsx
import { NavLink } from "react-router-dom";

const Navbar = () => {
  const activeStyle = "underline text-gray-500 underline-offset-4";

  return (
    <nav className="flex justify-between items-center fixed z-10 w-full py-5 px-8 text-md font-light top-0">
      <ul className="flex items-center gap-3">
        <li className="font-semibold text-lg">
          <NavLink to="/">Shopi</NavLink>
        </li>
        <li>
          <NavLink
            to="/"
            className={({ isActive }) => (isActive ? activeStyle : undefined)} >
            All
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/clothes"
            className={({ isActive }) => (isActive ? activeStyle : undefined)} >
            Clothes
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/electronics"
            className={({ isActive }) => (isActive ? activeStyle : undefined)} >
            Electronics
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/furnitures"
            className={({ isActive }) => (isActive ? activeStyle : undefined)} >
            Furnitures
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/toys"
            className={({ isActive }) => (isActive ? activeStyle : undefined)} >
            Toys
          </NavLink>
        </li>
      </ul>

      <ul className="flex items-center gap-3">
        <li>
          <NavLink
            to="/my-orders"
            className={({ isActive }) => (isActive ? activeStyle : undefined)} >
            My Orders
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/my-account"
            className={({ isActive }) => (isActive ? activeStyle : undefined)} >
            My Account
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/sign-in"
            className={({ isActive }) => (isActive ? activeStyle : undefined)} >
            Sign In
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/card"
            className={({ isActive }) => (isActive ? activeStyle : undefined)} >
            Card 0
          </NavLink>
        </li>
      </ul>
    </nav>
  );
};

export default Navbar;
```

### II. Modify the `App` file

Located in `src/Pages/App/index.jsx`

```jsx
import { useRoutes, BrowserRouter } from "react-router-dom";
import Home from "../Home";
import MyAccount from "../MyAccount";
import MyOrder from "../MyOrder";
import MyOrders from "../MyOrders";
import NotFound from "../NotFound";
import SignIn from "../SignIn";
import Navbar from "../../Components/Navbar";
import "./App.css";

const AppRoutes = () => {
  let routes = useRoutes([
    { path: "/", element: <Home /> },
    { path: "/my-account", element: <MyAccount /> },
    { path: "/my-order", element: <MyOrder /> },
    { path: "/my-orders", element: <MyOrders /> },
    { path: "/sign-in", element: <SignIn /> },
    { path: "*", element: <NotFound /> },
  ]);
  return routes;
};

const App = () => {
  return (
    <BrowserRouter>
      <AppRoutes />
      <Navbar />
    </BrowserRouter>
  );
};
export default App;
```

## 5.  **Layout** Componente

### I. Create the `Layout` Component

Located in `src/Components/Layout/index.jsx`

```jsx
const Layout = ({ children }) => {
  return (
  <div className="flex flex-col items-center mt-20">
    {children}
  </div>;
  )
};

export default Layout;
```

### II. Add the Layout to all my pages:

- `Home/index.jsx`
- `MyAccount/index.jsx`
- `MyOrder/index.jsx`
- `MyOrders/index.jsx`
- `NotFound/index.jsx`
- `SignIn/index.jsx`

Include the following structure:

```jsx
import Layout from "../../Components/Layout";

const NameHere = () => {
  return (
  <Layout>
  NameHere
  </Layout>;
};

export default NameHere;
```
> Replace the `NameHere` with the name of the folder.

## 6.  **Card** Componente

### I. Create the `Card` Component

Located in `src/Components/Card/index.jsx`

```jsx
const Card = () => {
  return (
    <div className="bg-amber-600/80 cursor-pointer w-56 h-60 rounded-lg">
      <figure className="relative mb-2 w-full h-4/5">
        <span className="absolute bottom-0 bg-white/60 rounded-lg text-black text-xs m-2 py-0.5 px-2">tag</span>
        <img
          className="rounded-lg w-full h-full object-cover"
          src="https://images.pexels.com/photos/3861969/pexels-photo-3861969.jpeg?auto=compress&cs=tinysrgb&w=300"
          alt="card image"
        />
        <div className="absolute top-0 right-0 flex justify-center items-center bg-white rounded-full w-6 h-6 m-2"> + </div>
      </figure>
      <p className="flex justify-around">
        <span className="text-sm font-light">Headphones</span>
        <span className="text-lg font-medium">$300</span>
      </p>
    </div>
  );
};

export default Card;
```

### II. Modify the `Home` Component

Located in `src/Components/Home/index.jsx`

```jsx
import Card from "../../Components/Card";
import Layout from "../../Components/Layout";

const Home = () => {
  return (
    <Layout>
      <Card />
    </Layout>
  );
};

export default Home;
```
























<!-- OTHER PROJECTS -->

## Projects 🚀

![](https://img.shields.io/badge/Platzi_Repos-121f3d?style=for-the-badge&logo=Platzi&logoColor=98CA3F)
[![](https://img.shields.io/badge/2021-222?style=for-the-badge)](https://github.com/JuanPabloDiaz/platzi/tree/main/2021)
[![](https://img.shields.io/badge/2022-222?style=for-the-badge)](https://github.com/JuanPabloDiaz/platzi/tree/main/2022)
[![](https://img.shields.io/badge/2023-222?style=for-the-badge)](https://github.com/JuanPabloDiaz/platzi/tree/main/2023)


<!-- LICENSE -->

## License 📜

Distributed under the MIT License. See `LICENSE.txt` for more information.

<!-- CONTACT -->

## Contact 📞

[![](https://img.shields.io/badge/@1diazdev-fff?style=for-the-badge&logo=linkedin&logoColor=0A66C2)](https://www.linkedin.com/in/1diazdev/)
[![](https://img.shields.io/badge/@1diazdev-fff?style=for-the-badge&logo=Twitter&logoColor=1DA1F2)](https://www.twitter.com/1diazdev)
[![](https://img.shields.io/badge/Gmail-fff?style=for-the-badge&logo=gmail&logoColor=EA4335)](mailto:juan.diaz93@hotmail.com)

[![](https://img.shields.io/badge/Platzi_Profile-121f3d?style=for-the-badge&logo=Platzi&logoColor=98CA3F)](https://platzi.com/p/DiazJuan/)

<!-- ACKNOWLEDGMENTS -->

## Acknowledgments 📚

Resources list that I find helpful and would like to give credit to.

- [How To Structure React Projects From Beginner To Advanced](https://blog.webdevsimplified.com/2022-07/react-folder-structure/)