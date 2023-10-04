---
layout: post
title: "Montar de Forma Rapida el Proyecto del Curso de Creación de Páginas Web con Astro"
categories: astro
tags: draft
---

Este archivo tiene como finalidad guiar al usuario en la creacion de un proyecto en Astro. Como correr el proyecto e instalar las dependencias necesarias.
Con esta informacion debe de ser capas de empezar de cero y crear nuevamente una pagina usando el framework de Astro.

El [Repo del curso](https://github.com/platzi/astrobuild.tips/commits/main) servira de guia:

> 📌 El **Deployment** se hace al final del curso, en la [Clase 22](http://localhost:4000/posts/astro-steps/#desplegar-en-cloudflare-pages--clase-23), no antes porque debemos configurarlo con algunos valores. Pueden surgir errores.

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
2. Instalar el plugin necesario
   ```bash
   npm install @tailwindcss/line-clamp
   ```
3. Agregamos el plugin a `tailwind.config.cjs`

   ```bash
   plugins: [ require('@tailwindcss/line-clamp') ]
   ```

   > 💀 warn - As of Tailwind CSS v3.3, the `@tailwindcss/line-clamp` plugin is now included by default.
   > warn - Remove it from the `plugins` array in your configuration to eliminate this warning.

4. Compilar y correr el proyecto:

   ```bash
   npm run build
   npm run dev
   ```

## 4. [ADD] First Commit ★ [Clase 9](https://platzi.com/clases/6207-astro/60190-github-vscode-prettier-astro-config/ "GitHub, VSCode, Prettier, Astro config") ★ [Repo](https://github.com/platzi/astrobuild.tips/commit/f0c9e325b2d4da163983f3608d41c52154f96e4d)

### GitHub

1. Crear repo
2. inicializar y linkiar proyecto.
3. hacer mi first commit sigiendo los pasos de GitHub.

## 5. [UPDATE] Config ★ [Repo](https://github.com/platzi/astrobuild.tips/commit/99817611298af2f22e9af43ee508e0a1de61db61)

### Prettier

1. install la integracion de Prettier:

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

## 6. [ADD] Components ★ [Clase 10](https://platzi.com/clases/6207-astro/60191-componentes-en-astro/ "Componentes en Astro") ★ [Repo](https://github.com/platzi/astrobuild.tips/commit/1af8500be54f88ecd6414c30bcfee38ab16a8781)

Para esta seccion de **componentes en Astro**, `solo debo copiar el codigo del repo`. No es necesario instalar ninguna integracion o plugin. Y luego subir los cambios a GitHub.

## 7. [ADD] Pages ★ [Clase 11](https://platzi.com/clases/6207-astro/60192-paginas-en-astro/ "Paginas en Astro") ★ [Repo](https://github.com/platzi/astrobuild.tips/commit/8db8a623adf3b4016a7444cff2f6a90dc28a374a)

### Como Crear una pagina 404

1. Para crear la pagina `src/pages/404.astro`, debemos buscarlo en [Hyper UI](https://www.hyperui.dev/)
2. Una vez encontremos el codigo, lo copiamos, pegamos y listo.
   - Ejemplo: [error 404 page](https://www.hyperui.dev/components/application-ui/error-pages)
     > 📌Note: esta pagina en particular no requiere ningun componente en JS, asi que no es necesario agregar frontmatter al commienzo.
3. Modificar el url del boton del archivo para que redireccione al root
   > Reemplazando el `href="#"` por `href="/"`
4. Compilar y correr el proyecto:

   ```bash
   npm run build
   npm run dev
   ```

5. Probar que funcione correctamente usando un url invalido. Ej: `http://localhost:3000/test`

## 8. [ADD] Layouts ★ [Clase 12](https://platzi.com/clases/6207-astro/60193-plantillas-en-astro/ "Plantillas en Astro") ★ [Repo](https://github.com/platzi/astrobuild.tips/commit/5f9915d21a959c4b173abb40ec2170d627412803)

No es necesario instalar ninguna integracion en la seccion de _Plantillas en Astro_. **Copiamos el codigo** y listo.
Recomiendo **compilar y correr** el proyecto:

```bash
npm run build
npm run dev
```

## 9. [ADD] Markdown ★ [Clase 13](https://platzi.com/clases/6207-astro/60194-markdown/ "Markdown") ★ [Repo](https://github.com/platzi/astrobuild.tips/commit/ddedf8b38a9b95b5021ecb3fdce7d4a45fa5ac3b)

No es necesario instalar ninguna integracion en la seccion de _Markdown_. **Copiamos el codigo** y listo.

## 10. [ADD] MDX ★ [Clase 14](https://platzi.com/clases/6207-astro/60195-mdx/ "MDX") ★ [Repo](https://github.com/platzi/astrobuild.tips/commit/b8f0dd81630e3f8ba722475cf9acbc83de8732c8)

1. instalar la integracion de MDX de forma auto:

   ```bash
   npx astro add mdx
   ```

2. Copiar el codigo al archivo `src/pages/*.mdx`

3. Compilar y correr el proyecto:

   ```bash
   npm run build
   npm run dev
   ```

## 11. [ADD] Static Routes ★ [Clase 15](https://platzi.com/clases/6207-astro/60196-enrutamiento-rutas-estaticas/ "Enrutamiento: rutas estáticas") ★ [Repo](https://github.com/platzi/astrobuild.tips/commit/29e4ef7ce87efcabd53d6ce5b2f2a39b2cd4a5a6)

No es necesario instalar ninguna integracion en la seccion de _Rutas estaticas_. **Copiamos el codigo** y listo.
Recomiendo **compilar y correr** el proyecto:

```bash
npm run build
npm run dev
```

## 12. [ADD] Dynamic Routes ★ [Clase 16](https://platzi.com/clases/6207-astro/60197-enrutamiento-rutas-dinamicas/ "Enrutamiento: rutas dinámicas") ★ [Repo](https://github.com/platzi/astrobuild.tips/commit/5d2379c9c9853a8035cab4a8306797523d7a4478)

No es necesario instalar ninguna integracion en la seccion de _Rutas dinamicas_. **Copiamos el codigo** y listo.
Recomiendo **compilar y correr** el proyecto:

```bash
npm run build
npm run dev
```

## 13. [ADD] Dynamic Template ★ [Clase 17](https://platzi.com/clases/6207-astro/60198-creando-template-de-nuestra-pagina-de-entrada-del-/ "Creando template de nuestra página de entrada del blog") ★ [Repo](https://github.com/platzi/astrobuild.tips/commit/f06e81de110c4d9ebc983990dc83710fd3bb952a)

1. Para crear la plantilla `src/layouts/Posts.astro`, debemos buscarlo en [Hyper UI](https://www.hyperui.dev/)
2. Una vez encontremos el codigo, lo copiamos, pegamos y listo.

   - Ejemplo: [secciones](https://www.hyperui.dev/components/marketing/sections)

3. Compilar y correr el proyecto:

   ```bash
   npm run build
   npm run dev
   ```

## 14. [ADD] React ★ [Clase 18](https://platzi.com/clases/6207-astro/60199-componentes-en-react-header/ "Componentes en React: header") ★ [Repo](https://github.com/platzi/astrobuild.tips/commit/1d46816eb2cc034709e0bf1fd2c60141890b7c0f)

1. instalar la integracion de React

   ```bash
   npm install @astrojs/react@2.0.2
   ```

   - Instalar vue en el proyecto

   ```bash
   npm install react@18.2.0 react-dom@18.2.0
   ```

   - instalar automáticamente React en Astro:

     ```bash
      npx astro add react
     ```

   Astro instalará y configurará automáticamente React y todas sus dependencias, también se encargará de modificar los archivos de configuración automáticamente.

2. Copiamos el codigo
3. Para el archivo `src/components/Header.tsx`, se uso un componente en react de [Hyper UI](https://www.hyperui.dev/)

4. Compilar y correr el proyecto:

   ```bash
   npm run build
   npm run dev
   ```

## 15. [ADD] Vue ★ [Clase 19](https://platzi.com/clases/6207-astro/60200-componentes-en-vue-footer/ "Componentes en Vue: footer") ★ [Repo](https://github.com/platzi/astrobuild.tips/commit/210a7894e05ec0c4ca571720880cfa5b5262bf9c)

1. instalar la integracion de Vue

   ```bash
   npm install @astrojs/vue@2.0.1
   ```

   - Instalar vue en el proyecto

   ```bash
   npm install vue@3.2.47
   ```

   - instalar automáticamente Vue en Astro:

     ```bash
      npx astro add vue
     ```

   Astro instalará y configurará automáticamente Vue y todas sus dependencias, también se encargará de modificar los archivos de configuración automáticamente.

2. Copiamos el codigo
3. Para el archivo `src/components/Footer.vue`, se uso un componente en vue de [Hyper UI](https://www.hyperui.dev/)

   > Se encapsulo el codigo en un tag `<template></template>`

4. Compilar y correr el proyecto:

   ```bash
   npm run build
   npm run dev
   ```

## 16. [ADD] Svelte ★ [Clase 20](https://platzi.com/clases/6207-astro/60201-componentes-en-svelte-redes-sociales/ "Componentes en Svelte: redes sociales") ★ [Repo](https://github.com/platzi/astrobuild.tips/commit/a2b5293c6bc2943d9cf68507fba782cf1624c6c3)

1. instalar la integracion de Svelte

   ```bash
   npm install svelte@3.55.1
   ```

   - instalar automáticamente Vue en Astro:

     ```bash
      npx astro add svelte
     ```

     Astro instalará y configurará automáticamente Svelte y todas sus dependencias, también se encargará de modificar los archivos de configuración automáticamente.

2. Copiamos el codigo
3. Compilar y correr el proyecto:

   ```bash
   npm run build
   npm run dev
   ```

## 17. [ADD] Islands ★ [Clase 21](https://platzi.com/clases/6207-astro/60202-patrones-de-diseno-astro-islands/ "Patrones de diseño: Astro Islands") ★ [Repo](https://github.com/platzi/astrobuild.tips/commit/83287a4b77275ddf7d92db6350719b137a527324)

1. Recursos:

   - [Astro Islands documentation](https://docs.astro.build/es/concepts/islands/)
   - La pagina es [Tailwind UI](https://tailwindui.com/).
   - El [Header](https://tailwindui.com/components/marketing/elements/headers#component-6f74644bcfda42fc3d6735054d46bbe1) del proyecto.

2. instalar el recurso/plugin/dependencia:

   ```bash
   npm install @headlessui/react
   ```

   - Para los iconos

     ```bash
     npm install @heroicons/react
     ```

3. Para que el componente pueda interactuar con el usuario, debemos agregar: `client:load` al final del componente.

   - **ej**: `<HeaderTop client:load />`

4. Copiamos el codigo

5. Compilar y correr el proyecto:

   ```bash
   npm run build
   npm run dev
   ```

## 18. [ADD] SEO ★ [Clase 22](https://platzi.com/clases/6207-astro/60203-integraciones-seo-rss-sitemap/ "Integraciones SEO, RSS, Sitemap") ★ [Repo](https://github.com/platzi/astrobuild.tips/commit/6f885dee5dd63c5480eec7191b619939179a1f48)

### SEO

1. Copiar el codigo de [Head](https://gist.github.com/gndx/fae954a6b2afdc07afe5441fba234801 "Head - Astro · GitHub de gndx/head")
2. Pegarlo en `src/components/BaseHead.astro`

   > Debo agregar estructura js al inicio del archivo.

3. en el archivo `astro.config.mjs`, debo agregar:
   [`site: "https://jpdiaz.top",`](https://platzi.com/clases/6207-astro/60203-integraciones-seo-rss-sitemap/?time=631 "mas detalles en capitulo del video")
4. Copiamos el resto del codigo

5. Compilar y correr el proyecto:

   ```bash
   npm run build
   npm run dev
   ```

### RSS

1. instalar la [integracion de RSS](https://platzi.com/clases/6207-astro/60203-integraciones-seo-rss-sitemap/?time=746 "mas detalles en capitulo del video"):

   ```bash
   npm install @astrojs/rss@2.1.0
   ```

2. Copiar el resto del codigo

3. Compilar y correr el proyecto:

   ```bash
   npm run build
   npm run dev
   ```

### Sitemap

1. instalar la [integracion de SiteMap](https://platzi.com/clases/6207-astro/60203-integraciones-seo-rss-sitemap/?time=1063 "mas detalles en capitulo del video"):

   ```bash
   npm install @astrojs/sitemap@1.0.1
   ```

2. Copiar el resto del codigo

3. Compilar y correr el proyecto:

   ```bash
   npm run build
   npm run dev
   ```

## 19. Desplegar en Cloudflare Pages ★ [Clase 23](https://platzi.com/clases/6207-astro/60204-desplegar-en-cloudflare-pages/ "Desplegar en Cloudflare Pages")

> Recomiendo ver el video completo en Platzi

Antes de un deploy, es buena practica compilar y correr el proyecto en local para verificar que no tenga ningun error.

```bash
npm run build
npm run dev
```

📌Ojo: debo agregar lo siguiente para que funcione el projecto:

1. Seleccionar Astro
2. Asignar las [variables de entorno](https://platzi.com/clases/6207-astro/60204-desplegar-en-cloudflare-pages/?time=300)
   - NODE_VERSION
   - 16.12.0
3. Deploy

Recursos:

- [Pages Cloudflare](https://pages.cloudflare.com/)

## 20. [ADD] FIX ★ [Clase 24](https://platzi.com/clases/6207-astro/60205-bonus-aplica-mejoras-a-tu-proyecto/ "Bonus: aplica mejoras a tu proyecto") ★ [Repo](https://github.com/platzi/astrobuild.tips/commit/fc8fbb3c956eeda53f97528485c240409f8b1cb3)

No es necesario instalar ninguna integracion en esta ultima seccion _Fix_. **Copiamos el codigo** y listo.
Solo se estan haciendo unas mejoras al codigo.

> Compilar y correr el proyecto:
>
> ```bash
> npm run build
> npm run dev
> ```

## 🔥 21. Make it my Own 🔥

Si llegue hasta aca, todo esta bien y ya puedo usar este proyecto y modificarlo a mi gusto para personalizar la pagina segun mis necesidades.
