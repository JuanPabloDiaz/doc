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
- Implement client-side navigation with React Router. Server-Side rendering (SSR)
- Consume the Platzi Fake Store using React.js.

### Demos: [JP·Shop](https://jpshop.jpdiaz.dev/) | [Shopi](https://shopi.jpdiaz.work)

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
        <div>Hello World</div>
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
    content: ["./index.html", "./src/**/*.{js,ts,jsx,tsx}"],
    theme: {
      extend: {},
    },
    plugins: [],
  };
  ```

- Add the Tailwind directives to your CSS

  ```css
  @tailwind base;
  @tailwind components;
  @tailwind utilities;
  ```

- Modify the code below to `src/App.jsx`:

  ```jsx
  import "./App.css";
  function App() {
    return (
      <>
        <div classname="bg-gray-500">Hello World</div>
      </>
    );
  }
  export default App;
  ```

- Run the project

  ```bash
  npm run dev
  ```

### IV. App Plugings

A. Install [React Icons](https://www.npmjs.com/package/react-icons)

```bash
npm i react-icons
```

> In this proyect. I will use [Heroicons](https://react-icons.github.io/react-icons/icons/hi/)

## 3. Create The Pages and Routes

For the [Structure](https://blog.webdevsimplified.com/2022-07/react-folder-structure/):

- Create a `Pages` folder inside the `src` folder
- Inside `src/Pages`, create files: - `Home/index.jsx` - `MyAccount/index.jsx` - `MyOrder/index.jsx` - `MyOrders/index.jsx` - `NotFound/index.jsx` - `SignIn/index.jsx`

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

## 5. **Navbar** Component

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
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            All
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/clothes"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            Clothes
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/electronics"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            Electronics
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/furnitures"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            Furnitures
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/toys"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            Toys
          </NavLink>
        </li>
      </ul>

      <ul className="flex items-center gap-3">
        <li>
          <NavLink
            to="/my-orders"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            My Orders
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/my-account"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            My Account
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/sign-in"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            Sign In
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/card"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            🛒 0
          </NavLink>
        </li>
      </ul>
    </nav>
  );
};

export default Navbar;
```

> [Learn more](https://platzi.com/new-home/clases/3468-react-router/51619-link-vs-navlink/)

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

## 6. **Layout** Componente

### I. Create the `Layout` Component

Located in `src/Components/Layout/index.jsx`

```jsx
const Layout = ({ children }) => {
  return <div className="flex flex-col items-center mt-20">{children}</div>;
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
  return <Layout>NameHere</Layout>;
};

export default NameHere;
```

> Replace the `NameHere` with the name of the folder.

## 7. **Card** Componente

### I. Create the `Card` Component

Located in `src/Components/Card/index.jsx`

```jsx
const Card = () => {
  return (
    <div className="bg-amber-600/80 cursor-pointer w-56 h-60 rounded-lg">
      <figure className="relative mb-2 w-full h-4/5">
        <span className="absolute bottom-0 bg-white/60 rounded-lg text-black text-xs m-2 py-0.5 px-2">
          tag
        </span>
        <img
          className="rounded-lg w-full h-full object-cover"
          src="https://images.pexels.com/photos/3861969/pexels-photo-3861969.jpeg?auto=compress&cs=tinysrgb&w=300"
          alt="card image"
        />
        <div className="absolute top-0 right-0 flex justify-center items-center bg-white rounded-full w-6 h-6 m-2">
          {" "}
          +{" "}
        </div>
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

## 8. Consume an API

Consuming APIs is the process by which the application developer accesses the various APIs that are exposed by you

### I. Go the API Website and read the Documentation

It is Extremely important to understand how to use and consume the API we are about to use.

API Examples:

- [Platzi Fake Store API](https://fakeapi.platzi.com/) 🕮 [Docs](https://fakeapi.platzi.com/en/about/introduction/)
- [Fake Store API](https://fakestoreapi.com/) 🕮 [Docs](https://fakestoreapi.com/docs)
- [Rapid API](https://rapidapi.com/hub)
- [Dummy json API](https://dummyjson.com)

### II. Use the API

After finding what we needed to do to be able to use the **API**

- Get the API URL from the section/element that we want to use

Example: [Fake **Store** API](https://fakestoreapi.com/docs#p-all)

```js
// Get all products:
fetch("https://fakestoreapi.com/products")
  .then((res) => res.json())
  .then((json) => console.log(json));
```

```js
// Output:
[
  {
    id: 1,
    title: "...",
    price: "...",
    category: "...",
    description: "...",
    image: "...",
  },
  /*...*/
  {
    id: 30,
    title: "...",
    price: "...",
    category: "...",
    description: "...",
    image: "...",
  },
];
```

Example: [Fake **Platzi** API](https://fakeapi.platzi.com/en/rest/products/)

```js
// Get all products:
fetch("https://api.escuelajs.co/api/v1/products")
  .then((res) => res.json())
  .then((json) => console.log(json));
```

```js
// Output:
[
  {
    id: 4,
    title: "Handmade Fresh Table",
    price: 687,
    description: "Andy shoes are designed to keeping in...",
    category: {
      id: 5,
      name: "Others",
      image: "https://placeimg.com/640/480/any?r=0.591926261873231",
    },
    images: [
      "https://placeimg.com/640/480/any?r=0.9178516507833767",
      "https://placeimg.com/640/480/any?r=0.9300320592588625",
      "https://placeimg.com/640/480/any?r=0.8807778235430017",
    ],
  },
  // ...
];
```

> _State_ and _Effect_ are use to consume an API

### III. Modify the `Home` Page

Located in `src/Pages/Home/index.jsx`

```jsx
import { useState, useEffect } from "react"; // Hooks to consume the API
import Card from "../../Components/Card";
import Layout from "../../Components/Layout";

const Home = () => {
  // UseState is a hook to add the info from the API to the state
  const [items, setItems] = useState(null);

  // UseEffect is a hook to fetch the data from the API
  useEffect(() => {
    fetch("https://api.escuelajs.co/api/v1/products")
      .then((response) => response.json())
      .then((json) => setItems(json));
  }, []);

  return (
    <Layout>
      <div className="grid gap-4 grid-cols-4 w-full max-w-screen-lg">
        {items?.map((item) => (
          <Card key={item.id} data={item} />
        ))}
      </div>
    </Layout>
  );
};

export default Home;
```

### IV. Modify the `Card` Component

Located in `src/Components/Card/index.jsx`

```jsx
const Card = (data) => {
  return (
    <div className="bg-amber-700/40 cursor-pointer w-56 h-60 rounded-lg">
      <figure className="relative mb-2 w-full h-4/5">
        <span className="absolute bottom-0 bg-white/60 rounded-lg text-black text-xs m-2 py-0.5 px-2">
          {data.data.category.name}
        </span>
        <img
          className="rounded-lg w-full h-full object-cover"
          src={data.data.images}
          alt={data.data.title}
        />
        <div className="absolute top-0 right-0 flex justify-center items-center bg-white rounded-full w-6 h-6 m-2">
          +
        </div>
      </figure>
      <p className="flex justify-around">
        <span className="text-sm font-light">{data.data.title}</span>
        <span className="text-lg font-medium">${data.data.price}</span>
      </p>
    </div>
  );
};

export default Card;
```

## 9. [Global Context](https://legacy.reactjs.org/docs/context.html) (or use [useContext](https://react.dev/reference/react/useContext) instead)

Global state with the Context API

### I. Create the Context file

Located in `src/Context/index.jsx`

```jsx
import { createContext } from "react";

const AppContext = createContext();

export const AppProvider = ({ children }) => {
  return <AppContext.Provider>{children}</AppContext.Provider>;
};
```

### II. Modify the `App` file

Located in `src/Pages/App/index.jsx`

```jsx
import { useRoutes, BrowserRouter } from "react-router-dom";
import { AppProvider } from "../../Context";
import Home from "../Home";
import MyAccount from "../MyAccount";
import MyOrder from "../MyOrder";
import MyOrders from "../MyOrders";
import NotFound from "../NotFound";
import SignIn from "../SignIn";
import Navbar from "../../Components/Navbar";
// import TestNavbar from "../../Components/TestJp/Navbar.jsx";
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
    <AppProvider>
      <BrowserRouter>
        <AppRoutes />
        <Navbar />
      </BrowserRouter>
    </AppProvider>
  );
};
export default App;
```

## 10. Cart Counter

### I. Modify the `Card` Component

Located in `src/Components/Card/index.jsx`

```jsx
import { useContext } from "react";
import { AppContext } from "../../Context";

const Card = (data) => {
  const context = useContext(AppContext);

  return (
    <div className="bg-amber-700/40 cursor-pointer w-56 h-60 rounded-lg">
      <figure className="relative mb-2 w-full h-4/5">
        <span className="absolute bottom-0 bg-white/60 rounded-lg text-black text-xs m-2 py-0.5 px-2">
          {data.data.category.name}
        </span>
        <img
          className="rounded-lg w-full h-full object-cover"
          src={data.data.image} // This is for the Fake Store API
          // src={data.data.images} // This is for the Platzi API (which is not very stable)
          alt={data.data.title}
        />
        <div
          onClick={() => context.setCount(context.count + 1)}
          className="absolute top-0 right-0 flex justify-center items-center bg-white rounded-full w-6 h-6 m-2"
        >
          +
        </div>
      </figure>
      <p className="flex justify-around">
        <span className="text-sm font-light">{data.data.title}</span>
        <span className="text-lg font-medium">${data.data.price}</span>
      </p>
    </div>
  );
};

export default Card;
```

### II. Modify the `Navbar` Component

Located in `src/Components/Navbar/index.jsx`

```jsx
import { NavLink } from "react-router-dom";
import { useContext } from "react";
import { AppContext } from "../../Context";

const Navbar = () => {
  const activeStyle = "underline text-gray-500 underline-offset-4";
  const context = useContext(AppContext);

  return (
    <nav className="flex justify-between items-center fixed z-10 w-full py-5 px-8 text-md font-light top-0">
      <ul className="flex items-center gap-3">
        <li className="font-semibold text-lg">
          <NavLink to="/">Shopi</NavLink>
        </li>
        <li>
          <NavLink
            to="/"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            All
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/clothes"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            Clothes
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/electronics"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            Electronics
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/furnitures"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            Furnitures
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/toys"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            Toys
          </NavLink>
        </li>
      </ul>

      <ul className="flex items-center gap-3">
        <li>
          <NavLink
            to="/my-orders"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            My Orders
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/my-account"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            My Account
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/sign-in"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            Sign In
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/card"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            🛒 {context.count}
          </NavLink>
        </li>
      </ul>
    </nav>
  );
};

export default Navbar;
```

### II. Modify the `Context` file

Located in `src/Context/index.jsx`

```jsx
import { createContext, useState } from "react";

export const AppContext = createContext();

export const AppProvider = ({ children }) => {
  // UseState is a hook to add the info from the API to the state
  const [count, setCount] = useState(0);
  // To inspect the value of count:  // console.log(count);

  return (
    <AppContext.Provider
      value={
        count,
        setCount,
      }
    >
      {children}
    </AppContext.Provider>
  );
};
```

> `value` is missing another set of `{}`. Should look like this: `value={ { ...content here.... } }`

## 11. **SideBar** Component

### I. Create the `ProductDetail` Component

Located in `src/Components/ProductDetail/index.jsx`

```jsx
const ProductDetail = () => {
  return (
    <aside className="flex flex-col fixed right-0 w-[360px] h-[90vh] border border-black shadow-xl shadow-black rounded-lg bg-white/70 p-2 m-2">
      {/* top-[68px] w-[360px] h-[calc(100vh-68px)] */}
      <div>
        <h1>Product Detail</h1>
        <img src="" alt="image" />
      </div>
    </aside>
  );
};

export default ProductDetail;
```

### II. Modify the `Home` Page

Located in `src/Pages/Home/index.jsx`

- Add the `ProductDetail` Component

```jsx
import { useState, useEffect } from "react";
import Card from "../../Components/Card";
import Layout from "../../Components/Layout";
import ProductDetail from "../../Components/ProductDetail";

const Home = () => {
  // UseState is a hook to add the info from the API to the state
  const [items, setItems] = useState(null);

  // UseEffect is a hook to fetch the data from the API
  useEffect(() => {
    // fetch("https://api.escuelajs.co/api/v1/products") // This is for the Platzi API (which is not very stable)
    fetch("https://fakestoreapi.com/products") // This is for the Fake Store API
      .then((response) => response.json())
      .then((json) => setItems(json));
  }, []);

  return (
    <Layout>
      Home
      <div className="grid gap-4 grid-cols-4 w-full max-w-screen-lg">
        {items?.map((item) => (
          <Card key={item.id} data={item} />
        ))}
      </div>
      <ProductDetail />
    </Layout>
  );
};

export default Home;
```

## 12. Add React Icon to the Proyect

> React Icon needs to be install. ([Docs](https://react-icons.github.io/react-icons/)).

### I. Modify the `ProductDetail` Component

Located in `src/Components/ProductDetail/index.jsx`

> Add the Exit icon (x)

```jsx
import { HiOutlineX } from "react-icons/hi";

const ProductDetail = () => {
  return (
    <aside className="flex flex-col fixed right-0 w-[360px] h-[90vh] border border-black shadow-xl shadow-black rounded-lg bg-white/70 p-2 m-2">
      {/* top-[68px] w-[360px] h-[calc(100vh-68px)] */}
      <div className="flex justify-between items-center ">
        <h2 className="font-medium">Product Detail</h2>
        <HiOutlineX />
      </div>
    </aside>
  );
};

export default ProductDetail;
```

### II. Modify the `Card` Component

Located in `src/Components/Card/index.jsx`

> Add the Plus icon (+)

```jsx
import { useContext } from "react";
import { AppContext } from "../../Context";
import { HiPlusSm } from "react-icons/hi";

const Card = (data) => {
  const context = useContext(AppContext);

  return (
    <div className="bg-amber-700/40 cursor-pointer w-56 h-60 rounded-lg">
      <figure className="relative mb-2 w-full h-4/5">
        <span className="absolute bottom-0 bg-white/60 rounded-lg text-black text-xs m-2 py-0.5 px-2">
          {/* {data.data.category.name} is for the Platzi API (which is not very stable) */}
          {/* {data.data.category.name}  */}
          {/* {data.data.category} is for the Fake Store API */}
          {data.data.category}
        </span>        </span>
        <img
          className="rounded-lg w-full h-full object-cover"
          src={data.data.image} // This is for the Fake Store API
          // src={data.data.images} // This is for the Platzi API (which is not very stable)
          alt={data.data.title}
        />
        <HiPlusSm
          onClick={() => context.setCount(context.count + 1)}
          className="absolute top-0 right-0 flex justify-center items-center bg-white rounded-full w-6 h-6 m-2"
        />
      </figure>
      <p className="flex justify-around">
        <span className="text-sm font-light">{data.data.title}</span>
        <span className="text-lg font-medium">${data.data.price}</span>
      </p>
    </div>
  );
};

export default Card;
```

### III. Modify the `Navbar` Component

Located in `src/Components/Navbar/index.jsx`

> Add the Shopping Cart icon (🛒)

```jsx
import { NavLink } from "react-router-dom";
import { useContext } from "react";
import { AppContext } from "../../Context";
import { HiOutlineShoppingCart } from "react-icons/hi";

const Navbar = () => {
  const activeStyle = "underline text-gray-500 underline-offset-4";
  const context = useContext(AppContext);

  return (
    <nav className="flex justify-between items-center fixed z-10 w-full py-5 px-8 text-md font-light top-0">
      <ul className="flex items-center gap-3">
        <li className="font-semibold text-lg">
          <NavLink to="/">Shopi</NavLink>
        </li>
        <li>
          <NavLink
            to="/"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            All
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/clothes"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            Clothes
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/electronics"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            Electronics
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/furnitures"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            Furnitures
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/toys"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            Toys
          </NavLink>
        </li>
      </ul>

      <ul className="flex items-center gap-3">
        <li>
          <NavLink
            to="/my-orders"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            My Orders
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/my-account"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            My Account
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/sign-in"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            Sign In
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/card"
            className={`flex justify-center items-center ${({ isActive }) =>
              isActive ? activeStyle : undefined}`}
          >
            <HiOutlineShoppingCart className="mr-1" /> {context.count}
          </NavLink>
        </li>
      </ul>
    </nav>
  );
};

export default Navbar;
```

## 13. Functions to Open And Close the Product Detail

### I. Modify the `Context` file

Located in `src/Context/index.jsx`

```jsx
import { createContext, useState } from "react";

export const AppContext = createContext();

export const AppProvider = ({ children }) => {
  // Hook to add the info from the API to the state:
  const [count, setCount] = useState(0);
  // To inspect the value of count:  // console.log(count);
  // Hook to open and close the product detail component:
  const [isProductDetailOpen, setIsProductDetailOpen] = useState(false);
  const openProductDetail = () => setIsProductDetailOpen(true);
  const closeProductDetail = () => setIsProductDetailOpen(false);

  return (
    <AppContext.Provider
      value={
        count,
        setCount,
        openProductDetail,
        closeProductDetail,
        isProductDetailOpen,
      }
    >
      {children}
    </AppContext.Provider>
  );
};
```

> `value` is missing another set of `{}`. It should look like this: `value={ { ...content here.... } }`

### II. Modify the `Product Detail` Component

Located in `src/Components/ProductDetail/index.jsx`

```jsx
import { HiOutlineX } from "react-icons/hi";
import { useContext } from "react";
import { AppContext } from "../../Context";

const ProductDetail = () => {
  const context = useContext(AppContext);
  return (
    <aside
      className={`${
        context.isProductDetailOpen ? "flex" : "hidden"
      } flex-col fixed right-0 w-[360px] h-[90vh] border border-black shadow-xl shadow-black rounded-lg bg-white/70 p-2 m-2`}
    >
      {/* top-[68px] w-[360px] h-[calc(100vh-68px)] */}
      <div className="flex justify-between items-center ">
        <h2 className="font-medium">Product Detail</h2>
        <HiOutlineX onClick={() => context.closeProductDetail()} />
      </div>
    </aside>
  );
};

export default ProductDetail;
```

### III. Modify the `Card` Component

Located in `src/Components/Card/index.jsx`

```jsx
import { useContext } from "react";
import { AppContext } from "../../Context";
import { HiPlusSm } from "react-icons/hi";

const Card = (data) => {
  const context = useContext(AppContext);

  return (
    <div
      className="bg-amber-700/40 cursor-pointer w-56 h-60 rounded-lg"
      onClick={() => context.openProductDetail()}
    >
      <figure className="relative mb-2 w-full h-4/5">
        <span className="absolute bottom-0 bg-white/60 rounded-lg text-black text-xs m-2 py-0.5 px-2">
          {/* {data.data.category.name} is for the Platzi API (which is not very stable) */}
          {/* {data.data.category.name}  */}
          {/* {data.data.category} is for the Fake Store API */}
          {data.data.category}
        </span>
        <img
          className="rounded-lg w-full h-full object-cover"
          src={data.data.image} // This is for the Fake Store API
          // src={data.data.images} // This is for the Platzi API (which is not very stable)
          alt={data.data.title}
        />
        <HiPlusSm
          onClick={() => context.setCount(context.count + 1)}
          className="absolute top-0 right-0 flex justify-center items-center bg-white rounded-full w-6 h-6 m-2"
        />
      </figure>
      <p className="flex justify-around">
        <span className="text-sm font-light">{data.data.title}</span>
        <span className="text-lg font-medium">${data.data.price}</span>
      </p>
    </div>
  );
};

export default Card;
```

## 14. Show the Products on `ProductDetail`

### I. Modify the `Context` file

Located in `src/Context/index.jsx`

```jsx
import { createContext, useState } from "react";

export const AppContext = createContext();

export const AppProvider = ({ children }) => {
  // Shopping Cart · Increment quantity
  const [count, setCount] = useState(0);

  // Product Detail · Open/Close
  const [isProductDetailOpen, setIsProductDetailOpen] = useState(false);
  const openProductDetail = () => setIsProductDetailOpen(true);
  const closeProductDetail = () => setIsProductDetailOpen(false);

  // Product Detail · Show product
  const [productToShow, setProductToShow] = useState({});

  return (
    <AppContext.Provider
      value={
        count,
        setCount,
        openProductDetail,
        closeProductDetail,
        isProductDetailOpen,
        productToShow,
        setProductToShow,
      }
    >
      {children}
    </AppContext.Provider>
  );
};
```

### II. Modify the `Product Detail` Component

Located in `src/Components/ProductDetail/index.jsx`

```jsx
import { HiOutlineX } from "react-icons/hi";
import { useContext } from "react";
import { AppContext } from "../../Context";

const ProductDetail = () => {
  const context = useContext(AppContext);
  return (
    <aside
      className={`${
        context.isProductDetailOpen ? "flex" : "hidden"
      } flex-col fixed right-0 w-[360px] h-[90vh] border border-black shadow-xl shadow-black rounded-lg bg-white/70 p-2 m-2`}
    >
      {/* top-[68px] w-[360px] h-[calc(100vh-68px)] */}
      <div className="flex justify-between items-center ">
        <h2 className="font-medium">Product Detail</h2>
        <HiOutlineX onClick={() => context.closeProductDetail()} />
      </div>
      <figure className="px-6">
        <img
          className="w-full h-full rounded-lg"
          src={context.productToShow.image}
          alt={context.productToShow.title}
        />
      </figure>
      <p className="flex flex-col p-6">
        <span className="font-medium text-2xl mb-2">
          ${context.productToShow.price}
        </span>
        <span className="font-medium text-md">
          ${context.productToShow.title}
        </span>
        <span className="font-light text-sm">
          ${context.productToShow.description}
        </span>
      </p>
    </aside>
  );
};

export default ProductDetail;
```

### III. Modify the `Card` Component

Located in `src/Components/Card/index.jsx`

```jsx
import { useContext } from "react";
import { AppContext } from "../../Context";
import { HiPlusSm } from "react-icons/hi";

const Card = (data) => {
  const context = useContext(AppContext);

  const showProduct = (productDetail) => {
    context.openProductDetail();
    context.setProductToShow(productDetail);
  };

  return (
    <div
      className="bg-amber-700/40 cursor-pointer w-56 h-60 rounded-lg"
      onClick={() => showProduct(data.data)}
    >
      <figure className="relative mb-2 w-full h-4/5">
        <span className="absolute bottom-0 bg-white/60 rounded-lg text-black text-xs m-2 py-0.5 px-2">
          {data.data.category}
        </span>
        <img
          className="rounded-lg w-full h-full object-cover"
          src={data.data.image}
          alt={data.data.title}
        />
        <HiPlusSm
          onClick={() => context.setCount(context.count + 1)}
          className="absolute top-0 right-0 flex justify-center items-center bg-white rounded-full w-6 h-6 m-2"
        />
      </figure>
      <p className="flex justify-around">
        <span className="text-sm font-light">{data.data.title}</span>
        <span className="text-lg font-medium">${data.data.price}</span>
      </p>
    </div>
  );
};

export default Card;
```

## 15. Add Products to My Order

### I. Modify the `Context` file

Located in `src/Context/index.jsx`

```jsx
import { createContext, useState } from "react";

export const AppContext = createContext();

export const AppProvider = ({ children }) => {
  // Shopping Cart · Increment quantity
  const [count, setCount] = useState(0);

  // Product Detail · Open/Close
  const [isProductDetailOpen, setIsProductDetailOpen] = useState(false);
  const openProductDetail = () => setIsProductDetailOpen(true);
  const closeProductDetail = () => setIsProductDetailOpen(false);

  // Product Detail · Show product
  const [productToShow, setProductToShow] = useState({});

  // Shopping Cart · add product to cart
  const [cartProducts, setCartProducts] = useState([]);

  return (
    <AppContext.Provider
      value={
        count,
        setCount,
        openProductDetail,
        closeProductDetail,
        isProductDetailOpen,
        productToShow,
        setProductToShow,
        cartProducts,
        setCartProducts,
      }
    >
      {children}
    </AppContext.Provider>
  );
};
```

> `value` is missing another set of `{}`. It should look like this: `value={ { ...content here.... } }`

### II. Modify the `Card` Component

Located in `src/Components/Card/index.jsx`

```jsx
import { useContext } from "react";
import { AppContext } from "../../Context";
import { HiPlusSm } from "react-icons/hi";

const Card = (data) => {
  const context = useContext(AppContext);

  const showProduct = (productDetail) => {
    context.openProductDetail();
    context.setProductToShow(productDetail);
  };
  const addProductToCart = (productData) => {
    context.setCount(context.count + 1);
    context.setCartProducts([...context.cartProducts, productData]);
    console.log(context.cartProducts);
  };
  return (
    <div
      className="bg-amber-700/40 cursor-pointer w-56 h-60 rounded-lg"
      onClick={() => showProduct(data.data)}
    >
      <figure className="relative mb-2 w-full h-4/5">
        <span className="absolute bottom-0 bg-white/60 rounded-lg text-black text-xs m-2 py-0.5 px-2">
          {data.data.category}
        </span>
        <img
          className="rounded-lg w-full h-full object-cover"
          src={data.data.image}
          alt={data.data.title}
        />
        <HiPlusSm
          onClick={() => addProductToCart(data.data)}
          className="absolute top-0 right-0 flex justify-center items-center bg-white rounded-full w-6 h-6 m-2"
        />
      </figure>
      <p className="flex justify-around">
        <span className="text-sm font-light">{data.data.title}</span>
        <span className="text-lg font-medium">${data.data.price}</span>
      </p>
    </div>
  );
};

export default Card;
```

## 16. Add a BackUp API

> Include a Backup API in case the current API is down

During the building of this proyect, the Fake APi I was using went down. I had to use another one to continuouse with the course.

### I. Modify the **Home** Page

Located in `src/Pages/Home/index.jsx`

```jsx
import { useState, useEffect } from "react";
import Card from "../../Components/Card";
import Layout from "../../Components/Layout";
import ProductDetail from "../../Components/ProductDetail";
import CheckoutSideMenu from "../../Components/CheckoutSideMenu";

const Home = () => {
  // UseState is a hook to add the info from the API to the state
  const [items, setItems] = useState(null);

  // UseEffect is a hook to fetch the data from the API
  useEffect(() => {
    // fetch("https://fakestoreapi.com/products") // Fake Store API
    fetch("https://api.escuelajs.co/api/v1/products") // Platzi API
      .then((response) => response.json())
      .then((json) => setItems(json));
  }, []);

  return (
    <Layout>
      Home
      <div className="grid gap-4 grid-cols-4 w-full max-w-screen-lg">
        {items?.map((item) => (
          <Card key={item.id} data={item} />
        ))}
      </div>
      <ProductDetail />
      <CheckoutSideMenu />
    </Layout>
  );
};

export default Home;
```

### II. Modify the **Card** Components

Located in `src/Components/Card/index.jsx`

```jsx
import { useContext } from "react";
import { AppContext } from "../../Context";
import { HiPlusSm } from "react-icons/hi";

const Card = (data) => {
  const context = useContext(AppContext);

  const showProduct = (productDetail) => {
    context.openProductDetail();
    context.setProductToShow(productDetail);
  };
  const addProductToCart = (productData) => {
    context.setCount(context.count + 1);
    context.setCartProducts([...context.cartProducts, productData]);
    console.log(context.cartProducts);
  };
  return (
    <div
      className="bg-amber-700/40 cursor-pointer w-56 h-60 rounded-lg"
      onClick={() => showProduct(data.data)}
    >
      <figure className="relative mb-2 w-full h-4/5">
        <span className="absolute bottom-0 bg-white/60 rounded-lg text-black text-xs m-2 py-0.5 px-2">
          {/* Fake Store API: */}
          {/* {data.data.category} */}
          {/* Platzi API: */}
          {data.data.category.name}
        </span>
        <img
          className="rounded-lg w-full h-full object-cover"
          // src={data.data.image} // Fake Store API
          src={data.data.images} // Platzi API
          alt={data.data.title} // Fake Store API
        />
        <HiPlusSm
          onClick={() => addProductToCart(data.data)}
          className="absolute top-0 right-0 flex justify-center items-center bg-white rounded-full w-6 h-6 m-2"
        />
      </figure>
      <p className="flex justify-around">
        <span className="text-sm font-light">{data.data.title}</span>
        <span className="text-lg font-medium">${data.data.price}</span>
      </p>
    </div>
  );
};

export default Card;
```

### III. Modify the **ProductDetail** Components

Located in `src/Components/ProductDetail/index.jsx`

```jsx
import { HiOutlineX } from "react-icons/hi";
import { useContext } from "react";
import { AppContext } from "../../Context";

const ProductDetail = () => {
  const context = useContext(AppContext);
  return (
    <aside
      className={`${
        context.isProductDetailOpen ? "flex" : "hidden"
      } flex-col fixed right-0 w-[360px] h-[90vh] border border-black shadow-xl shadow-black rounded-lg bg-white/70 p-2 m-2`}
    >
      {/* top-[68px] w-[360px] h-[calc(100vh-68px)] */}
      <div className="flex justify-between items-center ">
        <h2 className="font-medium">Product Detail</h2>
        <HiOutlineX onClick={() => context.closeProductDetail()} />
      </div>
      <figure className="px-6">
        <img
          className="w-full h-full rounded-lg"
          alt={context.productToShow.title}
          // Platzi API:
          src={context.productToShow.images}
          // Fake Store API:
          // src={context.productToShow.image}
        />
      </figure>
      <p className="flex flex-col p-6">
        <span className="font-medium text-2xl mb-2">
          ${context.productToShow.price}
        </span>
        <span className="font-medium text-md">
          ${context.productToShow.title}
        </span>
        <span className="font-light text-sm">
          {context.productToShow.description}
        </span>
      </p>
    </aside>
  );
};

export default ProductDetail;
```

## 17. Create the **Side Menu** for the Shopping cart

### I. Create a `CheckoutSideMenu` Component

Located in `src/Components/CheckoutSideMenu/index.jsx`

```jsx
import { useContext } from "react";
import { HiOutlineX } from "react-icons/hi";
import { AppContext } from "../../Context";

const CheckoutSideMenu = () => {
  const context = useContext(AppContext);
  return (
    <aside
      className={`${
        context.isCheckoutSideMenuOpen ? "flex" : "hidden"
      } flex-col fixed right-0 top-20 w-[360px] h-[90vh] border border-black shadow-xl shadow-black rounded-lg bg-white/70 p-2 m-2`}
    >
      <div className="flex justify-between items-center ">
        <h2 className="font-medium">My Order</h2>
        <div>
          <HiOutlineX onClick={() => context.closeCheckoutSideMenu()} />
        </div>
      </div>
    </aside>
  );
};

export default CheckoutSideMenu;
```

### II. Modify the `Context` file

Located in `src/Context/index.jsx`

```jsx
import { createContext, useState } from "react";

export const AppContext = createContext();

export const AppProvider = ({ children }) => {
  // Shopping Cart · Increment quantity
  const [count, setCount] = useState(0);

  // Product Detail · Open/Close
  const [isProductDetailOpen, setIsProductDetailOpen] = useState(false);
  const openProductDetail = () => setIsProductDetailOpen(true);
  const closeProductDetail = () => setIsProductDetailOpen(false);

  // Product Detail · Show product
  const [productToShow, setProductToShow] = useState({});

  // Shopping Cart · add product to cart
  const [cartProducts, setCartProducts] = useState([]);

  // Checkout Side Menu · Open/Close
  const [isCheckoutSideMenuOpen, setIsCheckoutSideMenuOpen] = useState(false);
  const openCheckoutSideMenu = () => setIsCheckoutSideMenuOpen(true);
  const closeCheckoutSideMenu = () => setIsCheckoutSideMenuOpen(false);

  return (
    <AppContext.Provider
      value={
        count,
        setCount,
        openProductDetail,
        closeProductDetail,
        isProductDetailOpen,
        productToShow,
        setProductToShow,
        cartProducts,
        setCartProducts,
        isCheckoutSideMenuOpen,
        openCheckoutSideMenu,
        closeCheckoutSideMenu,
      }
    >
      {children}
    </AppContext.Provider>
  );
};
```

> `value` is missing another set of `{}`. It should look like this: `value={ { ...content here.... } }`

### III. Modify the **Card** Components

Located in `src/Components/Card/index.jsx`

```jsx
import { useContext } from "react";
import { AppContext } from "../../Context";
import { HiPlusSm } from "react-icons/hi";

const Card = (data) => {
  const context = useContext(AppContext);

  const showProduct = (productDetail) => {
    context.openProductDetail();
    context.setProductToShow(productDetail);
    context.closeCheckoutSideMenu();
  };
  const addProductToCart = (event, productData) => {
    event.stopPropagation(); // Para que no se abra el modal de detalle de producto

    context.setCount(context.count + 1);
    context.setCartProducts([...context.cartProducts, productData]);
    // console.log(context.cartProducts);
    context.openCheckoutSideMenu();
    context.closeProductDetail();
  };
  return (
    <div
      className="bg-amber-700/40 cursor-pointer w-56 h-60 rounded-lg"
      onClick={() => showProduct(data.data)}
    >
      <figure className="relative mb-2 w-full h-4/5">
        <span className="absolute bottom-0 bg-white/60 rounded-lg text-black text-xs m-2 py-0.5 px-2">
          {/* Fake Store API: */}
          {/* {data.data.category} */}
          {/* Platzi API: */}
          {data.data.category.name}
        </span>
        <img
          className="rounded-lg w-full h-full object-cover"
          // src={data.data.image} // Fake Store API
          src={data.data.images} // Platzi API
          alt={data.data.title} // Fake Store API
        />
        <HiPlusSm
          onClick={(event) => addProductToCart(event, data.data)}
          className="absolute top-0 right-0 flex justify-center items-center bg-white rounded-full w-6 h-6 m-2"
        />
      </figure>
      <p className="flex justify-around">
        <span className="text-sm font-light">{data.data.title}</span>
        <span className="text-lg font-medium">${data.data.price}</span>
      </p>
    </div>
  );
};

export default Card;
```

### IV. Modify the `App` file

Located in `src/Pages/App/index.jsx`

```jsx
import { useRoutes, BrowserRouter } from "react-router-dom";
import { AppProvider } from "../../Context";
import Home from "../Home";
import MyAccount from "../MyAccount";
import MyOrder from "../MyOrder";
import MyOrders from "../MyOrders";
import NotFound from "../NotFound";
import SignIn from "../SignIn";
import Navbar from "../../Components/Navbar";
// import TestNavbar from "../../Components/TestJp/Navbar.jsx";
import "./App.css";
import CheckoutSideMenu from "../../Components/CheckoutSideMenu";

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
    <AppProvider>
      <BrowserRouter>
        <AppRoutes />
        <Navbar />
        <CheckoutSideMenu />
      </BrowserRouter>
    </AppProvider>
  );
};
export default App;
```

## 18. **Order Card** Component

### I. Create the `OrderCard` Component

Located in `src/Components/OrderCard/index.jsx`

```jsx
import { HiOutlineX } from "react-icons/hi";
import { AppContext } from "../../Context";
import { useContext } from "react";

const OrderCard = (props) => {
  const { title, imageUrl, price } = props;
  const context = useContext(AppContext);
  return (
    <div className="flex justify-between items-center">
      <div className="flex items-center gap-2">
        <figure className="w-20 h-20 m-0.5">
          <img
            className="w-full h-full rounded-lg object-cover"
            src={imageUrl}
            alt={title}
          />
        </figure>
        <p className="text-sm font-light">{title}</p>
      </div>
      <div className="flex items-center gap-2">
        <p className="text-lg font-medium">$ {price}</p>

        <>
          <HiOutlineX
            onClick={() => context.closeCheckoutSideMenu()}
            className="h-6 w-6 text-black cursor-pointer"
          />
        </>
      </div>
    </div>
  );
};

export default OrderCard;
```

### II. Modify the `CheckoutSideMenu` Component

Located in `src/Components/CheckoutSideMenu/index.jsx`

```jsx
import { useContext } from "react";
import { HiOutlineX } from "react-icons/hi";
import { AppContext } from "../../Context";
import OrderCard from "../OrderCard";

const CheckoutSideMenu = () => {
  const context = useContext(AppContext);
  return (
    <aside
      className={`${
        context.isCheckoutSideMenuOpen ? "flex" : "hidden"
      } flex-col fixed right-0 top-20 w-[360px] h-[90vh] border border-black shadow-xl shadow-black rounded-lg bg-white/70 p-2 m-2`}
    >
      <div className="flex justify-between items-center p-6">
        <h2 className="font-medium">My Order</h2>
        <div>
          <HiOutlineX onClick={() => context.closeCheckoutSideMenu()} />
        </div>
      </div>
      <div className="px-6">
        {context.cartProducts.map((product) => (
          <OrderCard
            key={product.id}
            title={product.title}
            // imageUrl={product.image} // Fake Store API
            imageUrl={product.images} // Platzi API
            price={product.price}
          />
        ))}
      </div>
    </aside>
  );
};

export default CheckoutSideMenu;
```

## 19. Don't Repeat Products in Cart

### I. Modify the **Card** Components

Located in `src/Components/Card/index.jsx`

```jsx
import { useContext } from "react";
import { AppContext } from "../../Context";
import { HiCheck, HiPlusSm } from "react-icons/hi";

const Card = (data) => {
  const context = useContext(AppContext);

  const showProduct = (productDetail) => {
    context.openProductDetail();
    context.setProductToShow(productDetail);
    context.closeCheckoutSideMenu();
  };
  const addProductToCart = (event, productData) => {
    event.stopPropagation(); // Para que no se abra el modal de detalle de producto

    context.setCount(context.count + 1);
    context.setCartProducts([...context.cartProducts, productData]);
    // console.log(context.cartProducts);
    context.openCheckoutSideMenu();
    context.closeProductDetail();
  };

  // Check if the product is in the cart:
  const renderIcon = (id) => {
    const productIsInCart =
      context.cartProducts.filter((product) => product.id === id).length > 0;

    if (productIsInCart) {
      return (
        <HiCheck className="absolute top-0 right-0 flex justify-center items-center bg-black rounded-full w-6 h-6 m-2 text-white" />
      );
    } else {
      return (
        <HiPlusSm
          onClick={(event) => addProductToCart(event, data.data)}
          className="absolute top-0 right-0 flex justify-center items-center bg-white rounded-full w-6 h-6 m-2"
        />
      );
    }
  };
  return (
    <div
      className="bg-amber-700/40 cursor-pointer w-56 h-60 rounded-lg"
      onClick={() => showProduct(data.data)}
    >
      <figure className="relative mb-2 w-full h-4/5">
        <span className="absolute bottom-0 bg-white/60 rounded-lg text-black text-xs m-2 py-0.5 px-2">
          {/* Fake Store API: */}
          {/* {data.data.category} */}
          {/* Platzi API: */}
          {data.data.category.name}
        </span>
        <img
          className="rounded-lg w-full h-full object-cover"
          // src={data.data.image} // Fake Store API
          src={data.data.images} // Platzi API
          alt={data.data.title} // Fake Store API
        />
        {renderIcon(data.data.id)}
      </figure>
      <p className="flex justify-around">
        <span className="text-sm font-light">{data.data.title}</span>
        <span className="text-lg font-medium">${data.data.price}</span>
      </p>
    </div>
  );
};

export default Card;
```

## 20. To Modify the Quantity of the Products on my Order

> In beta for now. I didnt actually add it to the project.

### Modify the `OrderCard` Component

Located in `src/Components/OrderCard/index.jsx`

- Increase & decrease the quantity of items.
- Update the price depending on the quantity of items.

```jsx
import { HiOutlineX } from "react-icons/hi";
import { AppContext } from "../../Context";
import { useContext, useState } from "react";

const OrderCard = (props) => {
  const { title, imageUrl, price } = props;
  const context = useContext(AppContext);

  // quantity of the item in the cart:
  const [quantity, setQuantity] = useState(1);

  const incrementQuantity = () => {
    setQuantity(quantity + 1);
  };
  const decrementQuantity = () => {
    if (quantity > 1) {
      setQuantity(quantity - 1);
    }
  };

  return (
    <div className="flex justify-between items-center">
      <div className="flex items-center gap-2">
        <figure className="w-20 h-20 m-0.5">
          <img
            className="w-full h-full rounded-lg object-cover"
            src={imageUrl}
            alt={title}
          />
        </figure>
        <p className="text-sm font-light">{title}</p>
      </div>
      <div className="flex items-center gap-2">
        <p className="text-lg font-medium">${price * quantity}</p>
        <button onClick={decrementQuantity}>-</button>
        <p>{quantity} item</p>
        <button onClick={incrementQuantity}>+</button>
        <>
          <HiOutlineX
            onClick={() => context.closeCheckoutSideMenu()}
            className="h-6 w-6 text-black cursor-pointer"
          />
        </>
      </div>
    </div>
  );
};

export default OrderCard;
```

> I asked Copilote with this and it was pretty simple.

## 21. Use Components from Shadcn-Ui

> In beta for now. I didnt actually add it to the project.

### SetUp [Shadcn UI](https://ui.shadcn.com/) in the Project

### I. Install [Shadcn UI](https://ui.shadcn.com/docs/installation/vite) for Vite.

[Shadcn UI](https://ui.shadcn.com/). is a library with multiple designed components that you can copy and paste into your apps. Accessible. Customizable. Open Source. it will be use to style the page.

- Create a `jsconfig.json` file by adding the following code to the paths section:

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

- Install Node.
  ```bash
  npm i -D @types/node
  ```
- Overwrite the `vite.config.ts` file:

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

- Run the shadcn-ui init command to setup your project:
  ```bash
  npx shadcn-ui@latest init
  ```
- Configure `components.json`

You will be asked a few questions to configure `components.json`:

```bash
Would you like to use TypeScript (recommended)? `no` / yes ... no
Which style would you like to use? › `Default`
Which color would you like to use as base color? › `Slate`
Where is your global CSS file? › › `src/Pages/App/App.css`
Do you want to use CSS variables for colors? › `no` / yes ... no
Where is your tailwind.config.js located? › `tailwind.config.js`
Configure the import alias for components: › `@/components`
Configure the import alias for utils: › `@/lib/utils`
Are you using React Server Components? › no / `yes` ... yes
√ Write configuration to components.json. Proceed? ... yes
```

This will install all the necesary components

### II. Add a **Dropdown Menu** Component from [shadcn-UI](https://ui.shadcn.com/docs/components/dropdown-menu)

- Install component

```jsx
npx shadcn-ui@latest add dropdown-menu
```

- Modify the `Order`

## 22. Delete an Item From the Order

### I. Modify the `CheckoutSideMenu` Component

Located in `src/Components/CheckoutSideMenu/index.jsx`

```jsx
import { useContext } from "react";
import { HiOutlineX } from "react-icons/hi";
import { AppContext } from "../../Context";
import OrderCard from "../OrderCard";

const CheckoutSideMenu = () => {
  const context = useContext(AppContext);

  const handleDeleteProduct = (id) => {
    const newCartProducts = context.cartProducts.filter(
      (product) => product.id !== id
    );
    context.setCartProducts(newCartProducts);
    context.setCart(context.cart - 1);
  };

  return (
    <aside
      className={`${
        context.isCheckoutSideMenuOpen ? "flex" : "hidden"
      } flex-col fixed right-0 top-20 w-[360px] h-[90vh] border border-black shadow-xl shadow-black rounded-lg bg-white/70 p-2 m-2`}
    >
      <div className="flex justify-between items-center p-6">
        <h2 className="font-medium">My Order</h2>
        <div>
          <HiOutlineX onClick={() => context.closeCheckoutSideMenu()} />
        </div>
      </div>
      <div className="px-6 overflow-y-scroll">
        {context.cartProducts.map((product) => (
          <OrderCard
            key={product.id}
            id={product.id}
            title={product.title}
            // imageUrl={product.image} // Fake Store API
            imageUrl={product.images} // Platzi API
            price={product.price}
            quantity={product.quantity}
            handleDeleteProduct={handleDeleteProduct}
          />
        ))}
      </div>
    </aside>
  );
};

export default CheckoutSideMenu;
```

### II. Modify the `OrderCard` Component

Located in `src/Components/OrderCard/index.jsx`

```jsx
import { HiOutlineTrash } from "react-icons/hi";
import { AppContext } from "../../Context";
import { useContext } from "react";

const OrderCard = (props) => {
  const { id, title, imageUrl, price, handleDeleteProduct } = props;

  return (
    <div className="flex justify-between items-center">
      <div className="flex items-center gap-2">
        <figure className="w-20 h-20 m-0.5">
          <img
            className="w-full h-full rounded-lg object-cover"
            src={imageUrl}
            alt={title}
          />
        </figure>
        {/* <p className="text-sm font-light">{title}</p> */}
      </div>
      <div className="flex items-center gap-2">
        <p className="text-lg font-medium">${price}</p>

        <>
          <HiOutlineTrash
            onClick={() => handleDeleteProduct(id)}
            className="h-6 w-6 text-black cursor-pointer"
          />
        </>
      </div>
    </div>
  );
};

export default OrderCard;
```

## 23. Total Items and Total Price of the Order

### I. Create a `Utils` file

Located in `src/Utils/index.js`

```js
// **
// * @description: This function calculates the total price of the new order
// * @param {Array} products
// * @return: {Number} total price
// **

export const totalPrice = (products) => {
  let sum = 0;
  products.forEach((product) => (sum += product.price));
  return sum;
};
```

### II. Modify the `CheckoutSideMenu` Component

Located in `src/Components/CheckoutSideMenu/index.jsx`

```jsx
import { useContext } from "react";
import { HiOutlineX } from "react-icons/hi";
import { AppContext } from "../../Context";
import OrderCard from "../OrderCard";
import { totalPrice } from "../../Utils/index.js";

const CheckoutSideMenu = () => {
  const context = useContext(AppContext);

  const handleDeleteProduct = (id) => {
    const newCartProducts = context.cartProducts.filter(
      (product) => product.id !== id
    );
    context.setCartProducts(newCartProducts);
    context.setCart(context.cart - 1);
  };

  return (
    <aside
      className={`${
        context.isCheckoutSideMenuOpen ? "flex" : "hidden"
      } flex-col fixed right-0 top-20 w-[360px] h-[90vh] border border-black shadow-xl shadow-black rounded-lg bg-white/70 p-2 m-2`}
    >
      <div className="flex justify-between items-center p-6">
        <h2 className="font-medium">My Order</h2>
        <div>
          <HiOutlineX onClick={() => context.closeCheckoutSideMenu()} />
        </div>
      </div>
      <div className="px-6 overflow-y-scroll">
        {context.cartProducts.map((product) => (
          <OrderCard
            key={product.id}
            id={product.id}
            title={product.title}
            // imageUrl={product.image} // Fake Store API
            imageUrl={product.images} // Platzi API
            price={product.price}
            quantity={product.quantity}
            handleDeleteProduct={handleDeleteProduct}
          />
        ))}
      </div>
      <div className="p-6">
        <p>
          <span className="font-medium">Total</span>
          <span className="font-medium">
            ${totalPrice(context.cartProducts)}
          </span>
        </p>
      </div>
    </aside>
  );
};

export default CheckoutSideMenu;
```

## 24. Create a New Order

## I. Modify the `Context` file

Located in `src/Context/index.jsx`

```jsx
import { createContext, useState } from "react";

export const AppContext = createContext();

export const AppProvider = ({ children }) => {
  // Shopping Cart · Increment quantity
  const [cart, setCart] = useState(0);

  // Product Detail · Open/Close
  const [isProductDetailOpen, setIsProductDetailOpen] = useState(false);
  const openProductDetail = () => setIsProductDetailOpen(true);
  const closeProductDetail = () => setIsProductDetailOpen(false);

  // Product Detail · Show product
  const [productToShow, setProductToShow] = useState({});

  // Shopping Cart · add product to cart
  const [cartProducts, setCartProducts] = useState([]);

  // Checkout Side Menu · Open/Close
  const [isCheckoutSideMenuOpen, setIsCheckoutSideMenuOpen] = useState(false);
  const openCheckoutSideMenu = () => setIsCheckoutSideMenuOpen(true);
  const closeCheckoutSideMenu = () => setIsCheckoutSideMenuOpen(false);

  // Shopping Cart · Order
  const [order, setOrder] = useState([]);

  return (
    <AppContext.Provider
      value={
        cart,
        setCart,
        openProductDetail,
        closeProductDetail,
        isProductDetailOpen,
        productToShow,
        setProductToShow,
        cartProducts,
        setCartProducts,
        isCheckoutSideMenuOpen,
        openCheckoutSideMenu,
        closeCheckoutSideMenu,
        order,
        setOrder,
      }
    >
      {children}
    </AppContext.Provider>
  );
};
```

> `value` is missing another set of `{}`. It should look like this: `value={ { ...content here.... } }`

### II. Modify the `CheckoutSideMenu` Component

Located in `src/Components/CheckoutSideMenu/index.jsx`

```jsx
import { useContext } from "react";
import { HiOutlineX } from "react-icons/hi";
import { AppContext } from "../../Context";
import OrderCard from "../OrderCard";
import { totalPrice } from "../../Utils/index.js";

const CheckoutSideMenu = () => {
  const context = useContext(AppContext);

  const handleDeleteProduct = (id) => {
    const newCartProducts = context.cartProducts.filter(
      (product) => product.id !== id
    );
    context.setCartProducts(newCartProducts);
    context.setCart(context.cart - 1);
  };

  const handleCheckout = () => {
    const orderToAdd = {
      date: "2021-10-10",
      products: context.cartProducts,
      totalProducts: context.cartProducts.length,
      totalPrice: totalPrice(context.cartProducts),
    };

    context.setOrder([...context.order, orderToAdd]);
    context.setCartProducts([]);
  };

  return (
    <aside
      className={`${
        context.isCheckoutSideMenuOpen ? "flex" : "hidden"
      } flex-col fixed right-0 top-20 w-[360px] h-[90vh] border border-black shadow-xl shadow-black rounded-lg bg-white/70 p-2 m-2`}
    >
      <div className="flex justify-between items-center p-6">
        <h2 className="font-medium">My Order</h2>
        <div>
          <HiOutlineX onClick={() => context.closeCheckoutSideMenu()} />
        </div>
      </div>
      <div className="px-6 overflow-y-scroll flex-1">
        {context.cartProducts.map((product) => (
          <OrderCard
            key={product.id}
            id={product.id}
            title={product.title}
            // imageUrl={product.image} // Fake Store API
            imageUrl={product.images} // Platzi API
            price={product.price}
            quantity={product.quantity}
            handleDeleteProduct={handleDeleteProduct}
          />
        ))}
      </div>
      <div className="p-6">
        <p className="flex justify-around items-center ">
          <span className="font-light">Total</span>
          <span className="font-medium">
            ${totalPrice(context.cartProducts)}
          </span>
        </p>
        <button
          className="w-full bg-black text-white font-medium py-2 rounded-lg mt-2 hover:bg-gray-900/50 transition duration-300"
          onClick={() => handleCheckout()}
        >
          Checkout
        </button>
      </div>
    </aside>
  );
};

export default CheckoutSideMenu;
```

## 25. Checkout Products from Cart to My Last Order

### I. Modify the `CheckoutSideMenu` Component

Located in `src/Components/CheckoutSideMenu/index.jsx`

```jsx
import { useContext } from "react";
import { Link } from "react-router-dom";
import { HiOutlineX } from "react-icons/hi";
import { AppContext } from "../../Context";
import OrderCard from "../OrderCard";
import { totalPrice } from "../../Utils/index.js";

const CheckoutSideMenu = () => {
  const context = useContext(AppContext);

  const handleDeleteProduct = (id) => {
    const newCartProducts = context.cartProducts.filter(
      (product) => product.id !== id
    );
    context.setCartProducts(newCartProducts);
    context.setCart(context.cart - 1);
  };

  const handleCheckout = () => {
    const orderToAdd = {
      date: "2021-10-10",
      products: context.cartProducts,
      totalProducts: context.cartProducts.length,
      totalPrice: totalPrice(context.cartProducts),
    };

    context.setOrder([...context.order, orderToAdd]);
    context.setCartProducts([]);
  };

  return (
    <aside
      className={`${
        context.isCheckoutSideMenuOpen ? "flex" : "hidden"
      } flex-col fixed right-0 top-20 w-[360px] h-[90vh] border border-black shadow-xl shadow-black rounded-lg bg-white/70 p-2 m-2`}
    >
      <div className="flex justify-between items-center p-6">
        <h2 className="font-medium">My Order</h2>
        <div>
          <HiOutlineX onClick={() => context.closeCheckoutSideMenu()} />
        </div>
      </div>
      <div className="px-6 overflow-y-scroll flex-1">
        {context.cartProducts.map((product) => (
          <OrderCard
            key={product.id}
            id={product.id}
            title={product.title}
            // imageUrl={product.image} // Fake Store API
            imageUrl={product.images} // Platzi API
            price={product.price}
            quantity={product.quantity}
            handleDeleteProduct={handleDeleteProduct}
          />
        ))}
      </div>
      <div className="p-6">
        <p className="flex justify-around items-center ">
          <span className="font-light">Total</span>
          <span className="font-medium">
            ${totalPrice(context.cartProducts)}
          </span>
        </p>
        <Link to="/my-orders/last">
          <button
            className="w-full bg-black text-white font-medium py-2 rounded-lg mt-2 hover:bg-gray-900/50 transition duration-300"
            onClick={() => handleCheckout()}
          >
            Checkout
          </button>
        </Link>
      </div>
    </aside>
  );
};

export default CheckoutSideMenu;
```

### II. Modify the `OrderCard` Component

Located in `src/Components/OrderCard/index.jsx`

```jsx
import { HiOutlineTrash } from "react-icons/hi";
import { AppContext } from "../../Context";
import { useContext } from "react";

const OrderCard = (props) => {
  const { id, title, imageUrl, price, handleDeleteProduct } = props;
  let renderTrash;
  if (handleDeleteProduct) {
    renderTrash = (
      <HiOutlineTrash
        onClick={() => handleDeleteProduct(id)}
        className="cursor-pointer"
      />
    );
  }
  return (
    <div className="flex justify-between items-center">
      <div className="flex items-center gap-2">
        <figure className="w-20 h-20 m-0.5">
          <img
            className="w-full h-full rounded-lg object-cover"
            src={imageUrl}
            alt={title}
          />
        </figure>
        {/* <p className="text-sm font-light">{title}</p> */}
      </div>
      <div className="flex items-center gap-2">
        <p className="text-lg font-medium">${price}</p>

        <>{renderTrash} </>
      </div>
    </div>
  );
};

export default OrderCard;
```

### III. Modify the `App` file

Located in `src/Pages/App/index.jsx`

```jsx
import { useRoutes, BrowserRouter } from "react-router-dom";
import { AppProvider } from "../../Context";
import Home from "../Home";
import MyAccount from "../MyAccount";
import MyOrder from "../MyOrder";
import MyOrders from "../MyOrders";
import NotFound from "../NotFound";
import SignIn from "../SignIn";
import Navbar from "../../Components/Navbar";
// import TestNavbar from "../../Components/TestJp/Navbar.jsx";
import "./App.css";
import CheckoutSideMenu from "../../Components/CheckoutSideMenu";

const AppRoutes = () => {
  let routes = useRoutes([
    { path: "/", element: <Home /> },
    { path: "/my-account", element: <MyAccount /> },
    { path: "/my-order", element: <MyOrder /> },
    { path: "/my-orders", element: <MyOrders /> },
    { path: "/my-orders/last", element: <MyOrder /> },
    { path: "/sign-in", element: <SignIn /> },
    { path: "*", element: <NotFound /> },
  ]);
  return routes;
};

const App = () => {
  return (
    <AppProvider>
      <BrowserRouter>
        <AppRoutes />
        <Navbar />
        <CheckoutSideMenu />
      </BrowserRouter>
    </AppProvider>
  );
};
export default App;
```

### IV. Modify the `MyOrder` Component

Located in `src/Components/MyOrder/index.jsx`

```jsx
import { useContext } from "react";
import Layout from "../../Components/Layout";
import OrderCard from "../../Components/OrderCard";
import { AppContext } from "../../Context";

const MyOrder = () => {
  const context = useContext(AppContext);
  // console.log(context.order?.slice(-1)[0]);
  return (
    <Layout>
      <h1>MyOrder</h1>

      <div className="flex flex-col w-80">
        {context.order?.slice(-1)[0].products.map((product) => (
          <OrderCard
            key={product.id}
            id={product.id}
            title={product.title}
            // imageUrl={product.image} // Fake Store API
            imageUrl={product.images} // Platzi API
            price={product.price}
            quantity={product.quantity}
          />
        ))}
      </div>
    </Layout>
  );
};

export default MyOrder;
```

## 26. My Orders Page

### I. Create the **Order<ins>s</ins>Card** Component. (<ins>not</ins> `OrderCard`)

> **Order<ins>s</ins>Card** is a **NEW** file. It is not the same as `OrderCard`.

Located in `src/Components/OrdersCard/index.jsx`

```jsx
// import {} from "react-icons/hi";

const OrdersCard = (props) => {
  const { totalPrice, totalProducts } = props;
  return (
    <div className="flex justify-between items-center w-80 bg-slate-500">
      <p className="flex-col justify-center items-center text-white text-2xl font-bold">
        <span className="text-gray-400 text-xl p-5">date</span>
        <span className="p-2">{totalProducts} items</span>
        <span>${totalPrice}</span>
      </p>
    </div>
  );
};

export default OrdersCard;
```

### II. Modify the `MyOrders` Page

Located in `src/Pages/MyOrders/index.jsx`

```jsx
import { useContext } from "react";
import Layout from "../../Components/Layout";
import { AppContext } from "../../Context";
import OrdersCard from "../../Components/OrdersCard";
import { Link } from "react-router-dom";

const MyOrders = () => {
  const context = useContext(AppContext);

  return (
    <Layout>
      <h1 className="">MyOrders</h1>
      {context.order.map((order, index) => (
        <Link to={`/my-orders/${index}`} key={index}>
          <OrdersCard
            totalProducts={order.totalProducts}
            totalPrice={order.totalPrice}
          />
        </Link>
      ))}
    </Layout>
  );
};

export default MyOrders;
```

### III. Modify the `MyOrder` Page

Located in `src/Pages/MyOrder/index.jsx`

```jsx
import { useContext } from "react";
import Layout from "../../Components/Layout";
import OrderCard from "../../Components/OrderCard";
import { AppContext } from "../../Context";
import { HiChevronLeft } from "react-icons/hi";
import { Link } from "react-router-dom";

const MyOrder = () => {
  const context = useContext(AppContext);

  const currentPath = window.location.pathname;
  let index = currentPath.substring(currentPath.lastIndexOf("/") + 1);

  if (index === "last") {
    index = context.order?.length - 1;
  }
  return (
    <Layout>
      <div className="flex items-center justify-center relative w-80">
        <Link to="/my-orders" className="absolute left-0">
          <HiChevronLeft className="h-4 w-4 cursor-pointer" />
        </Link>
        <h1 className="">My Order</h1>
      </div>
      <div className="flex flex-col w-80">
        {context.order?.[index]?.products.map((product) => (
          <OrderCard
            key={product.id}
            id={product.id}
            title={product.title}
            // imageUrl={product.image} // Fake Store API
            imageUrl={product.images} // Platzi API
            price={product.price}
            quantity={product.quantity}
          />
        ))}
      </div>
    </Layout>
  );
};

export default MyOrder;
```

### IV. Modify the `App` file

By adding a new route: `{ path: "/my-orders/:id", element: <MyOrder /> },`

Located in `src/Pages/App/index.jsx`

```jsx
import { useRoutes, BrowserRouter } from "react-router-dom";
import { AppProvider } from "../../Context";
import Home from "../Home";
import MyAccount from "../MyAccount";
import MyOrder from "../MyOrder";
import MyOrders from "../MyOrders";
import NotFound from "../NotFound";
import SignIn from "../SignIn";
import Navbar from "../../Components/Navbar";
// import TestNavbar from "../../Components/TestJp/Navbar.jsx";
import "./App.css";
import CheckoutSideMenu from "../../Components/CheckoutSideMenu";

const AppRoutes = () => {
  let routes = useRoutes([
    { path: "/", element: <Home /> },
    { path: "/my-account", element: <MyAccount /> },
    { path: "/my-order", element: <MyOrder /> },
    { path: "/my-orders", element: <MyOrders /> },
    { path: "/my-orders/last", element: <MyOrder /> },
    { path: "/my-orders/:id", element: <MyOrder /> },
    { path: "/sign-in", element: <SignIn /> },
    { path: "*", element: <NotFound /> },
  ]);
  return routes;
};

const App = () => {
  return (
    <AppProvider>
      <BrowserRouter>
        <AppRoutes />
        <Navbar />
        <CheckoutSideMenu />
      </BrowserRouter>
    </AppProvider>
  );
};
export default App;
```

## 27. Refactor of my `Home` Page

Refactor means to change the code of my project. In this case, I made a refactor to use items, setItems and other functionalities of my website that were only available in a local state. In this case it was only working on the home.jsx file and now I need to use them somewhere else.

### I. Modify the `Home` Component

Located in `src/Components/Home/index.jsx`

```jsx
import { useContext } from "react";
import Card from "../../Components/Card";
import Layout from "../../Components/Layout";
import ProductDetail from "../../Components/ProductDetail";
import { AppContext } from "../../Context";

const Home = () => {
  const context = useContext(AppContext);
  return (
    <Layout>
      <h1>Home</h1>
      <div className="grid gap-4 grid-cols-4 w-full max-w-screen-lg">
        {context.items?.map((item) => (
          <Card key={item.id} data={item} />
        ))}
      </div>
      <ProductDetail />
    </Layout>
  );
};

export default Home;
```

## II. Modify the `Context` file

Located in `src/Context/index.jsx`

```jsx
import { createContext, useEffect, useState } from "react";

export const AppContext = createContext();

export const AppProvider = ({ children }) => {
  // Home · Get Products - Fetch data from API
  // UseState is a hook to add the info from the API to the state
  const [items, setItems] = useState(null);

  // UseEffect is a hook to fetch the data from the API
  useEffect(() => {
    // fetch("https://fakestoreapi.com/products") // Fake Store API
    fetch("https://api.escuelajs.co/api/v1/products") // Platzi API
      .then((response) => response.json())
      .then((json) => setItems(json));
  }, []);

  // Shopping Cart · Increment quantity
  const [count, setCount,] = useState(0);

  // Product Detail · Open/Close
  const [isProductDetailOpen, setIsProductDetailOpen] = useState(false);
  const openProductDetail = () => setIsProductDetailOpen(true);
  const closeProductDetail = () => setIsProductDetailOpen(false);

  // Product Detail · Show product
  const [productToShow, setProductToShow] = useState({});

  // Shopping Cart · add product to cart
  const [cartProducts, setCartProducts] = useState([]);

  // Checkout Side Menu · Open/Close
  const [isCheckoutSideMenuOpen, setIsCheckoutSideMenuOpen] = useState(false);
  const openCheckoutSideMenu = () => setIsCheckoutSideMenuOpen(true);
  const closeCheckoutSideMenu = () => setIsCheckoutSideMenuOpen(false);

  // Shopping Cart · Order
  const [order, setOrder] = useState([]);

  return (
    <AppContext.Provider
      value={
        items,
        setItems,
        count,
        setCount,
        openProductDetail,
        closeProductDetail,
        isProductDetailOpen,
        productToShow,
        setProductToShow,
        cartProducts,
        setCartProducts,
        isCheckoutSideMenuOpen,
        openCheckoutSideMenu,
        closeCheckoutSideMenu,
        order,
        setOrder,
      }
    >
      {children}
    </AppContext.Provider>
  );
};
```

> `value` is missing another set of `{}`. It should look like this: `value={ { ...content here.... } }`

> [Compare old version with the new version of home](https://github.com/JuanPabloDiaz/platzi_shopi/commit/a0801b65fa4d8bc1791db542a69166181c3df37b)

## 28. Seach by Products

### I. Modify the `Home` Component

Add an input to search products

Located in `src/Components/Home/index.jsx`

```jsx
import { useContext } from "react";
import Card from "../../Components/Card";
import Layout from "../../Components/Layout";
import ProductDetail from "../../Components/ProductDetail";
import { AppContext } from "../../Context";

const Home = () => {
  const context = useContext(AppContext);
  return (
    <Layout>
      <div className="flex items-center justify-center relative w-80 mb-4">
        <h1 className="font-medium text-xl">Products</h1>
      </div>
      <input
        type="text"
        placeholder="Search a product..."
        className="border border-black rounded-xl w-96 px-4 py-2 mb-4"
        onChange={(event) => context.setSearchByTitle(event.target.value)}
      />
      <div className="grid gap-4 grid-cols-4 w-full max-w-screen-lg">
        {context.items?.map((item) => (
          <Card key={item.id} data={item} />
        ))}
      </div>
      <ProductDetail />
    </Layout>
  );
};

export default Home;
```

## II. Modify the `Context` file

Add the logic to search products. Searching by title(input)

Located in `src/Context/index.jsx`

```jsx
import { createContext, useEffect, useState } from "react";

export const AppContext = createContext();

export const AppProvider = ({ children }) => {
  // Shopping Cart · Increment quantity
  const [cart, setCart] = useState(0);

  // Product Detail · Open/Close
  const [isProductDetailOpen, setIsProductDetailOpen] = useState(false);
  const openProductDetail = () => setIsProductDetailOpen(true);
  const closeProductDetail = () => setIsProductDetailOpen(false);

  // Product Detail · Show product
  const [productToShow, setProductToShow] = useState({});

  // Shopping Cart · add product to cart
  const [cartProducts, setCartProducts] = useState([]);

  // Checkout Side Menu · Open/Close
  const [isCheckoutSideMenuOpen, setIsCheckoutSideMenuOpen] = useState(false);
  const openCheckoutSideMenu = () => setIsCheckoutSideMenuOpen(true);
  const closeCheckoutSideMenu = () => setIsCheckoutSideMenuOpen(false);

  // Shopping Cart · Order
  const [order, setOrder] = useState([]);

  // Get Products ·
  // Fetch data from API · hook to add the info from the API to the state
  const [items, setItems] = useState(null);

  // Get Products · Search a product
  const [searchByTitle, setSearchByTitle] = useState("");
  console.log(searchByTitle);

  // UseEffect is a hook to fetch the data from the API
  useEffect(() => {
    // fetch("https://fakestoreapi.com/products") // Fake Store API
    fetch("https://api.escuelajs.co/api/v1/products") // Platzi API
      .then((response) => response.json())
      .then((json) => setItems(json));
  }, []);

  return (
    <AppContext.Provider
      value={
        items,
        setItems,
        cart,
        setCart,
        openProductDetail,
        closeProductDetail,
        isProductDetailOpen,
        productToShow,
        setProductToShow,
        cartProducts,
        setCartProducts,
        isCheckoutSideMenuOpen,
        openCheckoutSideMenu,
        closeCheckoutSideMenu,
        order,
        setOrder,
        searchByTitle,
        setSearchByTitle,
      }
    >
      {children}
    </AppContext.Provider>
  );
};

```

> `value` is missing another set of `{}`. It should look like this: `value={ { ...content here.... } }`

## 29. Filter by Title

### I. Modify the `Home` Component

Add a `renderView` function to filter the products while typing.

Located in `src/Components/Home/index.jsx`

```jsx
import { useContext } from "react";
import Card from "../../Components/Card";
import Layout from "../../Components/Layout";
import ProductDetail from "../../Components/ProductDetail";
import { AppContext } from "../../Context";

const Home = () => {
  const context = useContext(AppContext);

  const renderView = () => {
    if (context.searchByTitle?.length > 0) {
      if (context.filteredItems?.length > 0) {
        return context.filteredItems?.map((item) => (
          <Card key={item.id} data={item} />
        ));
      } else {
        return (
          <div className="flex items-center justify-center w-full">
            <h3 className="font-light text-md">No results found</h3>
          </div>
        );
      }
    } else {
      return context.items?.map((item) => <Card key={item.id} data={item} />);
    }
  };

  return (
    <Layout>
      <div className="flex items-center justify-center relative w-80 mb-4">
        <h1 className="font-medium text-xl">Products</h1>
      </div>
      <input
        type="text"
        placeholder="Search a product..."
        className="border border-black rounded-xl w-96 px-4 py-2 mb-4"
        onChange={(event) => context.setSearchByTitle(event.target.value)}
      />
      <div className="grid gap-4 grid-cols-4 w-full max-w-screen-lg">
        {renderView()}
      </div>
      <ProductDetail />
    </Layout>
  );
};

export default Home;
```

## II. Modify the `Context` file

Add a `Filter items by search` function (`filteredItemsByTitle`)

As well as a `useEffect` to implement the filtering.

Located in `src/Context/index.jsx`

```jsx
import { createContext, useEffect, useState } from "react";

export const AppContext = createContext();

export const AppProvider = ({ children }) => {
  // Shopping Cart · Increment quantity
  const [cart, setCart] = useState(0);

  // Product Detail · Open/Close
  const [isProductDetailOpen, setIsProductDetailOpen] = useState(false);
  const openProductDetail = () => setIsProductDetailOpen(true);
  const closeProductDetail = () => setIsProductDetailOpen(false);

  // Product Detail · Show product
  const [productToShow, setProductToShow] = useState({});

  // Shopping Cart · add product to cart
  const [cartProducts, setCartProducts] = useState([]);

  // Checkout Side Menu · Open/Close
  const [isCheckoutSideMenuOpen, setIsCheckoutSideMenuOpen] = useState(false);
  const openCheckoutSideMenu = () => setIsCheckoutSideMenuOpen(true);
  const closeCheckoutSideMenu = () => setIsCheckoutSideMenuOpen(false);

  // Shopping Cart · Order
  const [order, setOrder] = useState([]);
  // console.log(order);

  // Get Products ·
  // Fetch data from API · hook to add the info from the API to the state
  const [items, setItems] = useState(null);

  // Get Products · Search a product
  const [searchByTitle, setSearchByTitle] = useState("");
  // console.log(searchByTitle);

  // Filter items by search
  const [filteredItems, setFilteredItems] = useState(null);

  // UseEffect is a hook to fetch the data from the API
  useEffect(() => {
    // fetch("https://fakestoreapi.com/products") // Fake Store API
    fetch("https://api.escuelajs.co/api/v1/products") // Platzi API
      .then((response) => response.json())
      .then((json) => setItems(json));
  }, []);

  // Filter items by search
  const filteredItemsByTitle = (items, searchByTitle) => {
    return items?.filter((item) =>
      item.title.toLowerCase().includes(searchByTitle.toLowerCase())
    );
  };

  // Filter items by search · useEffect
  useEffect(() => {
    if (searchByTitle) {
      return setFilteredItems(filteredItemsByTitle(items, searchByTitle));
    }
  }, [items, searchByTitle]);
  // console.log("filteredItems: ", filteredItems);

  return (
    <AppContext.Provider
      value={
        items,
        setItems,
        cart,
        setCart,
        openProductDetail,
        closeProductDetail,
        isProductDetailOpen,
        productToShow,
        setProductToShow,
        cartProducts,
        setCartProducts,
        isCheckoutSideMenuOpen,
        openCheckoutSideMenu,
        closeCheckoutSideMenu,
        order,
        setOrder,
        searchByTitle,
        setSearchByTitle,
        filteredItems,
        setFilteredItems,
      }
    >
      {children}
    </AppContext.Provider>
  );
};
```

> `value` is missing another set of `{}`. It should look like this: `value={ { ...content here.... } }`

## 30. Filter by Category && Title

### I. Modify the `Navbar` Component

Add an `onClick` event to filter by category (`setSearchByCategory`) in the _NavLink_ tag.

Located in `src/Components/Navbar/index.jsx`

```jsx
import { NavLink } from "react-router-dom";
import { useContext } from "react";
import { AppContext } from "../../Context";
import { HiOutlineShoppingCart } from "react-icons/hi";

const Navbar = () => {
  const activeStyle = "underline text-gray-500 underline-offset-4";
  const context = useContext(AppContext);

  return (
    <nav className="flex justify-between items-center fixed z-10 w-full py-5 px-8 text-md font-light top-0">
      <ul className="flex items-center gap-3">
        <li className="font-semibold text-lg">
          <NavLink to="/" onClick={() => context.setSearchByCategory(null)}>
            Shopi
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
            onClick={() => context.setSearchByCategory(null)}
          >
            All
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/clothes"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
            onClick={() => context.setSearchByCategory("clothes")}
          >
            Clothes
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/electronics"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
            onClick={() => context.setSearchByCategory("electronics")}
          >
            Electronics
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/furnitures"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
            onClick={() => context.setSearchByCategory("furnitures")}
          >
            Furnitures
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/toys"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
            onClick={() => context.setSearchByCategory("toys")}
          >
            Toys
          </NavLink>
        </li>
      </ul>

      <ul className="flex items-center gap-3">
        <li>
          <NavLink
            to="/my-orders"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            My Orders
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/my-account"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            My Account
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/sign-in"
            className={({ isActive }) => (isActive ? activeStyle : undefined)}
          >
            Sign In
          </NavLink>
        </li>
        <li>
          <NavLink
            to="/card"
            className={`flex justify-center items-center ${({ isActive }) =>
              isActive ? activeStyle : undefined}`}
          >
            <HiOutlineShoppingCart className="mr-1" />
            <p>{context.cartProducts.length}</p>
          </NavLink>
        </li>
      </ul>
    </nav>
  );
};

export default Navbar;
```

### II. Modify the `App` file

By adding all the new routes: `{ path: "/newPath", element: <Home /> }`

Located in `src/Pages/App/index.jsx`

```jsx
import { useRoutes, BrowserRouter } from "react-router-dom";
import { AppProvider } from "../../Context";
import Home from "../Home";
import MyAccount from "../MyAccount";
import MyOrder from "../MyOrder";
import MyOrders from "../MyOrders";
import NotFound from "../NotFound";
import SignIn from "../SignIn";
import Navbar from "../../Components/Navbar";
// import TestNavbar from "../../Components/TestJp/Navbar.jsx";
import "./App.css";
import CheckoutSideMenu from "../../Components/CheckoutSideMenu";

const AppRoutes = () => {
  let routes = useRoutes([
    { path: "/", element: <Home /> },
    { path: "/clothes", element: <Home /> },
    { path: "/electronics", element: <Home /> },
    { path: "/furnitures", element: <Home /> },
    { path: "/toys", element: <Home /> },
    { path: "/others", element: <Home /> },
    { path: "/my-account", element: <MyAccount /> },
    { path: "/my-order", element: <MyOrder /> },
    { path: "/my-orders", element: <MyOrders /> },
    { path: "/my-orders/last", element: <MyOrder /> },
    { path: "/my-orders/:id", element: <MyOrder /> },
    { path: "/sign-in", element: <SignIn /> },
    { path: "*", element: <NotFound /> },
  ]);
  return routes;
};

const App = () => {
  return (
    <AppProvider>
      <BrowserRouter>
        <AppRoutes />
        <Navbar />
        <CheckoutSideMenu />
      </BrowserRouter>
    </AppProvider>
  );
};
export default App;
```

## III. Modify the `Context` file

By adding all the logic to filter the render products by `title`, `category`, `title and category`.

In other words, render the view depending on the action:

- Display all the products with NO filters.
- Display product/s when searching (filtering `title`)
- Display product/s by filtering `category`
- Display by filtering `title and category`

Located in `src/Context/index.jsx`

```jsx
import { createContext, useEffect, useState } from "react";

export const AppContext = createContext();

export const AppProvider = ({ children }) => {
  // Shopping Cart · Increment quantity
  const [cart, setCart] = useState(0);

  // Product Detail · Open/Close
  const [isProductDetailOpen, setIsProductDetailOpen] = useState(false);
  const openProductDetail = () => setIsProductDetailOpen(true);
  const closeProductDetail = () => setIsProductDetailOpen(false);

  // Product Detail · Show product
  const [productToShow, setProductToShow] = useState({});

  // Shopping Cart · add product to cart
  const [cartProducts, setCartProducts] = useState([]);

  // Checkout Side Menu · Open/Close
  const [isCheckoutSideMenuOpen, setIsCheckoutSideMenuOpen] = useState(false);
  const openCheckoutSideMenu = () => setIsCheckoutSideMenuOpen(true);
  const closeCheckoutSideMenu = () => setIsCheckoutSideMenuOpen(false);

  // Shopping Cart · Order
  const [order, setOrder] = useState([]);
  // console.log(order);

  // Get Products
  // Fetch data from API · hook to add the info from the API to the state
  const [items, setItems] = useState(null);

  // UseEffect is a hook to fetch the data from the API
  useEffect(() => {
    // fetch("https://fakestoreapi.com/products") // Fake Store API
    fetch("https://api.escuelajs.co/api/v1/products") // Platzi API
      .then((response) => response.json())
      .then((json) => setItems(json));
  }, []);

  // Get Products · Search a Product
  const [searchByTitle, setSearchByTitle] = useState(null);
  // console.log(searchByTitle);

  // Get Products · Filter items by category
  const [searchByCategory, setSearchByCategory] = useState(null);
  // console.log("searchByCategory: ", searchByCategory);

  // Filter items by search
  const [filteredItems, setFilteredItems] = useState(null);

  const filteredItemsByTitle = (items, searchByTitle) => {
    return items?.filter((item) =>
      item.title.toLowerCase().includes(searchByTitle.toLowerCase())
    );
  };

  const filteredItemsByCategory = (items, searchByCategory) => {
    return items?.filter((item) =>
      item.category.name.toLowerCase().includes(searchByCategory.toLowerCase())
    );
  };

  const filterBy = (searchType, items, searchByTitle, searchByCategory) => {
    // Filter by title
    if (searchType === "BY_TITLE") {
      return filteredItemsByTitle(items, searchByTitle);
    }

    // Filter by category
    if (searchType === "BY_CATEGORY") {
      return filteredItemsByCategory(items, searchByCategory);
    }

    // Filter by title and category
    if (searchType === "BY_TITLE_AND_CATEGORY") {
      return filteredItemsByCategory(items, searchByCategory).filter((item) =>
        item.title.toLowerCase().includes(searchByTitle.toLowerCase())
      );
    }

    // The is NO Filter, return all items
    if (!searchType) {
      return items;
    }
  };

  useEffect(() => {
    // Filter by title and category
    if (searchByTitle && searchByCategory) {
      return setFilteredItems(
        filterBy(
          "BY_TITLE_AND_CATEGORY",
          items,
          searchByTitle,
          searchByCategory
        )
      );
    }
    // Filter by title
    if (searchByTitle && !searchByCategory) {
      return setFilteredItems(
        filterBy("BY_TITLE", items, searchByTitle, searchByCategory)
      );
    }
    // Filter by category
    if (!searchByTitle && searchByCategory) {
      return setFilteredItems(
        filterBy("BY_CATEGORY", items, searchByTitle, searchByCategory)
      );
    }
    // No Filter, return all items
    if (!searchByTitle && !searchByCategory) {
      return setFilteredItems(
        filterBy(null, items, searchByTitle, searchByCategory)
      );
    }
  }, [items, searchByTitle, searchByCategory]);

  console.log("searchByCategory: ", searchByCategory);
  console.log("searchByTitle: ", searchByTitle);
  console.log("filteredItems: ", filteredItems);

  return (
    <AppContext.Provider
      value={
        items,
        setItems,
        cart,
        setCart,
        openProductDetail,
        closeProductDetail,
        isProductDetailOpen,
        productToShow,
        setProductToShow,
        cartProducts,
        setCartProducts,
        isCheckoutSideMenuOpen,
        openCheckoutSideMenu,
        closeCheckoutSideMenu,
        order,
        setOrder,
        filteredItems,
        setFilteredItems,
        searchByTitle,
        setSearchByTitle,
        searchByCategory,
        setSearchByCategory,
      }
    >
      {children}
    </AppContext.Provider>
  );
};
```

> `value` is missing another set of `{}`. It should look like this: `value={ { ...content here.... } }`

### IV. Modify the `Home` Component

Located in `src/Components/Home/index.jsx`

```jsx
import { useContext } from "react";
import Card from "../../Components/Card";
import Layout from "../../Components/Layout";
import ProductDetail from "../../Components/ProductDetail";
import { AppContext } from "../../Context";

const Home = () => {
  const context = useContext(AppContext);

  const renderView = () => {
    // if there are items in the filteredItems array, render them
    // Filter by title and category
    if (context.filteredItems?.length > 0) {
      return context.filteredItems?.map((item) => (
        <Card key={item.id} data={item} />
      ));
    } else {
      return (
        <div className="flex flex-col gap-3 w-full">
          <h3 className="font-light text-md">
            No results for:
            <span className="font-medium text-md text-gray-400 pl-2">
              {context.searchByTitle}
            </span>
          </h3>
          <p className="font-light text-sm text-gray-400/80">
            Try searching for another product
          </p>
        </div>
      );
    }
  };

  return (
    <Layout>
      <div className="flex items-center justify-center relative w-80 mb-4">
        <h1 className="font-medium text-xl">Products</h1>
      </div>
      <input
        type="text"
        placeholder="Search a product..."
        className="border border-black rounded-xl w-96 px-4 py-2 mb-4"
        onChange={(event) => context.setSearchByTitle(event.target.value)}
      />
      <div className="grid gap-4 grid-cols-4 w-full max-w-screen-lg">
        {renderView()}
      </div>
      <ProductDetail />
    </Layout>
  );
};

export default Home;
```

## 31. Testing and debugging

This is one of the most important parts.

### I. Cart Count

One problem I found was that the cart count was an independent number and need it to be the same as the order. I change it to the lenght of the array.

- Modify the `Navbar` Component

Located in `src/Components/Navbar/index.jsx`

```jsx
// Stop using the cart value:

context.cart;
// And use the lenght of the products array
context.cartProducts.length;
```

### II. Checkout Button

After placing an order, if the user previously typed something on the screen and didn't refresh the page, that input remained saved on the `setSearchByTitle`. I had to reset it after checkout.

- Check the values in `Context` file

```jsx
console.log("searchByCategory: ", searchByCategory);
console.log("searchByTitle: ", searchByTitle);
console.log("filteredItems: ", filteredItems);
```

- Modify the `CheckoutSideMenu` Component

Located in `src/Components/CheckoutSideMenu/index.jsx`

```jsx
// under handleCheckout, reset Title and Category

const handleCheckout = () => {
  // ... code ...

  context.setSearchByTitle(null); // Reset the search
  context.setSearchByCategory(null); // Reset the search
};
```

## 32. Improve the UI (User Interface) and UX (User Experience)

### I. Make the Site Responsive

Responsive design is a part of both UI (User Interface) and UX (User Experience). From a UI perspective, it involves designing interfaces that adapt to different screen sizes. From a UX perspective, it ensures that the user has a seamless experience on any device.

### II. Change the Icons

Changing the icons is a part of both UI (User Interface) and UX (User Experience). From a UI perspective, it involves updating the visual elements of the interface. From a UX perspective, it can improve the user's interaction with the system by making icons more intuitive or easier to understand.

### III. Modify the Styling of some pages

Styling is a part of both UI (User Interface) and UX (User Experience). From a UI perspective, it involves choosing colors, fonts, and layouts. From a UX perspective, good styling can make the interface easier to use and more enjoyable for the user.

## 33. Clean Up the Project

It's good practice to check if we are repeating code and clean up the project. Here is an example of code that we can clean.

In other words, refactoring the code to avoid repetition its good practice.

### Modify the `Navbar` Component

Refactor the code to avoid repetition by creating a new component for the navigation links.

Located in `src/Components/Navbar/index.jsx`

```jsx
import { NavLink } from "react-router-dom";
import { useContext } from "react";
import { AppContext } from "../../Context";
import { HiOutlineShoppingCart } from "react-icons/hi";
import { useScrollPosition } from "../../Utils/useScrollPosition";

// refactored code to avoid repetition. activeStyle was getting repeated.
const NavItem = ({ to, children, setSearchByCategory }) => {
  const activeStyle = "underline text-gray-500 underline-offset-4";
  return (
    <li>
      <NavLink
        to={to}
        className={({ isActive }) => (isActive ? activeStyle : undefined)}
        onClick={() => setSearchByCategory && setSearchByCategory(to.slice(1))}
      >
        {children}
      </NavLink>
    </li>
  );
};

const Navbar = () => {
  const context = useContext(AppContext);

  function classNamesNavBarScroll(...classes) {
    return classes.filter(Boolean).join(" ");
  }

  const scrollPosition = useScrollPosition();
  // console.log(scrollPosition);

  return (
    <header
      className={classNamesNavBarScroll(
        scrollPosition > 0
          ? "md:shadow md:bg-white md:-translate-y-6 md:h-auto"
          : "md:shadow-none md:bg-none md:translate-y-0 md:h-none",
        "absolute md:fixed top-2 inset-x-0 z-40 md:transition-shadow-xl md:shadow-black md:transition-color duration-500 md:-translate-y-6 md:h-20 lg:h-14"
      )}
    >
      <nav className="hidden sm:flex flex-col sm:flex-row justify-between items-center fixed z-10 w-full py-5 px-8 text-md font-light top-0">
        <ul className="flex flex-col sm:flex-row items-center gap-3">
          <li className="font-semibold text-lg">
            <NavLink to="/" onClick={() => context.setSearchByCategory(null)}>
              Shopi
            </NavLink>
          </li>
          <NavItem to="/" setSearchByCategory={context.setSearchByCategory}>
            All
          </NavItem>
          <NavItem
            to="/clothes"
            setSearchByCategory={context.setSearchByCategory}
          >
            Clothes
          </NavItem>
          <NavItem
            to="/electronics"
            setSearchByCategory={context.setSearchByCategory}
          >
            Electronics
          </NavItem>
          <NavItem
            to="/furnitures"
            setSearchByCategory={context.setSearchByCategory}
          >
            Furnitures
          </NavItem>
          <NavItem to="/toys" setSearchByCategory={context.setSearchByCategory}>
            Toys
          </NavItem>
        </ul>

        <ul className="hidden sm:flex items-center gap-3">
          <NavItem to="/my-orders">My Orders</NavItem>
          <NavItem to="/sign-in">Sign In</NavItem>
          <NavItem to="/my-account">My Account</NavItem>
          <li>
            <NavLink
              to="/card"
              className={`flex justify-center items-center ${({ isActive }) =>
                isActive ? activeStyle : undefined}`}
            >
              <HiOutlineShoppingCart className="mr-1" />
              <p>{context.cartProducts.length}</p>
            </NavLink>
          </li>
        </ul>
      </nav>
    </header>
  );
};

export default Navbar;
```

> In this refactored code, a new NavItem component is created which encapsulates the repeated NavLink code. The NavItem component takes a to prop for the link, children for the link text, and an optional setSearchByCategory function. If setSearchByCategory is provided, it will be called with the category name when the link is clicked.

> Notice that the "Shopi" item has its own unique styles and does not share the same styles as the other NavItem components, you can directly use the NavLink component for it instead of the NavItem component.

## 34. Create Private Routes and Public Routes

> Note: I implemented the private & public router in another project called [JP·Shop](https://jpshop.jpdiaz.dev/). Shopi does not have a working sign in, sign out, my account features.

Private and Public Routes refer to the accessibility of certain routes (or pages) based on the user's authentication status.

**Private Routes**: These are routes that are only accessible to authenticated users. If a user is not authenticated and tries to access a private route, they are typically redirected to a login page.

**Public Routes**: These are routes that are accessible to all users, regardless of their authentication status. Examples of public routes might include the login page, the registration page, or a public homepage.

### How can I implement Private and Public Routes in React?

- useAuth: login y logout

[Learn more](https://platzi.com/new-home/clases/3468-react-router/51623-useauth-login-y-logout/)

#### I. Create an `auth.jsx` file in context

Locate in `src/Context/auth.jsx`

```jsx
import React, { useContext } from "react";
import { useNavigate } from "react-router-dom";

const AuthContext = React.createContext();

function AuthProvider({ children }) {
  const navigate = useNavigate();
  const [user, setUser] = React.useState(null);

  const login = (username, password) => {
    if (typeof username !== "string") {
      throw new Error("Username must be a string");
    }
    setUser({ username, password });
    navigate("/my-account");
  };

  const logout = () => {
    setUser(null);
    navigate("/");
  };

  const auth = { user, login, logout };

  return <AuthContext.Provider value={auth}>{children}</AuthContext.Provider>;
}

function useAuth() {
  //here?
  const auth = React.useContext(AuthContext);
  return auth;
}
export { AuthProvider, useAuth };
```

#### II. Modify the `SignIn.jsx` page

```jsx
import React, { useState } from "react";
import Layout from "../../Components/Layout";
import { useAuth } from "../../Context/auth";

function SignIn() {
  const auth = useAuth(); // console.log("auth: ", auth);

  const [username, setUsername] = useState("");
  const [password, setPassword] = useState("");

  const handleLogin = (e) => {
    e.preventDefault();
    // console.log("username: ", username);
    // console.log("password: ", password);
    auth.login(username, password);
    //    onLogin(username, password); this is from copilot-signin. and onlogin needs to be passed in as a prop. at the beginning of... function SignIn({ onLogin }) {
  };

  return (
    <Layout>
      <div className="flex items-center justify-center relative mb-4">
        <h1 className="font-medium text-md sm:text-xl">Sign In</h1>
      </div>
      <form
        onSubmit={handleLogin}
        className="flex flex-col justify-center items-center w-screen h-screen gap-5"
      >
        <input
          type="text"
          value={username}
          onChange={(e) => setUsername(e.target.value)}
          placeholder="Username"
          className="border border-gray-300 rounded-md px-2 py-1"
        />
        <input
          type="password"
          value={password}
          onChange={(e) => setPassword(e.target.value)}
          placeholder="Password"
          className="border border-gray-300 rounded-md px-2 py-1"
        />
        <button
          type="submit"
          className="w-48 bg-black text-white font-medium py-2 rounded-lg mt-2 hover:bg-gray-900/50 transition duration-300"
        >
          Sign In
        </button>
      </form>
    </Layout>
  );
}

export default SignIn;
```

#### III. Modify the `MyAccount.jsx` page

```jsx
import Layout from "../../Components/Layout";
import { useAuth } from "../../Context/auth";

const MyAccount = () => {
  const auth = useAuth();
  return (
    <Layout>
      <div className="flex flex-col gap-7 items-center justify-center relative mb-4">
        <h1 className="font-medium text-md sm:text-xl">My Account</h1>
        <p className="font-semibold text-2xl">Welcome, {auth.user.username}</p>

        {console.log("username: ", auth.user.username)}
        {console.log("password: ", auth.user.password)}
      </div>
    </Layout>
  );
};

export default MyAccount;
```

#### IV. Modify the `App.jsx`

```jsx
import { useRoutes, BrowserRouter } from "react-router-dom";
import { AppProvider } from "../../Context";

import { AuthProvider } from "../../Context/auth"; // AuthContext is the context that will be used to store the user's data
import Navbar from "../../Components/Navbar";
import CheckoutSideMenu from "../../Components/CheckoutSideMenu";
import "./App.css";

import Home from "../Home";
import MyOrder from "../MyOrder";
import MyOrders from "../MyOrders";
import NotFound from "../NotFound";
import MyAccount from "../MyAccount";
import SignIn from "../SignIn";
import Logout from "../Logout";

const AppRoutes = () => {
  let routes = useRoutes([
    { path: "/", element: <Home /> },
    { path: "/smartphones", element: <Home /> },
    { path: "/laptops", element: <Home /> },
    { path: "/fragrances", element: <Home /> },
    { path: "/skincare", element: <Home /> },
    { path: "/groceries", element: <Home /> },
    { path: "/home-decoration", element: <Home /> },
    // Should be Private Route but for testing purposes it is public
    { path: "/my-order", element: <MyOrder /> },
    { path: "/my-orders", element: <MyOrders /> },
    { path: "/my-orders/last", element: <MyOrder /> },
    { path: "/my-orders/:id", element: <MyOrder /> },
    // Private Routes
    { path: "/my-account", element: <MyAccount /> },
    { path: "/sign-in", element: <SignIn /> },
    { path: "/logout", element: <Logout /> },
    // Not Found
    { path: "*", element: <NotFound /> },
  ]);
  return routes;
};

const App = () => {
  return (
    <AppProvider>
      <BrowserRouter>
        <AuthProvider>
          <AppRoutes />
          <Navbar />
          <CheckoutSideMenu />
        </AuthProvider>
      </BrowserRouter>
    </AppProvider>
  );
};
export default App;
```

#### V. Modify the `Navbar.jsx` Component

In your Navbar component, you can use the auth context to conditionally render links based on whether the user is authenticated or not. For example, you might only want to show the "My Account" and "Logout" links if the user is authenticated, and only show the "Sign In" link if the user is not authenticated.

Here's how you can do that:

- Option 1:
```jsx
<ul className="hidden sm:flex items-center gap-3">
  {auth.user && (
    <li>
      <NavLink
        to="/my-account"
        className={({ isActive }) => (isActive ? activeStyle : undefined)}
      >
        My Account
      </NavLink>
    </li>
  )}
  {auth.user ? (
    <li>
      <NavLink
        to="/Logout"
        className={({ isActive }) => (isActive ? activeStyle : undefined)}
      >
        Logout
      </NavLink>
    </li>
  ) : (
    <li>
      <NavLink
        to="/sign-in"
        className={({ isActive }) => (isActive ? activeStyle : undefined)}
      >
        Sign In
      </NavLink>
    </li>
  )}
</ul>
```

> if auth.user is truthy (i.e., the user is authenticated), the "Logout" and "My Account" links are rendered. If auth.user is falsy (i.e., the user is not authenticated), the "Sign In" link is rendered.

- Option 2:
```jsx
// ...
<ul className="hidden sm:flex items-center gap-3">
  {auth.user && (
    <>
      <li>
        <NavLink
          to="/my-account"
          className={({ isActive }) =>
            isActive ? activeStyle : undefined
          }
        >
          My Account
        </NavLink>
      </li>
      <li>
        <NavLink
          to="/my-orders"
          className={({ isActive }) => (isActive ? activeStyle : undefined)}
        >
          My Orders
        </NavLink>
      </li>
      <li>
        <NavLink
          to="/card"
          className={`flex justify-center items-center ${({ isActive }) =>
            isActive ? activeStyle : undefined}`}
        >
          <HiOutlineShoppingCart className="mr-1" />
          <p>{context.cartProducts.length}</p>
        </NavLink>
      </li>
      <li>
        <NavLink
          to="/Logout"
          className={({ isActive }) =>
            isActive ? activeStyle : undefined
          }
        >
          Logout
        </NavLink>
      </li>
    </>
  )}
  {!auth.user && (
    <li>
      <NavLink
        to="/sign-in"
        className={({ isActive }) =>
          isActive ? activeStyle : undefined
        }
      >
        Sign In
      </NavLink>
    </li>
  )}
</ul>
// ...
```

> You can also have the links to "My Account", "My Orders", "Card", and "Logout" will only be shown if auth.user is truthy, indicating that a user is authenticated. If auth.user is falsy, indicating that no user is authenticated, only the "Sign In" link will be shown. 

Here's how the `Navbar.jsx` should look like using option 2:

```jsx
import { NavLink } from "react-router-dom";
import { useContext, useState } from "react";
import { AppContext } from "../../Context";
import { HiOutlineShoppingCart } from "react-icons/hi";
import { useScrollPosition } from "../../Utils/useScrollPosition";
import { useAuth } from "../../Context/auth";

const Navbar = () => {
  const activeStyle = "underline text-gray-500 underline-offset-4";
  const context = useContext(AppContext);

  //scrollPosition:
  const [showDropdown, setShowDropdown] = useState(false);
  const [showDropdownTech, setShowDropdownTech] = useState(false);

  function classNamesNavBarScroll(...classes) {
    return classes.filter(Boolean).join(" ");
  }

  const scrollPosition = useScrollPosition();
  // console.log(scrollPosition);

  // AuthContext:
  const auth = useAuth();
  console.log("in Navbar, Auth.user: ", auth.user);

  return (
    <header
      className={classNamesNavBarScroll(
        scrollPosition > 0
          ? "md:shadow md:bg-white md:-translate-y-6 md:h-auto"
          : "md:shadow-none md:bg-none md:translate-y-0 md:h-none",
        "absolute md:fixed top-2 inset-x-0 z-40 md:transition-shadow-xl md:shadow-black md:transition-color duration-500 md:-translate-y-6 md:h-20 lg:h-14"
      )}
    >
      <nav className="hidden sm:flex flex-col sm:flex-row justify-between items-center fixed z-10 w-full py-5 px-8 text-md font-light top-0">
        <ul className="flex flex-col sm:flex-row items-center gap-3">
          <li className="font-semibold text-lg">
            <NavLink to="/" onClick={() => context.setSearchByCategory(null)}>
              JP·Shop
            </NavLink>
          </li>
          <li>
            <NavLink
              to="/"
              className={({ isActive }) => (isActive ? activeStyle : undefined)}
              onClick={() => context.setSearchByCategory(null)}
            >
              All
            </NavLink>
          </li>
          <li onClick={() => setShowDropdownTech(!showDropdownTech)}>
            Electronics
            {showDropdownTech && (
              <div>
                <NavLink
                  to="/smartphones"
                  className={({ isActive }) =>
                    isActive ? activeStyle : undefined
                  }
                  onClick={() => context.setSearchByCategory("smartphones")}
                >
                  Phone
                </NavLink>
                <NavLink
                  to="/laptops"
                  className={({ isActive }) =>
                    isActive ? activeStyle : undefined
                  }
                  onClick={() => context.setSearchByCategory("laptops")}
                >
                  Laptop
                </NavLink>
              </div>
            )}
          </li>
          <li onClick={() => setShowDropdown(!showDropdown)}>
            Cosmetics
            {showDropdown && (
              <div>
                <NavLink
                  to="/fragrances"
                  className={({ isActive }) =>
                    isActive ? activeStyle : undefined
                  }
                  onClick={() => context.setSearchByCategory("fragrances")}
                >
                  Perfumes
                </NavLink>
                <NavLink
                  to="/skincare"
                  className={({ isActive }) =>
                    isActive ? activeStyle : undefined
                  }
                  onClick={() => context.setSearchByCategory("skincare")}
                >
                  Skin Care
                </NavLink>
              </div>
            )}
          </li>
          <li>
            <NavLink
              to="/groceries"
              className={({ isActive }) => (isActive ? activeStyle : undefined)}
              onClick={() => context.setSearchByCategory("groceries")}
            >
              Groceries
            </NavLink>
          </li>
          <li>
            <NavLink
              to="/home-decoration"
              className={({ isActive }) => (isActive ? activeStyle : undefined)}
              onClick={() => context.setSearchByCategory("home-decoration")}
            >
              HomeGoods
            </NavLink>
          </li>
        </ul>
        <ul className="hidden sm:flex items-center gap-3">
          {auth.user && (
            <>
              <li>
                <NavLink
                  to="/my-account"
                  className={({ isActive }) =>
                    isActive ? activeStyle : undefined
                  }
                >
                  My Account
                </NavLink>
              </li>
              <li>
                <NavLink
                  to="/my-orders"
                  className={({ isActive }) =>
                    isActive ? activeStyle : undefined
                  }
                >
                  My Orders
                </NavLink>
              </li>
              <li>
                <NavLink
                  to="/card"
                  className={`flex justify-center items-center ${({
                    isActive,
                  }) => (isActive ? activeStyle : undefined)}`}
                >
                  <HiOutlineShoppingCart className="mr-1" />
                  <p>{context.cartProducts.length}</p>
                </NavLink>
              </li>
              <li>
                <NavLink
                  to="/Logout"
                  className={({ isActive }) =>
                    isActive ? activeStyle : undefined
                  }
                >
                  Logout
                </NavLink>
              </li>
            </>
          )}
          {!auth.user && (
            <li>
              <NavLink
                to="/sign-in"
                className={({ isActive }) =>
                  isActive ? activeStyle : undefined
                }
              >
                Sign In
              </NavLink>
            </li>
          )}
        </ul>
      </nav>
    </header>
  );
};

export default Navbar;
```


### Private and Public Routes

To create private and public routes, you can create two components: PrivateRoute and PublicRoute.

PrivateRoute will check if the user is authenticated. If they are, it will render the component passed to it. If not, it will redirect the user to the login page.

PublicRoute will check if the user is authenticated. If they are, it will redirect them to the "My Account" (or another page). If not, it will render the component passed to it.

The PrivateRoute and PublicRoute are components that you will create to handle private and public routes in your application. They will use the useAuth hook to check if a user is authenticated and the useNavigate hook to redirect users based on their authentication status.

Here's how you can create these components:

#### I. Modify the `App.jsx` Page

```jsx
import { useRoutes, BrowserRouter, Navigate } from "react-router-dom";
import { AppProvider } from "../../Context";

import { AuthProvider } from "../../Context/auth"; // AuthContext is the context that will be used to store the user's data
import Navbar from "../../Components/Navbar";
import CheckoutSideMenu from "../../Components/CheckoutSideMenu";
import "./App.css";

import Home from "../Home";
import MyOrder from "../MyOrder";
import MyOrders from "../MyOrders";
import NotFound from "../NotFound";
import MyAccount from "../MyAccount";
import SignIn from "../SignIn";
import Logout from "../Logout";

// Implementing the Private and Public Routes:
import { useAuth } from "../../Context/auth"; // make sure you have a useAuth hook in your auth context

const PrivateRoute = ({ children }) => {
  const { user } = useAuth();
  return user ? children : <Navigate to="/sign-in" />;
};

const PublicRoute = ({ children }) => {
  const { user } = useAuth();
  return user ? <Navigate to="/" /> : children;
};

const AppRoutes = () => {
  let routes = useRoutes([
    { path: "/", element: <Home /> },
    { path: "/smartphones", element: <Home /> },
    { path: "/laptops", element: <Home /> },
    { path: "/fragrances", element: <Home /> },
    { path: "/skincare", element: <Home /> },
    { path: "/groceries", element: <Home /> },
    { path: "/home-decoration", element: <Home /> },
    // Private Routes
    { path: "/my-order", element: <PrivateRoute><MyOrder /></PrivateRoute> },
    { path: "/my-orders", element: <PrivateRoute><MyOrders /></PrivateRoute> },
    { path: "/my-orders/last", element: <PrivateRoute><MyOrder /></PrivateRoute> },
    { path: "/my-orders/:id", element: <PrivateRoute><MyOrder /></PrivateRoute> },
    { path: "/my-account", element: <PrivateRoute><MyAccount /></PrivateRoute> },
    { path: "/logout", element: <PrivateRoute><Logout /></PrivateRoute> },
    // Public Routes
    { path: "/sign-in", element: <PublicRoute><SignIn /></PublicRoute> },
    // Not Found
    { path: "*", element: <NotFound /> },
  ]);
  return routes;
};

const App = () => {
  return (
    <AppProvider>
      <BrowserRouter>
        <AuthProvider>
          <AppRoutes />
          <Navbar />
          <CheckoutSideMenu />
        </AuthProvider>
      </BrowserRouter>
    </AppProvider>
  );
};
export default App;
```

> The code use the useAuth hook from auth context that returns the current user. If the user is null or undefined, it means that the user is not authenticated.

## 35. Add Product to Cart From `ProductDetail` page (or any page)

To use the `addProductToCart` function in your `ProductDetail` page, you need to move this function to the context so that it can be shared between different components. Here's how you can do it:

### I. Modify the `Context` file

In your AppContext, add a new function addProductToCart.

```jsx
import React, { createContext, useState } from "react";

export const AppContext = createContext();

export const AppProvider = ({ children }) => {
  const [count, setCount] = useState(0);
  const [cartProducts, setCartProducts] = useState([]);
  // other states...

  const addProductToCart = (productData) => {
    setCount(count + 1);
    setCartProducts([...cartProducts, productData]);
    // other actions...
  };

  return (
    <AppContext.Provider
      value={{
        count,
        setCount,
        cartProducts,
        setCartProducts,
        addProductToCart,
      }}
    >
      {children}
    </AppContext.Provider>
  );
};
```

`Context` should look something like this:

Located in `src/Context/index.jsx`

```jsx
import { createContext, useEffect, useState } from "react";

export const AppContext = createContext();

export const AppProvider = ({ children }) => {
  // Get Products · State to store the data from the dummy API. It's an empty array because the data is an array of objects
  // Fetch data from API · hook to add the info from the API to the state
  const [items, setItems] = useState([]);

  // UseEffect is a hook to fetch the data from the API
  useEffect(() => {
    fetch("https://dummyjson.com/products")
      .then((response) => response.json())
      .then((json) => {
        // console.log("Data from Dummy API: ", json); // Log the data
        // console.log("Products inside Data Dummy API: ", json.products); // Products is an array of objects inside the data from the API
        setItems(json.products); // Add the data to the state (setItems) and specify the data to be added (json.products)
      });
  }, []);

  // Shopping Cart · Increment quantity
  const [count, setCount] = useState(0);

  // Product Detail · Open/Close
  const [isProductDetailOpen, setIsProductDetailOpen] = useState(false);
  const openProductDetail = () => setIsProductDetailOpen(true);
  const closeProductDetail = () => setIsProductDetailOpen(false);

  // Product Detail · Show product
  const [productToShow, setProductToShow] = useState({});

  // Shopping Cart · add product to cart
  const [cartProducts, setCartProducts] = useState([]);

  // Checkout Side Menu · Open/Close
  const [isCheckoutSideMenuOpen, setIsCheckoutSideMenuOpen] = useState(false);
  const openCheckoutSideMenu = () => setIsCheckoutSideMenuOpen(true);
  const closeCheckoutSideMenu = () => setIsCheckoutSideMenuOpen(false);

  // Shopping Cart · Order
  const [order, setOrder] = useState([]);

  // add product to cart
  const addProductToCart = (productData) => {
    setCount(count + 1);
    setCartProducts([...cartProducts, productData]);
    // console.log("cartProducts: ", cartProducts);
    // console.log("productData: ", productData);
    openCheckoutSideMenu();
    closeProductDetail();
  };

  // Get Products · Search a product
  // const [searchByTitle, setSearchByTitle] = useState("");
  const [searchByTitle, setSearchByTitle] = useState(null);
  // console.log(searchByTitle);

  // Get Products · Filter items by category
  const [searchByCategory, setSearchByCategory] = useState(null);
  // console.log("searchByCategory: ", searchByCategory);

  // Filter items by search
  const [filteredItems, setFilteredItems] = useState(null);

  // Filter items by search
  const filteredItemsByTitle = (items, searchByTitle) => {
    return items?.filter((item) =>
      item.title.toLowerCase().includes(searchByTitle.toLowerCase())
    );
  };

  // Filter items by category
  const filteredItemsByCategory = (items, searchByCategory) => {
    return items?.filter((item) =>
      item.category.toLowerCase().includes(searchByCategory.toLowerCase())
    );
  };

  const filterBy = (searchType, items, searchByTitle, searchByCategory) => {
    // Filter by title
    if (searchType === "BY_TITLE") {
      return filteredItemsByTitle(items, searchByTitle);
    }

    // Filter by category
    if (searchType === "BY_CATEGORY") {
      return filteredItemsByCategory(items, searchByCategory);
    }

    // Filter by title and category
    if (searchType === "BY_TITLE_AND_CATEGORY") {
      return filteredItemsByCategory(items, searchByCategory).filter((item) =>
        item.title.toLowerCase().includes(searchByTitle.toLowerCase())
      );
    }

    // The is NO Filter, return all items
    if (!searchType) {
      return items;
    }
  };

  useEffect(() => {
    // Filter by title and category
    if (searchByTitle && searchByCategory) {
      return setFilteredItems(
        filterBy(
          "BY_TITLE_AND_CATEGORY",
          items,
          searchByTitle,
          searchByCategory
        )
      );
    }
    // Filter by title
    if (searchByTitle && !searchByCategory) {
      return setFilteredItems(
        filterBy("BY_TITLE", items, searchByTitle, searchByCategory)
      );
    }
    // Filter by category
    if (!searchByTitle && searchByCategory) {
      return setFilteredItems(
        filterBy("BY_CATEGORY", items, searchByTitle, searchByCategory)
      );
    }
    // No Filter, return all items
    if (!searchByTitle && !searchByCategory) {
      return setFilteredItems(
        filterBy(null, items, searchByTitle, searchByCategory)
      );
    }
  }, [items, searchByTitle, searchByCategory]);

  // console.log("searchByCategory: ", searchByCategory);
  // console.log("searchByTitle: ", searchByTitle);
  // console.log("filteredItems: ", filteredItems);

  return (
    <AppContext.Provider
      value={{
        items,
        setItems,
        count,
        setCount,
        openProductDetail,
        closeProductDetail,
        isProductDetailOpen,
        productToShow,
        setProductToShow,
        cartProducts,
        setCartProducts,
        isCheckoutSideMenuOpen,
        openCheckoutSideMenu,
        closeCheckoutSideMenu,
        order,
        setOrder,
        searchByTitle,
        setSearchByTitle,
        filteredItems,
        setFilteredItems,
        searchByCategory,
        setSearchByCategory,
        addProductToCart,
      }}
    >
      {children}
    </AppContext.Provider>
  );
};
```

### II. Modify the `Card` Component

In your Card component, use the addProductToCart from context.

```jsx
import { useContext } from "react";
import { AppContext } from "../../Context";

const Card = (data) => {
  const { addProductToCart } = useContext(AppContext);

  // other code...

  const renderIcon = (id) => {
    // other code...

    return (
      <TbShoppingCartPlus
        onClick={(event) => {
          event.stopPropagation();
          addProductToCart(data.data);
        }}
        className="w-4 h-4"
      />
    );
  };

  // other code...
};
```

`Card` should look something like this:

Located in `src/Components/Card/index.jsx`

```jsx
import { useContext } from "react";
import { AppContext } from "../../Context";
import { HiCheck } from "react-icons/hi";
import { TbShoppingCartPlus } from "react-icons/tb";

const Card = (data) => {
  const context = useContext(AppContext);
  const { addProductToCart } = useContext(AppContext);

  const showProduct = (productDetail) => {
    context.openProductDetail();
    context.setProductToShow(productDetail);
    context.closeCheckoutSideMenu();
  };

  // Check if the product is in the cart:
  const renderIcon = (id) => {
    if (data && data.data && data.data.id) {
      const productIsInCart =
        context.cartProducts.filter((product) => product.id === id).length > 0;

      if (productIsInCart) {
        return (
          <div className="absolute top-0 right-0 flex justify-center items-center bg-black text-white rounded-full border-none m-2 p-1">
            <HiCheck className="w-4 h-4" />
          </div>
        );
      } else {
        return (
          <div className="absolute top-0 right-0 flex justify-center items-center bg-white/50 hover:bg-white transition duration-300 rounded-full border-none m-2 p-1">
            <TbShoppingCartPlus
              onClick={(event) => {
                event.stopPropagation();
                addProductToCart(data.data);
              }}
              className="w-4 h-4"
            />
          </div>
        );
      }
    }
    return null;
  };

  return (
    <div
      className="bg-white border shadow-lg cursor-pointer w-56 h-60 rounded-lg  hover:scale-105 transition duration-300"
      onClick={() => showProduct(data.data)}
    >
      <figure className="relative mb-2 w-full h-4/5">
        <span className="absolute bottom-0 bg-white/60 rounded-lg text-black text-xs m-2 py-0.5 px-2">
          {data.data.category}
        </span>
        <img
          className="rounded-lg w-full h-full object-scale-down"
          src={data.data.images[0]}
          alt={data.data.title}
        />
        {renderIcon(data.data.id)}
      </figure>
      <p className="flex justify-around">
        <span className="text-sm font-light">
          {data.data.title.split(" ").slice(0, 3).join(" ")}
        </span>
        <span className="text-lg font-medium">${data.data.price}</span>
      </p>
    </div>
  );
};

export default Card;
```

### III. Modify the `ProductDetail` Component

In the ProductDetail component, use the addProductToCart from context.

```jsx
import { useContext } from "react";
import { AppContext } from "../../Context";

const ProductDetail = (data) => {
  const { addProductToCart } = useContext(AppContext);

  // other code...

  return (
    <button onClick={() => addProductToCart(data.data)}>Add to cart</button>
  );
};
```

`ProductDetail` should look something like this:

Located in `src/Components/ProductDetail/index.jsx`

```jsx
import {
  HiOutlineX,
  HiOutlineTag,
  HiOutlineShoppingCart,
  HiOutlineStar,
  HiOutlineCash,
  HiOutlineTruck,
  HiOutlinePhotograph,
  HiOutlineDocumentText,
  HiOutlineBadgeCheck,
  HiOutlineArrowNarrowLeft,
  HiOutlineArrowNarrowRight,
} from "react-icons/hi";

import { useContext, useState } from "react";
import { AppContext } from "../../Context";

import { BeatLoader } from "react-spinners"; // npm install react-spinners

const ProductDetail = (data) => {
  const context = useContext(AppContext);
  // console.log("context.productToShow: ", context.productToShow);

  const { addProductToCart } = useContext(AppContext);

  // Inside your component
  const [currentImageIndex, setCurrentImageIndex] = useState(0);

  const [isLoading, setIsLoading] = useState(false); // for image loading

  const handleNext = () => {
    setCurrentImageIndex((prevIndex) =>
      prevIndex === context.productToShow?.images?.length - 1
        ? 0
        : prevIndex + 1
    );
  };

  const handlePrev = () => {
    setCurrentImageIndex((prevIndex) =>
      prevIndex === 0
        ? context.productToShow?.images?.length - 1
        : prevIndex - 1
    );
  };
  // tailwind css classes for table:
  const tdElements = "flex justify-start items-center gap-2 py-0.5";

  return (
    <aside
      className={`${
        context.isProductDetailOpen ? "flex" : "hidden"
      } flex-col fixed right-0 top-20 w-[360px] h-min sm:h-[90vh] border border-black shadow-xl shadow-black rounded-lg bg-white sm:bg-white/70 p-2 m-2`}
    >
      <div className="flex justify-between items-center p-6">
        <h2 className="font-medium">Product Detail</h2>
        <HiOutlineX onClick={() => context.closeProductDetail()} />
      </div>
      {/* <figure className="flex justify-center items-center px-6">
        <img
          className="w-fit h-60 rounded-lg"
          src={context.productToShow?.images?.[0]}
          alt={context.productToShow?.title}
        />
      </figure> */}
      {/* Image Slices: */}
      <figure className="flex justify-center items-center px-6">
        {isLoading ? (
          <BeatLoader color="#123abc" />
        ) : (
          context.productToShow?.images?.[currentImageIndex] && (
            <img
              className="w-fit h-60 rounded-lg"
              src={context.productToShow?.images[currentImageIndex]}
              alt={context.productToShow?.title}
            />
          )
        )}
      </figure>
      <div className="flex justify-around items-center">
        <button
          onClick={handlePrev}
          className="flex justify-evenly items-center w-32 bg-black text-white font-medium py-2 rounded-lg mt-2 hover:bg-gray-900/50 transition duration-300"
        >
          <HiOutlineArrowNarrowLeft />
          Previous
        </button>
        <button
          onClick={handleNext}
          className="flex justify-evenly items-center w-32 bg-black text-white font-medium py-2 rounded-lg mt-2 hover:bg-gray-900/50 transition duration-300"
        >
          Next
          <HiOutlineArrowNarrowRight />
        </button>
      </div>

      {/* // ... other code */}
      <div className="p-6">
        {/* <HiOutlineBadgeCheck /> */}
        <h3 className="font-bold text-2xl mb-2 border-b">
          {context.productToShow?.title}
        </h3>

        {/* table */}

        <table className="table-auto w-full mt-4">
          <tbody className="text-gray-700">
            <tr>
              <td className={tdElements}>
                <HiOutlineCash /> Price
              </td>
              <td>${context.productToShow?.price}</td>
            </tr>
            <tr>
              <td className={tdElements}>
                <HiOutlineBadgeCheck /> Brand
              </td>
              <td>{context.productToShow?.brand}</td>
            </tr>
            <tr>
              <td className={tdElements}>
                <HiOutlinePhotograph />
                Category
              </td>
              <td>{context.productToShow?.category}</td>
            </tr>
            <tr>
              <td className={tdElements}>
                <HiOutlineTag /> Discount
              </td>
              <td>{context.productToShow?.discountPercentage} %</td>
            </tr>
            <tr>
              <td className={tdElements}>
                <HiOutlineStar /> Rating
              </td>
              <td>{context.productToShow?.rating}</td>
            </tr>
            <tr>
              <td className={tdElements}>
                <HiOutlineTruck /> Stock
              </td>
              <td>{context.productToShow?.stock} available</td>
            </tr>
            {/* <tr>
              <td className={tdElements}>Thumbnail</td>
              <td>{context.productToShow?.thumbnail}</td>
            </tr> */}
          </tbody>
        </table>
        {/* end table */}
        <div className={tdElements}>
          <HiOutlineDocumentText />
          <p className="mb-1 mt-2">Description</p>
        </div>
        <p className="text-gray-700 text-base">
          {context.productToShow?.description}
        </p>
        <button
          className="flex justify-center gap-2 items-center w-full bg-black text-white font-medium py-2 rounded-lg mt-2 hover:bg-gray-900/50 transition duration-300"
          onClick={() => addProductToCart(data.data)}
        >
          <HiOutlineShoppingCart /> Add to Cart
        </button>
      </div>
      {/* ... other code */}
    </aside>
  );
};

export default ProductDetail;
```

### Fix the error

I am able to add products from the card as before. However, I am not able to do it from the `ProductDetail` page. I am getting some errors.

> `Cannot read properties of undefined (reading 'id') at index.jsx:29:56 at Array.filter () at renderIcon (index.jsx:29:28) at Card (index.jsx:66:10) at renderWithHooks (react-dom.development.js:16305:18) at updateFunctionComponent (react-dom.development.js:19588:20) at beginWork (react-dom.development.js:21601:16) at HTMLUnknownElement.callCallback2 (react-dom.development.js:4164:14) at Object.invokeGuardedCallbackDev (react-dom.development.js:4213:16) at invokeGuardedCallback (react-dom.development.js:4277:31)`

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
