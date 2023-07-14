---
layout: post
title: "Para Montar de Forma Rapida el Proyecto del Curso de Creación de Páginas Web con Astro"
categories: astro
tags: draft
---

Este archivo sirve como guia para correr el proyecto e instalar las dependencias necesatias si por alguna razon me toca empezar de cero y crear nuevamente una pagina con Astro.

Paso a paso del curso basandonos en el [Repo del curso](https://github.com/platzi/astrobuild.tips/commits/main):

## 1. [ADD] First Commit ★ [Clase 6](https://platzi.com/clases/6207-astro/60187-conoce-tu-proyecto-colaborativo-astrobuildtips/ "Conoce tu proyecto colaborativo: astrobuild.tips")

1. inicializar el Proyecto desde Cero:

   ```bash
   npm create astro@2.0.2 astrobuild.tips
   ```

2. Compilar el proyecto para verificar que no tenga errores:

   ```bash
   npm run build
   ```

3. Correr el proyecto en local:

   ```bash
   npm run dev
   ```

## 2. [UPDATE] Config ★ [Clase 7](https://platzi.com/clases/6207-astro/60188-configuracion-de-tailwind-css/ "Configuración de Tailwind CSS")

> [**Hyper UI**](https://www.hyperui.dev/): Free Open Source Tailwind CSS Components

- instalación automática de Tailwind en Astro: `Es mas rapido`

  ```bash
  npx astro add tailwind
  ```

  > En el curso se instala Tailwind en Astro usando versiones especificas
  >
  > `npm install @astrojs/tailwind@3.0.1 tailwindcss@3.2.4`

  ***

- npm install @tailwindcss/line-clamp

## 3. [ADD] Components ★ [Clase 8](https://platzi.com/clases/6207-astro/60189-configuracion-de-typescript/ "Configuración de TypeScript")

2.  [ADD] Pages ★ Clase ]()
3.  [ADD] Layouts ★ [Clase ]()
4.  [ADD] Prettier -> npm install --save-dev prettier@2.8.4 prettier-plugin-astro@0.8.0
5.  [ADD] Markdown ★ [Clase ]()
6.  [ADD] MDX -> npx astro add mdx ★ [Clase ]()
7.  [ADD] Static Routes ★ [Clase ]()
8.  [ADD] Dynamic Routes ★ [Clase ]()
9.  [ADD] Dynamic Template ★ [Clase ]()
10. install React - npx astro add react
11. install @headlessui/react

Correr el projecto

```bash
   npm run dev
```

Compilar el projecto

```bash
   npm run build
```

# Astro Islands

## Recursos:

- La pagina es [Tailwind UI](https://tailwindui.com/).
- El [Header](https://tailwindui.com/components/marketing/elements/headers#component-6f74644bcfda42fc3d6735054d46bbe1) del proyecto.

debo instalar dependecias:

```bash
npm install @headlessui/react
```

Para los iconos

```bash
npm install @heroicons/react
```

`npx astro add sitemap`

`	site: "https://jpdiaz.top",`
