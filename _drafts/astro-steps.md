---
layout: post
title: "Para Montar de Forma Rapida el Proyecto del Curso de Creación de Páginas Web con Astro"
categories: astro
tags: draft
---

Este archivo sirve como guia para correr el proyecto e instalar las dependencias necesatias si por alguna razon me toca empezar de cero y crear nuevamente una pagina con Astro.

Paso a paso del curso basandonos en el [Repo del curso](https://github.com/platzi/astrobuild.tips/commits/main):

> Nota: El **Deployment** se hace al final del curso (Clase 22), no antes porque debemos configurarlo con algunos valores. Pueden surgir errores.

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

Para esta seccion de **componentes en Astro**, `solo debo copiar el codigo del repo`. No es necesario instalar ninguna integracion o plugin. Y luego subir los cambios a GitHub.

## 7. [ADD] Pages ★ [Clase 11](https://platzi.com/clases/6207-astro/60192-paginas-en-astro/ "Paginas en Astro")

### Como Crear una pagina 404

1. Para crear la pagina `src/pages/404.astro`, debemos buscarlo en [Hyper UI](https://www.hyperui.dev/)
2. Una vez encontremos el codigo, lo copiamos, pegamos y listo.
   - Ejemplo: [error 404 page](https://www.hyperui.dev/components/application-ui/error-pages)
     > Note: esta pagina en particular no requiere ningun componente en JS, asi que no es necesario agregar frontmatter al commienzo.
3. Modificar el url del boton del archivo para que redireccione al root
   > Reemplazando el `href="#"` por `href="/"`
4. Compilar y correr el proyecto:

   ```bash
   npm run build
   npm run dev
   ```

5. Probar que funcione correctamente usando un url invalido. Ej: `http://localhost:3000/test`

## 8. [ADD] Layouts ★ [Clase 12](https://platzi.com/clases/6207-astro/60193-plantillas-en-astro/ "Plantillas en Astro")

No es necesario instalar ninguna integracion en la seccion de _Plantillas en Astro_. **Copiamos el codigo** y listo.
Recomiendo **compilar y correr** el proyecto:

```bash
npm run build
npm run dev
```

## 9. [ADD] Markdown ★ [Clase 13](https://platzi.com/clases/6207-astro/60194-markdown/ "Markdown")

No es necesario instalar ninguna integracion en la seccion de _Markdown_. **Copiamos el codigo** y listo.

## 10. [ADD] MDX ★ [Clase 14](https://platzi.com/clases/6207-astro/60195-mdx/ "MDX")

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

## 11. [ADD] Static Routes ★ [Clase 15](https://platzi.com/clases/6207-astro/60196-enrutamiento-rutas-estaticas/ "Enrutamiento: rutas estáticas")

No es necesario instalar ninguna integracion en la seccion de _Rutas estaticas_. **Copiamos el codigo** y listo.
Recomiendo **compilar y correr** el proyecto:

```bash
npm run build
npm run dev
```

## 12. [ADD] Dynamic Routes ★ [Clase 16](https://platzi.com/clases/6207-astro/60197-enrutamiento-rutas-dinamicas/ "Enrutamiento: rutas dinámicas")

No es necesario instalar ninguna integracion en la seccion de _Rutas dinamicas_. **Copiamos el codigo** y listo.
Recomiendo **compilar y correr** el proyecto:

```bash
npm run build
npm run dev
```

## 13. [ADD] Dynamic Template ★ [Clase 17](https://platzi.com/clases/6207-astro/60198-creando-template-de-nuestra-pagina-de-entrada-del-/ "Creando template de nuestra página de entrada del blog")

1. Para crear la plantilla `src/layouts/Posts.astro`, debemos buscarlo en [Hyper UI](https://www.hyperui.dev/)
2. Una vez encontremos el codigo, lo copiamos, pegamos y listo.

   - Ejemplo: [secciones](https://www.hyperui.dev/components/marketing/sections)

3. Compilar y correr el proyecto:

   ```bash
   npm run build
   npm run dev
   ```

## 14. install React - npx astro add react

## 15. install @headlessui/react

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
