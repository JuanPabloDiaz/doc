---
layout: post
title: "Get Started React Tailwind"
date: 2023-10-10
categories: react
tags: react tailwind css responsive
image: /assets/img/featured-posts/react_tailwind.jpg
---

This is an step by step article on how to create, setup and deploy a simple React App using React.js, and Tailwind CSS.

#### [Demo]()

<!-- ABOUT THE PROJECT -->

This project was developed using

[![React](https://img.shields.io/badge/React-61DAFB.svg?style=for-the-badge&logo=React&logoColor=black)](https://www.w3schools.com/whatis/whatis_react.asp)
[![Tailwind](https://img.shields.io/badge/Tailwind%20CSS-06B6D4.svg?style=for-the-badge&logo=Tailwind-CSS&logoColor=white)](https://tailwindcss.com/)

## 1. Create a React Project

```bash
npx create-react-app my-project
```

- [Getting Started with React.js](https://www.w3schools.com/react/react_getstarted.asp)

## 2. Modify the React App

A. `Delete` files:

- App.css
- App.test.js
- logo.svg
- reportWebVital
- SetupTests.js
  - Warning: I will get some error if I start the server (thats ok)

B. Edit `index.js` and delete the `reportWebVitals function and import reportWebVitals`

C. Edit `App.js` by deleting the `<header>`, delete the `import App.css, import logo and add import React from react;` (Try changing the HTML content and save the file.)

D. Create components:

- Create the `components` folder inside `src`
- Create the `FileComponents.jsx` inside the `components` folder.

## 3. [Install Tailwind CSS](https://tailwindcss.com/docs/guides/create-react-app)

- Free libraries of [Tailwind CSS Components](https://dev.to/cruip/25-places-where-you-can-get-free-tailwind-css-components-47lm#Tailwind%20Design)
  Free Tailwind CSS Templates, Components and Resources
  Fully responsive libraries, multi-purpose UI kits, built with Tailwind CSS, for start-ups and products of any kind. `Build beautiful interfaces without reinventing the wheel.`

|                                                      |                                                      |                                        |                                                        |                                                                                                     |                                      |
| ---------------------------------------------------- | ---------------------------------------------------- | -------------------------------------- | ------------------------------------------------------ | --------------------------------------------------------------------------------------------------- | ------------------------------------ |
| [FloatUI](https://www.floatui.com/components)        | [a17t](https://a17t.miles.land/)                     | [Headless UI](https://headlessui.com/) | [Tailwind Components](https://tailwindcomponents.com/) | [Treact](https://treact.owaiskhan.me/)                                                              | [Mamba UI](https://mambaui.com/)     |
| [Tailwind Awesome](https://www.tailwindawesome.com/) | [Kometa UI Kit](https://kitwind.io/products/kometa)  | [Tailwind UI Kit](https://tuk.dev/)    | [Meraki UI](https://merakiui.com/)                     | [Tailwind Starter Kit](https://www.creative-tim.com/learning-lab/tailwind-starter-kit/presentation) | [Kutty](https://kutty.netlify.app/)  |
| [HyperUI](https://www.hyperui.dev/)                  | [Tailwind Toolbox](https://www.tailwindtoolbox.com/) | [DaisyUI](https://daisyui.com/)        | [Flowbite](https://www.flowbite-react.com/)            | [PostSrc](https://postsrc.com/)                                                                     | [Tailblocks](https://tailblocks.cc/) |

[Tailwind Elements](https://tw-elements.com/)

## 4. Install additional functionalities

### Icons

Install [react-icons](https://react-icons.github.io/react-icons/) to the project

```bash
npm install react-icons --save
```

- `npm install @headlessui/react`
- `npm install @heroicons/react`

  - Add `React-icon` to the fileComponent.jsx: - Import react-icons to `file.jsx`

  Example

  ```js
  import { AiOutlineClose, AiOutlineMenu } from "react-icons/ai";
  <AiOutlineMenu />
  <AiOutlineClose />
  ```

### Animation

Install [Framer Motion](https://www.framer.com/motion/) to the project ([learn more](https://www.framer.com/motion/introduction/##installation))

```bash
npm install framer-motion
```

- Add `framer-motion` to the fileComponent.jsx: - Import framer-motion to `file.jsx`

  Example

  ```js
  import framer-motion from "react";
  ```

  Project example: [Animated expandable cards with Tailwind CSS and Framer Motion](https://www.youtube.com/watch?v=bhRUBc0xjUo)

### Manage all of your changes to the document head: (Title, Icon, description, url...)

Install [Helmet](https://www.npmjs.com/package/react-helmet) to the project

```bash
npm install --save react-helmet
```

- [learn more](https://www.digitalocean.com/community/tutorials/react-react-helmet)

- Import and Add the `<Helmet>` tag to the fileComponent.jsx:

```bash
import React from "react";
import {Helmet} from "react-helmet";

class Application extends React.Component {
  render () {
    return (
        <div className="application">
            <Helmet>
                <meta charSet="utf-8" />
                <title>My Title</title>
                <link rel="canonical" href="http://mysite.com/example" />
                <meta name="description" content="Helmet application" />
            </Helmet>
            ...
        </div>
    );
  }
};
```

Example

```js

```

Project example: []()

For the Icon App:

1. Create or [Download](https://icon-icons.com/) your favicon. (download img as ico)
2. Replace the `favicon.ico` inside the `public` folder with yours.
3. Run the project.

[Video: How to Add a Favicon and Title to React app](https://www.youtube.com/watch?v=7pJmM-XdPm8)

## 5. Run the App in Localhost

```bash
npm start
```

Go to `localhost:3000`

## 6. Deployment

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

[![](https://img.shields.io/badge/Platzi_Profile-121f3d?style=for-the-badge&logo=Platzi&logoColor=98CA3F)](https://platzi.com/p/DiazJuan/)<!-- ACKNOWLEDGMENTS -->

## Acknowledgments 📚

Resources list that I find helpful and would like to give credit to.

- [Tailwindcss.com](https://tailwindcss.com/)
- [Tailwind CSS Cheat Sheet](https://tailwindcomponents.com/cheatsheet/)
- Video: [How To Use Tailwind CSS With React](https://www.youtube.com/watch?v=W99CEOBCPSI)
- [Create a Landing Page with React.JS and tailwind CSS](https://medium.com/@chiragmehta900/create-a-responsive-landing-page-with-react-js-and-tailwind-css-fa09ffb24cb7)
- [Pesticides extension](https://chrome.google.com/webstore/detail/pesticide-for-chrome/bakpbgckdnepkmkeaiomhmfcnejndkbi) to check the layout of the page
- How to set [React background Image](https://www.freecodecamp.org/news/react-background-image-tutorial-how-to-set-backgroundimage-with-inline-css-style/)

<p align="right">(<a href="#top">back to top</a>)</p>
````
