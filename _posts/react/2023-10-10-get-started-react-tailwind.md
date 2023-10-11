---
layout: post
title: "Get Started React Tailwind"
date: 2023-10-10
categories: react
tags: react tailwind css responsive
# image: /assets/img/featured-posts/gamer.jpg
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

## 5. Run the App in Localhost

```js
	npm start
```

Go to `localhost:3000`

## 6. Deployment

[For FREE](https://blog.logrocket.com/8-ways-deploy-react-app-free/#:~:text=For%20your%20React%20app%2C%20you,whenever%20you%20push%20your%20changes.)

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

- [Create a Landing Page with React.JS and tailwind CSS](https://medium.com/@chiragmehta900/create-a-responsive-landing-page-with-react-js-and-tailwind-css-fa09ffb24cb7)
- [Pesticides extension](https://chrome.google.com/webstore/detail/pesticide-for-chrome/bakpbgckdnepkmkeaiomhmfcnejndkbi) to check the layout of the page

<p align="right">(<a href="#top">back to top</a>)</p>
````
