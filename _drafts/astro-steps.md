---
layout: post
title: "Para Montar de Forma Rapida el Proyecto del Curso de Creación de Páginas Web con Astro"
categories: astro
tags: draft
---

Este archivo sirve como guia para correr el proyecto e instalar las dependencias necesatias si por alguna razon me toca empezar de cero y crear nuevamente una pagina con Astro.

Paso a paso del curso basandonos en el [Repo del curso](https://github.com/platzi/astrobuild.tips/commits/main):

## 1. Inicializar Proyecto ★ [Clase 6](https://platzi.com/clases/6207-astro/60187-conoce-tu-proyecto-colaborativo-astrobuildtips/ "Conoce tu proyecto colaborativo: astrobuild.tips")

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

## 2. Tailwind CSS ★ [Clase 7](https://platzi.com/clases/6207-astro/60188-configuracion-de-tailwind-css/ "Configuración de Tailwind CSS")

> [**Hyper UI**](https://www.hyperui.dev/): Free Open Source Tailwind CSS Components

- instalación automática de Tailwind en Astro: `Es mas rapido`

  ```bash
  npx astro add tailwind
  ```

  > En el curso se instala Tailwind en Astro usando versiones especificas
  >
  > `npm install @astrojs/tailwind@3.0.1 tailwindcss@3.2.4`

## 3. Componentes ★ [Clase 8](https://platzi.com/clases/6207-astro/60189-configuracion-de-typescript/ "Configuración de TypeScript")

1. Agregar Componentes al Proyecto.
   - **Ej**: Usando un [Blog card](https://www.hyperui.dev/components/marketing/blog-cards) de hyperui
2. Installar el plugin necesario
   ```bash
   npm install @tailwindcss/line-clamp
   ```
3. Agregamos el plugin a `tailwind.config.cjs`
   ```bash
   plugins: [ require('@tailwindcss/line-clamp') ]
   ```
4. Compilar y correr el proyecto:

   ```bash
   npm run build
   npm run dev
   ```

## 4. [ADD] First Commit ★ [Clase 9](https://platzi.com/clases/6207-astro/60190-github-vscode-prettier-astro-config/ "GitHub, VSCode, Prettier, Astro config")

### GitHub

1. Crear repo
2. inicializar y linkiar proyecto.
3. hacer mi first commit sigiendo los pasos de GitHub.

## 5. [UPDATE] Config

### Prettier

1. Correr:

   ```bash
   npm install --save-dev prettier@2.8.4 prettier-plugin-astro@0.8.0
   ```

2. Agregar el nuevo archivo `prettierrc.cjs`

3. Compilar y correr el proyecto:

   ```bash
   npm run build
   npm run dev
   ```

4. Subir los cambios a GitHub: [UPDATE] Config

---

## 6. [ADD] Components ★ [Clase 10](https://platzi.com/clases/6207-astro/60191-componentes-en-astro/ "Componentes en Astro")

Para esta seccion de **componentes en Astro**, `solo debo copiar el codigo del repo`. No es necesario instalar ninguna dependencia. Y luego subir los cambios a GitHub.

## 7. [ADD] Pages ★ [Clase ]()

2. [ADD] Layouts ★ [Clase ]()
3. [ADD] Markdown ★ [Clase ]()
4. [ADD] MDX -> npx astro add mdx ★ [Clase ]()
5. [ADD] Static Routes ★ [Clase ]()
6. [ADD] Dynamic Routes ★ [Clase ]()
7. [ADD] Dynamic Template ★ [Clase ]()
8. install React - npx astro add react
9. install @headlessui/react

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
