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

### IV. Get Information From the [IMDb](https://rapidapi.com/apidojo/api/imdb8/) API

- Go to the **Endpoints** tab in [IMDb](https://rapidapi.com/apidojo/api/imdb8/)
- Click on **Subscribe to Test** > select the *free* option.
- Select the **RapidAPI App** previously created above. (Movies)
- From the dropdown menu on the right, select **(Javascript) > fetch**
- Copy the code:
  ```js
  const url = 'https://imdb8.p.rapidapi.com/auto-complete?q=game%20of%20thr';
  const options = {
    method: 'GET',
    headers: {
      'X-RapidAPI-Key': 'db2542358dmsh9f6d5b036b73a56p1ad6dbjsnd4d4bab6da8a',
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
- Paste it on `App.js`
  ```js
  import "./App.css";

  function App() {
    // API That I Used: https://rapidapi.com/apidojo/api/imdb8
  const url = 'https://imdb8.p.rapidapi.com/auto-complete?q=game%20of%20thr';
  const options = {
    method: 'GET',
    headers: {
      'X-RapidAPI-Key': 'db2542358dmsh9f6d5b036b73a56p1ad6dbjsnd4d4bab6da8a',
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

## 6. Deployment

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

