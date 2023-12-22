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

## Instruccion para Copilot

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

## It didn't work

Si no funciona, asegúrate de que tu script de shell tenga permisos de ejecución. Puedes hacer esto ejecutando el siguiente comando en tu terminal:

```bash
chmod +x .github/scripts/auto_commit.sh
```

## Error despues de correr Github Actions

Si obtienes un error como este:

```bash
Run chmod +x ./.github/scripts/auto_commit.sh
[main 8a928cc] Commit automatizado
 1 file changed, 1 insertion(+)
 create mode 100644 commit.txt
remote: Write access to repository not granted.
fatal: unable to access 'https://github.com/JuanPabloDiaz/365.git/': The requested URL returned error: 403
Error: Process completed with exit code 128.
```

Esto significa que no tienes permiso para escribir/empujar a tu repositorio.

Puede ser que el token de acceso personal que configuraste no tenga los permisos correctos. Asegúrate de que el token de acceso personal tenga el permiso **repo**.

Yo tambien pegue el error en Copilot, y me dio posibles soluciones. Tambien pregunte: **how to solve in github actions write access to the repository not granted**

## Solucion

- Revise que el token de acceso personal tenga el permiso **repo**.
- Revise que el token de acceso personal este bien escrito en el archivo de flujo de trabajo.

#### [Assigning permissions to jobs](https://docs.github.com/en/actions/using-jobs/assigning-permissions-to-jobs)

You will need to assign the _permissions_ to jobs in a workflow using the `permissions` keyword. in this case, you will need to assign the `contents` permission to the job that is running the script.

```yaml
permissions: # Permissions needed for the job to run
  issues: write
  pull-requests: write
  contents: write
```

Here is how your workflow file should look like:

```yaml
# .github/workflows/daily-commit.yml
name: Daily Commit

on:
  schedule:
    - cron: "0 10 * * *" # Esto se ejecutará todos los días a las 5 AM EST. EST es UTC-5. Sin embargo, GitHub Actions ejecuta trabajos en la zona horaria UTC. Por lo tanto, si quieres que tu trabajo se ejecute a las 5 AM EST, debes convertir esa hora a UTC. 5 AM EST es igual a 10 AM UTC.
  workflow_dispatch: # This allows you to manually trigger the workflow

jobs:
  build:
    runs-on: ubuntu-latest

    permissions: # This grants permissions to the workflow - This is needed to create a commit - see https://docs.github.com/en/actions/reference/workflow-syntax-for-github-actions#permissions
      issues: write
      pull-requests: write
      contents: write

    steps:
      - uses: actions/checkout@v2

      - name: Set up Git credentials
        run: |
          git config --global user.name "JuanPabloDiaz"
          git config --global user.email "juanchodis@hotmail.com"
          git remote set-url origin https://${{ secrets.JD_GITHUB_TOKEN }}@github.com/JuanPabloDiaz/365.git

      - name: Run script
        run: |
          chmod +x ./.github/scripts/auto_commit.sh
          bash ./.github/scripts/auto_commit.sh
```

Here is how your script should look like:

```bash
# .github/scripts/auto_commit.sh
#!/bin/sh

# Check if the file exists, if not, create it
if [ ! -f ./days/auto-commit.md ]; then
    echo "- $(date)  " > ./days/auto-commit.md
	# it create a new file with the current date and time as a list item. the space after the date creates a line break
	# the > operator creates a new file
else
    # Append (add) the current date and time to the existing content of the file as a new list item
    echo "- $(date)  " >> ./days/auto-commit.md
	# the >> operator appends the output to the end of the file
fi

# Add the new file to the staging area
git add ./days/auto-commit.md

# Make a commit with a message
git commit -m "Commit automatizado $(date)"

# Push the changes to GitHub
git push origin main
```

<!-- ACKNOWLEDGMENTS -->

## Acknowledgments 📚

Resources list that I find helpful and would like to give credit to.

- []()
