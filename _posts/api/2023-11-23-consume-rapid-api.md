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

- Follow this [Tutorial](https://www.youtube.com/watch?v=FcwfjMebjTU&t=0s) from Ania.



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

