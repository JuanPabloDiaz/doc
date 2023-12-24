---
layout: post
title: "How to Auto Commit on Github"
date: 2023-12-22
categories: git
tags: git github githubactions shell devops
image: /assets/img/featured-posts/github.jpg
---

# Como Automatizar un commit diario en Github

# Como Automatizar un commit diario en Github

Un día me propuse un reto: **Hacer un commit diario en Github durante todo un año**. Ahora que ya tengo la disciplina de escribir codigo de manera constante. Se me ocurrio que quiero automatizar este proceso, y asi mismo aprender a hacerlo. Asi que le pregunte a Copilot:

## Instruccion para Copilot

> Un día me propuse un desafío: hacer un commit diario en Github durante todo un año. Ahora que ya tengo la disciplina de escribir codigo de manera constante. Se me ocurrio que quiero automatizar este proceso, y asi mismo aprender a hacerlo. ¿Hay alguna herramienta o script que pueda usar para hacer commits automáticos? preferiria usar Github Actions y Shell, pero estoy abierto a otras opciones.

## Respuesta de Copilot

Puedes automatizar este proceso utilizando **GitHub Actions**, que es una herramienta de _CI/CD_ integrada en GitHub. Aquí hay un ejemplo de cómo podrías configurar un flujo de trabajo para hacer un commit diario a tu repositorio.

Primero, necesitarás un **script que realice el commit**. Aquí hay un ejemplo simple de un **script de shell** que podría hacer esto (.github/scripts/auto_commit.sh):

```bash
#.github/scripts/auto_commit.sh

#!/bin/sh

# Crea un nuevo archivo con la fecha y hora actual como contenido. Si ya existe un archivo, reemplaza el contenido con la fecha y hora actual.

echo $(date) > commit.txt

# Agrega el nuevo archivo al staging area
git add commit.txt

# Hace un commit con un mensaje
git commit -m "Commit automatizado"

# Empuja los cambios a GitHub
git push origin main
```

Luego, necesitarás **crear un archivo de workflow de Github Actions para ejecutar este script una vez al día**. Este archivo define una serie de pasos que se ejecutan automáticamente en respuesta a eventos específicos de Github, como un push o un pull request. Aquí hay un ejemplo de cómo podría ser ese archivo de flujo de trabajo (.github/workflows/daily-commit.yml):

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

Es importante tener en cuenta que **no es una buena práctica almacenar las credenciales de Git en texto plano**. Sin embargo, en este caso, no hay forma de evitarlo, ya que el flujo de trabajo de GitHub Actions se ejecuta en un entorno aislado y no tiene acceso a las credenciales de Git almacenadas en tu máquina local. Por lo tanto, _necesitarás crear un token de acceso personal de GitHub_ y _configurarlo como una variable de entorno_ en tu flujo de trabajo.

## Como Configurar las Credenciales de Git

Para _configurar las credenciales de Git_ en el flujo de trabajo de GitHub Actions, necesitarás un **token de acceso personal de GitHub**. Aquí te explico cómo hacerlo:

### 1. Genera un **`token de acceso personal en GitHub`**:

- Ve a la configuración de tu cuenta de GitHub (haz clic en tu foto de perfil en la esquina superior derecha y selecciona **`"Settings"`** (Configuración) ).
- En el menú de la izquierda, selecciona **`"Developer settings"`** (Configuración de desarrollador).
- Luego, selecciona **`"Personal access tokens"`** (Tokens de acceso personal).
- Haz clic en **`"Generate new token"`** (Generar nuevo token).
- Dale un **nombre descriptivo** a tu token.
- Selecciona los **permisos** que necesitas para tu flujo de trabajo, en este caso, necesitarás el **`permiso repo`** y haz clic en **`"Generate token"`** (Generar token).

### 2. **Configura el token** de acceso personal **como una variable de entorno** en tu flujo de trabajo:

En tu archivo de flujo de trabajo (.github/workflows/daily-commit.yml), debes agregar una _nueva etapa_ antes de la etapa **`Run script`** para **configurar las credenciales de Git**. Aquí te muestro cómo:

- Opcion 1:

```yaml
- name: Set up Git credentials
  run: |
    git config --global user.name "your-username"
    git config --global user.email "your-email@example.com"
    git config --global credential.helper store
    echo "https://$TOKEN:x-oauth-basic@github.com" > ~/.git-credentials
  env:
    TOKEN: ${{ secrets.YOUR_GITHUB_TOKEN }}
```

> Nota:
>
> - Reemplaza **"your-username"** y **"your-email@example.com"** con tu nombre de usuario de GitHub y tu correo electrónico.
> - En la última línea, `TOKEN` es una variable de entorno que contiene tu token de acceso personal. Necesitarás agregar este token a las **"Secrets"** de tu repositorio en GitHub (más sobre esto más adelante).

- Opcion 2:

```yaml
- name: Set up Git credentials
  run: |
    git config --global user.name ""your-username"
    git config --global user.email "your-email@example.com"
    git remote set-url origin https://${{ secrets.YOUR_GITHUB_TOKEN }}@github.com/username/repo.git
```

> Nota:
>
> - Al igual que en opcion 1, reemplaza **"your-username"** y **"your-email@example.com"** con tu nombre de usuario de GitHub y tu correo electrónico.

<details>
<summary>Asi debería estar quedando el archivo de workflow de Github Actions</summary>

```yaml
# .github/workflows/daily-commit.yml
name: Daily Commit

on:
  schedule:
    - cron: "0 10 * * *"

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2

      - name: Set up Git credentials
        run: |
          git config --global user.name ""your-username"
          git config --global user.email "your-email@example.com"
          git remote set-url origin https://${{ secrets.YOUR_GITHUB_TOKEN }}@github.com/username/repo.git
```

</details>

#### Cuales son las diferencias entre las opciones 1 y 2?

La principal diferencia entre estos dos fragmentos de código es cómo se manejan las credenciales de Git:

- En la **Opcion 1**, se utiliza `git config --global credential.helper store` para almacenar las credenciales de usuario en un archivo en su directorio local. Luego, se crea un archivo `.git-credentials` en el directorio home del usuario con la URL que incluye el token de autenticación. Este método almacena las credenciales en un archivo en texto plano en su sistema.

- En la **Opcion 2**, se utiliza `git remote set-url origin` para cambiar la URL del repositorio remoto 'origin' a una que incluye el token de autenticación. Este método no almacena las credenciales en su sistema, sino que las incluye en la URL del repositorio remoto.

Ambos métodos tienen sus ventajas y desventajas. El almacenamiento de credenciales es más seguro ya que no expone el token en la línea de comandos, pero puede ser menos seguro si otras personas tienen acceso a su sistema. El uso de la URL del repositorio remoto es menos seguro ya que expone el token en la línea de comandos, pero puede ser más seguro si su sistema es seguro y sólo usted tiene acceso a él.

### 3. Agrega tu token de acceso personal a las **`"Secrets"`** de tu repositorio:

- Ve a la página principal de tu repositorio en GitHub y selecciona **`"Settings"`** (Configuración).
- Luego, selecciona **`"Secrets"`** en el menú de la izquierda.
- Haz clic en **`"New repository secret"`** (Nuevo secreto del repositorio).
- Ingresa **`YOUR_GITHUB_TOKEN`** como el nombre del secreto y pega tu token de acceso personal en el campo **`Value`** (Valor).
- Haz clic en **`"Add secret"`** (Agregar secreto).

Ahora, tu flujo de trabajo de GitHub Actions debería ser capaz de empujar a tu repositorio utilizando tu token de acceso personal.

### 4. Ejecuta tu flujo de trabajo de GitHub Actions manualmente:

En el archivo de flujo de trabajo de GitHub Actions, debes agregar un **evento** que permita ejecutar el flujo de trabajo manualmente. Aquí te muestro cómo:

```yaml
on:
  workflow_dispatch: # This allows you to manually trigger the workflow
```

Ahora, puedes ejecutar tu flujo de trabajo de GitHub Actions manualmente haciendo clic en el botón **`"Run workflow"`** (Ejecutar flujo de trabajo) en la página principal de tu repositorio en GitHub.

<details>
<summary>Asi debería estar quedando el archivo de workflow de Github Actions</summary>

```yaml
# .github/workflows/daily-commit.yml
name: Daily Commit

on:
  schedule:
    - cron: "0 10 * * *" # Esto se ejecutará todos los días a las 5 AM EST.
  workflow_dispatch: # This allows you to manually trigger the workflow

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2

      - name: Set up Git credentials
        run: |
          git config --global user.name ""your-username"
          git config --global user.email "your-email@example.com"
          git remote set-url origin https://${{ secrets.YOUR_GITHUB_TOKEN }}@github.com/username/repo.git
```

</details>

## Error al Ejecutar el Script de Shell

Si llegaste hasta aca y aun no puedes ejecutar el script de shell, asegúrate de que el script de shell tenga **`permisos de ejecución`**. Puedes hacer esto agregando el siguiente comando a tu flujo de trabajo de GitHub Actions:

```yaml
- name: Run script
  run: |
    chmod +x ./.github/scripts/auto_commit.sh
    bash ./.github/scripts/auto_commit.sh
```

<details>
<summary>Asi debería estar quedando el archivo de workflow de Github Actions</summary>

```yaml
# .github/workflows/daily-commit.yml
name: Daily Commit

on:
  schedule:
    - cron: "0 10 * * *" # Esto se ejecutará todos los días a las 5 AM EST.
  workflow_dispatch: # This allows you to manually trigger the workflow

jobs:
  build:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v2

      - name: Set up Git credentials
        run: |
          git config --global user.name ""your-username"
          git config --global user.email "your-email@example.com"
          git remote set-url origin https://${{ secrets.YOUR_GITHUB_TOKEN }}@github.com/username/repo.git

      - name: Run script
        run: |
          chmod +x ./.github/scripts/auto_commit.sh
          bash ./.github/scripts/auto_commit.sh
```

</details>

## Error Despues de Correr Github Actions

En este punto, el script de shell ya corre pero genera un error al intentar hacer el commit y empujar los cambios a tu repositorio. Aquí hay un ejemplo de lo que podría verse en la pestaña **`"Actions"`** (Acciones) de tu repositorio en GitHub:

```bash
Run chmod +x ./.github/scripts/auto_commit.sh
[main 8a928cc] Commit automatizado
 1 file changed, 1 insertion(+)
 create mode 100644 commit.txt
remote: Write access to repository not granted.
fatal: unable to access 'https://github.com/username/repoName.git/': The requested URL returned error: 403
Error: Process completed with exit code 128.
```

Si no sabes que significa este error, preguntale a Copilot **what does this error mean?** y te dara una explicacion. Tambien puedes preguntar: **how to solve in github actions write access to the repository not granted**.

### Explicacion del Error

Esto significa que **NO tienes permiso** para escribir/empujar a tu repositorio.

- Puede ser que el **token de acceso personal que configuraste no tenga los permisos correctos**. Asegúrate de que el token de acceso personal tenga el permiso **repo**.

### Solucion

- Revise que el token de acceso personal tenga el permiso **repo**.
- Revise que el token de acceso personal este bien escrito en el archivo de flujo de trabajo.

#### [Assigning permissions to jobs](https://docs.github.com/en/actions/using-jobs/assigning-permissions-to-jobs)

Necesitará asignar los **permisos a los trabajos** en un flujo de trabajo utilizando la palabra clave **`"permissions"`**. En este caso, deberá asignar el permiso **`"contents"`** al trabajo que está ejecutando el script. Aquí te muestro cómo:

```yaml
permissions: # Permissions needed for the job to run
  issues: write
  pull-requests: write
  contents: write
```

## Archivo Terminado del Flujo de Trabajo de Github Actions

Finalmente, aquí está el archivo de flujo de trabajo de GitHub Actions completo:

```yaml
# .github/workflows/daily-commit.yml
name: Daily Commit

on:
  schedule:
    - cron: "0 10 * * *" # Esto se ejecutará todos los días a las 5 AM EST.
  workflow_dispatch: # This allows you to manually trigger the workflow

jobs:
  build:
    runs-on: ubuntu-latest

    permissions: # This grants permissions to the workflow - This is needed to create a commit
      issues: write
      pull-requests: write
      contents: write

    steps:
      - uses: actions/checkout@v2

      - name: Set up Git credentials
        run: |
          git config --global user.name ""your-username"
          git config --global user.email "your-email@example.com"
          git remote set-url origin https://${{ secrets.YOUR_GITHUB_TOKEN }}@github.com/username/repo.git

      - name: Run script
        run: |
          chmod +x ./.github/scripts/auto_commit.sh
          bash ./.github/scripts/auto_commit.sh
```

## Archivo Terminado del Script de Shell

Aquí está el archivo de script de shell completo:

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
