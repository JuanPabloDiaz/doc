---
layout: post
title: "Para Montar de Forma Rapida el Proyecto del Curso de Creación de Páginas Web con Astro"
categories: astro
tags: draft
---

Este archivo sirve como guia para correr el proyecto e instalar las dependencias necesatias si por alguna razon me toca empezar de cero y crear nuevamente una pagina con Astro.

Paso a paso del curso basandonos en el [Repo del curso](https://github.com/platzi/astrobuild.tips/commits/main):

1. [ADD] First Commit ★ [Clase 6](https://platzi.com/clases/6207-astro/60187-conoce-tu-proyecto-colaborativo-astrobuildtips/)

   - 1.1 inicializar el Proyecto desde Cero:
     - `npm create astro@latest -- --template astrobuild.tips`
     - Or `npm create astro@2.0.2 astrobuild.tips`
   - 1.2 Compilar el proyecto para verificar que no tenga errores:
     - `npm run build`
   - 1.3 Correr el proyecto en local:

     - `npm run dev`

---

- npm install @tailwindcss/line-clamp

2. [UPDATE] Config ★ [Clase ]()
3. [ADD] Components ★ [Clase ]()
4. [ADD] Pages ★ Clase ]()
5. [ADD] Layouts ★ [Clase ]()
6. [ADD] Prettier -> npm install --save-dev prettier@2.8.4 prettier-plugin-astro@0.8.0
7. [ADD] Markdown ★ [Clase ]()
8. [ADD] MDX -> npx astro add mdx ★ [Clase ]()
9. [ADD] Static Routes ★ [Clase ]()
10. [ADD] Dynamic Routes ★ [Clase ]()
11. [ADD] Dynamic Template ★ [Clase ]()
12. install React - npx astro add react
13. install @headlessui/react

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
