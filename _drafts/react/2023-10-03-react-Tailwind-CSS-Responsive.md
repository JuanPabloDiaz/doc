---
layout: post
title: "React Tailwind CSS Responsive"
date: 2023-10-04
categories: platzi 2023
tags: react tailwind css responsive
image: /assets/img/featured-posts/react_tailwind.jpg
---

<!-- ABOUT THE PROJECT -->

Landing page from [Youtube](https://www.youtube.com/watch?v=ZU-drSVodBw&t=590s)

## Description 💡

This project was developed using

[![React](https://img.shields.io/badge/React-61DAFB.svg?style=for-the-badge&logo=React&logoColor=black)](https://www.w3schools.com/whatis/whatis_react.asp)
[![Tailwind](https://img.shields.io/badge/Tailwind%20CSS-06B6D4.svg?style=for-the-badge&logo=Tailwind-CSS&logoColor=white)](https://tailwindcss.com/)

## [Demo]()

## Step by Step

1. Create your React project: `npx create-react-app my-project`
   - [Getting Started with React](https://www.w3schools.com/react/react_getstarted.asp)
2. Once the react app is created, `Delete` files from the react template:
   - App.css
   - App.test.js
   - logo.svg
   - reportWebVital
   - SetupTests.js
     I will get some error if I start the server (thats ok)
3. Edit `index.js` and delete the `reportWebVitals function and import reportWebVitals`
4. Edit `App.js` by deleting the <header>, delete the `import App.css, import logo and add import React from react;`
5. [Install Tailwind CSS with Create React App](https://tailwindcss.com/docs/guides/create-react-app)
6. Create the `components` folder inside `src`
7. Create `Navbar.jsx` inside the `components` folder
   ```js
   import React from "react";
   const Navbar = () => {
     return (
       <div className="flex justify-between items-center h-24 max-w-[1240px] mx-auto text-white">
         <h1 className="w-full text-3xl font-bold text-[#00df9a]">REACT.</h1>
         <ul className="flex">
           <li className="p-4">Home</li>
           <li className="p-4">Company</li>
           <li className="p-4">Resources</li>
           <li className="p-4">About</li>
           <li className="p-4">Contact</li>
         </ul>
       </div>
     );
   };
   export default Navbar;
   ```
8. `Import` and `add` the <Navbar> component to the `App.js` file.
   ```js
   import React from "react";
   import Navbar from "./components/Navbar";
   function App() {
     return (
       <div>
         <Navbar />
       </div>
     );
   }
   export default App;
   ```
9. Use the [pesticides extension](https://chrome.google.com/webstore/detail/pesticide-for-chrome/bakpbgckdnepkmkeaiomhmfcnejndkbi) to check the layout of the page in localhost:3000
10. Install the [react-icons](https://react-icons.github.io/react-icons/) to the project
    `npm install react-icons --save`
11. install: `npm install @headlessui/react`
12. install: `npm install @heroicons/react`
13. Import react-icons to `Navbar.jsx`

```js
	import { AiOutlineClose, AiOutlineMenu } from "react-icons/ai";
	<AiOutlineMenu />
	<AiOutlineClose />
```

### Open Cards Section

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

- [w3schools](https://www.w3schools.com/)
- [Tiny png](https://tinypng.com/)
- [awesome-readme](https://github.com/matiassingers/awesome-readme)
- [PurpleBooth](https://gist.github.com/PurpleBooth/109311bb0361f32d87a2)
- [dbader](https://github.com/dbader/readme-template)
- [zenorocha](https://gist.github.com/zenorocha/4526327)
- [fvcproductions](https://gist.github.com/fvcproductions/1bfc2d4aecb01a834b46)
- [Git doc](https://git-scm.com/doc)
<p align="right">(<a href="#top">back to top</a>)</p>

<!-- MARKDOWN LINKS & IMAGES -->
<!-- https://www.markdownguide.org/basic-syntax/#reference-style-links -->

[contributors-shield]: https://img.shields.io/github/contributors/othneildrew/Best-README-Template.svg?style=for-the-badge
[contributors-url]: https://github.com/othneildrew/Best-README-Template/graphs/contributors
[forks-shield]: https://img.shields.io/github/forks/othneildrew/Best-README-Template.svg?style=for-the-badge
[forks-url]: https://github.com/othneildrew/Best-README-Template/network/members
[stars-shield]: https://img.shields.io/github/stars/othneildrew/Best-README-Template.svg?style=for-the-badge
[stars-url]: https://github.com/othneildrew/Best-README-Template/stargazers
[issues-shield]: https://img.shields.io/github/issues/othneildrew/Best-README-Template.svg?style=for-the-badge
[issues-url]: https://github.com/othneildrew/Best-README-Template/issues
[license-shield]: https://img.shields.io/github/license/othneildrew/Best-README-Template.svg?style=for-the-badge
[license-url]: https://github.com/othneildrew/Best-README-Template/blob/master/LICENSE.txt
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/othneildrew
[product-screenshot]: images/screenshot.png
