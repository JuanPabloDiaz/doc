---
layout: post
title: "Next.js Full-Stack: The Magic of a Single Framework"
date: 2025-06-27
categories: react
tags: react next.js tailwind css full-stack
image: /assets/img/featured-posts/next-js-13.jpg
---

As a developer, the traditional workflow has always seemed unnecessarily complex to me. You start by creating your frontend with React, then you realize you need dynamic data, so you set up an Express server on another port. Suddenly, you have two terminals open, you're battling CORS issues between localhost:3000 and localhost:5000, and you're maintaining two completely separate configurations. In the end, deploying becomes a headache: two builds, two deployments, and something always breaks in production. Next.js changes this completely, unifying frontend and backend into a single project, with a single command and a simplified deployment.

When I started developing **CountryHub**, my goal was to create a web application to explore countries of the world — with flags, fun facts, and an interactive quiz — without getting bogged down by unnecessary configurations. I wanted a tool that would allow me to build both the frontend and the backend in a simple and efficient way. That’s when I discovered the power of **Next.js as a full-stack framework**. In this post, I’ll tell you how I built my app using only Next.js, how I designed its architecture, and why I think it’s a great option for beginners and enthusiasts like us.

- **Demo**: [CountryHub](https://country-hub-jd.vercel.app/)
- **Repository**: [GitHub](https://github.com/JuanPabloDiaz/countryHub)

## What is CountryHub?

CountryHub is an educational web application with three main features:

- **List of Countries**: Explore all countries with their flags and basic information.
- **Country Details**: Dive into data such as capital, currency, population, and more.
- **Interactive Quiz**: Test your knowledge with random questions about countries.

The special thing about this project is that everything — frontend and backend — is built with Next.js. I didn’t need external servers or additional frameworks. Just Next.js and a bit of creativity!

## The Architecture of CountryHub: Everything in One Place

Next.js allowed me to organize my project clearly and build a complete application without leaving the ecosystem. Here, I’ll explain how I structured CountryHub and how Next.js made it possible for everything to work in harmony.

### Project Structure

The folder organization in Next.js is super intuitive. Here’s how I organized CountryHub:

```
countryHub/
├── app/                   # Heart of the project
│   ├── api/              # Backend: Endpoints for data
│   │   ├── countries/    # List and details of countries
│   │   └── quiz/         # Quiz questions and answers
│   ├── countries/        # Frontend: Dynamic country pages
│   └── quiz/             # Frontend: Quiz pages
├── components/           # Reusable components
├── data/                 # JSON data of countries
├── lib/                  # Functions to handle data
├── utils/                # General utilities
└── public/               # Images and static assets
```

- **Frontend**: The pages are in `app/`, using Next.js 13’s App Router for static routes (like the homepage) and dynamic routes (like `/countries/[slug]`).
- **Backend**: The API Routes in `app/api/` serve the data that the frontend needs, all from the same project.

### How I Built the Backend with API Routes

Next.js includes **API Routes**, a simple way to create REST endpoints without setting up a separate server. In CountryHub, I used these routes to handle all the backend logic. Here are some examples:

- **List of Countries**:

```javascript
// app/api/countries/route.js

export async function GET() {
  const countries = await fetchCountriesData();
  return Response.json(countries);
}
```

- **Country Details**:

```javascript
// app/api/countries/[slug]/route.js

export async function GET(request, { params }) {
  const country = await fetchCountryBySlug(params.slug);
  return Response.json(country);
}
```

- **Random Quiz Question**:

```javascript
// app/api/quiz/random/route.js

export async function GET() {
  const question = await fetchRandomQuizQuestion();
  return Response.json(question);
}
```

These functions are like mini-servers within my project. Next.js executes them when requests are made to the corresponding routes (for example, `/api/countries`). All the code lives in my project, and I didn’t have to worry about additional configurations.

### Connecting the Frontend with the Backend

In the frontend, I consume these endpoints directly with `fetch`. For example, to display the details of a country:

```javascript
// app/countries/[slug]/page.js

async function getCountry(slug) {
  const res = await fetch(`http://localhost:3000/api/countries/${slug}`);
  return res.json();
}

export default async function CountryPage({ params }) {
  const country = await getCountry(params.slug);
  return (
    <div>
      <h1>{country.name}</h1>
      <p>Capital: {country.capital}</p>
      {/* More details */}
    </div>
  );
}
```

Since the frontend and backend run on the same server (thanks to Next.js), there are no CORS issues or complications. Everything flows perfectly.

## Advantages of Next.js as a Full-Stack Framework

Using Next.js as my full stack brought benefits that I loved:

1. **All in One**:

   - A single command (`npm run dev`) starts both frontend and backend.
   - No need to switch between projects or terminals.

2. **Rapid Development**:

   - Hot reload works for both the frontend and the API Routes.
   - Less time configuring, more time creating.

3. **Easy Deployment**:

   - A single `npm run build` prepares everything.
   - Vercel (or any compatible hosting) deploys it without complications.

4. **Simple Scalability**:

   - The folder structure grows with me: more routes, more components, all organized.

5. **Built-in Optimization**:
   - Images, performance, and SEO ready to use without manual configurations.
   - **Automatic Optimization**: Next.js handles code splitting, optimized image loading, and more automatically.

## How I Made CountryHub Only with Next.js

So, how was it possible to build this entire app without additional tools? Here’s the step-by-step:

1. **Data**: I stored country information in JSON files in `/data/`.
2. **Backend**: I created API Routes in `app/api/` to transform and serve that data.
3. **Frontend**: I designed pages in `app/` that consume the API Routes with `fetch`.
4. **Styles**: I used Tailwind CSS for fast and responsive design.
5. **Optimization**: I took advantage of Next.js tools like the `Image` component.

I didn’t need Express, external databases, or additional servers. Next.js handled everything, from routing to deployment.

## Use Cases for Next.js Full-Stack

Next.js as a full-stack framework shines in projects like:

- **Personal Projects**: Perfect for small to medium-sized apps like CountryHub.
- **Prototypes**: Build something functional quickly without complex configurations.
- **Static or Semi-Static Content**: Ideal if your data doesn’t change much.
- **Educational or Interactive Applications**: Like my quiz, where simplicity matters.

## Disadvantages or Limitations

Although I loved using it, Next.js full-stack has its limits:

- **Complex Logic**: If you need to process real-time data or handle heavy logic, you might need a separate backend.
- **Massive Scaling**: For huge apps with microservices, you might want more flexibility.
- **Learning Curve**: If you’re new, API Routes and the App Router might require some practice.

Still, for projects like mine, these limitations weren’t a problem.

## Tips for Beginners

If you’re starting with Next.js or want to try it as a full-stack:

1. Create a project with `npx create-next-app@latest`.
2. Add a simple API Route in `app/api/hello/route.js`.
3. Connect a page to that API with `fetch`.
4. Explore and have fun!

## Final Reflection

As a developer, I’ve always looked for tools that let me focus on what matters: solving problems and creating useful things. Next.js gave me that freedom. For example, when I worked on CountryHub, I went from fighting with configurations to having a full-stack project running in hours, not days. The simplicity of unifying frontend and backend saved me time and headaches, leaving me space to experiment and enjoy the process.
If you’ve ever felt the weight of the traditional workflow, I invite you to try Next.js as your full stack. It’s a change that can transform how you develop. Have you tried it yet? If not, what are you waiting for to start?
