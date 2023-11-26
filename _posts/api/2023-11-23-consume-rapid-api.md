---
layout: post
title: "How to Consume Rapid API's"
date: 2023-11-23
categories: react api
tags: api react tailwindcss responsive
# image: /assets/img/featured-posts/react_tailwind.jpg
---

This is an step by step article on how to Consume a Rapid API.

<!-- BUILD WITH -->

### Built With 🔑

This project was developed using

[![React](https://img.shields.io/badge/React-61DAFB.svg?style=for-the-badge&logo=React&logoColor=black)](https://www.w3schools.com/whatis/whatis_react.asp)
[![Tailwind](https://img.shields.io/badge/Tailwind%20CSS-06B6D4.svg?style=for-the-badge&logo=Tailwind-CSS&logoColor=white)](https://tailwindcss.com/)

<!-- RELATED PROJECT -->

### Projects

| Project | Github | Demo | Other |
| :--- | :--- | :---- | :--- |
| Landing |  [Repo]() | [Description]() | [VideoTutorial, Figma]() | 
<!--- | Landing |  [Repo]() | [Description]() | [VideoTutorial, Figma]() | --->



<!-- CONTENT -->

# Content 🚦

- [Tutorial](https://www.youtube.com/watch?v=Li40L8tZcaI&t=266s)

## 1. Create the Rapid-API React Project

Follow the steps on this previous project to [Create a React Project using Vite](https://docs.jpdiaz.dev/posts/ecommerce-react-vite-tailwind/)(recommended)

```bash
npm create vite@latest react-rapid-api-1
```

Or, you can also do it with **Create-React-App** (Vite's performance is better)

## 2. SetUp by Customizing the Project

Continue following the steps 1 and 2 on this previous project to [Create a React Project using Vite](https://docs.jpdiaz.dev/posts/ecommerce-react-vite-tailwind/) and SetUp the Project by deleting unnecesary files, installing Tailwind CSS, and add App Plugings.

## 3. Find an API to Consume at [Rapid API](https://rapidapi.com/)

### I. Login to [Rapid API](https://rapidapi.com/).

### II. Add *New App* on [Rapid API](https://rapidapi.com/developer/apps/new-app).

- APPs > Add New App > give it a name > add app

examle: APPs > Add New App > 'Movies' > add app

### III. Search for Free API's

For this tutorial, we Will be using [IMDb](https://rapidapi.com/apidojo/api/imdb8/)

Some other Free and cool API's: 
- [Spotify](https://rapidapi.com/Glavier/api/spotify23/)
- [Call of Duty](https://rapidapi.com/sohamp2812/api/call-of-duty8/)

### IV. Get Endpoint Information From the [IMDb](https://rapidapi.com/apidojo/api/imdb8/) API

A. Go to the **Endpoints** tab in [IMDb](https://rapidapi.com/apidojo/api/imdb8/)

B. Click on **Subscribe to Test** > select the *free* option.

C. Select the **RapidAPI App** previously created above. (Movies)

D. From the dropdown menu on the right, select **(Javascript) > fetch**
 
- Copy the code:
  ```js
  const url = 'https://imdb8.p.rapidapi.com/auto-complete?q=game%20of%20thr';
  const options = {
    method: 'GET',
    headers: {
      'X-RapidAPI-Key': 'VITE_RAPID_API_KEY',
      'X-RapidAPI-Host': 'imdb8.p.rapidapi.com'
    }
  };

  try {
    const response = await fetch(url, options);
    const result = await response.text();
    console.log(result);
  } catch (error) {
    console.error(error);
  }
  ```

> Notice that I am calling a variable: `VITE_RAPID_API_KEY`. This is where its store my actual API Key. For security reasons, You don't want to expose your API key. This `VITE_RAPID_API_KEY` it's commonly saved on a `.env` file.

## 4. Consume the API

### I. Paste the code above on `App.js`
  ```js
  import "./App.css";

  async function App() { // async Function

    // API That I Used: https://rapidapi.com/apidojo/api/imdb8
  const url = 'https://imdb8.p.rapidapi.com/auto-complete?q=game%20of%20thr';
  const options = {
    method: 'GET',
    headers: {
      'X-RapidAPI-Key': 'VITE_RAPID_API_KEY',
      'X-RapidAPI-Host': 'imdb8.p.rapidapi.com'
    }
  };

  try {
    const response = await fetch(url, options);
    const result = await response.text();
    console.log(result);
  } catch (error) {
    console.error(error);
  }  
    return (
      <>
        <div className="flex justify-center items-center h-screen w-screen">
          <h1 className="text-7xl">Rapid API</h1>
        </div>
      </>
    );
  }

  export default App;
  ```

- Got an Error:
> Make sure to add an `async` function to `App` function. this is because the code has an `await` keyword.

### II. Modify the `App.js`

```js
import React, { useEffect } from 'react';
import "./App.css";

function App() {
  // API That I Used: https://rapidapi.com/apidojo/api/imdb8
  const url = 'https://imdb8.p.rapidapi.com/auto-complete?q=game%20of%20thr';
  const options = {
    method: 'GET',
    headers: {
      'X-RapidAPI-Key': 'VITE_RAPID_API_KEY',
      'X-RapidAPI-Host': 'imdb8.p.rapidapi.com'
    }
  };

  useEffect(() => {
    const fetchData = async () => { // async function
      try {
        const response = await fetch(url, options);
        const result = await response.json();
        console.log(result);
      } catch (error) {
        console.error(error);
      }
    };

    fetchData();
  }, []);

  return (
    <>
      <div className="flex justify-center items-center h-screen w-screen">
        <h1 className="text-7xl">Rapid API</h1>
      </div>
    </>
  );
}

export default App;
```

## 5. How to Hide Your API Keys SAFELY in React

### I. Create an Environment File( `.env` ). Then, Save API Key on `.env`

You can create an `.env` file in the application's root directory that contains key/value pairs defining the project's required environment variables. The dotenv library reads this .env file and appends it to process.env.

- For [Vite React app](#Env Variables in Vite)
- For [react-create-app](#How do I create an .env file?)

#### [How to hide API key on Vite? - Env Variables](https://vitejs.dev/guide/env-and-mode)

If you're using Vite, you can access environment variables in your project using `import.meta.env`

Vite has a special handling for environment variables. If you want to expose environment variables to your Vite application, they need to be prefixed with `VITE_`

1. Create a new file named `.env` in the root of your project.
2. In your new `.env` file, add a new key=value pair. For security reasons, you must prepend your key with `VITE_`, for example `VITE_API_KEY=abcdefg123456789`
3. Access it in your code like this: `"X-RapidAPI-Key": import.meta.env.VITE_RAPID_API_KEY`
4. Restart your server development server. In order for React to find and register your newly created environment variable you must restart your server. Do this every time you add or change a variable.
> Remember, you should not commit your .env file to the version control system. It's a good practice to create a .env.example file with all the environment variables used in the application, without the values.

Next steps:

- Check if the environment variable is correctly set in your .env file.
- Make sure to restart your development server after setting the new variables.
- Try to log the environment variable to see if it's correctly loaded.

#### How to hide API key on React create app

[How do I create an .env file for a React-create-app?](https://gist.github.com/Haugen/f6d685f18b4bd8a3cf5bcf6272577c5b)

Here is a simple way to use environment variables in your `react-create-app` project, follow these steps:

1. Create a new file named `.env` in the root of your project.
2. In your new `.env` file, add a new key=value pair. For security reasons, you must prepend your key with `REACT_APP`, for example `REACT_APP_API_KEY=abcdefg123456789`
3. Access it in your code like this: `"X-RapidAPI-Key": process.env.REACT_APP_RAPID_API_KEY`
4. Restart your server development server. In order for React to find and register your newly created environment variable you must restart your server. Do this every time you add or change a variable.
5. Your new variables will now be available throughout your React app via the global `process.env` object. In our case, we could get our API key using `process.env.REACT_APP_API_KEY`.

Additinal notes:

- Since we commonly store secrets in `.env` you probably want to add it to `.gitignore`.
- You don't need to install the `dotenv` package or anything else for this to work.

#### How to hide API key on Nextjs

To hide your API key in a Next.js project, you should use environment variables. Here's how you can do it:

1. Create a `.env.local` file in the root of your project if it doesn't exist already.
2. Add your API key to this file like so: `NEXT_PUBLIC_RAPID_API_KEY=your_api_key_here`. The `NEXT_PUBLIC_` prefix is necessary if you want to access this variable in the browser. If it's server-side only, you can omit this prefix.
3. Now you can access this variable in your code using `process.env.NEXT_PUBLIC_RAPID_API_KEY` for browser-accessible variables, or `process.env.RAPID_API_KEY` for server-side only variables.
4. Make sure to add `.env.local` to your `.gitignore` file to prevent it from being tracked by Git.

Here's the code:
```bash
// Accessing the API key in your code
const apiKey = process.env.NEXT_PUBLIC_RAPID_API_KEY;
```
Remember to replace `your_api_key_here` with your actual API key. Also, don't forget to restart your development server after setting the environment variables.

For your next steps, you might want to:

- Use the API key in your application
- Test that the API key is working correctly
- Make sure the `.env.local` file is ignored by Git

### II. Create a Backend to Store your Key

Storing the API key on an `.env` file and adding the `.env` file to `.gitignore` is good practice but not completely safe.

Anyone can inspect your code and get the API key from the browser.

Here is how you can prevent people from stealing your API key.

- Follow this [Tutorial](https://www.youtube.com/watch?v=FcwfjMebjTU&t=0s) from Ania.

A. Create a `./backend.js` in the root of your project

```js
const PORT = 8000;
const express = require("express");
const cors = require("cors");
const dotenv = require("dotenv").config();
// run: npm install express cors node-fetch dotenv

const app = express();

// Use dynamic import for 'node-fetch'
let fetch;
import("node-fetch").then((nodeFetch) => {
  fetch = nodeFetch;
});

app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});
```

> Got an Error? Use code from `step F` instead.

B. Install the dependencies: [express](https://www.npmjs.com/package/express) [cors](https://www.npmjs.com/package/cors) [node-fetch](https://www.npmjs.com/package/node-fetch) [dotenv](https://www.npmjs.com/package/dotenv)

```bash
npm install express cors node-fetch dotenv
```

C. Add a Script on `package.json`

```json
 "scripts": {
    "backend": "nodemon index.js",
```

It should look like this...
```json
{
  "name": "movies",
  "private": true,
  "version": "0.0.0",
  "type": "module",
  "scripts": {
    "backend": "nodemon index.js",
    "dev": "vite",
    "build": "vite build",
    "lint": "eslint . --ext js,jsx --report-unused-disable-directives --max-warnings 0",
    "preview": "vite preview"
  },
  "dependencies": {
    "cors": "^2.8.5",
    "dotenv": "^16.3.1",
    "express": "^4.18.2",
    "node-fetch": "^3.3.2",
    "nodemon": "^3.0.1",
    "react": "^18.2.0",
    "react-dom": "^18.2.0"
  },
  "devDependencies": {
    "@types/react": "^18.2.37",
    "@types/react-dom": "^18.2.15",
    "@vitejs/plugin-react": "^4.2.0",
    "autoprefixer": "^10.4.16",
    "eslint": "^8.53.0",
    "eslint-plugin-react": "^7.33.2",
    "eslint-plugin-react-hooks": "^4.6.0",
    "eslint-plugin-react-refresh": "^0.4.4",
    "postcss": "^8.4.31",
    "tailwindcss": "^3.3.5",
    "vite": "^5.0.0"
  }
}
```

D. Install [nodemon](https://www.npmjs.com/package/nodemon)

```bash
npm install nodemon
```

E. Run the Backend to test it

```bash
npm run backend
```
> Warning: If you got an error: `require is not defined in ES module scope, you can use import instead. This file is being treated as an ES module because it has a '.js' file extension and 'C:\Users\juanc\Documents\Github\ju\package.json' contains "type": "module". To treat it as a CommonJS script, rename it to use the '.cjs' file extens`

F. Fixing Error

The error message indicates that `require` is not defined in ES module scope. This is because your project is set to use ES modules due to the "type": "module" in your `package.json` file.

You should change all your `require` statements to `import` statements. Here's how you can modify your `backend.js` code:

```js
import express from "express";
import cors from "cors";
import { config as dotenvConfig } from "dotenv";
import nodeFetch from "node-fetch";

const PORT = 8000;

// run: npm install express cors node-fetch dotenv

const app = express();

let fetch = nodeFetch;

dotenvConfig();

app.listen(PORT, () => {
  console.log(`Server running on port ${PORT}`);
});
```

> Run the Backend to test it again `npm run backend`













## 6. Style `App.js` using Tailwind CSS

```js
import React, { useEffect } from "react";
import "./App.css";

function App() {
  const url = "https://imdb8.p.rapidapi.com/auto-complete?q=game%20of%20thr";
  const options = {
    method: "GET",
    headers: {
      "X-RapidAPI-Key": "VITE_RAPID_API_KEY",
      "X-RapidAPI-Host": "imdb8.p.rapidapi.com",
    },
  };

  useEffect(() => {
    // async function:
    const fetchData = async () => {
      try {
        const response = await fetch(url, options);
        const result = await response.json();
        console.log(result);
      } catch (error) {
        console.error(error);
      }
    };

    fetchData();
  }, []);

  return (
    <>
      <div className="flex flex-col items-center justify-center min-h-screen bg-gray-100">
        <div className="text-center">
          <h1 className="text-4xl md:text-6xl font-bold mb-4">Rapid API</h1>
        </div>
        <form className="w-full max-w-md">
          <input
            className="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
            type="text"
            placeholder="Search for a movie..."
            value={endPoint}
          />
          <button
            className="mt-4 bg-blue-500 hover:bg-blue-700 transition duration-300 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline w-full"
            type="submit"
          >
            Search
          </button>
        </form>
      </div>
    </>
  );
}

export default App;
```

## 7. Create **useState** Hooks

Modify the `App.js` file. Read the comments

```js
import React, { useEffect, useState } from "react";
import "./App.css";

function App() {
  const url = "https://imdb8.p.rapidapi.com/auto-complete?q=game%20of%20thr";
  const options = {
    method: "GET",
    headers: {
      "X-RapidAPI-Key": "VITE_RAPID_API_KEY",
      "X-RapidAPI-Host": "imdb8.p.rapidapi.com",
    },
  };
  // First element from useState is the state itself (""). The initial value, in this case an empty string
  // Second is the function that will update the state (setEndPoint). The "Changer" function
  const [endPoint, setEndPoint] = useState("");
  // "Changer" function: it change the state of the endPoint variable by taking the value from the input
  const onChangeHandler = (event) => {
    setEndPoint(event.target.value);
  };

  // "Submit" function: it prevent the default behaviour of the form. It won't refresh the page
  const onSubmitHandler = (event) => {
    event.preventDefault();
    console.log("submit");
  };

  // container is an empty array. setContainer is the function that will update the state of the container
  const [container, setContainer] = useState([]);

  useEffect(() => {
    // async function:
    const fetchData = async () => {
      try {
        const response = await fetch(url, options);
        const result = await response.json();
        // console.log(result);    console.log(result.d);
        setContainer(result.d); // setContainer is now an array of objects that contains the data from the API
      } catch (error) {
        console.error(error);
      }
    };

    fetchData();
  }, []);

  return (
    <>
      <div className="flex flex-col items-center justify-center min-h-screen bg-gray-100">
        <div className="text-center">
          <h1 className="text-4xl md:text-6xl font-bold mb-4">Rapid API</h1>
        </div>
        <form className="w-full max-w-md" onSubmit={onSubmitHandler}>
          <input
            className="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline"
            type="text"
            placeholder="Search for a movie..."
            value={endPoint}
            onChange={onChangeHandler}
          />
          <button
            className="mt-4 bg-blue-500 hover:bg-blue-700 transition duration-300 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline w-full"
            type="submit"
          >
            Search
          </button>
        </form>
      </div>
    </>
  );
}

export default App;
```

## 8. Search for Movies

### I. Modify the URL

In the API's URL, replace the information after the `q=` for `+${endPoint}`

in other words:
```js
// change:
  const url = "https://imdb8.p.rapidapi.com/auto-complete?q=game%20of%20thr";

// for:
  const url = `https://imdb8.p.rapidapi.com/auto-complete?q=+${endPoint}`;
```

> I also had to organize the code by moving the use states to the top since its trying to use variables that havent been declared and it was giving me an error (*Uncaught ReferenceError: Cannot access 'endPoint' before initialization at App*).

> Note: The error message is indicating that you're trying to access the endPoint variable before it's been initialized. This is happening because you're using endPoint in the url constant declaration, which is above the useState hook where endPoint is initialized.

### II. Move the URL inside the useEffect 

This way, the url is updated every time endPoint changes.

The `App.js` should look like this:

```js

```

## 9. Display or Render data from the API

Modify the `App.js`

```js

```

## 10. Render Data when clicking Submit

The app has an issue, it is rendering everytime you type a letter in the input.
Instead. We want to render when clicking on Search button.

```js

```






Deployment

There are multiple ways to deploy a React app in just minutes. Here is an article that explains 8 different ways to [Deploy a React App](https://blog.logrocket.com/8-ways-deploy-react-app-free/#:~:text=For%20your%20React%20app%2C%20you,whenever%20you%20push%20your%20changes.).

[![Vercel](https://img.shields.io/badge/Vercel-000000.svg?style=for-the-badge&logo=Vercel&logoColor=white)](https://www.Vercel.com)

- From a [Github Repo](https://www.youtube.com/watch?v=sauV-3_Nn60)
- From a [new project on your machine](https://www.youtube.com/watch?v=FvsvHzcwOmQ)

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

- [Rapid API](https://rapidapi.com/developer/apps/new-app).
- [IMDb](https://rapidapi.com/apidojo/api/imdb8/)
- [Tutorial](https://www.youtube.com/watch?v=FcwfjMebjTU&t=0s)
- [express](https://www.npmjs.com/package/express)
- [cors](https://www.npmjs.com/package/cors)
- [node-fetch](https://www.npmjs.com/package/node-fetch)
- [dotenv](https://www.npmjs.com/package/dotenv)
- [nodemon](https://www.npmjs.com/package/nodemon)