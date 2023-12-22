---
layout: post
title: "How to Auto Commit on Github"
date: 2023-12-22
categories: git
tags: git github githubactions shell devops
image: /assets/img/featured-posts/github.jpg
---

# Como Automatizar un commit diario en Github

Un día me propuse un reto: **Hacer un commit diario en Github durante todo un año**. Ahora que ya tengo la disciplina de escribir codigo de manera constante. Se me ocurrio que quiero automatizar este proceso, y asi mismo aprender a hacerlo. Asi que le pregunte a Copilot:

## Instruccion para copilot

> Un día me propuse un desafío: hacer un commit diario en Github durante todo un año. Ahora que ya tengo la disciplina de escribir codigo de manera constante. Se me ocurrio que quiero automatizar este proceso, y asi mismo aprender a hacerlo. ¿Hay alguna herramienta o script que pueda usar para hacer commits automáticos? preferiria usar Github Actions y Shell, pero estoy abierto a otras opciones.

## Respuesta de Copilot

Puedes automatizar este proceso utilizando GitHub Actions, que es una herramienta de CI/CD integrada en GitHub. Aquí hay un ejemplo de cómo podrías configurar un flujo de trabajo para hacer un commit diario a tu repositorio.

Primero, necesitarás un script que realice el commit. Aquí hay un ejemplo simple de un script de shell que podría hacer esto (.github/scripts/auto_commit.sh):

```bash
#.github/scripts/auto_commit.sh

#!/bin/sh

# Crea un nuevo archivo con la fecha y hora actual como contenido
echo $(date) > commit.txt

# Agrega el nuevo archivo al staging area
git add commit.txt

# Haz un commit con un mensaje
git commit -m "Commit automatizado"

# Empuja los cambios a GitHub
git push origin main
```

Luego, necesitarás crear un archivo de workflow de Github Actions para ejecutar este script una vez al día. Este archivo define una serie de pasos que se ejecutan automáticamente en respuesta a eventos específicos de Github, como un push o un pull request. Aquí hay un ejemplo de cómo podría ser ese archivo de flujo de trabajo (.github/workflows/daily-commit.yml):

```yaml
name: Daily Commit

on:
  schedule:
    - cron: "0 0 * * *" # Esto se ejecutará todos los días a medianoche

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2

      - name: Run script
        run: bash /path/to/your/auto_commit_script.sh
```

Este flujo de trabajo se ejecutará todos los días a medianoche y ejecutará tu script, que hará un commit y lo empujará a tu repositorio.

Nota: Asegúrate de reemplazar `/path/to/your/repo` y `/path/to/your/script.sh` con las rutas reales a tu repositorio y a tu script, respectivamente. Además, este script asume que estás trabajando en la rama `main`. Si estás trabajando en una rama diferente, reemplaza main con el nombre de tu rama.

Además, necesitarás **configurar las credenciales de Git** en el flujo de trabajo de GitHub Actions para que pueda empujar a tu repositorio. Puedes hacer esto utilizando un **token** de acceso personal de GitHub y configurándolo como una **variable de entorno** en tu flujo de trabajo.

## Como configurar las credenciales de Git

Para configurar las credenciales de Git en el flujo de trabajo de GitHub Actions, necesitarás un token de acceso personal de GitHub. Aquí te explico cómo hacerlo:

1. Genera un token de acceso personal en GitHub:

- Ve a la configuración de tu cuenta de GitHub (haz clic en tu foto de perfil en la esquina superior derecha y selecciona "Configuración").
- En el menú de la izquierda, selecciona "Developer settings" (Configuración de desarrollador).
- Luego, selecciona "Personal access tokens" (Tokens de acceso personal).
- Haz clic en "Generate new token" (Generar nuevo token).
- Dale un nombre descriptivo a tu token, selecciona las casillas de verificación que correspondan a los permisos que necesitas (para este caso, necesitarás el permiso repo) y haz clic en "Generate token" (Generar token).

2. Configura el token de acceso personal como una variable de entorno en tu flujo de trabajo:

En tu archivo de flujo de trabajo (.github/workflows/daily-commit.yml), puedes agregar una nueva etapa antes de la etapa "Run script" para configurar las credenciales de Git. Aquí te muestro cómo:

```yaml
- name: Set up Git credentials
  run: |
    git config --global user.name "Your Name"
    git config --global user.email "your-email@example.com"
    git config --global credential.helper store
    echo "https://$TOKEN:x-oauth-basic@github.com" > ~/.git-credentials
  env:
    TOKEN: ${{ secrets.YOUR_GITHUB_TOKEN }}
```

3. Reemplaza "Your Name" y "your-email@example.com" con tu nombre de usuario de GitHub y tu correo electrónico.
4. En la última línea, TOKEN es una variable de entorno que contiene tu token de acceso personal. Necesitarás agregar este token a las "Secrets" de tu repositorio en GitHub:

- Ve a la página principal de tu repositorio en GitHub y selecciona "Settings" (Configuración).
- Luego, selecciona "Secrets" en el menú de la izquierda.
- Haz clic en "New repository secret" (Nuevo secreto del repositorio).
- Ingresa `YOUR_GITHUB_TOKEN` como el nombre del secreto y pega tu token de acceso personal en el campo "Value" (Valor).
- Haz clic en "Add secret" (Agregar secreto).

Ahora, tu flujo de trabajo de GitHub Actions debería ser capaz de empujar a tu repositorio utilizando tu token de acceso personal.

<!-- ACKNOWLEDGMENTS -->

## Acknowledgments 📚

Resources list that I find helpful and would like to give credit to.

- []()
